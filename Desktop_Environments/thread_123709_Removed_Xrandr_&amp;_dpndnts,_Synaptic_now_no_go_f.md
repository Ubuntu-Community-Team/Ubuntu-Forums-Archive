---
title: "Removed Xrandr &amp; dpndnts, Synaptic now no go: fear 2 shut down"
date: 2006-01-30
forum: Desktop Environments
---

### Post by PeteAJ on 2006-01-30
I thought I had loaded it (XrandR) myself (to mirror screen[near mirror]) but was frustrated with XrandR as it was seeming to prevent my changing the screen resolution & had since moved the monitor away from the mirror (no I didn't get that going & yes very newb like diltantism as yes, very newb)

I didn't feel comfortable doing it with all the packages it wanted to take with it but thought I'd be able to reload it should there be any trouble.

**:???: **

Then after and trying to return to Synaptic it reports

> Failed to execute child process GKSUDO - "no file or directory"

Real sorry to bother you all and extend my thanks in advance for your time in consideration and looking even, and wish you all the treasures of life for your helping myself and/or others using open source technology.
With kind regards, Pete AJ

---

### Post by RAOF on 2006-01-30
You should be able to fix this from a terminal: apt-get (or aptitude) is the command-line version of Synaptic, and that should work.  You can get to a terminal from "Applications->Accessories->Terminal"

Run "sudo apt-get install ubuntu-desktop".  That should install everything the default desktop has installed, so Synaptic should work.

---

### Post by PeteAJ on 2006-01-30
I thought I lost this post from Quick reply, when it needed me to log on, then returned me to error page, message redundant by next message made.

Sorry for the litter I couldn't find where to delete post.

---

### Post by PeteAJ on 2006-01-30
Thanks fellow NSWelshian ROAF, You saved the day. Tha t worked nicely.

Though in my angst I previously had used APt-get to reload XrandR hoping it would reinstall all the stuff that it had insisted that go with it when uninstalling. I didn't so guess it is a feature of Synaptic to work dependencies.
:-k ([I]  SOOO, would using apt-get uninstall xrandr be appropriate? I wonder??)
[/I]
So the problem that led to the problem
> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

is still a problem, :( 

But not so critical as I am getting used to pushing enlarged desktop ctrl+shft+[+] around.

Thank ROAF, and Ubuntu forums and those members (like ROAF) that make it.

---

