# Homework: Generative QA with Pretrained Encoder

## Задание

Заполните пропуски в ноутбуке `generative_qa_pretrained.ipynb` и обучите модель генеративного QA.

**Цель**: достичь **F1 ≥ 25%** на валидационном наборе.

## Архитектура

```
[Question + Context] → Frozen DistilBERT (pretrained on SQuAD) → Encoder Embeddings
                                                                        ↓
                                                              Trainable Decoder → Answer
```

## Рекомендации

1. **Learning rate**: начните с `3e-4`, если loss не падает — уменьшите до `1e-4`

2. **Batch size**: используйте максимальный, который влезает в память (64-128)

3. **Epochs**: 5-10 эпох обычно достаточно, следите за val_loss

4. **Pretrained embeddings**: не замораживайте их полностью — fine-tuning помогает

5. **Gradient clipping**: используйте `gradient_clip_val=1.0` для стабильности
