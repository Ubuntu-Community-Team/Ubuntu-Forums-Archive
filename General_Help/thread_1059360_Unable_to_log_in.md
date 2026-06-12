---
title: "Unable to log in"
date: 2009-02-03
forum: General Help
---

### Post by moodog on 2009-02-03
I was using my system this morning and everything was going fine. I then noticed that my printer wasn't working properly, and so decided to try to restart cups. When I executed 

[PHP]sudo /etc/init.d/cups restart[/PHP]

i got a segmentation fault. Thinking this was weird, I restarted. When the system restarted and came to the gdm login screen, if I enter my username and password, the screen flashes back to the console with all messages visible, and then comes back up with the gdm login screen (i.e. doesn't log in properly).

I then rebooted into the recovery mode and checked a few things, and most things seem good. I couldn't see any errors that i would think are relevant in /var/log/messages (although there are a few), and nothing in the output of dmesg. 


Something unusual though, was at the root console I wanted to try to change the password of my normal user, and executing 

[PHP]passwd <username>[/PHP]

gave a segfault too.

Any tips on how to solve this? logfiles to look at etc.? I'm at a bit of a loss, and would really like to be able to log in...

---

### Post by dcstar on 2009-02-03
> **moodog said:**
> I was using my system this morning and everything was going fine. I then noticed that my printer wasn't working properly, and so decided to try to restart cups. When I executed 

[PHP]sudo /etc/init.d/cups restart[/PHP]

i got a segmentation fault. Thinking this was weird, I restarted. When the system restarted and came to the gdm login screen, if I enter my username and password, the screen flashes back to the console with all messages visible, and then comes back up with the gdm login screen (i.e. doesn't log in properly).
.........
Any tips on how to solve this? logfiles to look at etc.? I'm at a bit of a loss, and would really like to be able to log in...

File corruption or hardware failure may have caused this, boot off a Live CD and do a fsck on the root partition of the drive.

---

### Post by moodog on 2009-02-03
Thanks for the reply. Booted off live cd and ran fsck -f on both / and /home, and unfortunately found nothing. I booted back in and tried to log in, but still the same.

---

### Post by moodog on 2009-02-03
I suspect it's something to do with authentication failing. If I look at /var/log/auth.log there are messages in there indicating "failure to authenticate user <username>" etc. I followed this thread here:

[http://forums.devshed.com/unix-help-35/segmentation-fault-after-root-password-reset-411014.html](http://forums.devshed.com/unix-help-35/segmentation-fault-after-root-password-reset-411014.html)

and removed the x for my particular user, but it didn't make any difference.

---

### Post by moodog on 2009-02-03
Have tried running memtest for some time just in case, but it hasn't turned anything up. May just have to reinstall... dammit.

---

### Post by moodog on 2009-02-03
have just found this:

[http://ubuntuforums.org/showthread.php?t=987788](http://ubuntuforums.org/showthread.php?t=987788)

this also lists the problem:

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/303458)

problem solved.

---

