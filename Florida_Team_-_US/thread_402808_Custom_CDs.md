---
title: "Custom CDs"
date: 2007-04-06
forum: Florida Team - US
---

### Post by max.diems on 2007-04-06
I missed the meeting, but I just read the minutes and saw minimal discussion on the topic of custom CDs. I think we should, even if not much is changed. We can use [Reconstructor]("http://reconstructor.aperantis.com") to make it easier.

---

### Post by Bordy on 2007-04-06
max:
yeah we were thinking about it, but it seems to be way too much work for one person to do. If you want to give it a shot, I am sure somebody would gladly collaborate on it.

Have you used reconstructor before?

---

### Post by ep2011 on 2007-04-06
> **Bordy said:**
> max:
yeah we were thinking about it, but it seems to be way too much work for one person to do. If you want to give it a shot, I am sure somebody would gladly collaborate on it.

Have you used reconstructor before?


I've never used it, but it seems VERY easy to use (I was looked at screenshots, which is basically a guide, and also [http://ubuntusoftware.info/distro.html](http://ubuntusoftware.info/distro.html) . I'd be interested in helping with that, but what sort of features would be useful for it?

---

### Post by feravolo on 2007-04-07
I have been working most of yesterday on getting a USB key drive to work as a Live Boot Device, maybe we can consider including these as a way to spend ubuntu or use them ourself during the development of custom distribution. They are getting cheaper all the time and I have seen lots of 1 Gig Keys for under $20. 

You can also have them custom made with our Florida LoCo  Logo, but them we would have to sell them to recover the productions costs.

I will document how I got this to work when I am done, since following the procedures on the websites that I have found doesn't. I have got to the point when my computer recognizes the key as the boot device, then I see ISO Debian bla bla and then it snarls out saying it can't find the kernel.

One another note there is a really e-zine called "Full Circle" developing for the different flavors of Ubuntu. Here are there website and forum thread.

[http://fullcirclemagazine.org](http://fullcirclemagazine.org)
[http://ubuntuforums.org/showthread.php?p=2369160#poststop](http://ubuntuforums.org/showthread.php?p=2369160#poststop)

I am going to mirror copies of the magazine in the folder below:

[http://FullCircle.DoLinuxNow.com](http://FullCircle.DoLinuxNow.com)

They have been working very hard and it's looking real good. Links to it are at the end of the tread. I plan to mirror the issues somewhere soon.

Mike

---

### Post by feravolo on 2007-04-24
Hello:

Here is a Quick Fix for the Scary Live CD . . . 

In a post to the marketing group I noted that people that I have given the Live CD's to were scared off by the term "Start or Install Ubuntu" on the splash screen. Here is know you can change that "scary text" before you burn your own Live CD's. You will need the following software tools: An ISO Editor (isomaster), a text editor (gedit) and a iso image of a unbuntu distribution.

1) Download your Favorite Ubuntu, Kubuntu, Xubuntu or Edubuntu Distribution

2) Open the ISO image file with the ISO editor

3) Extract the File /isolinux/isolinux.cfg to your desktop

4) Make sure you have read and write permission to isolinux.cfg

5) Edit isolinux.cfg and remove the word install, and/or replace it with something like "Test Drive" to make it less scary.

6) Save isolinux.cfg and quit the text editor

7) using the ISO Editor replace the file /isolinux/isolinux.cfg with the one that you edited

8) Save the Modified ISO Image for your favorite flavor of *-buntu

9) Burn it to a CD

10) Restart Your System and Enjoy 

IF you have any questions feel free to give me a call: 321-784-5553 or mail: eztips at earthlink dot net.

Mike Feravolo


ttps://wiki.ubuntu.com/MikeFeravolo?highlight=%28Mike%29%7C%28Feravolo%29

---

### Post by ElementC on 2007-04-24
fervalo, that's an actual bug now. It'll be fixed by Gutsy (I hope).

Anyway, have we started work on a desktop package yet? I would like to read up on this, but can't find any really good resources.

Regards,

-E/C

---

### Post by Bordy on 2007-04-24
ElementC, if you would like to get with max.diems, yall can try to come up with some ideas.

Maybe add that as an agenda item to the wiki meeting page to be brought up on the 6th at the meeting?

---

