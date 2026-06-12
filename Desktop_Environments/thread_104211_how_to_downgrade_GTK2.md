---
title: "how to downgrade GTK2?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by bcrowell on 2005-12-15
I'm having a problem where GTK2 >=2.8 causes an application to crash, so I need to downgrade to 2.7. (This is actually a weird thing where GTK 2.8 broadcasts X events that are picked up by other apps, and it causes Perl/Tk apps to crash.) I currently have version 2.8.6-0ubuntu2.1, which was what came with breezy. Pawing around in synaptic, it doesn't look like it knows about any versions earlier than 2.8. By googling, I've found out that there used to be a  2.7.3-1ubuntu2 version, which would probably work for me. So it sounds like I need to do something like this:

# apt-get install libgtk2.0-0=2.7.3-1ubuntu2

But apt doesn't know about this version, so it doesn't work. Can anyone suggest how to approach this? Do I need to add something to my /etc/apt/sources.list?

And is downgrading from GTK 2.8 to 2.7 likely to break all my other GTK apps? (Well, I guess I could always undo it if that was the case.)

TIA! :razz:

---

### Post by bcrowell on 2005-12-15
Hmm...OK, I found that if I added a line to /etc/apt/sources.list that pointed to hoary, it would know where to find gtk 2.6.4. But then this happens:

The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-bin (>= 2.6.4-0ubuntu3) but it is not going to be installed

# apt-get install libgtk2.0-0=2.6.4-0ubuntu3
[...]
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-bin (>= 2.6.4-0ubuntu3) but it is not going to be installed
E: Broken packages

Even if I install libgtk2.0-bin, it still gives the same error message.:(

---

