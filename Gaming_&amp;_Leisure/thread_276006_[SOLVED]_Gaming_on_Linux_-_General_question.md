---
title: "[SOLVED] Gaming on Linux - General question"
date: 2006-10-12
forum: Gaming &amp; Leisure
---

### Post by wieman01 on 2006-10-12
Hello, 

I've got a general question (and hence expect a general answer) as far as Windows computer games on Linux are concerned. Are most of the recent computer games supported by Linux & Wine? How easy is it to install games and have sound, mouse, video, networking(!), etc. supported? Is there a good guide available?

I'm not a big gamer but it seems challenging to give it a go on Linux. Just curious how I would go about that.

Thanks in advance - as always.

---

### Post by Hmarroqu on 2006-10-12
I tried using Counter Strike with wine, as well as other non games like Nero and PQDVD, everything freaks out....i have no idea as to why all i knw is that any windows program freaks out and doesnt work properly...ubuntuguide.org has some info on wine and winehq.??? obviously.
:-|

---

### Post by wieman01 on 2006-10-12
> **Hmarroqu said:**
> I tried using Counter Strike with wine, as well as other non games like Nero and PQDVD, everything freaks out....i have no idea as to why all i knw is that any windows program freaks out and doesnt work properly...ubuntuguide.org has some info on wine and winehq.??? obviously.
:-|
Mmm... I see. But there must be people around who have made good experience with Wine & games. I see tons of posts regarding that.

---

### Post by crane on 2006-10-12
It really depends on what game you want. There are many many different games and many, many different kinds of people who play them. Most of the games I play are supported. (UT2004, Q3, Q4) But many are not. That brings in the wine question you asked. I have Call of Duty and Call of Duty United Offensive running in wine. I was also able to get Prey Demo to run as well. Finding documentation should be fairly easy with a little searching. If you have questions post them in the appropriate forum here or at [UGA]("http://gaming.gwos.org/index.php")

---

### Post by bastiegast on 2006-10-12
> **wieman01 said:**
> Hello, 

I've got a general question (and hence expect a general answer) as far as Windows computer games on Linux are concerned. Are most of the recent computer games supported by Linux & Wine? How easy is it to install games and have sound, mouse, video, networking(!), etc. supported? Is there a good guide available?

I'm not a big gamer but it seems challenging to give it a go on Linux. Just curious how I would go about that.

Thanks in advance - as always.

its quite hard to answer this in general since there are recent computer games working fine in linux, but theres also a lot of recent games not working and the issues differ greatly.

As far as I know most source games (Half life 2 Counter strike source etc) work fairly well in linux. Little or no issues on sound, mouse and networking, im afraid performance might be a little worse and you will(although rarely) encounter some corrupted graphics and for now, forget about things like HDR in windows games on linux, but still Half life 2 looks very nice on my computer.

Refer to the cedega wiki for some info on supported games in cedega and check out the wine app db for info on games in wine.

---

### Post by wieman01 on 2006-10-12
Great. I was actually looking at UT2004 and Prince of Persia (the new 3D version, not the old stuff). Are there any guides around?

---

### Post by Rhubarb on 2006-10-12
UT2004 is very easy to install:
```
sudo sh /media/cdrom0/linux-installer.sh
```
I could've got the "linux-installer.sh" file name wrong, so please check for the correct file name if it doesn't work.
Then press ok to everything.  Don't run the game after installation (as it'll have su privileges).
Now just type in ut2004 and you're in.
You'll need to make sure you have your 3d drivers working.
If you want to play online, be sure to grab the linux patch and the Mega pack.  Once you've unzipped these patches and packs, do a:
```
sudo cp -r * /usr/local/games/ut2004/
```
And everything will be running fine.

Just one thing to note, a few users on this forum have recently bought UT2004 Editors Choice Edition (ECE).  This particular DVD doesn't have the linux-installer.sh file.  So beware!

If you want to install the ECE bonus pack you'll need to do some tricky stuff with wine to allow you to extract the files (it's a winzip self extracting executable installer) - I personally used 7zip with wine to get around this problem.

If you need any more specific help with ut2004 let me know - I can help you out when I get home - away from m$ @ work.
Don't know about prince of persia though.

---

### Post by Anonii on 2006-10-12
Hello,

I only tried one Windows game in Linux. And that was Planescape:Torment, an 7years old game. After two days of boring tweaking and Wine understanding, I made it. I had to change many things, install different Wine versions, and learn the basics of no-cd patches. After that I managed to make it playable, and it was working all right! But yes, it was really tiring.

Anyway, sites about windows applications in wine:
[http://frankscorner.org/](http://frankscorner.org/) (Not many applications/games, but there are good instructions in there.)
[http://appdb.winehq.org/appbrowse.php?catId=0](http://appdb.winehq.org/appbrowse.php?catId=0)  (Official)

---

### Post by wieman01 on 2006-10-12
> **Rhubarb said:**
> UT2004 is very easy to install:
```
sudo sh /media/cdrom0/linux-installer.sh
```
I could've got the "linux-installer.sh" file name wrong, so please check for the correct file name if it doesn't work.
Then press ok to everything.  Don't run the game after installation (as it'll have su privileges).
Now just type in ut2004 and you're in.
You'll need to make sure you have your 3d drivers working.
If you want to play online, be sure to grab the linux patch and the Mega pack.  Once you've unzipped these patches and packs, do a:
```
sudo cp -r * /usr/local/games/ut2004/
```
And everything will be running fine.

Just one thing to note, a few users on this forum have recently bought UT2004 Editors Choice Edition (ECE).  This particular DVD doesn't have the linux-installer.sh file.  So beware!

If you want to install the ECE bonus pack you'll need to do some tricky stuff with wine to allow you to extract the files (it's a winzip self extracting executable installer) - I personally used 7zip with wine to get around this problem.

If you need any more specific help with ut2004 let me know - I can help you out when I get home - away from m$ @ work.
Don't know about prince of persia though.
Wow... Excellent! Thank you very much. I will give it a shot next weekend. I assume you have to have Wine installed, correct?

---

### Post by frodon on 2006-10-12
For sure the best for windows games is to use cedega, if you don't want to pay for it just compile it from CVS (the sources are free).
I play counter strike and counter strike sources without any problems with cedega, trust me or not but on my old 700MHz computer counter strike run faster on linux than on windows despite it is a windows game.

However since i discovered enemy territory i don't use cedega !

Crane i'm ready to kick your *** at ET lol

---

### Post by skymt on 2006-10-12
> **wieman01 said:**
> Wow... Excellent! Thank you very much. I will give it a shot next weekend. I assume you have to have Wine installed, correct?

No, UT2K4 has a native Linux version. It doesn't even need Wine.

---

### Post by wieman01 on 2006-10-12
> **skymt said:**
> No, UT2K4 has a native Linux version. It doesn't even need Wine.
Oh great! Even better. Wasn't aware of that. So I'll definitely give it go then.

---

### Post by Rhubarb on 2006-10-12
But you might need wine if you want to install the ECE bonus pack.  That's all.
Again if you need more specific instructions to get ut2004 give me a shout on this thread - so I can get you online ... and hunt you down with a redeemer!  <insert evil laugh here>

---

### Post by crane on 2006-10-12
[UT how to at Ubuntu Gamers arena!]("http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63")
For all the latest in UT read this [Get the Latest]("http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=view&id=256&catid=11")

---

### Post by Kateikyoushi on 2006-10-12
I am big C&C fan.
What are my chances to get C&C Generals working in wine ?

---

### Post by Anonii on 2006-10-12
> **crane said:**
> [UT how to at Ubuntu Gamers arena!]("http://gaming.gwos.org/index.php?option=com_content&task=view&id=75&Itemid=63")
For all the latest in UT read this [Get the Latest]("http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=view&id=256&catid=11")
My turn for a question.

UT is free as in free beer, in Linux?

---

### Post by Rhubarb on 2006-10-12
> **Anonii said:**
> My turn for a question.
UT is free as in free beer, in Linux?

No, not at all.  UT2004 isn't free (you have to buy it), nor is it free as in beer either.  I like it because it comes with a native linux installer (that and it's fun too).

---

### Post by crane on 2006-10-12
Yea, it's not free but it should be affoordable now.
Where can I find free beer?

---

### Post by dmn_clown on 2006-10-13
> But you might need wine if you want to install the ECE bonus pack. That's all.

No.  Just follow the instructions here [http://icculus.org/news/news.php?id=2192]("http://icculus.org/news/news.php?id=2192")

---

### Post by wieman01 on 2006-10-29
I have downloaded UT2004 demo version & I must say I am impressed. Runs like a charm & has absolutely brilliant gameplay.

Now I'd like to buy the full Linux version of UT2004. Does anybody know where to get it?

_**EDIT:**_
Plus I want to download it, not buy the CD/DVD.

---

