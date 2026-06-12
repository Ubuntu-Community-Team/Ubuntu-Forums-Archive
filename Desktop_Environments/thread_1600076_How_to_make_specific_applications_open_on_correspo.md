---
title: "How to make specific applications open on corresponding workspaces?"
date: 2010-10-18
forum: Desktop Environments
---

### Post by vaul on 2010-10-18
I have a lot of application scheduled to load at startup (GoldenDict, Tomboy Notes, Evolution Mail, Liferea, etc.) and I'd like some of them to appear on the workspaces different from the default.

I have Ubuntu 10.10 with Gnome and Compiz effects.

Is there a way to do this without a lot of mess?

---

### Post by Bonster on 2010-10-18
Use Compiz Place Windows

---

### Post by vaul on 2010-10-18
I took a look at it and it's quite strange and buggy, for instance, "Grab" dialogue do not grab anything and you have to fill all details yourself.

And worst, it do not work at all in the start up: all windows are in the one big messy pile on the first workspace.

Anyway, thank you for help.

P.S. I don't think there is a way to make it sort windows in the boot up as well? Anyway, I have filled a bug reports about it.

---

### Post by Jim Danner on 2010-10-29
It looks a bit messy, but I think you can get it to work.

I assume from your description that you have gone into the CompizConfig Settings Manager, into the *Place Windows* section, into the *Fixed Window Placement* tab, and you have clicked to add a new item at *Windows with fixed viewport* and clicked on the green + button.

Before you hit the 'Grab' button, select the type *Window Name* from the dropdown list. After hitting 'Grab', you have to click somewhere in the window of an application (*not* on its title bar, unintuitively). Then the name appears. Copy it, hit 'Add', and paste it behind *name=*. Select the viewport where you want it to open by default and close the dialog box.

All of this requires, apparently, that the *Regex Matching* module of CompizConfig is also enabled.

---

### Post by vaul on 2010-10-30
Yes, thank you, but I figured that out myself.

Problem still remains — it do not place windows where they should belong on the system startup, I guess that's because a lot of things happen too fast on the login.

That's what I opened a bug about.

---

### Post by Jim Danner on 2010-10-31
> **vaul said:**
> 
Problem still remains — it do not place windows where they should belong on the system startup, I guess that's because a lot of things happen too fast on the login.You could install [wmctrl]("http://linux.die.net/man/1/wmctrl") and try to work with that: as a final startup command after the launch of all those programs, you'd have it run a list of commands like
```
 wmctrl -r firefox -e 0,1280,0,-1,-1

```
(this moves the Firefox window to the second viewport if your screen is 1280 pixels wide).

---

