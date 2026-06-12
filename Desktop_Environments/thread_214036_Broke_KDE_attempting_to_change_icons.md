---
title: "Broke KDE attempting to change icons"
date: 2006-07-12
forum: Desktop Environments
---

### Post by meatbop on 2006-07-12
I decided to play around with the appearance of KDE last night.  I entered system settings then appearance and tried to change the icons my system is using.  When I selected a different icon set and clicked apply however there was no change to the desktop icons, though the screen did flicker.  I tried selecting a few different icon sets with the same lack of results.  Concerned I might have screwed up somehow I clicked the "defaults" button and my desktop icons disappeared!

I gave the machine a reboot but still no icons and when I tried to launch Konqueror only the outline of the window appeared and it was elongated vertically off the screen.  The machine was also thrashing the hard drive in a big way and did not respond to Ctrl + Alt + Backspace. Repeated attempts always gave the same result.

The system seems fine under Gnome, any ideas?  Would removing and reinstalling kde-desktop be likely to fix the problem?

---

### Post by editrix on 2006-07-12
First off, create a new user and log in as that user. If all is okay, then you can copy configurations to the new user's /home directory and become someone else :-)

If that doesn't work, then your problem goes a lot deeper and, sorry, I haven't a clue.

---

### Post by meatbop on 2006-07-12
Thanks, I'll give that a try when I get home tonight.  If that doesn't work I'll try reinstalling KDE, if no joy from that then I guess it's format and reinstall time.

To copy configurations I just copy everything in the old home directory to the new one right?  Are there any hidden files or anything like that to look out for?

---

### Post by editrix on 2006-07-12
> **meatbop said:**
> To copy configurations I just copy everything in the old home directory to the new one right?  Are there any hidden files or anything like that to look out for?

No! Do NOT copy *everything* because one of those configurations broke your KDE.

All KDE's files are in /home/<username>/.kde (i.e., a hidden directory). Don't be afraid to poke around in there, they're almost all text files anyway.

Copy your personal files, and of course email and stuff (although I had some issues with copying email from one computer to another--no idea if the same problem would exist one user to another. You won't break anything trying, I don't think.)

If you've got some program configured up the ying yang and want to save those configurations, I'd suggest you rename the "original" <new username> file for it (add BACKUP or ORIGINAL to it) before copying the <old username> into the new directory. It will also be in a hidden directory. Just in case, belt and suspenders.

I did what you did years ago (I suspect almost everyone does it once) and I honestly can't recall how I fixed it, but I know I didn't reinstall.

Good luck with it!

---

### Post by aysiu on 2006-07-12
No need to create a new user. ```
mv ~/.kde ~/.kde.old
``` Log out. Log back in again.

---

### Post by meatbop on 2006-07-13
Yay! Editrix's new user idea got me back into KDE.  Thanks for that.

> **editrix said:**
> No! Do NOT copy *everything* because one of those configurations broke your KDE.

Heh, yeah I assumed that would be the case, I turned on show hidden files and had a poke around in the various folders.  I've only been using Kubuntu for a couple of weeks so my install isn't super tweaked, I just grabbed the handfull of files I had in there and brought them over. 

I'll give your mv ~/.kde ~/.kde.old method a try on the old account too aysiu.  I take it when KDE can't find it's configuration settings on startup it creates a new default set?

Thanks again for the help folks.

---

### Post by editrix on 2006-07-13
> **meatbop said:**
> Yay! Editrix's new user idea got me back into KDE.  Thanks for that.

You're welcome. First time I feel I've helped someone, so it makes me feel good.

> **meatbop said:**
> I'll give your mv ~/.kde ~/.kde.old method a try on the old account too aysiu.

aysiu's method is certainly quicker. I find it handy to have a second user, Test (or some such) for trying out stuff I'm not sure of.

---

### Post by meatbop on 2006-07-14
The mv ~/.kde ~/.kde.old method worked, though I renamed the folder using konqueror launched with the kdesu command from the new account I had created rather than from the terminal.

KDE did indeed create a new set of default configuration files, a useful trick to know, cheers.

---

### Post by utnubu001 on 2006-07-14
lol that exact thing happend to me with mandrake 10.2

---

