---
title: "installing realplayer..."
date: 2005-12-17
forum: General Help
---

### Post by medya on 2005-12-17
hey peopel , I tried to make this problem solved in begginer section, but it wasnt.

I want to install reall player , and i dont have internet in linux, because I cant install my Zoltrix Smart Spirt Ineternal modem .

I want to know, if there is RealPlayer or other programs in Ubunutu's CD ? if not why not ? dont you know that I am in a poor country and I have dial up internet and I can not download everything ?


by the way I downloaded the RealPlayer's RPM file thorugh my windows intenret and moved it to linux drive by a USB Memory.

I was told by ppl in this forum , to convert RPM to DEB, with Allien, after a lot of  headaches I installed Allien, and I converted RPM to DEB , but still I dont have RealPlayer.

---

### Post by aysiu on 2005-12-17
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by medya on 2005-12-17
[QUOTE=aysiu][https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)[/QUOTE]

whats that link ....

---

### Post by doitashimashite on 2005-12-17
You can install the .deb by entering

sudo dpkg -i <deb filename>

or you could install from the rpm file as well (using alien):

sudo alien -i <rpm filename>

Good luck

---

### Post by medya on 2005-12-18
[QUOTE=doitashimashite]You can install the .deb by entering

sudo dpkg -i <deb filename>

or you could install from the rpm file as well (using alien):

sudo alien -i <rpm filename>

Good luck[/QUOTE]


I did that commands ...what to do after that ?

---

### Post by doitashimashite on 2005-12-18
Enter:

realplay

from the command line, or type it in with ALT-F2 from the desktop.

---

### Post by Rackerz on 2005-12-18
Command line = Terminal/Konsole if you wanted to know.

Also doitashimashite, thanks for the command for installing rpms using alien, didn't know you could do that :).

---

### Post by medya on 2005-12-18
i entered the realplay in the command line. .doenst work.

---

### Post by Rackerz on 2005-12-18
Try 'realplayer'

---

### Post by medya on 2005-12-18
i tried that tooo....I just found out my linux doenst run any SH file..

for example i downloade Scanmodem to reconginze my modem...but i cant run that either,,,

when I click on SH files...nothing happens...why is that ?

---

### Post by Swab on 2005-12-18
[QUOTE=medya]i tried that tooo....I just found out my linux doenst run any SH file..

for example i downloade Scanmodem to reconginze my modem...but i cant run that either,,,

when I click on SH files...nothing happens...why is that ?[/QUOTE]

Why would something happen when you click on them?

---

### Post by medya on 2005-12-18
[QUOTE=Swab]Why would something happen when you click on them?[/QUOTE]


in red hat linux, I used to click on the ScanModem.sh file and it used to run ...
but now I can not run that file..the realplayer has the same file ...realplay.

how should I run files in ubuntu?

whit which command ? is there any palce that teach me some usefull , commands... I know none of the commands of terminal...

for example how to run a file.

---

### Post by Swab on 2005-12-18
[QUOTE=medya]in red hat linux, I used to click on the ScanModem.sh file and it used to run ...
but now I can not run that file..the realplayer has the same file ...realplay.

how should I run files in ubuntu?

whit which command ? is there any palce that teach me some usefull , commands... I know none of the commands of terminal...

for example how to run a file.[/QUOTE]

./filename.sh

For Realplayer I downloaded from [here]("http://www.real.com/linux?pcode=rn&src=freeplayer_partner&opage=freeplayer_partner") and followed their instructions.

---

### Post by medya on 2006-01-21
hey after months from starting this topic , my problem has solved.let tell you a brief about my problem :

I couldnt install my modem, so I downloaded the Real Player's RPM (redhat file type) by my windows internet , I made .RPM file install-able by allien, I installed the realplayer  on ubuntu. it was added and was checked in my list of resporiters..(or whatever the spell is) ..but I couldnt run it,


today after months I bought a cheap External 14.4 modem . (very slow) and it works with ubuntu, I uninstalled the former RealPlayer and added the program through Ubunutu's ADD PRGORAM , it took several hours to download the things.

after that , it was added to my program list , but when I click on it , the cpu do somethng but it neverr runs...

 whats should i do ?

---

### Post by medya on 2006-01-21
hey after months from starting this topic , my problem has solved.let tell you a brief about my problem :

I couldnt install my modem, so I downloaded the Real Player's RPM (redhat file type) by my windows internet , I made .RPM file install-able by allien, I installed the realplayer  on ubuntu. it was added and was checked in my list of resporiters..(or whatever the spell is) ..but I couldnt run it,


today after months I bought a cheap External 14.4 modem . (very slow) and it works with ubuntu, I uninstalled the former RealPlayer and added the program through Ubunutu's ADD PRGORAM , it took several hours to download the things.

after that , it was added to my program list , but when I click on it , the cpu do somethng but it neverr runs...

 whats should i do ?

---

### Post by Noelinho on 2006-01-25
I have the same problem - it appears in applications --> sound and video --> realplayer. You click, and it bring up a pane in the taskbar saying 'starting realplayer', and after about 10 seconds, it vanishes.

---

### Post by AirIntake on 2006-01-25
The easiest way to install RealPlayer is to go to [www.real.com](www.real.com) and download their RealPlayer10GOLD.bin install file. Do this in the directory you downloaded it to:
```
sudo chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```
and RealPlayer 10 will install and work no problem.

All linux installs that aren't in a repository should be this simple.

---

### Post by medya on 2006-01-25
>  	The easiest way to install RealPlayer is to go to [www.real.com](www.real.com) and download their RealPlayer10GOLD.bin install file. Do this in the directory you downloaded it to:
Code:

sudo chmod a+x RealPlayer10GOLD.bin sudo ./RealPlayer10GOLD.bin
NO NO NO !
> and RealPlayer 10 will install and work no problem.

NO NO NO !

I had done that but .. I got error !

you are right thats the easiet way but the complete code is this :
cd ~/Desktop
**sudo apt-get install libstdc++5**
chmod +x RealPlayer10Gold.bin
sudo ./RealPlayerGold.bin


the best way to learn installing real player is WIKI
[https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28realplayer%29](https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28realplayer%29)

---

### Post by AirIntake on 2006-01-25
I must have already had that library installed, as I didn't get any errors. It's funny that Real.com didn't mention it as being needed. Oh well, at least the Wiki knows about it. It's good that you got it working!

---

