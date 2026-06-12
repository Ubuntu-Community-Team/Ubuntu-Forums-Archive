---
title: "World of Warcraft (Not an install question ;))"
date: 2007-02-24
forum: Gaming &amp; Leisure
---

### Post by Kastang on 2007-02-24
I am about 90% fully moved to Ubuntu, I have been making the move over the past six months or so. The last thing I really need to do is move World of Warcraft over before I can finally say goodbye to Windows, and stick with OS X and Ubuntu.

I can play WoW on my Mac, I have a PM G5, Dual 2.0 GHz Processors, 1GB Ram, Radeon 9500(I think) - It plays WoW decently but It the video card is killing it, I really do not want to invest any more money into it, I am getting a MBP before fall.

Back to the topic though, I have a preaty nice computer, Dual 2.13 GHz Conroe (E6400) CPU, 2GB Ram, 320GB SATA Drive, Radeon x1600xt Video Card... It plays WoW wonderfully on Windows.

I have been reading up on WoW on linux, I see that there are a lot of mixed opinions on it, Installing it is not the issue, The performance is though. 

My questions are:

-I am an Addon person, a collection of about 20 addons that I cannot live without. Does addons with Wine/Cedega hurt the performance?
-With my specs of my computer, Will there be a noticable performance difference?
-How stable is it? Will i be able to play for 5+ hours without having any handing issues?


I have been looking on google, I see a lot of older links (1+ year old) that say performance is horrible, if you want to game play on windows.. etc. But some of the more recent articals seem to be going the other way and saying windows games with cedega/wine are playing better on it. The problem is no one usually posts their specs for me to compare with my own.

Thanks for the help

---

### Post by tuxcantfly on 2007-02-24
Performance should be fine if you toggle the opengl flag; the people complaining about performance probably forgot to use opengl mode. The command should be wine wow.exe -opengl

Also remember to install the ATI proprietary drivers for better performance, more info at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The rating is gold on the wine appdb, so everything, including stability and performance, should work well.

More info at [http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482)

---

### Post by Kastang on 2007-02-24
Thank you for the prompt response. I am in the process of following the links you gave me now. Hopefully by morning I should have it up and running :)

---

### Post by ragnar_123 on 2007-02-24
Addons are no problem in Wine. It works just really good. I don't feel any performance difference. 

I've not found anything which isn't working just because you're not running off Windows (okay, there is a little textbox with news in the launcher, which isn't working, I think it uses Microsoft Internet Explorer as backend :-))

---

### Post by Praill on 2007-02-26
I'm running WoW with wine and it works great. Maybe not as good as windows but definently really close.
Oh and re: the launcher problem. You can fix that by installing gecko into your fake c drive with wine :mrgreen:

---

### Post by Ferrat on 2007-02-26
> **ragnar_123 said:**
> Addons are no problem in Wine. It works just really good. I don't feel any performance difference. 

I've not found anything which isn't working just because you're not running off Windows (okay, there is a little textbox with news in the launcher, which isn't working, I think it uses Microsoft Internet Explorer as backend :-))

U can use Gecko if you want to see it aswell but some ppl has had some problems after installing it, and it's just news anyways that you can read on the wow homepage

---

### Post by Sammi on 2007-02-26
> **ragnar_123 said:**
> ...okay, there is a little textbox with news in the launcher, which isn't working, I think it uses Microsoft Internet Explorer as backend :-)
Works for me :p

Wine asked me if I wanted to download and install Gecko the first time I ran that file(it runs automatically after an update is applied to WoW). I just clicked yes and it fixed itself.

I've got a Dell Dimension 9150 with a pentium 4 CPU, 2 gig of RAM, and a Geforce 6800 256 MB RAM. I've got ALL the video settings set to high(!) and I used to get frame rates between 20-30 outside during regular grinding gameplay, but after I updated to Wine 0.9.31 I've been getting 30+ most of the time.

Anyway here's the mandatory link to the Ubuntu community WoW/Wine wiki/howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ;)

---

