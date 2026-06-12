---
title: "How to make Alt-Tab invoke Skippy?"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Dralt on 2007-04-22
I would like to rig Alt-Tab to trigger Skippy, How do I do that?

---

### Post by JayDoubleM on 2007-05-06
change the .skippyrc file to A-Tab

---

### Post by aussiebuddha on 2008-05-31
what is the value for the .skippyrc?

---

### Post by urukrama on 2008-05-31
It won't work. Skippy doesn't support modifiers; you'll need a single key to launch it.

You can change the key in ~/.skippyrc. When you download the tarbal, you'll see a file in there called skippyrc-default. Copy that to your home directory and rename it .skippyrc

Here is the relevant section of the file, using Scroll_Lock as an example:

> [general]
**keysym = Scroll_Lock**
distance = 50
useNETWMFullscreen = true
ignoreSkipTaskbar = false

Btw, you can use xautolock to launch skippy when you move the mouse cursor in  a screen corner. See [here]("http://urukrama.wordpress.com/2008/05/23/expose-type-behaviour-in-openbox/") for more info.

---

### Post by issih on 2008-05-31
Chances are you know this, but I'll say it on the off chance you don't. If you are running compiz, theres a plugin that does the same as it loks like skippy does. just ensure scale is enabled in ccsm, mind you its key bindings are a bit screwy at the moment.

I assume you are probably running some other window manager, but I thought I'd mention it anyway

---

### Post by Joeb454 on 2008-05-31
I'd suggest making a new thread on this rather than reviving a thread over a year old - things have changed a lot in that year (2 new releases etc.)

---

### Post by urukrama on 2008-05-31
> **Joeb454 said:**
> I'd suggest making a new thread on this rather than reviving a thread over a year old - things have changed a lot in that year (2 new releases etc.)

True, and it is a good policy, but skippy hasn't changed over the last year. It is no longer developped.

---

