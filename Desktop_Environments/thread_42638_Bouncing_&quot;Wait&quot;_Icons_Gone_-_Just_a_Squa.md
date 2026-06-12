---
title: "Bouncing &quot;Wait&quot; Icons Gone - Just a Square"
date: 2005-06-18
forum: Desktop Environments
---

### Post by polo_step on 2005-06-18
I have no idea why, but all the little bouncing, pulsating "wait" icons that trail the cursor while the programs are loading have diappeared and there's just a colored square there now.

Not earthshaking, but it's annoying to look at.

Any idea what happened?

Thanks...

---

### Post by SzymonDrejewicz on 2005-06-19
In english UI you need to:
1) open 'Control Center'
2) select 'Appearance & Themes' > 'Launch Feedback' (a red-orange rocket icon)
3) set 'Bouncing Cursor' in 'Busy Cursor' section.

---

### Post by polo_step on 2005-06-20
Thanks!

---

### Post by zer0cubed on 2006-02-19
I've been searching for an answer to this issue.  I think there's something bigger happening here.  Changing the Launch Feedback options is like sweeping dirt under the rug.  My busy cursor was working properly before, but I'm not sure when I started getting the square.

Also, I am pretty new to the Kubuntu scene.  For the first time, as of last night, I've rid myself of Windows.  That said, yesterday was the first time I've used Kopete.  I didn't know what to expect to see when I ran it, but I noticed my protocol icon and the status icon of each of my buddies was a solid square, like the busy cursor.  At first I thought maybe that's just the way it's supposed to look, but after looking at some screenshots online of Kopete, I'm not so sure.  

I've attached a screenshot of Kopete.  Do you think this might be a graphics driver issue?  I have been dorking around with my xorg.conf to get twinview working.  It may have been around that time when these boxes started showing up.  Any help is appreciated.

---

### Post by zer0cubed on 2006-02-19
By the way, I'm running Kubuntu Breezy, not Hoary.

---

### Post by zer0cubed on 2006-02-20
I figured out the problem.  

Under Settings, Appearance and Themes, Icons, Advanced tab:

I had dorked around with the Toolbar icons size, making them too small.  Setting it back to the defaults fixed the problem with both the busy cursor and the icons in Kopete.  Easy fix.

---

