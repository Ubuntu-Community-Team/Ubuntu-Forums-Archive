---
title: "Change Display Manager"
date: 2008-05-16
forum: Desktop Environments
---

### Post by celticbhoy on 2008-05-16
Need a little help here, I have a system where Gnome is the default window manager, but I also have KDE3 & Enlightenment installed also. I can switch between the three options without any problems, but yesterday I downloaded KDE4 and I now have a small problem. During KDE4 setup I was asked which display manager to use, and I selected KDE thinking the question would only affect KDE4, but it has set the display manager for all sessions. I would like to return to GDM how do I go about this ???

---

### Post by Patb on 2008-05-16
Celtic, when I uninstall and then reinstall GDM using Synaptic, it gives me a choice during reinstall as to which DM I want to use as the default.  

Cheers, Pat.

---

### Post by Xiong Chiamiov on 2008-05-17
The simpler way to do it is:
```

sudo dpkg-reconfigure gdm

```
You can optionally replace gdm with kdm or kdm-kde4.  Dpkg-reconfigure re-runs whatever configuration happens when you install a package, without having to actually reinstall it.

---

### Post by celticbhoy on 2008-05-17
Thanx guys back to where I was. If I can just open this up a little, as I say I also use Enlightenment & KDE3, will KDE4 also run on the same system, or will it not sit with the other window managers?

---

### Post by Xiong Chiamiov on 2008-05-17
Yes, you can run KDE4 and KDE3.5 simultaneously.  I have both of them installed, though I can't get KDE4 to work very well at all (not that it matters - I hate it anyways).  It'll be just the same as having both KDE and GNOME installed, since KDE4 uses different packages.

---

### Post by celticbhoy on 2008-05-17
I know it works as it is there, but If I run Gnome my settings dont affect KDE3 or Enlightentment, yet they seem to affect KDE4. By that I mean I autoload screenlets under Gnome, they dont show or load under KDE3 or Enlightenemnt (the way I want it to be), but when I start a session for KDE4 all my gnome autostarts load. Is there a way around this so that KDE4 has its ouw sesion startup rules?

---

### Post by Xiong Chiamiov on 2008-05-17
That's rather odd behavior; I'm not sure what's causing that.  Do you know how GNOME's autostarts are configured (eg, in a folder somewhere in your home directory)?

---

### Post by celticbhoy on 2008-05-17
I'm not really that on the ball or technical I'm affraid. Must say though looking through the forum's you are a busy boy helping others.

---

### Post by Xiong Chiamiov on 2008-05-17
> **celticbhoy said:**
> I'm not really that on the ball or technical I'm affraid. Must say though looking through the forum's you are a busy boy helping others.
A busy boy, perhaps.  Knowledgeable, not as much.  I enjoy helping others, and the Ubuntu forums have taken the place of random cleanup tasks on Wikipedia, since I feel this has a more direct impact.  Besides, sleeping isn't really that important, right?

---

### Post by yoda2031 on 2008-05-17
I'm in the same position as Xiong Chiamiov - not very knowledgable but keen to be helpful!!

Ok, do you use compiz-fusion then I take it?  If so, is it KDE4 and Gnome you use it for or all your environments?  I thought screenlets were a compiz thing, not a gnome thing...

---

### Post by celticbhoy on 2008-05-17
I do use compiz, but compiz and screenlets are both started on my gnome autostart list. Neither of these apps start if I select enlightenment or KDE4 as my sesion, so does that mean that KDE4 will only ever shar a startup list with Gnome, or can they both have there own autostart apps?

---

