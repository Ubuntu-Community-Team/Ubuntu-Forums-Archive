---
title: "Why don't files saved to /home/***/desktop not appear on the actual desktop?"
date: 2009-02-02
forum: General Help
---

### Post by photon_man62 on 2009-02-02
That's my friend's question.

---

### Post by PriceChild on 2009-02-02
Try saving the files to /home/***/Desktop instead, so for example /home/pricechild/Desktop

---

### Post by photon_man62 on 2009-02-02
He did it through the file explorer, whatever it's called.

---

### Post by Mud.Knee.Havoc on 2009-02-02
> **photon_man62 said:**
> He did it through the file explorer, whatever it's called.

What the other poster is trying to say is that linux is case-sensitive.  Desktop and desktop are two different things.  If I go to /home/myname/Desktop and create an empty document, for example, it will appear immediately on my desktop.

You may be experiencing one of the following issues:
- you are not running gnome (I don't know about KDE, but other window managers often won't show desktop icons without a bit of fiddling)
- you have Nautilus set to not display desktop icons
- Nautilus is not working properly (ie. not taking care of your desktop at all)
- you are looking at the /home/yourname/desktop directory instead of /home/yourname/Desktop
- I'm sure there's something else, these are just off the top of my head

---

### Post by pwicken on 2009-02-02
If your friend is running his session i Polish I guess his /home/USER/Desktop is replaced by /home/USER/Biurko or whatever Desktop is in Polish. I am not sure, but something like "Biurko" comes to mind.

---

### Post by photon_man62 on 2009-02-05
> **pwicken said:**
> If your friend is running his session i Polish I guess his /home/USER/Desktop is replaced by /home/USER/Biurko or whatever Desktop is in Polish. I am not sure, but something like "Biurko" comes to mind.

It's "Pulpit".

I meant he saved the file using the FILE EXPLORER, not by typing in text.

Anyways, it doesn't matter now, since he switched to Ubuntu and doesn't have this problem anymore.

---

### Post by PriceChild on 2009-02-06
If you ask a question here we will assume Ubuntu. That causes problems.

---

### Post by cornsay on 2010-05-20
I was wondering this myself for a while, after switching to Kubuntu 10.04 from Ubuntu... here's the solution. Simple, but worth putting here since this thread comes up high on the search results for this question...

1. right-click on the desktop and select "desktop activity" from the context menu.
2. Select "activity" from the tabs on the left.
3. Change the "type" in the dropdown from desktop view to folder view.
4. You may also have to change the location under the location tab (which will appear once you've done 3).

---

