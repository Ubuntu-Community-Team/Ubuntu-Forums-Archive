---
title: "xfce don't save desktop for appz"
date: 2008-12-09
forum: Desktop Environments
---

### Post by grzeslaw on 2008-12-09
Hello

Iam looking for the solution from few weeks, and I don't saw any;/

What I would like to?:

When I start firefox and push it to the second desktop, I want, to firefox store the window, witch is located on. Is it possible in xfce? In kde when i click right mouse button on the window there is options what to store of the window setting. I would like to store only the desktops. Is it possible?

---

### Post by rnevins82 on 2008-12-09
Hi Grzeslaw

I got bored and went looking for a solution to your problem. I think I may have found it, I really hope this helps, as I use Kubuntu and have no idea how Xfce works, this got from the Xfce wiki pages.


Firefox jumps between workspaces, why?

When a new tab is opened from an external link in Firefox, it asks the WM to show the window containing the new tab. If the window that has requested to be raised is not on the current desktop, the Xfce Window manager will bring it to the current desktop by default. If you do not want this behavior, there is a hidden option to control this behavior. in ~/.config/xfce4/xfwm4/xfwm4rc you can put the following:

  activate_action=bring|switch|none

As the name suggests, the “bring” option moves the window requesting to be raised to the current workspace, the “switch” option switches workspaces, and the “none” option takes no action.


Here's the link.  [http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)

---

### Post by grzeslaw on 2008-12-09
thanks for answer.

Unfortunately this is not what Iam looking for. I'am lookin for "somethink" which store dekstop for the applications. For example. I use thunderbird on the 4th desktop, firefox on the second, and my xterminal on the first. The problem is, how to ascribe application to the specific desktop number. For example: When I start my xfce manger, I open the FF, which should open on second desktop, and when iopen the thunderbird, it should open on the 4th dekstop. 

Is it possible?

---

### Post by rnevins82 on 2008-12-09
You're wecome, sorry I was wrong though, lol.
Maybe if you browse the wiki pages for Xfce it'll help, I have no idea, lol.


Not much help am I? lol.

I really am trying though!

---

### Post by sisco311 on 2008-12-09
> **grzeslaw said:**
> thanks for answer.

Unfortunately this is not what Iam looking for. I'am lookin for "somethink" which store dekstop for the applications. For example. I use thunderbird on the 4th desktop, firefox on the second, and my xterminal on the first. The problem is, how to ascribe application to the specific desktop number. For example: When I start my xfce manger, I open the FF, which should open on second desktop, and when iopen the thunderbird, it should open on the 4th dekstop. 

Is it possible?
it's possible with devilspie.

install it:
```
sudo aptitude install devilspie
```

create a configuration file for firefox:
```
mkdir ~/.devilspie
```
```
mousepad ~/.devilspie/firefox.ds
```
> (if
(is (application_name) "Firefox")
(begin
(set_workspace 2)
(maximize)
)
)
add devilespie to the autostarted application and restart your session.

[https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie")
[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/")

---

### Post by grzeslaw on 2008-12-10
sisco311: THANKS! Your solution help me alot. Thanks you, I could use my WM, without any problems, and drawbacks. I use devilspie, and emplace my appz on desktops, whitch I want to. yeahh, now it's great hehe ;)

rnevins82: yes you help me too: thanks!

Now Iam using the devilspie to save desktop for app, and resolve problem witch jumping appz, witch xfwm4rc config option.

One more time; thanks a lot guys!

---

