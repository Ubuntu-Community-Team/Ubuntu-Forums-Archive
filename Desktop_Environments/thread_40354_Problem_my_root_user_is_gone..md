---
title: "Problem: my root user is gone."
date: 2005-06-08
forum: Desktop Environments
---

### Post by vcmsxs on 2005-06-08
Im so stupid, did something like this: sudo userdel root.
And now I cant fix or do anything as root. Does anyone know how to fix this (how to useradd root).

Best regards.

---

### Post by aysiu on 2005-06-08
Let me make sure I've got this straight. So now when you're in terminal and try to do a *sudo* command (e.g., *sudo apt-get update*) what happens? I only ask this because Ubuntu comes with the root log-in disabled,  but it does allow *sudo* to perform tasks as something root-like.

---

### Post by defkewl on 2005-06-09
Just install a new one :D

---

### Post by Takis on 2005-06-09
No offence, but that's hilarious. Out of curiousity, what made you feel that was necessary?

You should sign up for [breakmyubuntu](http://www.ubuntulinux.org/wiki/BreakMyUbuntu).

---

### Post by defkewl on 2005-06-09
Well could you tell me what is so funny? Or at least give the man a way out to his problem ;)

---

### Post by vcmsxs on 2005-06-09
No, it is funny, I admint. A true Buster Keaton stunt made in bash  :). I it not my firt so  God cursed the day I got my first computer .

Why I did it? Well I have just installed the Ubuntu for the first time and before I rtfm and relized that Ubuntu uses sudo instead of su I had changed the root passwd. At some point late last night when trying to corret it (change it back) my brain had a short circuit due some frustration that I´ve just missed the last episode of desperate house whifes and way too much coffe :) eh.... to the point.

When trying something like "sudo useradd root" or "sudo passwd root" or "sudo apt-get update" the console tells me that I dont have root privelege and that I need it. Also when I reboot unbutu I get a message dialog that said something like "Cant initialize HAL !"

I would rather not reinstall, any other Idés ?

Thanks
Johan.

---

### Post by zAo on 2005-06-09
[QUOTE=vcmsxs]No, it is funny, I admint. A true Buster Keaton stunt made in bash  :). I it not my firt so  God cursed the day I got my first computer .

Why I did it? Well I have just installed the Ubuntu for the first time and before I rtfm and relized that Ubuntu uses sudo instead of su I had changed the root passwd. At some point late last night when trying to corret it (change it back) my brain had a short circuit due some frustration that I´ve just missed the last episode of desperate house whifes and way too much coffe :) eh.... to the point.

When trying something like "sudo useradd root" or "sudo passwd root" or "sudo apt-get update" the console tells me that I dont have root privelege and that I need it. Also when I reboot unbutu I get a message dialog that said something like "Cant initialize HAL !"

I would rather not reinstall, any other Idés ?

Thanks
Johan.[/QUOTE]
Johan (Dutch?  :) ),
You can start in singleuser-mode, then add the rootuser again.
You can also start with the liveCD and chroot you rootfs, but since this is you first installation, I'd say: try singleuser mode.

---

### Post by vcmsxs on 2005-06-09
Thanks !
Singeluser mode... then I just reboot and press escape before the os i loaded.
When prompted I  do: "useradd root" and then  "passwd root" , am I on the right track here?

Im Swedish, Geffle (20 mil north of Stockholm by the cost)

Regards Johan

---

### Post by nocturn on 2005-06-09
[QUOTE=vcmsxs]Im so stupid, did something like this: sudo userdel root.
And now I cant fix or do anything as root. Does anyone know how to fix this (how to useradd root).

Best regards.[/QUOTE]

Boot the system with a liveCD (Either ubuntu or something like knoppix).
Mount your root partition read-write.


Open /pathtomountedroot/etc/passwd and add 
```
root: x:0:0:root:/root:/bin/bash
```
at the top. (remove the space here  : x:, I added it because the forum software tried to make a smiley).

Umount, reboot.

Good luck

---

### Post by vcmsxs on 2005-06-09
Thanks a bunch !
J.

---

### Post by Takis on 2005-06-09
[QUOTE=defkewl]Well could you tell me what is so funny? Or at least give the man a way out to his problem[/QUOTE]
Fair call, it was a bit harsh on my part, and I didn't have anything constructive to add. All I wanted to know was what made Johan do it - good old late night hacking.

---

