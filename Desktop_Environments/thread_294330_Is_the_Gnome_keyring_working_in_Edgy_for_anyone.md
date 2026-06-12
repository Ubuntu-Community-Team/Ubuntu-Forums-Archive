---
title: "Is the Gnome keyring working in Edgy for anyone?"
date: 2006-11-06
forum: Desktop Environments
---

### Post by wpwood3 on 2006-11-06
I'm trying to find out if only a few people have this problem or lots of us...

Everything worked fine in Dapper. 
I did a clean install of Edgy and cannot get the Gnome keyring to work at all. It doesn't seem to save any passwords. I first noticed this after installing Samba and trying to connect from my Ubuntu box to a share on my Windows XP box. I can connect but I have to re-enter my username & password each time.

If I go to Places > Network Servers I see my Windows shares displayed in Nautilus. If I doubleclick on one of them I get the Authorization Required box. It makes no difference if I check the boxes to remember the password for this session or save in keyring. My password is not remembered either way.

The problem appears to be the same as described in [THIS BUG]("https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/67189").

When I go to System > Administration > Keyring Manager and I view keyrings (F9) there is nothing there but the session keyring and nothing under the Key or Applications tabs.

I have tried reinstalling gnome-keyring and gnome-keyring-manager but it made no difference. At this point I am not certain if the problem is caused by the Gnome keyring, Nautilus or Samba.

Any feedback appreciated!

---

### Post by davescafe on 2006-11-07
I am also having problems with the keyring storing passwords for Samba shares. It doesn't seem to remember the passwords at all, even though I click the box to "remember this password in keyring" when I am authenticating. 

Dave

---

### Post by tenjin on 2006-11-11
Hi,

It doesn't work for me either.

Any ideas anyone?

Cheers

D.

---

### Post by tenjin on 2006-11-15
* bump *

---

### Post by wpwood3 on 2006-11-15
There is currently no fix for the Samba keyring problem in Edgy.

There is a Gnome bug report [HERE]("http://bugzilla.gnome.org/show_bug.cgi?id=370951").

There is an Ubuntu bug report [HERE]("https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/67189").

---

### Post by ryan on 2006-12-03
I had the same problem with a clean install on my desktop but on my laptop where I upgraded to Edgy everything works fine, does anyone know is there a .conf file for gnome keyring that I could possibly copy to desktop and it might work.

---

### Post by Shay Stephens on 2006-12-03
The keyring didn't work well for me in dapper, but it now works fine in edgy.

---

### Post by jasonxh on 2006-12-03
It's working fine as far as I'm using it up to now, which is in fact only for wireless authentication.

---

### Post by ryan on 2006-12-03
I found something that I hope works long term i copied my "default.keyring" from my laptop (Dapper>Edgy upgrade..) which worked fine to my Desktop and the PW's for the network are working.

---

### Post by munwin on 2007-02-14
@ryan.
Confirmed. Just copied my old default.keyring file, and it's OK now.
Thanks.

---

### Post by johnd126 on 2007-03-19
Is there a solution for this?  I don't seem to ever have any entries in keyring manager and have to enter samba passwords on every session.

John

---

