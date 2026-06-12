---
title: "Screen  does not refresh"
date: 2009-03-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Broady on 2009-03-07
Hi,
If i open a new tab in firefox then the new page loads but screen does not refresh to show the  new tab .If i click somewhere on the screen then the new page is seen.Similarly when i scroll down using cursor through some text (say in open office)then also the old text stays and when i click somewhere on the screen the new text is seen.

Specs:-
Dell Inspiron 1520
2 gb ram
NVIDIA 8400 graphics card(it is working fine)
Ubuntu 8.04 hardy

Can somebody help me out to set this right...
Broady

---

### Post by sdennie on 2009-03-07
What nvidia driver version are you using?  You can find this information with:

```

nvidia-settings -q NvidiaDriverVersion

```

Also, are you running compiz (Desktop Effects).

---

### Post by Broady on 2009-03-07
Hi
the version is :
 Attribute 'NvidiaDriverVersion' (satish-laptop:0.0): 180.22   

Yes i am running compiz(system monitor shows it as "compiz.real")

---

### Post by sdennie on 2009-03-07
This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904).  Nvidia claims it's a fundamental problem with the design of compiz and the X server.  There are workarounds that partially or mostly fix it but, there is no "good" fix.

---

