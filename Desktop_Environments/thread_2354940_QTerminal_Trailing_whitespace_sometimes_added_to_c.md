---
title: "QTerminal: Trailing whitespace sometimes added to copied terminal output"
date: 2017-03-07
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2017-03-07
When copying stuff from QTerminal to clipboard, there is sometimes a bunch of trailing whitespace appended to every line.  For example -
```
$ ps -C thunar,Thunar -o pid,command                                            
  PID COMMAND                                                                   
 3045 thunar                                                                    
 3059 Thunar /var                                                               
$                                                                               
```
If you select the text in the code box above, you will notice that the lines don't stop where the text does.  I didn't type any of that whitespace.

Now let's clear QTerminal with Ctrl-Shift-X and try running the command again.  Copy the result, and we get -
```
$ ps -C thunar,Thunar -o pid,command
  PID COMMAND
 3045 thunar
 3059 Thunar /var
$ 

```
Yay, much better!

This erratic behavior of QTerminal is...less than ideal, especially when copying patches.

How to prevent QTerminal from ever adding all that trailing whitespace?

---

### Post by &amp;KyT$0P# on 2017-03-28
bump

---

### Post by &amp;KyT$0P# on 2017-04-04
bump

---

### Post by &amp;KyT$0P# on 2017-04-15
bump

---

### Post by &amp;KyT$0P# on 2017-04-22
bump

---

### Post by &amp;KyT$0P# on 2017-04-27
bump

---

### Post by &amp;KyT$0P# on 2017-05-12
Hmm, no one here has any suggestions.  Should I be filing a bug report about this?  If so, should I do it against [QTerminal]("https://launchpad.net/ubuntu/+source/qterminal/+bugs") or [qtermwidget]("https://launchpad.net/ubuntu/+source/qtermwidget/+bugs")?

(I searched upstream bug reports in both projects, but didn't find anything about this specific issue.)

---

### Post by again? on 2017-05-15
Maybe it's something in your ~/.bashrc
I can see what you mean by using the gedit plugin to draw spaces.

---

### Post by &amp;KyT$0P# on 2017-05-15
> **guber2 said:**
> Maybe it's something in your ~/.bashrc
But I get the issue with [FONT=Courier New]sh[/FONT] too.  I don't think I've done any custom configuration for [FONT=Courier New]sh[/FONT] (which is a symlink to [FONT=Courier New]dash[/FONT]).

Ran from Xfce terminal -
```
qterminal -e sh
```

(in QTerminal, before clearing)
```
$ ps -C thunar,Thunar -o pid,command
  PID COMMAND
 2669 Thunar /var                                                               
 2674 thunar                                                                    
$
```

(in QTerminal, after clearing)
```
$ ps -C thunar,Thunar -o pid,command
  PID COMMAND
 2669 Thunar /var
 2674 thunar
$
```

---

### Post by &amp;KyT$0P# on 2017-05-24
For reasons unrelated to this thread, I installed Antergos in a VM.  And there QTerminal does not have this problem!

Since Ubuntu zesty appears to have the same QTerminal version as Antergos, I built the zesty QTerminal source packages for 16.04.  And it showed exactly the same problem.

I really doubt this is a Ubuntu-specific issue, as I've seen it in CentOS too.  So I did some digging and, as far as I can tell, Antergos QTerminal is just a straight build from upstream sources -
[https://git.archlinux.org/svntogit/community.git/tree/?h=packages/qterminal]("https://git.archlinux.org/svntogit/community.git/tree/?h=packages/qterminal")
[https://git.archlinux.org/svntogit/community.git/tree/?h=packages/qtermwidget]("https://git.archlinux.org/svntogit/community.git/tree/?h=packages/qtermwidget")

But building the upstream source on Ubuntu (with the zesty "debian" tarballs and [FONT=Courier New]dpkg-buildpackage[/FONT], so that I could build .deb packages) didn't help either.

Not sure what to make of all this.  What to try next?


Maybe I should also ask, do others get the same issue with QTerminal on Xubuntu 16.04 or is it just me?

---

### Post by &amp;KyT$0P# on 2018-04-20
In QTerminal in Xubuntu 18.04, I do not see this problem.

---

