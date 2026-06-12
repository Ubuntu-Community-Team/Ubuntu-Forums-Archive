---
title: "Startup in console mode"
date: 2006-01-06
forum: General Help
---

### Post by Tottigoal on 2006-01-06
Hi all,
I'm sorry to post this question (probably it's easyer than I think)...

I want to start up my ubuntubox without starting the server X.

I thought I did it the installation before, but then I had problems and I had to make a complete new installation.
And I really don't know if the problem was due to the dis-activation of the server X or for other reasons (I disconnected the floppy..... :rolleyes: ).

So, How can I start my ubuntubox directly to text? I would like to start the server later using 'startx' as a command.

I hope I was clear and Sempre Forza Roma. :KS 
Marco

---

### Post by dcstar on 2006-01-06
[QUOTE=Tottigoal]Hi all,
I'm sorry to post this question (probably it's easyer than I think)...

I want to start up my ubuntubox without starting the server X.

I thought I did it the installation before, but then I had problems and I had to make a complete new installation.
And I really don't know if the problem was due to the dis-activation of the server X or for other reasons (I disconnected the floppy..... :rolleyes: ).

So, How can I start my ubuntubox directly to text? I would like to start the server later using 'startx' as a command.

I hope I was clear and Sempre Forza Roma. :KS
Marco[/QUOTE]
When the system does try to start the X server, just press CTRL-ALT-F1 to go to a text login screen.

Once logged in, you can kill the stalled X process and restart it later when you want.

---

### Post by le_jawa on 2006-01-06
Slick answer!  That's the hard way, but slick.

Here's an easier, more pesistent way to deal with that:

Change directories to /etc/rc2.d

[FONT=Courier New] cd /etc/rc2.d[/FONT]

Then as root, delete the link to the gdm startup script, probably S13gdm

[FONT=Courier New] sudo rm S13gdm[/FONT]

then re-enter run level two by entering

[FONT=Courier New] sudo init 2
[/FONT] 
or 

[FONT=Courier New] sudo telinit 2[/FONT]

Either will work, but they say telinit is a cleaner way of doing it.  This should kill your x-server and start you at a command prompt.  You could also just reboot.

Either way, your computer will now start without X every time.

For more info on Linux run levels and initialization scripts, check out [http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlrunlevels.html ]("http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlrunlevels.html")
and read section 3, 4 and 5.  It seems to explain things pretty well. Let us know if you still need help of course.

Good luck!

---

### Post by zappa86 on 2006-01-06
If you ever want your GDM back you will need to go into the rc2.d directory and under super user remake the symlink
```
ln -s ../init.d/gdm S13gdm
```

---

### Post by Tottigoal on 2006-01-07
Thanks to all, that was quick and professional!

Sempre Forza Roma :KS

PS: special 10x to le_jawa, I did what you suggested.

---

