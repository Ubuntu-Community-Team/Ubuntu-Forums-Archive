---
title: "Suspend to ram (on a desktop NOT a laptop)"
date: 2005-12-25
forum: General Help
---

### Post by Bananas21ca on 2005-12-25
Im wondering how to get my desktop computer to suspend to ram. I couldent get acpi or apm to work and all the forum posts about this are for laptops. Is it the same thing? Im a complete noob as you can tell:razz: Anyone else try this?

---

### Post by missmoondog on 2006-01-03
very good question and i see no responses. i've been searching for the whole 2-3 months i've been using ubuntu for an answer to this.

edit:
after some more searching around here, i found a reference to install the gnome power management package. doesn't appear to do anything. :(

---

### Post by malmjako on 2006-01-30
I have recently bought a Dell Dimension 9150 and installed Breezy on it. For the past year I have been running Ubuntu on a laptop with suspend/resume working, but I can't get it to work on my new desktop computer. In Windows I have no problems.

What happens when I try either "Suspend the computer" (added by editing /etc/default/acpi-support) or "Hibernate the computer" from the logout dialog is the screen goes blank, for suspend it then flickers for a little while and I get the screensaver password dialog.

Anyone who has suspend and/or hibernate working on their DESKTOP computer, please share any experiences!

---

### Post by RAOF on 2006-01-30
Not terribly helpful, but I've been able to successfully suspend & resume my desktop athlon64.  I didn't even have to configure anything, it was out of the box.  That was with Dapper, though ;)  So maybe you only need to wait for April & the release of Dapper.

---

### Post by malmjako on 2006-01-30
Sounds promising, RAOF. Do you know what has been changed in Dapper related to this problem? (Maybe one can backport in some way...)

---

### Post by RAOF on 2006-01-30
[QUOTE=malmjako]Sounds promising, RAOF. Do you know what has been changed in Dapper related to this problem? (Maybe one can backport in some way...)[/QUOTE]
I have absolutely no idea, sorry ;)

---

### Post by mtron on 2006-01-30
good to hear, i thought i am too stupid, tried serveral times andgot sick of it, so i just don't switch it off, but logout...

But good to hear it works in drapper

---

### Post by madmetal on 2006-02-03
if dapper supports suspend to ram that will be great!
the one of my two problems left in ubuntu..

when dapper is out should i make a new install or just upgrade?

---

### Post by nrwilk on 2006-02-03
oh god, I hope Dapper fixes this.

I'm looking forward to that!

---

### Post by missmoondog on 2006-03-14
[QUOTE=madmetal]if dapper supports suspend to ram that will be great!
the one of my two problems left in ubuntu..

when dapper is out should i make a new install or just upgrade?[/QUOTE]

it's about my only issue now that i have my old nvidia vanta video card figured out.

the choice is yours for making a new install or upgrading. myself, i'm doing the full new install. didn't care to much for upgrade from hoary to breezy process.

---

### Post by JurB on 2006-04-09
Try these commands and see what they do for you:

sudo pmi action hibernate
sudo pmi action suspend

---

### Post by missmoondog on 2006-04-09
what do you mean "try" those commands? do they work or not and how would i cancel the command if it does work?

thanks

---

### Post by kaffeine on 2006-04-11
you can open /etc/default/acpi-support with your favorite editor and uncomment the second line to enable suspend to RAM option on the logout menu.

however, this 'suspend' on my desktop, only turns off the monitor and locks the screen - it does not shut off the drives and CPU (which is what windows Standby does).  users who have reported success with suspend to RAM on Dapper - could you please confirm that you get the same effect as windows standby  or is it just a monitor power saving mode?

btw jurB, this is the same as ```
sudo pmi action suspend
```

---

### Post by missmoondog on 2006-04-11
yeah, that's the ONE thing i dislike about ubuntu!

edit:
same thing for me.
"however, this 'suspend' on my desktop, only turns off the monitor and locks the screen"

---

