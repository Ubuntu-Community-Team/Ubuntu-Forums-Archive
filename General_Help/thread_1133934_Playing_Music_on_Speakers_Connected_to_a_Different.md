---
title: "Playing Music on Speakers Connected to a Different Machine"
date: 2009-04-23
forum: General Help
---

### Post by hwttdz on 2009-04-23
My machine doesn't have any speakers however my officemate's does.  It'd be nice to play music when I'm the only one in office.  Is there any way to play music using those speakers?  It'd be best if I could use rhythmbox on my machine, however I'll certainly consider other alternatives.

---

### Post by Kareeser on 2009-04-23
X forwarding through SSH to your friend's machine.

You'll need a login to this computer, though.

```

ssh [machine2] -X
rhythmbox &

```

Rhythmbox should open up on your screen, running on his computer.

---

### Post by hwttdz on 2009-04-23
I'll try it as soon as they stop back in.  Devious uses about blasting dominican music in retaliation at my neighbors while I'm not there come springing to mind.

---

### Post by hwttdz on 2009-04-23
So I:
1) set up an account
2) scp'd some music from my directory on my machine to my directory on that machine
3) started up rhythmbox

Rhythmbox does nothing.  Well, it did successfully import my music from that machine,  but it hangs if I start to play anything.  Any suggestions?

My plan is to try both mplayer and mpg123, and possibly mpg321 (if all of these exist).  Of course upgrading to 9.04 prevents me from trying too much right now (the upgrade is not going quickly).

---

### Post by Kareeser on 2009-04-26
Weird...

Try running Rhythmbox on the host machine. Does it play music properly?

mpg321 might be an easier way to go about it... small and nimble program it is.

---

