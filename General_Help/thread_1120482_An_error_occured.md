---
title: "An error occured"
date: 2009-04-09
forum: General Help
---

### Post by bug67 on 2009-04-09
Hello,

I posted this in "General" because I wasn't sure where it really fit in.  And, please, forgive me if this has been covered before.

When I run Update Manager, I am getting the following error message:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DBF1CA1622460E60


I started getting this error after installing the **[Google Linux Package Signing Key]("http://www.google.com/linuxrepositories/aboutkey.html")** so I could install the Picasa photo organizer as described **[here]("http://www.google.com/linuxrepositories/ubuntu704.html")**.

Can anyone tell me what's going on?  Thanks in advance.

---

### Post by juancarlospaco on 2009-04-09
Remove the Google Repo or Fix the Key.

---

### Post by bug67 on 2009-04-09
Forgive a n00b,

How do I fix the key?  I did remove to repo and I was still getting the same error.

Not *really* sure now that the Google repro is the problem.

This error key #:

DBF1CA1622460E60

Isn't showing up anywhere in my key list.  The Google one is a completely different number.

[B]The signing keys I have installed are as follows:
[/B]
437D05B5 2004-09-12
Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

FBB75451 2004-12-30
Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

0C5A2783 2006-11-23
Medibuntu Packaging Team <admin@lists.medibuntu.org>

7FAC5991 2007-03-08
Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>

**I have the following repositories installed (and checked):**

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

[http://ppa.launchpad.net/gkulyk/ubuntu](http://ppa.launchpad.net/gkulyk/ubuntu) intrepid main

[http://dl.google.com/linux/deb/stable](http://dl.google.com/linux/deb/stable) non-free

[http://dl.google.com/linux/deb/testing](http://dl.google.com/linux/deb/testing) non-free

[http://packages.medibuntu.org/intrepid](http://packages.medibuntu.org/intrepid) free non-free

I don't suppose it's really that big a deal.  Nothing really seems to be affected.  I'm just at a loss as to why I'm getting this weird error message.

---

### Post by chriskin on 2009-04-09
follow this : 

> **taavikko said:**
> This is for the first key,

```
gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
``````
gpg --export --armor 0c713da6 | sudo apt-key add -
```Do the same for the other key...
Last 8 digits...

Probably good idea to tell the problem to owner of ppa?

as said , use the 8 last digits instead of the ones in the example above


(my 4th time sending this exact same messagem, the original poster gave by far the best answer ever :) all credit goes to taavikko)

---

### Post by bug67 on 2009-04-09
> **chriskin said:**
> follow this : 



as said , use the 8 last digits instead of the ones in the example above


(my 4th time sending this exact same messagem, the original poster gave by far the best answer ever :) all credit goes to taavikko)

Forgive my lack of knowledge, but what "8 last digits?" from where?  Which 8 last digits?  I'm confused.  :p

**_EDIT_**:

Never mind.  I figured it out...finally!

Thanks for the help!  Ubuntu/Linux (and you guys/gals) ROCK!:guitar:

---

### Post by chriskin on 2009-04-09
i thought it was obvious that i meant the last 8 digits from your pubkey's digits :)

---

### Post by bug67 on 2009-04-09
Yeah, I'm kinda slow sometimes:P

---

