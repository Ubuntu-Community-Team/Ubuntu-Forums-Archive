---
title: "x11vnc with kde4 and remote login"
date: 2009-02-10
forum: General Help
---

### Post by rvjr on 2009-02-10
Hey guys, I'm somewhat in trouble here as well: I'm running Kubuntu with KDE4. I put the startup command line of x11vnc into my Xsetup file and I can successfullly connect via VNC and the login screen is presented to me. Problem is now: When I type my user and password and press the login button, the vnc server gets killed. No obvious errors in the log or other messages, it just disconnects the vnc viewer and jumps back to the login (Which is actually weird: it does not log me in, when i look at the real screen...)

Does anybody have a hint what might be wrong here?

thanks
Rainer

---

### Post by rvjr on 2009-02-10
oh, and what I also just verified: When I log in manually at the pc, the vnc server is still running after login and I can connect normally... :(

What's wrong here?

---

### Post by krunge on 2009-02-11
> **rvjr said:**
> oh, and what I also just verified: When I log in manually at the pc, the vnc server is still running after login and I can connect normally... :(


Search the forum for these terms (and subsets):  killinitclients gdm x11vnc

Verify that problem isn't happening in your setup (I don't know what Kubuntos display manager is, but check carefully whether it has a setting like this)

---

### Post by rvjr on 2009-02-11
hmm... gdm. I'm using KDE, not Gnome and that config file doesn't exists :-/ Any other suggestions?

---

### Post by krunge on 2009-02-11
check carefully whether it has a setting like this.

---

### Post by glancep on 2009-05-26
Did you ever figure this out?  I am having the same problem.  Thanks!

---

### Post by rvjr on 2009-05-27
Hi glancep

no, I never figured it out :-( I had quite a lot of work to do and didn't digg any further... If you can find a solution, please let me know. It would help me a lot!

bye
Rainer

---

### Post by glancep on 2009-05-28
rvjr --

I finally got mine working... unfortunately, I don't really understand the fix (I didn't expect it to do help any for that matter), but all I had to do was add the -noxfixes option to the x11vnc command.  I found it [here]("http://ubuntuforums.org/archive/index.php/t-965695.html"), which is mostly Gnome users, but the same issue.  The side effect of this option is to disable your system mouse cursors on the remote machine.  Here is what the [option]("http://www.karlrunge.com/x11vnc/x11vnc_opts.html") means:

```
-noxfixes              Do not use the XFIXES extension to draw the exact cursor
                       shape even if it is available.

```I hope it works for you!
Gideon

---

### Post by rvjr on 2009-05-29
wow, thanks! I'll try it sometime!

---

