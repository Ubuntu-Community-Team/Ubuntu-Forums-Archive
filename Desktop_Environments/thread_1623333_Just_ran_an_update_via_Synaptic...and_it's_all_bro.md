---
title: "Just ran an update via Synaptic...and it's all broken."
date: 2010-11-16
forum: Desktop Environments
---

### Post by Norwood on 2010-11-16
So, as the titles states after my upgrade I can no longer run Nautilus, right click on the desktop or anything.

I've read all the threads on here regarding this problem, followed their advice and I can't get anything to work.

What's goin' on 'round here?

I even created a new user, logged in as it and was still unable to right click, browse using nautilus etc.

---

### Post by deconstrained on 2010-11-16
I assume you've tried 'sudo dpkg --configure -a' already...

The mouse problem is most likely related to an improperly configured xorg. If you're using a vendor-supplied display driver, it most likely came with a tool/utility for automagically generating a new config file, which would be worth a try before digging through /etc/X11/xorg.conf. For example, if your graphics is NVidia, you can do it with 'sudo nvidia-xconfig'.

---

### Post by Norwood on 2010-11-17
> **deconstrained said:**
> I assume you've tried 'sudo dpkg --configure -a' already...


I hadn't, but just did and it just brought me back to the prompt.

> **deconstrained said:**
> 
The mouse problem is most likely related to an improperly configured xorg. If you're using a vendor-supplied display driver, it most likely came with a tool/utility for automagically generating a new config file, which would be worth a try before digging through /etc/X11/xorg.conf. For example, if your graphics is NVidia, you can do it with 'sudo nvidia-xconfig'.

What would I be looking for exactly in the xorg?  Also, I've got no 'nvidia-xconfig' command...perhaps because it's a vm?

---

### Post by lin-athi on 2010-11-17
I also have the same problem after updates.

---

### Post by sikander3786 on 2010-11-17
Did you try installing any available updates from terminal?

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get install -f
```

And did you try starting nautilus from terminal? Does it start? Any errors there?

```
nautilus
```

---

### Post by Norwood on 2010-11-17
> **sikander3786 said:**
> Did you try installing any available updates from terminal?

```
sudo apt-get update
``````
sudo apt-get upgrade
``````
sudo apt-get install -f
```And did you try starting nautilus from terminal? Does it start? Any errors there?

```
nautilus
```

Yes, those are all instructions from other threads about this and nothing works.

I said screw it and simply installed a new VM with 5.0.6

Anyway, I guess my last question with this is Nautilus behavior/look & feel.

It used to look like a regular filebrowser.

Now, it just looks like a window with a list of files.  Double clicking a directory opens a new nautilus window etc.

How can I get it so there's a directory tree on the left side, and new directories open right there, not some who new window leaving me with 100 open windows because I needed to drill down into a deep directory?

---

### Post by sikander3786 on 2010-11-17
Open nautilus.

Go to View and enable Side Pane.

Go to Edit > Preferences > Behavious and disable Open each folder in its own window.

---

