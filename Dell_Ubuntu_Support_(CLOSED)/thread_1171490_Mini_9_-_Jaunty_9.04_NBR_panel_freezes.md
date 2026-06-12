---
title: "Mini 9 - Jaunty 9.04 NBR panel freezes"
date: 2009-05-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ugm6hr on 2009-05-27
Has anyone else had problems with the Gnome panel crashing on their Mini 9 with NBR 9.04?

I have had it crash 3 times now, and at least 2 of these were related to the Evolution calendar applet.

Unfortunately, with gnome panel out of action, I have had to Ctrl-Alt-PrtScrn R-E-I-S-U-B to reset, since logging out seems impossible.

This may be a residual problem, since I copied back my /home directory from the original Dell 8.04 installation; presumably 9.04 doesn't like this...

But just curious to hear from others.  In the meantime, I'll stop using the calendar applet.

---

### Post by Blue Sassley on 2009-05-27
With a clean install on my Mini 9 (from Winblows 7 Beta) I have not had any issues at all. The only real big problem I had was my BlueTooth adapter not working but I fixed that by installing aircraft-manager 12.1 and enabling the adapter.

[http://ubuntuforums.org/showthread.php?t=1161536](http://ubuntuforums.org/showthread.php?t=1161536)

Maybe its something that came across on your home directory?

Blue

---

### Post by ugm6hr on 2009-05-28
> **Blue Sassley said:**
> Maybe its something that came across on your home directory?

That was my first thought too...

I will try removing the .gnmome2 and .gconf directories, to see if it helps.

Unfortunately, I can't remove the .evolution directory, since I need my address book etc.

---

### Post by tyroeternal on 2009-05-28
@ugm6hr is your calendar tied to any web based calendars?  If so you may be having the same problems as this thread which was solved at the end: [http://ubuntuforums.org/showthread.php?t=860753](http://ubuntuforums.org/showthread.php?t=860753)

---

### Post by ugm6hr on 2009-05-29
> **tyroeternal said:**
> @ugm6hr is your calendar tied to any web based calendars?  If so you may be having the same problems as this thread which was solved at the end: [http://ubuntuforums.org/showthread.php?t=860753](http://ubuntuforums.org/showthread.php?t=860753)

This sounds like it! Thanks.  I use Google Calendars too.

Shame I didn't search specificially for calendar applet problems - sorry everyone...

However, this basically makes either the calendar applet or G Calendar on Evolution unusable; not exactly ideal.  Has a bug been submitted?

I changed from T-bird+Lightning to Evolution when I got my Mini 9, since I wanted to avoid unnecessary installation of applications on my 8GB HD.  I might have to reconsider that position now, since having a calendar (even without the diary function) on the panel is invaluable.

---

### Post by tyroeternal on 2009-05-29
It looked like if you open the calendar in evolution before trying to use the applet, it works fine.  Because it is a connection problem, evolution initializes the connection correctly so from then on the applet works fine, even after evolution is closed.

---

### Post by ugm6hr on 2009-05-29
> **tyroeternal said:**
> It looked like if you open the calendar in evolution before trying to use the applet, it works fine.  Because it is a connection problem, evolution initializes the connection correctly so from then on the applet works fine, even after evolution is closed.

And this is perhaps why it has not happened more often to me.

I may tolerate it for now; it does remain a significant bug in Gnome integration as far as I am concerned.

---

### Post by tyroeternal on 2009-05-29
It most definitely is.  Is there a bug filed in launchpad for it already?

---

### Post by ugm6hr on 2009-05-29
> **tyroeternal said:**
> It most definitely is.  Is there a bug filed in launchpad for it already?

I'll go look this weekend...  Should be doing a job application rather than playing on the forum now!

---

