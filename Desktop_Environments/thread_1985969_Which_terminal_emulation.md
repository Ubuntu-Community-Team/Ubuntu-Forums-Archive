---
title: "Which terminal emulation?"
date: 2012-05-24
forum: Desktop Environments
---

### Post by alawson on 2012-05-24
Hi,

I have a Ubuntu 12.04 server that I SSH into from various different boxes. Any other Ubuntu box is fine, I just run ssh [hostname] and all the terminal emulation stuff is taken care of.

Under Win7, using putty or securecrt I get loads of gibberish on screen when I try and use any text menu driven apps. The one I'm specifically having trouble with at the moment is Midnight Commander.

What terminal settings should I configure on the Windows boxes to make this problem go away?

Thanks for your help!

Andy.

---

### Post by papibe on 2012-05-24
Hi alawson.

Unfortunately I'm away from my Windows laptop, but if I were you I'd play with Putty's options. I'm think there are options to either change the type of emulation, or adapt for the ncurses library (text mode menus).

Just a thought.
Regards.

---

### Post by alawson on 2012-05-24
Thanks for the response. I had a good dig through the putty options. I'm running v0.60 and I can't find anything the specifically lists ncurses.....

---

### Post by papibe on 2012-05-24
I'm still away from my Windows laptop (I think that may never change :P), but...

It looks like it is a well know problem, and there are a few tips around.

Try setting this options on Putty:
```
BCE (Background Color Erase)

Under Settings / Windows / Translation -> UTF-8
```
Also there's an environment variable that can be set to create better compatibility:
```
export NCURSES_NO_UTF8_ACS=1
```

I hope it helps.
Regards.

Sources: [this]("http://www.linuxquestions.org/questions/linux-software-2/putty-doesnt-display-curses-based-stuff-correctly-196454/"), [this]("http://www.linuxquestions.org/questions/linux-software-2/midnight-commander-graphics-under-winxp-ssh-536908/"), and [this]("http://forums.freebsd.org/showthread.php?t=15688").

---

### Post by alawson on 2012-05-24
Thanks very much for your help - that's working great!

(A little bit ashamed that I didn't find that 1st link myself :)

---

