---
title: "Filemaker PRO 5.5"
date: 2005-12-02
forum: Desktop Environments
---

### Post by lybbe on 2005-12-02
Hi!

I've been trying UBUNTU on one of my testmachines for a little while. I must say that i'm really impressed of this dist! Nice work guys!

I want to switch from Winxp to UBUNTU on my work-laptop, but there is a small but...

How do i install Filemaker PRO 5.5 with wine? I really don't want a dualboot, but i need filemaker for my work.

Have anyone managed to get this work with UBUNTU and Wine? (or with any other dist). To complete my switch, i really need to get FM to work on UBUNTU. 

Thanks in advance

/ Martin

---

### Post by suoko on 2005-12-02
I'm trying to run filemaker with wine 0.9.2 but up to now I had no success.
However I could successfully run it through crossover 4.2 with no problems at all. Just install it as an unsupported application

---

### Post by lybbe on 2005-12-02
suoko,

Thanks, have never heard of crossover before, but found it on google. Will download the trial and see if i can get it to work.

Thank you

/ Martin

---

### Post by lybbe on 2005-12-02
I managed to install Filemaker with crossover, and that is great! But all my datafiles is located on a networkshare. 

How can i access the network from within Filemaker? Even if i've mounted a share on the desktop, it's not visible on the desktop from the "open dialogue" in filemaker?

Thanks

/ Martin

---

### Post by suoko on 2005-12-02
You have to configure wine to do so.
Running winecfg you have to add a drive which should point to the remote directory.
Don't know where gnome puts this mount points, sorry.

---

