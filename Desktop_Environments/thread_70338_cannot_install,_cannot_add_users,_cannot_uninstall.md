---
title: "cannot install, cannot add users, cannot uninstall..."
date: 2005-09-29
forum: Desktop Environments
---

### Post by urbandryad on 2005-09-29
basically, anything that requires ROOT seems to not be functioning. I can't login to ROOT from the login screen, and I'm guessing I'm not supposed to? My user account seems to be set as a non-admin account as well. I can't use synaptic, or add users or programs, and I haven't gotten a response in the unrelated thread that the topic came up in, so I'm posting a new thread under the appropriare heading.

Any help would be hot guys. I'd really like to be able to install some programs, and lame so I can convert my OGG's to MP3's at least (which is how I discovered the issue in the first place) XD Thanks!

---

### Post by aysiu on 2005-09-29
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by urbandryad on 2005-09-29
where do I put sudo? In my regular terminal window? o.o And I use my user password or a different password? Those links you gave me are confusing. I don't know anything about terminal. Accept how to set the hardware clock. I can do the clock. ^__^

---

### Post by leezer3 on 2005-09-29
Another one with totally bust root access- Join the club!
*Edited*
Cheers
-Leezer-

---

### Post by FLeiXiuS on 2005-09-29
[QUOTE=leezer3]Another one with totally bust root access- Join the club!
[http://ubuntuforums.org/showthread.php?t=67786](http://ubuntuforums.org/showthread.php?t=67786)
As a temporary measure, do CTRL+ALT+F1 to kill X, and then login as root. After that, run killall gdm and then startx.
This will get you a working (TOTAL ROOT) GUI. 
Cheers
-Leezer-[/QUOTE]

WARNING:

It's unimaginable of the flaws and vulernabilities your handing to the world by loggin into the GUI as root.  I'd always advise against it.  Simple right click on your desktop and click open terminal for a terminal.  Linux is based on a command line interface.  It's the parent for the GUI.  Anything that needs root can be done in the terminal without hassle.  If not, then you may use gksudo for a gtk root.  

Again, please don't follow the what the previous post explained.

---

### Post by leezer3 on 2005-09-30
(Post edited to only show with the warning)

Yeah, I understand what you're saying, but again, he seems to be in the same situation as described in my thread.
In that there seems to be some sort of problem with sudo & gksudo, which means that they simply do not work, and only actually getting to a GUI as root will allow you to do anything root related. If you have a solution to this, then please share it, because I've tried everything I can think of, and am still beating my head against a brick wall! 	](*,) 	](*,)
To test whether this is the case, open up a standard terminal, and run 
```
sudo network-admin
```
(This will attempt to run network-admin as 'proper root' as opposed to via gksudo, and will prompt you for the root password you entered at install) If you're in the same hole as my thread, then it'll bitch about your user not being in the sudoers file.

Cheers

-Leezer-

---

### Post by Quirky on 2005-09-30
Is this problem in Hoary?

</stupid question>

---

### Post by leezer3 on 2005-09-30
Yep, it's in Hoary, as well as the latest Breezy. As far as I can see, it's totally random; This is the third install I've done from this disk, and the only one thats messed :rolleyes:
I would probably try installing again, but every time I do this, Ubuntu seems to trash my partitioning, and I really don't want to loose the amount of customisation I've now put into both this & Windoze.

Cheers

-Leezer-

---

### Post by urbandryad on 2005-09-30
I don't think I have a choice but to use a root GUI. I can't seem to use sudo in terminal. And even if I could I HATE using command lines for something as simple as installing an application. Its frustrating me to no dang end that I have to use it just for an app. I have to use it to add users. I have to use terminal for EVERYTHING but basic desktop functions.

I SHOULDN'T HAVE TO. If I can't figure out how to make Linux work as a GUI environment, or if I can't learn terminal by the end of October, I'm investing in Jaguar again. Its just too fricking frustrating.

Somebody told me that Linux wasn't complicated at all. its been nothing but complications for me. :(

---

### Post by Quirky on 2005-09-30
What groups is the supposed sudoer/admin user in? (the command 'groups' tells you) If admin isn't there, then that could be the problem. The solution would be single user mode and then, as root, add the user to the admin group.

---

### Post by leezer3 on 2005-10-01
As I suspected, precisely the same hole :cool: 
Care to join this F*** club?
I need someone to fix this, and fast. Admin group doesn't exist, only a group named adm, & I have no idea on how to go about creating a working admin group.

Cheers

-Leezer-

---

