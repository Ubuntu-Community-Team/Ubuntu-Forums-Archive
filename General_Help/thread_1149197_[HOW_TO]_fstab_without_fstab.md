---
title: "[HOW TO] fstab without fstab"
date: 2009-05-05
forum: General Help
---

### Post by soulmatic09 on 2009-05-05
i've always had trouble with fstab in mounting my ntfs partitions.

but i just found a GUI called pysdm that can do all of the fstab editing for you pretty easily. Here are the instructions from this site:

[http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

To install Pysdm do this:

Command to install it

```
sudo apt-get install pysdm
```

Command to run it after install

```
sudo pysdm
```

Once it opens select the drive and then partition you want to mount on the left hand side of the GUI and then click mount and it should do it for you.

that's all there is to it! 

you may need to do a sudo fdisk -l to list your current drives. it's also a good idea to back up the old fstab, just in case.

---

### Post by dcstar on 2009-05-05
> **soulmatic09 said:**
> i've always had trouble with fstab in mounting my ntfs partitions.

but i just found a GUI called pysdm that can do all of the fstab editing for you pretty easily. Here are the instructions from this site:

[http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html)

To install Pysdm do this:

Command to install it

```
sudo apt-get install pysdm
```

Command to run it after install

```
sudo pysdm
```
.......

You do **not** run terminal commands when the package installs a perfectly good menu entry, and you should **not** tell people to use arcane command line install instructions when simply going into Synaptic and installing the package does the job.

Ubuntu is a GUI system, there is no need whatsoever to tell people to use non-GUI methods to install GUI packages which they can do simply anyway.

---

### Post by jowilkin on 2009-05-05
> **dcstar said:**
> You do **not** run terminal commands when the package installs a perfectly good menu entry, and you should **not** tell people to use arcane command line install instructions when simply going into Synaptic and installing the package does the job.

Ubuntu is a GUI system, there is no need whatsoever to tell people to use non-GUI methods to install GUI packages which they can do simply anyway.

Some of us enjoy using the command line.  Why do you feel the need to force people to do things the way you like?

A more polite way to say what you just did would be "Here is another way this can be accomplished for those who don't like to use the command line ..."

---

### Post by soulmatic09 on 2009-05-05
ok, fine.

instead of the 2 lines of code, search for "pysdm" in synaptic instead.


there. happy?

---

### Post by real_ate on 2009-05-21
wow! pysdm is a fantastic program! I'm a computer scientist and I still hate using config files no matter how easy they are! 

And for that matter the Synaptic way of doing this is pretty simple and very efficient! just giving my 2c. 

Thanks guys!:D

---

### Post by baseface on 2009-05-21
whoops. wrong quote

---

### Post by michy99 on 2009-05-21
> **dcstar said:**
> You do **not** run terminal commands when the package installs a perfectly good menu entry, and you should **not** tell people to use arcane command line install instructions when simply going into Synaptic and installing the package does the job.

Ubuntu is a GUI system, there is no need whatsoever to tell people to use non-GUI methods to install GUI packages which they can do simply anyway.

1. Terminal commands work for everybody, regardless of which GUI they use.

2. If I know the name of the package I want, it is faster and easier to use the command line to install.

---

### Post by ashmew2 on 2009-05-21
> **dcstar said:**
> You do **not** run terminal commands when the package installs a perfectly good menu entry, and you should **not** tell people to use arcane command line install instructions when simply going into Synaptic and installing the package does the job.

Ubuntu is a GUI system, there is no need whatsoever to tell people to use non-GUI methods to install GUI packages which they can do simply anyway.

Easy there on the keys man , they hurt sometimes ;)
Plus i think entering a command and installing is better than having to look around in synaptic etc etc..

I was pretty afraid of editing fstab when i was new (i still am sometimes :lolflag: ) ,

Nevertheless , A job nicely done soulmatic09..

---

### Post by detroit/zero on 2009-05-21
> **baseface said:**
> snip
+1

I had to read that guys post like three times before I could believe what I was seeing. The bolded words really added to the effect, too.

"Ubuntu is a GUI system":lolflag:
**Unless** it's the **server** edition, in **which** case it **doesn't** come standard with a **GUI**.

---

### Post by ibuclaw on 2009-05-21
> **detroit/zero said:**
> +1

I had to read that guys post like three times before I could believe what I was seeing. The bolded words really added to the effect, too.

"Ubuntu is a GUI system":lolflag:
**Unless** it's the **server** edition, in **which** case it **doesn't** come standard with a **GUI**.

I went into **Applications -> Add/Remove**

Typed in **pysdm** in the search filter, it came back with 1 result, "Storage Device Manager", to which I checked the box and clicked "Apply Changes".

Then I went in **System -> Administration -> Storage Device Manager**
and applied my changes there.

dcstar speaks sense here. I agree with him.

---

### Post by baseface on 2009-05-21
> **tinivole said:**
> I went into **Applications -> Add/Remove**
 
Typed in **pysdm** in the search filter, it came back with 1 result, "Storage Device Manager", to which I checked the box and clicked "Apply Changes".
 
Then I went in **System -> Administration -> Storage Device Manager**
and applied my changes there.
 
dcstar speaks sense here. I agree with him.
 
dcstar speaks sense by saying you should **not **use the "arcane command line". lol... right.

---

### Post by overdrank on 2009-05-21
Ok this thread has gone in the wrong directions. Thread closed.

---

