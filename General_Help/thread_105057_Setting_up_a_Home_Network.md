---
title: "Setting up a Home Network"
date: 2005-12-17
forum: General Help
---

### Post by DJiNN on 2005-12-17
Anyone know what's the easiest way to setup a Home Network in Ubuntu 5.10? I'm using a Netgear DG834G WiFi Router & would like to be able to share with some XP computers (Soon to be changed into Linux) indoors. I read somewhere that it's something to do with Samba but can't see any way of getting one set up, plus i'm not that good at the whole Network thing .... YET. :)

Any advice, help or links where to read info etc would be much appreciated.

Many thanks......

DJiNN

---

### Post by yanik on 2005-12-17
sudo shares-admin

and you'll be good to go, it'll ask you to install either NFS or SAMBA, select samba.  After that you'll be able to create shared folders and manage your samba config.

---

### Post by brickbat on 2005-12-17
Hamachi is out.  It is zeroconfig secure networking

---

### Post by DJiNN on 2005-12-17
[QUOTE=brickbat]Hamachi is out.  It is zeroconfig secure networking[/QUOTE]

I've used Hamachi a lot in XP & love it, but this is where i completely fall down with Linux, because it's not a simple click to install. Unfortunately it's far too complicated for me at this moment in time. :) So it looks like i'll have to switch back to XP to do any networking stuff, which is a shame but there you go. This is where the learning curve starts i guess.... :)

Thanks for the info though, much appreciated.

DJiNN

---

### Post by DJiNN on 2005-12-17
[QUOTE=yanik]sudo shares-admin

and you'll be good to go, it'll ask you to install either NFS or SAMBA, select samba.  After that you'll be able to create shared folders and manage your samba config.[/QUOTE]

Thanks for that. I've installed Samba but where i go from there is a mystery. :)  I think i'll finally have to learn about Networking properly rather than rely on Simple File Sharing etc. :)

Appreciate the info & the help though.

DJiNN

---

### Post by Zimmer on 2005-12-17
[QUOTE=DJiNN]Anyone know what's the easiest way to setup a Home Network in Ubuntu 5.10? I'm using a Netgear DG834G WiFi Router & would like to be able to share with some XP computers 

Any advice, help or links where to read info etc would be much appreciated.

Many thanks......

DJiNN[/QUOTE]

Links..
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server) 
[http://ubuntuguide.squarecows.com/doku.php#samba_server](http://ubuntuguide.squarecows.com/doku.php#samba_server)

[http://ubuntuguide.org/](http://ubuntuguide.org/)

and when you get really good at deciphering techno babble.
[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

If you need any clarification, do not hesitate to ask...(and someone will try to help   :)  )

Regards
Zimmer

---

### Post by DJiNN on 2005-12-17
[QUOTE=Zimmer]Links..
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-server) 
[http://ubuntuguide.squarecows.com/doku.php#samba_server](http://ubuntuguide.squarecows.com/doku.php#samba_server)

[http://ubuntuguide.org/](http://ubuntuguide.org/)

and when you get really good at deciphering techno babble.
[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

If you need any clarification, do not hesitate to ask...(and someone will try to help   :)  )

Regards
Zimmer[/QUOTE]

Zimmer, thank you ever so much for the links.... i shall bookmark them now & start reading. This will make all the difference.

DJiNN

---

