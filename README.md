# custom_gpt_llama_train

Pretrained model for translating japanese to english can be found here->https://huggingface.co/tirthadagr8/Japanese_to_english_gpt2CasualLM_GemmaTokenizer

Made using Gpt-Small from scratch for learning purpose.
Tokenizer used is from Gemma 2-2B-JPN-IT which is trained on japanese dataset from JESC.

Model usage:-

```python
from transformers import AutoTokenizer,AutoModelForCausalLM
tokenizer=AutoTokenizer.from_pretrained('tirthadagr8/Japanese_to_english_gpt2CasualLM_GemmaTokenizer')
model=AutoModelForCausalLM.from_pretrained('tirthadagr8/Japanese_to_english_gpt2CasualLM_GemmaTokenizer')
model.cuda()
src_text='あなたとは遊びたくない'
print(tokenizer.batch_decode(model.generate(tokenizer.encode(f"Translate the following Japanese sentence to English:\n\nJapanese:{src_text}\nEnglish:",return_tensors='pt')[:,:-1].cuda(),max_length=128))[0])
```
OUTPUT:
```
<bos>Translate the following Japanese sentence to English:

Japanese:あなたとは遊びたくない
English:i don't want to play with you.<eos>
```
```bibtex
@ARTICLE{pryzant_jesc_2018,
   author = {{Pryzant}, R. and {Chung}, Y. and {Jurafsky}, D. and {Britz}, D.},
    title = "{JESC: Japanese-English Subtitle Corpus}",
  journal = {Language Resources and Evaluation Conference (LREC)},
 keywords = {Computer Science - Computation and Language},
     year = 2018
}
```
