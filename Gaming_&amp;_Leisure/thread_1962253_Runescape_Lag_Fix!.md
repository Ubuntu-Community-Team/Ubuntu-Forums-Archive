---
title: "Runescape Lag Fix!"
date: 2012-04-20
forum: Gaming &amp; Leisure
---

### Post by LinuxCharms on 2012-04-20
In my desperate attempts today to get RS to work in my Chrome browser without massive lag, I became fed up. Therefor, I went looking for something to fix it. And did I find just the thing!
What you'll need for this:
Perl (Software Center)
Perl FindBin Module (Software Center)
p7zip (Software Center)
Windows Runescape Download Client (From RS Website)

Now I'll assume you have all of this now, and we'll pop right into the installing process. Don't worry, It's **REALLY** simple.

Run (In A Terminal):
```
wget http://dl.dropbox.$(echo -e "\x63\x6f\x6d" )/u/11631899/opensource/Perl/unix-runescape-client.tar.gz && tar -vxzf unix-runescape-client.tar.gz 
```

Then:
```
~/runescape/install-desktop-icons
```

-----
After all of this is done, you just need to go into your Applications, look under "Games" then hit Runescape from the menu. This will open up a small prompt and you will follow the instructions. When it asks for you to choose a number, just type "1", without the "".
Then it will do some downloading and will ask you a few more questions. Just type "Y" to them all.
BAM. You now have your own Runescape Client without massive browser and java lag and can play freely from your desktop.

All credit for this goes to HikariKnight, whom put it all together. This man is amazing.

Questions? Ask. (:
Happy playing.

---

### Post by IWantFroyo on 2012-04-20
Nice guide. I used to be pretty intensely into RuneScape before I switched to Linux. I might start playing again now, thanks to you.
Haven't tried it yet, but I'm planning to shortly.

Suggestion, you can use the [code] [/code tags (last ] left off on purpose) for terminal commands. Not particularly important, but generally appreciated.

---

### Post by Dlambert on 2012-04-20
Cool!

---

### Post by syko2277 on 2012-05-13
hello i am having a problem with it it says that it could not find 

sh: 7z: not found
sh: 7z: not found
sh: 7z: not found
sh: 7z: not found

could you tell me what this means as i would like to play runescape on my computer

---

### Post by doorknob60 on 2012-05-13
> **syko2277 said:**
> hello i am having a problem with it it says that it could not find 

sh: 7z: not found
sh: 7z: not found
sh: 7z: not found
sh: 7z: not found

could you tell me what this means as i would like to play runescape on my computer
It means you don't have p7zip installed. Install it from the software center or this link should work too: [Click]("apt:p7zip")

---

### Post by syko2277 on 2012-05-13
> **doorknob60 said:**
> It means you don't have p7zip installed. Install it from the software center or this link should work too: [Click]("apt:p7zip")

i clicked the click button and it said i already have it installed so i uninstalled it and then reinstalled it but it still say it can not find them

---

### Post by HikariKnight on 2012-05-15
the info is slightly wrong
you need the [p7zip-full]("apt:p7zip-full") package ;)

however the client still requires sun/oracle java OR openjdk6 or openjdk7
the client also fixes some library linking issues that java7/openjdk7 suffers from.

for the same fix for browsers just check my post on the linux thread in the runescape forum :)
[http://services.runescape.com/m=forum/forums.ws?25,26,99,61985129,2850,315804921,goto,286#2850](http://services.runescape.com/m=forum/forums.ws?25,26,99,61985129,2850,315804921,goto,286#2850)

happy scaping :)
PS: yes it is me

---

