---
title: "Many Fluxbox problems"
date: 2010-07-20
forum: Desktop Environments
---

### Post by aeronotix on 2010-07-20
Ok this could be a long thread.

I installed Ubuntu on a laptop and was not happy with the performance, so I installed Fluxbox and was totally impressed with it. However, certain programs do not load when I want them to and I can't seem to figure out why.

I have edited the file in /usr/bin/startfluxbox

Here is what I have done```


#!/bin/sh

command="`basename \"$0\"`"
fluxdir="$HOME/.fluxbox"
startup="$fluxdir/startup"

while [ $# -gt 0 ]; do
    case "$1" in
        -c|--config)
            if [ $# -lt 2 ]; then
                echo "$command:error, missing argument"
                exit 1
            fi
            shift
            startup=$1
        ;;
        -h|--help) cat <<EOF
Usage: $command [-h] [-c startupfile]
EOF
        exit
        ;;
    esac
    shift
done

if [ -x "$startup" ]; then
    exec "$startup"
elif [ -r "$startup" ]; then
    exec sh "$startup"
else
    if [ ! -d $fluxdir ]; then
        mkdir -p "$fluxdir/backgrounds" "$fluxdir/styles" "$fluxdir/pixmaps"
    fi
    if [ ! -r "$startup" ]; then
        ( cat << EOF
#!/bin/sh
#
# fluxbox startup-script:
#
# Lines starting with a '#' are ignored.

# Change your keymap:
xmodmap "$HOME/.Xmodmap"

#set the background
fbsetbg /skynet/Downloads/Sunset.jpg &

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &
# We start the network manager
nm-applet &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

fluxbox &
fbpid=$!

sleep 1
{
   # Applications you want to run after fluxbox has started
   # MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN & AT THE END.
   # ipager &
   # gkrellm2 &
     nm-applet &
     gnome-panel &
} &
 
wait $fbpid
# or if you want to keep a log:
# exec fluxbox -log "$fluxdir/log"
EOF
    ) > "$startup"
    fi
    chmod 644 "$startup"
    exec sh "$startup"
fi
```

Maybe another script is being used in place of this one? Also what about that # before the !/bin/sh?

Ok, and another thing.

Since at the moment I have to manually load the gnome-panel, when I load this the theme I had from before doesn't load until I go to System>Preferences>Appearance as soon as I load that Appearance manager, boom, the theme appears, and the terminal that I opened up gnome-panel with spits out..

```
skynet@skynet-laptop:~$ gnome-panel
** Message: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

** (gnome-panel:5085): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

(gnome-appearance-properties:5187): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:5187): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
/usr/share/themes/Loma/gtk-2.0/gtkrc:47: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Loma/gtk-2.0/gtkrc:49: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Loma/gtk-2.0/gtkrc:50: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Taqua/gtk-2.0/gtkrc:54: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/Taqua/gtk-2.0/gtkrc:55: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Taqua/gtk-2.0/gtkrc:56: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/usr/share/themes/Taqua/gtk-2.0/gtkrc:57: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/usr/share/themes/Murrina-Tangoesque/gtk-2.0/gtkrc:50: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrina-Tangoesque/gtk-2.0/gtkrc:51: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrina-Tangoesque/gtk-2.0/gtkrc:63: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/MurrinaCandido/gtk-2.0/gtkrc:84: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:45: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:51: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Sky/gtk-2.0/gtkrc:54: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:86: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:134: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:187: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:249: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBlu/gtk-2.0/gtkrc:294: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaCappuccino/gtk-2.0/gtkrc:41: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaLoveGray/gtk-2.0/gtkrc:50: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaVerdeOlivo/gtk-2.0/gtkrc:45: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaChrome/gtk-2.0/gtkrc:83: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaStormCloud/gtk-2.0/gtkrc:53: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:54: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:60: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:63: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:77: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:89: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:105: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:121: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:136: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:151: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:172: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:206: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:233: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:257: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Murrine-Gray/gtk-2.0/gtkrc:272: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/MurrinaAzul/gtk-2.0/gtkrc:75: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaAzul/gtk-2.0/gtkrc:78: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaEalm/gtk-2.0/gtkrc:47: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Kiwi/gtk-2.0/gtkrc:78: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/Kiwi/gtk-2.0/gtkrc:82: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/MurrinaCandy/gtk-2.0/gtkrc:46: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaAquaIsh/gtk-2.0/gtkrc:50: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaNeoGraphite/gtk-2.0/gtkrc:52: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaBleu/gtk-2.0/gtkrc:85: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
/usr/share/themes/MurrinaCream/gtk-2.0/gtkrc:83: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:54: Unable to locate image file in pixmap_path: "stock_bottom.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:59: Unable to locate image file in pixmap_path: "stock_first.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:64: Unable to locate image file in pixmap_path: "stock_last.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:69: Unable to locate image file in pixmap_path: "stock_top.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:74: Unable to locate image file in pixmap_path: "stock_left.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:79: Unable to locate image file in pixmap_path: "stock_down.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:84: Unable to locate image file in pixmap_path: "stock_right.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:89: Unable to locate image file in pixmap_path: "stock_up.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:94: Unable to locate image file in pixmap_path: "stock_cancel.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:99: Unable to locate image file in pixmap_path: "stock_apply.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:104: Unable to locate image file in pixmap_path: "stock_cancel.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:109: Unable to locate image file in pixmap_path: "stock_ok.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:114: Unable to locate image file in pixmap_path: "stock_apply.png"
/usr/share/themes/TropicBomb/gtk-2.0/gtkrc:119: Unable to locate image file in pixmap_path: "stock_refresh.png"


```

If anyone could shed some light on my situation I would greatly appreciate it!

---

### Post by aeronotix on 2010-07-22
bump

---

### Post by aeronotix on 2010-07-22
Sheeeeit

I was editing the wrong startup file, I should have been editing ~/.fluxbox instead of the one I was doing.
OK

Now we have the nm-applet and gnome-panel running on startup, but the theme problem still persists, and we also have two error messages appearing when I start the fluxbox session.

Time for some more reading!

---

### Post by urukrama on 2010-07-22
If you would like to use Gnome applications to set the theme, you can load *gnome-settings-daemon* when you start fluxbox (just add  that on a line in your start file). Whenever you click on the Appearance menu entry of Gnome-panel, it will launch gnome-settings-daemon if it is not already running, which explains why suddenly your themes work.

Gnome-settings-daemon controls more than just your Gtk theme, though. It also sets the icons, cursor theme, fonts, and wallpaper. If you don't want that (and want to control some of these appearance aspects in a different way) there are other applications available. If speed and resource usage is a concern, gnome-settings-daemon is also not the lightest option.

If you want to set your Gtk theme differently, this might also help: [http://urukrama.wordpress.com/openbox-guide/#Gtkthemes](http://urukrama.wordpress.com/openbox-guide/#Gtkthemes) (though this is about Openbox most of it applies to Fluxbox).

---

### Post by urukrama on 2010-07-22
> **aeronotix said:**
> 
Since at the moment I have to manually load the gnome-panel, when I load this the theme I had from before doesn't load until I go to System>Preferences>Appearance as soon as I load that Appearance manager, boom, the theme appears, and the terminal that I opened up gnome-panel with spits out..

You don't need to worry much about these errors. It just means that the Murrine Gtk engine (which allows you to use Murrina themes correctly) is a newer version than some of your Murrine themes were written for. The Murrine engine has changed considerably and uses a different syntax now than when these themes were created (and that is why these error messages say that a certain term "is no longer supported and will be ignored"). Some of your Murrine themes may not be properly displayed, but that is about all.

---

### Post by aeronotix on 2010-07-23
Ok, yeah.

About 20 seconds after this post I added the gnome-settings-daemon to my startup file and that was working great.

The only thing I am missing is the Window List applet.

When I try to load it manually I receive an error.

Any workaround?

---

