---
title: "I think Ive destroyed my desktop.. and a couple of other things..."
date: 2006-06-17
forum: Desktop Environments
---

### Post by w1z4rd on 2006-06-17
I think I messed up big time with my desktop (that I had just leetified) Last night I was pretty trashed and installing a couple of applications from resiviours a noob like me should not be touching.

I was using adept for something, then, um  arp-get wouldnt work, and then I messed up my sources list, and somewhere in all of this my KDE has stopped working. It just kinda loads up and then hangs, im not to sure what to do :/

I tried to run that command it tells you to to run to fix xorg.conf file... and since Ive installed XGL and compwiz, I think I have only messed it up more.

Well, needless to say, Im totally lost, and not to sure what to do. Im writing this from a breazy badger CD I had lying around.

---

### Post by aysiu on 2006-06-17
Are you able to log into at least a terminal mode (black screen, white text, no graphics)?

Or is it so broken it won't even boot?

---

### Post by w1z4rd on 2006-06-17
[QUOTE=aysiu]Are you able to log into at least a terminal mode (black screen, white text, no graphics)?

Or is it so broken it won't even boot?[/QUOTE]

Yeah, I can login with everyhing but I suppose X. I have command line with network support.

---

### Post by aysiu on 2006-06-17
Well, the first thing I'd do is type ```
sudo apt-get -f install
``` and see if you can fix the broken packages. Then I'd do a ```
sudo dpkg-reconfigure xserver-xorg
``` and stay conservative (for now) with the screen resolution just until you can get everything working. If that seems to well then you can try ```
sudo /etc/init.d/kdm start
``` Good luck.

---

### Post by w1z4rd on 2006-06-17
thanks, will give it a shot and let you know how it goes when i get into the office just now.

---

### Post by w1z4rd on 2006-06-17
[QUOTE=aysiu]Well, the first thing I'd do is type ```
sudo apt-get -f install
``` and see if you can fix the broken packages. Then I'd do a ```
sudo dpkg-reconfigure xserver-xorg
``` and stay conservative (for now) with the screen resolution just until you can get everything working. If that seems to well then you can try ```
sudo /etc/init.d/kdm start
``` Good luck.[/QUOTE]


when i run the dpkg command, i get an error message telling me  xserver-xorg is not installed. Um...  where do I go now?

---

### Post by aysiu on 2006-06-17
Hm. Try this and see if it works. ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by w1z4rd on 2006-06-17
[QUOTE=aysiu]Hm. Try this and see if it works. ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```[/QUOTE]

I did this... still get told that im missing  xserver-xorg

---

### Post by aysiu on 2006-06-17
I'm stumped, then.

---

### Post by w1z4rd on 2006-06-17
bugger :/ hmmmm.... I dont want to reinstall *sigh*.

---

### Post by aysiu on 2006-06-17
Maybe someone else will be able to jump in with a brilliant suggestion.

---

### Post by yteh on 2006-06-17
w1z4rd.... I'm not an expert but would like to see if I can help. Do still have your xorg.conf file correct? If so, could you post the contents?

Also, not sure whether this will help or make things worse but maybe re-install xserver-xorg?

---

### Post by raptros-v76 on 2006-06-17
ive seen this before. hmm. the problem sounds like X is gone. uhh. try sudo aptitude install xserver-xorg. dont be afraid of anything that happens though. when i dealt with it, i got a kernel panic mode error right before everything was working again

---

### Post by w1z4rd on 2006-06-17
[QUOTE=raptros-v76]ive seen this before. hmm. the problem sounds like X is gone. uhh. try sudo aptitude install xserver-xorg. dont be afraid of anything that happens though. when i dealt with it, i got a kernel panic mode error right before everything was working again[/QUOTE]

How would I resintall xserver-xorg (thanks for the help)?

---

### Post by raptros-v76 on 2006-06-17
try:
```
sudo aptitude update&&sudo aptitude install xserver-xorg
```

---

### Post by w1z4rd on 2006-06-17
[QUOTE=raptros-v76]try:
```
sudo aptitude update&&sudo aptitude install xserver-xorg
```[/QUOTE]


You guys rawk! thanks guys, got my desktop up and running, and will work on getting the XGL implimented on monday. No more live CD and all my settings back! w00t!

---

### Post by raptros-v76 on 2006-06-17
this problem has been cropping up everywhere. i dont know what it is, but many people have been losing X. any time someone has this problem, reccomend what i said. it seems to work

---

