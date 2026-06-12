---
title: "I seem to have killed my sudo..."
date: 2006-08-17
forum: Desktop Environments
---

### Post by ekstasys on 2006-08-17
Ok, lets start from the beginning, I wanted to change the skin for my xmms, but it is read only so I was unable to write it into the skins folder...  Off to the documentation to see how to solve this problem...  I am running kubuntu 6.06.

The documentation told me to go into my menu and start grahical sudo, however, I could not find it there, so I went into adept and searched for it to make sure it had been installed properly, it had, and was working, so I exited.

Next I went into the user account settings to make sure I had given myself access to use sudo, which I had.  The next thing the documentation tells you to do is then use the terminal to run sudo, and make sure to be very clear to tell you to use the "kdesu" command and not usual sudo with graphical programs, or else you will have all sorts of problems.  Well, this is what I did, my exact command was "kdesu xmms" but that promptly failed.  So, I went back to try the user accounts again, make doubly sure I had given myself proper permissions, and when I tried to go into admin mode, it told me that the connection to su failed.  The exact thing that the documentation told me would happen if I ran usual sudo rather than the command given that I then used.

I have been using linux of any form for about 9 days now, so I really dont know much about it, and know it is a slow going proscess to be able to do all I want to.  But, I cant seem to find documentation on how to fix what shouldnt have happened when using the command the documentation gave, so any help at all would be appreciated.

Thanks for your time and energy!!

---

### Post by aysiu on 2006-08-17
This fixes most broken sudo problems. Let us know if you need more help than that:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by ekstasys on 2006-08-17
Sorry to bother you, deleted, stupid question....

---

### Post by ekstasys on 2006-08-17
I am bookmarking that page, my sudo works again, thank you so much, aysiu.

Now, the next question, how does one achieve my original goal of baing able to copy new skins into the folder without breaking my sudo.  

I tried the rules in the documentation twice now, to amke sure I didnt mistype the first time, but it did the same thing again.  Luckily, this time, I knew what to do in that case...

---

### Post by aysiu on 2006-08-17
I don't know much about XMMS, but you shouldn't need root privileges to install a skin.

Maybe an XMMS user can chime in here...

---

### Post by ekstasys on 2006-08-17
The problem is that the folder the skins are contained in is read only.  That is when the sudo problem started, when I was trying to chage the folder settings to be able to copy files into it.  So, basically, what I need to know now is the proper way to change the permissions on a folder without killing my sudo again, lol.

---

### Post by aysiu on 2006-08-17
The proper way is not to change the permissions on the folder at all. If you're just moving skins, follow this tutorial on temporarily gaining root permissions:

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by ekstasys on 2006-08-17
Thanks, works beautifully...  I was trying to stay away from non-official docs because you never know what person out there thinks it is funny to kill your system, but this is amazing...

I really, really appreciate it...

---

### Post by aysiu on 2006-08-17
Even a lot of the "official" docs out there are written by forum members here--volunteers.

---

