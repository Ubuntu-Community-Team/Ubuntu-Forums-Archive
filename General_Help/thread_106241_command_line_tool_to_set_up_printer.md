---
title: "command line tool to set up printer"
date: 2005-12-20
forum: General Help
---

### Post by Darren Crotchett on 2005-12-20
Is there a command line utility in *buntu for setting up a printer?  

I know how to do it in kde, gnome and probably the cups web interface.  I'm just looking for a command line utility because this particular box has been set up as a server.  I don't want to install X if I can avoid it.  And, I've never had much luck with the cups web tool.  However, if there is no command line tool, the cups interface is what I plan to use.

TIA,
Darren

---

### Post by BathroomNinja on 2005-12-20
Check out this link:
[http://www.togaware.com/linux/survivor/CUPS_Command.shtml](http://www.togaware.com/linux/survivor/CUPS_Command.shtml)

I think that might be what you're looking for.

---

### Post by macgyver2 on 2005-12-20
Also, I've set up printers in cups through lynx several times in the past.  Technically, not a commandline solution, but IMO it works rather well for machines without X.

---

### Post by Darren Crotchett on 2005-12-20
Thanks all.  I guess the short answer is, "No.".  There is not one.

I appreciate your replies, though.

Darren

---

### Post by BathroomNinja on 2005-12-20
[QUOTE=Darren Crotchett]Thanks all.  I guess the short answer is, "No.".  There is not one.

I appreciate your replies, though.

Darren[/QUOTE]


Well, CUPS works from the command line.  you can install cups and use the commands from that link to do all the work from the command line.

---

### Post by Darren Crotchett on 2005-12-20
[QUOTE=BathroomNinja]Well, CUPS works from the command line.  you can install cups and use the commands from that link to do all the work from the command line.[/QUOTE]

Well, yes.  That is true.  But, I was looking for a "wizard" type of tool.  The last time (about 2 years ago) that I used the cups interface was on my FreeBSD box.  I just didn't have good luck with it.  I ended up using apsfilter.  For all of my Linux boxes, I just used kprinter to find it.  Anyway, the point is that I've been spoiled with kprinter.  And, I have bad memories of the cups interface.  So, I thought I would see if *buntu had a "wizard" type utility.  They don't.  That's OK.  I'll just do the command line cups thing, connect to the web interface from another box that has X (like this one) or I'll do as the other poster suggested and just use links or lynx.

---

### Post by -DarkMind- on 2005-12-20
install cups and configure via web, open links (browser in text mode) and go to [http://localhost:631](http://localhost:631)

---

