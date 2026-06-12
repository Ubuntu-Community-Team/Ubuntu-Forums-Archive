---
title: "installing wine HQ in non-internet connected Dapper"
date: 2009-03-07
forum: General Help
---

### Post by waxwing_user on 2009-03-07
Hello,

I've been trying to install WineHQ in a dapper-installed machine that is not connected to the internet.  I am using a USB drive to transfer the packages.  When I try to install Wine, I get plenty of activity transfering files, etc. but when I go to look for it anywhere (menu, file manager...)...no Wine.  Any Ideas what's wrong?

-Andrew

---

### Post by taurus on 2009-03-07
If you think you have installed wine on your machine, open a terminal and look to see if it's on your system at all.

Applications -> Accessories -> Terminal
```
whereis winecfg
-or-
whereis wine
```

---

### Post by waxwing_user on 2009-03-07
Thanks for the info.  I checked and it is indeed there.  So now the question is, where is Wine in the menu?  I have it on my own computer (Dell Laptop) and have installed it there in the past without any problems but it doesn't seem to want to display on this older machine.  Yelp!!

---

### Post by waxwing_user on 2009-03-07
And how do I run it?  Thanks

---

### Post by dcstar on 2009-03-07
> **waxwing_user said:**
> And how do I run it?  Thanks

You don't "run" it, it is used by Windows programs. There are already plenty of instructions on using things with wine.

---

### Post by waxwing_user on 2009-03-07
That makes sense.  Okay...I have some exe files that I want (or need) to run for an NIC.  When I run them I get "Couldn't Display "home/rick/Desktop/3c90xcpg.exe"  I thought I was getting that because Wine wasn't properly installed.  True?

---

### Post by taurus on 2009-03-07
Try to configure it first before you use it to install a windows app.

```
winecfg
```

Then, 
```
cd ~/Desktop
wine 3c90xcpg.exe
```

---

### Post by waxwing_user on 2009-03-08
Thank you taurus and DCstar for advising me.  The steps worked to a point but I still couldn't get exe files to run nor do I know why Wine wouldn't show up on the menu.  Unfortunately, there is still much to do and I've run out of time.  Sadly, I must return Windows (ugh!) to the machine and let the owner (my brother) deal with it until such time as HE has to invest in making the change.  They (microsoft) won't get me without a fight though.  I will still put open source applications on the machine.  WE WILL PREVAIL!!

---

