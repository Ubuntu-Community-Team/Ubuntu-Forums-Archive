---
title: "disappearing kicker (KDE)"
date: 2006-12-11
forum: Desktop Environments
---

### Post by phyoptik on 2006-12-11
my KDE kicker menu has disappeared.  It appears to be running in the background, but does not show up on screen.  If i kill -9 it, and restart it via kicker &, it shows up for a little while, until i change windows, where it disappears again.

I've tried reconfiguring it via kcontrol, making it permanantly visible, and increasing it's size, however it is still not there, and now after about an hour, i've tried to reinstall kde, but it still does not show, is there a way to bring it back?

---

### Post by aysiu on 2006-12-11
Have you tried creating a new test user to see if that user runs into the same problem (you can always delete the test user later)?

If you both experience it, it's a systemwide problem. If only your current user experiences it, it may be a configuration file that's corrupt or something.

---

### Post by ubfoxi on 2008-01-31
I had this problem.  Run kcontrol from a console or using alt-f2.  Type kicker in the search box and select Panels from results.  Select the Hiding tab and change it to Only hide when a panel-hiding button is clicked.  Click Apply.  Kicker comes back.  Now you can change hiding back to what you want it to be.  :KS

---

