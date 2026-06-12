---
title: "How to remove Xorg and install Xfree86"
date: 2005-12-25
forum: General Help
---

### Post by Masteroc on 2005-12-25
Hi,

I am a noob at linux and was wondering how to uninstall xorg and install xfree86??

---

### Post by kaamos on 2005-12-25
May I ask why you wish to do this?

---

### Post by zoiks on 2005-12-25
You better have a very good reason, as it doesn't appear to be supported in ubuntu.  It'll be a lot of work and after you're done things probably won't work just right.

---

### Post by The Warlock on 2005-12-25
[QUOTE=Masteroc]Hi,

I am a noob at linux and was wondering how to uninstall xorg and install xfree86??[/QUOTE]

There is pretty much no reason at all to do this, ever. Why do you want to?

---

### Post by briancurtin on 2005-12-25
[QUOTE=The Warlock]There is pretty much no reason at all to do this, ever. Why do you want to?[/QUOTE]
...especially for a noob to do. im wondering as well what this person is hoping to obtain by switching

---

### Post by Masteroc on 2005-12-25
wow,

soo many people want to know, so i better tell them!!

My main reason for this is to get my video card working. My video card is an old ATI Rage 128 PRO. I have asked everywhere on the forum and have looked on the internet but have found nothing in regards to ubuntu or xorg. The only thing that i have found that works is Xfree86 which supposedly has the drivers in it.

Am i wrong with any of this. If so, please tell me!

---

### Post by BathroomNinja on 2005-12-25
well, according to ATI's own website, it works in X.org
[http://www.ati.com/developer/altoschart.pdf](http://www.ati.com/developer/altoschart.pdf)

Also looks like it's already in the kernel (just need to turn it on) since 2.4

On THESE forums there is a howto:
[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ATI+Rage+128+PRO](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ATI+Rage+128+PRO)

Also try:
[http://www.ubuntuforums.org/showthread.php?t=90222&highlight=ATI+Rage+128+PRO](http://www.ubuntuforums.org/showthread.php?t=90222&highlight=ATI+Rage+128+PRO)


I'm not trying to be a jerk, but did you do any searches?

---

### Post by Masteroc on 2005-12-25
yeah, i have been searching for days. 

Maybe i am just incompetent

But thanks alot, i cant believe that it was that simple and no one else could tell me.

Really, thanks!!

---

### Post by BathroomNinja on 2005-12-25
No problem.  Looks like you just need to install the mentioned ATI drivers in those threads.  I linked the second one in case you get the problem that person had.

---

### Post by Masteroc on 2005-12-26
yeah, thanks for your help and all, but it did not work.

if i direct you to this page:
[HTML]http://www.ubuntuforums.org/showthread.php?t=75378&page=24&highlight=ATI+Rage+128+PRO[/HTML]

You will see that those drivers do not work for an ati rage 128 card. 

I tried just putting the card into the machine, but the screen got all jumbled and said that the x screen thing failed to start and that there was someting wrong with the video card. 

Should i try and reinstall ubuntu so that it can auto configure itself with the ati card. Or is there a way that i can do that without reinstalling it?

---

### Post by zoiks on 2005-12-26
ATI hasn't traditionally supported linux very well.  If you really need to use that card, maybe another distro that does use XFree86 will work better for you, though it seems almost all distros have gone the x.org route now.

---

### Post by Lambert on 2005-12-26
[quote=Masteroc]

Should i try and reinstall ubuntu so that it can auto configure itself with the ati card. Or is there a way that i can do that without reinstalling it?[/quote]

hit ctrl+alt+f1 to get to a console. login then run this command

sudo dpkg-reconfigure -phigh xserver-xorg

most default answers will be ok but when you get to the video section you can try to modify those according to your video card.

---

### Post by Masteroc on 2005-12-26
i'll try that, thanks

---

### Post by Masteroc on 2005-12-27
can i just type this into the command line without even starting up the gui?

---

### Post by fordfan753 on 2005-12-27
[QUOTE=Masteroc]can i just type this into the command line without even starting up the gui?[/QUOTE]

Yes

---

### Post by Masteroc on 2005-12-27
Thanks!!

This is the only this that has actually worked for me!!

I just installed the graphics card and am posting this from the ubuntu machine that it is intalled in.

Thanks everyone and Lambert!

---

### Post by BathroomNinja on 2005-12-27
[QUOTE=Masteroc]Thanks!!

This is the only this that has actually worked for me!!

I just installed the graphics card and am posting this from the ubuntu machine that it is intalled in.

Thanks everyone and Lambert![/QUOTE]


It never dawned on me that you did not install Ubuntu with the card already in the system.  Now I feel stupid.  Glad you found your answer!

---

### Post by Masteroc on 2005-12-27
Sry, i should have mentioned this!

Thanks

---

### Post by klineberger on 2005-12-31
Masteroc has a point. I have the same graphics card, and xorg does not provide hardware acceleration for it.
  When I installed Ubuntu 5.04 it auto-configured hardware acceleration, but after upgrade to 5.10 it was lost.
  I'm not sure, but I understand 5.04 uses xfree86 and 5.10 uses xorg, isn't it? Is it possible to upgrade from 5.04 to 5.10 without switching to xorg??

thanks

---

### Post by juantxorena on 2005-12-31
5.04 uses xorg, not xfree86. Maybe the problem isn't in the graphic server, but in the kernel, or something else.

---

### Post by Masteroc on 2006-01-01
maybe they took something out of 5.10 that was in 5.04. I can see no other reason why 5.10 would have less capability than 5.04.

---

### Post by klineberger on 2006-01-02
Don't know, all I can tell you is my video card is "ATI Technologies, Inc. Radeon 320M (RS200 IGP)" (sorry, I said differently) and I use "ati" driver in 5.04. In 5.10 neither "ati", nor "fglrx", nor "radeon" would work. Actually, with "fglrx" the server crashes.
   I have actually reverted to 5.04, and I'll wait for the upgrade till I know why this happens.
   At [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards")
 I found that 3D is not supported for this video card. It's strange, cause it says the driver was released in Breezy.:???:

---

