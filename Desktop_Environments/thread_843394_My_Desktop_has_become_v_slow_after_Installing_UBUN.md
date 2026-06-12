---
title: "My Desktop has become v slow after Installing UBUNTU"
date: 2008-06-28
forum: Desktop Environments
---

### Post by mirchichamu on 2008-06-28
I am new to Ubuntu. I installed in both desktop and laptop. I noticed that my desktop has become v slow. It is Pentium 4 with 512 memory.Scrolling very slow. Programs open late, unlike windows. I wanted to switch to Ubuntu,although I am having genuine windows

I don't know what is wrong with that. My laptop stopped working with Ubuntu at all.
Any suggestions will be highly appreciated.

---

### Post by stoneybroke on 2008-06-28
Did you download and install the right version of Ubuntu for the desktop and laptop computers you should have got the 32 bit version for the desktop and try goubuntu for the laptop

---

### Post by mirchichamu on 2008-06-28
> **stoneybroke said:**
> Did you download and install the right version of Ubuntu for the desktop and laptop computers you should have got the 32 bit version for the desktop and try goubuntu for the laptop

Thanks alot.
I didn't know this but I saw only one download on ubuntu desktop annd downloaded that. And installed in my laptop also.
By the awy what is the difference in gubuntu and ubuntu?

---

### Post by stoneybroke on 2008-06-28
There are a few different versions of Ubuntu for both 32 and 64 bit computers the desktop version should also work on the laptop providing you get the right one 32 or 64 bit the GoUbuntu is dedicated to laptops as it has all the s/ware installed for mobile computers. Having said that I know of it but can't remember where it is on the site to download. So if anyone can help there then thanks.

---

### Post by stoneybroke on 2008-06-28
I have just remembered enter sudo tasksel in the shell you will get a menu that will allow you to download GoUbuntu and other items.

---

### Post by dinub1 on 2008-06-28
> **stoneybroke said:**
> Did you download and install the right version of Ubuntu for the desktop and laptop computers you should have got the 32 bit version for the desktop and try goubuntu for the laptop

If you are questioning if the users installed a 64 bit version on a 32 bit machine, the answer is installer will not proceed if it does not recognize a valid 64 bit machine. However 32 bit Ubuntus work quite well on 64 bit machines, without any appreciable degradations or delays....

In my view a P4 with 512 MB of RAM is quite good for any Ubuntu.
Anyway Windows (if XP) would task a computer resources more heavily than Ubuntu does...

---

### Post by dinub1 on 2008-06-28
> **stoneybroke said:**
> There are a few different versions of Ubuntu for both 32 and 64 bit computers the desktop version should also work on the laptop providing you get the right one 32 or 64 bit the GoUbuntu is dedicated to laptops as it has all the s/ware installed for mobile computers. Having said that I know of it but can't remember where it is on the site to download. So if anyone can help there then thanks.

Uhu :) So farting in a safe saves natural gas :) ? Does new Ubuntu help you better contain the farts in da safe :) ??

If it doesn't try Kubuntu instead.... bwahahahah :)

---

### Post by dinub1 on 2008-06-28
> **stoneybroke said:**
> I have just remembered enter sudo tasksel in the shell you will get a menu that will allow you to download GoUbuntu and other items.

Why would GoUbuntu be advantageous on a laptop? A 32 bit version of the OS should work well.

---

### Post by stoneybroke on 2008-06-29
Go here [http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu) and you will find all variants of Ubuntu and the description of each.

---

### Post by Samhain13 on 2008-06-29
Could this be as simple as the search application indexing your disk, since these are new installations? I think the app's called "Tracker".

To test this theory, go to Preferences > Sessions. In the Startup Programs tab, look for Tracker and/or Tracker Applet uncheck them. Hit close then logout (System > Quit > Log Out). Then log back in again.

If you notice a speed improvement, then it could just be Tracker. You can enable Tracher again and let your computer run for a while, so Tracker can finish indexing. After that, your computer's speed should be fine.

From what I understand, that indexing task takes a lot of processing power. And that can cause other applications to work more slowly than normal.

But then, I could be wrong. :)

---

### Post by mirchichamu on 2008-06-29
> **stoneybroke said:**
> Go here [http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu) and you will find all variants of Ubuntu and the description of each.

Thanks stoneybroke for your support. I went to page as you quoted, I found the following statement there.
"Please note that because running Gobuntu on most laptops and many desktops will be difficult, Gobuntu is intended for experienced Linux enthusiasts at this time"

And you may be knowing that I am completely new to ubuntu. At present My ubuntu is running. Lets hope for the best.

---

### Post by mirchichamu on 2008-06-29
> **Samhain13 said:**
> Could this be as simple as the search application indexing your disk, since these are new installations? I think the app's called "Tracker".

To test this theory, go to Preferences > Sessions. In the Startup Programs tab, look for Tracker and/or Tracker Applet uncheck them. Hit close then logout (System > Quit > Log Out). Then log back in again.

If you notice a speed improvement, then it could just be Tracker. You can enable Tracher again and let your computer run for a while, so Tracker can finish indexing. After that, your computer's speed should be fine.

From what I understand, that indexing task takes a lot of processing power. And that can cause other applications to work more slowly than normal.

But then, I could be wrong. :)

Thanks Samhain for your continuous support.
I tried this but of no use. Around 400 MB of my 500 MB memory is used.The processor is always 80 % busy.I don't know what is taking all this memory. That's the reason it is slow.

I shall be thankful for further suggestions.

---

### Post by Samhain13 on 2008-06-29
To know what's in constant use, in the terminal, do:

```
top
```

That should tell you what applications are using your resources.

---

