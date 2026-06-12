---
title: "gnome-panel crashes on startup"
date: 2006-12-10
forum: Desktop Environments
---

### Post by 1002285 on 2006-12-10
I ran into this problem using LinuxMint today. Suddenly I started getting error reports and it always said sth like "problem is back-traced to /us/bin/gnome-panel".
It started during normal work and then came ack every time I restarted.
I tried recovery modes and everything and tried installing LinuxMint again, but the CD was broken and then I installed Ubuntu Edgy again (I have been using Edgy for months and only for about a week I had been using LinuxMint, which was better for some reasons).
But to my very unpleasant surprise I got the very same error messages after the boot of this freshly-installed Edgy, and it crashed the same way, i.e there are no more panels and menus anymore, so nothing can be done.
What is this, does anybody know?

I am just adding now that this problem does not go away. I have now made a fresh install of LinuxMint. Gnome-panel crashes and nothing can be done in gnome. I was able to install kubuntu-desktop, so the computer is at least usable now, but I don't like KDE particularly.
I did uninstall gnome-panel and then the entire ubuntu-desktop and installed ubuntu-desktop again, but the same crash occurred. I have had my /home partition in place all this time. Can the problem be there? What should I look for?

---

### Post by KJS on 2007-01-07
**solution**
delete the 
*recently-used.xbel *
file found in your home directory

---

### Post by 1002285 on 2007-01-08
> **KJS said:**
> **solution**
delete the 
*recently-used.xbel *
file found in your home directory

I'm glad you found the solution. I didn't. I just used KDE for a while and when I tried Gnome again in a couple of weeks it just "magically" worked.
But I did come to the understanding that the problem was in my home directory, because gnome-panel continued crashing even after a format of the OS partition and fresh install of Ubuntu. (It didn't make any sense to me, of course).
So what's the recently-used.xbel for? I tried to see it now, but couldn't understand.

---

### Post by serlex on 2007-01-08
cant find recently-used.xbel

---

### Post by mts-fi on 2007-01-09
Thank's a lot!!
I've been four days without panels... and now I got them back!
Cause of the problem is still unsolved.
read: [http://bugzilla.gnome.org/show_bug.cgi?id=358044](http://bugzilla.gnome.org/show_bug.cgi?id=358044)

---

### Post by mts-fi on 2007-01-09
> **serlex said:**
> cant find recently-used.xbel

It's hidden file! (.recently-used.xbel)
Goto your home directory and press Ctrl+h

---

### Post by serlex on 2007-01-10
thank you mts-fi

---

### Post by ugho75 on 2007-04-02
> **KJS said:**
> **solution**
delete the 
*recently-used.xbel *
file found in your home directory

:) I had the same problem with gnome-panel and bug-buddy. After many attempts to kill the looping processes I found this solution. Great! Thanks. You made me save a lot of time.

---

### Post by TallMatthew on 2007-06-20
I get this error anytime I try to extract files from an ISO image using "Extract Here."

For some reason, the URI for the file gets munged into cryptic hex.  Not that your recent documents are that important, but if you look at the final entry in your .recently-used.xbel, you'll see that the entry for the ISO file looks really odd.  Removing (or correcting) that URI will fix the problem, just as blowing the file away will.

---

