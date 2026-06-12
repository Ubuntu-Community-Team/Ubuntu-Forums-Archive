---
title: "xorg trouble after enabling ctrl+alt+backspace in 9.04"
date: 2009-04-22
forum: Desktop Environments
---

### Post by raymondh on 2009-04-22
Sorry for the double post ... did not realize I had posted my woes on a sticky at the Jaunty dev/test forum.

This is on 9.04 RC

I wanted to enable the crt+alt+backspace combo and edited my xorg.conf.  This is what I added:

> Section "ServerFlags"
   Option   "DontZap"   "False"
EndSection

I then saved, closed,rebooted, tested and used the combo keys successfully a number of instances yesterday and today.  From hereon, I messed up.  Someone advised me to (taken from xorg.conf):

[PHP] Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg[/PHP]

Arrggh ... I now COULD NOT boot into my Ubuntu.  About 5 secs into splash, my screen goes blank/black with some vertical lines on the top 5th portion.  This stays this way for about 20-30 mins.  I tried to go into recovery mode to "fix graphical problems" to no avail.  I get this message :

> xserver-xorg postinst warning: overwriting possiblly-customized configuration file. Back up in /etc/x11/xorg.conf    and I have no idea how to get to that back-up file.

I also tried using the terminal and root in recovery and typed: 

```
sudo dpkg-reconfigure xserver-xorg
```  also to no avail

I don't know what to do now except 

a) kick myself for messing with something that already works, and/or
b) to a fresh install

Help ..... arrrrgh.

Raymond

---

### Post by raymondh on 2009-04-22
tried cp goodfile badfile .... restarted .... splash would finish but I still get a black/blank monitor.

Help

---

### Post by Claus7 on 2009-04-22
Hello,

the sudo.. command won't get you anywhere. You said that you copy pasted a good file to a bad one. Do you know exactly which were these files? How did you choose them on the first place. If it said that your "original-good" file was backed-up then it should be in /etc/X11/xorg.conf.backup or something like that. Now what I would do if I were in your shoes would be to:
cd /etc/X11/
sudo cp xorg.conf xorg.conf.last
sudo cp xorg.conf.backup xorg.conf

There wasn't another way to enable this combination of keys? 

Regards!

---

### Post by raymondh on 2009-04-22
> **Claus7 said:**
> Do you know exactly which were these files? How did you choose them on the first place. 

postinst warning says that the backup file is in /etc/X11/xorg.conf.20090422143028

Do I go ahead with your advice to

```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.last
sudo cp xorg.conf.backup xorg.conf
```


I got so used to ctrl-alt-backspace to discipline a misbehaving app.  That combo key is disabled (as you know) and the "new" key is altR + sysreq + k.

---

### Post by Claus7 on 2009-04-23
Hello,

i) the command I gave you:
cd /etc/X11/

is to go inside the folder where the files in question are placed.

ii)sudo cp xorg.conf xorg.conf.last
with this command I just tell you to backup your existing xorg.conf file even if it is not working as it is supposed to. You might want to check it later and do some comparisons with the one that it is working. I named it randomly xorg.conf.last. You can name it as you like (last goes for the last xorg you have at the time, give it whatever name you like).

Also sudo goes for root priviledges. As a regular user you cannot change the contents of the folder in question (/etc/X11).

iii)So taking into account what you said in your last post, the most important command you can type is:
sudo cp xorg.conf.20090422143028 xorg.conf

That way, as root, you will place a backup file (hope the one that it was working) to the place of the xorg.conf which is the file that your system recognises.

Reboot and see what it will happen.

Regards!

---

### Post by raymondh on 2009-04-23
Thanks for your efforts.

Could not get to the back-up file from recovery mode.  Anyways, I decided to practice on "maybe-forgotten" installation skills and did a fresh install.

Thanks anyway.

Best,

Raymond in "don't-mess-with-a-working-install" mode.  

PS .... Could not install dontzap thru terminal. Don't know why ... will not bother to know why.  

Re-did editing xorg.conf, saved, closed and rebooted and tested combo keys ctrl-alt-backspace as many times as I could.  All works.  

In my experience, after saving and closing the /etc/X11 file, there is/was no need for this even though it was stated in the file (which started my woes in the first place):

[HTML]# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg[/HTML]

Again, I may have troubles when it comes time to update (though I've updated 3x after just to check ... no prob) but, i'll cross the bridge when i get there.

Other folks opinions may vary.

---

### Post by Claus7 on 2009-04-23
Hello,

its nice that you solved your problem. The process I described you, can be followed any time, if you mess with your file and want to put it back. If you do not bother, you can have from now a backup of your original xorg.conf file so as to be on the safe side if, as you say, an update messes up your existing configuration. After sometime I do not think that it is a good idea to go and reinstall your os.

Yes, if something works it is best not to mess with it, yet without experimenting a little, you do not learn. 

I cannot help you with dontzap.

Regards!

---

### Post by juanbretti on 2009-04-25
How do I get back my "ctrl+alt+backspace"?

[https://answers.launchpad.net/ubuntu/+question/63011](https://answers.launchpad.net/ubuntu/+question/63011)

Thanks!

---

### Post by juanbretti on 2009-04-26
Is there any way to restart the Gnome by command line?
Something like: "xserver -restart"?

---

### Post by djbushido on 2009-04-26
Uh, logging out restarts gdm which restarts X which restarts Gnome...

---

### Post by juanbretti on 2009-04-26
> **djbushido said:**
> Uh, logging out restarts gdm which restarts X which restarts Gnome...
So, logging out is the same as "Ctrl+Alt+Backspace?

---

### Post by djbushido on 2009-04-26
Yes. Actually, it is. But logging out usually means that you've saved your work first.

---

### Post by juanbretti on 2009-04-26
> **djbushido said:**
> Yes. Actually, it is. But logging out usually means that you've saved your work first.
Oh, I didn't knew that logging out will restart X.

Thanks!

---

### Post by juanbretti on 2009-04-28
Here's another solution:
[http://webupd8.blogspot.com/2009/04/ctrl-alt-backspace-disabled-in-most.html](http://webupd8.blogspot.com/2009/04/ctrl-alt-backspace-disabled-in-most.html)

> Press **AltGR + SysRQ + K** instead (AltGR is the RIGHT ALT button and SysRQ is labelled "Print Screen" most of the times, and remeber to press and hold the keys in the in the right sequence, eg. starting with ALtGR, and ending with the K(ill) key).

---

### Post by djbushido on 2009-04-30
Sorry for the long post interval, but logging out kills all user processes, thus displays get reset.

---

