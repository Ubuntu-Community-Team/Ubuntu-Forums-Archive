---
title: "Freezing on Kubuntu 20.04LTS when switching Users during Login"
date: 2021-10-14
forum: Desktop Environments
---

### Post by jonray74 on 2021-10-14
Hello,

Hoping someone can point me to the right direction to solve the issue I have with my Ubuntu. I was previously an Ubuntu user back when it was Feisty Fawn (7.04) and also installed Compiz Fusion with it back in 2007. Time flies. :P

Anyways just a few days ago, I decided to go back and install the latest Kubuntu 20.04 LTS. I'm so happy to be back again using Ubuntu after 14+ years of not being into it. Everything has changed and i'm so blown away by the newest features it has and all the things that I could do now compared to when it was 14 years ago. Now everything about Ubuntu has changed. So amazed by it and I love it. Happy to be back in it again.

However, every OS has it's own issues and the issue I currently have is whenever I do a lock on my desktop, and when I click Switch User, and re-enter my UserID, Kubuntu goes into the splash screen and then suddenly freezes with black screen. I don't know why it keeps doing this and I am forced to hard reset the PC.

Is there a work-around on this issue. Whenever this happens I just do a hard reset cause everything just stops. All I see is black screen and mouse pointer.

I hope someone can reply with a link on the workaround on this one so I could fix it. Overall though, everything runs great. 

My PC is an
HP EliteDesk 800 G1 SFF
16GB Ram (UEFI Bios) 
256GB SSD (Primary)
1TB HDD (Slave Drive) - Installed Kubuntu 20.04LTS (Dual boot with Win 10 Pro)
Intel HD Graphics 4600


Thank you.
John

---

### Post by grahammechanical on 2021-10-14
Are you waiting long enough? I do not have Kubuntu but on Ubuntu 20.04 that switch user icon when clicked does freeze the lock screen but after a few seconds the screen switches to a login screen. I first tried to replicate the problem on Ubuntu 21.10 and there the screen did freeze. Perhaps I do not wait long enough. I did do a power off to reboot.

I think that the problem is caused by only having one user. Do you have more than one user? A delay might occur as the OS searches for other users and not finding any it does a repeat search. I am just guessing.

On Ubuntu 20.04 the way to change user is to select Power Off / Log out and then Log out. And at the log out screen change users. What you seem to be doing is trying to change users without logging out as the present user.

Regards

---

### Post by jonray74 on 2021-10-15
hey!

Thanks for the reply. Yes I waited about good 20 minutes just to see if it was going to somehow do something but nothing happened, so i just did a TTY5, CTRL + ALT+ F5 and was able to login via command prompt and had to do a reboot command from there to reset the machine. 

I just tried to simulate the way how people switch users from Windows 10 wherein if there were 2 accounts in there and the current user locks their desktop and does a switch user and then re-login again using their account, that it should just log them back in without issues, however on 20.04 it froze on me, so only way to get around it was CTRL + ALT + F5 and reboot command. Previously I did a hard reset but was concerned i might corrupt the entire system, so luckily there's the TTY5 environment.

I wish this could be fix. I wonder if my swap file wasn't large enough to maybe handle instances of saving the sessions and then logging in again. I did setup my swap file to be 2x the size of my RAM (16GB), so I created a 32G swap file which I guess would be enough to save sessions etc. when someone logs off, locks their desktop etc. Maybe what's happening is when I try to login using the same userid, it creates another instance of that session which then depletes my swap file (just guessing) which is why the system freezes. However that shouldn't be happening, the system should be able to figure out "oh ok, it's the same user, just load the old session and get them in". Because when I do the lock and click switch, and then re-login, it takes me to the Splash screen which is basically creating another session which I believe is what's causing the freezing, no more virtual memory. Anyways, that's just a wild guess. Maybe there's a workaround this in future updates.

Thanks,
John



> **grahammechanical said:**
> Are you waiting long enough? I do not have Kubuntu but on Ubuntu 20.04 that switch user icon when clicked does freeze the lock screen but after a few seconds the screen switches to a login screen. I first tried to replicate the problem on Ubuntu 21.10 and there the screen did freeze. Perhaps I do not wait long enough. I did do a power off to reboot.

I think that the problem is caused by only having one user. Do you have more than one user? A delay might occur as the OS searches for other users and not finding any it does a repeat search. I am just guessing.

On Ubuntu 20.04 the way to change user is to select Power Off / Log out and then Log out. And at the log out screen change users. What you seem to be doing is trying to change users without logging out as the present user.

Regards

---

### Post by jonray74 on 2021-10-15
will Editing Grub do the trick? I saw a post about freezing and they added this line to grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noaer pci=nomsi" 
GRUB_CMDLINE_LINUX="text pci=noaer pci=nomsi"

Not sure if this will somehow temporarily fix the issue

---

