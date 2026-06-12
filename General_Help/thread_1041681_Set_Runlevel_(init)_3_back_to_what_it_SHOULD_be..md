---
title: "Set Runlevel (init) 3 back to what it SHOULD be."
date: 2009-01-16
forum: General Help
---

### Post by Spudz0r on 2009-01-16
Is it possible and if so how can i do it.

I want to reset runlevel 3 back to a Multiuser, cmdline ONLY (No X-Server at all)

basically, It has become a headache trying to install things that dont like x running. I need to have a way to include all my bootup procedures including my wireless dongle for network access.

I also need this for installing the NVIDIA drivers which require no X running. I tried this in the "recovery" mode but it gives me an error when its installing OpenGL stuffs.

basically, what i want is to be able to set one of my boot options in GRUB to boot into a multiuser console.

I used to be able to do this simply by adding a "3" to the end of the boot args but alas, runlevel 2-5 are the same in ubuntu now. (last ubuntu i used was 7.4)

so to recap. I ONLY want to edit runlevel 3, i want to leave all the others as they are. I want this to be a perminant change to runlevel 3. (i still want 2 to be the default)

---

### Post by taurus on 2009-01-16
Wait for your machine to finish booting.  Then at GUI login screen, press <Ctrl><Alt>F2 with log in with your username and password.  Now, stop GDM.

```
sudo /etc/init.d/gdm stop
```
You should be able to install nvidia driver now.  And when you want to restart X again, just run

```
sudo /etc/init.d/gdm start
```

---

### Post by Spudz0r on 2009-01-16
except that doesnt seem to kill X.. nor is it what i want to do.


that would be the first thing i tried.


run the NVIDIA setup. - "X Server is Running"

---

### Post by bodhi.zazen on 2009-01-16
Ubuntu uses upstart and the run levels 2-5 have ALWAYS been the same.

You have to stop kdm or gdm and exit your gnome or kde session.

Is there some reason you ware manually installing the nvidia drivers ?

Why not use the drivers in the Ubutnu-repositories ?

If you *must* install the nvidia drivers from within X as you say, try Envy.

Envy is also in the repos and can be run from within X

For additional information see :

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mssever on 2009-01-16
Doing what you want would be difficult. It would involve both editing the links in /etc/rc*.d and toying with upstart. Ubuntu hasn't distinguished between runlevels 2-5 for as long as I've been using it (I started with Dapper, 6.06). By default, it tuns in the equivalent of runlevel 2, though with upstart, runlevels are only emulated.

Taurus' suggestion will do what you need. If ```
sudo service gdm stop  # I love how Ubuntu has finally added this command from Red Hat-land
```doesn't kill X, then X is wedged. In that case, just kill X via your favorite method. I like htop for this and related tasks.

---

### Post by Spudz0r on 2009-01-16
fair enough..

must be remembering things from my fedora days (could never get everything working properly in ubuntu on my old system)


i will retry the gdm stop. but i dont think it actually does anything on my system for some reason.

---

### Post by dcstar on 2009-01-16
> **Spudz0r said:**
> Is it possible and if so how can i do it.

I want to reset runlevel 3 back to a Multiuser, cmdline ONLY (No X-Server at all)
.......
so to recap. I ONLY want to edit runlevel 3, i want to leave all the others as they are. I want this to be a perminant change to runlevel 3. (i still want 2 to be the default)

[http://ubuntuforums.org/showpost.php?p=1349493&postcount=4](http://ubuntuforums.org/showpost.php?p=1349493&postcount=4)

---

### Post by Spudz0r on 2009-01-17
lol.

i had already tried that, but as what is established. runlevel 3 is exactly the same as runlevel 2 in ubuntu.


what the poster was refering to is a multiuser non gui environment (like what you would get with fedora init 3), but alas.. telinit 3 does not do this in ubuntu. it just starts the x server and pretty much continues the normal boot.

if somebody knows where to point me to edit the configs to remove x from loading just from runlevel 3. thats pretty much all i need really.

---

### Post by heindsight on 2009-01-17
> **Spudz0r said:**
> 
if somebody knows where to point me to edit the configs to remove x from loading just from runlevel 3. thats pretty much all i need really.

well you could do
```
cd /etc/rc3.d
mv S30gdm K70gdm
```

In which case gdm will be stopped in runlevel 3.

but (as long as everything else in /etc/rc3.d is exactly the same as in /etc/rc2.d) doing
```
sudo telinit 3
```
would effectively be equivalent to doing
```
sudo invoke-rc.d gdm stop
```

i think you'd probably be better off just stopping and restarting gdm (using invoke-rc.d) when you don't want X running.

---

### Post by unutbu on 2009-01-17
The command
```

sudo update-rc.d gdm stop 70 3 .
```

would stop gdm from running on runlevel 3. It adds a symlink from /etc/rc3.d/K70gdm to /etc/init.d/gdm.

If you'd like a GUI to aid in configuring the runlevels, install the sysv-rc-conf package.

You might find this interesting too: [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by dcstar on 2009-01-17
> **Spudz0r said:**
> lol.

i had already tried that, but as what is established. runlevel 3 is exactly the same as runlevel 2 in ubuntu.


what the poster was refering to is a multiuser non gui environment (like what you would get with fedora init 3), but alas.. telinit 3 does not do this in ubuntu. it just starts the x server and pretty much continues the normal boot.

if somebody knows where to point me to edit the configs to remove x from loading just from runlevel 3. thats pretty much all i need really.

You simply edit the links in /etc/rc3.d and add/remove what you want.

---

### Post by Spudz0r on 2009-01-18
thought it would be something like that (couldnt remember what the files were)


assuming i just hash out all references to GDM and X (ubuntu uses what now, XOrg or X11.. its been a while...)

edit - went over last few posts also:  thanks for the input guys.. I dont mind using the console to make it console only for runlevel 3. (its half the point)..

its been a few years since i really got into linux, and then it was on redhat/fedora so it was a little different... and THEN it was also on a VM so again, not quite the same.

as silly as it sounds, i really like having the option to boot into just a command line (the single user mode just doesnt to what i want it to... its good for diags, and thats about it), simply have an additional grub menu item to boot into runlevel 3.. or even being able to switch after the machine is on is very handy. (as i learn more commands its likely not needed as much as i could just use what has been listed here)

- i also looked at that link.. i do like that sysv-rc-conf package.. seems to take a bit of the 'fun' out of it.. but it looks very quick to make changes.

---

### Post by unutbu on 2009-01-18
Spudz0r, this guide shows how to edit GRUB's /boot/grub/menu.lst (and /etc/event.d/rc-default) so you can boot directly into run level 3. 

There is a slight error in the guide, however. Read the guide and the ensuing comments. 

[http://ubuntuforums.org/showthread.php?p=5281223#post5281223](http://ubuntuforums.org/showthread.php?p=5281223#post5281223)

---

### Post by bodhi.zazen on 2009-01-18
> **Spudz0r said:**
> thought it would be something like that (couldnt remember what the files were)


assuming i just hash out all references to GDM and X (ubuntu uses what now, XOrg or X11.. its been a while...)

edit - went over last few posts also:  thanks for the input guys.. I dont mind using the console to make it console only for runlevel 3. (its half the point)..

its been a few years since i really got into linux, and then it was on redhat/fedora so it was a little different... and THEN it was also on a VM so again, not quite the same.

as silly as it sounds, i really like having the option to boot into just a command line (the single user mode just doesnt to what i want it to... its good for diags, and thats about it), simply have an additional grub menu item to boot into runlevel 3.. or even being able to switch after the machine is on is very handy. (as i learn more commands its likely not needed as much as i could just use what has been listed here)

- i also looked at that link.. i do like that sysv-rc-conf package.. seems to take a bit of the 'fun' out of it.. but it looks very quick to make changes.

See if this link helps : 

[http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml](http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml)

---

### Post by Spudz0r on 2009-01-18
> **unutbu said:**
> Spudz0r, this guide shows how to edit GRUB's /boot/grub/menu.lst (and /etc/event.d/rc-default) so you can boot directly into run level 3.

i was under the impression i could just add a "3" to the end of the line, and remove splash from its args.. - at least this is how u set a runlevel on boot in redhat.


but thanks to the help in this guide i will try out modifying the rc3.d and booting into runlevel 3. if that works.. i will be one happy chappy.. as its the second (first was getting the draytek dongle to work) hurdle in getting my ubuntu working how i like.

next hurdle is getting compiz to work properly (it dies on load atm. think it isnt loading GL properly, but that could be a part of the NVIDIA drivers not installing right)

---

### Post by unutbu on 2009-01-18
I'd recommend following the instructions in bodhi.zazen's link.
That method will allow you to just add "3" to the end of your kernel line in /boot/grub/menu.lst, instead of "text".
It also allows you to boot other runlevels easily too. I like it. Thanks bodhi.zazen :)

---

### Post by Spudz0r on 2009-02-15
yeah, i got the run levels fixed, however if i boot into "3" it still loads gdm for some reason (nfi why). however if am just boot normally and when i open a terminal and switch to level 3 it closes gdm. strange.

so i just boot using text. and if i need to kill gdm once i boot normally, i use run level 3.

---

