---
title: "Dell + linux = fail"
date: 2009-04-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jackal242 on 2009-04-04
The /etc/apt/sources.list that Dell ships with the Mini 12 (running Ubuntu) is full of fail.

```
    $ cat sources.list
    deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
    deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

    deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
    deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

    deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
    deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

    deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
    deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

    deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
    deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted

```


When you try to do a apt-get update it just sits there and hangs....

```
    $ sudo apt-get update
    0% [Waiting for headers]                                         
    0% [Waiting for headers]
    0% [Waiting for headers]
    0% [Waiting for headers]
```


I called Dell to tell them their servers are offline and not working... ... and they responded, "So the problem is with your bluetooth?"  hahahahahaha

---

### Post by miami2verona on 2009-04-04
lol
I called them and they told me: we don't support ubuntu.....so look in the forum or call ubuntu support

---

### Post by gbrainin on 2009-04-04
If you're calling the general (*i.e.*, windows) support line, you shouldn't expect them to have clue one regarding linux.  And, apparently, you were not disappointed.

However, while the repositories may be provided by Dell, they are clearly (from the URLs) hosted by Canonical.  If the servers are down, that's Canonical's problem.

---

### Post by Kareeser on 2009-04-04
> **gbrainin said:**
> However, while the repositories may be provided by Dell, they are clearly (from the URLs) hosted by Canonical.  If the servers are down, that's Canonical's problem.

Not necessarily, that subdomain could simply be a CNAME record to one of dell's servers. Canonical doesn't own many of their servers... chances are, you're downloading from a mirror :)

---

### Post by anjilslaire on 2009-04-04
Am I the only person who drills down in synaptic and specifies the closest server to my physical location? I have all my systesms pulling from the open source lab in a nearby university that's listed in the repository section of synaptic, not just "Server for the United States" in my case.

Downloads are much faster than using the default, and I get better uptime. Probably because they get hammered less then the default server locations.

---

### Post by durand on 2009-04-04
> **anjilslaire said:**
> Am I the only person who drills down in synaptic and specifies the closest server to my physical location? I have all my systesms pulling from the open source lab in a nearby university that's listed in the repository section of synaptic, not just "Server for the United States" in my case.

Downloads are much faster than using the default, and I get better uptime. Probably because they get hammered less then the default server locations.

I thought that that was done automatically based on the location you set for timezone and localisation in the installer. It shows the UK mirrors here and I didn't change anything since it's correct.

---

### Post by anjilslaire on 2009-04-04
That may work for the UK, but in the US, the only location for Pacific Time is Los Angeles, or somewhere in Mexico.

Seing as I'm nowhere near those locations, selecting a location manually gets far better results.

---

### Post by durand on 2009-04-04
Oh hmm, I thought that it might be something like that. I think there's a debian tool which pings the mirrors and selects the best one but I can't remember what it's called now.

---

### Post by ugm6hr on 2009-04-04
> **anjilslaire said:**
> Am I the only person who drills down in synaptic and specifies the closest server to my physical location? 

But the lpia kernel that the Dell Mini comes with doesn't have local mirrors, does it?

Besides which, Dell Ubuntu should work with the repositories they give you.  As far as I know, all the lpia kernels are on the same main server, including those for the Toshiba etc.

---

### Post by Kareeser on 2009-04-04
Come to think of it, is there a problem with selecting a normal Ubuntu mirror? The packages are the same, as is the distribution...

---

### Post by gbrainin on 2009-04-04
> **Kareeser said:**
> Not necessarily, that subdomain could simply be a CNAME record to one of dell's servers. Canonical doesn't own many of their servers... chances are, you're downloading from a mirror :)

Fair cop.  But I stand by my position on Dell's (non-Linux) support line being clueless about Linux.

---

### Post by hessczoo on 2009-04-05
> **anjilslaire said:**
> Am I the only person who drills down in synaptic and specifies the closest server to my physical location? I have all my systesms pulling from the open source lab in a nearby university that's listed in the repository section of synaptic, not just "Server for the United States" in my case.

Downloads are much faster than using the default, and I get better uptime. Probably because they get hammered less then the default server locations.

Hey, hey, I do too. Possibly because uwaterloo has a mirror and it's on campus. Every dorm has a dedicated 100Mbps port, so I can download my updates quite fast.

Dell support for Linux is brutal. I have an XPS 1530, and it's hit and miss who you get. One time, I called for a simple hard drive failure, and when I booted down so fast, the guy knew I was on Ubuntu and he actually had a conversation with me about Linux. But he was probably just a lone wolf guy.

Maybe there is a number for Linux support?

---

### Post by gbrainin on 2009-04-05
> **hessczoo said:**
> Maybe there is a number for Linux support?

It might be (866) 622-1947.  But it might be U.S. only.

---

### Post by anjilslaire on 2009-04-05
> **ugm6hr said:**
> But the lpia kernel that the Dell Mini comes with doesn't have local mirrors, does it?

Besides which, Dell Ubuntu should work with the repositories they give you.  As far as I know, all the lpia kernels are on the same main server, including those for the Toshiba etc.

I got rid of the Dell Ubuntu on all my systems pretty fast, and went with i386 *buntu all the way around.

You're probably right though, the lpia likely doesn't have many mirrors.

---

