---
title: "x11vnc key repeat problem since 9.04"
date: 2009-12-03
forum: Desktop Environments
---

### Post by damdam76 on 2009-12-03
Hi,

Since I upgraded from Hardy (8.04) to Jaunty, and then to Karmic, I've noticed a strange bug in key repetition when using x11vnc.
Problem appeared as I moved to Jaunty and remains with Karmic. Don't know if it's a x11vnc issue or Xorg one.
I don't suspect anybody but I've already noticed there had been lots of changes on Xorg since last Ubuntu versions ....:confused:

Let's expose the situation:
I have three different installs to do my tests
One computer with Hardy, one with Jaunty, and one with Karmic.
All these 3 computers use the last binary of x11vnc (v0.9.9) downloaded from Karl's personnal binaries collection.
Connection tests are done using RealVNC Viewer from a fourth computer running Windows XP, and from any of the Linux three machines using SSVNC,KRDC, or vinagre.
My purpose is to make everything working on the newest version of Ubuntu, Karmic
When connecting from any Linux machine (whatever the client I use) to my Karmic machine, everything works well,keys are repeated correctly.Using xev on the remote machine, I can see many KeyPress & KeyRelease events, showing why everything's going well.
BUT when connecting from a Windows machine, key repeat is NOT working, and xev only shows one KeyPress event and remains still as long I maintain the key pressed, and finally only one KeyReleased event when key is released.
I firstly thought this was due to the way Windows handles key repeat, I thought it could be the one that does not send the key repetitions. I understood the problem was somewhere else when the same test (RealVNC from XP, on a the Hardy machine) showed the same xev's KeyPress/KeyRelease events repeating as long a key is maintained.
Don't know how to explain what could have changed.
I can add that I really spent some times to do lot of tests, checking what was the version of the protocol version was used for each tries, but I have to admit that it did not proved anything.

I'm talking directly to you Karl since we've already exchanged via this place and via mail, and since I know you'll probably be the one that might help me once again with this (thanks again for helping me each time).Don't hesitate to ask me any details or tests you could need, I can't expose everything there, this would probably to long and probably unusefull.

Thank you.

---

### Post by krunge on 2009-12-03
So the repeating only fails when using Windows as the viewer-side, correct?

And then, it only fails to ubuntu 9.04 or greater, correct?

Run x11vnc with the option "-dk -dk" to get lots of reporting on keystroke activity.  BTW, the Windows vncviewers can do some really weird stuff (e.g. 10 Shift or Control keypresses in a row with no keyreleases, perhaps you will see it in the wild.)

---

### Post by damdam76 on 2009-12-06
Hi Karl,

> **krunge said:**
> So the repeating only fails when using Windows as the viewer-side, correct?
That's it.

> And then, it only fails to ubuntu 9.04 or greater, correct?
Exact.


> Run x11vnc with the option "-dk -dk" to get lots of reporting on keystroke activity.  BTW, the Windows vncviewers can do some really weird stuff (e.g. 10 Shift or Control keypresses in a row with no keyreleases, perhaps you will see it in the wild.)
Please find 3 logfiles as attachment.

1/ x11vnc-dk-dk.txt : Is the log file of a x11vnc-0.9.9 running on my Ubuntu 9.10 computer. The "w" key as been pressed from a Windows client for some seconds and no repeat was seen, and, on a second connection the "l" key was also pressed for some seconds from a Linux computer and the key was well repeated
2/ x11vnc-hardy-dk-dk-from-win.txt : Is the log file of a x11vnc-0.9.9 running on my Ubuntu 8.04 computer. A client connects from Windows and keys are well repeated
3/ x11vnc-hardy-dk-dk-from-linux.txt : Is the log file of a x11vnc-0.9.9 running on my Ubuntu 8.04 computer. A client connects from Linux and keys are well repeated

Files 2/ and 3/ are just in case would like to check for differences between 9.10 & 8.04. But maybe the trick is in the x11vnc-dk-dk.txt file, especially near this 
```
04/12/2009 14:06:22 XTestFakeKeyEvent: keycode=0x34 "w" is *already* down
```

Hope this helps.
Thanks.

---

### Post by krunge on 2009-12-06
Thanks for the log files.

It seems your Windows viewer/OS only sends down key-events during key repeat for some keys (i.e. "w")

For clarity I only show the XTestFakeKeyEvent lines:

Windows Viewer -> x11vnc ubuntu-9.10 for "w":
```

04/12/2009 14:06:21 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
04/12/2009 14:06:22 XTestFakeKeyEvent(dpy, keycode=0x34 "w", down)
...

```
Whereas for "l" the Windows viewer sends down and up as one feels it should:
```

04/12/2009 14:06:06 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:06:07 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)

```

To be clear, these show what events x11vnc has received **over the wire** from the vncviewer. Even though x11vnc complains the key "is already down", he does dutifully inject the down keystroke every time and hopes that the X server will do the right thing with them.

So evidently ubuntu 9.10 does not process this series of down's in a row as it had previously.

Note that in your connection Windows viewer -> ubuntu 8.04, x11vnc still complains that key "a" is already down, but again he sends them, and evidently (from what you have said) the ubuntu 8.04 window system interprets each one (as we want it to.)

For completeness, your Linux Viewer -> ubuntu 8.04 sends the up keystrokes: ```

04/12/2009 14:49:51 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", down)
04/12/2009 14:49:52 XTestFakeKeyEvent(dpy, keycode=0x2e "l", up)

```
and so the repeating works as expected (I will assume this works for all held down keys with Linux viewer, but I can't prove that happens)

Not sure what to do next.  Perhaps try failsafe-xterm login on ubuntu 9.10 and see if it still happens, then try xfce and kde sessions to see if it only happens in gnome.

It would be useful to know why Window vncviewer only sends downs for some keys... Did you try a different viewer on Windows?  E.g. ultravnc?

---

### Post by damdam76 on 2009-12-07
Hi Karl,

> **krunge said:**
> 

Not sure what to do next.  Perhaps try failsafe-xterm login on ubuntu 9.10 and see if it still happens,
I did the test with a failsafe-xterm and results are the same.

>  ...then try xfce and kde sessions to see if it only happens in gnome.
Did not test KDE, but things are the same under Xubuntu (xfce) & Ubuntu (gnome)

> It would be useful to know why Window vncviewer only sends downs for some keys... Did you try a different viewer on Windows?  E.g. ultravnc?
I tested all the Windows clients that I know, UltraVNC, RealVNC, ThighVNC, and all these have the same behaviour.
I even tried the thighvnc-java applet, and guess what, launched from the same version of Firefox on Linux and Windows, Linux applet repeats keys where Windows's one does not !
Unbelievable !

Since events seems to be handled the same way between 8.04 and 9.04 x11vnc's side, maybe this issue deals somewhere with Xorg's changes, I don't know if there will be a way to handle this ...

Thank you.

---

### Post by krunge on 2009-12-16
Is a workaround for this problem to use the "-repeat" x11vnc option?
```
x11vnc -repeat ...
```
That is to say, we use the remote (x11vnc-side) X server's autorepeating?  Does this workaround the problem for you?

Of course there are other problems leaving the X server autorepeating on when vnc viewers are connected (repeated keys; the reason why -norepeat is the default.)

I was testing this on ubuntu 9.10 w/o using Windows-side-viewers or any vnc viewer's by using x11vnc new remote control trick:
```
x11vnc -display :0 -R DIRECT:keycode:38,1
```
(keycode 38 happens to be "a" on my test system; the "1" means press key down; "0" would mean up.)  So doing the above a number of times in a row (all down) does seem to reproduce the problem you see if the X server autoreating is off ('xset r off'), but it does, of course, autorepeat if the autoreating is on ('xset r on' to turn it back on.)

(BTW the above DIRECT: remote control trick had a bug for keycode and so one would need the lastest x11vnc tarball, uploaded today, for it to work properly.)

---

### Post by damdam76 on 2010-01-06
Hi Karl, and Happy New Year !

> **krunge said:**
> Is a workaround for this problem to use the "-repeat" x11vnc option?
```
x11vnc -repeat ...
```
That is to say, we use the remote (x11vnc-side) X server's autorepeating?  Does this workaround the problem for you?

Yes ! It solves the problem (included some key combinations that I could not do such as @,|,# ...) as long as I use a VNC client from Windows !
Like you were supposing, when connecting from a Linux VNC client (that was working pretty well without -repeat) it brings some kind of double key repetitions that can be very disturbing !
So to get rid of these matter, I've found the solution to leave x11vnc without the -repeat parameter by default, and manualy activate repeat mode by doing
```
x11vnc -R repeat
```

> I was testing this on ubuntu 9.10 w/o using Windows-side-viewers or any vnc viewer's by using x11vnc new remote control trick:
```
x11vnc -display :0 -R DIRECT:keycode:38,1
```

I made some tests using your DIRECT trick, and except confirming that it is probably a Xorg issue, it did not solved anything.
When launched in a terminal from a Windows VNC connection, it only shows one "a", whereas launched from a Linux VCN one, it shows many...

Well, until something changes Xorg's side, I think my -R repeat trick will make the deal.

Thank you anyway !

---

### Post by krunge on 2010-01-06
Hmmm, I would have thought "x11vnc -repeat" would be equivalent to using the remote control command "x11vnc -R repeat".  Are you sure you see a difference?  Is there a difference in the auto repeating reported by "xset q"?

---

### Post by damdam76 on 2010-01-06
> **krunge said:**
> Hmmm, I would have thought "x11vnc -repeat" would be equivalent to using the remote control command "x11vnc -R repeat".  Are you sure you see a difference?  Is there a difference in the auto repeating reported by "xset q"?

Oh no ! There are no differences between a "x11vnc -repeat" set in "/etc/gdm/Init/Defaut" and a "x11vnc -R repeat" launched later in terminal !
What I was trying to explain is that , since I sometimes use VNC from Linux and sometimes from Windows, I did not added any "-repeat" by default, and that I "manualy" activate "repeat" mode once I'm connected from Windows.
Thus, keys are not repeated madly when I'm connected from Linux.

Hope it's more clear explained this way !
:)

---

### Post by krunge on 2010-01-06
> What I was trying to explain is that , since I sometimes use VNC from Linux and sometimes from Windows, I did not added any "-repeat" by default, and that I "manualy" activate "repeat" mode once I'm connected from Windows.

I think I see now.  So you run "x11vnc -R norepeat" to undo the setting?

---

### Post by ottoflick on 2011-06-24
I have the same problem with x11vnc running on Ubuntu 10.04 & Windows 7 + TightVNC / RealVNC client ... no matter whether I turn "-repeat" on or not. 

Linux clients works OK and TightVNC server works well with Windows clients, too – but I need to see my original display and to connect from a Windows machine.

---

