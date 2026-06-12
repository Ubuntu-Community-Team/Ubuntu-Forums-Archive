---
title: "Login error"
date: 2005-10-17
forum: Desktop Environments
---

### Post by tebibyte on 2005-10-17
When ever I log onto breezy, the following error message pops up:
[CENTER]
> [CENTER]configuration is not correct:
The configuration file contains an invalid command line for the login dialog, so running the defalt command. Please fix your configuration.[/CENTER] [/CENTER]
I click OK and am able to log in

In addition my themed login manager does not appear, the gnome desktop manager appears instead. I would assume it is related.

I tryed changing the login theme, but it had no effect. THis problem started to occur after I upgraded from hoary to breezy. There was some "turbulence" during the upgrade. 

Finally, my shutdown, & reboot options were removed from the log out menu, but I fixed that. It turns out an option was unselected that originally allowed those options to appear.

Thank you for your help :)

---

### Post by manicka on 2005-10-17
Sounds like you've messed up some config files during the upgrade. 

What do you mean by 'turbulence'?

A backup of your home directory and a clean install may be the way to go

---

### Post by tebibyte on 2005-10-17
[QUOTE=manicka]Sounds like you've messed up some config files during the upgrade. 

What do you mean by 'turbulence'?

A backup of your home directory and a clean install may be the way to go[/QUOTE]

Sorry about the metaphor. I was speaking figurativly. I had to finish upgrading from the command promt, with no GUI. The upgrade process stopped for some reason during my first try. I rebooted to find no gui in sight. Luckly thats out of the way :???:

The OS still works fine, i don't think it is nessasary to go through all that trouble just for a login screen. Is there any other way?

---

### Post by manicka on 2005-10-17
OK, have you tried reinstalling gdm?

---

### Post by manicka on 2005-10-17
Also run 

```
sudo dpkg-reconfigure gdm
```

to reconfigure the gdm

---

### Post by tebibyte on 2005-10-18
[QUOTE=manicka]Also run 

```
sudo dpkg-reconfigure gdm
```

to reconfigure the gdm[/QUOTE]

Nothing... :(

I tried configuring it first, rebooted, and it the problem still existed. Reinstalled gdm and did a new login. still no luck. I agree that it is most likely a gnome problem. There was a similer probelm in Red Hat that I heard about, though the error was slightly different.

---

### Post by bayr00t on 2005-10-22
I resolved it by following the instructions posted [here]("http://ubuntuforums.org/showthread.php?t=78740&highlight=%22login+dialog%22").

HOWTO:
1. ctrl+alt+F1 (to leave the GUI and login to the console)
2. sudo /etc/init.d/gdm stop (to stop gdm)
3. sudo apt-get remove gdm --purge (to remove old gdm configuration files)
note: write down, on a paper, which software is going to be removed!
4. sudo apt-get install gdm ubuntu-desktop (+add all the software removed)
5. sudo /etc/init.d/gdm start (after this I rebooted the machine)

...and it worked ;)

---

### Post by tebibyte on 2005-10-25
> > sudo apt-get install gdm ubuntu-desktop

I did the previous steps but now can not install gdm again. Now I am without a GUI.

Error:
Packdge GDM has no installation candidate.

Now ...I'm GUIless

-----
Nevermind, I tryed the command agian, and everything works fine now. Thank you so very much.

---

