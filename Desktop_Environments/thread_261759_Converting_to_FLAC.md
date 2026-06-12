---
title: "Converting to FLAC"
date: 2006-09-20
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-20
I have a wave file and two RealAudio files I'd like to convert to FLAC, but I'm having trouble finding the easiest to way to this. I'm using Kubuntu, and don't mind doing this using a terminal (since I'll likely not be doing this often).

---

### Post by JAwuku on 2006-09-20
You could try soundconverter, which is a simple install:

```
sudo apt-get install soundconverter
```

(enable universe repository first)

This is a GTK program, but all dependencies will be installed automatically.

For a simple WAV to FLAC conversion, install shntool, then one command:

```
sudo apt-get install shntool
shntool conv -o flac *.wav

```

---

