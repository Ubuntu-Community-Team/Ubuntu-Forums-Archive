---
title: "GDM problem!!"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Duncan_Idaho on 2005-11-02
I got this huge problem with gdm, when booting after the nvidia logo screen
instead of loading the gdm screen, it trows this error message ''can't load /usr/share/gdm/themes/human.xpm'' or something like that, and I can't log in so I figured the problem was that gdm theme...... so I tough of repair it with synaptic, but I can't even do 'startx'
so, I switched to recovery mode in the grub menu, and tried to apt/get reinstall it, but it trows me lots of errors and finally don't let me do that. also trid to purge it and remove it, to install it again, but not worked, 
I thik gdm pakage got corrupted or something, please help me, it's really late and I don't know what to do, I don't want to reinstall ubuntu all over :confused: 

right now I'm using a Slax live-cd I had to post this (if it helps I also got a copy of mepis)

PS: sorry my english, I'm not a native speaker  :p :KS

---

### Post by aysiu on 2005-11-02
[QUOTE=Duncan_Idaho]I switched to recovery mode in the grub menu, and tried to apt/get reinstall it, but it trows me lots of errors and finally don't let me do that.[/QUOTE] What were the errors?

---

### Post by Duncan_Idaho on 2005-11-02
[QUOTE=aysiu]What were the errors?[/QUOTE]
I don't remember very well 8-[ , but they where related to the GDM pakage, it was something when apt was configuring the pakage, after I told him to reinstall it, it said something like the actual gdm pakage didn't let it reconfigure it nor re-write it's configuration file 'n stuff   :-k 
sorry, right now I'm too sleepy to remember, but tomorrow morning I'm gonna write down the complete error and post it #-o

---

### Post by ecobuntu on 2005-11-02
[QUOTE=Duncan_Idaho]I don't remember very well 8-[ , but they where related to the GDM pakage, it was something when apt was configuring the pakage, after I told him to reinstall it, it said something like the actual gdm pakage didn't let it reconfigure it nor re-write it's configuration file 'n stuff   :-k 
sorry, right now I'm too sleepy to remember, but tomorrow morning I'm gonna write down the complete error and post it #-o[/QUOTE]

Good!  That's the only way we can help :)

---

### Post by Duncan_Idaho on 2005-11-03
I managed to start my gnome session, but when I started synaptic it trows me this error, saying that I cannot run synaptic as root cuz it's impossible to copy my Xauthorization archive, what's that archive for :confused: 

for now I bypassed that running from a terminal ```
sudo synaptic
```
but when I intend to reinstall gdm, it said that it cannot make 'stat' over './usr/share/gdm/themes' that was going to be instaled
any clue 'bout how to repair gdm pakage? ](*,) 
I rally don't wanna reinstall ubuntu all over again, but I'm against time becuz I have a deadline nextweek on a report I'm writting and I have to finish it before the weekend [-o<

---

### Post by southernman on 2006-01-11
Amen to "I really don't wanna reinstall ubuntu all over again"!

I have a couple of links for you to look at... since I am not that hip myself to tell you how to do this things. :p

This link will show you how to reconfigure your x server:
[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

And this link will teach you how to backup and restore said backup for your system. It works well as I just spent about an hour doctoring my own system from a backup:
[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+system]("http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+system")

HTH's some how

---

### Post by leech on 2006-01-11
try from a terminal 'sudo gdmsetup' this will let you change your themes.  I would suggest changing it to Plain mode (under the Style).  Then close X, make sure it's not running, and make sure gdm is not running, then 'sudo gdm' and hopefully it'll work.

Also it sounds like your Xauthority may have been corrupted, just 'rm ~/.Xauthority'

Leech

---

### Post by southernman on 2006-01-11
Here is the command to reconfigure your gdm

You first will need to run:
> sudo /etc/init.d/gdm stop

Then run:
> sudo dpkg-reconfigure gdm

To restart gdm do:
> sudo /etc/init.d/gdm start

---

### Post by leech on 2006-01-11
You missed the -.  It's 'sudo dpkg-reconfigure gdm'

That could work as well, though it sounds like he's already tried to remove and re-install it with apt-get.  Could be he needs a 'sudo apt-get -f install' as well.

Leech

---

### Post by southernman on 2006-01-11
Thanks Leech! I edited my post to reflect the change.

---

