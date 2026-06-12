---
title: "Take the XFCE or Debian menu and plop it into E17?"
date: 2007-06-07
forum: Desktop Environments
---

### Post by botulismo on 2007-06-07
I installed E17 from  there and got everything set up looking good and so on but I'm kind of at a loss because Enlightenment didn't carry over any of my applications except for Firefox (which I'm sure is just there by default anyway.) Is there anyway to copy over the XFCE (or the Debian Menu - does it exit in XFCE?) so I can access all of my installed apps?

I like enlightenment so far but it severely impairs its usability for me be able to only browse the web with it. I am halfway satisfied with XFCE but I know I could squeeze more performance out of this laptop and enlightenment appears to run much faster... but I'm not motivated enough to track down everything and copy it over app by app.

Any ideas on a way to go about doing that?

---

### Post by pbw on 2007-06-07
e17genmenu will create a menu for you - [http://sourceforge.net/projects/e17genmenu](http://sourceforge.net/projects/e17genmenu)

Here's a deb someone made for it. i have no idea hjow well it works. - [http://ubuntuforums.org/showthread.php?t=127820](http://ubuntuforums.org/showthread.php?t=127820)

-- pbw

---

### Post by botulismo on 2007-06-07
Awesome. Well, something is better than nothing, in this case. Thanks for the info!

---

### Post by worldwithoutgurus on 2007-06-07
e17genmenu... Are you kidding ?
It's completely outdated and no longer used.

---

### Post by pbw on 2007-06-07
I just did a quick google for him. Like i said, i have no idea how well it works. I don't use e17. Figured a suggestion was better than no suggestion *shrug*.

---

### Post by RedSquirrel on 2007-06-07
> **botulismo said:**
> I installed E17 from  there and got everything set up looking good and so on but I'm kind of at a loss because Enlightenment didn't carry over any of my applications except for Firefox (which I'm sure is just there by default anyway.) Is there anyway to copy over the XFCE (or the Debian Menu - does it exit in XFCE?) so I can access all of my installed apps?

I like enlightenment so far but it severely impairs its usability for me be able to only browse the web with it. I am halfway satisfied with XFCE but I know I could squeeze more performance out of this laptop and enlightenment appears to run much faster... but I'm not motivated enough to track down everything and copy it over app by app.

Any ideas on a way to go about doing that?

I have only used E16, but I was able to generate a menu in the "usual" way:

Install the menu package:

```
sudo apt-get install menu
```and then run (in a terminal):

```
sudo update-menus
```

Give that a try.

---

