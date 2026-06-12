---
title: "Gaim - No sound after update"
date: 2006-11-23
forum: Desktop Environments
---

### Post by DimitrisC on 2006-11-23
I installed gaim 2 beta 5 as explained in this howto (i had gaim 2 beta 3 before) [http://neoaddict.wordpress.com/2006/11/10/build-gaim-200-beta-5-from-source/](http://neoaddict.wordpress.com/2006/11/10/build-gaim-200-beta-5-from-source/) and it works except one problem.  No sound.  In the sound options there is no more the "Automatic" option.  Only system beep, command and no sound options.  Is there a way to enable sound? :-k

---

### Post by Jimmey on 2006-11-23
If you compliled the source, you'll need to have the apropriate development packages installed.

There are many methods Gaim can use to make the sounds. Esd and Alsa being among them. You want to make sure the development packages are installed for both of these if you want sound. So:

> apt-cache search esd dev
> apt-cache search alsa dev

Install the stuff that looks right, and re-compile.

[EDIT]

I remember having the same problem. I was advised to install gstreamer's development packages...You might want to try that. It'll probably be something like "gstreamer0.10-dev".

---

### Post by Qew on 2006-11-23
You can select "command" in the drop-down and type in "aplay -q %s" (no quotes) into the box.

---

### Post by DimitrisC on 2006-11-23
Thank you both for your help!  I tried the command method suggested by Qew (too lazy to install new packages and recompile :-D ) and now i have sound in gaim!!!! 

Thanks again!
Another problem solved with the help of all the people in these forums! Ubuntu forums and the whole ubuntu community is simply the best! :-D

---

