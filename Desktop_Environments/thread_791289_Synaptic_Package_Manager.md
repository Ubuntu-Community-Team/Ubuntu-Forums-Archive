---
title: "Synaptic Package Manager"
date: 2008-05-12
forum: Desktop Environments
---

### Post by kiwi-pete on 2008-05-12
Hello all, I have a problem with my Ubuntu Hardy Heron desktop.
When I try to open Synaptic Package Manager from System, Administration, it tries to open, but doesn't.
I can run this application from the Terminal program using sudo synaptic.

This is what is displayed in terminal when I execute this command.

kiwipete@Ubuntu-laptop:~$ sudo synaptic
sudo: unable to resolve host Ubuntu-laptop
[sudo] password for kiwipete: 

It has just recently started behaving like this, everything was just fine and dandy prior to this.

PS. im a noob at this Linux too, having only used it for 3 weeks now. No dual booting, Linux all the way on this Laptop.):P

---

### Post by zenwalker on 2008-05-12
After entering password, do u get the GUI or what error is displaud?

Also can u change the host name to some thing blah blah. I wonder why its giving problem with host name. Better if left blank i guess.

---

### Post by corevette on 2008-05-12
it looks like there is a problem with 'sudo' more than 'synaptic'
try running
```
synaptic
```
without sudo and see if it loads up

if it loads up fine, it's a sudo/permission fault
if it doesn't load up, it's a synaptic problem

---

### Post by Fenris_rising on 2008-05-12
your not alone. ive had problems with that. admin starts but fails to follow through and ask for the password. thats not through terminal here btw for me. in my ignorance i just said screwit and reinstalled heron. no ones come up with an answer so far to my same question. hope you do though.

---

### Post by kiwi-pete on 2008-05-12
> **corevette said:**
> it looks like there is a problem with 'sudo' more than 'synaptic'
try running
```
synaptic
```
without sudo and see if it loads up

if it loads up fine, it's a sudo/permission fault
if it doesn't load up, it's a synaptic problem

I tried this and got this error in a seperate box.

Starting without administrative privileges

You will not be able to apply any any changes. But you can still export the marked changes or create a download script for them.

The application did load all the same though.

---

### Post by corevette on 2008-05-12
that error was supposed to come up, because you didn't type in 'sudo'
so it looks like a 'sudo' problem then
what happens if you type:
sudo nautilus
or
sudo rhythmbox
or
sudo firefox

does that message come up again?

---

### Post by kiwi-pete on 2008-05-12
Ok, here is what I get,

kiwipete@Ubuntu-laptop:~$ sudo rhythmbox
sudo: unable to resolve host Ubuntu-laptop
[sudo] password for kiwipete: 
sudo: unable to resolve host Ubuntu-laptop
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:30397): WARNING **: Unable to add monitor: Not supported
seahorse nautilus module shutdown
kiwipete@Ubuntu-laptop:~$ 
~: This opens the file viewer though


(rhythmbox:30074): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
kiwipete@Ubuntu-laptop:~$ 

kiwipete@Ubuntu-laptop:~$ sudo firefox
sudo: unable to resolve host Ubuntu-laptop
kiwipete@Ubuntu-laptop:~$ 
~: couldn't run the application because it was already running?

~:This message appears in a seperate box.
Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

Thanks, Pete.

---

### Post by kiwi-pete on 2008-05-18
It looks like I have this all sorted now, thanks for all the help guys.:biggrin:

See this thread for my end results. [http://ubuntuforums.org/showthread.php?t=797442](http://ubuntuforums.org/showthread.php?t=797442)

I gotta learn not to go poking around at things I know little about.:confused:

---

