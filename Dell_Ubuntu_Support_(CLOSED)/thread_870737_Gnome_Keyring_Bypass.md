---
title: "Gnome Keyring Bypass"
date: 2008-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drsaamah on 2008-07-26
I am using a dell xps m1330 and have had some issues with ThinkFinger.  I started using ThinkFinger on Gutsy and had everything running perfectly.  For the first time since I've started using Hardy, I've installed ThinkFinger.  Everything works perfectly except that when I first log into Gnome, that pesky gnome-keyring applet pops up before I can connect to a wireless network.  The fixES that I have tried implementing are based on the instructions found [here]("http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/").
All the fixes I've tried either break gdm, or seem to do nothing.
Any suggestions?
Thanks in advance for the help!

---

### Post by drsaamah on 2008-07-31
*bump*

---

### Post by tibrisch on 2008-09-10
I am in the same situaion, i h8 the keyring password

---

### Post by augoldfinger on 2008-09-11
Same Here!
I went to System, Preferences, Encryption & Keyrings, selected remove. When I restarted the computer voila I had to select a keyring.

---

### Post by chris.raighn on 2008-11-08
Here is the solution:
[URL="http://ubuntuforums.org/showpost.php?p=2776815&postcount=1"]
http://ubuntuforums.org/showpost.php?p=2776815&postcount=1[/URL]

---

### Post by j0rd on 2008-11-17
I don't believe the solution you posted chris applies to the issue of keyring and thinkfinger, which as far as I can tell, is still not resolved.

Check out more information here:
[https://bugs.launchpad.net/gnome-keyring/+bug/276384](https://bugs.launchpad.net/gnome-keyring/+bug/276384)

---

### Post by red_five on 2008-11-21
It's probably going to be a while before thinkfinger can unlock your keyring. It's a fundamental design and usage issue in Gnome-Keyring, because it uses passwords to unlock the keyrings. Thinkfinger does not "type" your password into authentication prompts or anything; it simply integrates with PAM to tell the system to accept a different form of authentication when it asks for it.

Since Gnome Keyring can hold passwords to various network sites and so forth, its developers and those of Thinkfinger have decided thus far not to incorporate that level of integration. Fingerprints can be spoofed pretty easily to fool the scanner, so if they get logged in and GK can use the fingerprint to unlock keyrings as well, the spoofer has the master key to Fort Knox, as it were. He can get to anything that has a password stored in the keyring. I don't think I have to tell you how bad that could turn out.

---

### Post by shmish111 on 2010-10-08
After 2 years this problem still exists.  Where can I request it as a new feature?  It's not exactly high priority but it's the type of thing that can change someone's opinion of Linux over windows.  Also, what about a GUI linked to the User management window?  OpenSUSE has all of this, worked right out of the box but unfortunately I really don't like SUSE compared to Ubuntu!

---

