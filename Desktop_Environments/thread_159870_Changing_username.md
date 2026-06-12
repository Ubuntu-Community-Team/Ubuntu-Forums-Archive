---
title: "Changing username"
date: 2006-04-13
forum: Desktop Environments
---

### Post by Rhapsody on 2006-04-13
How do I change my username? I used my real first name in the Kubuntu installation, but I found it was broadcast while I was chatting in Konversation. For various reasons, I'm not happy with this and I'd like to change it to an alias. I've looked at the Users & Groups settings (which seems a bit badly designed as it won't fit on-screen at 1024x768), but even when I enter my password, it still doesn't seem to give me actual administrative access, as I still can't change any settings. What's going on?

---

### Post by taurus on 2006-04-13
There are many ways but one way is to boot into single user mode or recovery mode from GRUB.  You will be root now so be extra careful, okay.  Now change the name from peter to angel, assuming peter is the old and angel is the new username, in /etc/passwd and /etc/group.  Then, you also need to make the changes to /home/peter as well as
```

cd /home
chown -R angel peter
chgrp -R angel peter

```
Reboot and log in as angel now...

---

### Post by Rhapsody on 2006-04-13
So, I go into recovery mode, enter the code you just posted into the Terminal Program, then login with my new name?

---

### Post by taurus on 2006-04-13
That's the plan...  One more thing since I can't check it because I don't have my Ubuntu handy around right now, see if Ubuntu uses shadow password, /etc/shadow, because you also need to change the name in there from peter to angel as well!

---

### Post by Rhapsody on 2006-04-13
Doesn't seem to be working. Once I type in the the chown command, it just says that the new username is an 'Invalid Name'. Is there a limit to the number of characters?

Edit: Scratch that, it's 'invalid user'. What's going on here?

---

### Post by taurus on 2006-04-13
After you modified both /etc/passwd & /etc/group (and perhaps /etc/shadow)!!!

---

### Post by Rhapsody on 2006-04-13
Well how do I do that then? You're talking to quite a beginner who's very unaccustomed to using command-line interfaces (I've spent more than ten years of computer usage trying to avoid them).

---

### Post by taurus on 2006-04-13
Sorry, my bad...  :mrgreen: 

From a terminal, type
```

nano /etc/group
(scroll down to the end and change the name...)
nano /etc/passwd
(scroll down to the end and change the name...)

```
Then, do the chown and chgrp thing and see if it lets you change owner and group now...

---

### Post by Rhapsody on 2006-04-13
Wow, I took a look at /etc/group, and there seem to be an awful lot of references to my current username, which I assume will all need changing. Should I be looking at /etc/shadow as well? Also, just how fubared can I actually make my system if I screw this up (just to see if I should get some sleep before continuing).

---

### Post by taurus on 2006-04-13
Sorry mate but you need to replace all the old login name with the new login name in /etc/group.  There is no easy way there...  Of course, ALWAYS back up both files, /etc/group & /etc/passwd, just in case and if your system uses the shadow password, you need to look at that too.
```

sudo cp /etc/group /etc/group.bak
sudo cp /etc/passwd /etc/passwd.bak

```

---

### Post by Rhapsody on 2006-04-14
Alright, the backup thingy didn't want to work, so words that may now haunt me for the rest of my life emerged from my mouth "Sod it, I'll just be careful".

Predictably, Kubuntu is now broken. Logging in with the new usernane gives a load of errors about not being able to start KDE and then dumps me back at the login screen, and the old one doesn't work at all (at least we have some progress).

So now I have no backups and can't get into Kubuntu outside of recovery mode. I'm either going to have to figure out what went wrong or set a new record for reformatting and reinstalling.

What I did:

Used "cd /home".

Tried "sudo cp /etc/group /etc/group.bak", didn't work, now infamous phrase emerges.

Used "nano /etc/group", found several references to my username, changed them all.

Used "nano /etc/passwd", found some more references to my username, changed them all.

Used "nano /etc/shadow", found one reference to my username, changed it.

Used "chown -R angel peter" (with my usernames in place), worked.

Used "chgrp -R angel peter" (with my usernames in place), worked.

Rebooted into Kubuntu, found I now had problems.

I'd prefer to find a way to make this work, but a reinstall probably wouldn't be too bad right now. I've barely done anything with Kubuntu by this point, and I have a seperate /home partition with my files it. But I don't want that to become my solution to everything.

---

### Post by Rhapsody on 2006-04-14
Update. Catastophe not really averted, I had to reformat and reinstall Kubuntu, but I'm back to where I left off, and I have my new username. Not quite how I expected it, but I got what I wanted antway.

---

### Post by fdoving on 2006-04-15
Why not just do:
```

sudo usermod -l newusername oldusername

```

finished :)

---

