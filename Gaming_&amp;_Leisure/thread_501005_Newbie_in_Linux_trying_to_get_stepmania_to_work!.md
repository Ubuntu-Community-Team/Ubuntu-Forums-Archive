---
title: "Newbie in Linux trying to get stepmania to work!"
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by Cigue on 2007-07-14
So, it's my first time working in Linux and i'm trying to get StepMania to work. what do I do with the tar.gz files and stuff?

---

### Post by Contrast on 2007-07-14
Extract it wherever, go to the new folder, and click "stepmania" - simple as that. ;-)

---

### Post by Cigue on 2007-07-14
at first I downloaded Binary, wich made my computer reboot. then I added Source, and it plain doesn't works. HEELP T_T

Edit : tried to re-install, and when I extract it I get the following error :

tar: Pattern matching characters used in file names. Please,
tar: use --wildcards to enable pattern matching, or --no-wildcards to
tar: suppprimer cet avertissement.
[.....]
tar: StepMania-3.9/Themes/default/Fonts/MusicList titles [[]extras[]].png: ne peut être retrouvé dans l'archive.
tar: Pattern matching characters used in file names. Please,
tar: use --wildcards to enable pattern matching, or --no-wildcards to
tar: suppprimer cet avertissement.
tar: StepMania-3.9/Themes/default/Fonts/_shared2 [[]extras[]].png: ne peut être retrouvé dans l'archive.
tar: Statut d'erreur reporté d'erreurs précédentes.

---

### Post by BlahMan_of.Doom on 2007-07-14
[http://www.stepmania.com/download.php?file=downloads/StepMania-3.9a-linux.tar.gz](http://www.stepmania.com/download.php?file=downloads/StepMania-3.9a-linux.tar.gz)

Download that to your desktop. Double click it, and extract it to a folder on your desktop. Then double click the stepmania file. You could also go to terminal and run it too. You don't need to compile it from source. Try it this way, you might have done somethign wrong, even though you said it reboots.

---

### Post by Cigue on 2007-07-14
Thanks Doom dude, i'll try that. When I try running Warcraft on Wine, it restarts my session too! and Stepmania on Wine lags like **** :( any clue how I might fix the Wine version?

EDIT : tried it, and I still get the error while extracting.

---

### Post by AJB2K3 on 2007-07-15
I HAD ISSUES TO. Try redownloading the file from another mirror.

theres also something about the tar command/archiver that needed altering to extract step mania.
There some sort of bug in the files that causes tar to be a bit confused.

---

### Post by Cigue on 2007-07-15
Meh, there IS NO other mirror :( anybody has a clue what I should do?

I get the same error while trying to run Warcraft III on Wine -.- I mean, my session reboots when I try to run stepmania-linux and warcraft-wine.

---

### Post by BlahMan_of.Doom on 2007-07-17
> **Cigue said:**
> Meh, there IS NO other mirror :( anybody has a clue what I should do?

I get the same error while trying to run Warcraft III on Wine -.- I mean, my session reboots when I try to run stepmania-linux and warcraft-wine.

Okay. Let's see..you want Warcraft to work too? Do me a favor. Tell me what kind of video card you have, and type
```
glxinfo | grep rendering
``` into your terminal and tell me what the output is. That's the first step.

---

