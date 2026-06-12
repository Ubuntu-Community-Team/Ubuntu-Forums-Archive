---
title: "Samba SWAT"
date: 2006-04-17
forum: Desktop Environments
---

### Post by Geffers on 2006-04-17
Samba is shown as installed but does not show up on any of the application short cuts; I assume it has to be run from the command line but variations of samba, samba server etc are unsuccessful.

I try to access SWAT via [http://127.0.0.1:901](http://127.0.0.1:901) and that gives me an error message.

Samba is shown on my services utility as running.

How do I get access to the configuration set up...

Geffers

---

### Post by Ramses de Norre on 2006-04-17
Samba is kind of a protocol, as http and ftp. So it isn't a program you can run, you use it for browsing network folders by typing smb://ip-adress/share-name
in a file browser.
You can configure it in /etc/samba/smb.conf (shouldn't be necessary to browse other computers, but you'll need to set some things to make it possible for others to browse your pc).

---

### Post by Intangir on 2006-04-17
as far as i can tell swat is broken

it crashes every time its run, im using dapper drake, i dont know if its broken on your version, but the dapper version doesnt work, just crashes

also when it installs if you dont have inetd it just makes an inetd file anyway, and completely ignores xinetd

but even if you set it up for xinetd, or install inetd for it it .. still doesnt work, the swat binary crashes

---

### Post by Geffers on 2006-04-21
[QUOTE=Intangir]as far as i can tell swat is broken

it crashes every time its run, im using dapper drake, i dont know if its broken on your version, but the dapper version doesnt work, just crashes

[/QUOTE]

That's strange, I'm sure I used to use it a couple of years back via Mandrake.

Geffers

---

### Post by sadjack on 2006-04-21
I used SWAT recently on Breezy and it worked fine. I had to download it seperately though as it was not installed with samba.

---

### Post by Geffers on 2006-04-21
[QUOTE=sadjack]I used SWAT recently on Breezy and it worked fine. I had to download it seperately though as it was not installed with samba.[/QUOTE]

That's interesting, I'll have another look at my installation, I thought SWAT was installed as part of samba but maybe I am mistaken.

Thanks for info.

Geffers

---

