---
title: "Gutsy Gibbon End-of-Life?  Now what do I do with these 1500 servers..."
date: 2009-05-18
forum: General Help
---

### Post by drachs on 2009-05-18
So I have a development server with gutsy gibbon installed on it.  Using the binaries from this server I compile firmware that gets installed on flash chips.  We have about 1500 devices out in the field right now with these flash chips.   

So the boss needs radius support, and I go to "apt-get install" it to the development server so I can move the binaries to our flash firmware and ... Uh... Well looks like the repositories have been deleted.

I knew end of life was coming up, but I didn't expect the repositories to disappear.  I fully expect to be patching any critical bugs myself, but I assumed basic software would be available.

So now what do I do?  Am I consigned to compiling all future software from scratch?  That would be inconvenient. Can I update apt-get to access the old repositories some where else?  Is there a "supported" version that is binary compatible with gutsy gibbon?  Can I somehow migrate to the long supported branch?   

I need some advice here.   

Thank you for your help!

David

---

### Post by PhilMize on 2009-05-18
Wow! That's not cool... Wish I could help you out but I have no idea. Maybe call Canonical? Do they even have a support line?

---

### Post by michy99 on 2009-05-18
I believe the repositories are moved to:

[http://old-releases.ubuntu.com/ubuntu/dists/gutsy](http://old-releases.ubuntu.com/ubuntu/dists/gutsy)

---

### Post by arsenic23 on 2009-05-18
> **michy99 said:**
> I believe the repositories are moved to:

[http://old-releases.ubuntu.com/ubuntu/dists/gutsy](http://old-releases.ubuntu.com/ubuntu/dists/gutsy)

Holly crap!  I did not know this.  Thank you.

---

### Post by HermanAB on 2009-05-18
Gee man, if you have that many servers, then you should copy the WHOLE repository with wget and keep it.  A complete distro is about 20 to 30GB including source.

---

### Post by drachs on 2009-05-18
> **michy99 said:**
> I believe the repositories are moved to:

[http://old-releases.ubuntu.com/ubuntu/dists/gutsy](http://old-releases.ubuntu.com/ubuntu/dists/gutsy)
Anybody know what changes I need to make to my sources.list in order to access this repository location?

---

### Post by drachs on 2009-05-18
> **HermanAB said:**
> Gee man, if you have that many servers, then you should copy the WHOLE repository with wget and keep it.  A complete distro is about 20 to 30GB including source.
That's a good idea, I might just do that.

---

### Post by michy99 on 2009-05-18
> **drachs said:**
> Anybody know what changes I need to make to my sources.list in order to access this repository location?

Try changing "us.archive.ubuntu.com" to "old-releases.ubuntu.com" wherever it occurs.

---

### Post by drachs on 2009-05-18
> **michy99 said:**
> Try changing "us.archive.ubuntu.com" to "old-releases.ubuntu.com" wherever it occurs.

Thanks, that did the trick.   Is there any information on how long this online archive should be online?

David

---

### Post by Wiebelhaus on 2009-05-18
> **drachs said:**
> Thanks, that did the trick.   Is there any information on how long this online archive should be online?

David

Seriously mate , Download the whole thing to a server that you manufacture with Ubuntu Server and redirect them all to that , that way you can maintain the whole shebang and control everything.

Build a server with 160 gig raptor , the whole repository shouldn't be more than 40gigs or so.

---

