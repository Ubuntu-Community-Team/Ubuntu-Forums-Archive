---
title: "Resolution is too high for my screen."
date: 2008-05-18
forum: Gaming &amp; Leisure
---

### Post by luke949 on 2008-05-18
Hi everyone!

    I have a problem. Two games that I have are set on too high of a resolution for my screen to even show! The two games are Tremulous and Counter-Strike Source via Wine. Is there any way I can change the resolutions without entering the games themselves? 


Thanks!

---

### Post by Jammy4041 on 2008-05-18
Is it just when you play the games? If so your wine setting is probably set too high. It might be in the Wine Configuration under Default Resolution or something.

if it's not, then try changing the resoultion of Ubuntu itself (System>>Administartion>>Screens and Graphics or System>.Preferences>>Screen Resolution)

Sorry to be so vague, but I'm using Windows at the moment.

---

### Post by luke949 on 2008-05-18
well, Counter-strike 1.6 starts up in a resolution my screen can display, so its really only tremulous and counter-strike source.

---

### Post by luke949 on 2008-05-18
Ok I tried running it in a virtual desktop, but all I get is a black box.

---

### Post by luke949 on 2008-05-18
I tried removing and reinstalling Tremulous, but it still starts up in a higher resolution.

---

### Post by Perfect Storm on 2008-05-18
Try look for their configuration files in your home folder (hidden). You can open the config files with an editor and change the resolution of tremolous.

---

### Post by luke949 on 2008-05-18
I fished through the files and I found a cfg file in Tremulous. I found seta r_customwidth "1600" and seta r_customheight "1024" And I changed them to 
seta r_customwidth "768" and seta r_customheight "1024". But my screen is still unable to display it. And the desktop resolution is set at 1280 x 1024

---

### Post by Perfect Storm on 2008-05-18
Try set it to your actually desktop resolution.

---

### Post by luke949 on 2008-05-18
Ok i fixed CSS. I pasted -dxlevel 70 into the launch options. So tremulous is just the problem now.

---

### Post by luke949 on 2008-05-18
Ok I got css to run in virtual destop, but I can only get it to run in virtual desktop. When trying to start it noramlly, my screen says its over range. Also, in virtual desktop, I'm getting a slight sound delay in css.

---

