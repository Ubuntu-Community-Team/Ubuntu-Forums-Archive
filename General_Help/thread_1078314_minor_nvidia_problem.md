---
title: "minor nvidia problem"
date: 2009-02-23
forum: General Help
---

### Post by sigurnjak on 2009-02-23
As of yesterday i am having this message when i tried to run glxgears :
andrey@andrey-desktop:~$ glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
andrey@andrey-desktop:~$ 


Btw i am using proprietary drivers and do not think i have any other issues , it boots fine , x is ok  . What should i do to fix this little annoyance ?

---

### Post by jbrown96 on 2009-02-23
You need a "glx" section in your xorg.conf. Make sure that you have a section like this in /etc/X11/xorg.conf

> Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection


---

### Post by sigurnjak on 2009-02-24
Tx for a reply and sorry it took so long to get back to you .
I tried adding that bit to my xorg.conf but it didn't make any difference even after reboot . 
Do you have any other suggestions . I tried reinstalling nvidia drivers , but no luck !

---

### Post by sigurnjak on 2009-02-24
O.k. here is what i have done so far .
I run sudo nvidia-xconf and reset x , reboot and glx is fine .
On the other hand now my gdm and boot screen and nvidia logo  during boot are way out of proportions . How do i set them  to defaults ! 
Ah . progress is slow and educating experience ! :lol::lol:

---

### Post by fooman on 2009-02-24
you could try using startupmanager to adjust the boot screens resolution, see if that does the trick.

open a terminal and type or copy/paste the following:

```
sudo apt-get install startupmanager
```

after it installs,  find it in system > administration > startup-manager.  under the boot options tab you will find the options for display resolution.

hope that helps.

---

### Post by sigurnjak on 2009-02-26
Hi there ! Sorry it took so long to get back to you !
Yes , i tried startup manager and no luck . It makes my ubuntu logo better  , but gdm is still huge and so is nvidia logo  . I guess i am lucky i have autologin and timed login set .

---

### Post by stim on 2009-02-26
I've said this elsewhere on these forums and I will say it again here: I have used Envy for my 8800GTX since the day I got the system and it has worked flawlessly the entire time.  It will download the latest drivers, install and configure them automatically.  Additional configuration can then be done through the nvidia drivers tool.  I HIGHLY recommend checking it out.

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by sigurnjak on 2009-02-27
I have tried ENVY ! now i have newer drivers  , little better score with glxgears and darn gdm is still out of whack ! .:lolflag:

Like i said it is a little annoyance but hunting it down is becoming frustrating  ! :confused:

Maybe i will just leave it  until next upgrade in April .

---

