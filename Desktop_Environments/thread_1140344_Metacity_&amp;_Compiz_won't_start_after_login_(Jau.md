---
title: "Metacity &amp; Compiz won't start after login (Jaunty Upgrade)"
date: 2009-04-27
forum: Desktop Environments
---

### Post by HDave on 2009-04-27
I just upgraded to Jaunty and everything works pretty well except for one thing -- whenever I log into a gnome session, neither compiz nor metacity starts automatically.

If I start them manually using "compiz --replace" or "metacity --replace" they work fine.   

FWIW -- If I log into a KDE session everything works fine.

Any idea's as to what is broken with Gnome?

---

### Post by Inferiority Complex on 2009-09-18
Mine has broken today but I didn't change any of my settings or install any software.  I'm quite confused.

---

### Post by earthpigg on 2009-09-18
> **HDave said:**
> whenever I log into a gnome session, neither compiz nor metacity starts automatically.

what window manager _*does*_ start when you log in, then?

---

### Post by Mayfairy on 2009-09-19
Or do you mean compiz starts but without emerald borders? That seems to be pretty common.

---

### Post by Inferiority Complex on 2009-09-19
I haven't got emerald instaled but when I log in, I get borderless windows with no way of maximising or resizing them.  I can start metacity with the command line but when exiting the command line, metacity terminates also.  All my compiz effects are set up but nothing is applied to any windows which makes me suspect that it hasn't started either.

:?

---

### Post by earthpigg on 2009-09-19
workaround:

system -> preferences (or is it administration?) -> startup applications

add:

metacity --replace

---

### Post by Inferiority Complex on 2009-09-19
I have found a partial solution for this.

Whilst doing a little further searching, I stumbled upon another thread in these forums which brought the Metacity Compositor to mind.  Unfortunately, I cannot find the thread any longer (even in the browser history) but here's the gist:

I'd installed **Ubuntu Tweak** some time ago and had been looking through the settings the other day and enabled the metacity compositor checkbox.  A warning flashed up about how I should disable 'Desktop Effects' manually first.  I unchecked the box deciding that I'd best leave that setting alone.

If I go into the **Appearance Preferences** in Gnome, I can see that Desktop Effects have been disabled.  I just re-enable them and metacity and compix spring back into life.  Wahey!!!  :D:D:D

After a restart, I need to re-enable them again.

And again, and again...

I can't seem to get the setting to gain any permanence on my system.  :(

I did find this that suggests a workaround for what appears to be a bug in Metacity:
[https://bugs.launchpad.net/metacity/+bug/178953](https://bugs.launchpad.net/metacity/+bug/178953)

---

### Post by earthpigg on 2009-09-19
> **Inferiority Complex said:**
> 
If I go into the **Appearance Preferences** in Gnome, I can see that Desktop Effects have been disabled.  I just re-enable them and metacity and compix spring back into life.  Wahey!!!  :D:D:D

After a restart, I need to re-enable them again.

And again, and again...

I can't seem to get the setting to gain any permanence on my system.  :(


try adding 'compiz --replace' to system -> pref -> startup applications

---

### Post by Inferiority Complex on 2009-09-22
> **earthpigg said:**
> try adding 'compiz --replace' to system -> pref -> startup applications

Works a treat!

The Gnome Panel is invisible until I access one of the menu's whereupon is becomes visible again but I can live with that.

---

