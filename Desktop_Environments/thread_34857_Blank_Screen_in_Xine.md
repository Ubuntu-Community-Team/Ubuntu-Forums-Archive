---
title: "Blank Screen in Xine"
date: 2005-05-16
forum: Desktop Environments
---

### Post by mrscintilla on 2005-05-16
installed i386, ran the automated script to grab all the codecs.  played couple .wmv, .mpeg, etc.   sound is fine but the video in xine is all blank.    My totem crashes always. 

I can play movies inside firefox fine.  

ANy ideas what is going on?



My video card is nvidia 6600.  I installed nvidia-glx and nvidia-setting from Synaptic. but given that I can see videos inside firefox, I don't suspect the video drivers to be the problem.

---

### Post by cdhotfire on 2005-05-16
for totem
```

$ sudo apt-get install totem-xine

```

only try vlc, best video player out there.:)

---

### Post by mrscintilla on 2005-05-16
totem-xine is already installed.  just installed vlc, and it crashed within 2 seconds of opening a video file.

What's up with my system?

---

### Post by cdhotfire on 2005-05-16
run vlc, on terminal and then wait till it crashes and post the output in the terminal.

---

### Post by mrscintilla on 2005-05-18
[QUOTE=cdhotfire]run vlc, on terminal and then wait till it crashes and post the output in the terminal.[/QUOTE]

I ran the sudo dkpg...., xorg-xserv command, and the problem is now fixed. The lessons here is that I had to reconfigure xorg after I installed the nvidia driver.

One more thing, does anyone know why xine doesn't play sound when I have another program with sound on?   Is it a known issue with xine?

---

