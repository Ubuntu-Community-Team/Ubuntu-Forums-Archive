---
title: "My Ubuntu is broken"
date: 2006-09-29
forum: Desktop Environments
---

### Post by pod25 on 2006-09-29
I needed to reboot my comp, before I did reboot everything was working just fine.
So I reboot, I get to my login screen and I login, the comp then begins to load the desktop, then it loops back to the login screen, so I login again and the same thing happens over and over again.
Why is it doing this, and can it be fixed ?

---

### Post by bigken on 2006-09-29
boot into a treminal and try this sudo aptitude install ubuntu-desktop

---

### Post by Titan_Prometheus on 2006-09-29
I think it has to do with a broken X configuration, or a broken Gnome configuration. I've had this problem happen before when I was experimenting with XGL, it would load, so I just gave up. I would recommend running dpkg-reconfigure xserver-xorg and dpkg-reconfigure ubuntu-desktop

---

### Post by pod25 on 2006-09-29
> **Titan_Prometheus said:**
> I think it has to do with a broken X configuration, or a broken Gnome configuration. I've had this problem happen before when I was experimenting with XGL, it would load, so I just gave up. I would recommend running dpkg-reconfigure xserver-xorg and dpkg-reconfigure ubuntu-desktop

Ok, I tried the dpkg-reconfigure ubuntu-desktop as this is what I have installed, but, it comes back with ubuntu-desktop is not installed ? but I know it is.

---

### Post by pod25 on 2006-09-29
If I re-install the ubuntu-desktop, will that effect any of my settings ?

---

### Post by ajgreeny on 2006-09-29
I don't think so, but if your settings are not working does it really matter?

---

### Post by eylisian on 2006-09-29
You will not loose any settings that are in your home directory by invoking dpkg-reconfigure <package name>

If you want to troubleshoot it "alt-ctl-F1" to a virtual terminal and login there. Using your sudo powers look at both /var/log/messages and the X server logs /var/log/Xorg.0.log

you can use tail, less and grep to maybe find something out about what hidious thing happened to your box.

sudo dmesg |tail 

sudo tail -n 20 /var/log/messages  Right after it fails to work correctly might yeild some good results. 

sudo less /var/log/Xorg.0.log |grep LoadModule  Will show you if any modules (drivers) are being skipped (if you know which modules load normally).

If you have a /var/log/auth.log tail it... And please, If have any hassles post back here in as much detail as you can manage and we can keep on working it.

peas.

---

### Post by pod25 on 2006-09-29
This is what i get from auth.log :
```
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Fri Sep 29 17:24:55 2006 from podmedia
admin@podserver:~$ sudo tail -n 20 /var/log/auth.log
Sep 29 14:46:47 pod25 gdm[4327]: (pam_unix) session closed for user admin
Sep 29 14:47:03 pod25 perl: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Sep 29 14:47:06 pod25 webmin[6039]: Webmin starting
Sep 29 14:54:58 pod25 sshd[6360]: Accepted password for admin from 192.168.1.202 port 1150 ssh2
Sep 29 14:54:58 pod25 sshd[6364]: (pam_unix) session opened for user admin by (uid=0)
Sep 29 15:00:02 pod25 CRON[6443]: (pam_unix) session opened for user root by (uid=0)
Sep 29 15:00:02 pod25 CRON[6444]: (pam_unix) session opened for user root by (uid=0)
Sep 29 15:00:02 pod25 CRON[6444]: (pam_unix) session closed for user root
Sep 29 15:54:22 pod25 saslauthd[5029]: detach_tty      : master pid is: 5029
Sep 29 15:54:22 pod25 saslauthd[5029]: ipc_init        : listening on socket: /var/spool/postfix/var/run/saslauthd/mux
Sep 29 15:54:23 pod25 sshd[5049]: Server listening on :: port 22.
Sep 29 15:54:23 pod25 gdm[4332]: (pam_unix) session opened for user admin by (uid=0)
Sep 29 15:54:46 pod25 gdm[4332]: (pam_unix) session closed for user admin
Sep 29 15:55:03 pod25 perl: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root
Sep 29 15:55:06 pod25 webmin[6071]: Webmin starting
Sep 29 15:55:26 pod25 gdm[5759]: (pam_unix) session opened for user admin by (uid=0)
Sep 29 15:55:46 pod25 gdm[5759]: (pam_unix) session closed for user admin
Sep 29 16:00:01 pod25 CRON[6550]: (pam_unix) session opened for user root by (uid=0)
Sep 29 16:00:01 pod25 CRON[6549]: (pam_unix) session opened for user root by (uid=0)
Sep 29 16:00:01 pod25 CRON[6550]: (pam_unix) session closed for user root
```

---

### Post by pod25 on 2006-09-29
> **Titan_Prometheus said:**
> I think it has to do with a broken X configuration, or a broken Gnome configuration. I've had this problem happen before when I was experimenting with XGL, it would load, so I just gave up. I would recommend running dpkg-reconfigure xserver-xorg and dpkg-reconfigure ubuntu-desktop

I now got dpkg-reconfigure ubuntu-desktop to work, but my problem is still present.
So I then tried dpkg-reconfigure xserver-xorg but this asks questions about my video card I simply do not have the answers for.

I'm running out of ideas.
Does ubuntu break this easliy normally ?

---

### Post by oldgit on 2006-09-29
I had this once, turned out my /home partition was full, check your wastebasket directory.

---

### Post by pod25 on 2006-09-29
> **oldgit said:**
> I had this once, turned out my /home partition was full, check your wastebasket directory.

I'm pretty sure it's empty, however I
how can I check if I can not login, I presume there is a command for that via terminal ?

---

### Post by oldgit on 2006-09-29
df will tell you how full your /home is
cd ~/.Trash gets you into your trash directory
ls to list it

---

### Post by pod25 on 2006-09-29
9% , so it's not my trashcan

---

### Post by oldgit on 2006-09-29
Sorry, I'm out of ideas now, best of luck with this.

---

### Post by pod25 on 2006-09-29
Any more suggestions ? I'm really stuck now, I've also spent ages setting this ubuntu server up, so it would be a proper kick in the teeth to start again.

---

### Post by Old Pink on 2006-09-29
> **pod25 said:**
> Any more suggestions ? I'm really stuck now, I've also spent ages setting this ubuntu server up, so it would be a proper kick in the teeth to start again.

Wait a few weeks if you have an alternate computer, and upgrade to Edgy via terminal when it stablizes. 

Otherwise, use terminal to copy your important data to a blank CD or memory stick/pen/thumb and start afresh. :(

---

### Post by pod25 on 2006-09-29
> **Matt.H said:**
> Wait a few weeks if you have an alternate computer, and upgrade to Edgy via terminal when it stablizes. 

Otherwise, use terminal to copy your important data to a blank CD or memory stick/pen/thumb and start afresh. :(

So apart from ubuntu, is there a better linux server os with a gui, that doesn't break so easy ?

---

### Post by Old Pink on 2006-09-29
Ubuntu doesn't break easily, only you could've broken it. 

Why not wait for some more advice before starting afresh, I know it's a time consuming process. :(

---

### Post by pod25 on 2006-09-30
> **Matt.H said:**
> Ubuntu doesn't break easily, only you could've broken it. 

Why not wait for some more advice before starting afresh, I know it's a time consuming process. :(

Well the only thing I have done recently was to make a ssh connection to a remote server for a private news group i am involved with, but the connection didn't go so well, hence the reboot, and now I got this logon problem, it doesn't make sense.

---

### Post by pod25 on 2006-09-30
How do I completely remove the ubuntu-desktop , so i can re-install it in a bid to fix this ? because i have tried ```
sudo apt-get remove --purge ubuntu-desktop
``` and yet after i reboot the desktop is still there !!!

---

### Post by pod25 on 2006-09-30
What does this mean ? > /etc/cron.monthly/scrollkeeper:
/var/lib/scrollkeeper/it/scrollkeeper_extended_cl.xml:1057: parser error : Extra
content at the end of the document
       </sect>
       ^
/var/lib/scrollkeeper/it/scrollkeeper_extended_cl.xml:1057: parser error : Extra
content at the end of the document
       </sect>
       ^
/var/lib/scrollkeeper/it/scrollkeeper_extended_cl.xml:1057: parser error : Extra
content at the end of the document
       </sect>
there's a whole load of them ?
Could this be part of my problem ?

---

### Post by bigken on 2006-09-30
have you tried sudo aptitude install ubuntu-desktop ?

---

### Post by pod25 on 2006-09-30
> **bigken said:**
> have you tried sudo aptitude install ubuntu-desktop ?

Yes I have. It allows me to login, then it begins to load the desktop, the desktop lasts about 5-10 seconds then it loops back to the login page.

---

### Post by bigken on 2006-09-30
boot into safe mode again and try this sudo apt-get update then sudo apt-get upgrade when its finished type startx ;)

---

### Post by pod25 on 2006-09-30
> **bigken said:**
> boot into safe mode again and try this sudo apt-get update then sudo apt-get upgrade when its finished type startx ;)

I did those commands via Putty from my windows machine.

After I put ```
startx
```I got this```
admin@podserver:~$ startx
xauth:  creating new authority file /home/admin/.serverauth.6309
xauth:  creating new authority file /home/admin/.Xauthority
xauth:  creating new authority file /home/admin/.Xauthority

X: user not authorized to run the X server, aborting.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
Couldnt get a file descriptor referring to the console
```

---

### Post by bigken on 2006-09-30
did it install any updates have tried a normal boot ?

---

### Post by pod25 on 2006-09-30
See my other post [http://www.ubuntuforums.org/showthread.php?t=268455]("http://www.ubuntuforums.org/showthread.php?t=268455")
I think it is now fixed.

---

### Post by bigken on 2006-09-30
pleased you got it sorted :D

---

