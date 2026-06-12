---
title: "FvwmConsole not working in Lubuntu 18.10"
date: 2018-11-09
forum: Desktop Environments
---

### Post by jakesaddress on 2018-11-09
I've just finished a fresh install of Lubuntu 18.10, and then installed FVWM.  When I log into FVWM, everything comes up fine, but the FvwmConsole won't appear.  It doesn't appear to want to use QTerminal; if I change to "Module FvwmConsole -terminal xterm", it works fine.

I've obviously worked around the issue myself, but am posting this so hopefully it can be fixed properly.  :-)

Cheers,

John Moe

---

### Post by him610 on 2018-11-11
Their home webpage [http://www.fvwm.org/]("http://www.fvwm.org/") states >  Support is excellent. You may have better luck inquiring there.

---

### Post by TheFu on 2018-11-11
Does qterminal work fine under Lubuntu's default DE?
If so, then contacting the fvwm team makes sense.
If not, then the LXQt guys need to know.

If you run Qterminnal from an xterm, how does that go?  Works?  Errors?  The point is to see the text output which I'd guess will complain about some missing or wrong dependencies.

---

### Post by jakesaddress on 2018-11-15
him610 Did you read my post?  I'm not asking for any help?

TheFu Yes, of course QTerminal works fine if I use the default DE.

My point is that according to the FVWM man pages, FvwmConsole will work in any terminal that understands the -name, -title, and -e options.  See [http://www.fvwm.org/documentation/manpages/FvwmConsole.html](http://www.fvwm.org/documentation/manpages/FvwmConsole.html)

I had a look at the docs I could find for QTerminal, and it only lists -e.  So I presume FvwmConsole will not work with it.  As such, you might want to modify the FVWM package to not use QTerminal by default.

---

### Post by TheFu on 2018-11-15
Nobody here works for Canonical.
Nobody here works on the fvwm project.

We are simply volunteering our time, experience trying to be helpful. Sometimes we are not. Sorry.

---

