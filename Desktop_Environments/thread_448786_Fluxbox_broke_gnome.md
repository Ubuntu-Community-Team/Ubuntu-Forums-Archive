---
title: "Fluxbox broke gnome"
date: 2007-05-19
forum: Desktop Environments
---

### Post by treak007 on 2007-05-19
I was using gnome as a desktop environment, then I installed fluxbox through the repos to be a secondary window manager. Fluxbux did not work properly and I uninstalled it, however when I attempted to use gnome again, it is slow to start up (maybe 5-10 minutes), it won't start up any of the session start-up programs till after a couple minutes and in general isn't working properly. Is anyone else having some trouble with fluxbox breaking gnome?

---

### Post by treak007 on 2007-05-19
nevermind..resolved...just had to reinstall fluxbox..sorry for wasting anyone's time.

---

### Post by kerry_s on 2007-05-19
Sounds like you need help help with fluxbox? is it the no menu thing? in gnome open the terminal and run> sudo update-menus < that should give you the menus in fluxbox.

You can do a forum search for fluxbox. Or you can just post them problem red squirrel will help you he's a master at fluxbox, i'm on xfce4 for the next couple of months. Taking a break from fluxbox. :)

---

### Post by RedSquirrel on 2007-05-19
> **treak007 said:**
> I was using gnome as a desktop environment, then I installed fluxbox through the repos to be a secondary window manager. Fluxbux did not work properly and I uninstalled it, however when I attempted to use gnome again, it is slow to start up (maybe 5-10 minutes), it won't start up any of the session start-up programs till after a couple minutes and in general isn't working properly. Is anyone else having some trouble with fluxbox breaking gnome?

> **treak007 said:**
> nevermind..resolved...just had to reinstall fluxbox..sorry for wasting anyone's time.

I haven't heard of this issue. Sounds strange. Oh well...

What was it about Fluxbox that wasn't working? I have a feeling (like kerry_s said) that you had no menu in Fluxbox... was that it? 

```
sudo update-menus
```will fix the problem. See the HOWTO in my sig for more gory details.

If you decide to play with Fluxbox some more, have a look around on ubuntuforums and don't hesitate to ask questions. You won't be wasting anyone's time. :)  

> **kerry_s said:**
> You can do a forum search for fluxbox. Or you can just post them problem red squirrel will help you he's a master at fluxbox, 

Thanks for the compliment. I've learned a large number of tricks from you and yabbadabbadont. ;)



> **kerry_s said:**
> i'm on xfce4 for the next couple of months. Taking a break from fluxbox. :)

How dare you! :lol:

By the way, I hope you're feeling better. I noticed in another thread you mentioned you were under the weather and I meant to say something then. :oops:

And nice avatar, although I'm gonna miss your two cents.

---

### Post by treak007 on 2007-05-20
Actually, i didn't have any menus, but that wasn't the problem. I quickly found the configuration file,edited that manually for a while, then found out I could generate them automatically. But that wasn't the problem, the problem was that since I kept gnome as a secondary desktop manager, gnome became unbearably slow after I installed fluxbox, also applications like gkrellm and gvim took forever to open in fluxbox, gkrellm took up to a couple minutes where gvim would hang completely.

---

### Post by kerry_s on 2007-05-20
> How dare you! 

By the way, I hope you're feeling better. I noticed in another thread you mentioned you were under the weather and I meant to say something then. 

And nice avatar, although I'm gonna miss your two cents. 

I had surgery and i'm on all kinds of meds, they screw up my brain. :p
It seems only certain times of the day, i can actually understand what i'm reading to help out. I seem to be starting to get use to them alittle, pretty soon i should be helping alot more, like before.

Yeah, i thought i would change some looks since, i'm sitting in front of the computer with my blurry eye's so instead of making the fonts huge so i can read them, i figured i'd play with the pics.

Well, i was starting to forget all the xfce4 stuff and it seems like more people were asking so i thought i'd better get to know xfce4 again, if i'm using it than it makes it easier to help.
So i'll leave the fluxbox stuff up to you for now. ;)

---

### Post by kerry_s on 2007-05-20
> **treak007 said:**
> Actually, i didn't have any menus, but that wasn't the problem. I quickly found the configuration file,edited that manually for a while, then found out I could generate them automatically. But that wasn't the problem, the problem was that since I kept gnome as a secondary desktop manager, gnome became unbearably slow after I installed fluxbox, also applications like gkrellm and gvim took forever to open in fluxbox, gkrellm took up to a couple minutes where gvim would hang completely.


Those are some weird effects, i never had a problem were fluxbox would slow down other applications or gnome itself. I don't know where to start.

---

### Post by treak007 on 2007-05-20
ok, i figured it out. First off, I compiled fluxbox from source, which made it quite a bit faster. Another thing I noticed was that I had set my wireless card to start on default in /etc/network/interfaces and I didn't realize it was already set to auto below, therefore it was hanging when loading this file. But yeah, this thread was kinda a waste, but I am definitely enjoying fluxbox now. Thanks.

---

### Post by kerry_s on 2007-05-20
Glad you figuered it out, RedSquirrel compiles his to, so if you get stuck again speak up, so he can help. ;)

---

### Post by treak007 on 2007-05-20
thanks. Is there any way for it to remember which system theme I was using and automatically use it, rather then forcing me to change it every startup? Thanks again.

edit: I saw your other post about gtk-theme-switch and such and tried those, however those changes wouldn't stay when i rebooted fluxbox. I am referring to the themes in fluxbox menu->user styles.

---

### Post by kerry_s on 2007-05-20
Yes in /.fluxbox/init look for

session.screen0.rootCommand:
add
session.screen0.rootCommand: fbsetbg -l

You meant background right?

Styles is this line->

session.styleFile:	path/to/style

It's weird yours is not remembering, have you tried using the reconfigure in the menu after you set it all up?

---

### Post by RedSquirrel on 2007-05-20
> **treak007 said:**
> First off, I compiled fluxbox from source, which made it quite a bit faster. 

Nice. The latest SVN, I hope... :)


> **treak007 said:**
> I am definitely enjoying fluxbox now. Thanks.

Great. Glad you got it sorted out.


> **treak007 said:**
> thanks. Is there any way for it to remember which system theme I was using and automatically use it, rather then forcing me to change it every startup? Thanks again.

edit: I saw your other post about gtk-theme-switch and such and tried those, however those changes wouldn't stay when i rebooted fluxbox. I am referring to the themes in fluxbox menu->user styles.

Yeah, like kerry_s said above, you should select **Fluxbox menu -> Reconfigure** (or 'Reload config' as it's called in some menus) to make it stick. I think that should solve it.

---

### Post by kerry_s on 2007-05-20
It just occuered to me that since you compiled yours you might not have used the fluxbox-generate-menu that came with it so you might not have the reconfigure entry. It looks like this->

```
   [reconfig] (Reconfigure)
```

a stock menu->

```
# This is an automatically generated file.
# Please see <file:/usr/share/doc/menu/README> for information.

# to use your own menu, copy this to ~/.fluxbox/menu, then edit
# ~/.fluxbox/init and change the session.menuFile path to ~/.fluxbox/menu

[begin] (Fluxbox)

# Automatically generated file. Do not edit (see /usr/share/doc/menu/html/index.html)

   [submenu] (Apps) {}
      [submenu] (Editors) {}
         [exec] (Geany) {/usr/bin/geany} </usr/share/pixmaps/geany.xpm>
         [exec] (OpenOffice.org Writer) {/usr/bin/oowriter} </usr/share/icons/gnome/32x32/apps/openofficeorg-21-writer.xpm>
      [end]
      [submenu] (Graphics) {}
         [exec] (OpenOffice.org Draw) {/usr/bin/oodraw} </usr/share/icons/gnome/32x32/apps/openofficeorg-21-draw.xpm>
         [exec] (OpenOffice.org Impress) {/usr/bin/ooimpress} </usr/share/icons/gnome/32x32/apps/openofficeorg-21-impress.xpm>
      [end]
      [submenu] (Net) {}
         [exec] (Firefox Web Browser) {firefox} </usr/share/pixmaps/firefox.xpm>
         [exec] (Opera) {/usr/bin/opera} </usr/share/pixmaps/opera.xpm>
      [end]
      [submenu] (Programming) {}
         [exec] (Tclsh8.4) { x-terminal-emulator -T "Tclsh8.4" -e /usr/bin/tclsh8.4} <>
         [exec] (TkWish8.4) {x-terminal-emulator -e /usr/bin/wish8.4} <>
      [end]
      [submenu] (System) {}
         [exec] (GDM Photo Setup) {gdmphotosetup} </usr/share/pixmaps/gdm.xpm>
         [exec] (GDM Setup) {gksu gdmsetup} </usr/share/pixmaps/gdm.xpm>
         [exec] (Graveman) {graveman} <>
         [exec] (Pstree) { x-terminal-emulator -T "Pstree" -e /usr/bin/pstree.x11} </usr/share/pixmaps/pstree16.xpm>
         [exec] (Synaptic Package Manager) {/usr/bin/gksu /usr/sbin/synaptic} </usr/share/synaptic/pixmaps/synaptic_32x32.xpm>
         [exec] (Top) { x-terminal-emulator -T "Top" -e /usr/bin/top} <>
      [end]
      [submenu] (Tools) {}
         [exec] (Conky) { x-terminal-emulator -T "Conky" -e /usr/bin/conky} <>
         [exec] (emelFM) {/usr/bin/emelfm} </usr/share/pixmaps/icon_dirparent.xpm>
         [exec] (fbpager) {/usr/bin/fbpager} <>
         [exec] (GTK+ 1.2 Theme Switch) {/usr/bin/switch} <>
         [exec] (GTK+ 2.0 Theme Switch) {/usr/bin/switch2} <>
         [exec] (gtklp) {/usr/bin/gtklp} <>
         [exec] (gtklpq) {/usr/bin/gtklpq} <>
      [end]
      [submenu] (Viewers) {}
         [exec] (GV) {/usr/bin/gv} </usr/share/pixmaps/mini-gv.xpm>
         [exec] (ImageMagick) {/usr/bin/display} <>
         [exec] (MPlayer) {/usr/bin/gmplayer} </usr/share/pixmaps/mplayer.xpm>
         [exec] (VLC media player) {/usr/bin/wxvlc} </usr/share/vlc/vlc.xpm>
      [end]
   [end]
   [submenu] (XShells) {}
      [exec] (XTerm) {xterm} <>
      [exec] (XTerm (Unicode\)) {uxterm} <>
   [end]

   [config] (Configuration)
   [submenu] (Styles) {}
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [workspaces] (Workspaces)
   [reconfig] (Reconfigure)
   [restart] (Restart)
   [exit] (Exit)

[end]

```

Here's my menu->

```
[begin] (Fluxbox)

[exec] (Run Program) {exec fbrun -nearmouse -text exec  -w 600 -h 50 -font verdana-18}
[exec] (Terminal) {exec xterm} 

[separator]

[exec] (File Manager) {exec emelfm} 

[submenu] (Net)
 [exec] (Opera) {exec opera}
 [exec] (Firefox) {exec firefox}
 [exec] (Pidgin) {exec pidgin}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {exec gksu synaptic}
 [exec] (Root-Emelfm) {exec gksu emelfm}
 [exec] (Root-run) {exec gksu}
[end]

[separator]

[submenu] (Settings)
  [exec] (Edit-menu) {exec geany -i ~/.fluxbox/menu}
  [exec] (Edit-startup) {exec geany -i ~/.fluxbox/startup}
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [exec] (Black) {exec fbsetroot -solid black}
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[submenu] (ScreenShots)
 [exec] (Snap) {exec scrot %T.jpg}
 [exec] (Select) {exec scrot -b -s %T.jpg}
 [exec] (Wait 5) {exec scrot -d 5 %T.jpg}
[end]

[separator]

[submenu] (Stock-menu)
 [exec] (Update-menus) {exec update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
[end]

[separator]

[exec] (Screen Off) {sleep 5; exec xset +dpms dpms force off }

[submenu] (Logout)
 [exit] (Exit)
 [exec] (Reboot) {exec sudo /sbin/reboot}
 [exec] (Shutdown) {exec sudo /sbin/shutdown now -h}
[end]


```

---

### Post by treak007 on 2007-05-21
Thank you both so much for your help.

---

