---
title: "Suggestions for terminal application?"
date: 2016-07-31
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2016-07-31
Looking for a replacement for Konsole to use in Xubuntu 16.04 given that [this issue]("https://ubuntuforums.org/showthread.php?t=2327689") seems not to be solvable.  I'm not very knowledgeable about terminal applications, and all I've tried so far have some or other annoying shortcoming :(

In Lubuntu 14.04, I use Konsole and it's awesome. 8-)  But that Konsole is from KDE 4, so it won't work with 16.04.
What terminal program would you recommend that fits all of these criteria?

**Must-have list**
 - Drag&drop from file manager (in this case Thunar) into the terminal window pastes the location(s) of the dragged item(s)
 - Option to open the file manager (or any specified application, which I'd specify to be Thunar) in the shell's working directory
 - Clear scrollback with keyboard shortcut (equivalent of Konsole's Ctrl-Shift-K)
 - Clearing scrollback needs to avoid to kill or disappear the prompt or prior input
 - Support for ANSI escape sequences (which I think all terminals have these days?)
 - Customizable scrollback length
 - Ability to select/copy/paste any text in the terminal
 - Running program (or, if just the shell, optionally just the shell's working directory) displayed in the title bar
 - Ability to customize appearance, including colors, font, etc
 - Prompt before closing the terminal if processes other than a specified list are still running inside the shell
 - Mouse wheel scrolling in pagers, such as when using less and reading man pages

**Nice-to-have list**
 - Tabs as well as windows
 - Ability to detach tabs and merge windows into tabs


Thanks

---

### Post by mook765 on 2016-08-05
I am with Ubuntustudio 16.04 which comes with xfce.
the built-in terminal is "xfce4-terminal 0.6.3" and as i checked just right now, it fits most of your needs.
Tabs are available, deatachable but not mergeble, you can paste from thunar, mark copy paste...
You can customize appearance.
Some points off your list i didn't check out, just want to give some fast feedback now...
On the other side, i don't see why Konsole won't run. If you install it, needed librarys would be installed as well.
I have KDE-applications installed and they run properly...

---

### Post by &amp;KyT$0P# on 2016-08-05
Thanks for the reply.  I managed to get Konsole running in 16.04, the problem I have with it is that drag&drop does **nothing** if I don't have write permissions on the shell's cwd (see the thread I linked in the first post).  Hard to just live with that given how often I use a Terminal with cwd in /etc and /usr for example.

xfce-terminal does not prompt before closing if something is running in the shell, which in the past has caused minor data loss :o

---

### Post by Habitual on 2016-08-05
terminator.
nuff said.

---

### Post by &amp;KyT$0P# on 2016-08-05
> **Habitual said:**
> terminator.
nuff said.
Close but not quite.  How much of the missing features can be added with custom plugins?

---

### Post by SeijiSensei on 2016-08-20
> **halogen2 said:**
> Thanks for the reply.  I managed to get Konsole running in 16.04, the problem I have with it is that drag&drop does **nothing** if I don't have write permissions on the shell's cwd (see the thread I linked in the first post).  Hard to just live with that given how often I use a Terminal with cwd in /etc and /usr for example.
I never drag and drop anything into the terminal, but I was wondering whether that was true if you're running as root inside Konsole.  Is it limited by your permissions when you open Konsole, or by the permissions of the user running the session inside Konsole?

99.9% of the time when I'm doing anything that requires root privileges I just become root in the terminal.  I've spent so much time running as root that I'm not likely to do anything damaging.

---

### Post by &amp;KyT$0P# on 2016-08-20
Not completely sure how to answer your question?

If I use sudo to get a root shell in Konsole then drag&drop always just pastes the location regardless of cwd.

I tried running Konsole itself as root, from there created a directory in /tmp and set its permissions 0400, cd inside it, drag&drop fails there too.  But, being root, I can still read/write files from the terminal, and list the directory's contents.

---

### Post by coldraven on 2016-08-27
I don't know the answer, Guake maybe?
Whatever you finally choose make sure that you enable incremental history search, it's the best!
[http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/](http://codeinthehole.com/writing/the-most-important-command-line-tip-incremental-history-searching-with-inputrc/)

---

### Post by Habitual on 2016-08-27
good stuff, the interactive search.
I've used this awhile now.
### bind fix for inter and non-interactive shell
```
iatest=$(expr index "$-" i)
if [[ $iatest > 0 ]]; then bind '"\e[A": history-search-backward'; fi
if [[ $iatest > 0 ]]; then bind '"\e[B": history-search-forward'; fi
```

---

### Post by &amp;KyT$0P# on 2016-08-27
> **coldraven said:**
> I don't know the answer, Guake maybe?
It doesn't prompt about killing process when I close the tab, and it can't be cleared by keyboard shortcut, and when it is cleared the rest of stdin is vanished from visibility.  While most of the feature list is fulfulled by any decent graphical terminal, these few seem to be the hardest features to find. :(

The interactive history thing sounds interesting, thanks!  I'll have to look into increasing the amount of stored history for it to be really useful as some of the time I enter the same few commands over and over.  These are a feature of the shell (in this case bash & ksh) not the terminal emulator, right?

---

### Post by Habitual on 2016-08-27
> **halogen2 said:**
> It doesn't prompt about killing process when I close the tab, and it can't be cleared by keyboard shortcut, and when it is cleared the rest of stdin is vanished from visibility.  While most of the feature list is fulfulled by any decent graphical terminal, these few seem to be the hardest features to find. :(

The interactive history thing sounds interesting, thanks!  I'll have to look into increasing the amount of stored history for it to be really useful as some of the time I enter the same few commands over and over.  These are a feature of the shell (in this case bash & ksh) not the terminal emulator, right?
I've used mine in console and terminal emulators for years, (and I'm a bash nut).

---

### Post by &amp;KyT$0P# on 2016-08-27
> **Habitual said:**
> good stuff, the interactive search.
I've used this awhile now.
### bind fix for inter and non-interactive shell
```
iatest=$(expr index "$-" i)
if [[ $iatest > 0 ]]; then bind '"\e[A": history-search-backward'; fi
if [[ $iatest > 0 ]]; then bind '"\e[B": history-search-forward'; fi
```
Works great for bash but ksh doesn't know what to make of it.  That's OK though, I usually prefer bash for command-line anyway.

Related to doing this in bash, I'll just leave this here: [http://www.math.utah.edu/docs/info/features_7.html]("http://www.math.utah.edu/docs/info/features_7.html")

---

### Post by &amp;KyT$0P# on 2016-10-31
bump

---

### Post by &amp;KyT$0P# on 2016-11-10
bump

---

### Post by &amp;KyT$0P# on 2016-11-17
bump

---

### Post by sudodus on 2016-11-18
Maybe there is no terminal window program that satisfies the whole ***must-have*** list. So nobody has anything to suggest.

I searched the internet with the search string ***linux terminal emulators*** and found some web sites, that list several alternatives. I suggest that you read the lists and try the listed terminal emulators and select the one that works best for you, even if none of them is perfect. For example, did you try sakura?

---

### Post by &amp;KyT$0P# on 2016-11-18
> **sudodus said:**
> I searched the internet with the search string ***linux terminal emulators*** and found some web sites, that list several alternatives. I suggest that you read the lists and try the listed terminal emulators and select the one that works best for you, even if none of them is perfect. 
Thank you for the suggestion sudodus!  I was using only Synaptic package manager to search for terminal emulators.  Internet search turned up QTerminal which looks about perfect.  Thanks again! :D

---

### Post by sudodus on 2016-11-18
I'm glad you found a good terminal emulator; that QTerminal can do what you want.

Thanks for sharing your solution :-)

---

### Post by &amp;KyT$0P# on 2016-11-19
No problem.

Something I would like to note about QTerminal regarding my must-have list.  It gets better.  The lack of UI for custom ANSI colors, does not mean you're forced to pick from the presets you see listed.  You're not, this is actually just as customisable as Konsole when you go under the hood. \\:D/

If you've already got a nice custom color scheme from Konsole, you're almost done.  Just grab that custom color scheme from [FONT=Courier New]~/.kde/share/apps/konsole[/FONT] and drop it in [FONT=Courier New]/usr/share/qtermwidget5/color-schemes[/FONT], and that's it.  It'll now be listed in QTerminal's preferences as another color scheme preset.

Tested with a color scheme from KDE 4 Konsole.  A quick glance indicates color schemes for KDE 5 Konsole might work, but I haven't actually tested that.

---

### Post by &amp;KyT$0P# on 2016-12-12
One other thing to note here.  When adding custom color schemes, **they _must_ be world-readable**.  Otherwise QTerminal will segfault on startup.

---

