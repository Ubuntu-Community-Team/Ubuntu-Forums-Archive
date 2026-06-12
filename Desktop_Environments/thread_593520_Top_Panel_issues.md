---
title: "Top Panel issues"
date: 2007-10-27
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2007-10-27
Hello,

Got an issue with the top panel in Ubuntu.  I have unticked the 'Expand' field so that it bunches up in the top/middle of the screen.  Upon reboot, the top panel has defaulted to the bottom/middle.  I then attempt to go and change its Orientation to 'Top' again using the panels properties, but as soon as I select 'Top', it changes back to 'Bottom' and will not go to the top.  I have to check the 'Expand' field, then select 'Top'.  I can then uncheck 'Expand' and it will be centered in the middles as I want.  Restart and I have to repeat the process all over.

Any ideas on what maybe causing the issue?   It is a clean install of Gutsy 7.10 BTW.

Thanks,

---

### Post by The Pinny Parlour on 2007-10-27
BUMP

I'm about to submit this as a bug and would like some comment please.

Thanks

---

### Post by The Pinny Parlour on 2007-11-02
Top Panel is really badly justified to the right and no amount of resets/restarts seems to fix it. It all started when I tried to remove the tick from 'Expand' in the top panel properties. A restart rendered the top panel to the bottom, and ever since then I can't get it non-expanded and centered. It's the biggest visual annoyance so far (that doesn't involve X). I wish I knew how to fix it.

---

### Post by The Pinny Parlour on 2007-11-17
[SIZE="7"]BUMP[/SIZE]

When will this serious Panel issues be fixed?   I dislike having to enter the panel properties and change it upon EVERY boot of Ubuntu.

---

### Post by Ebuntor on 2008-01-26
Hi,

I know this is a somewhat old thread but I think I have the solution to your problem.
I had the same problem and what I did was as soon as I started up, while the panel was at the bottom I created a second panel at the top. I moved all the icons to the new panel and deleted the old one. Worked for me and it stays on top.

Hope that helps. :)

---

### Post by anaconda on 2008-03-05
yes.. an old thread indeed, (been searching a solution to a similar problem)
but since the search gives this thread, and the same problem still exist even in hardy I think this thread is still "current"

A better solution would be to go to gconf-editor (type gconf-editor in terminal) and from there go to:
Apps>panel>toplevels

and select the correct panel. eg mine would be "top_panel_screen_0" (yours may have a different name)
and set the values of "x", "x-centered" and "Y" to the desired values.

---

