---
title: "rdesktop focus problems"
date: 2009-03-18
forum: General Help
---

### Post by remarkosmoc on 2009-03-18
Hello,

New to the forum and ubuntu; not new to linux.  I just got a new laptop (dell E6500).  My last laptop was using Fedora and I had everything working as desired.  When googling issues or other research I found that a great many of the solutions available on the Internet were right here on ubuntuforums.  This forum is the reason I switched to ubuntu and didn't put on Fedora.  Thanks to all the contributors who have made this site a great resource.

Now to my problem.  I am a system admin and spend most of the day using rdesktop to work on windows servers.  I love using the spinning cube effect of compiz and frequently have all sides of the cube filled up with different rdesktop sessions.  The issue at hand is rdesktop won't release focus.  If I hit ctrl-enter several times I can win the battle sometimes.  I did the following two fixes that worked in the past but they are not working for me in ubuntu:

1.  define geometry manually instead of using the -f option 
2.  Disable the Legacy fullscreen support in compiz settings manager

The connection line I am using is rdesktop -g 1440x900 -K servername

I know that I can just turn compiz off but that isn't really an option.

Thanks in advance for the help!

---

### Post by albandy on 2009-03-18
Have you tried with "Terminal Server Client" ?

Applications --> Internet --> Terminal Server Client

---

### Post by fieroboom on 2009-03-18
The -K switch tells rdesktop not to override you window manager's key bindings.
[Rdesktop man page](http://linux.die.net/man/1/rdesktop)
Search for the word "focus", and you'll find the -K switch about halfway down.
:D
-Paul

---

### Post by kpatz on 2009-03-18
Here's what I use:> /usr/bin/rdesktop -5 -u username -a 16 -0 -D -K -r sound:local -k en-us -g 1280x1024 remote_machine_IP

The important parameters are -K (Do  not override window manager key bindings), -g (set geometry--change this to your screen's resolution), and -D (no window decorations, these simulate full screen without actually being IN full screen mode).

When I need full screen, I use Ctrl-Alt-Enter to toggle in and out.  When not in full screen, I can still flip the cube and access other desktop objects.

---

### Post by remarkosmoc on 2009-03-18
Wow that's a lot of quick responses.  Thanks for the efforts.  Unfortunately still no dice:

fieroboom:  I was already using the -K

albandy:  I tried it and got the same results.  I think that that is just a graphical app that builds the rdesktop command line for you based on the options you select in the gui

kpatz:  I tried adding the -D switch but didn't help

Additionally I noticed that sometimes I can spin the cube and focus works correctly when I am at the login prompt of the remote system, but then after I enter credentials and log in  I can no longer do this.

---

### Post by kpatz on 2009-03-18
> **remarkosmoc said:**
> Wow that's a lot of quick responses.  Thanks for the efforts.  Unfortunately still no diceIf you have -f in your parameters, remove it.  When in full-screen, the Compiz keybindings don't work.  What happens if you hit Ctrl-Alt-Enter when in rdesktop?

---

### Post by remarkosmoc on 2009-03-18
No -f.  I know compiz doesn't work with the -f.  When I was on Fedora the -f caused all sides of the cube to have the rdesktop session on it.

If I press ctrl-alt-enter the screen flashes like it is trying to go full screen (or exit full screen) and then goes back.  If I very rapidly press ctrl-alt-enter then ctrl-alt-arrow when I am lucky (takes about 6 or so tries to get the timing right) I can spin the cube.

---

### Post by kpatz on 2009-03-18
Can you spin the cube with Ctrl-Alt-left mouse button, even if the Ctrl-Alt-Arrow keys don't work?

---

### Post by remarkosmoc on 2009-03-18
No.  The only time I can spin the cube is if I first hit ctrl-alt-enter a few times and are able to very quickly hit ctrl-alt-arrow right away.  Works after 6 or so attempts to get the timing right.  It does not just work without some luck attempting to defocus with ctrl-alt-enter

---

### Post by kpatz on 2009-03-18
When rdesktop is not in full-screen mode, do you see the GNOME menu bar at top, or the status bar on the bottom?  Try clicking on one of those, and then see if you can spin the cube.  This will take the focus off of rdesktop and then the compiz bindings should work.

---

### Post by remarkosmoc on 2009-03-18
When not in fullscreen mode, I do see the banners unless.  However I still can't rotate the cube.  I did notice that if I minimize then maximize the cube again then I can rotate until the next time I click on the window.

If I don't minimize the rdesktop window; when I click on the on the menus it doesn't respond.

---

### Post by remarkosmoc on 2009-03-18
I found this link that describes the problem as being a known bug with the current version of rdesktop when used with intrepid.  There is a link about halfway down to downgrade to an older package which worked for me.

[https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/270997](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/270997)

Thanks for the help!

---

### Post by erichaase on 2009-05-26
looks like 1.6.0-0 was removed so I'm currently using 1.5.0-3 which works:

[http://us.archive.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.5.0-3+cvs20071006_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.5.0-3+cvs20071006_i386.deb)

---

