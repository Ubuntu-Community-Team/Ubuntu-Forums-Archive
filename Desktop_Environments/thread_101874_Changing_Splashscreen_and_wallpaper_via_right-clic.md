---
title: "Changing Splashscreen and wallpaper via right-click menus"
date: 2005-12-10
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-10
These are nautilus scripts. I posted a thread about nautilus scripts which contains more helpful informaion for those of you who find nautilus scripts useful. My post can be found at: [http://ubuntuforums.org/showthread.php?t=101870](http://ubuntuforums.org/showthread.php?t=101870)

Do you have a graphic that you'd like to have as a gnome wallpaper or splash screen? Here is an easy way to do that.

**Changing the desktop wallpaper by right-clicking on a graphic**

1) Open your favourite text editor and the following text to a new file:

```

#!/bin/bash
#
# Vers.: 1.00 11.02.2004
    title="Set as Wallpaper"
    choix="choice"
    type="value"
    gconf="key gconf"
    none="none"
    wallpaper="wallpaper"
    centered="centered"
    scaled="scaled"
    stretched="stretched"
case $LANG in
    fr* )
    title="DÃ©finir comme fond d'Ã©cran"
    choix="choix"
    type="valeur"
    gconf="clÃ© gconf"
    none="aucun"
    wallpaper="mosaÃ¯que"
    centered="centrÃ©"
    scaled="redimensionnÃ©"
    stretched="Ã©tirÃ©" ;;
esac
#
# fix gnome 2.2 bug
#
curpath=`echo $NAUTILUS_SCRIPT_CURRENT_URI | sed 's/file\:\/\///'`
cd $curpath
#
# choice with centered tile .....
#
if
    bckgrnd=`zenity --title "$title" --height 220 --list --radiolist --column "$choix" --column "$gconf" --column "$type" FALSE "none" "$none" FALSE "wallpaper" "$wallpaper" FALSE "centered" "$centered" TRUE "scaled" "$scaled" FALSE "stretched" "$stretched" 2>&1`
then
    gconftool-2 --type string --set /desktop/gnome/background/picture_options "$bckgrnd"
    gconftool-2 --type string --set /desktop/gnome/background/picture_filename "$curpath/$1"
fi

```

2. Make the file executable with chmod a+x filename
3. Move the new file to ~/.gnome2/nautilus-scripts/
4. When nautilus is re-started (I use killall nautilus to re-start), you can right-click on any graphic, choose Scripts->new_file and your desktop wallpaper will change immediately.


**Changing the gnome splashscreen by right-clicking on a graphic**

1) Open your favourite text editor and the following text to a new file:

```

#!/bin/bash
#
curpath=`echo $NAUTILUS_SCRIPT_CURRENT_URI | sed 's/file\:\/\///'`
cd $curpath
#
# gconf editor
#
gconftool-2 --type string --set /apps/gnome-session/options/splash_image "$curpath/$1"

```

2. Make the file executable with chmod a+x filename
3. Move the new file to ~/.gnome2/nautilus-scripts/
4.  When nautilus is re-started (I use killall nautilus to re-start), you can right-click on any graphic, choose Scripts->new_file and your Gnome splashscreen will change immediately.

---

### Post by anil_robo on 2005-12-11
Wonderful script! I wish the script menu would be visible onlly for graphic files. For example, I right click on a simple text file and still see "set as desktop background" which is kinda weird.

Still, wonderful script to make desktop decoration a matter of seconds! Should be included in Ubuntu installations by default! :)

---

### Post by ardchoille on 2005-12-11
[QUOTE=anil_robo]Wonderful script! I wish the script menu would be visible onlly for graphic files. For example, I right click on a simple text file and still see "set as desktop background" which is kinda weird.[/QUOTE]
Hmm.. I suppose one could write an if/then statement into the script to determine a certain action based on the file's mimetype, but I haven't learned how to detect mimetypes yet.

[QUOTE=anil_robo]Still, wonderful script to make desktop decoration a matter of seconds! Should be included in Ubuntu installations by default! :)[/QUOTE]
Thank you. I agree, Ubuntu should ship with a collection of various scripts.

---

### Post by ardchoille on 2005-12-11
Edit: Not applicable anymore.

---

### Post by anil_robo on 2005-12-11
The popularity of M$ windoze is frequently attributed to its "ease of use" and "customizability". With some default pre-installed scripts, even Linux can achieve both these goals.

I had some ideas for improving Ubuntu, but I could not post them on Launchpad.net. I guess they've stopped taking new ideas. Could someone tell me how do I inform the developers what ideas do I have in mind?

Thanks! :)

---

### Post by ardchoille on 2005-12-11
[QUOTE=anil_robo]I had some ideas for improving Ubuntu, but I could not post them on Launchpad.net. I guess they've stopped taking new ideas. Could someone tell me how do I inform the developers what ideas do I have in mind?

Thanks! :)[/QUOTE]
I tried to post the nautilus scripts under new ideas, but couldn't find the new ideas section either. I'd like to know how to inform the devs also.

---

