---
title: "Hard drive problems"
date: 2009-02-22
forum: General Help
---

### Post by thermobee on 2009-02-22
Just before i installed ubuntu, i added a second 40gb drive to my first 80gb. I made the 40 the slave and the 80 one had windows installed on it. Then i installed ubuntu on the 40 and i liked it so much that after i pulled out all of my documents from C:, i decided to format my 80gb drive since i dont want windows anymore. Now in the 80gb( and the probem might be that i dont completely understand how to work with the drives in linux) but i cant do anything in it, after i mount it. For example i cant create folders or paste files.

Thank you for your help in advance

---

### Post by thermobee on 2009-02-22
bump

---

### Post by thermobee on 2009-02-22
?

---

### Post by thermobee on 2009-02-22
bump

---

### Post by thermobee on 2009-02-22
can anyone please explain this to me?

---

### Post by prinny42 on 2009-02-22
I had a similar problem recently when I formatted a 4GB USB stick to ext3 (so that I could preserve permissions on my backup documents).

I'm not sure if this is the optimal solution (I'm not really even sure if it's a very good solution at all), but what worked for me was mounting the volume and changing the owner of its mount folder from root to me.

This can be accomplished like so:  Say the mount folder is /media/disk, simply execute this command
```
sudo chown (Your Username Here) /media/disk
```

Of course, my situation was a bit different, so I'm not sure if this will work, but it seems worth a try.

Also, please refer [here]("http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/").

---

### Post by thermobee on 2009-02-22
> **prinny42 said:**
> I had a similar problem recently when I formatted a 4GB USB stick to ext3 (so that I could preserve permissions on my backup documents).

I'm not sure if this is the optimal solution (I'm not really even sure if it's a very good solution at all), but what worked for me was mounting the volume and changing the owner of its mount folder from root to me.

This can be accomplished like so:  Say the mount folder is /media/disk, simply execute this command
```
sudo chown (Your Username Here) /media/disk
```

Of course, my situation was a bit different, so I'm not sure if this will work, but it seems worth a try.

Also, please refer [here]("http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/").
Thanks ill try this.

---

### Post by thermobee on 2009-02-22
how do you address folders in ubuntu?

---

### Post by prinny42 on 2009-02-22
> **thermobee said:**
> how do you address folders in ubuntu?

The filesystem is like a big tree.  The ultimate parent directory, the root of the tree, is just "/".  Your personal things are kept in your home folder, which is at "/home/(your username)" (this is often simply abbreviated "~").  Things can technically mount just about anywhere, but by default in Ubuntu external media automounts at "/media/(something)".  To find where something is mounted, just plug it in, wait for it to show up on the desktop and open, and there should be its address near the top of the browser window.  If that's not the case, just click the pencil and paper near the top-left and it will show up.

A better and more in-depth overview of the filesystem organization (and some other basics as well) can be found [here]("http://www.linuxcommand.org/learning_the_shell.php").

---

