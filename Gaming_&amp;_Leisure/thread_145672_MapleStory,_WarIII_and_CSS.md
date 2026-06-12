---
title: "MapleStory, WarIII and CS:S?"
date: 2006-03-16
forum: Gaming &amp; Leisure
---

### Post by BobElBuildero on 2006-03-16
For maplestory i the site has to be accessed using internet explorer, but Avant Browser gets past that. however that too is an .exe file and i am completely oblivious as to how to install .exe on linux. my brother switched this computer from windows earlier in the week because of the ever frequent "blue screen of death". is there a way for Wine to open any .exe file, not just games, and if so, can someone "halp meh"? ;)

---

### Post by Jucato on 2006-03-16
If you have wine installed, you can open up a terminal, go to the directory of the .exe file and type:
```
wine *filename.exe*
```
I'm not sure how wine will behave if you double-click on the .exe file in Nautilus (I'm using Kubuntu).

About Maplestory, I'm not sure if it will work. Most MMORPGs that use GameGuard don't usually work in Wine. There might be some hack around it though. 

(And if ever you find a solution, could you kindly send me a PM? I'd like to play this one in Linux, too. :D)

---

### Post by dpaint4 on 2006-03-17
Maple Story *would* run under Wine, but they have hack checker and it thinks that the game has been hacked when you're running in Wine, and won't let you play.

Sad. I'd love to access that.

I've been playing Cave Story. The English patched version runs *perfectly* under Wine when you set the sound mode to full emulation.

---

### Post by lordofkhemenu on 2006-03-17
[quote=BobElBuildero]For maplestory i the site has to be accessed using internet explorer, but Avant Browser gets past that. however that too is an .exe file and i am completely oblivious as to how to install .exe on linux. my brother switched this computer from windows earlier in the week because of the ever frequent "blue screen of death". is there a way for Wine to open any .exe file, not just games, and if so, can someone "halp meh"? ;)[/quote]
Just an FYI - Avast **IS** Internet Explorer but with a pretty face (it uses the Internet Explorer html rendering engine, so it requires the same dlls, etc that IE does).

---

### Post by BobElBuildero on 2006-03-18
so ive followed the instructions from WineHQ.com for Ubuntu. i'm pretty sure the latest version of wine is on my computer now. ive seen the applications available but the instructions for those specific application arent quite clear. i havent seen a way to view the files from cds such as StarCraft so i still dont know the name of the .exe to add to the terminal. someone help? Badger v5.1 if that helps any.

---

### Post by FizDev on 2006-03-18
Insert cdrom, an icon should appear on your desktop.
Open it, and then right-click on the .exe you want to run, select "Open with Other Application"
in the Custom Command, write "wine" then press OK.

If you want to do this in the terminal :
Just insert the cdrom and then type :
```
cd /cdrom
```
```
ls
```
```
wine nameoftheexe.exe
```

---

### Post by Chozabu on 2006-03-19
if you right-click, and open with wine - would it not leave the working path as your home dir and not be able to find the files?

---

