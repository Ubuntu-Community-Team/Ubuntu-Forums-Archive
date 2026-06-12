---
title: "unix system resources"
date: 2009-01-03
forum: General Help
---

### Post by sulekha on 2009-01-03
Hi all,

In the Linux file system what does the name usr , sbin stands for  ?

 some say that

 sbin means secure binary or system binary
 usr means user, unix system resources 

 can any one  give the correct explanation ?


NB: i know the purpose of usr and sbin directories, i just want to know 
    the naming thing

---

### Post by RealPSL on 2009-01-04
Interesting question with an answer here [http://www.itworld.com/nlsunix071101]("http://www.itworld.com/nlsunix071101")

It does not talk about sbin however I believe sbin stood for static binaries meaning not linked to shared objects but I could be wrong.

---

### Post by mcduck on 2009-01-04
sbin is for system binaries, binary files that are important parts of the OS itself, needed for system maintenance and/or admin tasks.

---

### Post by sulekha on 2009-01-04
in the same lines what about mnt,opt,srv and sys ?

---

### Post by mcduck on 2009-01-04
/mnt is for **mount**ing devices, either for temporary mounting of a single device directly to /mnt, or for mounting non-removable drives into their own directories under /mnt.

(/media is for removable drives)

/opt is for **optional** programs, typically you'd install things that are from outside of your distributions package sources into /opt.

/sys includes kernel, firmware and **system** related files.

I'm not sure about /srv, I believe it has something to do with running **server**s/services.

/usr is for all **user**-related files & programs. Everything normal (non-admin) users need goes here. For example you'll find binary files for most of your desktop programs, like browsers, music players etc. in /usr/bin and all system-wide installed themes in /usr/share/themes. Most of the documentation and help files for your programs are in /usr/share/doc.

You can read pretty good explanations of the directory structure here: [http://www.pathname.com/fhs/pub/fhs-2.3.html]("http://www.pathname.com/fhs/pub/fhs-2.3.html")

---

### Post by albinootje on 2009-01-04
> **sulekha said:**
> 
NB: i know the purpose of usr and sbin directories, i just want to know 
    the naming thing

Here's a little more :
[http://www.linux.org/docs/ldp/howto/HighQuality-Apps-HOWTO/fhs.html](http://www.linux.org/docs/ldp/howto/HighQuality-Apps-HOWTO/fhs.html)

---

