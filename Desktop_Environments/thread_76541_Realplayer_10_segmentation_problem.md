---
title: "Realplayer 10 segmentation problem"
date: 2005-10-15
forum: Desktop Environments
---

### Post by jerryhao on 2005-10-15
after runing, it shows:

line 75: 13886 Segmentation fault      $REALPLAYBIN "$@"

what is the problem? 

i just want my totem to support rm and rmvb playing, how can i do it please?

---

### Post by Abiezer on 2005-10-15
Same here. RealPlayer appears to start, but attempting to open a file or location gives an error message such as
```
/usr/bin/realplay: line 75: 24074 Segmentation fault      $REALPLAYBIN "$@"
```
I reinstalled from the downloaded .bin file but that hasn't helped.

Jerry - can i assume from your name that you're using an Asian locale too? I wonder if that's related? I got some error messages during upgrade that didn't seem to like the fact that I work in both English and Chinese.

---

### Post by jerryhao on 2005-10-15
yup i am from China, my breezy version is a fresh installed one, and my locale is set to English, i don't think the locale will make the problem

---

### Post by jerryhao on 2005-10-15
i have download realplayer 8 version from real.com and installed it, guess what, it works....but it says cannot open the audio device, another application maybe using it, and i have closed all runing program even restart, still there is no audio

---

### Post by Abiezer on 2005-10-15
I downloaded the rpm and tried using the installer in Synaptic and that fails too. Any other suggestions welcome.

---

### Post by Abiezer on 2005-10-15
Googling more with the error message doesn't give a solution as such but suggest it's related to a conflict with SCIM, the multilingual input method, which might explain why both Jerry and I in China have the issue. Now to see if that can be sorted.

Following the advice [here]("http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started"), I find that cd'ing to the RealPlayer directory and then doing
```
~/RealPlayer$ GTK_IM_MODULE=xim ./realplay
``` gives an instance of Realplayer that works.

Then did ```
 sudo gedit ~/RealPlayer/realplay
``` and appended the line he gives```
export GTK_IM_MODULE=xim
```
Now its seems to be working!

---

### Post by jerryhao on 2005-10-15
oooooooooooops, it works, but i still have this problem:

Cannot open the audio device. Another application may be using it.

faint!

---

