---
title: "Firefox doesn't start"
date: 2007-05-28
forum: Desktop Environments
---

### Post by marciovinicius on 2007-05-28
My firefox doesn't start when I click the link in gnome panel.

I tryed to open it thru terminal and it returns the folowing message (pt-br):

```

mmp@grom09-ubuntu:~$ firefox
Falha de segmentação (core dumped)
```

After several attempts I can open thew firefox. The terminal shows the folowing message:

```
mmp@grom09-ubuntu:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
```
Is it normal?

And (most important) what does "core dumped" mean?

---

### Post by marciovinicius on 2007-07-08
Anyone?

---

### Post by bartbrinkman on 2007-09-12
Having the same problem. Firefox Just fails to start; terminal shows nothing. Reinstall, X restart, computer restart, nothing helps. Any hints?

---

### Post by kellemes on 2007-09-12
Do you use any plugins? Try to disable them and see what happens.
Also recreating your profile can help.
"firefox -profilemanager"

---

### Post by bartbrinkman on 2007-09-12
Solved it. You have to (ch)own ~/.mozilla in order for Firefox to start...

---

### Post by lutherhert on 2007-09-14
> **bartbrinkman said:**
> Solved it. You have to (ch)own ~/.mozilla in order for Firefox to start...

This sounds like the same problem that I am having with firefox. I am not sure how do to enter the command in the terminal to test this. Can someone help with the complete command?

Thank you.

---

### Post by marciovinicius on 2007-09-14
helping with the command:
```
sudo chown yourusername -R /home/yourusername/.mozilla
```

BUT...

well, I think we need another browser. I have a lot of troubles with Firefox in Linux which simply don't happen in other OS. This is only one more.

This one doesn't happen to me anymore (don't know why, I didn't do anything to solve the problem), but I still have several other problems. Now, I can't click on flash movies, and scrolling down some pages is painful slow.

I know that to write it here doesn't help to much, but my bug reports (in mozilla and Ubuntu systems) seem not helping too... :-(

---

