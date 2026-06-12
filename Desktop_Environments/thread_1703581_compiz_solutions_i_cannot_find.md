---
title: "compiz solutions i cannot find"
date: 2011-03-09
forum: Desktop Environments
---

### Post by maja_z on 2011-03-09
Hi there!
I've got a few questions about compiz that I can't figure out:

1. I don't seem to have an option to add mouse key bindings to the "unfold cube" action in the desktop cube plugin. (There are only three keyboard bindings available there: unfold, next slide and previous slide. I have no idea what the last two are meant to do though!?). I do use the mouse to rotate the cube, but I would love to be able to use it to unfold it and then scroll right and left. Is that possible?

2. On my old install I managed to find a plug-in that would stretch the active window to the full height of the screen. Just snap it to the top and bottom if that makes sense. Now for some reason I can't find it anywhere? Any tips would be well appreciated!

Thanks!

(Oh, I'm on ubuntu 10.04, gnome 2.30.2, compiz 0.8.4 and and compiz settings manager 0.8.2)

---

### Post by false truths on 2011-03-09
For the Unfold Cube plugin, Next Slide will move you one desktop to the right. Previous Slide will move you one desktop to the left.

As far as vertically maximising windows, I believe that is a metacity function. I don't know if it's the default in 10.04, but in 10.10 when I middle-click the maximise button it only maximises vertically, and when I right-click it, it only maximises horizontally.

---

### Post by maja_z on 2011-03-09
Thanks false truths, that solved question 2! I didn't even know I had metacity :) is there any way to change those settings as well?

[edit: found the settings (if any other newbies might be interested: in the terminal type gconf -editor, then go to apps | metacity | window_keybindigs and look for maximize_horizontally and maximize_vertically where you can set the bindings. still not sure how metacity and compiz work side by side without getting into each other's way? i mean it would make more sense to edit these settings in one place only?]

But about the cube: whatever i set as the bindings for 'prev slide' and 'next slide' those keys do nothing. But when I unfold the cube using Ctrl+Alt+down arrow I can then release the down arrow and use the left and right arrows to scroll through the desktops.
But is there any way I could do that same thing with a mouse?

---

### Post by false truths on 2011-03-09
I looked at Desktop Cube and Rotate Cube again. If you use Unfold Cube, you're able to click-and-drag the unfolded cube to one side or the other to change desktops. You're also able to use the left and right keys. You can only do this with the Rotate Cube plugin enabled, though.

Another option is what I prefer to use: Expo. You can bind this to a mouse action, screen edge, or key command, and it'll pan out and show you all your desktops at once, letting you switch them with your mouse or keyboard.

---

### Post by Copper Bezel on 2011-03-09
> [edit: found the settings (if any other newbies might be interested: in the terminal type gconf -editor, then go to apps | metacity | window_keybindigs and look for maximize_horizontally and maximize_vertically where you can set the bindings. still not sure how metacity and compiz work side by side without getting into each other's way? i mean it would make more sense to edit these settings in one place only?]

Much of the more granular behavior of the Gnome desktop can be configured only in gconf-editor, which is 99% of why Ubuntu Tweak exists. There's a GUI configuration screen for Metacity in the ubuntu-tweak package that doesn't require any typing. 

Maximize Vertically (which is just a *godsend *on the modern widescreen desktop) can also be set to a Compiz keybinding. I really wish it was an available window decorator button in Metacity (like close, menu, maximize, and minimize) but I'm glad to hear that it's back to being enabled by default as a titlebar action. (At one time, I think it was the default titlebar double-click action.)

---

### Post by maja_z on 2011-03-09
> I looked at Desktop Cube and Rotate Cube again. If you use Unfold Cube, you're able to click-and-drag the unfolded cube to one side or the other to change desktops. You're also able to use the left and right keys. You can only do this with the Rotate Cube plugin enabled, though.See there. That's not how mine works! 1st of all I do have both Desktop Cube and Rotate Cube enabled.. Then if my Unfold cube binding is the default Ctrl+Alt+down arrow, I can keep holding down Ctrl+Alt and use right and left keys to scroll. I cannot however use the mouse at this point. Its just not responding!? Also, I noticed, if I change the Unfold cube binding to sth. else, then the Ctrl+Alt+right or left does not work any more. Not sure I understand the logic here? Seems like something is off though?

What I don't get is that practically every other plugin in compiz has (in the settings manager anyway, that is what I'm using) a dozen possible mouse bindings! At least the same number of keyboard and mouse bindings. But Desktop Cube has only three keyboard bindings and no mouse ones!?

> Another option is what I prefer to use: Expo. You can bind this to a mouse action, screen edge, or key command, and it'll pan out and show you all your desktops at once, letting you switch them with your mouse or keyboard.Yeah, Expo is neat, but I really like the fact that unfold cube uses my background - which looks great because I have semi-transparent desktops, so unfolding the cube makes a rather seamless transition. If there's a way to include the background in Expo?

> Maximize Vertically (which is just a *godsend *on the modern widescreen desktop) can also be set to a Compiz keybinding..Can it? Where? That was my original question really, I can't find it anywhere?

Btw, all this has got me thinking. Is it right that I have both metacity and compiz working at the same time? Is it possible that that is causing some incosistencies?

---

### Post by Copper Bezel on 2011-03-09
> Can it? Where? That was my original question really, I can't find it anywhere?

It's under the General Options plugin.

> Btw, all this has got me thinking. Is it right that I have both metacity and compiz working at the same time? Is it possible that that is causing some incosistencies?

Compiz integrates really nicely with Metacity. It's supposed to supersede Metacity settings, but I've seen problems where both have a keybinding for the same keystroke.

---

### Post by maja_z on 2011-03-10
> It's under the General Options plugin.Man, that was obvious. Thanks Copper Bezel!

Still looking for a mouse key way of unfolding the cube! Anyone?

---

### Post by mcduck on 2011-03-11
> **Copper Bezel said:**
> It's under the General Options plugin.



Compiz integrates really nicely with Metacity. It's supposed to supersede Metacity settings, but I've seen problems where both have a keybinding for the same keystroke.

Well, actually Compiz is just pulling the configured shortcuts & theme from Metacity. (Assuming you have right Compiz plugins enabled, and are using GWD as the decorator plugin in Compiz)

They can't be used at the same time. You can only have one window manager running at a time. Both are installed by default, though, and the Visual effects-options in the Appearance dialog switch between running Metacity (Visual effects set to "None" and two pre-configured Compiz setups (Normal and Extra).

---

### Post by mcduck on 2011-03-11
> **maja_z said:**
> Hi there!
I've got a few questions about compiz that I can't figure out:

1. I don't seem to have an option to add mouse key bindings to the "unfold cube" action in the desktop cube plugin. (There are only three keyboard bindings available there: unfold, next slide and previous slide. I have no idea what the last two are meant to do though!?). I do use the mouse to rotate the cube, but I would love to be able to use it to unfold it and then scroll right and left. Is that possible?

2. On my old install I managed to find a plug-in that would stretch the active window to the full height of the screen. Just snap it to the top and bottom if that makes sense. Now for some reason I can't find it anywhere? Any tips would be well appreciated!

Thanks!

(Oh, I'm on ubuntu 10.04, gnome 2.30.2, compiz 0.8.4 and and compiz settings manager 0.8.2)
You already got the answer for 2. question, so here's for the point 1....

The Cube plugin itself indeed only has a keyboard shortcut option for unfold. If you want similar functionality, but using mouse, you have to use the Expo plugin.

Of course it *would* be nice if the Cube plugin had other than just keyboard shortcuts, or if Expo would use the Skydome image...

---

### Post by Copper Bezel on 2011-03-11
You can get around it, though. You can set an xdotool command to a button binding that runs the keystroke to unfold the cube. So, say the keystroke was Alt+Space, then you could put

```
xdotool keydown "Alt" key "Space" keyup "Alt"
```

as a command with a binding to Upper Right + Button1, and clicking the screen corner would unfold the cube.

> Well, actually Compiz is just pulling the configured shortcuts & theme from Metacity. (Assuming you have right Compiz plugins enabled, and are using GWD as the decorator plugin in Compiz)

They can't be used at the same time. You can only have one window manager running at a time.

Well, it still confused Compiz greatly when I had certain shortcuts assigned in Metacity and then tried to override them in Compiz's settings. And Compiz inherits all of the relevant Metacity behaviors in gconf-editor, not just the theme, which seems like fairly slick integration to my mind, and that's what I was referring to, although I should have been more specific. 

I wasn't certain whether or not any part of Metacity was still running with Compiz, so thanks for the information there.

---

### Post by Copper Bezel on 2011-03-11
Hey wait, question then:

So if Compiz does all of the window decoration, why does it default to Emerald in XFCE instead of using my Metacity theme and settings? Just curious. = )

---

### Post by Krytarik on 2011-03-11
> **Copper Bezel said:**
> Hey wait, question then:

So if Compiz does all of the window decoration, why does it default to Emerald in XFCE instead of using my Metacity theme and settings? Just curious. = )
Technical answer :-D:

I believe Compiz' decorator check ends up where I marked:

/usr/bin/compiz-decorator:
```
#!/bin/sh
COMPIZ_BIN_PATH=/usr/bin/
KWIN=`which kwin`
METACITY="/usr/bin/metacity"

#
# Default to gtk/kde(4)-window-decorator
#
USE_EMERALD="yes"
DECORATOR=""

#Do not leave users without decoration if decorator fails
if [ "$DESKTOP_SESSION" = "kde" ]; then
    FALLBACKWM="${KWIN}"
else
    FALLBACKWM="${METACITY}"
fi
FALLBACKWM_OPTIONS=" --replace"

#
# Set to yes to enable verbose
#
VERBOSE="yes"
 
#
# Echos the arguments if verbose
#
verbose()
{
    if [ "x$VERBOSE" = "xyes" ]; then
        printf "$*"
    fi
}

# Read configuration from XDG paths
if [ -z "$XDG_CONFIG_DIRS" ]; then
    test -f /etc/xdg/compiz/compiz-manager && . /etc/xdg/compiz/compiz-manager
else
    test -f $XDG_CONFIG_DIRS/compiz/compiz-manager && . $XDG_CONFIG_DIRS/compiz/compiz-manager
fi

if [ -z "$XDG_CONFIG_HOME" ]; then
    test -f $HOME/.config/compiz/compiz-manager && . $HOME/.config/compiz/compiz-manager
else
    test -f $XDG_CONFIG_HOME/compiz/compiz-manager && .  $XDG_CONFIG_HOME/compiz/compiz-manager
fi

# start a decorator
if [ -x ${COMPIZ_BIN_PATH}emerald ] && [ "$USE_EMERALD" = "yes" ]; then
    DECORATOR=emerald
elif [ -x ${COMPIZ_BIN_PATH}gtk-window-decorator ] && [ -n "$GNOME_DESKTOP_SESSION_ID" ]; then
    DECORATOR=gtk-window-decorator
elif [ -x ${COMPIZ_BIN_PATH}kde-window-decorator ] && [ -n "$KDE_FULL_SESSION" ]; then
    DECORATOR=kde-window-decorator
elif [ -x ${COMPIZ_BIN_PATH}kde4-window-decorator ] && [ x$KDE_SESSION_VERSION = x"4" ]; then
    DECORATOR=kde4-window-decorator
fi

# fall back to any decorator that is installed
if [ -z "$DECORATOR" ]; then
    verbose "Couldn't find a perfect decorator match; trying all decorators\n"
[B][COLOR=Red]    if [ -x ${COMPIZ_BIN_PATH}emerald ]; then
        DECORATOR=emerald
[/COLOR][/B]    elif [ -x ${COMPIZ_BIN_PATH}gtk-window-decorator ]; then
    DECORATOR=gtk-window-decorator
    elif [ -x ${COMPIZ_BIN_PATH}kde-window-decorator ]; then
    DECORATOR=kde-window-decorator
    elif [ -x ${COMPIZ_BIN_PATH}kde4-window-decorator ]; then
    DECORATOR=kde4-window-decorator
    fi
fi

if [ -n "$DECORATOR" ]; then
    verbose "Starting ${DECORATOR}\n"
    exec ${COMPIZ_BIN_PATH}$DECORATOR "$@"
else
    verbose "Found no decorator to start\n"
    exec $FALLBACKWM $FALLBACKWM_OPTIONS
fi

```

---

### Post by Copper Bezel on 2011-03-11
Yeah, I looked through the script, but there didn't seem to be anything to tell it whether or not the current *session *was running Metacity (or "GTK Window Decorator", apparently), although that you've highlighted is the most likely bit. I'll have to try running it with -v.

---

### Post by Krytarik on 2011-03-11
> **Copper Bezel said:**
> but there didn't seem to be anything to tell it whether or not the current *session *was running Metacity (or "GTK Window Decorator", apparently)
Honestly, Compiz doesn't care about what *was*. It just runs its stuff. ;-)

---

