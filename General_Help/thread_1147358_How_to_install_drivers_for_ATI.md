---
title: "How to install drivers for ATI?"
date: 2009-05-03
forum: General Help
---

### Post by VyperX on 2009-05-03
Hello, I'm having some graphic problems because I dont have the ATI drivers installed yet... I dont know how to install them (I'm a linux noob)
My video card is ATI X1200...

Here is an image of the problem...
[http://img10.imageshack.us/img10/2373/screenshotinitializatio.png]("http://img10.imageshack.us/img10/2373/screenshotinitializatio.png")

---

### Post by jcm1107 on 2009-05-03
> **VyperX said:**
> Hello, I'm having some graphic problems because I dont have the ATI drivers installed yet... I dont know how to install them (I'm a linux noob)
My video card is ATI X1200...

Here is an image of the problem...
[http://img10.imageshack.us/img10/2373/screenshotinitializatio.png]("http://img10.imageshack.us/img10/2373/screenshotinitializatio.png")

Did you try using synaptic package manager to install the drivers?
just go to system-admin-synaptic package manager.

---

### Post by BslBryan on 2009-05-03
I've got instructions for you to try, but first I need to know what version of Ubuntu you're using.  (7.10, 8.04, 8.10, 9.04)?

:)

---

### Post by VyperX on 2009-05-03
I dont know what to look for in the  synaptic package manager in order to install the drivers...

And I'm using 9.04....

---

### Post by miegiel on 2009-05-03
> **VyperX said:**
> Hello, I'm having some graphic problems because I dont have the ATI drivers installed yet... I dont know how to install them (I'm a linux noob)
My video card is ATI X1200...

Here is an image of the problem...
[http://img10.imageshack.us/img10/2373/screenshotinitializatio.png]("http://img10.imageshack.us/img10/2373/screenshotinitializatio.png")

I strongly suggest the restricted drivers that come with ubuntu. These have quite a few issues, but so do the drivers you can download from ATI. And the drivers from the ubuntu repository will automatically update with the rest of ubuntu. If you decide to get the linux drivers from ATI anyway, make sure they support your card. IIRC the latest linux catalyst drivers don't support the X1200 anymore and you'll need to get an older version of the catalyst drivers.

After installing ubuntu you get a icon in your system tray asking if you want to install the restricted drivers. You can also install/activate them by going to *System > Administration > Hardware Drivers*.

---

### Post by BslBryan on 2009-05-03
```
sudo apt-get install envyng-qt
```

This will install Envy.  It's a program used to install and configure nVIDIA and ATI drivers.

Then, it should be in your Applications --> System Tools menu, but you could also type 
```
sudo envyng -t
```

Then, follow the instructions for the ATI driver.

Good luck. :)

---

### Post by VyperX on 2009-05-03
> **BslBryan said:**
> ```
sudo apt-get install envyng-qt
```

This will install Envy.  It's a program used to install and configure nVIDIA and ATI drivers.

Then, it should be in your Applications --> System Tools menu, but you could also type 
```
sudo envyng -t
```

Then, follow the instructions for the ATI driver.

Good luck. :)

Are you sure that this will fix my problem... because I'm thinking of uninstalling ubuntu 9.04 and installing ubuntu 8.10...

---

### Post by BslBryan on 2009-05-03
It's worth a shot.  :)

---

### Post by BslBryan on 2009-05-03
Also, if that doesn't work the other simple solution is to go to
System --> Administration --> Hardware Drivers and install and activate the proprietary driver.

If you want simple solutions, this doesn't work, and you don't want to mess with it any more, than install 8.10.  If you like Jaunty otherwise, I have a few more suggestions. :)

---

### Post by VyperX on 2009-05-03
> **BslBryan said:**
> Also, if that doesn't work the other simple solution is to go to
System --> Administration --> Hardware Drivers and install and activate the proprietary driver.

If you want simple solutions, this doesn't work, and you don't want to mess with it any more, than install 8.10.  If you like Jaunty otherwise, I have a few more suggestions. :)

There are no drivers available for ATI in Hardware Drivers... should I install 8.10?

---

### Post by BslBryan on 2009-05-03
Did you already try to use Envy?

---

### Post by VyperX on 2009-05-03
> **BslBryan said:**
> Did you already try to use Envy?

No, I will... I'm currently facing another problem... I dont know if you can help me... This happened to me when I used Gutsy Gibbon time ago, I actually fixed the problem with a  guide... but the link to the guide  wont work... my problem is that ubuntu wont detect my wireless card... it's an AR5007EG and heres the link to the guide (it wont open)
[http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007]("http://home.nyc.rr.com/computertaijutsu/rhwireless.html#5007")

Heres a link to the thread which helped me out to solve this problem ( the wireless one)
[http://ubuntuforums.org/showthread.php?t=729079]("http://ubuntuforums.org/showthread.php?t=729079")

Thanks!

---

