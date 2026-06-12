---
title: "Speech Recognition with VoxForge/Julius"
date: 2009-06-14
forum: General Help
---

### Post by Morgath on 2009-06-14
I have installed julius and downloaded the current Julian-Quickstart from VoxForge. However, it has a limited vocabulary - "DIAL", "STEVE", etc,.

I have tried searching for documentation, but I can't seem to find the right guides to build my own vocabulary for use with this. Anyone got ideas?

---

### Post by Soul-Sing on 2009-06-14
I think voxforge is busy building the vocabulary, thats what I have heard. I had never heard of julius.
I will ask around.

---

### Post by rvk on 2009-08-21
Julius itself is made for continuous speech recognition (dictation). There is a part of Julius, Julian, which can be used for command and control applications. Such an application uses a grammar, which defines the commands (separate words and how they can be combined). You should be able to find information on how to build a grammar for Julian on VoxForge.org

What you have downloaded is a demo of Julius/Julian (the speech recognition engine) with an example grammar (CALL DAVE etc) an acoustic model and a vocabulary.

The vocabulary is big enough to do dictation, but the acoustic model is not good enough to get adequate results. This is because it is based on a very limited amount of speech. Please submit some speech in your native language to help VoxForge create better acoustic models. If your language is not being collected yet, then translate the speech submission app into your language.

The acoustic model is good enough to do some simple command and control, because this is a lot easier than dictation. I think you should probably start with reading the documentation at VoxForge. You might want to start with the [Julius manual]("http://voxforge.org/home/docs/julius-manual").

In the future it's probably better to ask questions over at the VoxForge forums. Speech recognition is quite hard and the few people who know a lot about it can only check out so many forums.

Good luck!

---

### Post by RainCT on 2009-09-02
You can install Julius and the Voxforge acoustic model on Ubuntu by installing the packages [julius](apt://julius) and [julius-voxforge](apt://julius-voxforge). Then you'll find examples in /usr/share/doc/julius-voxforge/examples/ of how to create your own grammar and even an example of how to write a simple command and control application.

---

