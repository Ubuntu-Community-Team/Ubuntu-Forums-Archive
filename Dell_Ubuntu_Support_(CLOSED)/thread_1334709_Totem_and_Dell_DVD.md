---
title: "Totem and Dell DVD"
date: 2009-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Debra.S on 2009-11-22
Totem will not play DVD's for me anymore.  My computer is about 2 months old and I just went to play a movie for the first time in awhile.  It is telling me that it cannot determine the stream.

So I went to play it in Dell DVD and that's telling me that it doesn't support the type of media.

I've used both of these before.  If it matters, I couldn't put the DVD by pressing the external button - I had to go into the drive and press "eject".

So two questions:

1) Could these problems be related?

2) Any idea what's going on?

I'm new to this and trying to learn, please be kind!

---

### Post by Debra.S on 2009-11-25
Problem solved. [OPs husband here.]

The original issue was with being able to play DVD movies specifically, and had the error message "No URI handler..."

The issues started when updating to 9.10.  The simple solution was merely to go through the Synaptic Package Manager and install the ubuntu-restricted package, and then to run the install script for DVD reading capability as instructed on the official Ubuntu guide.

The complexity had to do with a previous uninstallation of Dell's proprietary DVD player that apparently had not gone cleanly.  The Synaptic Package Manager had a forced removal of pdvdlinux package (this package was for the proprietary Dell DVD player, and was not able to be unmarked for deletion).  That removal would always fail with an error code and the Package Manager would not continue on to install the restricted media package.

This has been resolved but involved hand editing some configuration files and forcing some package management on the command line.

---

