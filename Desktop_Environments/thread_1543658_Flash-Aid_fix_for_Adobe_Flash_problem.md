---
title: "Flash-Aid fix for Adobe Flash problem"
date: 2010-08-01
forum: Desktop Environments
---

### Post by chettyk on 2010-08-01
This is not a request for help, but to say that Flash-Aid, the Firefox extension, helped sort out a recurrent problem that I was having with Adobe Flash player. I thought I should pass on this experience so that anyone else having the same problem could benefit.

Just recently, I got around to loading Ubuntu Lucid Lynx (32-bit) on my two laptops, one an aging Compaq Presario 2200 and the other an Asus EEE-PC 1000H. (The EEE-PC looks terrific with Lucid Lynx running on it.)

I installed the ubuntu-restricted-packages on both machines so that I could have MP3 support, Flash player and so on available.

But, to my immense frustration, I found that the Adobe Flash player would crash as soon as I opened any web page with Flash content in either Mozilla or Chrome browsers.

Then, after reading the thread [http://ubuntuforums.org/showthread.php?t=1491268]("http://ubuntuforums.org/showthread.php?t=1491268"), I installed the Flash-Aid extension. Flash-Aid uninstalled the Flash version that existed, and then downloaded and installed a fresh one. That sorted out the problem that I was having. Great!

Is it the case that the ubuntu-restricted-package installed the wrong type of Flash player or what? Anyway, I am happy to have a nagging problem fixed.

Cheers.

---

### Post by lovinglinux on 2010-08-01
I'm glad to see my extension being appreciated. Thanks for your comments.

The problem is not ubuntu-restricted-extras, but the alternative plugins and the manually installed ones.

---

### Post by chettyk on 2010-08-01
> **lovinglinux said:**
> 
The problem is not ubuntu-restricted-extras, but the alternative plugins and the manually installed ones.

Thanks lovinglinux for your Firefox extention - and your message.

But I'd like to understand your explanation a bit more. As far as I could judge from what appeared on the terminal window, Flash-Aid uninstalled the Adobe Flash that was on my two laptops. It then downloaded a fresh copy of the software and installed that.

As I said in my first message, I installed Flash support through the ubuntu-restricted-extras package. I did, however, install Adobe Acrobat Reader manually. But I didn't see Flash-Aid change that software.

So what sort of "alternative plugins and the manually installed ones" might interfere with Flash?

Cheers

---

### Post by lovinglinux on 2010-08-01
> **chettyk said:**
> 
So what sort of "alternative plugins and the manually installed ones" might interfere with Flash?

There are two open source flash plugins in the repositories, called swfdec and gnash. If they are installed already, then they are detected by Firefox even if you install the version from Adobe. Since these alternative plugins are usually behind Adobe in regard to compatibility and features, you get error messages and sometimes crashes depending on the system and web site. 

In Ubuntu there are several folders to where the flash plugin shared object is linked when you install it. If one of these symlinks are not present, flash could fail to be loaded, depending on the program you are using. Additionally, the user could extract the flash plugin shared object from a manual download to a user folder, in order to override the system version. If this shared object has incompatibilities, flash will fail no matter how many times you install ubuntu-restricted-extras.

So what FLASH-AID does is to remove the flash shared object from all those possible locations and remove the open source alternatives, then re-install flash. Is like a flash plugin reset.

---

