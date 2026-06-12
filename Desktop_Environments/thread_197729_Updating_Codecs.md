---
title: "Updating Codecs"
date: 2006-06-16
forum: Desktop Environments
---

### Post by smoove on 2006-06-16
Hi I followed the Ubuntu guide to get all the codecs, but at the end of the update in terminal it states:

> 
After unpacking 1819kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.


Even though I entered "Y", it still continues to abort the process, is there something Im doing wrong? Thanks.

---

### Post by l4v4_f10w on 2006-06-16
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs)

follow this guide, always worked for me.

---

### Post by smoove on 2006-06-16
Thanks, done that, but I dont get sound online with flash?

---

### Post by Ramses de Norre on 2006-06-16
```
sudo aptitude install flashplugin-nonfree alsa-oss
``` and change the shortcuts, launchers and menu entries for firefox to "aoss firefox" instead of "firefox". 

(You might need to enable universe or multiverse for this)

---

### Post by smoove on 2006-06-26
[QUOTE=Ramses de Norre]
and change the shortcuts, launchers and menu entries for firefox to "aoss firefox" instead of "firefox". 

[/QUOTE]

Sorry how would I do this?

---

### Post by Ramses de Norre on 2006-06-26
I found a better way in the mean time =)
Do ```
sudo gedit /etc/firefox/firefoxrc
``` and change ```
FIREFOX_DSP="none"

```
to
```
FIREFOX_DSP="aoss"

```

---

### Post by smoove on 2006-07-03
Thanks dude, done that, but still no sound :(

---

### Post by smoove on 2006-07-04
bump

---

