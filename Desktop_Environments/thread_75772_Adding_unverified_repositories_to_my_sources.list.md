---
title: "Adding unverified repositories to my sources.list?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by last1 on 2005-10-14
I want to add the marillat repo to my sources.list and updating gives me error about needing the pubkey, what do I need to do to make it allow me to use unverified repositories without the hassle of adding the key?

I remember there's a way to do that, I just don't remember what it is ;)

---

### Post by jasmuz on 2005-10-14
Maybe there is some light in this wiki:

[https://wiki.ubuntu.com/BreakMyUbuntu](https://wiki.ubuntu.com/BreakMyUbuntu)

Break My Ubuntu!

---

### Post by last1 on 2005-10-14
The info doesn't seem to be in there, and if it is then I must have missed it. 

That's kind of annonying, I'd think it should be there, or that somebody could provide the info..Always peoples are saying "do this to add other repos" but they leave out the part about how to get around that, and it's just too much trouble to add the public key to my gpg keyring for a repository that I'm only going to use once to grab codecs and stuff.
EDITED to add:
Looks like I figured it out I think, you can create a file called apt.conf in /etc/apt/, and put in the line
APT::Get::AllowUnauthenticated;

Then it works. I think. ;)

---

