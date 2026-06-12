---
title: "&quot;Give root password for maintenance&quot; on shutdown ??"
date: 2006-09-20
forum: Desktop Environments
---

### Post by James79 on 2006-09-20
Since yesterday, I've been getting a weird message on my server when I'm trying to shutdown. I've attached a screenshot.

Observations:

- I **ONLY** get the message strangely enough when I ssh to my server, and type "**shutdown now**". "shutdown -r now" seems to work fine and reboots the server as intentioned.

- I **do NOT** get the message when I go to my server and choose shutdown at the login screen (I rarely ever physically log into it unless I'm doing some maintenance)... so when I click on shutdown/reboot on the gnome graphical boot screen, everything works fine. Not sure what the difference is between doing that and issuing a command at the CLI...

So as you can see from the screenshot, it asks for the root password, or CTRL-D to continue. It doesn't mention WHAT the password is for. If I enter my root pw, it drops me to shell and does nothing. If I hit ctrl-d, it actually restarts gnome and I'm back at the login screen! :confused: 

I've been setting up this server from scratch since last saturday. So I've been changing things on a daily basis obviously... the only change that I made that I believe is relevant to this is adding "rootpw" to my /etc/sudoers file, in order to get sudo to use the root password instead of my own. 

Could that be responsible for this? If not, what else??

TIA! ~ James

---

### Post by kidders on 2006-09-20
Hi there,

**shutdown now** *is* the command for dropping to a maintenance shell. If you want to halt your computer, try **shutdown -h now**.

Basically, "shutdown" requires an instruction to tell it what to do after shutting down your system, usually either "-r" (reboot) or "-h" (halt). See **man shutdown** for more detail.

---

### Post by James79 on 2006-09-20
Oh damn... that would explain it then wouldn't it :redface: 

Will halt turn off the computer as well?

I'll try this as soon as I get home...

Thanks! James

---

### Post by kidders on 2006-09-20
Hehe no worries :-)

The only reason using the "-h" option could fail to cut the power is if Linux and your BIOS's power manager aren't getting along. You should be fine though.

Best of luck.

---

### Post by Suman Jyothi on 2008-04-15
hi

while booting system i am getting something error like give root password for maintenance or press ctrl+D
before showing the error it is also shows file system error
orcl ================         | 58.46%
what might be the problem 
to rectify this i have also reinstalled the operating system inspite of that it is bagging the same error.

---

