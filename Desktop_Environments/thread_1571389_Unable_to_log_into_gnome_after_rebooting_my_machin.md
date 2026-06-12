---
title: "Unable to log into gnome after rebooting my machine"
date: 2010-09-09
forum: Desktop Environments
---

### Post by elperrillo on 2010-09-09
HI, I am in a bad predicament.

I installed NX to be able to log into my server running ubuntu remotely, while using NX I rebooted the server remotely, now I cannot log into it, not remotely and not physically either!!!!!!

Every time I enter my user name and password the screen goes black for a couple of seconds displaying some nx messages and then it goes back to the login prompt.

Can anybody help me I am extremely desperate, this is one of my most important server at work.

---

### Post by elperrillo on 2010-09-09
Can anybody help me for the love of god!!!!!!!!!!!!!

---

### Post by elperrillo on 2010-09-09
Please!!!!!

---

### Post by elperrillo on 2010-09-09
I can't believe nobody is helping me with this!

---

### Post by rtimai on 2010-09-09
elperrillo,

Sorry you're not getting a quick response. Please remember that this is a forum, like a bulletin board with thousands of messages in the Desktop Environment forum alone, and they're answered by fellow Ubuntu users like yourself. I don't think many Ubuntu users have much experience with NX. NoMachine NX is not supported in available repositories that I know of. I had to look it up to find out what it was. 

You may get more qualified help directly from the OEM site (below.) I don't know if NX Free receives any support, but you might find information in the documentation...

Documentation
[http://www.nomachine.com/documents.php](http://www.nomachine.com/documents.php)

Support
[http://www.nomachine.com/support.php](http://www.nomachine.com/support.php)

Good luck.

---

### Post by elperrillo on 2010-09-09
Thank you so much for your response, however I can't find anything on their website and was hoping that somebody here would help me, I just need to get into gnome so I can uninstall the dam NX and get it over with! is there anyway I can do this? I get as far as the ubuntu login window but I can't get passed that.

---

### Post by hrickh on 2010-09-09
> **elperrillo said:**
> Thank you so much for your response, however I can't find anything on their website and was hoping that somebody here would help me, I just need to get into gnome so I can uninstall the dam NX and get it over with! is there anyway I can do this? I get as far as the ubuntu login window but I can't get passed that.
Do you remember the package name used to install NX? If so, do this:

Once you've booted up (not logged in, since you can't ), switch to another virtual terminal (Type: cntl alt F1). Log in at the command line. You may want to try to find all packages with "nx" in them. Type "dpkg -l *nx*"

From there, uninstall the nx packages. Type: "sudo apt-get remove whatever-the-package-name-is".

That'll remove the nx package.

R.
==

---

### Post by rtimai on 2010-09-10
Good luck with 'sudo apt-get remove' elperrillo. The lesson to be learned here may be: If possible install from the tested repositories using Ubuntu Software Center or Synaptic Package Manager. Beyond that is the territory of more experienced users who know how to generate backtraces and file detailed bug reports. 

Oh yeah, try posting an inquiry in a Ubuntu "Networking & Wireless" forum. Someone may be able to suggest an equivalent of NoMachine NX that works for you. Good luck!

---

### Post by elperrillo on 2010-09-13
hrickh

Thanks for your response, I was able to get to the terminal and it asks me for login name and password however same thing happens, every time I type it, it acknowleges it as the correct username and password but instead of loggin in it prompts me for username and password again, and does not let me in. Any ideas?

---

### Post by elperrillo on 2010-09-13
rtimai, thanks for your suggestion, I was using FreeNX as a server wich worked beautifly and regular NX as client on my windows machine. However my Windows machine crashed and I had to reintall NX. After that I was not able to log in again, so I decided to uninstall FreeNX and install NX server (Big Mistake) now my server is inacessible.

---

### Post by elperrillo on 2010-09-13
UPDATE:

I was able to boot up in "Recovery Mode" and selected the option to log in as root and was able to log in, then I did the

dpkg -l *nx*

and then the 

sudo apt-get remove

and was able to remove every simgle NX package there. then I rebooted and I still can't log in.

Any Ideas??

---

### Post by elperrillo on 2010-09-14
Does anybody have any other ideas????? plase!!! I cannot aford to format my server, it is mission critical!!!

---

### Post by cain171562 on 2010-09-14
go back into recovery mode and reset your user and or root password

---

### Post by vortmax on 2010-09-14
I agree about resetting the user password through the recovery console.  While you are in there, look through the /var/log/syslog and other log files and see if you can find an error.  That would point you in the right direction.

You said this is a production server?  How long would it take you to backup your data, fresh install and restore the machine?  It might actually be the fastest way to get back up and running.

---

### Post by elperrillo on 2010-09-15
Hi Vortmax and Cain171562:

1) I cannot reset the username and password, it will not let me it comes back with a strange error. "Segmentation fault"

2) This is a proxy server that comunicates us with another network, is used 24hr/day and it is mission critical, right not what I am doing is I am working in my office with a cloned version of it. I rather not backup the data, I would not even know where to start, I have arround 150 users configured and a lot if exeptios in the proxy server and I do not know how to back that up. I rather stay away from that.

I have to fix this one

---

### Post by elperrillo on 2010-09-15
PROBLEM SOLVED!!!!

It was a samba issue, I went to and too a look at the logs at **/var/log/syslog** and spent quite some time there and finally saw an error that went something like...

**segfault error 4 in pam_smbpass**

So I went back to the login prompt and looked for all samba packages intalles using the command:

**dpkg -l *smb***

and then I decided to remote the libpam-smbpass package by executing

**sudo apt-get remove libpam-smbpass**

I rebooted and was able to log back on with no problems. Thanks to all of you that helped specially to Vortmax.

---

