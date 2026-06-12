---
title: "Synaptic &quot;can't stat source packages&quot;"
date: 2006-01-09
forum: Desktop Environments
---

### Post by endangst on 2006-01-09
I just turned on my computer today and tried to run Synaptic and this is what happens:

```
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
```

help? :(

---

### Post by handy on 2006-01-09
If your internet is OK, & your using a broadband router, you go to:

**Menu:  System/Administration/Networking**

Choose the **DNS** Tab in **Network Settings** Dialogue & check that the **DNS Server** IP addresses are correct for your ISP.  

You can easily check that you can query your router, usually via your web browser.

This solution worked for me.

Cheers

handy

---

### Post by endangst on 2006-01-09
Hi there.  I use dial-up, but checked DNS and everything seems normal there.

I did find this link:  [http://ubuntuforums.org/showthread.php?t=105563&highlight=synaptic+stat+source](http://ubuntuforums.org/showthread.php?t=105563&highlight=synaptic+stat+source)

where GeneralZod says:
"The "stat" errors are usually solved by clicking "Reload"; have you tried this, yet?"

The problem has resolved now.

Thanks! :)

---

### Post by akiro.yamamoto on 2006-01-09
I tried re-loading after a similar error and it worked for me...

---

### Post by handy on 2006-01-09
Maybe **reload** would have worked for me?  

The DNS thing did anyway.

It's interesting as a Ubuntu (Linux) noob, doing things with such a superficial knowledge.  

There is sooo much to learn, wow!!!

Great fun, :KS 

handy

---

