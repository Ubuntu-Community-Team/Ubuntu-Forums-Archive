---
title: "Window snapping in MATE"
date: 2014-10-20
forum: Desktop Environments
---

### Post by AnalBeard on 2014-10-20
I'm currently running Mint with Cinnamon but I'm thinking of moving to MATE (on Ubuntu), and I'm more or less sold apart from one deal breaker - window snapping with keyboard shortcuts.

I spend the majority of my day working over SSH, and my most-used functionality in Cinnamon is to snap windows with win+<arrow>. I can enable snapping in MATE, but I can't see a way of using shortcuts to control it - is this possible?

---

### Post by tgalati4 on 2014-10-20
What version of MATE are you using?  I couldn't find the snapping windows option.  Where did you activate it?

If you don't see a Snap-to-Windows action in the Keyboard Shortcuts preferences, then there is no way to assign a a keycode to it.

---

### Post by AnalBeard on 2014-10-21
> **tgalati4 said:**
> What version of MATE are you using?  I couldn't find the snapping windows option.  Where did you activate it?

If you don't see a Snap-to-Windows action in the Keyboard Shortcuts preferences, then there is no way to assign a a keycode to it.

1.8 on both Ubuntu and Mint - [http://www.mate-desktop.org/blog/2014-03-04-mate-1-8-released/](http://www.mate-desktop.org/blog/2014-03-04-mate-1-8-released/)

Looks like I need to do more digging, but I'm fairly sure there was nothing in the shortcut prefs :(

---

### Post by tgalati4 on 2014-10-21
You are correct.  Snapping windows is in Menu->Preferences->Windows.  And yes, I can see that it is handy on a wide-screen monitor and opening a lot of bash terminals.  I don't see a shortcut action to assign a keystroke to.  So that would be a request to the MATE (marco window manager) developers for a future release point release (perhaps 1.8.2).

How do you use the shortcut key?  How is it useful?  Do you use it to move an existing window?

A workaround is to assign the meta+<arrow> keys to scripts that perform the same functions.

---

### Post by vasa1 on 2014-10-21
Is MATE compatible with something window managers like Openbox (or Fluxbox)? Window snap via the keyboard is built into these WMs.

I got the impression that Metacity (from which marco is derived) is somewhat limited in this respect.

---

### Post by tgalati4 on 2014-10-22
I have *marco* but not *metacity* on my system.  So I presume that it is a fork that is specific to MATE.  According the to manual page:

> DESCRIPTION
       This manual page documents briefly marco.

       marco  is  a minimal X window manager aimed at nontechnical users and is designed to integrate well with the MATE desktop.  marco lacks some fea&#8208;
       tures that may be expected by traditional UNIX or other technical users; these users may want to investigate other available window managers  for
       use with MATE or standalone.


---

### Post by vasa1 on 2014-10-22
[https://wiki.archlinux.org/index.php/MATE#Use_a_different_window_manager_with_MATE](https://wiki.archlinux.org/index.php/MATE#Use_a_different_window_manager_with_MATE)

---

