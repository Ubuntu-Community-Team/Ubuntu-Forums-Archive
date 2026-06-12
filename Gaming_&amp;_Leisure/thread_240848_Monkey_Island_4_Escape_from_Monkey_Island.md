---
title: "Monkey Island 4: Escape from Monkey Island"
date: 2006-08-21
forum: Gaming &amp; Leisure
---

### Post by peabody on 2006-08-21
I was wondering if anyone had managed to get this game working.  Google seems to indicate that this game is supported in cedega.  I installed the userfolder version of cedega via this guide:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Cedega%20CVS](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Cedega%20CVS)

Which seemed to go without a hitch.  However, I'm having two problems with getting Monkey Island 4 to work:

1) One is the installation.  If I try and do a full install, it gets through it until it asks for the second CD at which point nothing I try gets Linux to reliquish the CD.  Launching cvscedega with --monitor-cdrom-eject doesn't seem to help.

2) I can get around this by doing a minimal install which only requires the first cd.  However, upon launching the game with the following:

```

cvscedega "C:/Program Files/monkey4/Monke.exe" -- -gl

```

The game plays and gets to the video sequeces.  However, the video sequence is very choppy and slow.  Pressing esc to quit the video sequence seems to hang the game.  Waiting for the sequence to finish has the same effect.  I have to switch to a VT and kill the wine process.

I have a Radeon 9000 64MB with the fglrx drivers installed, version 8.28.8.  glxinfo shows direct rendering enabled.  I have the following in my device section of my xorg.conf:

```
Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "UseInternalAGPGART" "no"
        #Option      "KernelModuleParm" "agplock=0"
EndSection

```

Any and all advice appreciated.

---

### Post by idrinkwhisky on 2006-12-22
hey,

i got this game to work with the beta version of crossover office.
All i had to do was 
1)pop in cd1 and run crossover. 
2)select the minimum install 195 MB.

3) note that switching to cd 2 is a bit weird. While trying to do fullinstall it didn't work but with the 195mb install it did.
Just click on eject cd in the crossover menu. Pop in cd2 wait till ubuntu recognizes it and only then click continue. 

4) open monkey island and in options switch graphics to OpenGL instead of direct. 

hope it works for you

---

### Post by hyperactive on 2007-01-11
Hello I am stuck in the game right now. I am on the island with the bank and the lawyers. I am supposed to get a prothetic hand out of a pink basket but it wont let me. When I walk to it it will only diplay the option to look at the wooden leg and nothing else. It shows the option to look at the wooden hand but it wont let me. Please help!

---

