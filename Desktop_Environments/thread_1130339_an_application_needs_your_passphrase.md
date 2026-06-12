---
title: "an application needs your passphrase"
date: 2009-04-19
forum: Desktop Environments
---

### Post by amanda on 2009-04-19
An upgrade (possibly to Hardy Heron? It was quite some time ago.) introduced a new annoyance to my Gnome desktop, which is this:

When I log in and/or launch a nautilus window, Gnome (or nautilus?) asks for my ssh passphrase two or three times. The number of asks corresponds directly to the number of ssh / sftp connections that I have bookmarked in nautilus. 

I have three sftp locations bookmarked:

sftp://user@machine.example.com/home/directory

And so everytime I open nautilus it asks me to authenticate my ssh key three time. I also have two shortcuts saved on my desktop directly. And when I first login, gnome asks for my passphrase twice. 

To make things more frustrating, the alert says only that "an application" needs my passphrase. Not *which* application. For added annoyance, the same update that introduced these alerts introduced a change in my ssh-agent behavior, and it seems that my passphrase is stored for the duration of my login, whether or not I invoke it. 

These bookmarks are super useful, but I find this new behavior really frustrating. I've had a hard time figuring out how to go about reporting it, though. Is anyone else seeing this?  Is there a bug report I should have found for myself if I'd searched on the right terms?

---

### Post by amanda on 2010-01-29
FWIW this doesn't seem to be happening in Karmic.

---

