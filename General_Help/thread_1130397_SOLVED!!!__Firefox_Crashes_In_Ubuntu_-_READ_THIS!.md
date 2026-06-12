---
title: "SOLVED!!!  Firefox Crashes In Ubuntu - READ THIS!"
date: 2009-04-19
forum: General Help
---

### Post by umechanism on 2009-04-19
If you found this thread then you already know what I'm talking about.  FF crashes randomly and, for me at least, most often on Facebook and YouTube.  Is it Flash?  Is it Java?  Is it some obscure plug-in?  Who knows but I've scoured the web and finally found something that works for me.  Your mileage may vary.

I found this link:  [http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/](http://ninetynine.be/blog/2009/04/fix-random-crashes-firefox-thunderbird-and-evolution-on-ubuntu-810/)  which instructs you on how to make modifications to your /etc/nsswitch.conf file.  You can read the article yourself but the below text is taken directly from the website (all credit given to that website):

```
Enter this in your console:

sudo nano /etc/nsswitch.conf

And look for a line like this:

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Change it into

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Now, odd thing for me was that the "hosts:" line in my nsswitch.conf file was commented out so I just uncommented the file as shown below in a copy/paste of my actual file.

```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts: wins files dns mdns
[B]#I uncommented "hosts" below to see if it would solve FF crash issue.
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4[/B]
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

I've been using FF now for two days since I've made the change and I've not had one - no, not even one - crash and FF is much, much faster than it was before.  I hope this helps you as much as it did me.

-73

---

### Post by lovinglinux on 2009-04-19
Is this a secure procedure?

---

### Post by ibuclaw on 2009-04-19
> **lovinglinux said:**
> Is this a secure procedure?
This is the default nsswitch.conf file in Jaunty.
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
So my suggestion to you is 'yes', it probably is secure.

Regards
Iain

---

### Post by Svensk023 on 2009-04-19
very interesting, I shall give this a try

---

### Post by lovinglinux on 2009-04-19
> **tinivole said:**
> This is the default nsswitch.conf file in Jaunty.
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
So my suggestion to you is 'yes', it probably is secure.

Regards
Iain

Thanks. That's all I needed to know.

---

### Post by JK3mp on 2009-04-19
I've never had problems with firefox. Lol, but i might try it out for the increased speed.

---

### Post by codeseer on 2009-04-19
Mine was already like that and Firefox still crashes from time to time; it's probably from a corrupt profile or addon though.

---

### Post by lovinglinux on 2009-04-19
> **codeseer said:**
> Mine was already like that and Firefox still crashes from time to time; it's probably from a corrupt profile or addon though.

Oops, mine too  :mrgreen: 

Mine was crashing sometimes on youtube, but since I installed Flash 10 I didn't notice any crash.

---

### Post by codeseer on 2009-04-19
I have Flash 10 (64-bit) and still crash.

---

### Post by phantom3113 on 2009-04-19
> **tinivole said:**
> This is the default nsswitch.conf file in Jaunty.
```

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```
So my suggestion to you is 'yes', it probably is secure.

Regards
Iain

This is also the default settings in Intrepid.

---

### Post by Telescope_Nerd on 2009-06-01
Thanks for the post. My firefox has been crashing very frequently I checked the config file and I found that it contained the "wins" option along with a comment line from me saying that i had added the "wins" option in at a previous date. I can't remember doing this but I suppose it was to try and cure some other problem. 

Anyway I hope it fixes the problem, i'll let you know!

---

### Post by umechanism on 2009-06-01
I hope it works for you.  It has worked for me just perfectly.  No crashes since I first made this post.  FF is working great now!

---

### Post by Telescope_Nerd on 2009-06-03
0 crashes so far. Good fix!

---

### Post by coffeecat on 2009-06-03
> **Telescope_Nerd said:**
> Thanks for the post. My firefox has been crashing very frequently I checked the config file and I found that it contained the "wins" option along with a comment line from me saying that i had added the "wins" option in at a previous date. I can't remember doing this but I suppose it was to try and cure some other problem.

So that you could resolve Windows hostnames in order to browse Windows shares, perhaps?

Point 3 in:

[http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

Which links to:

[http://ubuntuforums.org/showpost.php?p=7075850&postcount=4](http://ubuntuforums.org/showpost.php?p=7075850&postcount=4)

By the way, I've put the wins argument **in** that line and I don't get random Firefox crashes.

---

### Post by Telescope_Nerd on 2009-06-08
> **coffeecat said:**
> So that you could resolve Windows hostnames in order to browse Windows shares, perhaps?

Point 3 in:

[http://ubuntuforums.org/showpost.php?p=7157868&postcount=12](http://ubuntuforums.org/showpost.php?p=7157868&postcount=12)

Which links to:

[http://ubuntuforums.org/showpost.php?p=7075850&postcount=4](http://ubuntuforums.org/showpost.php?p=7075850&postcount=4)

By the way, I've put the wins argument **in** that line and I don't get random Firefox crashes.
Yes, that was it. Interesting that you don't get Firefox crashing. Removing this argument definitely fixed the problem I had. It must be connected somehow, perhaps this bug was triggered by a combination of this and some other setting?

---

### Post by eldenico on 2009-12-22
None of these solutions works... That is the default configuration, My FF was working Ok until I made an update yesterday and my FF starts to crash. Is there any way to rollback my last update?

---

### Post by Musicologynut85 on 2010-01-08
I've been having this problem ever since I upgraded to Jaunty, and I have yet to find a solution. I don't have the "wins" option enabled, but I might enable it just for giggles.

For me, when I am using firefox (usually facebook) the entire screen will freeze (except for the mouse), and nothing will work until I do a cold reboot (pull the plug).

It is *REALLY* annoying.

---

### Post by tauren on 2010-02-19
I too am having this problem. Firefox crashes sometimes as soon as I start it, and other times it will run for an hour or more and then crash.  I haven't found any particular site or page that causes it to happen.  By crash, I mean firefox windows will just disappear all of a sudden. No error is displayed, they are just gone. It can happen while I'm using FF, or while I'm doing something else and FF is in the background.

This is on a fresh Ubuntu 9.10 64-bit desktop that I just installed yesterday. From Ubuntu Software Center, I added Ubuntu Restricted Extras, which I think adds flash, java, and other addons for Firefox.

I created a new profile and used it for a while. Then it crashed. Upon restarting, I got this message:

$ firefox -ProfileManager
pure virtual method called
terminate called without an active exception
Aborted

I don't have wins in my nsswitch.conf.

Suggestions?

Tauren

---

### Post by distortedecho on 2010-12-22
My default is also without the "wins" and I still get Crashes...

---

### Post by 4Orbs on 2010-12-22
Another thing that might help: increase the size of the Firefox cache, maybe double or more.

---

### Post by Ghost_Mazal on 2010-12-22
Also had this problem. Annoyed me so much that I just switched to Chrome.

---

### Post by Machiavelli on 2011-03-29
> **Ghost_Mazal said:**
> Also had this problem. Annoyed me so much that I just switched to Chrome.

I feel you, it's now 2011 and still the same problem!!

---

