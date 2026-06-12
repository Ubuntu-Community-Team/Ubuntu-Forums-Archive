---
title: "It suddenly stopped working!"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by FrogSpot on 2007-04-20
I was changing Icon styles in System/Theme Preferences/Theme Details/Icons and I clicked on an icon style and my icons all went away I was unable to recover them I had to press Ctrl-alt-backspace and tried to re-login. It wouldn't let me get past the initial splash screen. 

I can login as root but not into my normal profile. 

How do I go about changing my icon preferences back in my normal profile from the root?

---

### Post by mssever on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/108290](https://bugs.launchpad.net/bugs/108290) [br].[/br] ---------------------------- [br].[/br] [br].[/br]                 This has been filed as Ubuntu [bug 108290]("https://bugs.launchpad.net/bugs/108290"). FrogSpot and I discussed this over the phone. I'm posting the results here for the benefit of anyone else who may be experiencing such a problem.

The problem is that if you've installed custom cursor themes, the files go in ~/.icons. This is the same place that custom icon themes go. When you're in the theme manager, if you mistakenly choose a cursor theme from the list of icon themes, a bunch of stuff crashes. Worse, you can't log in normally until you fix the problem. I've tried this myself on my Edgy system and had the same issue. (If someone can try this in Feisty and report the results, it would be helpful.)

**Here's how to restore your system to normal after borking it:**[LIST=1]
[*]Log in using the failsafe terminal session.
[*]Type ```
gnome-theme-manager
```
[*]Choose a *real* icon theme.
[*]Close the theme manager and type ```
exit
```[/LIST]

---

