---
title: "ubuntu 12.04 not turning on"
date: 2012-05-28
forum: Desktop Environments
---

### Post by bobthe on 2012-05-28
I've had ubuntu 12.04 since the release date on my hp laptop, and now today all of a sudden when I try to login (both my account and the guest account), the screen turns black, some text is shown (too fast for me to notice what it says something about /etc..) and then im sent back to the login window. I'm not able to login at all into my account. I don't know why this is happening as I've had 12.04 since the release date around a month ago and its been working completely fine!

can someone please help? thanks

---

### Post by bobthe on 2012-05-29
someone please help

---

### Post by stewi1014 on 2012-05-29
I Know i had this exact problem once, I am pretty sure it is something to do with the home directory not existing. try pressing ctrl + alt + f1 at the login screen, then type your user-name, then password. then type "ls" . if it says anything after you type your user-name and password then what ever it says will help people solve it. if after you type ls it shows little or nothing (like only 2 files) your home directory is missing. as to how to fix that, i don't really know.

---

### Post by bobthe on 2012-05-29
thanks for replying! I'll try that out asap. what did you end up doing? were you able to solve this problem?

---

### Post by bobthe on 2012-06-06
sorry for the late reply, but i finally got the time to check. after doing ctr-alt-f1, i logged in and was able to see all my directories and files in my home directory. everything still exists. i even changed my password and tried to login again, but wasn't able to. even the guest account isn't working. i dont understand how all of a sudden this can happen. after some tries (of logging in), a couple error messages on a black screen came up:

```

could not write bytes: Broken pipe
-Stopping anac(h)ronistic cron
-checking battery state...

```

sometimes it would say that and immediately return to the login window, but one time it got stuck for a while and i was able to take a picture of it and then had to reboot as nothing was responding.

can someone please help me with this?

---

### Post by typhoon_tip on 2012-06-06
How old is your hard drive ? Looks like something cannot be written to the disk... Can you check SMART data to see the drive's health ?

---

### Post by typhoon_tip on 2012-06-06
Actually, forget about the HD check, is still related to the graphic:
[http://askubuntu.com/questions/143267/ubuntu-12-04-based-distros-desktop-crashes-with-could-not-write-byte-broken-pi](http://askubuntu.com/questions/143267/ubuntu-12-04-based-distros-desktop-crashes-with-could-not-write-byte-broken-pi)

Lots of reports on this problem.

---

### Post by bobthe on 2012-06-06
thank you for your reply. What do I do at this point?

---

### Post by bobthe on 2012-06-09
thank you for your reply. What do I do at this point?

---

### Post by typhoon_tip on 2012-06-09
What video card do you have ? And by the way, have you read my link ? Have you run the command:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Hugo Napoli on 2012-08-23
[COLOR="purple"]Hi all. I had the same error. Black screen with following message:

could not write bytes: Broken pipe
-checking battery state...

It was after replacing video drivers (it was suggested by the System).
Two times i was Xubuntu working well, and two times System suggested replacing the existing video driver for the privative ones.
Two times black screen, and so on.
My machine is a NP-N102N Samsung notebook, and [B][COLOR="SeaGreen"]the solution proposed by typhoon_tip worked GREAT:[/COLOR]

sudo apt-get install ubuntu-desktop[/COLOR][/B]

[COLOR="Purple"]I had entered today just for this. I think it is what one have to do for all the community.

I am OpenSuse user with Ubuntu for "Ceibal Plan" on Uruguay. I am very happy to find help from another flavor communities.

Long life to Linux and all its distributions.

Big hug![/COLOR]

---

### Post by Hugo Napoli on 2012-08-23
[COLOR="purple"]Hi all. I had the same error. Black screen with following message:

could not write bytes: Broken pipe
-checking battery state...

It was after replacing video drivers (it was suggested by the System).
Two times i was Xubuntu working well, and two times System suggested replacing the existing video driver for the privative ones.
Two times black screen, and so on.
My machine is a NP-N102N Samsung notebook, and [B][COLOR="SeaGreen"]the solution proposed by typhoon_tip worked GREAT:[/COLOR]

sudo apt-get install ubuntu-desktop[/COLOR][/B]

[COLOR="Purple"]I had entered today just for this. I think it is what one have to do for all the community.

I am OpenSuse user with Ubuntu for "Ceibal Plan" on Uruguay. I am very happy to find help from another flavor communities.

Long life to Linux and all its distributions.

Big hug![/COLOR]

---

