---
title: "install problems-blank screen after login"
date: 2009-01-25
forum: General Help
---

### Post by diaperfecto on 2009-01-25
Hi, I'm a new user installing Ubuntu through Wubi on an older Dell Latitude c400.  I went through the installation without any problems, but after I log in with my username and password it goes to a blank, tan screen with just the arrow.  I let it sit for a long time but nothing happens.

I've looked through a few other posts for solutions, but my laptop doesn't respond to anything I try (one post suggested pressing control-alt-F2, but nothing registers).

My laptop meets the requirements listed on the Wubi page - 512 MB of memory when it needs 256 MB, about 12 GB free when it needs 5 GB, and running XP - but I did notice that its processor speed of 133 MHz is less than what's recommended in the Ubuntu guide.

Please let me know of any suggestions or if you need more info.  Thanks

---

### Post by diaperfecto on 2009-01-29
> **diaperfecto said:**
> Hi, I'm a new user installing Ubuntu through Wubi on an older Dell Latitude c400.  I went through the installation without any problems, but after I log in with my username and password it goes to a blank, tan screen with just the arrow.  I let it sit for a long time but nothing happens.

I've looked through a few other posts for solutions, but my laptop doesn't respond to anything I try (one post suggested pressing control-alt-F2, but nothing registers).

My laptop meets the requirements listed on the Wubi page - 512 MB of memory when it needs 256 MB, about 12 GB free when it needs 5 GB, and running XP - but I did notice that its processor speed of 133 MHz is less than what's recommended in the Ubuntu guide.

Please let me know of any suggestions or if you need more info.  Thanks
I've done some more research and found that my processor speed is actually 1 GHz so that's not the problem.  A similar problem with a blank screen after login was solved for another user by adjusting the video buffer, but unfortunately you can't do that on a Dell Latitude c400 and trying different things in the recovery menu doesn't seem to help.  

My video card is an Intel 830M.  Is there any type of driver that I can get to fix this?  Does it make sense to uninstall Ubuntu 8.10 and then try installing Kubuntu or an earlier version of Ubuntu that might work?

---

### Post by bakkegaard on 2009-01-29
I have the same problem on an old compaq computer :(

---

### Post by freeztar on 2009-01-31
I'm having the same problem with wubi, Kubuntu 8.10 in XP.
What can I try to fix this. I'm a complete linux noob.

---

### Post by diaperfecto on 2009-02-06
So I ended up uninstalling 8.10 and reinstalling 8.04 with wubi, which is working ok except for occasional crashes.

---

