---
title: "Multiple Desktops with independent ~/Desktop folders"
date: 2008-07-21
forum: Desktop Environments
---

### Post by uraldinho on 2008-07-21
Hi, 

someone asked me a question today, and the question is: "I would like to have multiple desktops that are completely independent from each other, and each desktop has different icons on it. How can I configure my linux to do that?". I thought of the standard multiple desktops present in Gnome and KDE, but they all share ~/Desktop folder and therefore the same icons on all desktops. 

First of all, is there a program that does what he wants? 

My logic is that it is possible to have different background images for each desktop, so it might be possible to change the Desktop folder for each desktop so that we can have different icons on each desktop. Is this possible? 

I could think of a more complex solution, but this might be unnecessarily complicating things. The solution I came up with was to create a new Gnome or KDE "session type", like some of us do for Compiz. This is something I've done in the past and I can do it again. However, the new session type will have a Desktop folder that points to ~/Desktop by default. 

Let's say I have a new session type and I called it KDE2. How can I change the Desktop folder for this session without affecting the normal KDE session? 

I have used multiple monitors in the past, and I know the display manager creates a second Desktop folder, ie Desktop1, for the second monitor. So, it is possible to change the default location for the desktop folder. 

Any input? 

Thanks

---

### Post by smartboyathome on 2008-07-21
I remember seeing a script that did what he wants, but it was buggy and slow, and only worked for KDE. It isn't able to do this now because the desktop manager (usually the file manager) has to be restarted with the new desktop when you switch, and especially with the case of Nautilus in gnome, can take a while to come up again.

EDIT: The "new session" you are talking about seems to be just another user session. Just link everything from one user to another BUT the desktop folder.

---

### Post by uraldinho on 2008-07-22
Thanks, 

how can I change the default desktop folder in KDE or Gnome? 

I did a bit of searching last night, but I couldn't find the answer. 

regards

---

### Post by Mgiacchetti on 2008-08-13
a vid of [the concept]("http://www.youtube.com/watch?v=oGXYLdZEf2c") (note concept only not actually implemented)

---

### Post by meburke on 2008-08-13
I have done this on other systems, mostly Unix, so I don't know if this will work without you doing some research.

If the user is willing to switch between terminal sessions using the ALT-CTL sequence, it is simply a matter of using different window managers on each login.

If the user is addicted to a specific window manager,then (what I did) was read a different configuration file for each login session. This required a fairly extensive edit to the .profile. This still requires switching between tty sessions.

You could configure the system to run a virt session that has the disk mounted. (This is a hassle, I just tried it. I had to re-configure the hard drive so that the /home directory was on a separate volume. Only do this if the user desperately needs the convenience to stream line the workload.)

I am not aware of anyway to customize individual workspaces, although I suppose it could be done by someone ambitious enough to hack Gnome.

KDE has an extensive list of things that you can do to your desktop from a configuration file, but I don't know if you can change individual workspaces.

---

