---
title: "Cups config through browser"
date: 2006-06-05
forum: Desktop Environments
---

### Post by brumen on 2006-06-05
Hi, 


What is the username and the password for cups to modify the printer setup 
through the browser (localhost:631). I know you can change them 
through the ubuntu tool, but it does not work, maybe this way goes. 

Thanks a lot, 
Gorazd

---

### Post by denisesballs on 2006-06-05
First you have to add the user cupsys to the shadow group:

```
useradd cupsys shadow
```

---

### Post by andy_cowman on 2006-06-05
Then log in with your normal username and password.

---

### Post by brumen on 2006-06-06
[QUOTE=andy_cowman]Then log in with your normal username and password.[/QUOTE]

does it suffices if i just add the user cupsys 
to the /etc/group file per hand or do i have to do it 
through the useradd command??? 

thanks, g.

---

### Post by brumen on 2006-06-06
thanks a lot guys, it works now.

---

### Post by zasf on 2006-06-10
here is the full procedure

```
# Add user cupsys to shadow group
sudo adduser cupsys shadow
# add yourself to lpadmin group
sudo adduser <yourusername> lpadmin
# restart cupsys
sudo sudo /etc/init.d/cupsys restart
# configure printer via browser and enter your username and pw when requested
http://localhost:631/

```

ready to print!

---

### Post by master_b on 2006-06-20
Matteo

THANK YOU!

this fixed my problem re getting my Canon BJ printer to work after upgrading Kubuntu Dapper to KDE 3.5.3

Received no replies to my post elsewhere

This should be a HOWTO

Bill

---

### Post by zasf on 2006-06-21
Nice to know it was helpful :)
Ciao

---

### Post by raluke on 2006-06-29
Matteo, thanks very much, this saved me too!  

Just in case it is of any help to anyone with a Lexmark T622, the following subsequent settings worked for us:

1.  device = "Internet Printing Protocol (ipp)"
2.  device URI = "socket://<printer's four-octet IP address>"
3.  Make/manufacturer = "Raw"
4.  Model/driver = "Raw Queue (en)"

The listed Lexmark printers didn't include the T622, or anything even close, as far as I could tell.  A colleague knew about using the "raw" stuff instead.

Thanks again,
-Robert

---

### Post by Ron Byers on 2006-07-25
> **master_b said:**
> Matteo

THANK YOU!

this fixed my problem re getting my Canon BJ printer to work after upgrading Kubuntu Dapper to KDE 3.5.3

Received no replies to my post elsewhere

This should be a HOWTO

Bill

I have a Canon BJ Printer. I can't get it to work either. What settings did you use?

---

### Post by claypole on 2006-07-26
Thanks, this was really helpful :D 

[http://www.linuxprinting.org](http://www.linuxprinting.org) is a very useful resource for specific drivers and general CUPS help too.

---

### Post by lmcogs on 2006-08-19
Printing is an essential part of any os and it took me some hours to come across this thread which worked and I am not a raw beginner.  Another problem I have is with sudo and root.  Its a pity we have no root option in the installation, which I am comfortable with.  Can I set up root etc

Anyway thanks for help

---

### Post by lenswipe on 2008-05-22
hi all.

im trying to print to a laserjet 2420n through an ethernet connection on ubuntu 7.10 gutsy gibbon. When i click print and send the job the printer keeps printing the job infinately or until paper runs out. Which in a laser printer is a hell of alot of paper!

anyone got any ideas as to why this is happening?


thanks

-L

---

