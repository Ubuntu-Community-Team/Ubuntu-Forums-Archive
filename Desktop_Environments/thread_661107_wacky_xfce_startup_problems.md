---
title: "wacky xfce startup problems"
date: 2008-01-07
forum: Desktop Environments
---

### Post by stairwayoflight on 2008-01-07
Hello,

I have recently installed xubuntu gutsy, and at some point probably clicked "save session on logout" or the like.

I have some weirdness happening like the orage calendar opening in the middle of the desktop on every login. I unchecked "save sessions..." in the logout dialog on one exit. The calendar still opened on subsequent logins.

Now when I login the panel doesn't start. I have a desktop shortcut for it so I can get it going, but its irritating.

Can someone please help me? I want my panel to start on login, and orage NOT to start :-)

Thanks in advance,

Stwy.

---

### Post by kh1116 on 2008-01-07
oh man, im glad im not the only one. i just posted a thread very similiar to you. adding "xfce4-panel" in the "Applications>Settings>Autostarted Apllications will make the panel start automatically, but theres gotta be a better fix. idk ill see what happens

---

### Post by stairwayoflight on 2008-01-09
Hello people,

Just wondering if anyone's come up with anything, I would reinstall but I would at least need to know how to NOT duplicate the problem..

?

---

### Post by sandwormblues on 2008-01-22
I found the same problem on a client's xubuntu box.  the only way i could get the panel back was by unintstalling xfce-panel, deleting the user settings (can't remember which directory it was), then reinstalling it.  but that only worked for one of the 3 "saved sessions" that won't go away.  This was an Edgy installation that's worked relatively smooth for about a year.  upgrading to Gutsy anyway.

For those who don't feel like doing a clean install, try backing up the home/user directory (ESSENTIAL), remove the user account, add the user account again, and copy the files back over.

my client says he didn't know what he did, but he was browsing porn at the time.  possible malicious code?  (though systemwide malware is extremely unlikely, user-level malware is still a possibility that would be imprudent to ignore).

---

### Post by stairwayoflight on 2008-01-24
Well,

I found that it was a little bit of an annoyance. On top of that, the network-manager dialog displayed weird behavior. For the longest time I had 3 interfaces showing:

wireless
wired
modem

the top one stopped showing 'wireless', and began to flash between 'wired' and 'modem' (the other two remained unchanged) and of course I had various connection difficulties. I could still unload the driver, load up the ipwraw driver for my card in monitor mode, reload the ipw3945, use it, etc., but the network manager seemed to bung things up when I started it.

The other weird thing is that I have a 2 core centrino 32bit duo chip, the cpu monitor showed close to  zero 99% of the time, then once in a while it would idle at 50% or so with no apps open.

I decided to give it up and go for something lighter weight, get more used to the command line. But thats another story...

---

