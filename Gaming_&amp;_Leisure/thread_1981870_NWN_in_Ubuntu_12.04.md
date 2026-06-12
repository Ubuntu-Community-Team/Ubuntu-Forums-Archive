---
title: "NWN in Ubuntu 12.04"
date: 2012-05-17
forum: Gaming &amp; Leisure
---

### Post by rasmus91 on 2012-05-17
Hello All

Am I The only one here still playing Neverwinter Nights?

anyways, if any of you know how to install it from a windows installation, and where to get the linux files and everything, please tell me. I would like a guide, used to use the one written by artificial intelligence, but can't seem to find the gwos.org website anymore.

I appreciate any help given, i love this game.

---

### Post by regor210 on 2012-05-17
[http://ubuntuforums.org/showthread.php?t=113259](http://ubuntuforums.org/showthread.php?t=113259)

NWN can be installed natively but the installer is old and outdated. When you use it there are missing dependences.

I use Wine then rename the Movies folder to Movies1 to disable them.

Works for me.

---

### Post by TheDevilYouKnow on 2012-05-17
Rasmus, 

        What is "WTF Tae-Kwon-Do" ?   I play NWN too and am trying to get it installed as well...did the above mentioned method work for you in 12.04 ?


Thanks!

---

### Post by regor210 on 2012-05-17
Goto the Ubuntu Software Center. Type wine in the search bar. Install wine. Put your NWN cd in. Right click on setup.exe and select open with wine.

After you install NWN goto your home folder. Under view select show hidden. find the .wine folder  .wine > drive_c > Program Files > NWN then right click on the movies folder and rename it movies1 

Play NWN

---

### Post by Soulcage on 2012-05-18
If you have the diamond edition got mine from newegg.com

wget -c [http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz)
wget -c [http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz)
wget -c [http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz](http://files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz)

mkdir ~/nwn && cd ~/nwn && unzip /media/NW_DIAMOND/Data_Shared.zip && unzip /media/NW_DIAMOND/Data_linux.zip && unzip -o /media/NW_DIAMOND/data/XP1.zip && unzip -o /media/NW_DIAMOND/data/XP2.zip && tar -vxzf ~/nwclientgold.tar.gz && tar -vxzf ~/nwclienthotu.tar.gz && tar -vxzf ~/English_linuxclient169_xp2.tar.gz

./fixinstall
./nwn

You can also check this [http://liflg.org/?catid=6&gameid=65]("http://liflg.org/?catid=6&gameid=65")

---

### Post by rasmus91 on 2012-05-20
> What is "WTF Tae-Kwon-Do" ? I play NWN too and am trying to get it installed as well...did the above mentioned method work for you in 12.04 ?


Im gonna install it in wine, seeing as the only other guide I can find is for a CD version of Diamond edition, which i do not posses.

WTF Tae-Kwon-Do stands for World Tae-Kwon-Do Federation, it follows the Kukkikwon (i believe its called) Teachings. Other styles include for an example ITF, International Tae-Kwon-Do Federation.

Tae-Kwon-Do is a martial art, as far as i know the most widespread one. its origins is in Korea.

---

### Post by rasmus91 on 2012-05-20
installed with [this]("http://********************/forum/1/topic/187/index/4643217#9021203") and there was no missing dependencies or anything the game runs smoooooooth!

appearently the link doesn't work. here it is: [http://********************/forum/1/topic/187/index/4643217](http://********************/forum/1/topic/187/index/4643217)

Update 2: ?! just google "nwn on linux" you should find it...

---

### Post by vanquishedangel on 2012-11-09
I got it working on 64bit here 
[http://ubuntuforums.org/showthread.php?t=2082534](http://ubuntuforums.org/showthread.php?t=2082534) with movies, it should work with 32 bit as well

---

