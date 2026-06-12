---
title: "best option for a file server??"
date: 2006-08-20
forum: Desktop Environments
---

### Post by hobieone on 2006-08-20
i would like to setup a second box to use as a file server. basically to store picture and transfer files from one computer to another on my home network and possibly remotely. basically have network with one linux machine and the other is a laptop with windows xp. normaly the laptop ia hooked up to the network wirlessly and may need to acess files remotely thru the internet if traveling. wondering whats the bast and easiest way to set this up or what program  should i use on ubuntu plus having password security is must due to logging  into the file server remotely.

---

### Post by crane on 2006-08-20
I think it would really be more dependant on what your comfortable with.
An FTP server would allow access across the network and the internet. You can also connect through ssh or http.
You can set up an ftp server which will be password protected and you can "cage" the access. Meaning when you log into the server you will only be allowed to access a certain folder. You would not be able to go to the root folder or any where else. Also be sure not to allow root the ability to even log in remotely.

Just one suggestion. Do some research. There are many ways of connecting.

---

### Post by neouser99 on 2006-08-21
WARNING - this is not a shameless plug for anything!

it would seem that you have already got ubuntu up and running good. if you really like linux, and would want to take it to the next step and learn what it is really all about (and have the time to spare, like hours), i would look into setting up a Gentoo box. its a bleeding edge distribution, forces you to build it and setup things without a graphical installer (even though i think it has that too now) step by step, has some great tools and imho the best for servers.

wether you do down that path or not, since windows is involved, i would have to say that Samba is definately the way to go. it will allow seemless integration with any windows pcs, its encrypted, and it works with most linux distributions too. like crane said, there is also ftp and rsync, some clear text protocols that are very fast and have been around forever.

-neo

---

### Post by BoneKracker on 2006-08-21
typical gentoo user -- "omg linux!"  ;)
       [http://funroll-loops.org/](http://funroll-loops.org/)


SMB is a good approach for setting up the file server for use within your home network.  However, it's not appropriate for use over the open internet (over vpn would be ok).  The windows equivalent of this would be turning on "file & printer sharing" and turning off "windows firewall".  About as smart as a screen door in a submarine.

Since you are trying to set up a connection for your own use, I'd recommend OpenSSH.  The main benefit of this approach (vs. ftp or http) is that it gives you complete shell access to your home computer.  It's low overhead and secure if properly configured.

To reduce vulnerability, change the port to something unusual and disable root login (in /etc/sshd_config).  To be even safer, also disable password-based logins altogether and issue yourself a public key on the laptop.

See the man...
man sshd
man sshd_config

If you want to share the files with others (put links to them in emails, or let people come get them), or if you aren't comfortable working in a shell, then ftp or http would be better.  Look into how to "chroot" the ftp or http server, and put the file repository in its own partition or directory.  That way if it gets hacked, all you lose is your pictures

---

