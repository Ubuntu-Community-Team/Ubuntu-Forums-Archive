---
title: "Manager seems KOO KOO"
date: 2009-06-07
forum: General Help
---

### Post by Archie69 on 2009-06-07
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513

Thats the error message I see when I run 'check' on update manager.

I ran this prior to getting the message:

sudo gedit /etc/apt/sources.list in terminal to get the source list, but as I imagined it only made me lost more. The index page is:

[http://ppa.launchpad.net/](http://ppa.launchpad.net/)

It didn't bother me at first but now its making me nuts.  Any help would be awesome.

---

### Post by jonathanysp on 2009-06-07
that means that you dont have a gpg key to verify the things you download from launchpad. Go to the launchpad site where you got the ppa and download the gpg key from there and then add it in the software sources.

---

### Post by Archie69 on 2009-06-07
I'm on the launchpad site and I can't find the gpg key.  I might sound like an idiot, but I have no idea where to go from this point.

---

### Post by cariboo on 2009-06-07
If you gave us a direct link to the ppa you don't have the proper key for, it would make things a lot easier. The page you linked to just shows a list of all the ppa's.

---

### Post by Archie69 on 2009-06-07
I know, but it was a while ago.  Sorry.  This all happened when I updated my screenlets, (trash can was missing).  When I updated it using that line in terminal, this error started happening.  Its doesnt seem to be effecting anything, but I'd prefer it to run seamlessly.

---

### Post by Archie69 on 2009-06-30
So I'm not sure what the problem actually was, but in Software Sources under the third party tab i unchecked [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) hardy  and the error on the system update doesn't pop up anymore.  I don't know if this helps anyone or not, but just wanted to close this post.

---

