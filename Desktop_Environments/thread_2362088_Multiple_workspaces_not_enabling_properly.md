---
title: "Multiple workspaces not enabling properly"
date: 2017-05-24
forum: Desktop Environments
---

### Post by timothylegg on 2017-05-24
Ubuntu 16.04 with gnome-flashback enabled.

In the past, I loved the 2x2 workspace switcher that for some crazy reason was decided to be bad and was disabled.  I followed a posting with instructions for enabling these workspaces:

[https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html](https://help.ubuntu.com/stable/ubuntu-help/shell-workspaces.html)

I completed these, and even chose the 2x3 arrangement just to humor the HOWTO's intentions.  I logged out and returned, but I still see a single workspace.  I have verified that multiple workspaces is still enabled.

In Figure 1, is a screenshot of the lower right hand corner.  The workplace switcher (acquired by right clicking on the workspace applet) only allows the ability to define rows, not columns, but despite this, clicking on the workspace applet with the left button has no perceivable effect, regardless of where you click on the applet.  It is as if it is only for appearance and no longer responds to the mouse.  The keyboard shortcuts for switching the workspace doesn't work either.

[ATTACH=CONFIG]275267[/ATTACH]
Figure 1, Workplace switcher.

I'm surprised to not see other people having this problem.  I would have  figured this feature being broken in this version would have everybody  up in arms.  Is there a workaround for bringing this feature back?


Timothy D Legg

---

### Post by howefield on 2017-05-24
I use the package unity-tweak-tool for setting up workspaces, among other things. It does mean installing it but it is useful for making changing many settings easily.

---

### Post by again? on 2017-05-26
The workspace switcher works fine, you're just changing the settings for the unity compiz session instead of the Flashback compiz session .
I ran 
```
dconf watch /
```
and then used ccsm to change the number of desktops which showed the the paths to use are
```
dconf write /org/compiz/profiles/Default/plugins/core/hsize
dconf write /org/compiz/profiles/Default/plugins/core/vsize
```
or simply use **compizconfig-settings-manager** (ccsm) which will adjust settings for whatever session you are in.

You don't need to change anything with the workspace switcher.
It will adjust to your compiz settings.

---

