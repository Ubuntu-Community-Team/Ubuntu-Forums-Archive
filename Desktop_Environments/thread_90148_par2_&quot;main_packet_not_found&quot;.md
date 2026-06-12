---
title: "par2 &quot;main packet not found&quot;"
date: 2005-11-14
forum: Desktop Environments
---

### Post by mspruell on 2005-11-14
Howdy y'all, I just upgraded my hoary to breezy and found that par2 doesnt work anymore.  I asked Uncle Google about it, and it seems to affect powerpc linux users.  I tried it on my hp dv1000 and the par2 worked.  So, on to the fix!

Par2 has not been updated in over a year, so you breezy users who have this problem can use the hoary par2 package.  It works fine.  first thing to do is visit [http://packages.ubuntu.com/hoary/utils/par2]("http://packages.ubuntu.com/hoary/utils/par2")
 and grab the deb for your architexture.  For powerpc, that would be par2_0.4-2_powerpc.deb.  

While you wait for the download, open a console or your gui package manager and remove the existing par2. In console it goes like this: "sudo apt-get remove par2"

Now we will pin our version of par2 we want, otherwise as  soon as you install the hoary version into your breezy, apt-get will want to upgrade back to the broken one. [https://wiki.ubuntu.com/PinningHowto]("https://wiki.ubuntu.com/PinningHowto")
 comes in handy for times like this.

Open a terminal and type "sudo gedit /etc/apt/preferences" (ubuntu) or "kdesu kate /etc/apt/preferences (kubuntu).
In your text editor, put this below any existing entries:
> 
Package: par2
Pin: version 0.4-2*
Pin-Priority: 999

Now save the file.

The /etc/apt/preferences file tells apt that you want that particular file and not to bother you with "upgrade available". 

now in your terminal, assuming you downloaded the par2 deb to your home directory, type "sudo dpkg -i ~/par2_0.4-2_powerpc.deb"

You should now have a working par2 implementation.

---

### Post by Mustard on 2005-11-14
Ah cool, thats handy to know. :)

---

