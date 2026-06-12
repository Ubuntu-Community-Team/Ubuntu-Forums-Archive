---
title: "Xterm not displaying characters where ASCII &gt;127"
date: 2006-11-27
forum: Desktop Environments
---

### Post by arie_maron on 2006-11-27
Hello All,

I am running edgy on an old 400MHz PC with an AMI BIOS dated 1998.

When I run xterm or xfce4-terminal without any command line parameters Hebrew characters (ASCII > 127)are all correctly displayed.

When I try to run xterm with font parameter in the command line using option flags "-fn *fontname*" or "-fa *fontname*"
the hebrew characters are either not displayed at all or replaced by graphic characters even though the fonts I try all correctly display hebrew characters in **xfontsel**.

My questions are:

1- How can I identify the default font that does handle Hebrew correctly ("xterm -fn fixed" doesn't work)?
2- Since it seems that the fonts are correct is there some flag or configuration parameter that I am missing that turns extended ASCII handling on?

I can't just accept the default because I am trying to run legacy apps with Hebrew under dosemu and it apparently insists on setting up it's own xterm including fonts.

TIA
 -Arie

---

