---
title: "Xgl not starting"
date: 2006-09-06
forum: Desktop Environments
---

### Post by lozenge on 2006-09-06
I had a power cut and my computer died, when I restarted, Xgl just wouldn't load.

I set it up so I could log straight into an Xgl session, and before the power cut, I was able to log in without issues, everything working correctly.

Now, when I attempt to log into Xgl, I finish typing my password and the screen goes the dark Ubuntu red. Normally, it would go gray for a number of seconds (the patterny gray) and then the Gnome splash came up. Now, however, it just restarts X, I think, and goes back to the logon window.

Any ideas on what to do? I've checked hardware acceleration and attempted a re-install of Xgl with no luck.

Any help would be appreciated.

---

### Post by kendals on 2006-09-06
I'm not an expert so this might not help much, but I'd say there are remnant files still there that are corrupted or something? Try doing a search for ANYThing related to XGL and then remove it, and start again? ...

---

### Post by tribunal on 2006-09-06
Write here your /var/log/Xorg.0.log
you can do it right after Xgl fail from one of the first (1-6) text consoles
Ctrl + Alt + F<1-6> (excuse me, you know it)

---

### Post by lozenge on 2006-09-06
[http://hyynes.opius.info/src/linux/log.txt](http://hyynes.opius.info/src/linux/log.txt)

---

### Post by tribunal on 2006-09-06
It seems, you X started without errors
Try login using usual X,
and then write in command line:
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
If I am right, and evth ok, you should see dark screen and a cross of X
(kill Xgl after this using consol or Ctrl + Alt + BackSpace)

---

### Post by lozenge on 2006-09-06
I removed all hardware acceleration, all Xgl and Compiz components, and started reinstalling.

Why do I now get this, plus an extremely laggy destkop? (The first restart I had perfect hardware acceleration, now I'm getting a slow and clunky desktop)

```
james@monkey:~$ fglrxinfo
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0
```

I'm pretty sure I can get Xgl/Compiz going if I can just fix whatever is doing this.

---

### Post by tribunal on 2006-09-06
How does glxgears work?

---

### Post by lozenge on 2006-09-06
Okay, ignore everything above, I've sussed it.

Basically, there's a non-accelerated X server running on display 1, which is where Xgl would load after I've logged in via display 0.

I press control+alt+F8 and I get another X server, that really shouldn't be there.

Control+alt+F7 (where I am now, full hardware accel. etc) is bound to display 0, and as far as I knew, Xgl binds to display 1, which is being used by another X server.

When I start my computer, I get a login screen (display 0), then it goes blank, and another X server starts.

Ideas?

---

### Post by tribunal on 2006-09-06
Second X server at Display 1? Not Xgl? :-k 
You should have one server at display 0 (X)
And the second at display 1 (Xgl)
Then you should work at display 1. That is all

So, the question is, what method do you use to turn on Xgl? 
With sessions ?

---

### Post by lozenge on 2006-09-06
I can guarantee you that there is two X servers running, one on display 0 and one on display 1.

Yes, I've configured my computer to use sessions, but I can't login, because Xgl binds to 1, which is being hogged by the unused X server.

---

### Post by tribunal on 2006-09-06
For me, 2 X sessions means, that there are 2 commands, like
/usr/bin/X
So, after login, try to enter this at command line:
ps -ax | grep X
And write results here

---

### Post by lozenge on 2006-09-06
james@monkey:~$ ps -ax | grep X
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 4472 tty7     RLs+   1:20 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 4692 ?        S      0:00 /usr/bin/Xgl :1 -fullscreen -br -accel xv:pbuffer -accel glx:pbuffer -auth /var/lib/gdm/:1.Xauth -nolisten tcp vt9
 4725 tty9     Ss+    0:05 /usr/bin/Xorg -br vt9 -auth /tmp/.Xgl-auth-bRrETS -nolisten tcp :94 -terminate
 6017 pts/0    S+     0:00 grep X
james@monkey:~$

---

### Post by tribunal on 2006-09-06
4725 tty9 Ss+ 0:05 /usr/bin/Xorg -br vt9 -auth /tmp/.Xgl-auth-bRrETS -nolisten tcp :94 -terminate
Heh, I don't understand this string
The first two are ok
I don't remember, how it should be (I'm not at home now, here I have only Slackware)
But, try to find file with this string:
/usr/bin/Xorg -br vt9 .... (and so on)
May be this string is ok, sorry :)
I just don't remember

---

### Post by lozenge on 2006-09-06
I'm sure someone else'll be able to help.

Thanks mate.

---

### Post by tribunal on 2006-09-06
I will be able to help in 4 hours

---

### Post by lozenge on 2006-09-06
That's 2am here, I might not be awake. I'll check in tomorrow if I'm not though!

---

### Post by lozenge on 2006-09-06
Bumping.

james@monkey:~$ ps -e | grep X
 4464 tty7     00:01:06 Xorg
 4684 ?        00:00:00 Xgl
 4717 tty9     00:00:05 Xorg

Definitely one too many Xorgs :P

---

### Post by tribunal on 2006-09-06
kolya@kolya-desktop:~$ ps -e | grep X
 4857 tty7     00:00:05 Xorg
 5292 ?        00:00:51 Xgl

This is my result...

If I were you, I will start search files with 
/usr/bin/Xorg in it

---

### Post by lozenge on 2006-09-07
bump

---

