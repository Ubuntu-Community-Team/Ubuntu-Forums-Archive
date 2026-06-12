---
title: "Ubuntu  Security : Is this true ?"
date: 2014-03-01
forum: Forum Members Chat
---

### Post by raja.genupula on 2014-03-01
Guys this is from a Linux Magazine in India. Is it true ? if it is so can we fix this ?

---

### Post by Elfy on 2014-03-01
read it elsewhere - pretty sure I read it on a ubuntu mailing list in fact

not bothered enough to go looking though

---

### Post by Elfy on 2014-03-01
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-December/014804.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2013-December/014804.html)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1060907](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1060907)

[http://news.softpedia.com/news/All-Linux-Distributions-Store-Wi-Fi-Passwords-in-Plain-Text-If-You-Don-t-Use-Encryption-412387.shtml](http://news.softpedia.com/news/All-Linux-Distributions-Store-Wi-Fi-Passwords-in-Plain-Text-If-You-Don-t-Use-Encryption-412387.shtml) - quote from this one > Well, guess what? The truth is that all Linux operating systems that use the NetworkManager software expose Wi-Fi passwords by default, not just Ubuntu.

I hope that's an old magazine article.

---

### Post by sandyd on 2014-03-01
This is true and not true.

If you
- Do NOT check the box that says something like "All users may connect to this network" (note this is what its named in kde) - it will be saved in the home folder.

If you
- DO check that box, it will be saved in /etc/NetworkManager/system-connections (which will require root privileges to view)

---

### Post by Old_Grey_Wolf on 2014-03-01
I am trying to think of scenarios were this is a security risk for me.

If someone has physical access to my computer they also have physical access to my router. Resetting router gives access to the internet. 

If they do not have physical access; however, gained root access to my computer; then, I made a big mistake somewhere else.

---

### Post by varunendra on 2014-03-01
> Whether **[COLOR="#FF0000"]Canonical[/COLOR]** will make any changes to this or not remains to be seen.
..as if NM is designed and developed by Canonical :P

I guess the author will go running on the streets screaming and ripping off his clothes when he comes to know that the "Traditional" methods of using 'interfaces' file or wpa supplicant (in fact almost all connection managers) also use plain text format for storing passwords, and these files don't even need root privilege to read them!

Adding to Elfy's quote -
> Anyway, the best method to protect your entire computer remains full disk encryption.
..and even that is just 'Enhanced' security, not 'Absolute' security. ;)

[COLOR="#696969"]"Did you know that a matchstick has the potential to burn the entire house? Even entire city if used properly?? :shock:"[/COLOR]

---

### Post by sffvba[e0rt on 2014-03-02
Tallest trees, most wind etc...

---

