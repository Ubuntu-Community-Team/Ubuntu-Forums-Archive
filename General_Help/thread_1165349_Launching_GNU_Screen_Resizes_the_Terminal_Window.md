---
title: "Launching GNU Screen Resizes the Terminal Window"
date: 2009-05-20
forum: General Help
---

### Post by rko618 on 2009-05-20
When I either start, or resume, a screen session in gnome-terminal it automatically resizes my gnome-terminal window to a width of 80 characters.

This started happening when I added a line to my ~/.bashrc to set my TERM to gnome-256color. I do not understand why my TERM value is causing this to happen.

I am running Ubuntu 9.04 and using the new screen profiles feature.

How can I stop this from happening and still keep my TERM as gnome-256color?

---

### Post by baseface on 2009-05-20
you need to setup  your screenrc.

---

### Post by rko618 on 2009-05-20
> **baseface said:**
> you need to setup  your screenrc.

What needs to go in my .screenrc? I had a blank one is place but that did not do anything. Is there some "nosize" command that I need to use?

---

### Post by baseface on 2009-05-20
have you read the man page?

---

### Post by rko618 on 2009-05-20
> **baseface said:**
> have you read the man page?

Baseface- I request that you refrain for posting replies such as this one and the one above that contain no actual substance or useful information. Saying things like "you need to setup your screenrc" does not at all.

Put more effort into helping or don't help at all.

---

### Post by rko618 on 2009-05-20
I discovered a solution to my problem. /etc/screenrc has the following line:

```
# Change the xterm initialization string from is2=\E[!p\E[?3;4l\E[4l\E>
# (This fixes the "Aborted because of window size change" konsole symptoms found
#  in bug #134198)
termcapinfo xterm 'is=\E[r\E[m\E[2J\E[H\E[?7h\E[?1;4;6l'

```

By adding gnome* to the list of terms that the line applies to, I got it to stop resizing. The line now looks like this [http://pastie.org/484603](http://pastie.org/484603)

---

