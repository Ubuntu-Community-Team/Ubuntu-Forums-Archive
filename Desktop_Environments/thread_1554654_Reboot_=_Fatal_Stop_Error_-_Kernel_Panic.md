---
title: "Reboot = Fatal Stop Error - Kernel Panic"
date: 2010-08-17
forum: Desktop Environments
---

### Post by miserly-martyred on 2010-08-17
[SIZE=2]My most recent updates to Ubuntu 10.04 {stable} were around 7pm EST 8-16-10  ~100mb of files - ubuntu ftp server ftp.ussg.iu.edu, i think.[/SIZE]
        [SIZE=2]When I rebooted prior to the updates, all went well, then the immediate following boot created this error:[/SIZE][SIZE=2]
[/SIZE]
            [SIZE=2]BEGIN ERROR--------------------------[/SIZE]

> [SIZE=2]Target filesystem doesn't have /sbin/init.a - 99d0ae2fd8e95c4[/SIZE]
        [SIZE=2]run - init: /etc/init: Permission Denied[/SIZE]
        [LEFT][SIZE=2][1.632956] Kernel Panic - not syncing  Attempted to Kill init![/SIZE][/LEFT]
[LEFT][SIZE=2]END ERROR-----------------------------[/SIZE]
[SIZE=2]
[/SIZE][/LEFT]
        [LEFT][SIZE=2]I don't want to be a long-winded weirdo so I won't detail ALL of my pc specs immediately in case some admin already knows of this error.[/SIZE][/LEFT]
        [LEFT][SIZE=2]I say this because my pc is along the lines of much eSATA, 2 usb hubs, and 9 HDD's of  7000 GB - so it's complicated but I didn't meddle with anything physical to get this error...[/SIZE]

[/LEFT]
        [LEFT][SIZE=2]Thanks for any help btw, it will be ridiculously appreciated :)[/SIZE][/LEFT]

---

### Post by nightshade209 on 2010-08-17
I had the same problem and managed to solve it. Check [here]("http://ubuntuforums.org/showthread.php?t=1555031").
Just be sure to make the appropriate changes according to your problem, i.e., replacing my /sbin/init file with your /sbin/init.a and my /dev/sda1 with whatever is appropriate for your system.
Hope this works!

---

### Post by miserly-martyred on 2010-08-17
although I seriously appreciate the effort/advice, my PC is still being a cruel oaf and after I tried your method just like you said ... I got the same error again.

... ughhh ... any other suggestions?

---

### Post by nightshade209 on 2010-08-18
Nope, sorry. As far as i can guess, it is a Permissions issue, so i thought changing back the permissions would solve it. If it doesn't, then I have no clue what else to do. Worst case, you'll have to re-install, but don't hurry to do that; look and ask around first.

---

### Post by miserly-martyred on 2010-08-19
k thanks, much appreciate the help - i guess i'll have to investigate and hunt down more options :?

---

### Post by miserly-martyred on 2010-08-21
... so ... no other ideas ??? [unfortunately when left to my own devices, I am now stuck] --> I'm just curious b/c I found it helpful that somebody else had this error, and if the error is between two individuals of completely separate PC setup/location, I would think that it's not just some random crap that I did personally.  I tried every logical combo/attempt at the suggested permissions settings, and they were all to no avail, and at that - the error message has neither progressed nor been modified.  I thought perhaps this would be similar to a bug of sorts but on a ridiculously smaller scale, I just cant figure out whether it's strictly an OS issue I have encountered or if there is a technical physicality to the matter ???

---

### Post by miserly-martyred on 2010-08-24
I checked the other thread that NightShade referenced and based on that and myself there seem to be at least two of us with ongoing unsolved issues.  That thread seems to have been closed with some of us still in the dark about the matter

---

### Post by miserly-martyred on 2010-08-30
Out of curiosity:

Is there a way people, such as myself, can pay Canonical directly for support issues.  If so, what route would I go to do that?

---

