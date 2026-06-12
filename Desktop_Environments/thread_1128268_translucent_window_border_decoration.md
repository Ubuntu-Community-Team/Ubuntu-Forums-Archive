---
title: "translucent window border decoration"
date: 2009-04-17
forum: Desktop Environments
---

### Post by meanmrmustard on 2009-04-17
I'm running Hardy and am trying to figure out how to change a window decoration.
I have Compiz enabled though I'm not sure this isn't in some other configuration. I find nothing in Compiz settings that affects it.

The problem is the decoration that is on every window (every application) and also at the edges of a blank desktop. This design overlaps the window border like a shadow.

I've tried multiple times to upload a screenshot to imagebin but it doesn't seem to be working.

If you understand what I'm describing, please tell me where to go to change or eliminate this decoration

Thanks,
Mr M.

---

### Post by nortexoid on 2009-05-06
I've been wondering about how to disable this too. I don't like how background windows have translucent window borders.

---

### Post by mcduck on 2009-05-06
I assume you are using the default window decorator for compiz (GWD, which uses Metacity themes ) and not Emerald?

In that case you can disable window frame transparency with the following trick:

First press Alt-F2 and run "gconf-editor" (or use a terminal to start it). Use it to browse to apps/gwd, and then set both "metacity_theme_active_opacity" and "metacity_theme_shade_opacity" to "1".

These settings configure how transparent active/inactive windows can become, as a number between 0 (transparent) to 1 (opaque).

(In case you are using Emerald instead of GWD just use the Emerald Theme Manager to set the transparency.)

---

### Post by nortexoid on 2009-05-06
Thanks mcduck, that worked brilliantly.

Are there any other interesting tweaks/settings in the gconf editor that one should be aware of?

---

### Post by mcduck on 2009-05-06
> **nortexoid said:**
> Thanks mcduck, that worked brilliantly.

Are there any other interesting tweaks/settings in the gconf editor that one should be aware of?

Countless amounts. :D

Gnome pretty much has the idea of only showing the most commonly needed configuration options to the user, but this doesn't mean that there wouldn't be options at all. They are all accessible through gconf-editor. (I suppose the point is that most basic user's won't need /want these option s anyway, while advanced users, system admins and distribution developers can still use gcong to change them when they need to) Luckily it's pretty simple tool and most of the options have very good descriptions included.

Unless you have some specific changes in your mind I suggest just browsing through the options in gconf to find out if there's any option you like. You'll find that each application as it's own directory under "apps" and inside it are all the same options you have in the program's preferences plus often a couple of extra settings. Under "desktop/gnome" you'll find the settings for Gnome itself. The rest you are unlikely to need.

Examples of stuff you can do in gconf include enabling/disabling different desktop icons, changing the locations of buttons (close, minimize etc) on window frames, setting your lock screen dialog theme, setting Gnome to use less resources or tighter user interface, setting panel backgrounds and configuring their scaling & rotation, and configuring what programs should run as part of Gnome (window manager, file manager, panels etc.). In other words pretty much every setting Gnome and it's programs have is in gconf.

***
edit: I suppose I should add some of the settings people most often are asking for:

**apps/nautilus/desktop** - here you'll find options to enable/disable different icons like home, trash & my computer, and mounted drives, on desktop.
[B]
apps/update-notifier/auto_launch[/B] - disable this to change the update manager to the old system, showing icon in the notification area when updates are available instead of popping up the Update manager.

**apps/panel/global/lockdown** - enable this to lock the panel configurations. I've installed Ubuntu on many peoples computers and I've found that some of them have the habbit of messing their panels and accidentally removing applets from panels. Locking down the panel removes all options for changing the panel configurarions and locks all applets in their current places until you disable the lock again.

**apps/panel/toplevels/*nameofyourpanel*/** - in addition to tormal panel settings you can set hide/unhide delays and hidden size for panels here

**apps/panel/toplevels/*nameofyourpanel*/background** - advanced options for panel background. In case you need to fit, scale or rotate the panel background images.

**apps/gnome-session/logout_prompt** - enable/disable confirming before logging out

**apps/metacity/general** - lots of settings for Metacity, including "button_layout" which is nice if you are used to Mac style of having close, minimize & maximize buttons on the left end of the window titlebar..

**apps/gnome-screensaver/lock_dialog_theme** - sets the log in dialog where you type your password after locking the screen or suspending the computer.

**desktop/gnome/interface/toolbar_style** - many people complain that the UI in Gnome wastes too much space. set this to "small-toolbar" to rduce the amount of whitespace a bit. Really useful if you have very small display, like a netbook.

---

### Post by nortexoid on 2009-05-06
Nice. Thanks for the list of useful settings. I recall using the gconf-editor to place the window buttons on the left rather than right side of the border, but didn't know it had settings for all sorts of things.

Do you know if there is a way to change the metacity window border color? I couldn't find it while digging around. The Appearance interface allows one to change the window colors but it doesn't affect the borders (unless your theme has them "locked" together).

---

### Post by mcduck on 2009-05-06
> **nortexoid said:**
> Nice. Thanks for the list of useful settings. I recall using the gconf-editor to place the window buttons on the left rather than right side of the border, but didn't know it had settings for all sorts of things.

Do you know if there is a way to change the metacity window border color? I couldn't find it while digging around. The Appearance interface allows one to change the window colors but it doesn't affect the borders (unless your theme has them "locked" together).

Window border color is defined by the Metacity theme and there's no other way to set it. The theme can then either hardcode the color to whatever the theme designer wants, or to use colors from current GTK theme.

If you want, you can try editing the Metacity theme itself, they are just plain text files. But Metacity themes are not the easiest ones to figure out so you'll probably just want to try to find a theme you like instead.

(Of course you could use Metacity theme that uses GTK colors, and a GTK theme that supports defining your own colors..)

---

### Post by gpwil1 on 2010-11-23
Thanks, this is very helpful!

I'm trying to do this for a customized distro to change theme to Clearlooks with controls on the right, as you would get doing it through the gui, unfortunately I dont have use of the gui, so I have done the following:

gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Clearlooks"

gconftool-2 --type string --set apps/metacity/general/button_layout ":minimize,maximize,close"

but now the window border is still the ambience theme, any idea how to change this to the clearlooks?

Cheers!


edit - nevermind, found it:

# Change the metacity theme (window borders)
gconftool-2 --type=string -s /apps/metacity/general/theme Clearlooks

---

