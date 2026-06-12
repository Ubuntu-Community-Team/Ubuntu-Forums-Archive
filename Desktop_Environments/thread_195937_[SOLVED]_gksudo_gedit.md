---
title: "[SOLVED] gksudo gedit"
date: 2006-06-13
forum: Desktop Environments
---

### Post by dstein on 2006-06-13
When I run gksudo gedit from a terminal, I get:

(gedit:10823): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default

but everything seems to work. Is something going wrong. Also, I have read about the differences but I don not really understand why it is necessary to use gksudo rather than sudo. Thanks.

---

### Post by zerwas on 2006-06-13
Nothing to worry about. It's about sound.
You **can** you sudo rather thaan gksudo ;), there's no problem in doing this if i am right. :)

Greetings,
zeR

---

### Post by aysiu on 2006-06-13
*kdesu* and *gksudo* from the terminal will almost always give you weird "errors," but they are still the preferred methods of using graphical applications.

Some graphical applications will screw up your settings permissions or just plain *not work* if you use them with *sudo*.

---

### Post by dpm on 2006-06-13
Alternatively, you can also use:

**ALT+F2** and then type **gksudo gedit**

I find this to be the quickest option.

---

### Post by aysiu on 2006-06-13
If you want to be super-quick, create a keyboard shortcut for the command ```
gksudo nautilus
```

---

### Post by dstein on 2006-06-13
This must be because my sound card is having probelms being recognized. Has anyone had success using a Philips Seismic Edge sound card with Linux? Thanks.

---

### Post by dpm on 2006-06-14
[quote=aysiu]If you want to be super-quick, create a keyboard shortcut for the command ```
gksudo nautilus
```[/quote]

That was an awesome tip, I had never thought of that. Thanks!

---

