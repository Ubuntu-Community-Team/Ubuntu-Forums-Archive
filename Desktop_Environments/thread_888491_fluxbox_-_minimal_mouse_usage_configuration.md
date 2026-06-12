---
title: "fluxbox - minimal mouse usage configuration"
date: 2008-08-13
forum: Desktop Environments
---

### Post by jetsabel on 2008-08-13
hello, i have recently got myself a laptop but i don't like using the touchpad. so, i have spent a while configuring fluxbox and my core applications for minimal mouse usage.

i think i have been quite successful - to the point where i now boot up with the kernel mouse module deactivated (i have a keyboard shortcut to re-activate it)

is anyone else on here using a similar setup? perhaps we can exchange ideas :)

some of the features of the setup:
*clean look - no window decorations or taskbars
*window focus is shown by all unfocused windows being slightly transparent
*windows logo modifier handles all windows manager functions
*vi style hjkl keys for moving/resizing/focusing windows
*execute modifier handles all execute commands (on my korean keyboard i have mapped it to hangul_hanja, on the right of the spacebar)
*all execute commands use a wmctrl script to focus the window if it is running and start+focus it if not running
*only 2 workspaces simplifies take/send/go to workspace (becomes a toggle)
*peer to peer (screen+rtorrent, museek) and music (mpd) are daemons = invisible unless using them
*firefox vimperator  add-on allows easy web browsing without mouse

---

### Post by Anzan on 2008-08-13
Well, that's very interesting.

I've tried to use WMs like awesome (but I've no Super or Windows key on my ThinkPad keyboards) and ratpoison but am not proficient enough as a typist.

Most of what I do in Fluxbox is done by hotkeys and shortcuts.

I'm trying to learn vim.

So I'll give your key file a try.

Thank you.

---

### Post by jetsabel on 2008-08-13
cool! if you try it you will need to put 2 scripts in your ~/.fluxbox/scripts directory: find_app.sh from the fluxbox wiki [http://fluxbox-wiki.org/index.php/Keyboard_shortcuts](http://fluxbox-wiki.org/index.php/Keyboard_shortcuts) and find_name.sh which i hacked from find_app

below is find_name.sh, but i must stress, this is my first attempt at shell scripting so please check it yourself, dont blame me if it borks your system and let me know if you improve on it!


```

#!/bin/bash
# Find_name
# Amatureishly Adapted from Lucas van Staden's find_app.sh
WMCTRL=`which wmctrl`;
GREP=`which grep`;
APPLICATION=$1;
APPNAME=$3;
BASENAME=`basename $APPLICATION`;
BASENAME=`echo $BASENAME | tr "[:upper:]" "[:lower:]"`
FOUND=0;
function findwindow {
        IFS=$'\n';
        for RUNNING in `$WMCTRL -l -x`
        do
                if [ `echo $RUNNING | $GREP -c $APPNAME` -gt 0 ]
                then
                        $WMCTRL -a $APPNAME
                        FOUND=1;
                fi;
        done
}
findwindow $BASENAME $WMCTRL $GREP; 
if [ $FOUND -eq 0 ]
then
        $1 $2 $3 $4 $5 $6 $7 
        sleep 2;
        findwindow $BASENAME $WMCTRL $GREP;
        if [ $FOUND -eq 0 ]
        then
                sleep 3;
                findwindow $BASENAME $WMCTRL $GREP;
        fi
fi

```

---

### Post by Anzan on 2008-08-13
Thanks again.

---

### Post by Anzan on 2008-08-14
jetsabel, I've changed a few of the bindings (so as not to conflict with those in some apps and to execute specific programs) but I find yours were well thought out.

Thank you (yet again).

I'm amazed at how configurable, fast, and elegant that Fluxbox is.

---

