---
title: "Printer Sharing"
date: 2004-10-18
forum: General Help
---

### Post by bartleby on 2004-10-18
How do I make this work? I have a Canon BJC4300 attached to one of the computers on my home network and I can't get my laptop to "see" it when I'm setting up printing. I'd like this to be an SMB printer if possible, but there doesn't seem to be a way to scan the network to find printers, unless I'm missing something.

Cheers

---

### Post by bartleby on 2004-10-18
OK I've done a little digging and it seems I don't have smbd installed. How can I install it? It doesn't show up in Synaptic even with Universe enabled.

---

### Post by bartleby on 2004-10-18
Right, I've installed Samba and the three machines can now "see" one another, but there is no graphical way in Gnome to set the printer on one machine as a shared printer. Does nobody have any idea how to do this? It's pretty basic I would have thought.

---

### Post by triad169 on 2004-10-18
Unfortunatly Ubuntu doesnt have a GUI for File or Print sharing.  (ie SWAT)  I thinks its in Universal.  But it is pretty easy to setup without a gui.

Just look at:

/etc/samba/smb.conf

File.  Thats your main samba Config file.  They give some good comments on file and print sharing setup in it.  Also look at this post I put up earlier about shring with Samba.  Some good info and links in it:

[http://www.ubuntuforums.org/viewtopic.php?t=933&amp;highlight=](http://www.ubuntuforums.org/viewtopic.php?t=933&amp;highlight=)

Hope this Helps.

Triad

---

### Post by bartleby on 2004-10-19
Thanks Triad, I'll look into it--printer sharing is essential for me.

---

