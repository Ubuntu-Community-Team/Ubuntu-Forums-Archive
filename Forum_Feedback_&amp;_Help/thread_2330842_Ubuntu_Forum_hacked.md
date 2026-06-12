---
title: "Ubuntu Forum hacked"
date: 2016-07-15
forum: Forum Feedback &amp; Help
---

### Post by expatver on 2016-07-15
Hello all

Wondering about any  response or recommendation  to this posting 

[http://betanews.com/2016/07/15/ubuntu-linux-forums-hacked/](http://betanews.com/2016/07/15/ubuntu-linux-forums-hacked/)

also from here

[https://it.slashdot.org/story/16/07/15/1533236/ubuntu-linux-forums-hacked----ip-address-username-email-of-2m-accounts-compromised](https://it.slashdot.org/story/16/07/15/1533236/ubuntu-linux-forums-hacked----ip-address-username-email-of-2m-accounts-compromised)

is this  ubuntuforums.org? If so, any  recommendations?

Thanks and regards
expat

---

### Post by QDR06VV9 on 2016-07-15
Just to be safe I would change your Email password you have Attached to the Forums.

---

### Post by QIII on 2016-07-15
[Here is the scoop from Canonical.]("https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums/")

This is what we know.

---

### Post by expatver on 2016-07-15
QIII 

Thanks for the link from Ubuntu.  Good information.


Hi runruckus how are you.....

 [COLOR=#333333][FONT=Ubuntu]They used this access to download portions of the ‘user’ table which contained usernames, email addresses and IPs for 2 million users. No active passwords were accessed; the passwords stored in this table were random strings as the Ubuntu Forums rely on Ubuntu Single Sign On for logins. The attacker did download these random strings (which were hashed and salted).

[/FONT][/COLOR]So if the hacker can crack the random strings they have access to our passwords from our Ubuntu account only, yes?  I am curious why  you recommend changing the  e mail account password for the e mail associated with an Ubuntu Single Sign on.....the password to the e mail account associated with my Ubuntu account had better not be anywhere on the Ubuntu site, no?


Regards to all

expat

---

### Post by QIII on 2016-07-15
If they crack it, they'll have random strings that mean nothing because you log in via SSO now.  Those old forum passwords were randomized and made useless.

I don't think we need to worry about email passwords.

---

### Post by QDR06VV9 on 2016-07-15
> **expatver said:**
> QIII 

Thanks for the link from Ubuntu.  Good information.


Hi runruckus how are you.....

 [COLOR=#333333][FONT=Ubuntu]They used this access to download portions of the ‘user’ table which contained usernames, email addresses and IPs for 2 million users. No active passwords were accessed; the passwords stored in this table were random strings as the Ubuntu Forums rely on Ubuntu Single Sign On for logins. The attacker did download these random strings (which were hashed and salted).

[/FONT][/COLOR]So if the hacker can crack the random strings they have access to our passwords from our Ubuntu account only, yes?  I am curious why  you recommend changing the  e mail account password for the e mail associated with an Ubuntu Single Sign on.....the password to the e mail account associated with my Ubuntu account had better not be anywhere on the Ubuntu site, no?


Regards to all

expat

I am well Thank You!
Here is all we know...I know that sounds like a brush-off..but just the facts
> **What the attacker could not access**
 
[LIST]
[*]We know the attacker was NOT able to gain access to any Ubuntu code repository or update mechanism.
[*][U]**We know the attacker was NOT able to gain access to valid user passwords.**
[/U]
[*]We believe the attacker was NOT able to escalate past remote SQL  read access to the Forums database on the Forums database servers.
[*]We believe the attacker was NOT able to gain remote SQL write access to the Forums database.
[*]We believe the attacker was NOT able to gain shell access on any of the Forums app or database servers.
[*]We believe the attacker did NOT gain any access at all to the Forums front end servers.
[*]We believe the attacker was NOT able to gain any access to any other Canonical or Ubuntu services.
[/LIST]

The Email password change is just a wise thing to do regardless.;)

---

### Post by expatver on 2016-07-15
QIII and runruckus

Thanks. Good info from both of you. I use a password generator and go through the labor of ageing all critical passwords particularly e mail accounts somewhat regularly.  Adminning this type of thing.... and it is administration...... can be a PITA given Ive got do it on 4 different devices....this Ubuntu desktop, an Apple laptop,  an Android tablet and an Android smartphone. And for 2 different e mail accounts as well on 3 of the devices, the smartphone only is allowed to sync mail on my throwaway g mail account, not the one that I use PGP on. 

Interesting isnt it. And some people  use  the internet particularly via an Android device connected to a public hotspot via wifi like someone would either a toilet or a toaster with an RS232 interface. I more and more consider moving to the jungle, having one throwaway account, and checking anything on the internet bi monthly.  Someone once said there is fiber in the Amazon , buried by the forerunners of the Maya to connect Teotihuacan to Machu Picchu. If I can find it and dig it up, wonder if its still lit.......

---

### Post by bapoumba on 2016-07-15
One thread that could be of interest : 
[https://ubuntuforums.org/showthread.php?t=2330572](https://ubuntuforums.org/showthread.php?t=2330572)

---

### Post by expatver on 2016-07-15
bapoumba 

Thanks

---

### Post by uRock on 2016-07-16
> **QIII said:**
> [Here is the scoop from Canonical.]("https://insights.ubuntu.com/2016/07/15/notice-of-security-breach-on-ubuntu-forums/")

This is what we know.

Thanks for sharing that. I wasn't very worried when I logged in and wasn't required to change my password. I know that would've happened if the maintainers thought our credentials were at risk.

---

### Post by misfitpierce on 2016-07-16
Thanks for more info on this. Wanted to see what the boards said.

---

### Post by bapoumba on 2016-07-17
We say we are doing our best to get back to a usable state :)

---

