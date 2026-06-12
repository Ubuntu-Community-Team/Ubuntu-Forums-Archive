---
title: "Automate a prosess."
date: 2007-12-11
forum: Desktop Environments
---

### Post by frodemt on 2007-12-11
We have Ubuntu 6.10 at my work to show powerpoint slides with information.

I want to make a program that makes it easy to upload new powerpoint-slides to this system and automatic start them in fullscreen mode.

Is this even possible?

I was thinking about using VB .net 2005, and perhaps sending commands with putty? Dont know about uploading files yet and what to use there, but it must be done via the program too.

Any ideas guys? This would be great!

---

### Post by skwerl530 on 2007-12-11
This thread may be of help:
[http://www.oooforum.org/forum/viewtopic.phtml?t=1051](http://www.oooforum.org/forum/viewtopic.phtml?t=1051)

---

### Post by frodemt on 2007-12-11
I have now figuered out a way (thanks to your post and the nice macro) to open a impress slideshow from command line within the desktop environment on the computer that is going to run the slidewshow.

I tried the same from putty but got this error saying it could not open the display. I guess this is because putty runs a completly diffentent session than the GUI that is allready logged on.

How can I start a new slideshow via putty on a GUI-session that is allready running?

And how can I close the impress on the GUI session from putty?

---

### Post by frodemt on 2007-12-11
I found the answer myself, but I will post them here so if someone else have the same problem in the future this might help them.

To kill a process without the knowledge of PID: "killall soffice"

to start a slideshow from putty: "ooffice -impress -o filename.odp -norestore -display :0.0"

-norestore is important if you killed the process because wants to restore the wrongly closed document.

Now I will have to figure out how to transfer files from windows to ubuntu. I was thinking about samba at first, but now I'm going to look at FTP. Samba might complicate things if the client system is not configured right, while FTP always works as long as there is a connection.

---

### Post by skwerl530 on 2007-12-12
> **frodemt said:**
> I found the answer myself, but I will post them here so if someone else have the same problem in the future this might help them.

To kill a process without the knowledge of PID: "killall soffice"

to start a slideshow from putty: "ooffice -impress -o filename.odp -norestore -display :0.0"

-norestore is important if you killed the process because wants to restore the wrongly closed document.

Now I will have to figure out how to transfer files from windows to ubuntu. I was thinking about samba at first, but now I'm going to look at FTP. Samba might complicate things if the client system is not configured right, while FTP always works as long as there is a connection.

Look at [ Winscp ](http://winscp.net/eng/index.php).  It may do what you want with a GUI from windows.  If it needs to be automated you might can make rsync work.

---

### Post by frodemt on 2007-12-12
WinSCP requires that you install it before it can be used.

I have solved this problem with plink and psftp. I have now a working version of the program. I will put it at my webpage and make a translated version (in english) if someone is interested.

The only problem with this program is that the program dont get any status from plink nor psftp, so it has no idea when they are done. For now only timers will "solve" this issue.

I will put a complete guide at my website.

---

### Post by skwerl530 on 2007-12-12
Cool it sounds like an interesting project.  Good luck man.

---

### Post by frodemt on 2007-12-14
I am now finished with the project. :guitar:

Lets hope that more than just my boss can have benefit of this project.


You can all visit the projects home page at this URL:

[SIZE="4"][http://tviberg.info/nettside/slideshow_linux_en.php]("http://tviberg.info/nettside/slideshow_linux_en.php")[/SIZE]

Thanks to skwerl530 and thouse who wrote psftp, plink, ubuntu and openoffice. :)

---

