---
title: "Synaptic won't install DOSBox"
date: 2005-07-13
forum: Gaming &amp; Leisure
---

### Post by SlugO on 2005-07-13
When I try to install DOSBox using synaptic it gives me this error:

Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

After clicking No, the next message is:

The following problems were found on your system:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dosbox/dosbox_0.63-2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/d/dosbox/dosbox_0.63-2_i386.deb)
  MD5Sum doesn't match

So for some reason the MD5Sum is wrong. Is there something wrong
with the package or would it be safe to install it if I could get synaptic
to do it? Or should I just get the Debian Woody package from [here](http://dosbox.sourceforge.net/download.php?main=1)?

---

### Post by adwait on 2005-07-13
the us server seems to be broken right now, open your sources.list file with

sudo gedit /etc/apt/sources.list

Then, in all places change us.archive.ubuntu.com to archive.ubuntu.com

---

