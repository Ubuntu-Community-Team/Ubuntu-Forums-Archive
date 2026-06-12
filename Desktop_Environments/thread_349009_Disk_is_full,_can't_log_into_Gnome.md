---
title: "Disk is full, can't log into Gnome"
date: 2007-01-29
forum: Desktop Environments
---

### Post by Zeedok on 2007-01-29
So I finally learned how to file share.

Unfortunately, I suspect that when I left for work with torrents happily downloading I have filled-up my Ubuntu partition (still plenty of room on other partitions).

After some searching I found that this can cause login problems with Gnome (ie when I login it bounces back to the login page repeatedly).

Can someone point me in the direction of a guide to logging in via the command line or some other way to get into Ubuntu so I can move some files etc, free up some space?

Thanks

---

### Post by Paerez on 2007-01-29
CTRL+ALT+F1 will put you at a command line. Then you can use standard unix commands to move around a remove files.

[http://mally.stanford.edu/~sr/computing/basic-unix.html](http://mally.stanford.edu/~sr/computing/basic-unix.html)

---

### Post by mexlinux on 2007-01-29
Once in command line, have a look at /var/cache/apt
maybe that space is enought to get your system back alive

---

### Post by taurus on 2007-01-29
```
sudo aptitude clean
```

---

### Post by Zeedok on 2007-01-30
Thanks Taurus. Thought it was only fair to tell you that your suggestion worked perfectly - not entirely sure what that command does, but . . . very grateful for the prompt, easy to use advice.

You guys keep Ubuntu going. 

Thanks again

---

### Post by Paerez on 2007-01-30
That will clean out the stuff ubuntu downloads to perform updates. It will grow back as you update more, so make sure to leave some space.

You can run it every now and then to keep ubuntu's package cache low in size. I do.

---

### Post by taurus on 2007-01-30
> **Paerez said:**
> That will clean out the stuff ubuntu downloads to perform updates. It will grow back as you update more, so make sure to leave some space.

You can run it every now and then to keep ubuntu's package cache low in size. I do.

Or you can have it remove automatically after it's installed with synaptic.

---

### Post by twisted_hick on 2007-03-09
Thank you Taurus you saved me from doing a ugly habit I developed when I was a windows baby." reinstalling "<shudders>. I love the ubuntu community Thanks again Taurus.

by the way this is my first post :)

---

### Post by taurus on 2007-03-09
> **twisted_hick said:**
> Thank you Taurus you saved me from doing a ugly habit I developed when I was a windows baby." reinstalling "<shudders>. I love the ubuntu community Thanks again Taurus.

by the way this is my first post :)

Glad to help and welcome.

---

