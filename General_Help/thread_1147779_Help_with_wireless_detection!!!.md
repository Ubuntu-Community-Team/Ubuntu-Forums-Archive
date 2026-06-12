---
title: "Help with wireless detection!!!"
date: 2009-05-03
forum: General Help
---

### Post by VyperX on 2009-05-03
Hello, **I am a noob at linux**, and I just installed Ubuntu 8.10 (32-bit) on my Toshiba Satellite A215-S4767 but it doesnt detect my wireless crad but I actually have one.

I did lspci -nn and it said that I had this wireless card AR5007EG
any help will be appreciated!

---

### Post by Wheels8257 on 2009-05-03
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by scottro on 2009-05-03
Howdy VyperX, long time no type. (Unfortunately, these days the job is so RH based system centric, I have little time to play with Ubuntu.)

What I've found is that on Intrepid, you have to install the backports modules, as was said in the post above mine.  In Jaunty, it *should* just work, however, I've found it to be a bit unreliable.  However--once again, installing the backports package seemed to fix the reliability issue. So, do that, whether running Jaunty or Intrepid and the card should almost certainly work.  
I'm wondering though, if you might be running an older kernel at this point, since most of the time, lspci will report it as AR242x.  You got that 5007 from lspci, or from Windows?

One thing that does complicate it a bit more is that Atheros apparently gave that designation to more than one card--however, once again, the link posted in the post above mine *should* fix the issue.

---

### Post by VyperX on 2009-05-03
> **scottro said:**
> Howdy VyperX, long time no type. (Unfortunately, these days the job is so RH based system centric, I have little time to play with Ubuntu.)

What I've found is that on Intrepid, you have to install the backports modules, as was said in the post above mine.  In Jaunty, it *should* just work, however, I've found it to be a bit unreliable.  However--once again, installing the backports package seemed to fix the reliability issue. So, do that, whether running Jaunty or Intrepid and the card should almost certainly work.  
I'm wondering though, if you might be running an older kernel at this point, since most of the time, lspci will report it as AR242x.  You got that 5007 from lspci, or from Windows?

One thing that does complicate it a bit more is that Atheros apparently gave that designation to more than one card--however, once again, the link posted in the post above mine *should* fix the issue.

Hello Scottro, thank you for helping me once again... I did the guide of the post above yours and unfortunately, nothing happened... I dont know why, I could find this **blacklist ath5k** so I dont know what else to do.

As of what you typed: > you got that 5007 from lspci, or from Windows? I dont know what lspci means... I basically dont understand the whole  sentence.


Once again, thank you.

---

### Post by scottro on 2009-05-03
Well, you said you ran the lscpi command (with nn).  Did that tell you that it was AR5007EG, or did you get that model number from looking at the card while running Windows and looking at the Windows Device Manager?  That's what that question meant.  

Navigate means to use the cd command.  So, they just mean do 

cd /etc/modprobe.d

and then search the blacklist file for something that reads

blacklist ath5k

If the line exists, put a comment sign (the #) in front of it. 

(Did you know that it's actually called an octothorp(e).  Sometimes spelled with an e and sometimes without.  That has nothing to do with any of this, but I just find it an interesting name. Of course, if I'd written, put an octothorp in front of the line...)

Sigh, I have to get to sleep. I won't be able to look again until tomorrow evening, I don't think, so if you don't get any more replies from me till then, don't worry, we haven't forgotten you.  :)

Anyway, hopefully I've answered your question.

---

### Post by VyperX on 2009-05-03
> **scottro said:**
> Well, you said you ran the lscpi command (with nn).  Did that tell you that it was AR5007EG, or did you get that model number from looking at the card while running Windows and looking at the Windows Device Manager?  That's what that question meant.  

Navigate means to use the cd command.  So, they just mean do 

cd /etc/modprobe.d

and then search the blacklist file for something that reads

blacklist ath5k

If the line exists, put a comment sign (the #) in front of it. 

(Did you know that it's actually called an octothorp(e).  Sometimes spelled with an e and sometimes without.  That has nothing to do with any of this, but I just find it an interesting name. Of course, if I'd written, put an octothorp in front of the line...)

Sigh, I have to get to sleep. I won't be able to look again until tomorrow evening, I don't think, so if you don't get any more replies from me till then, don't worry, we haven't forgotten you.  :)

Anyway, hopefully I've answered your question.

Ok, thanks for your reply, the lscpi command (with nn) told me that it was AR5007EG.

I navigated through here /etc/modprobe.d

and then I looked for the blacklist file  that said

blacklist ath5k

But unfortunately I couldnt find it... so I dont know what else I should do.

Thank you,

VyperX

---

### Post by scottro on 2009-05-04
If it's not in there, that's fine, it means that it isn't blacklisted.

You should have, if you do  

lsmod |grep ath


a line reading ath5k.

If you have that, then it should really work.  

The only other thing I can suggest is trying a page I have, that goes through seeing if the card is connecting, and if the problem is possibly NetworkManager. 

[http://home.roadrunner.com/~computertaijutsu/wireless.html](http://home.roadrunner.com/~computertaijutsu/wireless.html)


It's more Fedora based, but perhaps you can use it to help. 

Otherwise, I'm really not sure.  You can try going through other steps in that article.  

For what it's worth, *my* experience, but not necessarily others, did find that card a bit harder to get working with Ubuntu than with some other distributions.

---

### Post by VyperX on 2009-05-04
@Scottro
 Thank you so much for your support... I (we) finally did it... the wireless card is now working properly.

I just don't know how to thank you for all your support, patience, etc.

Sorry for being such a noob at ubuntu but hopefully I will improve my skills and hopefully I will be as good as you are at linux.

Best wishes,

VyperX

---

### Post by scottro on 2009-05-04
Well, that's great news.  You should probably post exactly what you did (as much as you've figured out anyway--sometimes, we try X, Y, and Z and lose track.)   :)

You're more than welcome, and I'm glad I could help. There were (and are) lots of people who have given, and continue to give, their time to help me, and helping you is perhaps the best way of thanking them.  Well, sending them money would probably be the best way, but, probably the second best way of thanking them.

---

