---
title: "I want to make the move from WinXp but..."
date: 2006-01-04
forum: General Help
---

### Post by kevin79 on 2006-01-04
I want to make the move from WinXp but I have a few questions/issues. I want to make the switch on my laptop (Dell Latitude D600) from Windows XP to Ubuntu. I use my laptop at work in a Windows 2000 AD domain (with all Windows 2000/2003 servers) and at home. I currently synchronize my "My Documents" folder with a server at work. I also synchronize some important documents that are stored on a different server. Is there any way to do this in Ubuntu? I would like to synchronize my home directory with our file server so that my documents are backed up and synchronize a few other folders so that I can work on stuff at home. I've looked at iFolder but it looks like a component needs to be installed on the servers, which I can't do.

My other question is about networking. My laptop has a wired NIC and a wireless NIC. At work, I want to use my wired NIC instead of wireless if I'm at my desk and use wireless when I'm roaming and at home. Is there a way to have Ubuntu automatically turn off the wireless NIC when there is a wired connection and turn the wireless on when wired isn't available?

Hopefully I'll get around these two issues and will be able to make the jump.

Thanks!

---

### Post by carlosqueso on 2006-01-04
I don't know about the first, but the network-manager package is supposed to do exactly what you want to do in the first question.  Once you get ubuntu working, just ```
sudo apt-get install network-manager
``` and it should work.  Good luck.

---

### Post by Rud on 2006-01-04
[QUOTE=kevin79] I currently synchronize my "My Documents" folder with a server at work. I also synchronize some important documents that are stored on a different server. Is there any way to do this in Ubuntu? I would like to synchronize my home directory with our file server so that my documents are backed up and synchronize a few other folders so that I can work on stuff at home. I've looked at iFolder but it looks like a component needs to be installed on the servers, which I can't do.
[/QUOTE]

Are these just network shares? If so, look into Samba. It can't defintely be done with Samba and some scripting, it just depends how much effort you want to put into it.

---

### Post by kevin79 on 2006-01-04
[QUOTE=Rud]Are these just network shares? If so, look into Samba. It can't defintely be done with Samba and some scripting, it just depends how much effort you want to put into it.[/QUOTE]

Yes, these are Windows network shares.  Are there any good tutorials on setting up Samba? The last time I tried Linux and Samba (a couple years ago) Samba was very difficult to set up and get working.

---

### Post by Tal on 2006-01-04
[QUOTE=kevin79]Yes, these are Windows network shares.  Are there any good tutorials on setting up Samba? The last time I tried Linux and Samba (a couple years ago) Samba was very difficult to set up and get working.[/QUOTE]

Connecting to a samba share is easy with Ubuntu. Go under the places menu at the top of the screen... "Connect to Server".  Just put in the connection info and BAM. an icon appears on your desktop. As far as synchronizing the files. I'd check sourceforge or freshmeat and just search for synch files or something similar. I'm sure there's an easy package to help with this.

---

