---
title: "Running Dell diagnostics"
date: 2010-07-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mahlatst on 2010-07-12
Hi

I need to download Dell Diagnostics for my Dell Inspiron laptop, but under "operating systems" the only options I get are BIOS, Windows XP, Windows Vista - Is there a way around this for ubuntu users?

---

### Post by mikewhatever on 2010-07-13
Does Dell offers Dell Diagnostics for Ubuntu?

---

### Post by astrobob.tk on 2011-05-29
> **mahlatst said:**
> Hi

I need to download Dell Diagnostics for my Dell Inspiron laptop, but under "operating systems" the only options I get are BIOS, Windows XP, Windows Vista - Is there a way around this for ubuntu users?

It seems now there's a "Linux" in the OS list. check it out coz im my case (studio xps 1640) i can find a Diagnostics. I will attempt to install it in in a few minutes

UPDATE:
=======

I've just downloaded "CL1358A2.bin" from the Dell Drivers & Downloads (i've selected my laptop using the service tag, then selected Linux from the OS list). You are offered 2 executables: .bin (which i chose for we're using Ubuntu) & .exe (for Win, obviously).
After you download; you need to open a terminal & cd to the download directory then execute:

(make sure you replace the file name w/ the correct one you downloaded (you may use ```
ls
```& copying (w/ ctrl+shift+c))

```
chmod +x CL1358A2.bin
```

this command (above) is to change the file permission to executable. Then execute the file w/

```
./CL1358A2.bin
```

A GUI will open & its up to you now to continue ;)

P.S.: the readme file says: > The DDDP script has been tested on Dell systems running the following
Linux operating systems:

* Red Hat(R) Enterprise Linux version 3 (AS) with a kernel level of
  at least 2.6

* Red Hat Enterprise Linux version 4 (AS)

* SUSE(TM) Linux Enterprise Server version 9

* Ubuntu Linux version 7.04

The graphical execution mode of Liunx DDDP requires Python GTK at or
above version 2.6 to execute.  DDDP may execute properly on other
releases of Linux as the DDDP script is based on bash/Python/gtk/pango
software packages.

---

