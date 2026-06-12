---
title: "Synaptic won't load"
date: 2006-01-23
forum: Desktop Environments
---

### Post by El Kabong on 2006-01-23
Hey everyone, I need some guidance...
 I just installed my first ever incarnation of linux (woohoo!), Ubuntu Breezy Badger. The install seemed to go great, and I'm loving the OS so far (except for one thing). When I'm logged in, and I go to System-->Administration, absolutely nothing will load when I click on it. I need for Synaptic to load so I can install some packages, including the one to get my dhcp up and running. Have yall ever run into this before? I really don't want to re-install it, but I'm willing if I have to (since I formatted my whole drive and it's completely clean anyway). When I tried to login as root at the login page it said the system administrator isn't allowed to login from this screen. Any help would be greatly appreciated, and thank you a lot ahead of time!

---

### Post by El Kabong on 2006-01-23
I also just remembered that during the installation, I activated an option regarding using a password with GNOME... I'm not sure if that would have anything to do with it, but when I just typed "sudo apt-get install build-essential", it asked me for a password, which I typed. It went back to the regular prompt, not doing anything related to the command that I put in. Not sure if this is related, but it seems to be similar. Thanks again!

---

### Post by RAOF on 2006-01-23
Well, the "can't login as root" thing is normal.  Ubuntu doesn't use a root account by default - whenever you would need to be root, use "sudo <command>" (at a terminal), or "gksudo <command>" (for a gui prompter).  It will ask for a password, this is the password of the user that you're in (**not** root).  That gives <command> temporary root privileges, and maintains a log of everything you do with sudo.  So it can be easier to fix stuff if it messes up, or at least work out what went wrong ;)

Everything from "System->Administration" should fade the screen & pop up a dialog in the middle saying "Enter password to run <whatever>".  If this isn't working, try running opening up a terminal, (Programs->Accessories->Terminal) & running (for example) "sudo synaptic".  That should ask for your password, & then run synaptic.  Try that first.

---

### Post by RAOF on 2006-01-23
[QUOTE=El Kabong]I also just remembered that during the installation, I activated an option regarding using a password with GNOME... I'm not sure if that would have anything to do with it, but when I just typed "sudo apt-get install build-essential", it asked me for a password, which I typed. It went back to the regular prompt, not doing anything related to the command that I put in. Not sure if this is related, but it seems to be similar. Thanks again![/QUOTE]
I don't suppose it gave you any error messages, did it?  They'd really help.  Also, could you run the command "groups" at a terminal?  It'll print out all of the groups that your user is a member of - it should include "admin".

---

### Post by El Kabong on 2006-01-23
Wow man, thanks a lot for the quick reply. I just tried running "sudo synaptic", and it asked for a password directly below it. I typed my password, but as I was typing, it didn't show any dots or "*" to be encrypted (I think I made it this way during installation). Once I'm done I hit enter, and it goes directly back to "mchaney2@matt:~$"

It does this every time, and I can't seem to get anything to load that requires a password.

---

### Post by El Kabong on 2006-01-23
okay, I did the "groups" command, and it gave me:

"mchaney2 adm dialout cdrom floppy audio dip video plugdev lpadmin scanner"

was I supposed to write "sudo groups" or just "groups?

thanks again for your help!

---

### Post by El Kabong on 2006-01-23
And no, no error messages

---

### Post by RAOF on 2006-01-23
[QUOTE=El Kabong]okay, I did the "groups" command, and it gave me:

"mchaney2 adm dialout cdrom floppy audio dip video plugdev lpadmin scanner"

was I supposed to write "sudo groups" or just "groups?

thanks again for your help![/QUOTE]
Just "groups".  Aha!  It seems you are not on the "admin" group.  Did you do an "expert" or "server" install?  I seem to recall that there was a problem with those, that they didn't add the user to the admin group.  Only users in the admin group can use sudo.

Anyway, boot in to recovery mode (at the grub prompt, you want "Ubuntu <somestuff> (Recovery mode)").  That will drop you to a command-prompt with root access.  From there you can run "adduser <yourusername> admin" to add your user to the admin group.  Then type "exit", and Ubuntu should continue loading normally.  That **should** fix it :)

---

### Post by El Kabong on 2006-01-23
I hate to be a noob, but where exactly is the grub prompt? I'm sure as hell glad you replied when you did, I was fixing to reinstall the whole system! But hey man thanks a lot for your help!

---

### Post by RAOF on 2006-01-23
[QUOTE=El Kabong]I hate to be a noob, but where exactly is the grub prompt? I'm sure as hell glad you replied when you did, I was fixing to reinstall the whole system! But hey man thanks a lot for your help![/QUOTE]
That's OK :)

What I mean when I say "grub prompt" is the list of things to boot just after you turn on/restart your computer.  There should be a list of things like
```
...
Ubuntu, kernel 2.6.12-10-amd64-k8
Ubuntu, kernel 2.6.12-10-amd64-k8 (recovery mode)
...
```although with different numbers after the "kernel" bit.  You want to select one marked (recovery mode).

---

### Post by El Kabong on 2006-01-23
when I turn it on, it boots into ubuntu automatically, it doesn't give me a choice or anything. do I have to hit a certain key at a certain time?

---

### Post by Madpilot on 2006-01-23
Early in boot, it should say "Starting Grub..." - if you hit the Escape key right then, it'll go into the Grub menu rather than continuing automatically to boot Ubuntu.

You've only got about 2 seconds to hit ESC, though.

---

### Post by RAOF on 2006-01-23
[QUOTE=El Kabong]when I turn it on, it boots into ubuntu automatically, it doesn't give me a choice or anything. do I have to hit a certain key at a certain time?[/QUOTE]
Aaaah, oh.  Hmm.  Let's see.

It looks like pressing "Esc" will make the menu visible.  Just hit it over, and over again as the computer boots (but after the bios stuff (otherwise the bios might think you have a stuck esc key and complain) - I can't tell you exactly what that looks like, but perhaps "after the screen blanks for the first time" will do).

---

### Post by El Kabong on 2006-01-23
wait, haha! I got it, I just had to press "esc" at a certain time... ok I'm trying it now...


okay, at the "root@<username>:~$", I typed "adduser mchaney2 admin" and it gave me this: "bash: the group 'admin' does not exist"

do I have to make it manually?

---

### Post by El Kabong on 2006-01-23
yeah, sorry about that... I just thought it automatically went into it, but turns out I just wan't paying attention!

---

### Post by El Kabong on 2006-01-23
*bump*

sorry, gotta keep it current!

---

### Post by RAOF on 2006-01-24
[QUOTE=El Kabong]wait, haha! I got it, I just had to press "esc" at a certain time... ok I'm trying it now...


okay, at the "root@<username>:~$", I typed "adduser mchaney2 admin" and it gave me this: "bash: the group 'admin' does not exist"

do I have to make it manually?[/QUOTE]
The admin group doesn't exist?  Awkward.  You could try "adduser --group admin", and then adding yourself to the admin group, but I'm not sure if that will work.  Try it?

---

### Post by El Kabong on 2006-01-24
okay, I just did exactly what you said:

"adduser --group admin" and it said done.

Then, I put "adduser <username> admin"
and it said done. I'm now going to go test it out in the system... thanks for all your help man!

---

### Post by El Kabong on 2006-01-24
dammit, it does the same thing! When I try to go System-->Administration-->Synaptic, it does the same as it did before (asks for a password, and then doesn't do anything after I enter it).

I tried "sudo synaptic" in the terminal, and it did the same as before as well.

---

### Post by RAOF on 2006-01-24
Ok, finally, boot back into recovery mode.  Run "visudo", which will allow you to edit your the file sudo looks at to work out who can run it, and replace it with this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

```
If **that** doesn't work, then... we'll try something else :(

---

### Post by El Kabong on 2006-01-24
once I make the changes, do I just hit ctrl+c to save and exit?

---

### Post by El Kabong on 2006-01-24
RAOF, you are a genious. It's working so far (Synaptic loaded up on the first try), and I'm about to try it out the other ways just to make sure. Thanks a lot for staying on here and helping me like that!

---

### Post by RAOF on 2006-01-24
Wooho!  He scores!

---

### Post by El Kabong on 2006-01-24
lol it works like a charm! Thanks again man... now I just gotta try to figure out how to setup my wireless card... sigh

---

