---
title: "maxima -- wxmaxima loses socket connection"
date: 2007-06-06
forum: Education &amp; Science
---

### Post by silbar on 2007-06-06
Greetings,

In looking for a substitute for Mathematica or Maple (which I can and do use at work) on my home machine, someone on this forum suggested installing maxima and its gui interface wxmaxima.  The former works but is not as nice and convenient as wxmaxima might be.  However, as soon as I do something in the wxmaxima window, such as "1+2;", I get the error message

   CLIENT: Lost socket connection ...Restart maxima with 'Maxima->Restart maxima'.

No matter what I try to do.  Is this a known problem?  Is there perhaps something that synaptic ought to have installed but didn't?

    Dick Silbar
    Los Alamos

---

### Post by WW on 2007-06-07
Yes, it is a known problem: [https://launchpad.net/ubuntu/+source/wxmaxima/+bug/43150/+index](https://launchpad.net/ubuntu/+source/wxmaxima/+bug/43150/+index)

If you add **dapper-updates** to your repositories, you should be able to install the fixed version of maxima.

---

### Post by silbar on 2007-06-07
> **WW said:**
> Yes, it is a known problem: [https://launchpad.net/ubuntu/+source/wxmaxima/+bug/43150/+index](https://launchpad.net/ubuntu/+source/wxmaxima/+bug/43150/+index)

If you add **dapper-updates** to your repositories, you should be able to install the fixed version of maxima.

Thanks, WW.  But I'm confused, as my /etc/apt/sources.list file already had these lines:

[INDENT]## Major bug fix updates produced after the final release of the
## distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
[/INDENT]

So, are wxMaxima 0.6.4 and maxima 5.9.2 (which I installed on Tuesday) not the latest versions?

    Dick Silbar

---

### Post by WW on 2007-06-07
You don't have the universe and multiverse components for dapper-updates in sources.list.  Change those two lines to
```

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

```
and then do an update, either with the command
```

$ sudo apt-get update

```
or by hitting the **Reload** button in Synaptic.

---

