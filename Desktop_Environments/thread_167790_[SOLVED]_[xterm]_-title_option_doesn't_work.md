---
title: "[SOLVED] [xterm] -title option doesn't work"
date: 2006-04-29
forum: Desktop Environments
---

### Post by bernardfrancois on 2006-04-29
I often have a lot of xterm windows open, and to make switching between them more easy I would like to give each of them a different title.

When I press Alt+F2 and I type **xterm -title test**, at first the title appears, but gets changed to a string in the following format: *user@host: working directory*.

Offcourse, I don't want this. I don't know what's exactly changing the title of my xterm window. For example when I try to give emacs windows a title, it works...

At school it works as well for xterm. They have Fedora Core 4 over there.

Anyone who can help me with this?

---

### Post by bernardfrancois on 2007-01-10
In the meantime I upgraded to ubuntu dapper LTS.

I just tried it, and it still doesn't work:
If I execute *emacs -title test* I get an emacs window with the given title.
If I execute *xterm -title test* I get an xterm window, not showing the given title.

If you're using several xterm windows at the same time for different tasks, it's really handy to be able to give them different names to be able to switch to the right window quickly...

Someone who can help?

---

### Post by bernardfrancois on 2007-05-19
Can anyone who has a more recent version than dapper tell if this problem is still unsolved? I'm currently still using dapper (I like the long term support).

---

### Post by kerry_s on 2007-05-19
Try> xterm -T "test"

You'll also need to comment out or remove this section in your .bashrc

```
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;$: ${PWD/$HOME/~}\007"'
#    ;;
#*)
#    ;;
#esac

```

---

### Post by bernardfrancois on 2007-05-19
Same effect, the 'test' title appears but disappears after a sec...

---

### Post by kerry_s on 2007-05-19
Sorry forgot about the .bashrc fixed above.

---

### Post by bernardfrancois on 2007-05-21
Thanks!

Now I wonder if I can have the default behaviour if I don't specify a title...

It could be done in the .bashrc file if the title argument passed by xterm could be obtained somehow in the bash script.

I think I need two things to get it done:
[LIST=1]
[*]A command which allows you to see which processes are running, and how they were started (with which flags). I think it exists... I had a brief look at the man page of **ps**, but I didn't see an option like that.
[*]A way to find out the PID of the started xterm instance causing .bashrc to be run.
[/LIST]

Anyone who can help me with this?

---

### Post by kerry_s on 2007-05-21
That's out of my skill range, if your using gnome you can add a drawer with several launchers for the different xterm's until you figure out the script.
Example:
xterm1
xterm -T "Terminal1"

xterm2
xterm -T "Terminal2"

etc....

---

### Post by bernardfrancois on 2007-05-22
That solution won't work, what I actually want is that I can run **xterm** and see my user name and working directory (the behaviour without those lines commented out in .bashrc), and when I run **xterm -T "title"** I want to see the title.

I wonder what other distro's do, I remember it worked like that in fedora core 5... Someone who can check those lines in .bashrc there or in another distro with the same behaviour?

---

### Post by bernardfrancois on 2007-05-26
I noticed the name in the task bar (under gnome) is still xterm, no matter which title I chose. If I recall correctly, this was not the case in fedora core.

Is there anyone who knows how I can make sure the string on the taskbar icon is the same as in the titlebar?

---

