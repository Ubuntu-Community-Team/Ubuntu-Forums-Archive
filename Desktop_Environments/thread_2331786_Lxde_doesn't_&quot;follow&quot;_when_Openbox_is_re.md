---
title: "Lxde doesn't &quot;follow&quot; when Openbox is resized in 16.04"
date: 2016-07-25
forum: Desktop Environments
---

### Post by franter on 2016-07-25
Hello,

Wanted to try Lubuntu on our little TV-PC instead of old Windows XP, but the desktop was too big for the screen. Happily Openbox can easily be resized exactly to fit the screen, but the LXDE desktop didn't "follow" the Openbox resizing and most of the Lxde menu is under the screen. Is there a way to get LXDE to "follow" Openbox when Openbox is resized to fit the screen?

One solution would be to choose a pure Openbox distribution, or install Openbox from Debian, but I quite like Lubuntu as I've used it quite a lot for some years.

---

### Post by DuckHook on 2016-07-25
What do you mean by "TV-PC"? Please describe your HW in detail, since your difficulties seem to stem from the interaction between your OS and this particular HW. For the sort of info we need, please see the link in my sig: *How to Ask for Help*

Please also rephrase what you mean by:> **franter said:**
> &#8230;the LXDE desktop didn't "follow" the Openbox resizing and most of the Lxde menu is under the screen. Is there a way to get LXDE to "follow" Openbox when Openbox is resized to fit the screen?Purely as an educated guess, I surmise that you are referring to the common overscanning issue, especially in light of your prior reference to a TV. If this is indeed the problem then, first, try turning off overscan in your TV settings. On some TVs it's not called "Overscan", but something else. You can Google how to do this for your specific TV model.

Note: XP is long past its end of life and is now a huge security hole just inviting you to get owned by some nasty scumbag prowling the Net. Either install some form of Linux or at least upgrade to Win7, which is still in support (though it's getting long in the tooth too).

---

### Post by &amp;KyT$0P# on 2016-07-25
It's possible to log in pure Openbox in Ubuntu, but the forum software does not allow me to explain how to do that.

EDIT Here's a screenshot of how to do it (this is the login screen of a Xubuntu system with Openbox installed):
[ATTACH=CONFIG]270344[/ATTACH]

---

### Post by vasa1 on 2016-07-25
Some posts on the Openbox session of Lubuntu: [https://ubuntuforums.org/showthread.php?t=2173126](https://ubuntuforums.org/showthread.php?t=2173126)

---

### Post by buzzingrobot on 2016-07-26
Openbox is LXDE's window manager, i.e., the thing that's responsible for drawing, moving, resizing, etc., the windows open on the display. So, there is no single "Openbox" to resize.

Hard to know without some info, but perhaps the display size is being set incorrectly?

---

### Post by franter on 2016-07-27
The HW is a Zotac Mag, Atom processor and Nvidia ION. The screen is a Panasonic plasma screen with full HD, and no it doesn't feature any overscan system that I know of.

Well I expect you all are young and don't remember the days when HW wasn't as automatic as today and that resizing the desktop was quite standard.

Openbox can easily be resized so that the window exactly fits the screen. This is also possible in Windows XP and prior versions, but as Windows is getting more and more Lite I don't know for later versions. Mac OSX hasn't this feature as I wanted to use a Mac Mini instead.

Back to Openbox, I've made the window to perfectly fit the screen, but the LXDE menus are not affected by the resizing of the Openbox window and stays mostly out of the screen.

In Windows or OSX his would clearly be a bug, but as in Lubuntu Lxde comes on top of Openbox maybe there is some way to stick Lxde to the Openbox window.

In the Lubuntu start menu, under "Preferences" there is an "Openbox Configuration Manager", so there is clearly a single Openbox to resize as I had no difficulty to resize the Openbox window to exactly fit the screen. But while rezizing Openbox the LXDE menus don't move at all, they stay mostly out of the screen. In Windows or OSX I would call this a bug as the Lxde menus should follow the Openbox window, but maybe there is some setting to make this possible?

---

