---
title: "Boots to terminal instead of Desktop"
date: 2006-03-16
forum: Desktop Environments
---

### Post by KiLLeR_WoMBaT on 2006-03-16
How do I have Ubuntu boot to the GDM graphical interface and load gnome?  It used to do this and has suddenly stopped.  Probably something broken from me tinkering with it; so don't ask me what I did (could be a million different things).
This all started from freaking Firefox!  It just shuts down on it's own randomly.  I tried several different solutions posted here in the forums...but to no avail.

And from the terminal when I log in and type startx, the background is like this black and white checker thing with an X as the cursor and then my desktop finally shows up.

How can I fix it?

---

### Post by KiLLeR_WoMBaT on 2006-03-16
What?  Is this such a stupid question it's not worth answering?  I wish I could provide more info, but I don't really know what caused it.  Things were running fine for MONTHS and now this.

I've searched...but these forums are so bloated it's hard to find that specific thread you need.

---

### Post by Blairboy on 2006-03-16
A thought would be to try "sudo dpxg-reconfigure xserver-xorg" and set up your xorg again.  Did you maybe mess with your video settings at all?

---

### Post by Sutekh on 2006-03-16
[QUOTE=KiLLeR_WoMBaT]What?  Is this such a stupid question it's not worth answering?  I wish I could provide more info, but I don't really know what caused it.  Things were running fine for MONTHS and now this.

I've searched...but these forums are so bloated it's hard to find that specific thread you need.[/QUOTE]
It's probably less of a stupid question and more of a difficult one.  

I know you said you've done a million things, but telling us some of them would really be helpful.

When you computer boots Ubuntu and leaves you at the command line, is there any indication that GDM encountered errors starting up?

What happens if you type this at the command line
```
sudo /etc/init.d/gdm start
```
Do you get a mesage like ```
GNOME Display Manager Starting                           [[COLOR="Red"]FAIL[/COLOR]]
```
If this is the case, you can reconfigure the GDM with
```
sudo dpkg-reconfigure gdm
```Then use this command to restart it
```
sudo /etc/init.d/gdm restart
```
If that works try rebooting and see if ou go staright to the GDM.

Problems with xserver-xorg usually result in you getting a semi-blue screen saying the the X server is not configured (I got this the other day, playing around with Dapper). You'd know if this was the case as you'd be required to acknowledge the error.

---

### Post by KiLLeR_WoMBaT on 2006-03-16
Okay, thank you for the responses.  Here goes:  I installed and ran Automatix to try and get some plugins running.  I installed all basically. (never trust that program again)  Everything was fine except for no sound and firefox would randomly exit itself.  I used update manager to install anything that had to do with ALSA; to no avail...still no sound (i've got sound at the greeter, just not in gnome).  After a few CTRL+ALT+BKSPC for various reasons that I can't remember I was stuck in some kind of loop between remote and normal login (or so it seemed).  I got back to normal login but started playing around with the Login Setup Appelet and disabled XDMCP settings in the Security and XServer tabs.  Several reboots nothing wrong.  A couple of Automatix tries again (I know...this is why I didn't want to spell this all out.  I know that's alot of tinkering with something that wasn't really broke to begin with); I still get no desktop without typing STARTX at the terminal that Ubuntu boots to.  When I reboot there is a kill message that did not used to be there about cardmanger (XXXX) some number.  I then tried a GRUB recovery boot by pressing ESC at boot time.  Same old terminal prompt.  Somewhere in there I was getting the "root can't access....blah, blah...check .Xauthority" crap.  Did what the forums said about moving that to a backup, which worked for the can't access file permissions .Xauthority stuff.  

All I want is for the Gnome desktop to start up automatically again.  I've given up on Firefox.  It's just going to exit when it wants, I guess.  I'll use Opera or something.

I do not get the blue screen.  Just the terminal where I have to type startx to get to gnome.  But it is different somehow...like with the black and white background and the "X" cursor until gnome starts.

---

### Post by KiLLeR_WoMBaT on 2006-03-16
[QUOTE=Blairboy]A thought would be to try "sudo dpxg-reconfigure xserver-xorg" and set up your xorg again.  Did you maybe mess with your video settings at all?[/QUOTE]

I tried this.  Same problem didn't help.

---

### Post by PhilOSparta on 2006-03-22
The same problem started on my box when I got a recent update to Dapper.
I tried the preceeding stuff to no avail, but the following helped:

[http://www.ubuntuforums.org/showthread.php?t=103363&highlight=gdm+broken+fully+installed](http://www.ubuntuforums.org/showthread.php?t=103363&highlight=gdm+broken+fully+installed)

Somehow the GDM was un-installed. ?!?!

Used synaptic to install gdm.  Everything okay now.

---

