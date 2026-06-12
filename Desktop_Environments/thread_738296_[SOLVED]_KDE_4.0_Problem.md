---
title: "[SOLVED] KDE 4.0 Problem"
date: 2008-03-28
forum: Desktop Environments
---

### Post by cptInsane0 on 2008-03-28
I recently acquired a Dell inspiron 1150, so I went ahead and loaded kubuntu with kde 4.0.  Figuring the intel video card could at least handle some effects, I toggled allow desktop effects. Now whenever I log in, all I get is a black screen where I can see my mouse cursor. Is there a keyboard command to shut off those desktop effects? Also, if I could just log into the console and fix it, that's doable too.


Another thing, I don't get any sound. I know the sound on this thing works, as it worked in windows before I wiped the hard drive.


Would I be better off just loading regular kubuntu without kde4? I don't especially want to do that, since I am not  a big fan of KDE, but 4 looks awesome.  Also I use gnome on several pc's and am tired of it.

---

### Post by MONODA on 2008-03-28
have you tried xfce ;)

---

### Post by cptInsane0 on 2008-03-28
Yes, I install it on every older pc I encounter.

---

### Post by der_joachim on 2008-03-29
As for the black screen thing, I haven't solved it yet, but I found a workaround. Either let KDE4 open an existing session or open the task manager by hitting Ctrl+Esc and closing it again. You'll have your desktop.
I haven't searched Launchpad yet, so I do not yot know whether there is a better workaround. 
[Edit]: [This bug report]("https://bugs.launchpad.net/ubuntu/+source/kdebase-kde4/+bug/182288") may be relevant.

As for your hardware problems: [this page]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1150") may help you further along.

---

### Post by benerivo on 2008-03-29
> **cptInsane0 said:**
> I toggled allow desktop effects. Now whenever I log in, all I get is a black screen where I can see my mouse cursor...Another thing, I don't get any sound. I know the sound on this thing works, as it worked in windows before I wiped the hard drive.

I've had very similar problems. When you log in, have you tried clicking around the screen, especially around where the taskbar would be? When I did this, I slowly brought my desktop back in to view, as if it were some sort of graphical glitch. I have also had problems with no sound from kde4 when it is the only desktop installed (from a command line minimal kde4 installation). The only thing i could do was to install another desktop such as as kde3 or gnome and when the sound is working in those then i can uninstall them, and then kde4 is fine.

---

### Post by cptInsane0 on 2008-03-29
Weird. I went ahead and installed normal kubuntu gutsy. Should I just install kde4 on top of that, then delete kde3? I can probably do without the desktop effects for the moment, but kde4 looks a lot better than kde3, so I would prefer it.

---

### Post by benerivo on 2008-03-29
> **cptInsane0 said:**
> Should I just install kde4 on top of that, then delete kde3?
Yes, it would be fine to install another desktop and delete the other one. You will have to decide which repository you want to use (either gutsy's or [http://ppa.launchpad.net/kubuntu-members-kde4]("http://www.kubuntu.org/announcements/kde-4.0.2.php") or install kubuntu hardy beta). Then you would have to carefully delete the kde3 packages making sure you don't delete kde4 in the process (using synaptic package manager is probably best for this). Of course kubuntu hardy kde4 release candidate is only about three weeks off so that will be the best way to get it.

---

### Post by cptInsane0 on 2008-03-29
If they will have a fairly stable version in about three weeks, I should probably just wait. I think I can deal with kde3 not being as cool for the time being.

---

### Post by munch3 on 2008-03-29
you can run a terminal session or safe-mode session...

---

### Post by NightwishFan on 2008-03-29
I am semi obsessive compulsive about the way my os works (thats why i like linux so much) I hated how when I shut down the Kubuntu beta it came up with like 5-6 error prompts then shut down. KDE4 I do not like, but I do wish to use it in the future. I am sure they can pull off a Stable KDE4 hardy in a month though. Some stuff was much improved in only a few days.

---

