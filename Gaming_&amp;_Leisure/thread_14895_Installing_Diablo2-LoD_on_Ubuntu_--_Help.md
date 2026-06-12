---
title: "Installing Diablo2-LoD on Ubuntu -- Help"
date: 2005-02-10
forum: Gaming &amp; Leisure
---

### Post by linuxNewb on 2005-02-10
I am a linux newb, but have taken the plunge and completely wiped XP. I have had little problems adding most of the programs I need, and I'm starting to get used to the Ubuntu (linux) file structure etc., but I'm having real trouble with getting Diablo2 - Lod (for play on Battle.net) installed. I've been reading about WINE (I attemted to install -- but screwed stuff up and had to reinstall Ubuntu entirely). The tutorials I've found  are really vague, seem dated, or assume that the game is already installed (on a windows partition). I have done my 'homework', and researched this for 3-4 hours, but I still don't get what I need to do. I'm lost.

Can someone please provide or direct me to some kind of tutorial that explains how to install WINE then install a game like Diablo2-LoD on Ubuntu. Thank you for your time and attention.

System info: running warty on compaq presario 900 -- everything on the 900 works great with warty 'right outa the box'.

---

### Post by jdodson on 2005-02-10
[QUOTE=linuxNewb]I am a linux newb, but have taken the plunge and completely wiped XP. I have had little problems adding most of the programs I need, and I'm starting to get used to the Ubuntu (linux) file structure etc., but I'm having real trouble with getting Diablo2 - Lod (for play on Battle.net) installed. I've been reading about WINE (I attemted to install -- but screwed stuff up and had to reinstall Ubuntu entirely). The tutorials I've found  are really vague, seem dated, or assume that the game is already installed (on a windows partition). I have done my 'homework', and researched this for 3-4 hours, but I still don't get what I need to do. I'm lost.

Can someone please provide or direct me to some kind of tutorial that explains how to install WINE then install a game like Diablo2-LoD on Ubuntu. Thank you for your time and attention.

System info: running warty on compaq presario 900 -- everything on the 900 works great with warty 'right outa the box'.[/QUOTE]

congratulations and welcome to the club.  sorry to hear about your problems.  i will try to help as best i can.

so make sure you have added the package repositories, this guide is helpful: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

now install wine.

sudo apt-get install wine
sudo apt-get install winesetup 
OR
sudo apt-get install winsetuptk

i forget if it is winesetup or winesetuptk.  

now after they are installed run:

winesetup

for the most part the defaults are fine.  

now you can run wine and pass in setup.exe or install.exe from the diablo CD to install the game.

you have to install a NOCD crack to play under wine as wine does not support windows copy protection.  there is a version of wine built specifically for games called cedega.  [http://www.transgaming.org](http://www.transgaming.org) is the site.  cedega costs $5 a month with a 3 month minimum subscription.  cedega does not require you to run winesetup it does it automagically.

---

### Post by Dylanby on 2005-02-10
There's a small tutorial over at [Frank's Corner](http://frankscorner.org/)

---

### Post by HaloGray on 2005-02-10
Here's a great bit for getting wine into synaptec and keeping it updated along with the rest of your system.  
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Winetools makes setting up wine a breeze and a half.  As well as installing a lot of common windows software (no games for now though).  There's something kind of funny about running IE on a linux system.

In order to install winetools you'll need to get the xdialog packages, which were not in my synaptec list (running hoary).

I found it here:
[http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/x/xdialog/](http://mirror.isp.net.au/ftp/pub/ubuntu/pool/universe/x/xdialog/)

Pick the appropriate .deb package and install it via the command line without issue:
$ alien -i xdialog_2.0.6-3_i386.deb

At that point you should be able to install winetools and setting up wine is easy from there.

---

### Post by satyam on 2005-02-14
Ok, so I installed wine in Warty, and now I'm trying to install Diablo 2 into wine. The Wine setup seemed to run perfectly, I'm getting wine notepad and wine winemine working.
  However, when I try to run the setup for Diablo, I get the error "Program Start Menu not found". As far as I can tell, wine set up the "Windoze" filesystem correctly, the profiles include the start menu folders etc. 
  I get the feeling that there's something I'm missing, but I don't know what it is. Any ideas? Thanks a lot.

---

### Post by trivialpackets on 2005-02-16
I could be wrong, but I believe this is what we meant that Wine does no't support the windows copy protection.  Go to Frank's Corner and set up the NoCD crack that is described there for D2 and you should be good to go.

---

### Post by linuxNewb on 2005-03-30
Your replies have been very helpful, thx. The only problem is that to play on Battle.net, you have to have the latest 1.10 patch installed, but the patch installer checks for the cd also. I have found "no cd" fixes, but I can't find a no cd fix for the 1.10 patch installer itself. Has anyone found a work around for this problem? Thanks.

---

### Post by ante0 on 2005-05-17
LinuxNewb, i've got Diablo 2 to run in single player, but not Battle.net. In order to play it in battle.net you would need to install something called ApiHooks. And about the patcher. it doesnt search for the cd, not on my comp anyway. First install the patch then the crack. 
If anyone could find a way to get a battle.net crack working, please tell me =)

---

### Post by nickless on 2005-08-01
In Frank's Corner is suggested, that one uses a little script to play battle.net with the crack. 
> 
#!/bin/sh
mv -f Game.exe Game1.exe
mv -f Game_crack.exe Game.exe
wine "Game.exe" &
sleep 2
mv -f Game.exe Game_crack.exe
mv -f Game1.exe Game.exe
exit

Save the script as diablo.sh
Now start Diablo 2 by typing sh diablo.sh 

But when I tried it, the files where not found, even when I wrote their paths in the script.
Whats going on?

---

