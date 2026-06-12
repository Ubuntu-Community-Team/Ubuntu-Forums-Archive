---
title: "Keeping X from loading..."
date: 2004-12-17
forum: Desktop Environments
---

### Post by oberon on 2004-12-17
I have done some searching thought the forum and still couldn't but couldn't find an answer.  How does one keep X from loading on boot.  This is a headless box, and I would like to keep the resources free for the daemons that are running on the box.  Any had a success?

-oberon

---

### Post by daniels on 2004-12-17
sudo apt-get remove xserver-x{free86,org}, is a pretty good way to do that.

---

### Post by regeya on 2004-12-17
[QUOTE=oberon]I have done some searching thought the forum and still couldn't but couldn't find an answer.  How does one keep X from loading on boot.  This is a headless box, and I would like to keep the resources free for the daemons that are running on the box.  Any had a success?

-oberon[/QUOTE]

At the risk of being flamed, why Ubuntu at all in that case?  Ubuntu is really intended for use as a workstation OS...why not vanilla Debian?

Other than that, I don't know whether the Debian|Ubuntu process changes /etc/inittab (as in runlevel 5) or if it just adds an entry to runlevel 3...*shrug*  I'd see if /etc/inittab is set for runlevel 5 as a default, and change it to 3 if it is.  Viola.

---

### Post by daniels on 2004-12-17
No, Ubuntu is targetted equally towards workstations and servers; it's just that the default install happens to be for workstations (admins running headless workstations are more likely to be far more skilled).  'linux custom' at the install prompt gives you a Ubuntu install with nothing like X, GNOME, et al installed; but you can install many of the programs from our supported seed, such as Apache 2, Postfix/Exim/whatever, BIND, PHP, ...

---

### Post by oberon on 2004-12-17
Well I am not that skilled yet, but thought that by dumping the monitor and forcing me to do everything through SSH would kinda force me to learn it.  I would like to keep X on cuz if I need to do somthing and havn't figureing out how to do it on CLI than I can always tunnel X apps to get it done (I do need xserver for this right?).  I will mess with the initab settings when I get home.  Thanks for the help.

-oberon

---

### Post by Hellsteeth on 2004-12-19
I was in exactly the same position.

I only wanted a minimum install but did not know how to do everything from a terminal so wanted the ability to occasionally start up X to get me out of jail.

I was also conscious of keeping the number of process down on my antique P200 I was using.

This is how I stopped X from automatically starting up, but retaining the ability to manually fire it up on demand.

In just two steps this is done like this.
1.	Confirm which Runlevel your system boots up into. i.e. Runlevel n
2.	Remove the symbolic link to gdm in /etc/rcn.d &#8211; changing n for the Runlevel 

If this is really new to you or other readers here it is again in more detail.

For whatever reason my system boots up to Runlevel 2. You can find out what yours does by issuing the command *$ runlevel* 
My system reports &#8220;N 2&#8221; which means I am now in Runlevel 2 and have not switched from anything else.

Knowing your runlevel you need to edit the directory containing the Runlevel 2 scripts and disable the Gnome Desktop Manager or &#8220;gdm&#8221;.

This is done like this. Change to the directory concerned

*$ cd /etc/rc2.d* &#8211; (This would be /etc/rc3.d for Runlevel 3.)

If you do a *$ ls &#8211;l*  you will see a list of links pointing to files in /etc/init.d

One of them will be along the lines of

S99gdm -> ../init.d/gdm      (Your "99" may be different, in which case replace with what you see in the next step)

This link needs to be removed

*$ sudo rm S99gdm*

This prevents ubuntu running the Gnome Desktop Manager at boot.

Now when you want to start X, you can just issue either of the following commands after loging in.

*$ startx*  which takes you right in or* $ sudo gdm*  for the normal start screen.

Best of luck.

---

### Post by Johan on 2004-12-19
Wouldn't it be easier to just do an apt-get remove gdm?

---

### Post by tomchuk on 2004-12-19
To simplify Hellsteeth's solution...
```

sudo apt-get install rcconf
sudo rcconf

```
Gives you a nice ncurses interface to enable or disable services from your current runlevel. Now your computer will boot, enabling only the services you want it to. If you want to start X and any other services you disabled you can just do:
```

sudo telinit 3

```
which will take you to runlevel 3 which will still contain all the original startup symlinks that runleve 2 had before you disabled them. You can set the default runleve in /etc/initab changing the 2 in the line "id:2:initdefault:" to whatever runlevel you want (well probably not 1 or 6 unless you're playing a mean joke on someone)

---

### Post by rageear on 2004-12-19
[http://sivut.koti.soon.fi/lindj/debian_problems.html#howto3](http://sivut.koti.soon.fi/lindj/debian_problems.html#howto3)

I used the update-rc.d method to disable the X server on my Ubuntu box and it seems to have worked fine so far.  Now all my administration is done via SSH; but I still have X kicking around in case I need it.

---

### Post by empcarl on 2007-03-02
Hey Hellsteeth .. makes sens e. nice one ... and to teh rest to, needed 'pure shell mode' to change drivers for NVIDIA :|

---

