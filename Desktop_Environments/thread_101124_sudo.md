---
title: "sudo?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by davebradford on 2005-12-09
can someone explain to me why we use sudo before commands? i'm an old fedora user.. still quite new to ubuntu and i've been doing commands left right and centre without using sudo and it still works!? sorry i am being a n00b?

Dave

---

### Post by giloth on 2005-12-09
sudo is basically for temporary root access.

Once you initially use sudo, I believe you have 15 minutes before the access expires. You also need to have permissions to use sudo which the first user to be setup is automatically given.

The root account is disabled in Ubuntu by default and that's what sudo is all about. ;)

I'm sleepy and mumbling.. Sorry. :)

---

### Post by frodon on 2005-12-09
If you want to become root in a terminal use the "sudo su" command.

---

### Post by davebradford on 2005-12-09
so enabling the root account for the system effectly makes the use of sudo redundent? there would be no point in using it?

---

### Post by e2k on 2005-12-09
[QUOTE=frodon]If you want to become root in a terminal use the "sudo su" command.[/QUOTE]
Thanks for the tip, I personally think it's frustrating to put sudo in front of everything you're about to do outside your ~/. It might be a matter of getting used to things though, been using gentoo and su for a year now, so I suppose it takes its time :)

---

### Post by frodon on 2005-12-09
normally you will never need to set a root account because you can do all you want with "sudo", so it's not redondant.
However some users who come from other distros are used to live with a root account and even if i don't advice to create a root account because it's against the ubuntu spirit you can do that : [https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin](https://wiki.ubuntu.com/RootSudo?action=show&redirect=EnableRootLogin)

---

### Post by davebradford on 2005-12-09
so there's nothing wrong with having a root account and a user account

---

### Post by frodon on 2005-12-09
It's not in the ubuntu spirit which prefer to not set a root account (it's a security strategy). 
But you seems to know what you do so i don't think there's something wrong doing that,  i just generally don't advice it.

So no problems here if you wish a root account ;)

---

### Post by ameerirshad on 2005-12-09
[quote=frodon]If you want to become root in a terminal use the "sudo su" command.[/quote]
 
Huh??? "sudo su"? I always use just "sudo".......  what's the difference?

---

### Post by frodon on 2005-12-09
When you type "sudo su" in a terminal you will be asked for your password and you will become root. So all the command you will type after will be launched as root without puting "sudo" before.
It's useful when you have many sudo commands to run and then don't want to type sudo each time.
By the way, type "exit" in the terminal to become again a simple user.

So there isn't any differencies, it's just a question of comfort.

---

### Post by magnusbb on 2005-12-09
I've always been wondering about one thing considering sudo. When you type sudo, you are granted root access for the next 15 minutes. Does that mean, that every command, fx. a process can get root access without a password during that time? That would be extremely vulnerable. 

Sometimes, during those 15 minutes, I've used some programs requiring root access, without knowing it, because they never asked me.

---

### Post by tokyovigilante on 2005-12-09
No it just means that in your current terminal session for 15 minutes sudo will not ask your password. Other running processes are not affected, and you still use sudo, it just doesn't need a password for those 15 min.

I usually just use sudo -i to get a root terminal, then exit back to my user one when I'm done.

---

### Post by esperantisto on 2005-12-09
Based on my previous experience with other Linuxes, I've set root password (just because I did not understand that sudo). The question is, what should I use now? Do root and sudo have equal rights, or root is higher?

---

### Post by lcg on 2005-12-09
[QUOTE=esperantisto]Based on my previous experience with other Linuxes, I've set root password (just because I did not understand that sudo). The question is, what should I use now? Do root and sudo have equal rights, or root is higher?[/QUOTE]
No, they are the same. sudo executes a command as root, with all its privileges. You can use whichever you are more comfortable with.

Lars

---

### Post by esperantisto on 2005-12-09
Thanks for explanation. Does this actually mean that I can set two different passwords: one for sudo and one for root, and they'll have the same effect?

---

### Post by frodon on 2005-12-09
[QUOTE=tokyovigilante]No it just means that in your current terminal session for 15 minutes sudo will not ask your password. Other running processes are not affected, and you still use sudo, it just doesn't need a password for those 15 min.

I usually just use sudo -i to get a root terminal, then exit back to my user one when I'm done.[/QUOTE]Yes, in addition you can, like me, disable this 15 min time during which the password is not asked so the password will be asked for each sudo command.
[http://www.ubuntuforums.org/showthread.php?t=38973](http://www.ubuntuforums.org/showthread.php?t=38973)

---

### Post by lcg on 2005-12-09
[QUOTE=esperantisto]Thanks for explanation. Does this actually mean that I can set two different passwords: one for sudo and one for root, and they'll have the same effect?[/QUOTE]
You do not set a password for sudo, you set passwords for users.

sudo is a tool that allows certain users to execute certain commands as root (see 'man sudo' and 'visudo' for details). E.g. in Ubuntus default configuration, your first user has the right to run all commands as root. However, to prevent abuse of this, you have to authorize again for sudo with your user's password before the command is actually executed. Without this check, if someone got hold of a shell on your computer where you are logged in (perhaps you had to leave your computer for a few seconds and did not lock your screen), he or she would have the right to run any command as root. Not really what you want, believe me. ;)

I hope this clarifies the use of sudo.

Lars

---

### Post by giloth on 2005-12-09
I just perfer sudo cause all the cool kids are doing it. :cool:

---

### Post by tokyovigilante on 2005-12-09
[QUOTE=esperantisto]Thanks for explanation. Does this actually mean that I can set two different passwords: one for sudo and one for root, and they'll have the same effect?[/QUOTE]
Ubuntu does not have a root password because it does not have a root user by default. You can set one up, but sudo works fine for everything else. When you install, the first user you create (usually yourself) is added to the etc/sudoers file and has the priviledge of root authentication. Your user password is used for this purpose, so when sudo asks for a password, it expects your user one.

[QUOTE=frodon]Yes, in addition you can, like me, disable this 15 min time during which the password is not asked so the password will be asked for each sudo command.[/QUOTE]
IMHO this probably isn't the best solution for those who are security conscious, as it means anyone who gains physical access to a terminal or program you have given root access to can do some damage. rm -fr / isn't too hard to type ;) On the other hand this would be very convenient if you are sure your physical terminal is safe.

---

### Post by frodon on 2005-12-09
[QUOTE=tokyovigilante]IMHO this probably isn't the best solution for those who are security conscious, as it means anyone who gains physical access to a terminal or program you have given root access to can do some damage. rm -fr / isn't too hard to type ;) On the other hand this would be very convenient if you are sure your physical terminal is safe.[/QUOTE]Yes, but when you use "sudo -i" or "sudo su" you should always type "exit" when you finished sudo thing in order to end the root access. So no problems here.

---

### Post by tokyovigilante on 2005-12-09
[QUOTE=frodon]Yes, but when you use "sudo -i" or "sudo su" you should always type "exit" when you finished sudo thing in order to end the root access. So no problems here.[/QUOTE]
Also you should close the terminal window you were using, as even after exit you can still log back on as root without a password until the timeout expires, and if you have disabled it then that terminal is able to be used as root indefinitely.

However if your computer is physically secure i guess it's a non-issue.

---

### Post by frodon on 2005-12-10
Ok, when i say that i disable the 15 min during which you don't have to tyope the root password that means that you are **ALWAYS** asked for the password when you use a sudo command (like if you have a timout of 0 sec) even if you used a sudo command 5 seconds before that doesn't mean at all that you could use the root terminal indefinitely.

Am i enough clear or is there still a black point for you with this trick ?
It's just a way to increase the security, of course it's not really needed.

---

### Post by tokyovigilante on 2005-12-10
Oh I see, sorry about that. I thought you meant the opposite, that you had disabled the timeout so you were asked once and never again.

---

### Post by frodon on 2005-12-11
lol, no problem ;)

---

