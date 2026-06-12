---
title: "Dell ispirion 531 graphics help"
date: 2011-11-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ZeroSforza on 2011-11-28
im using ubuntu 11.10 and im having a graphics driver issue i went to additional drivers and it gives me a list of graphics drivers i chose the one ubuntu recommends the problem is i cant play any of my games such as minecraft san andreas or company of heroes is there a way the grahpics card is a onboard one its a geforce 8600 gt could i possibly instal l the windows drivers and use it that way or is there another way?

---

### Post by ZeroSforza on 2011-12-05
-bump-

---

### Post by mikewhatever on 2011-12-07
Unfortunately, no, Windows graphics drivers don't work on Linux.

I suggest you repost the question in the gaming sub-forum instead of here, cause the problem, apparently, has nothing to do with Dell.

Here is the link: [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

---

### Post by ZeroSforza on 2011-12-08
mike is there a possibility of instead of using ubuntu's genric drivers is it possible to use actual drivers?

---

### Post by mikewhatever on 2011-12-09
Of cause. By default, Ubuntu uses the open source Nouveau driver for Nvidia GPUs. You can use the Addidtional Drivers utility to install the recommended driver from Nvidia. 
...but I thought you've done that already.

---

### Post by ZeroSforza on 2011-12-10
unfortunately not i was using the one it recommended and its a poor choice the video card i have is a onboard one and all i know is its a dell driver that makes it run properly i have no lcue what the vid card is

---

### Post by mikewhatever on 2011-12-11
Somehow, I rather doubt that Dell makes graphics cards of its own and writes drivers for them. Dell probably just redistributes what's supplied by the vendor - Nvidia, ATI, etc.

You can find out more about the GPU by loking at the output of **lspci**.

---

### Post by ZeroSforza on 2012-01-27
> **mikewhatever said:**
> Somehow, I rather doubt that Dell makes graphics cards of its own and writes drivers for them. Dell probably just redistributes what's supplied by the vendor - Nvidia, ATI, etc.

You can find out more about the GPU by loking at the output of **lspci**.  lspci?

---

### Post by ruffEdgz on 2012-01-27
> **ZeroSforza said:**
> lspci?
[LIST]
[*]open a terminal
[*]type in the command: **lspci | grep -i vga**
[*]display the results on this post
[/LIST]

Example below:
```

usera@computera:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 1050 (rev ff)

```

---

### Post by bobvfr on 2013-02-10
Well seeing as I have the same machine here is my output from:

 [B]lspci | grep -i vga

01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]
bob@ubuntu:~$  lspci | grep -i vga
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS690M [Radeon X1200 Series]

[/B]So what next, I see no way in settings to update a driver[B].

[/B]I am sure it aint rocket science but I do have to go to work at times and life just gets in the way sometimes.


Bob

---

### Post by wildmanne39 on 2013-02-10
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

