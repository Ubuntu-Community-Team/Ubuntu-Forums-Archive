---
title: "Window Manager doesn't start during login; succeeds after login"
date: 2009-04-26
forum: Desktop Environments
---

### Post by Kibz on 2009-04-26
I'm running Ubuntu 9.04 (Jaunty) on an Acer Aspire 5600 laptop. So far everything works, apart from the regressions in the xserver-xorg-video-intel driver for my 945GM card. However, I have enabled greedy migration, disabled tiling, applied the EXA optimizations, set up a script to fix MTRR and reverted to the 2.4 version of the driver, all as recommended in various threads and forums; these changes have brought my performance back on par with 8.10 (Intrepid), and improved, in some cases.

However, for some reason I cannot get compiz (or metacity, for that matter) to start on login properly. Once logged in I can open a terminal from the menu (gnome-panel's run application doesn't work) and start both compiz and metacity successfully. I can also add compiz to my session startups and have it work, but doing so confuses gnome-do and emerald. 

I've fiddled with all the related settings I could find in gconf to no avail. Compiz's crash dumping hasn't turned anything up, and there's nothing in my X error logs.

I was wondering if anyone had ideas on where to look next. Also, a pointer to somewhere that details when and how the window manager is called would be helpful, because I haven't found anything particularly helpful through Google et al.

Thanks!

Attached for reference:
xorg.conf
lspci -v | grep VGA
Xorg.0.log
fixmtrr.sh

EDIT: I figured out the problem and [posted the solution]("http://http://ubuntuforums.org/showpost.php?p=7610738&postcount=4").

---

### Post by linuxuser21 on 2009-04-26
Do you have the compiz-settings-manager installed?  If so, open it, go to Window decorations and in the command part, put: ```
emerald --replace
```.  That might unconfuse it.

---

### Post by Kibz on 2009-04-27
Thanks for the reply. It helped fix the problem I was having with emerald; confusion in this case meant that my autostart entry for emerald wasn't working. I suspect it was causing a race, and emerald was winning (losing?).

The original entry was '/usr/bin/compiz-decorator' (sans quotes), which is bash script that calls an appropriate decorator. By default in Jaunty it's set to use metacity or kwin rather than emerald, I decided to edit the script to prefer emerald for the sake of robustness, but using 'emerald --replace' worked, as well.

The main problem -- that the window manager isn't starting after login -- is still there, though, so any help in that direction would be appreciated.

Note: Gnome-do's confusion is that it is set to run as a dock, but ends up running in its default mode, presumably because there's no compositor running.

---

### Post by Kibz on 2009-07-13
I found the source of the problem, and it's pretty easy to fix. Very non-intuitive to find, though.

At some point *gnome-session* switched from using regular commands to using *.desktop launchers* for launching things like the panel and window manager. It looks for these files in a few locations, including _/usr/share/applications_ and _$HOME/.local/share/applications_. 

It also appears that *alacarte* (the menu application), or possibly just the freedesktop.org specification for menus, uses _$HOME/.local/share/applications_ for user-specific menu customizations.

For whatever reason, a copy of _/usr/share/applications/gnome-wm.desktop_ was made in my _$HOME/.local/share/applications_ directory which I suspect added *Window Manager* in my menu somewhere. I'm pretty anal about keeping my menus clean of stuff I don't use, so I would have gone in and disabled that entry which changed the *Hidden* setting in my fancy new _$HOME/.local/share/applications/gnome-wm.desktop_ file to True.

The last piece of the puzzle is that gnome-session stops searching after it finds an appropriate file, but it also doesn't run a launcher if it's hidden, so it was just straight-up skipping that step.

**There are two ways to fix it**, according to your preference:
[LIST]
[*]Change the *Hidden* setting in _$HOME/.local/share/applications/gnome-wm.desktop_ to false. This will (probably) put a *Window Manager* item in your applications menu somewhere.
[*]Remove _$HOME/.local/share/applications/gnome-wm.desktop_ entirely so that *gnome-session* has to find it elsewhere. If you're gonna do this, make sure you check for *Window Manager* (or _gnome-wm.desktop_) in _/usr/share/applications_ first.
[/LIST]

This should work for the *gnome-session* panel and file manager, too.

New user notes:
[LIST]
[*]_$HOME_ refers to your home directory, which is _/home/*yourusername*_. My sister qualifies as a new user, and she said she may not have been able to figure that out right away.
[*]To find _$HOME/.local/share/applications_ using the file browser, you'll need to show hidden files, since _.local_ is hidden.
[*]*Launcher* files (like _gnome-wm.desktop_) are generally listed in the file browser by a name they declare, rather than their file name. This particular file will probably be called *Window Manager*
[/LIST]

---

### Post by FFuser on 2009-08-08
Hi,

I had the same problem recently in karmic (after cleaning up my menus...)
 (I solved it with rm -rf .local/share/applications)

This seems to be a real bug in gnome(-session) did you file a bug report already?

EDIT: I filed one myself already: [http://bugzilla.gnome.org/show_bug.cgi?id=591224](http://bugzilla.gnome.org/show_bug.cgi?id=591224)

---

### Post by Kibz on 2009-08-10
Thanks for filing the bug report, Ffuser. I was/am in exam study mode when I did my last post, so I just wanted to make sure that the problem was out in the tubes before I forgot. I didn't think to file a bug report along with it.

---

### Post by eugen_nicoara on 2009-11-25
> **FFuser said:**
> Hi,

I had the same problem recently in karmic (after cleaning up my menus...)
 (I solved it with rm -rf .local/share/applications)


I had exactly the same problem and your solution save my installation for the moment. It's just that it happened on the released Karmic version ...

---

### Post by tcavaleiro on 2010-01-06
Hi all,

Thank you for the tip [Kibz]("http://ubuntuforums.org/member.php?u=461244") I was going "crazy" with this :) 
Last three months whenever I had time I was searching for some solution until I find this thread.

[FFuser]("http://ubuntuforums.org/member.php?u=81482"): Just for curiosity the bug you filled in [https://bugzilla.gnome.org/show_bug.cgi?id=591224](https://bugzilla.gnome.org/show_bug.cgi?id=591224) was closed as a "NOT A BUG"...

---

### Post by FFuser on 2010-01-16
@tcavaleiro:

Yeah, I know the bug was closed, and I understand why.

Gnome is following the specs. Since hidden=true in the .desktop files, means that the metacity.desktop does not exists (even if it exist physically on disk in /usr/share/whatever)


Still I do believe that gnome should fallback on a hardcoded binary if it can't find any desktop files that are window managers.

Still I do believe that removing an entry from your menu (in edit-menu/alacarte) should not have anything to do with your window manager on startup.

---

