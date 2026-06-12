---
title: "[SOLVED] GNOME not starting (I think). No root privelages?"
date: 2009-01-09
forum: General Help
---

### Post by jrockpunk1 on 2009-01-09
I'm using ubuntu 8.10

Well, it started when I clicked on firefox. Ubuntu crashed and I had to restart. When I restarted it loaded like normal, and I typed my username and password. Then it's just a light brown screen and not even the loading circle or "bum bum tish tush bum bum tish tush tush tish, bum bum tish tush tiiissshhh" sound. So then I did ctrl+alt+backspace to reset Xwindow or whatever. It took me back to the logon screen and the same thing happens. I've booted in recovery mode, and done everything on there to no avail, and I've deleted the .gnome and .gnome2 files in /home by using "rm -rf .gnome" command, which doesn't do anything. I read somewhere that it might be something has took away my root privelages that's causing the problem. Oh and I don't have an internet connection, so I can't do any apt-get commands either. In fact it was my internet connection I was trying to get up and running when it crashed. Heh.

Anyone help me please?

jrockpunk1

---

### Post by albinootje on 2009-01-09
> **jrockpunk1 said:**
>  It took me back to the logon screen and the same thing happens. I've booted in recovery mode, and done everything on there to no avail, and I've deleted the .gnome and .gnome2 files in /home by using "rm -rf .gnome" command, which doesn't do anything. 

Can you try the following :
1) switch to a virtual console with ctl-alt-F1
2) log in there
3) type in :
```

startx -- :1

```
Post any errors.

Do you have enough free disk space left ?
Check with :
```

df -h

```
And, as a reminder, the sysadmin account root has normally 5 % extra space left.

---

### Post by jrockpunk1 on 2009-01-09
It seems I have fixed it :) Thanks for trying to help.
I used the wrong command to delete the .gnome file.

This is how I did it:

Boot up the computer, and load into ubuntu
When it asks to "click esc to exit to the menu" click esc
Click on the recovery mode
When the blue box comes up, go to the one that says something like "start from root terminal"
in the terminal, type:
```

rm -rf ~/.gnome*

```

then type:
```

restart -r 1

```
And wait 1 minute for it to restart. Then, I had to boot into failsafe GNOME mode (on the logon screen go to "options">"something(lol)">GNOME(failsafe))
Then restart and it will be back to normal.

I'll mark this thread as solved, though feel free to bump this thread if this solution didn't work for you.

Now we can continue to try and get my wireless working lol!

---

