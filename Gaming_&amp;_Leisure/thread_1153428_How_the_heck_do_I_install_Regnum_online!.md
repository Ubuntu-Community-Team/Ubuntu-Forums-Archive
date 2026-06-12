---
title: "How the heck do I install Regnum online?!"
date: 2009-05-08
forum: Gaming &amp; Leisure
---

### Post by xakh on 2009-05-08
I downloaded the danged file, but I just can't get it to work!

---

### Post by hansdown on 2009-05-08
Hi xakh.

This may help.

[http://www.google.ca/search?q=Regnum+online+in+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Regnum+online+in+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by xakh on 2009-05-08
I'm still quite lost. Is there a precompiled package I can get?

---

### Post by hansdown on 2009-05-08
You can find more knowledgable information here.

[http://www.regnumonline.com.ar/forum/showthread.php?t=41090](http://www.regnumonline.com.ar/forum/showthread.php?t=41090)

---

### Post by xakh on 2009-05-08
I don't think you're following me. I'm not having trouble running Regnum. I am having trouble installing it. No problems running it yet, because it has not installed.

---

### Post by Catboy~ on 2009-05-08
Give this a try, go to Places->Home Folder 
Now create a new folder called something like ".regnum"
Put the file you downloaded into that folder, now right click on the file you downloaded, click properties, and go into the permissions tab. Check the little thing that says "Allow this file to be ran as an executable"
Now just double-click the file, and voila! It should be working.:)

---

### Post by Bölvaður on 2009-05-09
> **Catboy~ said:**
> Give this a try, go to Places->Home Folder 
Now create a new folder called something like ".regnum"
Put the file you downloaded into that folder, now right click on the file you downloaded, click properties, and go into the permissions tab. Check the little thing that says "Allow this file to be ran as an executable"
Now just double-click the file, and voila! It should be working.:)



[Installing - Executable files]("http://www.youtube.com/watch?v=B6QrBtk3U4o")

---

### Post by Warpnow on 2009-05-09
> **xakh said:**
> I don't think you're following me. I'm not having trouble running Regnum. I am having trouble installing it. No problems running it yet, because it has not installed.

Try this, assuming you have the 32 bit one, if not then just replace the numbers so the filename matches.

Navigate to where you downloaded the file.

sudo chmod +x RegnumOnlineInstall_32
./RegnumOnlineInstall_32

---

### Post by xakh on 2009-05-09
I've tried every one of these install tips, and it gives me this:
application-specific initialization failed: bad end of central directory record
%
every time.

---

### Post by proksy on 2010-01-21
> **xakh said:**
> I've tried every one of these install tips, and it gives me this:
application-specific initialization failed: bad end of central directory record
%
every time.

Ya Im stuck at this point too...I'm noobuntu

---

### Post by Ruskiy Letenant on 2010-01-26
[Catboy~]("http://ubuntuforums.org/member.php?u=745336") You are amazing, thanks for the simplest and best working answer i've seen for something in too long. Thanks.

---

### Post by Ruskiy Letenant on 2010-01-30
Anybody get this?

---

### Post by knighthaq on 2010-01-30
hey i just tried it and installed fine no problems, except when i launch the application after install all i get is a blank screen.

---

### Post by Tribalwarrior on 2010-02-02
please help me too. i tried to install it everything wo'ked until it finished installing it replied with a 'Error in executable action'
and a 'Error install uninstall' help would be much appreciated.

---

### Post by Don Mega on 2010-04-29
the "sudo chmod +x RegnumOnlineInstall_32"
and "./RegnumOnlineInstall_32"
works fine learn to navigate in a terminal using root user and you will get it
type " su " to get into root user mode if your password doesn't work type " sudo passwd " to create a unix password it'll ask for a password first this is your user password then it'll ask for your new unix password then when you finish type " su " then your new unix password then woola your now in root user mode then type " cd /your/downloaded/file/directory " (not literally find the specific location) then then type the in the commands above if this doesn't work delete the file and download a fresh one. GOOD LUCK

---

### Post by ViceWolf on 2010-06-25
Hy i have a problem, i loaded it but it keeps giving me this strange pop up message it says that, 
i dont have an up to sate video card (even though i can play UT3)
i dont have all the drivers loaded
or i dont have the latest directX

can any one help me with this???


i am running 10.4, on a dell, 

also if any one knows how to get a web cam running that would be nice, but game first.

---

### Post by Klanek on 2010-07-27
> **ViceWolf said:**
> Hy i have a problem, i loaded it but it keeps giving me this strange pop up message it says that, 
i dont have an up to sate video card (even though i can play UT3)
i dont have all the drivers loaded
or i dont have the latest directX

can any one help me with this???


i am running 10.4, on a dell, 

also if any one knows how to get a web cam running that would be nice, but game first.

update your graphics drivers... and to play regnum!!  :p

---

### Post by Dusty2711 on 2010-11-27
Hey guys I have my own question. I downloaded the game all went good the game starts but...All the players are black and every thing else is fine. Do you guys know what this could be. Hope you guys can help.

---

### Post by myromance123 on 2010-11-28
To those who are having graphics errors and problems, please state your graphics card vendor, card number, and your graphics driver version.

 For example:
 Nvidia GeForce 9600 GT driver 190.xx

 or 

 ATI/AMD Radeon 4850 driver xx.xx

This will help us know if its that your graphics card is too old and unsupported, or if your driver is outdated, or if its a general problem with Regnums graphics.

---

