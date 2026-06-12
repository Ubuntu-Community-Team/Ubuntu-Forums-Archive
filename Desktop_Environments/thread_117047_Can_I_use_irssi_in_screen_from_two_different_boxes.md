---
title: "Can I use irssi in screen from two different boxes?"
date: 2006-01-14
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-14
I use Ubuntu 5.10 on two computers. These two computers are on the same internal network; one is 192.168.0.2 and the other is 192.168.0.3.

I start my irssi sessions with:

1. screen -S irssi (start irssi in screen)
2. CTRL+A and d (detach the screen)
3. screen -r irssi (to attach it again later)

This way I can log in and out and not have to disconnect from the irc session; or I can pick up irssi in tty1 or so. Now I am wondering if it is possible to screen -r irssi (re-attach) from the other computer. 

It would be nice to just pick up the irssi session if I happen to be upstairs instead of having to go down two floors to use irssi.

Can I start a screen irssi session on one computer and pick it up on the other computer? If so, how do I do that? What do I need to have installed? What are the steps?

---

### Post by nxn on 2006-01-14
Ssh into the computer running the screen first, you can recall the screen through ssh and it will show up on the one you're on at the moment. You will need sshd, although I think ubuntu has it on by default?

just as an example:
```

ssh 192.168.0.2 -l <username> (if that's the one running the screen with irssi)
password:

screen -r <the name of the screen> (or -dr if it's still attached)

```

---

### Post by ardchoille on 2006-01-14
[QUOTE=nxn]ssh into the computer running the screen first, you can recall the screen through ssh and it will show up on the one you're on at the moment.[/QUOTE]
OK, that helps, thanks. How do I SSH to another Linux box? Is there some setting that I need to do to allow ssh into the other box?

---

### Post by nxn on 2006-01-14
[QUOTE=ardchoille]OK, that helps, thanks. How do I SSH to another Linux box? Is there some setting that I need to do to allow ssh into the other box?[/QUOTE]
On the computer you want to run irssi on, go to System > Administration > Services, then find Remote Shell Server, and make sure it's checked.

Then go on the other computer and in a terminal: ssh [ip/domain of the computer running irssi] -l [name of user that is running irssi, if it's the same as on the other computer you can ignore the -l part], enter the password, and you can recall the screen.

---

### Post by ardchoille on 2006-01-14
OK, I got everything except the "System > Administration > Services, then find Remote Shell Server, and make sure it's checked" part. I don't see Remote Shell Server there in the services list. What do I need to run or install to get that?

---

### Post by nxn on 2006-01-14
All right, sorry, I just could have sworn ubuntu came with sshd, just follow this wiki to set it up:
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)

Just set it up on the computer you plan to actually run irssi on, you don't need it on both unless you really want to.

---

### Post by ardchoille on 2006-01-15
Thanks, it works :)

---

### Post by toorima on 2006-01-15
screen -x irssi will attach to the screen while the other screen is still attached so both will work

---

### Post by ardchoille on 2006-01-15
[QUOTE=toorima]screen -x irssi will attach to the screen while the other screen is still attached so both will work[/QUOTE]
Awesome! Thank you for that little gem of info.

---

