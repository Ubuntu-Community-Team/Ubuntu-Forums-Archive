---
title: "making commands run on boot up"
date: 2009-02-08
forum: General Help
---

### Post by wawacito on 2009-02-08
Hello all,

I've been trying to get help with a webcam issue but got zero replies.  
[http://ubuntuforums.org/showthread.php?t=1056511](http://ubuntuforums.org/showthread.php?t=1056511)

Eventually after a week and hours upon hours of websearching i finally found a solution on my own.  Basically I have to do this:

sudo rmmod uvcvideo
sudo modprobe uvcvideo quirks=16


Thing is - I have to do this EVERYtime i boot.

Is there a way to make this happen automagically? kind of like equivalent to a "autoexec.bat" in windows/dos? (yes im *trying* to make the switch to linux but im unhappy to find that i have to fight through every single stinkin step of the way)

alternatively - it looks like those commands above are unloading the uvcvideo module and then reloading it - is there a way to load it the right way (with the quirk=16 option) the first time?


please show me that support from the ubuntu community is as good as everybody says - so far i have been sorely disappointed and am very close to quiting and going back to windows

---

### Post by tehforum on 2009-02-08
[http://linux.about.com/od/ubuntu_doc/a/ubudg28t5.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg28t5.htm)

Is that of any help?

---

### Post by wawacito on 2009-02-08
i should probably include some of this just in case somebody asks

Intrepid Ibex 8.10 with all updates installed
Kernel 2.6.27-11-generic

Lenovo thinkpad SL400

---

### Post by wawacito on 2009-02-08
@tehforum - does this happen before or after the standard uvcvideo load?

if it happens after - then i need to include the rmmod statement above
if it happens before then i don't need the rmmod statement

right?

---

### Post by wawacito on 2009-02-08
didn't work i tried it both ways: with and without sudo

inside the crontab -e editor i added

@reboot rmmod uvcvideo
@reboot modprobe uvcvideo quirks=16


that didnt work - so i edited it again with sudo in front - didnt work either

---

### Post by HermanAB on 2009-02-08
You can put boot commands in /etc/rc.d/rc.local

Cheers,

Herman

---

### Post by wawacito on 2009-02-09
there is no /etc/rc.d/ directory

there is 
/etc/rc0.d
/etc/rc1.d
/etc/rc2.d
/etc/rc3.d
/etc/rc4.d
/etc/rc5.d
/etc/rc6.d
/etc/rcS.d

none of them have an rc.local file

---

