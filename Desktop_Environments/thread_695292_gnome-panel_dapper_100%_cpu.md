---
title: "gnome-panel dapper 100% cpu"
date: 2008-02-12
forum: Desktop Environments
---

### Post by dgermann on 2008-02-12
Hi--

I have two desktop 6.06 boxes and one of them has developed this problem recently:

gnome-panel forces cpu usage to 100%. Running top gnome-panel's usage runs between about 80% and 95%. If I sudo kill -9 pid, it clears up the problem--for a little while. Then it comes back again.

The sequence seems to be: start Firefox, start OOo, jump to 100% cpu.

ctrl-alt f1 will sometimes give me a terminal from which I can kill the process. ctrl-alt-backspace always seems to work to give a new panel.

Often at this 100% usage, the panel flickers or wavers.

I have seen some old stuff from 2006 or so about similar problems, but nothing that I have found that works. I just used update manager to update firefox tonight, that did not resolve the problem. Also reinstalled gnome-panel and gnome-panel-data with no effect. Running gnome-session-remove gnome-panel did work; but then I had no panels for the rest of the session.

This is a production machine so I would really like for it to play nice!

It works ok on the other 6.06 box.

Any ideas?

---

### Post by Andrew Stone on 2008-02-13
Welcome to the club!  I opened a bug on this:
[http://bugzilla.gnome.org/show_bug.cgi?id=514572](http://bugzilla.gnome.org/show_bug.cgi?id=514572)

Tell me, are you running 64 bit or 32 bit versions?  I did not see this problem until I upgraded to 64 bit.  I think that a "workaround" might be to run firefox from a command line, not by clicking on the panel.  Try it and tell me if it works for you.

I pasted your post into the bug...

---

### Post by dgermann on 2008-02-14
Andrew--

Well, you could be right.

I worked with this for about 40 minutes last night and it seemed that starting firefox from a terminal allowed things to go on OK. But starting from the panel caused a lock up. I was running top in a terminal all along so I could watch it. Tried all sorts of combinations of start order and manner.

As to 64 bit, I don't know how to tell. The computer is 2-3 years old. lshw reports this  ```
*-cpu
          description: CPU
          product: Intel(R) Celeron(R) CPU 2.53GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: [blanked]
          slot: J2E1
          size: 2533MHz
          capacity: 3060MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 pni monitor ds_cpl tm2 cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: None
             size: 16KB
             capacity: 16KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: None
             size: 256KB
             capacity: 256KB
             capabilities: pipeline-burst internal varies unified

```

I am running 6.06 Dapper, if that is a clue. Have made no changes to hardware or software and as I said, have a nearly identical machine which is not exhibiting this behavior. Both are kept up to date with the update manager. The only difference there is that this machine might sit turned off for several months at a time and only then booted and updates applied en masse. Both machines are pretty plain vanilla out of the box stuff--we run mainly OOo Writer and spreadsheets. We open a lot of jpg and pdf files, too.

Also, last night I reinstalled firefox. That made no difference.

Does this give any clues to the bug or answer?

Thanks Andrew!

---

### Post by dgermann on 2008-02-14
Andrew--

Might try this too:
[http://www.justlinux.com/forum/showthread.php?t=143341&highlight=gnome-panel+%22100%25+cpu%22]("http://www.justlinux.com/forum/showthread.php?t=143341&highlight=gnome-panel+%22100%25+cpu%22")

---

### Post by dgermann on 2008-02-14
Reporting back:

OK, I tried this tonight: mv both .gnome and .gnome2. Rebooted. These directories were recreated on login, and the problem was still present.

---

