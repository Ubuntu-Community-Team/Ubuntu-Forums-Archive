---
title: "Thunderbird cursor jumps to start/end of line"
date: 2006-08-16
forum: Desktop Environments
---

### Post by davidjxyz on 2006-08-16
My installation of Dapper Thunderbird has a wierd bug with the cursor. If you are in the middle of a line, and up or down arrow, the cursor will jump to the beginning or end of the line.

This didn't happen in Breezy and (horror) doesn't happen in Windows either.

Thunderbird v. 1.5.0.5, although I've been upgrading since 1.0 so there may be vestiges about.

Does anyone have a fix? I've seen other reports of this bug but no solution.

---

### Post by neels on 2007-06-03
Hi,

in my ubuntu feisty (new install),  I have the same problem, and have had for a long time. Doesn't anyone know what's going on here??

Why does the cursor jump to line starts/line ends (sometimes chaotically) when pressing the up/down keys in the thunderbird mail composition? It changes the line correctly, but the cursor will always be either at the start or at the end of the line. That's really annoying.

---

### Post by davidjxyz on 2007-06-08
It's a known bug.

[https://launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/38758](https://launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/38758)
[https://bugzilla.mozilla.org/show_bug.cgi?id=325480](https://bugzilla.mozilla.org/show_bug.cgi?id=325480)

The problem is with the Pango library. The work-around is to disable Pango with

$ MOZ_DISABLE_PANGO=1 mozilla-thunderbird

or set MOZ_DISABLE_PANGO=1 in /etc/environment

See the bug reports for more details. There is a known fix but it seems to be taking an awfully long time to get in the Mozilla build.

---

