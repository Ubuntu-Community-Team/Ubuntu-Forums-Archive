---
title: "Applications (esp. freemind) losing keyboard input"
date: 2009-04-07
forum: Desktop Environments
---

### Post by ABCDPG3 on 2009-04-07
Hello

I've just recently put 8.10 onto my Dell Inspiron E1705 (aka 9400).

I've noticed that some applications will suddenly stop receiving input from the keyboard.  I can still use the mouse with the broken applications, but the keyboard never works again, until I restart the app.  I can switch to another window (ex. alt-TAB) and back and the keyboard still does not work.

The rest of the desktop (panels, menus, other applications) works fine, accepting both mouse and keyboard input.

There are no other problems or weirdnesses that correlate with this problem.

Freemind is one of the worst programs for this problem.  I can open it and use it just fine for some very random number of minutes (or maybe keystrokes), but it ALWAYS ALWAYS ends up losing the keyboard input.  I installed freemind with synaptic.

Eagle 5.4.2 (not the version in apt; installed directly from the cadsoft website) has the same problem.  However, each time I start it up, it either has keyboard input the whole time, or not at all.  As usual, the mouse input (and everything else) works fine with Eagle.

I haven't seen any other programs have this problem so regularly.

Has anyone had similar experiences?  I am particularly curious if freemind is causing similar problems for anyone else.

Thanks

---

### Post by linuxvacuum on 2009-04-14
I have the same problem with FreeMind. I think it depends of the window manager you are using. With fvwm-crystal, the focus problems is always there. It happens when I add a link or if I do a search. Whenever I pop up a window inside FreeMind it happens. It is probably related to Java. But if I use OpenBox, the focus will work perfectly.

I'm glad to see another FreeMind user. It is my favorite application!

---

### Post by ABCDPG3 on 2009-05-20
I was having an eerily similar problem with eagle.  Sometimes I found that if one eagle window had lost KB input, I could go to its parent and open and close a menubar menu, and that would restore the original window's input.  But eventually things would crash and burn, and I'd need to restart eagle to regain KB repsonse.

Sooo I just tried turning off SCIM (right click on SCIM icon, hit exit) and this fixed the problem with eagle.

It seems to also have fixed the problem with freemind.  I haven't done any marathon freemind sessions yet to test this out.  But so far it's lasted longer than it used to.

Yeah I love freemind too.  Because of this stupid problem, I had to use a couple of other mindmappers, like View Your Mind and Labyrinth.  I still like freemind much more.  I'll be thrilled if I can use it once again.

---

### Post by John James on 2011-01-29
Ok a little late but I had a similiar problem with freemind on Lucid tried different Java installations and Deb packages.  Nothing seemed to work. Loaded fine started inserting and then stop! Annoying!

This post said it could be the SCIM (keyboard input). I turned it off and what would you know..... all okay. So far no problems.

Not sure why freemind has problems with SCIM. I feel it is also a JAVA issue.

Lastly, I too think freemind is great.

update.

now even with the SCIM enabled it works fine. Have no idea why it didn't before. Maybe the whole system just needed turning off "shutdown" and then to be switched on again after inital install. Just thought I'd add this incase someone has a similiar problem.

---

### Post by nomnex on 2011-02-11
Guys, thank you. Got the same problem with an USB keyboard (losing input). Turning i-bus solved the problem temporarily (as long as I type in English). You might want to report the issue on your bug tracker on Launchpad, or directly on sourceforge.

[https://bugzilla.redhat.com/show_bug.cgi?id=676960](https://bugzilla.redhat.com/show_bug.cgi?id=676960)

---

### Post by nomnex on 2012-03-26
This might be of some interest for anyone experiencing a similar issue, using a LXDE DE:

[https://bugzilla.redhat.com/show_bug.cgi?id=803098](https://bugzilla.redhat.com/show_bug.cgi?id=803098)

---

