---
title: "Please help, I am desperate"
date: 2006-01-05
forum: Desktop Environments
---

### Post by HJB on 2006-01-05
Just before x-mass I build a web server to use in my office to capture stats of a few people. I installed ubuntu breezy server, apache2,  php5.1 and mysql. Everything worked (is working) fine. 

The BIG problem is that I left the same day on holiday and the cleaner must have chucked the paper which I left at the comp with all the passwords on. [COLOR="Red"][COLOR="Red"]I can’t for the life of me remember my user password[/COLOR][/COLOR]. I can access via phpmyadmin and have also set up a ssh server on that day.

PLEASE HELP! Where do I start? I can take the machine home if that would help to connect to my other Linux box at home if there is a way to look in the logs of the ssh or access a file on the hard drive.
I don’t know anymore. I have been trying every combination I can think of, of all the usual passwords I use, but nada.

Is there a way to brute force try to open the box via ssh or via access to a password file or something similar which I can get of the hard drive?

I can’t export the database via phpmyadmin but that is the last route ill consider (time, time, time)

I desperately need to change a php page and add a user but I can’t!!

HELPPPP, what can I do?

Bye
H

---

### Post by encompass on 2006-01-05
There are many ways to ceack the password.  First try to talk to the people in your irc channels.  They have helped me.  Next google, be sure to put ubuntu in your search.

---

### Post by mcduck on 2006-01-05
when you boot the machine, there's option for 'safe mode' or something like that in grub menu. Choose that, and you'll get into text mode as root. then do 'passwd <username>' and set a new password.

---

### Post by slux on 2006-01-05
Did that work out for you? Debian, at least, asks for the root password when booting into recovery (single) mode :P

You can still boot with a livecd, mount your root drive and edit /etc/passwd & /etc/shadow. One more way to get in with a very simple environment is to pass init=/bin/sh thru grub/lilo :)

It's not very hard to get in if you have physical access to a system. protecting the BIOS helps a bit but you can still always open the machine and reset it. :P

---

### Post by mcduck on 2006-01-05
[QUOTE=slux]Did that work out for you? Debian, at least, asks for the root password when booting into recovery (single) mode :P

You can still boot with a livecd, mount your root drive and edit /etc/passwd & /etc/shadow. One more way to get in with a very simple environment is to pass init=/bin/sh thru grub/lilo :)

It's not very hard to get in if you have physical access to a system. protecting the BIOS helps a bit but you can still always open the machine and reset it. :P[/QUOTE]
Ubuntu of course doesn't ask for root password, as there isn't any ;)

---

### Post by HJB on 2006-01-05
[QUOTE=mcduck]when you boot the machine, there's option for 'safe mode' or something like that in grub menu. Choose that, and you'll get into text mode as root. then do 'passwd <username>' and set a new password.[/QUOTE]

Hi mcDuck. Thanx a lot. Im back in. I cant believe its so easy to 'hach' into a linux box. What do people do (should I do) to prevent anyone else from just doing the same. The box is in a very quiet out of the way place where anyone can go at anytime?

Thanx again for the help
Bye
H:smile:

---

### Post by nocturn on 2006-01-05
[QUOTE=HJB]Hi mcDuck. Thanx a lot. Im back in. I cant believe its so easy to 'hach' into a linux box. What do people do (should I do) to prevent anyone else from just doing the same. The box is in a very quiet out of the way place where anyone can go at anytime?

Thanx again for the help
Bye
H:smile:[/QUOTE]


1# Install a grub password
2# Force boot to HD only in your BIOS
3# Set up a BIOS password

These help, but it is almost imposible to keep someone out that has physical access to a machine ...

---

### Post by bulldogzerofive on 2006-01-05
This page has a some good ideas to secure your linux box:

[http://www.puschitz.com/SecuringLinux.shtml](http://www.puschitz.com/SecuringLinux.shtml)

If you think that it is harder to hack into a windows box when you have physical access read this one:

[www.irongeek.com/i.php?page=security/localsamcrack](www.irongeek.com/i.php?page=security/localsamcrack)

---

### Post by slux on 2006-01-08
Indeed, even with protecting the bios and only allowing HD-boot any would-be attacker will just have to pop the case open and use a jumper to reset the bios.

Physical access is pretty much guaranteed to get you in. You can of course make it more difficult (lockable case comes to mind) but basically can never stop a determined attacker.

---

### Post by handy on 2006-01-08
I don't know if any of the info' from the following site will help?

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=639759](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=639759)

These are the appropriate headings listed, scroll down to find them.

# 16 Rescue Mode

    * 16.1 How to gain root user access without login
    * 16.2 How to modify kernel boot-up arguments, to gain root user access
    * 16.3 How to use Ubuntu Installation CD, to gain root user access
    * 16.4 How to change root user/main user password if forgotten
    * 16.5 How to change GRUB menu password if forgotten

All the best.

handy

---

