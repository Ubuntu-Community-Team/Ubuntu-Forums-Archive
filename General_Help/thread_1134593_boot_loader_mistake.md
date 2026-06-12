---
title: "boot loader mistake"
date: 2009-04-23
forum: General Help
---

### Post by deadsump on 2009-04-23
Hello everyone,
This is my first post at this forum, and I am a novice ubuntu user.
I had just installed ubuntu 8.10 as a dual boot computer by following the "How to dual-boot Vista with Linux (Vista installed first)" guide.  I had been doing fine and had both vista and ubuntu working before I tried to change the boot loader as described on this page

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

and this is where I messed up badly.  I messed up following the directions and ended up uninstalling both the boot loader for vista and ubuntu.  Currently when I start up my computer I get a message that says that somthing is not found and then restarts.

I know I am an idiot, but can anyone help me?

I am currently using my computer by running ubuntu off the load disk.  A very nice feature!

Please help.

Otis

---

### Post by nandemonai on 2009-04-23
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by deadsump on 2009-04-23
That worked like a charm!  Thank you.

Do you know any nifty tricks to fix my Vista like that?  :D  please?  If I try to start that I get a ntldr not found message and I then have to restart.  If you know anything about fixing this problem I would be very grateful.

If not at least I was able to get one of my operating systems back up and running.

Thank you again, this stressful night is having a bit of a bright spot!  I don't know why I could not find those on my own (probably because I did not know what I was looking for :D )

Otis

---

### Post by nandemonai on 2009-04-23
> **deadsump said:**
> That worked like a charm!  Thank you.

Do you know any nifty tricks to fix my Vista like that?  :D  please?  If I try to start that I get a ntldr not found message and I then have to restart.  If you know anything about fixing this problem I would be very grateful.

If not at least I was able to get one of my operating systems back up and running.

Thank you again, this stressful night is having a bit of a bright spot!  I don't know why I could not find those on my own (probably because I did not know what I was looking for :D )

Otis

Should be a recovery option on the Vista disc but be warned, it will nuke grub and you'll have to fix grub again.

If this turns out to becomes a looping problem search the forums here in regard to the issue. I remember seeing a post where a Vista upgrade would continually kill grub. There is a way around it but I can't remember at the moment (I don't use Vista myself).

---

### Post by deadsump on 2009-04-24
Thank you for the tip I will see what I can figure out.

> **nandemonai said:**
>  (I don't use Vista myself).
Don't rub it in:).

Thank you again.

Otis

---

