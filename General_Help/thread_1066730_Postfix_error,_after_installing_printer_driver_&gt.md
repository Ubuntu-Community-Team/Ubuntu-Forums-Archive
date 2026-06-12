---
title: "Postfix error, after installing printer driver &gt; My solution"
date: 2009-02-11
forum: General Help
---

### Post by thehat on 2009-02-11
I got this config error after installing a proprietary printer driver for a Toshiba e-Studio451c "all-in-one" printer

the error appeared, and kept appearing whenever I installed or removed any software, using apt, or synaptic.

 E: postfix: subprocess post-installation script returned error exit status 75

Along with other dependency issues.

the reason for this post is that I couldn't see a solution for the error.

In the end, as I am running a desktop, not a server, I simply removed Postfix, and used 

[http://www.linuxprinting.org/show_driver.cgi?driver=Postscript](http://www.linuxprinting.org/show_driver.cgi?driver=Postscript)

to create an open pdd file to use instead of the proprietary one.

To date no issues, and I haven't encountered the error again as yet.

cheers

Edit: Sorry if this is the wrong place for this post, but I thought general help was the best place, as I've seen people asking about this when making changes to their windows manager.

Edit2: Also meant to say that i ran this past a couple of "power" Ubuntu/Debian work colleagues, who are of the opinion, that this wouldn't hurt.

---

### Post by k3jsparks on 2010-09-20
Hi,
I am glad to see you got the Toshiba e-Studio 451c working. Can you help me figure out an install for it? I decided to use Wine to install and it was doing the install but asked for an address for the printer, but I have no idea how to find that address. Can you tell me how to do that?

I am new to Ubuntu and Linux, but I want to learn.

:confused:

---

