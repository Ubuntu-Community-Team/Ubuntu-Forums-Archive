---
title: "Ubuntu 12.04 LTS 3d games with  blackscreen with sound"
date: 2012-12-18
forum: Gaming &amp; Leisure
---

### Post by JuicyJewz on 2012-12-18
I am a total newbie when it comes to ubuntu and linux, so anyhelp with my question would be much appreciated.  I have a Acer Aspire one netbook that can run some 3d games on windows 7 but none on Ubuntu. Everytime I download one (tremulous, open arena, alien arena, ect) it goes to fullscreen and totally black. I have sound from the games but cannot see any. I thought this might be because my netbook is hooked up to a tv for a screen (since my netbooks screen is broken) and the resolution is too high, however I have no idea how to make the resolution smaller. I am only assuming this is the problem. As car as my systems hardware I have Intel® Atom™ CPU N450 @ 1.66GHz × 2 with a 32x operating system. It says my graphics are unknown, but they are intergrated. Please help!

---

### Post by Bashing-om on 2012-12-18
JuicyJewz; Hi ! Welcome to the forum .

Is the only problem experienced when attempting to run these games ???
Are these "games" native to windows that you are trying to run in a linux environment ?
[INDENT](Don't know much about games)
[/INDENT]

[INDENT][INDENT]would like to help, but ? <== BDQ

[/INDENT][/INDENT]

---

### Post by JuicyJewz on 2012-12-20
I do believe these games a native. Like I said I am a totally noobie at linux and besides this problem I choose linux over windows anyday! Some of the games are Alien Arena, Urban Terror, and Tremulous. Now the funny thing about Tremulous is that I downloaded it on 3 different operating systems. The first one was Windows 7. It worked fine on windows 7 (and even on my acer aspire One netbook) Then I got Joli OS 1.2 dual booted with windows 7 and I ran into the black screen promblem. Joli Os is ubuntu based. I had sound but had to restart my whole computer just to get back to the menue once the game was up. So I got rid of Joli OS 1.2 (many reasons, but this being one of the main ones) and got Ubuntu. Now on ubuntu I tried downloading it first from  the Ubuntu store. I got the same results I got with Joli os however, if I pressed the windows key and it brought me to my unity 3d app menue I could click on Tremulous and see and hear the main menue for about 3 seconds before it went back to full screen. Is there a way to make all my games load and pop up in a "windowed controlled box" with the x menue?

Please and thank you for your time. I love the Ubuntu community help!

---

### Post by Bashing-om on 2012-12-20
JuicyJewz;

Let's look; To see your graphics card and info:
terminal codes:
```
sudo lshw -C display
lspci -nnk | grep -iA3
```Maybe your graphics cards is not hoss 'nuff to run higher end games ?
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

