---
title: "Middle mouse button pasting random stuff (Lubuntu / LXDE)"
date: 2017-06-08
forum: Desktop Environments
---

### Post by simonhk2 on 2017-06-08
Hi!

I installed Lubuntu (16.10) a few days ago and I'm having a super weird problem.

Clicking the middle mouse button pastes random text that I've typed in the past.
In other words... if I click the middle mouse button it pastes some text which is not the clipboard content, but some text I have recently typed and never copied.
For example if I type some changes in an HTML document and go to another document and hit the middle mouse button some of that previously typed text appears there, this is a huge problem as I'm accidentally pasting content from IMs, e-mails, websites and so on all across the place! :-(

I'm not sure what this is, seems more like a bug than a feature.

I would like my middle mouse button to behave in the default way and do nothing but allow me to scroll, I don't want it to paste random text.
I've looked at the mouse options in the GUI but not managed to find anything related to this.

Thank you.

// Simon

---

### Post by again? on 2017-06-09
It's not really random.
It is the primary **copy**/**paste** buffer.
Highlight **copy** with left mouse and **paste** with middle click.

There are various solutions floating around as shown [**HERE**]("https://askubuntu.com/questions/4507/how-do-i-disable-middle-mouse-button-click-paste") but most seem to disable the middle mouse button completely
so that things like closing browser tabs with middle click cease to work.

In the latest Gnome you can disable through a dconf setting
```
dconf write /org/gnome/desktop/interface/gtk-enable-primary-paste false
```
but in Lubuntu this wouldn't work.

The best solution I can give is invest in a basic gaming mouse where middle click isn't so sensitive to be accidentally triggered when scrolling.
I find middle click paste invaluable.

---

### Post by vasa1 on 2017-06-09
> **guber2 said:**
> ...
There are various solutions floating around as shown [**HERE**]("https://askubuntu.com/questions/4507/how-do-i-disable-middle-mouse-button-click-paste") but most seem to disable the middle mouse button completely
so that things like closing browser tabs with middle click cease to work.
...
A couple of solutions in the AU link are application-specific and, if OP is using Firefox as the browser, tweaking *about:config* can selectively turn off the paste function of the middle mouse button. Changing the default from *true* to *false* for "middlemouse.paste" would do the job. There's a setting in LibreOffice as well under *Tools > Options > LibreOffice > View*.

Of course, having a global solution would be the best.

---

