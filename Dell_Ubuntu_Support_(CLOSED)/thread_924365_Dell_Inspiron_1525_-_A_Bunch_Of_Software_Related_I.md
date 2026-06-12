---
title: "Dell Inspiron 1525 - A Bunch Of Software Related Issues"
date: 2008-09-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by BarfBag on 2008-09-19
My little brother got a Dell Inspiron 1525 as a gift.  It's my job to get it all set up for him.  I've had quite a few software related problems, though.

1.  Even though it was suppost to ship with Hardy, it shipped with Gutsy.  I'm thinking I should upgrade to Hardy.  Is the following image supported by the Inspiron 1525?  (It says it supports 1525n - I'm not sure if that's the same thing.)  [http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO)

2.  Ubuntu-restricted-extras does not work.  This means that I can not get Microsoft Fonts or certain multimedia codecs.  The Totem browser plug-in does not work, either.  I have a theory - I looked at the repositories, and it looked shorter than I remember it being.  Did Dell trim it down?  If so, is it still trimmed down in the image above?  Would it be worth my while to just install the official Hardy image?  Of course, if Dell didn't trim down sources.list, what's going on here?

3.  Steam (running through WINE, installed with Plays On Linux) will not work.  When I click on it, it opens and I can see the client for about five seconds.  It then randomly closes.

4.  Wireless drivers are included by default, but it's really weird.  It won't connect to my home network by default - it always connects to the neighbor's (it's unprotected, mine is not).  How do I get it to connect to mine by default?  Also, once it's connected to a network, I can't click on another on the list.  It just does nothing.

---

### Post by superm1 on 2008-09-19
> **BarfBag said:**
> My little brother got a Dell Inspiron 1525 as a gift.  It's my job to get it all set up for him.  I've had quite a few software related problems, though.

1.  Even though it was suppost to ship with Hardy, it shipped with Gutsy.  I'm thinking I should upgrade to Hardy.  Is the following image supported by the Inspiron 1525?  (It says it supports 1525n - I'm not sure if that's the same thing.)  [http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Dell_OS_Factory_Recovery_8.04.1_DVD_ISO)

Sure will work fine.

> 
2.  Ubuntu-restricted-extras does not work.  This means that I can not get Microsoft Fonts or certain multimedia codecs.  The Totem browser plug-in does not work, either.  I have a theory - I looked at the repositories, and it looked shorter than I remember it being.  Did Dell trim it down?  If so, is it still trimmed down in the image above?  Would it be worth my while to just install the official Hardy image?  Of course, if Dell didn't trim down sources.list, what's going on here?

You can open up software-properties-gtk to turn on any missing components.  Dell doesn't trim the sources.list.  Make sure you do all your updates though so that everything is populated.

The nonfree Fluendo codec pack is only available when purchased with hardy (not on that ISO image).  The microsoft fonts are in the repo, as are the free codec pack.

> 
3.  Steam (running through WINE, installed with Plays On Linux) will not work.  When I click on it, it opens and I can see the client for about five seconds.  It then randomly closes.

I'd say run it from a terminal and look for interesting output.

> 
4.  Wireless drivers are included by default, but it's really weird.  It won't connect to my home network by default - it always connects to the neighbor's (it's unprotected, mine is not).  How do I get it to connect to mine by default?  Also, once it's connected to a network, I can't click on another on the list.  It just does nothing.
You have to elaborate more on what wireless you are using.  You can consider using the network manager editor to go in and remove all wireless networks and try again from scratch.

---

