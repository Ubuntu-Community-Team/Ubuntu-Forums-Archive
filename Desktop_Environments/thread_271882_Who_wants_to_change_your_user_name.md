---
title: "Who wants to change your user name"
date: 2006-10-05
forum: Desktop Environments
---

### Post by fululian on 2006-10-05
hi,

i am running ubuntu with a single user, which is therefor attributed the sudo-rights. if i am now trying to change that one user's name, i thought i first switched to the terminal-mode, edited the ```
/etc/passwd and /etc/shadow
``` and finally did a ```
sudo mv /home/old_user /home/new_user
```.

is this the right procedure or would i get myself into a horrible mess?

which way is the best way to get to a non-grafical environment in order to do this?

which ist the best way to edit the said files in the terminal?

thanks so far...

---

### Post by uros678 on 2006-10-06
You are on the right track I would say. Don't forget to give the new user sudo rights. And don't forget to run chown on the home dir.

I would boot into single user mode or use init to go to runlevel 1 which is single user mode and change the files with the vi editor or joe or something else. Don't know what editor are available on your system.

Hope that helps a little bit and don't forget to backup the files you are editing in case something goes wrong.

Best regards,
Uros

---

### Post by fululian on 2006-10-06
hi, thanks.

how do i boot into single-user-mode?

and why do i have to "chown" and give sudo-rights to the /home/folder after sipmply exchanging the name of the superuser? the rights would have to be the same still, or am i just wrong on this?

do you have a cute little vim-description?

thank you still...

---

### Post by uros678 on 2006-10-09
> **fululian said:**
> hi, thanks.

how do i boot into single-user-mode?


That's something I found on the net, it was way faster than if I had to type it up.. :)

*To get into single user mode from GRUB, highlight the linux operating system you want to boot. After the line is highlighted, press 'e'. 'e' will get you into the GRUB editor. Next, highlight the line that begins with "kernel" and press 'e' again. 'e' the second time will allow you to edit the "kernel" line. Add the word "single" to the end of the line, "single" will tell the kernel to boot into single user mode. After adding the word "single", press "Enter" and then 'b' to boot the operating system.*

Or you could just go into a terminal windows and run "sudo init 1" command... that will work too...

> 
and why do i have to "chown" and give sudo-rights to the /home/folder after sipmply exchanging the name of the superuser? the rights would have to be the same still, or am i just wrong on this?


I think I messed up a little here. I thought that the files owned by the sudo user are not gonna be owned by the new user after you changed the name. Forgot to take into account that linux _probably_ uses UID and GID numbers for that sort of thing.. :D

For the sudo I meant for the new user to receive the sudo right. Don't know exactly how ubuntu does that. I'm kinnda new to ubuntu...

Hope that clarifies some things a little more.. :)

> 
do you have a cute little vim-description?

Don't know exactly what you mean by that. I use vi or joe if it's installed on a system. By any means I am not a power user of vi. I now just how to do a basic edit of a file..

Best regards,
Uros

---

### Post by fululian on 2006-10-09
well,

many thanks for the time...

cu. fululian

---

