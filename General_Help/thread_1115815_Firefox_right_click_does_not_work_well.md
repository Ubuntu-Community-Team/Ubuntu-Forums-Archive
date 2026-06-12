---
title: "Firefox right click does not work well"
date: 2009-04-04
forum: General Help
---

### Post by crazyfuturamanoob on 2009-04-04
When I press right mouse button in firefox, it might show a pop-up menu, or then it selects randomly something from the menu even before the menu shows up.

This happens often and it is very annoying when I have to try it 5 times before I see the menu. Any solutions?

---

### Post by Confuseling on 2009-04-04
Install this add-on as a workaround.

[https://addons.mozilla.org/en-US/firefox/addon/39](https://addons.mozilla.org/en-US/firefox/addon/39)

---

### Post by crazyfuturamanoob on 2009-04-04
How is that supposed to fix it?

---

### Post by Confuseling on 2009-04-04
Presumably it 'steals' the input when you click the right button - as if you were going to do a gesture. You don't do a gesture, and it passes the 'right click' signal to firefox. Its code works, the firefox code, presently, doesn't.

If you don't want gestures you can probably disable them all (or perhaps all except one) in the add-on, and it will still fix the bug.

Try it ;)

What's the worst that can happen?

---

### Post by lovinglinux on 2009-04-04
> **Confuseling said:**
> Presumably it 'steals' the input when you click the right button - as if you were going to do a gesture. You don't do a gesture, and it passes the 'right click' signal to firefox. Its code works, the firefox code, presently, doesn't.

If you don't want gestures you can probably disable them all (or perhaps all except one) in the add-on, and it will still fix the bug.

Try it ;)

What's the worst that can happen?

IMO this is not a good workaround. It will be annoying, since the extension will try to understand the gesture every time.

The best workaround I have found is to hold the right button for a while (1 or 2 secs) instead of just clicking, then moving to the context menu options.

---

### Post by Confuseling on 2009-04-04
> **lovinglinux said:**
> IMO this is not a good workaround. It will be annoying, since the extension will try to understand the gesture every time.
...

Why is that a problem? You mean in terms of overhead, or randomly triggering gestures by mistake?

---

### Post by paradigm2 on 2009-04-04
> **lovinglinux said:**
> IMO this is not a good workaround. It will be annoying, since the extension will try to understand the gesture every time.

The best workaround I have found is to hold the right button for a while (1 or 2 secs) instead of just clicking, then moving to the context menu options.

Do these problems (this one and another here) :

[http://ubuntuforums.org/showthread.php?t=1115868](http://ubuntuforums.org/showthread.php?t=1115868)

Also occur in previous versions on Ubuntu such as Fx 3.0.7 or is this new?  I wouldn't know I just moved over to *nix again from windows right when 3.0.8 was released but I do know these did not occur at all in windows with 3.0.8.  If a revert will work, I will probably do it despite the security risks.

---

### Post by lovinglinux on 2009-04-04
> **paradigm2 said:**
> Also occur in previous versions on Ubuntu such as Fx 3.0.7 or is this new?  I wouldn't know I just moved over to *nix again from windows right when 3.0.8 was released but I do know these did not occur at all in windows with 3.0.8.  If a revert will work, I will probably do it despite the security risks.

This is not new. It comes and go, with no apparent reason. I think this could be a gnome issue, because sometimes it happens also when using nautilus.

---

