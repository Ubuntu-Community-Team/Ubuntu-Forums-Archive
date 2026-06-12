---
title: "Problems installing XFCE"
date: 2009-02-22
forum: Desktop Environments
---

### Post by MuRRe on 2009-02-22
Hi!
I have installed Ubuntu (EEEbuntu).
I really like it besides it's a little slow.
Therefor I was thinking of switching to XFCE, but I'm having problem.

Requested 'glib-2.0 >= 2.17.6' but version of GLib is 2.6.6
No package 'atk' found 
No package 'pango' found
No package 'cairo' found


Why does it want an older version?
Also, Synaptic says ATK is installed 

Thanks in advance
MuRRe

---

### Post by taurus on 2009-02-22
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by MuRRe on 2009-02-23
I tried

apt-get install kubuntu-desktop

Lets just say I can no longer get a GUI, i just get to the prompt.

How do I get back to gnome? I know it has to do with Xconf or something? Where is it located and what do I have to change in it??

Thanks in advance

---

### Post by taurus on 2009-02-23
```
sudo /etc/init.d/gdm start
```

---

### Post by MuRRe on 2009-02-24
> **taurus said:**
> ```
sudo /etc/init.d/gdm start
```

It failed :(

> **taurus said:**
> Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

How do I post it without being able to get into Gnome (or XFCE for that matter)?

---

### Post by taurus on 2009-02-24
But you're still able to log in from a console!  Otherwise, boot with a LiveCD and mount your harddrive where root filesystem is, /.  Then post the content of your /etc/apt/sources.list.

---

