---
title: "building my own ubuntu distribution?"
date: 2008-09-28
forum: Desktop Environments
---

### Post by hardyn on 2008-09-28
Curious if anybody could help me?

looking at doing a bit of a motion control project, and was curious if i could be pointed in the right direction for some help on trimming down the ubuntu environment (or building up from a text based environment).

I will be using the EMC2 for the motion control, they do provide a live disk based on 8.04; however, i don't want a full 8.04 environment.  it is a project, do i don't mind doing a little work, but will need an idea of what tools are available, and where i might be able to find some information.

my thought was to start with a 8.04 server, with real-time kernel, XCFE with its base tools (file manager, text editor, etc.) and of course EMC2... with not much more.  i would like to make my own usplash sequence as well.  using as much of the existing repos would be ideal.

I guess what i am trying to do is the same as those that created the special interest 'buntus.  ubuntu with some custom applications.

thanks for any help.

---

### Post by lykwydchykyn on 2008-09-28
Either the server disc or one of the alternate install discs will give you the ability to install with the old ncurses Debian installer.  Go through this install, and when you get to tasksel (the menu of what functions you want to install) just choose "standard system" and nothing else.

When it finishes, login, sudo to a root shell, and run aptitude.

If you just want a bare bones xfce install, the packages to grab would be xorg, xdm, and xfce4.

Hope that gets you started!

---

### Post by hardyn on 2008-09-29
Thanks for the help, i will check that out.  Would there be a way after i have something set up to my liking that i would be able to master an install CD?

Thanks again.

---

