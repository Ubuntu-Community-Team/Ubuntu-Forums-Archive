---
title: "a clearly written WINE guide?"
date: 2006-02-19
forum: Gaming &amp; Leisure
---

### Post by illfilles on 2006-02-19
Hello. I am a linux/ubuntu rookie and I'm trying to learn more about WINE and how to get it up and running. I've googled all over the place and I can't seem to find a guide that I can understand and follow through with. Can someone point me in the direction of a good WINE guide.

If it helps at all, the app I am trying to run is Jagged Alliance 2, along with the Urban Chaos mod (although I don't know if this is possible).

Any help would be great.

---

### Post by Zeroedout on 2006-02-19
it's pretty simple if you just read a little. if you go to winehq.com (the main wine site) and click downloads, you'll see a list of linux distros with maintained packages. Click on your one (ubuntu), and you come here [http://winehq.com/site/download-deb](http://winehq.com/site/download-deb) . Those instructions are VERY clear, and getting and installing wine is 100% gui. To install your program, go to the cdrom or whereever the .exe is located, and open it with wine. Quite simple if you ask me. I'm really surprised you didn't find the wine site with googling, but it can happen. If you look in their app db, Jagged Alliance 2 works quite well, and has been since one of the 2003 releases [http://appdb.winehq.org/appview.php?appId=1273](http://appdb.winehq.org/appview.php?appId=1273) . Usually as long as the game works, most mods will, at least that has been my experiance. Anywho, if there are any more problems post back.

---

### Post by drewbie on 2006-02-19
There is also the ubuntu wiki at [https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine) which might help

---

### Post by illfilles on 2006-02-20
Thanks guys. I had taken a look at Wine HQ but somehow was missing the point. I read through the links and have the app up and running. Still tinkering through a few things... hopefully I'll be in Arulco soon. :)

---

### Post by handy on 2006-02-20
Here can be helpful too:

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

---

### Post by manicka on 2006-02-20
For games you want cedega

[http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by illfilles on 2006-02-20
[QUOTE=manicka]For games you want cedega

[http://www.transgaming.com/](http://www.transgaming.com/)[/QUOTE]
I understand that cedega would be a better way to run games manicka... but right now the only thing I am running Linux on is an old eMachines computer that finally refused Windows. Unfortunately, the box is a bit lacking in horsepower. Now that I've been getting more exposure to this wonderful ubuntu thing I think I am on my way to building a dedicated machine for gaming.

From what I see there should be some other good posts here to help me do that. :)

---

### Post by MAbans on 2006-02-20
I think at times people like myself can find Linux much less wine a daunting task.   You'll get used to it, I know I  am getting used ot it.

---

### Post by illfilles on 2006-02-20
Ok, ran into some trouble this afternoon. I clicked on the Audio Tab of wine and  winecfg closed down.

My terminal reads:

ALSA lib seq_hw.c:455: (snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

How can I obtain this magical /dev/snd/seq directory...?


....quick edit. Below the above terminal msg it also says:

Link points to "/tmp/ksocket-~"
can't create mcop directory

---

