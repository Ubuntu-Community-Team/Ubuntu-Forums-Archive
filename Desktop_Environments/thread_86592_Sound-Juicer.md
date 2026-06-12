---
title: "Sound-Juicer"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Mikulcak on 2005-11-05
Hi all,
I'm just spending time configuratin my Ubuntu the way I want to have it, but I stumbled over the configuration of Sound-Juicer. I want it to work with lame and VBR; what is the correct GStreamer - Pipeline to have it do this?
I don't want to use rippers like grip, because I really am fed up with overloaded programs. I want a simple, easy-to-use surface that rips my cd with after one click. It's not that I couldn't handle them, but I don't want to.
To be honest, I'm a little bit in love with Apple...

Thank you,
Mikulcak

P.S.: And is there a way to add another name of the files created during the ripping - process? The name I wish: titlenumber. title

---

### Post by poofyhairguy on 2005-11-05
> **Mikulcak]Hi all,
I'm just spending time configuratin my Ubuntu the way I want to have it, but I stumbled over the configuration of Sound-Juicer. I want it to work with lame and VBR said:**
> 

Moved to correct forum- the other one is not for questions.

I know the the files you need for lame support. First follow this guide:

[https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu](https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu).

Then close synaptic and use this command:

[QUOTE]sudo apt-get install gstreamer0.8-plugins-multiverse lame lame-extras

That command might fix your other problem too.

---

### Post by Mikulcak on 2005-11-06
Well, thank you, but that didn't solve any problem. In fact, I don't really *have *a problem.
Of course, I arlready have installed lame and it works, but I wanted to know the GStreamer - Pipeline to create *vbr *- mp3s with lame.
The other question was whether I could add any other file - creation rule?
But, thank you, anyway,
Mikulcak

---

