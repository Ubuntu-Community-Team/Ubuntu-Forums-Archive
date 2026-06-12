---
title: "LXTerminal vs Mouse"
date: 2011-02-23
forum: Desktop Environments
---

### Post by starling13 on 2011-02-23
Does anyone know, if LXTerminal supports mouse usage in console applications? (&#1054;r it only allows it for selections of the text and hyperlinks?)

---

### Post by kellemes on 2011-02-23
> **starling13 said:**
> Does anyone know, if LXTerminal supports mouse usage in console applications? (&#1054;r it only allows it for selections of the text and hyperlinks?)

I guess it depends on the console-application.
[Midnight Commander]("http://www.midnight-commander.org/") for example supports mousecontrol.

---

### Post by starling13 on 2011-02-23
> I guess it depends on the console-application.
[Midnight Commander]("http://www.midnight-commander.org/") for example supports mousecontrol.     Yes, but mc, as well as Free Pascal IDE (for example) don't react on mouse clicks while working in LXTerminal. It's only possible to select/copy the parts of text. Of course in xterm all gpm-enabled applications work fine. I could use the xterm, but it is too hard to configure...

---

### Post by kellemes on 2011-02-24
Well, there must be something else going on then..
I just installed lxterminal and using mc my mouse works fine..

Have you tried restarting the gpm daemon?
Something like: "/etc/init.d/gpm restart"
Probably won't help since it works with xterm..

Edit: Currently using Lazarus myself, I'm interested to know what Pascal IDE you use from terminal.

---

### Post by starling13 on 2011-03-04
I use Free Pascal ide (fp command), small terminal-based ide wich is included in the Free Pascal distribution, while teaching the children of programming basics.
I think LXTerminal has two modes: text selection and console mouse actions through gpm usage. I'v deleted ~/config/lxterminal, but nothing has changed... I'll continue the explorations.

---

