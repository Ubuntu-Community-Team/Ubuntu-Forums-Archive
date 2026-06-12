---
title: "Kubuntu 20.04.1 fresh install - paste problems ??"
date: 2021-01-02
forum: Desktop Environments
---

### Post by oygle on 2021-01-02
Since doing a fresh install of 20.04.1 (this was necessary as updating 19.10 was removed), there have been quite a number of problems. This is probably the worst install of Kubuntu I have experienced. Mostly of the display, theme, colors problems, but I may leave that to another post.

Running terminal today and there was only partial history when using the **UP** arrow. The ```
history
``` command showed that only partial history is being kept ? If I **ENTER** a command, the history is kept, but if I use _Shift-Ctrl-V_ to paste a previously copied command, the history is **NOT** kept.

Which reminds me of another paste problem also, where the foreground color is changed to white, so I cannot see the text. This happens after a copy and then positioning the mouse in the same field/box.

Are these two problems related, in that they both seem to be sourced from paste ??

---

### Post by SeijiSensei on 2021-01-02
Try creating a new user and see if that helps. Perhaps there's something(s) in your profile that 20.04 doesn't like. (I can't say I've ever had this problem though, and I've had no problems installing and using Kubuntu 20.04.)

---

### Post by oygle on 2021-01-02
> **SeijiSensei said:**
> Try creating a new user and see if that helps. 

Okay thanks, I'll try that. I did read up more and issued a ```
history -a
``` yet that works (up arrow to retrieve) for some commands and not others ??

The commands that were pasted (Shift, Ctrl-V) and were retrieved with the up arrow are ..

```

journalctl -b
sysctl fs.inotify.max_user_watches
sudo sysctl -w fs.inotify.max_user_watches=524288
sysctl fs.inotify.max_user_watches
grep -i -r "guitar"  *.txt

```

plus any commands entered manually can be seen in history or UP arrow. Yet this command doesn't appear in history or UP arrow ??

```

grep -i guitar **/*txt

```

... later, now it does ?? Unless there is some sort of delay in writing to .bash_history file ?

---

### Post by oygle on 2021-01-04
It's working okay now.  :)

---

### Post by oldfred on 2021-01-04
If I have more than one terminal open, then not all commands yet seem to be in history to be seen from other terminal.
I like that I can open terminal in Kate, but used to Ubuntu and having separate terminal, so now often have two or more open at one time.

---

