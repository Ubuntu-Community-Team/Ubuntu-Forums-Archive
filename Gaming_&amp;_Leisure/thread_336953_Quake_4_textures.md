---
title: "Quake 4 textures"
date: 2007-01-12
forum: Gaming &amp; Leisure
---

### Post by stinkball on 2007-01-12
I'm not having any performance problems, but the textures in quake 4 are worse looking than low-quality in windows.  Is there a way to fix this?  as far as performance goes, it runs about the same as in windows.

MSI k8tNeo-fis2r
AMD Athlon64 3200+
Sapphire Radeon x800GTO
2GB pc3200 RAM
SB Audigy 2 ZS
Ubuntu 6.10 Edgy

---

### Post by Lord Illidan on 2007-01-12
It could be the fact that you are running an ATI card. Opengl is worse on ATI than on Nvidia, especially under Linux.

Can you post a screenshot of Quake 4 here? And at what resolution and quality settings are you running it?

---

### Post by stinkball on 2007-01-12
1280x1024 on High quality.

How do you take a screenshot?

---

### Post by stinkball on 2007-01-12
i had to take a delayed screenshot, but here is the guy floating in space with his guts spilled out:

[http://img155.imageshack.us/img155/1641/screenshotzs9.png](http://img155.imageshack.us/img155/1641/screenshotzs9.png)

the tearing in the image isn't there, i think it has to do with how i took the screenshot.

---

### Post by stinkball on 2007-01-12
here is a similar screenshot taken in windows:

[http://img231.imageshack.us/img231/5372/untitledfj6.png](http://img231.imageshack.us/img231/5372/untitledfj6.png)

---

### Post by Lord Illidan on 2007-01-12
That does look ugly. My game looks like yours in Windows, I haven't tested it on Windows seeing as I haven't got it installed there.

My only guess is that it is the ATI graphics..

---

### Post by CaptainN on 2007-04-01
Did anyone ever find a solution to this problem?

I'm dealing with this now. Hopefully ATI's drivers will be better with the coming opengl rewrite.

---

### Post by fakie_flip on 2007-04-19
Where can I download a demo of quake 4 for Linux? Thanks.

---

### Post by Syke on 2007-04-19
Right here: [Quake 4 Linux Demo](ftp://ftp.idsoftware.com/idstuff/quake4/demo/quake4-linux-1.0-demo.x86.run)

---

### Post by abitwise on 2008-03-09
I have similar problem with ATI Graphic card, i can't believe, it has been so long time and still same problem. The funny thing is, that everything works - effects are great only textures look really awful. I think i'm gonna sell the ATI card and buy Nvidia, which i had previously used for 8 years, but i gave ati a try, too bad for me lol.

Athlon X2 5200+
4 GB RAM
Gigabyte Radeon HD3850 256 MB
Ubuntu 7.10

---

### Post by Sockerdrickan on 2008-03-09
**** happens...

Your card should be pretty well supported with their latest drivers though.

---

### Post by abitwise on 2008-03-09
Hi again

I got the thing working woohoo for that!  After exiting Quake 4 and i saw it only said my pc had 64 megs on video ram, although it has 256. Q4 failed to detect video ram on my card. So i went to Quake4Config.cfg (home/username/.quake4) and set it to 256 (both sys_videoRam and com_videoRam) - nothing got better, still the same ugly textures. But i did something bold, who cares if the thing crashes - i set it to 1024, just for kicks :)
And it worked, graphics were like they should - just beautiful textures! After the game exit it somehow set it to 512 in the config file.

So i think that Quake 4 with AMD Catalyst drivers fails to detect video ram size. maybe it is the 64 bit release, i don't know why. At least now if people read this and have the same problem - try the same thing, maybe it will work for you.

Bottom line: force Quake 4 to believe you have lot's of video ram (but if you don't have at least 512 - this time really not theoretically, then don't put on Ultra Quality, it is as slow as software rendering).

:popcorn:

---

### Post by Sockerdrickan on 2008-03-09
That's great to hear! Would be great if you reported it as a bug to id software/amd

---

### Post by tlages on 2008-06-28
I have the same problem but with an nVidia card. I also have 1.3 patch installed.

---

### Post by RIchard James13 on 2008-06-29
I have a nvidia 7600 AGP and the demo ran fine.

---

### Post by CHaoSlayeR on 2008-12-16
Hi there,

it's a bit late but I also had that low texture resolution issue and solved it another way. Fortunately the Quake4Config.cfg offers very detailed configuration options. So basically I did what has been told here too, namely to set the **com_videoRam** and **sys_videoRam** to **"256"** (I have a ATI/AMD Radeon HD2400 PRO using the FGLRX 8.10). After that doesn't changed anything but the warning at startup disappearing on the console regarding the video ram size I searched the web for a most complete explanation of the configuration options. And here is what I came up with:

```

seta image_downSize "1"
seta image_downSizeLimit "1024"
seta image_downSizeBump "1"
seta image_downSizeBumpLimit "1024"
seta image_downSizeSpecular "1"
seta image_downSizeSpecularLimit "1024"

```

The explanations for this and a lot other options can be found [here]("http://www.tweakguides.com/Quake4_8.html").

Hope that helps anyone that visits this thread again.

Regards,

C]-[aoZ

---

