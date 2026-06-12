---
title: "Command &quot;menu-cached&quot; takes 100% CPU usage"
date: 2016-12-08
forum: Desktop Environments
---

### Post by vasa1 on 2016-12-08
Operating system: Lubuntu 16.04, fully updated (Lubuntu session or Openbox session).

Twice, in the last few days, while using the Openbox session, I did something, I'm not sure what, that caused %CPU usage to rise to 100%. I opened *top* and found that the command responsible was "menu-cached".

After a bit of searching, I came across [menu-cached utilize 100% CPU]("https://github.com/lxde/menu-cache/issues/7"). The first date in this issue is from January 2016, but, as I said, I've not encountered this problem until very recently.

[One poster]("https://github.com/lxde/menu-cache/issues/7#issuecomment-230171886") showed how to reproduce the issue:
[LIST=1]
[*]Open PCManFM
[*]Right-click on a file
[*]Hover over "Open with" and from the context menu, again select "Open with"
[*]In the window that appears, choose "Custom Command Line"
[*]Enter a legitimate program name such as *leafpad* or *geany* if the file is a text file, for example
[*]Press "Okay"
[/LIST]

The result is that %CPU usage immediately rises to 100% (in *Conky* and in *top*). Killing the process immediately brings things back to normal.

I can reproduce this both in a Lubuntu 16.04 session which has lxpanel running and in an Openbox session which does not have lxpanel running. [A user of Lubuntu 16.10]("https://github.com/lxde/menu-cache/issues/7#issuecomment-255239082") also reported the anomaly. 

[mtasaka]("https://github.com/lxde/menu-cache/issues/7#ref-commit-5800ac6") provided a fix that works judging by responses in the issue. And [LStranger]("https://github.com/lxde/menu-cache/issues/7#issuecomment-255250840") has incorporated the patch in "menu-cache". Users of Arch, including [Melodie]("https://ubuntuforums.org/member.php?u=13351"), are happy because [the new version reached AUR]("https://github.com/lxde/menu-cache/issues/7#issuecomment-265412915") apparently on or about 20161207.

I don't know what the process involved is but I'm guessing this first has to be accepted in Debian before the Lubuntu Team could think of backporting this to Lubuntu 16.04 and 16.10 (even though they're mostly tied up with getting LXQt on the road).

---

