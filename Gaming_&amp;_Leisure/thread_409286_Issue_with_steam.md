---
title: "Issue with steam"
date: 2007-04-14
forum: Gaming &amp; Leisure
---

### Post by boast on 2007-04-14
When I was using steam last week, everything worked fine. Starting it up today, all I get is ```
compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time
fixme:xrender:X11DRV_AlphaBlend not supported - XRENDER headers were missing at compile time

```

[img]http://img114.imageshack.us/img114/9104/esgzdgiy2.jpg[/img]

any ideas? I installed msttcorefonts to see if it would help, but nothing.

---

### Post by tors on 2007-04-14
Install xrender headers:

sudo apt-get install libxrender-dev


Download and compile the sources to a .deb and install it manually:

sudo apt-get build-dep wine

sudo apt-get --build source wine


dpkg -i wineXYZ.deb

Enjoy!

---

### Post by abowman on 2007-04-14
Same thing here.  No fonts in steam after I updated to the latest wine version.

---

### Post by maka on 2007-04-14
same here...

---

### Post by dan171717 on 2007-04-14
how didu get it that far anyway steam needs a font i forgot what its called and were you put it?? but it requres a perticular font dig on google for a while :(  but it should work inoticed there was no text on your pic so thats probbly it :) :)

---

### Post by Mr.Kuchinawa on 2007-04-14
> **tors said:**
> 

Download and compile the sources to a .deb and install it manually:

sudo apt-get build-dep wine


Enjoy!

Doesn't work. It says it can't find the source code pack.

This is just f****** irritating..

---

### Post by Mr.Kuchinawa on 2007-04-14
> **dan171717 said:**
> how didu get it that far anyway steam needs a font i forgot what its called and were you put it?? but it requres a perticular font dig on google for a while :(  but it should work inoticed there was no text on your pic so thats probbly it :) :)

Well, you see, we all have the tahoma font installed, but after updating to the newest wine this thing happened.

---

### Post by gschoper on 2007-04-14
Same issue here after updating to 0.9.35. However, I was able to re-install 0.9.34 which was hanging out on my machine in /var/cache/apt/archives:

```
cd /var/cache/apt/archives
sudo dpkg -i wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb

```

gschoper

---

### Post by boast on 2007-04-14
> **tors said:**
> Install xrender headers:

sudo apt-get install libxrender-dev


Download and compile the sources to a .deb and install it manually:

sudo apt-get build-dep wine

sudo apt-get --build source wine


dpkg -i wineXYZ.deb

Enjoy!

geez, that took forever to compile. 

Thanks, it worked.

But it sucks Update Manager wants to update wine, but when I update, it I get the problem again. Will I have to compile wine for every update?

---

### Post by boast on 2007-04-14
> **Mr.Kuchinawa said:**
> Doesn't work. It says it can't find the source code pack.

This is just f****** irritating..

> Adding the WineHQ APT Repository:

First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Edgy (6.10):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Dapper (6.06):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list

Then, you can install Wine from WineHQ like it were any other package, such as by using the Synaptic Package Manager under System->Administration. Alternatively, you can install from the terminal by running 'sudo apt-get update' to update APT's package information and then 'sudo apt-get install wine'..

---

### Post by tors on 2007-04-14
> **boast said:**
> geez, that took forever to compile. 

Thanks, it worked.

But it sucks Update Manager wants to update wine, but when I update, it I get the problem again. Will I have to compile wine for every update?

Hmm, you are right. That sucks.
I guess you can reinstall your wineXYZ.deb after everytime you do an update of many packages (including wine of course).

Hopefully the person who has packaged wine will notice that it wasn't compiled with xrender and make a new package.

---

### Post by abowman on 2007-04-14
> **gschoper said:**
> Same issue here after updating to 0.9.35. However, I was able to re-install 0.9.34 which was hanging out on my machine in /var/cache/apt/archives:

```
cd /var/cache/apt/archives
sudo dpkg -i wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb

```

gschoper

Thanks!

---

### Post by aknapp on 2007-04-14
I have tried all of the above suggestions and I still have no fonts in steam. What else can I do?

---

### Post by aknapp on 2007-04-14
Dissreguard my post, I forgot to recopy the tahoma font back into the wine/windows/fonts dir. Thanks guys, it looks like im back in working order.

---

### Post by pippy on 2007-04-15
Downgrading to version .94 worked for me, looks like we will have to wait until the next version comes out with the proper xrenderer to upgrade

---

### Post by Steve H on 2007-04-15
> **gschoper said:**
> Same issue here after updating to 0.9.35. However, I was able to re-install 0.9.34 which was hanging out on my machine in /var/cache/apt/archives:

```
cd /var/cache/apt/archives
sudo dpkg -i wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb

```

gschoper

Many Thanks for that, i can see all my fonts in Steam again, woohoo i can play CS online.

:D

---

### Post by YokoZar on 2007-04-15
> **tors said:**
> Install xrender headers:

sudo apt-get install libxrender-dev


Download and compile the sources to a .deb and install it manually:

sudo apt-get build-dep wine

sudo apt-get --build source wine


dpkg -i wineXYZ.deb

Enjoy!Ah hah! That was the problem, a missing build depends.  I'm not sure why something like this didn't happen earlier.

Anyway, I've added libxrender-dev to the package build depends and am compiling it now.  I'll upload the new version to the APT repository later today; users who do nothing should automagically be prompted for the package upgrade and have it taken care of.

---

### Post by Steve H on 2007-04-15
I started that but it said it was going to install 200 meg ( or there abouts), I´m just concerned about constantly downloading upgrades of packages, and the system NOT deleting the old packages. Maybe I&#7743; being a naive newbie but it seems extravagant to download that much just for a WINE update. Anyway, i have raised this issue with WineHQ within Bugzilla. So hopefully we should have a more efficient fix.....maybe.

---

### Post by gschoper on 2007-04-15
> **Steve H said:**
> I started that but it said it was going to install 200 meg ( or there abouts), I´m just concerned about constantly downloading upgrades of packages, and the system NOT deleting the old packages. Maybe I&#7743; being a naive newbie but it seems extravagant to download that much just for a WINE update. Anyway, i have raised this issue with WineHQ within Bugzilla. So hopefully we should have a more efficient fix.....maybe.

The package is being fixed as we speak according to YokoZar who maintains the Ubuntu Wine packages (See post directly above yours).

gschoper

---

### Post by Steve H on 2007-04-15
Thanks gschoper, i will look out for the new package.

---

### Post by dan171717 on 2007-04-16
you said you updated wine if u did downgrade

---

### Post by gschoper on 2007-04-16
The new package is in the repo. Just updated to 0.9.35~winehq0~ubuntu~6.10-2 (edgy).

gschoper

---

### Post by rcatman on 2007-04-30
I've been running wine-0.9.36 from the ubuntu repositories (edgy) and had the font problem. I'm currently working on compiling the wine source to include the xrenderer (?). I'm not very knowledgeable in this part of linux but hopefully I'll learn something and it'll work :)

EDIT: Just used tors method and it didnt work for me. I'm going to try downgrading to 0.9.34

EDIT2: Downgrading did not work. The solution WAS to install the tahoma font. I downloaded the font here [http://fonts.appliedlanguage.com/tahoma_font.shtml]("http://fonts.appliedlanguage.com/tahoma_font.shtml")
This post told me where to install it, [http://ubuntuforums.org/showthread.php?t=421989]("http://http://ubuntuforums.org/showthread.php?t=421989")

Move the tahoma.ttf file into ~/.wine/drive_c/windows/fonts/ folder  , where ~ is the location of your home folder ($home). The text is back!

---

### Post by Steve H on 2007-04-30
Downgrading did work for me when i was running Edgy, Now I'm running Feisty with the new (and hopefully improved) package from WINE. It still had the Tahoma.ttf problem, which was quickly fixed by robbing it from Windoze. I think that WINE & Ubuntu moved quite fast to repair the faulty package that had not had all the deps added, which should be in the repos now.

It is all working beautifully again, I've used it every night since doing a clean install of Feisty. A lot of these probs did seem to come from a failed (or partial) upgrade to Feisty from Edgy.

Fingers crossed it's all working again.

---

### Post by acalafra on 2007-05-04
i have tahoma installed but still get font issues

---

### Post by acalafra on 2007-05-04
all i had to do to fix this was enable the driver under administration ->Restricted Drivers Manager. I got full text and changing the heapsize to 512000 helped but i'm still a little slow and stuck in a little box. does anybody know how to launch steam from command line in fullscreen? this is what im using now
 sudo wine "c:\Program Files\Steam\Steam.exe" -fullscreen \ -width 800 -height 600 -applaunch 10 \ -heapsize 512000 

im using sudo because i was getting permision errors since im a newb and dont know the right way to fix it.

ps box covering cs window is snapshot program, how do i fix that for future shots?

---

