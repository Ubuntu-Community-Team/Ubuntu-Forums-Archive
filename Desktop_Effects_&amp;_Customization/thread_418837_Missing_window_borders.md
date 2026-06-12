---
title: "Missing window borders"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by jsiii on 2007-04-22
Hello.

I am missing window borders so I cannot move nor resize windows. I am not using Beryl or Compiz or whatever. I have ATI.

When I run the failsafe Gnome session everything works.

Thanks for any help.

---

### Post by Neuralgia on 2007-04-22
this is the same problem as here [http://ubuntuforums.org/showthread.php?t=418489](http://ubuntuforums.org/showthread.php?t=418489)

please any advice?

---

### Post by iceclow on 2007-04-22
That is exactly the same problem I have. It differs from the other posts in the fact that this is a feisty fresh install. When I turned on the effects they worked flawlessly but after a reboot I lost all the title bars of the window.

I know desktop effects are in early stages, however I hope this feedback be useful to the development team.

---

### Post by jsiii on 2007-04-22
I actually never changed anything about graphics at all. I never used destop effects. I only installed few applications like Amarok and I tried to make my surround sound work and suddenly, after one restart, I got this problem. It surely is related to sessions. Maybe some bug or something. Since this started to happen, I noticed one more thing. Everytime I run session affected by this bug, Nautilus window is loaded with one particular folder. And I can not get rid of this too :-/

---

### Post by braveerudite on 2007-04-22
This happens to me too but after I sudo nvidia-settings.  After I apply the nvidia settings I pick everything turns in to %$#@!

My solution:

Re isntall Ubuntu and not do sudo nvidia-settings

---

### Post by Rinzwind on 2007-04-22
This solved it for me:
[http://ubuntuforums.org/showthread.php?t=418550](http://ubuntuforums.org/showthread.php?t=418550)

---

### Post by jsiii on 2007-04-23
Thanks for the link. It however is not applicable for my needs as I don't have Beryl. I have tried to reinstall and reconfigure ATI drivers which resulted in the complete loss of display. Sigh...

I am now downloading 32bit Ubuntu and am thinking about Kubuntu and maybe any other different Linux distro. Do you think that Kubuntu may resolve the problem? I mean, is it different enough to solve my problems with graphics?

**UPDATE** - Yesterday, I installed openSUSE and so far, I am quite happy with it. I already had some problems and was able to fix them. I am not saying I dislike Ubuntu, but openSUSE did much better job. Anyway. Ubuntu, thank you for bringing me to linux :-)

---

### Post by DracoPsycho on 2007-04-23
You should add this to your xorg.conf under the screen section

```
Option "AddARGBGLXVisuals" "true"
```

It worked for me.

---

### Post by sjb2h on 2007-04-24
Just wanted to say I am experiencing the same problem. I just nuked my xorg.conf file, so I'm going to try to repair it and add that option line. I'll let you guys know if it works!

---

### Post by sjb2h on 2007-04-24
I found this on the Ubuntu forums (cannot remember which post, as I passed it hours ago) that should solve your problem.

Open the Terminal and type
```
metacity
```
Then go to System -> Preferences -> Session, and save the changes to the current session. This should resolve the problem. A big thanks to whoever originally posted this!

---

### Post by corstar on 2007-04-30
this fixed it for me too. I am using feisty and window borders died after enabling desktop effects.

---

### Post by djen9999 on 2007-05-15
Thanks guys, this worked for me as well.

---

