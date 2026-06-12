---
title: "Burning an ISO file onto a CD-RW"
date: 2009-04-13
forum: General Help
---

### Post by superbiskit on 2009-04-13
This is going to look like a really dumb noobie question, <sigh!>.

I was using Ubuntu 8.10, quite happily. I've been using Ubuntu for about 5 years now.

When Jaunty got near ready-to-go (Beginning of April), I tried
```
 aptitude dist-upgrade -t=jaunty 
```

That turned my machine into a doorstop.  No, I exaggerate grossly! It's just that when I try to log into Gnome desktop, the machine thinks for a while with a black screen, then reboots.

SO! Maybe dist-upgrade isn't so safe.

I got the iso image from a mirror (from the console, of course).
Then I went looking for the command to write the iso onto a real disk.  That wound up with 'wodim'.
Every time I try to write a disk, everything goes fine until the end.  Then wodim tries to 'fixate' (finalize?!) the disk and tells me that is not a legal function on segment 0.

If anyone has gotten this to work, [bold]please[/bold] advise: what combination of options is appropriate for writing an iso image filesystem onto the real media?

From the amount of witching and moaning on the forum about wodim, I suppose that could easily be the problem.  I plan to pull down the original cdrtools package and try with cdrecord, which worked for me in the past; but the secret incantation (options) is still a question.

---

### Post by lisati on 2009-04-13
You might find some tips here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

