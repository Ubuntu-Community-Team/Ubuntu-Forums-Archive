---
title: "unable to mount iPhone 3GS since recent updates"
date: 2011-05-30
forum: Desktop Environments
---

### Post by eltonw on 2011-05-30
I was quite pleased to see that Ubuntu 11.04 now loads and reads the contents of my iPhone 3GS.
(Once I connect the phone to my netbook, Shotwell and Banshee would recognize the cell-phone and give me options to manage my data.

_Alas, that joy has been very short-lived._ As of the most recent updates, something appears to have 'broken' this functionality. [TODAY's DATE: Monday, 30 May, 2011],

Now when I connect the phone Nautilus _[COLOR="DarkRed"]fails to mount it[/COLOR]_, and I consistently get the *[COLOR="DarkRed"]same error message[/COLOR]*:
"[FONT="Georgia"]DBus error org.freedesktop.DBus.Error. NoReply:
Message did not receive a reply (timeout by message bus)[/FONT]" :frown:

Is there a fix for this?

TIA for any assistance or pointers to a solution.

---

### Post by volkstech on 2011-06-07
Found the fix! 

  [http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/](http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/)

---

### Post by eltonw on 2011-06-08
> **volkstech said:**
> Found the fix! 

  [http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/](http://www.multimediaboom.com/iphone-not-recognized-after-upgrading-ios-4-2-in-ubuntu-heres-how-to-solve-the-problem/)
The above link is dated December 6th, 2010. It relates to iPhones with iOS 4.**2**.

So....does this fix work for YOU? IF you read my original post, I stated that:

1) My IPhone has IOS 4.**3**
2) The pmcenery fix was applied.
3) This fix did not work for me _when I installed it_, nor after the usual and most recent channel updates.:(

[FONT="Franklin Gothic Medium"][COLOR="DarkRed"]Can someone confirm IF the pmcenery fix is working after the most recent updates to ubuntu 11.04?[/COLOR][/FONT]

---

### Post by &#5097;&#5103;waya on 2011-06-12
Also for iPad it seems.

---

### Post by inhumangeek on 2011-07-11
I'm having the same issue. Installed 11.04 a while ago, iPhone 4 (iOS 4.3) was working... now it's not.

Perhaps I'll contact pmcenery

---

### Post by Futtermania on 2011-07-24
I've got the same problem. Iphone 3gs 4.3.3 Ubuntu 11.04. Tried fixes i found in forum and online - no joy.

---

### Post by regionsofsorrow on 2011-07-27
I'm experiencing the same problem - iPhone 3gs, IOS 4.2, Ubuntu 11.04. Also tried all known fixes.  The device is mounted flawlessly on another laptop running 10.10, which I daren't upgrade for this reason.

---

### Post by regionsofsorrow on 2011-09-16
If anyone who's posted here's still interested, and for anyone looking for a solution to this problem: I've tried this fix for iPhone 4 with success

[http://ubuntuforums.org/showthread.php?t=1828465]("http://ubuntuforums.org/showthread.php?t=1828465")

```
idevicepair unpair
idevicepair pair
idevicepair validate
```

After plugging in the device and executing these commands, the iPhone was automatically mounted.

---

