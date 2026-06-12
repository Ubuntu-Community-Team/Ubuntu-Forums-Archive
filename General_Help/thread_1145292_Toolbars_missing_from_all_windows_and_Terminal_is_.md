---
title: "Toolbars missing from all windows and Terminal is blank."
date: 2009-05-01
forum: General Help
---

### Post by JamieLeece on 2009-05-01
I'm very new to linux and just installed ubuntu two days ago. I've been really liking it so far but today all of the toolbars at the top of every window have disappeared. Also the terminal just shows blank white. If I want to use the terminal I have to hit Alt+F2 and type in xterm to get a different terminal. I tried to look for help and I saw a few references to problems with nvidia video cards but I tried the usual fix for that problem and it didn't help. If anyone has any ideas I sure could use them.

---

### Post by Tews on 2009-05-01
Try this ..
```
metacity --replace
```
This should take care of your toolbar problem, but I dont know about your terminal problem...  :)

---

### Post by soro2005 on 2009-05-01
According to my experience, this can happen when the sound server hangs/stalls. The blank terminal, I mean. Trying opening an xterm and enter
```
killall pulseaudio
```
If that solves it, you can start pulse audio by entering
```
pulseaudio -D &
```
Of course, this is not a solution. Just to find out what's going on.

---

### Post by JamieLeece on 2009-05-01
The metacity command fixes both problems, but if I close the xterm window all the toolbars dissapear again. When I try to close the terminal, it says "There is still a process running in this terminal. Closing the terminal will kill it." any ideas?

---

### Post by soro2005 on 2009-05-01
```
metacity --replace &
```
then don't just shut the terminal window, but type
```
exit
```
into it.

Or you may hit <alt> + <f2> and enter metacity --replace there.

---

### Post by Tews on 2009-05-01
To make the fix permanent, System>Preferences>Start up Application>Add>enter a title, i.e Metacity,> Command enter metacity --replace.
Close and restart .. problem fixed!!  :lolflag:

---

### Post by soro2005 on 2009-05-01
If his Metacity crashes a lot, then we should help him to find out why that is and not just plaster over it. Most likely he won't need to restart it at the beginning of each session.

---

### Post by mbsullivan on 2009-05-14
> The metacity command fixes both problems, but if I close the xterm window all the toolbars dissapear again. When I try to close the terminal, it says "There is still a process running in this terminal. Closing the terminal will kill it." any ideas?

This warning is new since 2.26, and will happen if you have a running program or are logged in as su.

You can do one of three things to get out of the terminal, in such a case:
  (1) press the "close" button
  (2) type "exit" from the terminal
  (3) press Ctrl+d, twice

In order to disable the warning forever (I don't like it), you can do the following:

```
launch gconf-editor (Alt+F2, "gconf-editor"), and then go to apps->gnome-terminal->global and disable "confirm_window_close"
```

I got this info from [the Arch forums]("http://bbs.archlinux.org/viewtopic.php?id=69780").

Mike

PS: I realize that I didn't address your original problem, but I figured that this information is useful and this thread appears high in Google's ranking. Did your original problem resolve itself?

---

### Post by apcks on 2009-07-22
metacity --replace

:D
Thanks! this fixed my blank terminal too!, along with title bars.

---

### Post by ktsteel on 2009-11-27
I know I am jumping in late but any ideas would be great, I used all the fixed and resolved the "white out" and tool bar issues. Only thing is it comes back on reboot even with the fix above. Did anyone determine if this is an issue with pulseaudio update? and if so can I disable it ??

---

