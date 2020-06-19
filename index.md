## Xiaomingbot：A Multilingual Robot News Reporter

Xiaomingbot is an intelligent, multilingual and multimodal software robot equipped with four integral capabilities: 

- News Generation
- News Translation
- News Reading 
- Avatar Animation

### News Generation

Xiaomingbot takes a table as input，for example, a table that describes the score of each player in a soccer game.
To generate news, Xiaomingbot use templated-based table-to-text methods.
That is, we have many different templates to generate sentences for the news.
Every time Xiaomingbot generate a sentence, she randomly pick up a template and replace the placeholders with the according content in the input table.
To generate the news abstract, Xiaomingbot use a BERT-based model to score sentences in the news and pick up those achieving high score to make up the final abstract.

### News Translation

Xiaomingbot uses a Transformer-based machine translation model to translate the generated news in chinese into different languages, so that people around the world can read the news conveniently.
Although it can already generate fluent translated news, some certain proper nouns are still hard to translate because it may be confusing for the translation model.
Therefore, Xiaomingbot also use named entity replacement mechanism, that is, directly replace the named entitie with its according translation.
To accelerate the decoding process, we implement a faster CUDA-based NMT system, whose inference speed is ten times than tensorflow, and it can be found [Here](https://github.com/bytedance/byseqlib).

### News Reading

With a small amount of recorded voice of a speaker in one language provided as training data, we can train a TTS model for Xiaomingbot.
This TTS model has a cross-lingual voice cloning mechanism.
In detail, after training, it can read news in different language with exactly the same voice as we provided before.

### Avatar Animation

Xiaomingbot can generate lip motion synced with the audio synthesized by the TTS model, and render hairs, clothing, etc.
For lip motion, we use a Seq2Seq model.
The input sequence is the phoneme and the according duration drawn from the TTS model, and the ouput is a sequence of mouth blendshape weights.
With these different mouth blendshape weights, Xiaomingbot can make a lot of different facial expressions.
For other rendering, we use Unity and different algorithms like normal mapping.

## Demo Video

Here is our Demo Video.

