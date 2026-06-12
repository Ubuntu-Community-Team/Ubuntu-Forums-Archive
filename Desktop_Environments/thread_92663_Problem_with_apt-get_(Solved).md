---
title: "Problem with apt-get (Solved)"
date: 2005-11-20
forum: Desktop Environments
---

### Post by Mozzer on 2005-11-20
When an application is not available via Synaptic, I turn to Root Terminal. However, apt-get doesn't seem to be working.

e.g.
```
mozzer@ubuntu:~$ sudo apt-get install gstreamer0.8-mad
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

What does all this mean?

Thanks in advance,
Mozzer

EDIT: In Synaptic, it looks like the only repository listed is the Breezy Badger CD. Why is this? And does this have something to do with my problem?

---

### Post by Haegin on 2005-11-20
It normally means you have another program using the administration directory. In reality this means you probably have synaptic or kynaptic (or similar) open. Close these programs and try again.

---

### Post by Mozzer on 2005-11-20
Thanks, that was a bit silly of me really.

Now I'm past that hurdle, I'm fairly convinced that my lack of repositories is my next problem to overcome.

I get feedback like:
```
mozzer@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
Package gstreamer0.8-plugins is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gstreamer0.8-plugins has no installation candidate

```

And:
```
mozzer@ubuntu:~$ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer0.8-lame
```

Again, thanks for the help
Mozzer

---

### Post by Haegin on 2005-11-20
edit your sources.list file
```

sudo gedit /etc/apt/sources.list

```

This is my sources.list file so you an just use these:
```

# Breezy Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb http://ubuntu-backports.mirrormax.net/ breezy-extras main restricted universe multiverse

# Main Updates
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

# Multiverse
deb http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main universe multiverse restricted

# Main Security
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

# Universe Security
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

# plf
deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

```

Alternatively just uncomment (remove the #) some of the lines (anything that isnt  normal english basically)

---

### Post by Mozzer on 2005-11-20
Well that was odd - for some reason all my sources were commented out.

After changing them it still didn't seem to be happy but it said you might want to try apt-get update so I did and now it works just fine.

Thankyou :)

---

