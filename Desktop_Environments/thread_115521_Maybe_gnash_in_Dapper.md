---
title: "Maybe gnash in Dapper?"
date: 2006-01-10
forum: Desktop Environments
---

### Post by mattisking on 2006-01-10
Well everyone seems to be talking about, so might as well start the topic here in Dapper. What about [Gnash?]("http://www.gnu.org/software/gnash/#downloading") Maybe that could be the default Firefox/Flash combination without using Macromedia's component. I love Firefox and Ubuntu and Flash... but they have never loved each other on this machine... ever. I have Flash completely removed on this machine. Every update that's ever released on here as left me with a frozen browser window. I miss Flash. Maybe gnash could fill the void?

---

### Post by BoyOfDestiny on 2006-01-10
[QUOTE=mattisking]Well everyone seems to be talking about, so might as well start the topic here in Dapper. What about [Gnash?]("http://www.gnu.org/software/gnash/#downloading") Maybe that could be the default Firefox/Flash combination without using Macromedia's component. I love Firefox and Ubuntu and Flash... but they have never loved each other on this machine... ever. I have Flash completely removed on this machine. Every update that's ever released on here as left me with a frozen browser window. I miss Flash. Maybe gnash could fill the void?[/QUOTE]

Sounds good to me!

Has anyone gotten the cvs to compile? 
Also, can anyone tell me if the browser plugin offers a "stop" option... That would be a sweet feature... :)

---

### Post by mattisking on 2006-01-10
So far I haven't been able to compile from CVS. It goes a long way and dies while building the plugin. The website says it's under "heavy" development so maybe tomorrow or the next day...

---

### Post by GameGod on 2006-01-10
This would definitely be nice to have in the repos... :)

---

### Post by drizek on 2006-01-11
[QUOTE=GameGod]This would definitely be nice to have in the repos... :)[/QUOTE]

hint... hint...

---

### Post by Burgundavia on 2006-01-11
Likely in Universe, unlikely in main and shipped by default. Think dapper+1.

Corey

---

### Post by GameGod on 2006-01-11
[QUOTE=Burgundavia]Likely in Universe, unlikely in main and shipped by default. Think dapper+1.
[/QUOTE]

Good enough for me. :)

---

### Post by kaamos on 2006-01-11
Got it installed in breezy from the tarball. Had to do a few symlinks to get it running. ATM does not play stuff well at all, but the project certainly has great potential! In my opinion though it's not far enough yet to be shipped with dapper.

---

### Post by mattisking on 2006-01-12
[QUOTE=kaamos]Got it installed in breezy from the tarball. Had to do a few symlinks to get it running. ATM does not play stuff well at all, but the project certainly has great potential! In my opinion though it's not far enough yet to be shipped with dapper.[/QUOTE]
I got the latest from CVS today and can now build. However, I get this:
   open /dev/sequencer: No such file or directory
when I run it from a terminal. Is this what you meant with the symlink? Could you clue me in please?

---

### Post by Burgundavia on 2006-01-12
The "open /dev/sequencer/" should be a harmelss cosmetic bug. Most programs that directly access sound using dmix do that.

Corey

---

### Post by mattisking on 2006-01-13
[QUOTE=Burgundavia]The "open /dev/sequencer/" should be a harmelss cosmetic bug. Most programs that directly access sound using dmix do that.

Corey[/QUOTE]
Eh, I should have been more clear... It builds, installs, and runs just fine. The plugin is even in the right place for Firefox... but when used, nothing happens at all. The files included under testsuite directory don't even play. From a terminal the window pops up but nothing plays in it. 

I just thought maybe the /dev/sequencer thing might be a symptom.

---

### Post by mattisking on 2006-01-17
Actually... now it IS working for some flash files but sporadically, it's slow to start, and while it's working as I just described from the terminal, I've yet to encounter a flash site that worked... (the Firefox plugin isn't working for me at all).

---

### Post by huwshimi on 2006-05-31
I jusst compiled Gnash on amd64 and it seems to be working in firefox. I don't think it's working perfectly, but who cares - it's such a big step forward.

Hrm... maybe no sound, but I have a weird soundcard anyway so maybe it's not gnash's fault.

---

### Post by apejcic on 2006-05-31
Gnash is migrating to gstreamer 0.10, that is why there is no sound.... wait a month or two.

---

### Post by bruce89 on 2006-05-31
[QUOTE=apejcic]wait a month or two.[/QUOTE]
Or until October for Edgy!

---

