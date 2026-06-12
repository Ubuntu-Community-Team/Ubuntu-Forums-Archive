---
title: "klik fails - requires rpm2cpio"
date: 2005-12-20
forum: General Help
---

### Post by kambei on 2005-12-20
Hi all... I am having a problem getting Klik to work. It fails with the message:

**Please install rpm2cpio in order to use klik.**

I am using Kubuntu Breezy. Steps taken so far:

I installed klik by hitting 'alt-F2' and running...

wget klik.atekon.de/client/install -O -|sh

...and was prompted to run (as root) the command...

./klik-cmg-install-root

...which I did, and it returned no errors.

Restarted Firefox, went to the klik website, chose an application, clicked on the link, which produced a dialog box stating an external application would have to be launched to handle the request. I clicked on 'Launch Application' and a error box popped up:

**Please install rpm2cpio in order to use klik.**

I checked the package repositories for rpm2cpio and did not find anything, and I searched the forums for klik requiring a rpm2cpio dependency - no luck.

How can I fix this? Thanks in advance for any help.

---

### Post by One Quick Question on 2005-12-20
What klik package was it?

---

### Post by ace2005 on 2005-12-20
i used "sudo wget klik.atekon.de/client/install -O -|sh" after it said run as root and i use konqueror to go to klik's site and get a package

---

### Post by ace2005 on 2005-12-20
Oh wait i also have the "rpm" package in synaptic installed and one of the files it provides is "/usr/lib/rpm/rpm2cpio.sh"

So install "rpm" in Synaptic

---

### Post by imranj on 2005-12-20
Install RPM from apt and it should be fine and yeah use fire fox to install the software, the concept isnt so fancy, i dont like it much tho.

I want one click install in offline mode, what about dial-up users?

---

### Post by One Quick Question on 2005-12-20
[QUOTE=imranj]I want one click install in offline mode, what about dial-up users?[/QUOTE]
Kliking a link downloads the cmg file to your desktop, which you can run whenever offline.

---

### Post by kambei on 2005-12-20
Thanks for the input - as suggested, 'sudo apt-get install rpm' supplied the missing rpm2cpio command. Klik is now working OK (I am using a klik-installed Firefox v1.5 to post this reply).

Again, thanks for the help.

---

### Post by anaconda on 2007-02-08
Thanks.. installing rpm solved my problem too. in ubuntu Dapper 6,06
Strange that they dont know anything about this in the klik-forums..

---

