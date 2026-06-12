---
title: "Cant Share Internet Between Users"
date: 2006-07-31
forum: Desktop Environments
---

### Post by magnoliablossom on 2006-07-31
The only way the internet works for the other users is if I connect under my name then log out and let one of them log on.  Although this is alright for the short-term, it will pose a problem eventually.  I prefer to *not* give my 13 and 14 year olds my password to sign in under my name.  They may decide to play with things.  How can I set this up so that they have access to this as well?

---

### Post by Paerez on 2006-07-31
There should be something like "System->Administration->Users". Look up yourself in the list and see what groups you belong to. Hopfully one of them is called "net" or "internet" or "wifi" or something. Then, go to your kids' user name and give them membership to that group.

---

### Post by magnoliablossom on 2006-07-31
the only thing that remotely resembles that is www-data and according to the list thing i don't belong to any groups.

---

### Post by Paerez on 2006-07-31
hmm it may be part of the "able to run admin commands" group, which you wouldn't want to give your kids access to. In that case, this involves creating a new group and giving members of that group access to the programs used to manage wireless (like iwconfig and ifconfig and nm-applet if you use network-manager). But I don't know how to do that sorry. Try searching for it.

---

### Post by FenrisAbraxas on 2006-07-31
> **magnoliablossom said:**
> The only way the internet works for the other users is if I connect under my name then log out and let one of them log on.  Although this is alright for the short-term, it will pose a problem eventually.  I prefer to *not* give my 13 and 14 year olds my password to sign in under my name.  They may decide to play with things.  How can I set this up so that they have access to this as well?

How do you connect to the internet? DHCP with a router? your pc is working as a server? is a single computer? 

Can you be a little more detailed about the way it hooks up to the net, ethernet, usb modem, serial modem :P

It  probably have to be a problem with groups or permissions

---

### Post by magnoliablossom on 2006-07-31
> **FenrisAbraxas said:**
> How do you connect to the internet? DHCP with a router? your pc is working as a server? is a single computer? 

Can you be a little more detailed about the way it hooks up to the net, ethernet, usb modem, serial modem :P

It  probably have to be a problem with groups or permissions

I connect via serial modem...lucent winmodem....it's a single computer with 4 accounts set up...myself, my husband, and my two oldest children....but i fixed it...i just gave everyone admin access because frankly i'm sick of having to try to figure every thing out.

I went to the help documentation and did a search for "groups"....It did nothing to explain what groups are, how they work, or what they do.  All it says is how to add/delete users and how to add/delete groups.  It's in entirely inadequate as a type of "help" documentation. 

I hope to God I don't have to come back to this or any other forum for help about internet and modems.  I'm not upset with you and I'm very sorry if I sound like I am...I'm just frustrated with the entire thing.

---

### Post by FenrisAbraxas on 2006-08-04
> **magnoliablossom said:**
> I connect via serial modem...lucent winmodem....it's a single computer with 4 accounts set up...myself, my husband, and my two oldest children....but i fixed it...i just gave everyone admin access because frankly i'm sick of having to try to figure every thing out.

I went to the help documentation and did a search for "groups"....It did nothing to explain what groups are, how they work, or what they do.  All it says is how to add/delete users and how to add/delete groups.  It's in entirely inadequate as a type of "help" documentation. 

I hope to God I don't have to come back to this or any other forum for help about internet and modems.  I'm not upset with you and I'm very sorry if I sound like I am...I'm just frustrated with the entire thing.

Groups work like memberships, audio group per example, the audio device have persmissions for (just an example :P) user root and everyone which is inside the group "audio".

you can add groups like "topsecret" and make a folder wich can only let read and write to the user with the membership to the topsecret group.

I never used a serial modem to connect to the internet, but let me google for it and i'll try to post what i get, all users in the admin group is a little dangerous.

---

