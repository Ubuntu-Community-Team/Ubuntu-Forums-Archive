---
title: "xorg.conf and monitor damage"
date: 2009-04-27
forum: General Help
---

### Post by Barmaleychik on 2009-04-27
I red several times in this forums that if I put wrong data into xorg.conf file I can damage my monitor permanently. What should I look for while editing the file?

---

### Post by joeyknuccione on 2009-04-27
> **Barmaleychik said:**
> I red several times in this forums that if I put wrong data into xorg.conf file I can damage my monitor permanently. What should I look for while editing the file?
First and always make a backup, I also prefer to have a backup of the backup in my home folder under "MyBackups", just in case something gets really crazy.

Also, I recommend using your card's config editor when possible.

In regards to what you can and can't put in xorg, notice what is already there when you start to edit, and if a new command looks really out of place, thoroughly research it before you use it.

Also keep in mind the use of double quotes, and where and when they apply.

---

### Post by RazVayne on 2009-04-27
Don't forget to read your monitor's User's Manual!

---

### Post by ddrichardson on 2009-04-27
It is possible but most modern monitors will switch off if they don't care for the signal they're receiving - what is it you're trying to do.

---

### Post by Thelasko on 2009-04-27
> **Barmaleychik said:**
> What should I look for while editing the file?

In general, you shouldn't edit xorg.conf at all.  There are only a few occasions where it's justified.  [Here are some nice instructions to help you on your way.]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2#Summing_up")

---

### Post by Barmaleychik on 2009-04-27
Thank you guys, you gave me very important information; I feel that I am getting better with Linux. However, nobody gave a definite answer: 

a) can one damage a monitor in Ubuntu or modern monitors are well protected? (I have SyncMaster 204T
b)If yes, then WHAT can damage a monitor?

Thank you in advance

---

### Post by mcduck on 2009-04-27
> **Barmaleychik said:**
> Thank you guys, you gave me very important information; I feel that I am getting better with Linux. However, nobody gave a definite answer: 

a) can one damage a monitor in Ubuntu or modern monitors are well protected? (I have SyncMaster 204T
b)If yes, then WHAT can damage a monitor?

Thank you in advance

a) It's not likely with modern monitors, but yes, you can damage a monitor with wrong settings. Not only with Ubuntu but with any OS/tool that allows you to freely configure your graphics.

b)Too high resolution and/or refresh rate. Most likely the monitor will just turn off the picture and instead display a message about not supported frequency or something like that, but in worst case trying to use way too high resolution/frequency might break the monitor.

---

### Post by Thelasko on 2009-04-27
Well, when I started using Ubuntu back in Feisty Fawn, I configured the xorg.conf file by hand.  I made quite a few mistakes and never broke the monitor.  Usually one of three things happened:

[LIST=1]
[*]Gnome didn't load
[*]The image was unreadable
[*]My monitor displayed a message that its input was incorrect (it still displayed an image though)
[/LIST]

---

### Post by ddrichardson on 2009-04-27
Really, the frequencies being sent to the monitor could be outside it's limits but this is mainly true of CRT monitors. CRT monitors use an electron gun and deflector plates, if rates were too high then it can cause all sorts of problems, depending on how technical you want to get.

For all intents and purposes this is not going to happen on a modern monitor (anything in the last ten years should be capable of detecting a bad input signal).

---

