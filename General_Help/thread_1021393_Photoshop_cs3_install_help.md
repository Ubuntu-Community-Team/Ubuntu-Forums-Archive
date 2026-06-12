---
title: "Photoshop cs3 install help"
date: 2008-12-25
forum: General Help
---

### Post by SonnHalter on 2008-12-25
ok i have the cd loaded. i went to the cd browser-adobe cs3 and right clicked "setup.exe" chose "open with wine program loader"

and then nothing happens. nothing.


help?

wine forum=lack of support

---

### Post by socrazy143 on 2008-12-25
I found this archived Ubuntu forum:

[http://ubuntuforums.org/archive/index.php/t-447287.html](http://ubuntuforums.org/archive/index.php/t-447287.html)

With a link to this blog that talks about CS2.  As the poster said in the forum you can give it a try and see if it helps.

[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

Any particular reason you aren't giving [GIMP]("http://www.gimp.org") a try?  I just used it last night to edit a screenshot and it keeps getting better and better.

You can get it from APT with:

```
apt-get install gimp
```

---

### Post by albinootje on 2008-12-25
> **SonnHalter said:**
> ok i have the cd loaded. i went to the cd browser-adobe cs3 and right clicked "setup.exe" chose "open with wine program loader"

and then nothing happens. nothing.

See here :
[http://ubuntuforums.org/showthread.php?p=6435080#post6435080](http://ubuntuforums.org/showthread.php?p=6435080#post6435080)
And :
[http://ubuntuforums.org/showthread.php?t=857033](http://ubuntuforums.org/showthread.php?t=857033)

---

### Post by namdung on 2008-12-25
[http://ubuntuforums.org/showthread.php?t=1021335](http://ubuntuforums.org/showthread.php?t=1021335)

---

### Post by SonnHalter on 2008-12-25
links didn't help :( 

i just need to know how to run the setup

---

### Post by albinootje on 2008-12-25
> **SonnHalter said:**
> links didn't help :( 

i just need to know how to run the setup

Do you have Wine installed actually ? 
You can run "winecfg" and then under "Drives" you can add your cdrom-drive.

Did you install Wine 1.1.1 which has a fix for installing Photoshop CS3 ?

---

### Post by SonnHalter on 2008-12-25
yes i installed wine 1.1.1

and 

my disc drive is already listed under "drives

---

### Post by SonnHalter on 2008-12-25
i'm following this guide [http://www.wine-reviews.net/applications/photoshop-cs3-on-linux-with-wine.html](http://www.wine-reviews.net/applications/photoshop-cs3-on-linux-with-wine.html)

after i use the wine setup i get an error saying

wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

---

### Post by SonnHalter on 2008-12-25
i'm following this guide [http://www.wine-reviews.net/applications/photoshop-cs3-on-linux-with-wine.html](http://www.wine-reviews.net/applications/photoshop-cs3-on-linux-with-wine.html)

after i use the wine setup i get an error saying

wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

---

### Post by SonnHalter on 2008-12-25
bump

---

### Post by igknighted on 2008-12-25
The appdb is currently down (but the link would be [http://appdb.winehq.org](http://appdb.winehq.org)).  I don't think CS3 really works in linux.  I would try VirtualBox in seamless mode.

---

### Post by dankegel on 2008-12-25
> **SonnHalter said:**
> 
wine: could not load L"C:\\windows\\system32\\setup.exe": Module not found

That means you aren't in the right directory.  You need to use
the cd command to change to the directory containing your cdrom.

[http://wiki.winehq.org/FAQ](http://wiki.winehq.org/FAQ) should have the answer to your question,
but maybe it doesn't yet.

See also [http://wiki.winehq.org/AdobePhotoshop](http://wiki.winehq.org/AdobePhotoshop) for more tips about photoshop.

---

### Post by FrankVdb on 2008-12-28
Apparently, CS3 is not supported yet.


[http://www.wine-apps.org/content/show.php/show.php?content=92676&vote=bad&tan=52445649&PHPSESSID=2a32ea47dd35b947eb4246e69079adb0](http://www.wine-apps.org/content/show.php/show.php?content=92676&vote=bad&tan=52445649&PHPSESSID=2a32ea47dd35b947eb4246e69079adb0)

---

### Post by Skripka on 2008-12-28
> **FrankVdb said:**
> Apparently, CS3 is not supported yet.


[http://www.wine-apps.org/content/show.php/show.php?content=92676&vote=bad&tan=52445649&PHPSESSID=2a32ea47dd35b947eb4246e69079adb0](http://www.wine-apps.org/content/show.php/show.php?content=92676&vote=bad&tan=52445649&PHPSESSID=2a32ea47dd35b947eb4246e69079adb0)

It is unlikely it will be IMHO-the problem is the installer.  If you bypass the installer via underhanded less than legal means-Photoshop CS3 works....BUT, the installer will not run under Wine.

---

### Post by Lazerouth on 2008-12-28
I work in photography on a professional basis. Used to be a Photoshop fan. With Gimp 2.6, I'm faltering in my beliefs, give it a week to get used to it, you won't be dissapointed.

---

