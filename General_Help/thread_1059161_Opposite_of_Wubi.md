---
title: "Opposite of Wubi"
date: 2009-02-03
forum: General Help
---

### Post by schmidtbag on 2009-02-03
Quick question - is it possible to do the complete opposite of Wubi?  This means, create a virtual hard drive on your Linux partition so you can install Windows on it?

I would shrink my Ubuntu partition but I'm not 100% sure if I want to do that yet and I don't want to risk losing any data.

---

### Post by theDaveTheRave on 2009-02-03
schmidtbag

sound like you are describing a virtual machine to me?

this is possible in terms of a VM, but you will need to either make a virtual machine of your existing windows system, or have an installation CD for windows to be able to set this up.

My personal experience of virtual machines is that they never seem to want to work!

I was able to <install> XP under Qemu, but it was a painfully slow process, and didn't work properly! Then I discovered that I couldn't get access to MySQL on my host pc, so I forgot about the whole thing!

David

---

### Post by schmidtbag on 2009-02-03
no not at all, I'm aware of virtual machines but I want something like wubi where you can boot it up from restarting the computer.  I don't have enough memory or video power to do a virtual machine so thats why I want a virtual bootable disk.

btw, if you want a good vm, virtualbox has been phenomenal lately.  like almost right up there with vmware

---

### Post by Feivel on 2009-02-03
I always thought the opposite of Wubi was ibuW but what do I know...

---

### Post by theDaveTheRave on 2009-02-04
> **schmidtbag said:**
> no not at all, I'm aware of virtual machines but I want something like wubi 

Ah fair enough..

> 
where you can boot it up from restarting the computer.  I don't have enough memory or video power to do a virtual machine so thats why I want a virtual bootable disk.


I know the "not enough memory" issue, one of the many reasons I departed from windows, it kept using up all the memory then crashing out, with Linux you can kill a "misbehaving" application more easily.

> 
btw, if you want a good vm, virtualbox has been phenomenal lately.  like almost right up there with vmware

True, but again, for some reason it never wants to work for me! and I really don't have the time to put in a whole afternoon of "non-productivity" at work.... and it seems that the package I really want to be able to use functions through wine.... I just need time to give it a try!

David

---

### Post by schmidtbag on 2009-02-04
Be sure to download virtualbox from virtualbox.org, not from the repositories.  you get more out of it and its more up to date.  but, you have to specify the whole path of the program if you're to run it.  update your kernel too, that might be a problem




so nobody has an answer to my question?

---

