---
title: "Different Wallpapers in Different Workspaces..   Why Not?"
date: 2016-05-26
forum: Desktop Environments
---

### Post by liberatio-spero on 2016-05-26
Hi Guys,

As a relatively inexperienced user I'm starting to find my way around 16.04.

It's a very nice experience,  but the only slightly annoying thing I've encountered so far is that while you can have 4 different work spaces to flick between,   you can't (natively) have different wall papers for each one (as a visual reminder as to which screen you are on).

Searching through the forums it seems this is common to most releases,  not just 16.04,   and a fix exists if you don't mind downloading "tweaking" software and then not being able to have desktop icons ever again.   I'm not really sure that's a path I want to go down..

Does anyone else find this frustrating?  Is there a reason it has never been changed (ie,  technically somehow difficult to program or nobody else give a frig apart from me) ?

Is there a way to share requests/suggestions like this with the development teams?  (like a Ubuntu "comments box")..   it would be a really great feature to have!


Libs

---

### Post by Dennis N on 2016-05-26
Depends on what you are using as a desktop environment. XFCE desktop allows different backgrounds (wallpaper images or solid color) on different workspaces.

---

### Post by mcduck on 2016-05-26
I'd assume the main reason is simply that the workspaces are handled by the window manager, while desktop (with it's icons and wallpaper) is handled by the file manager (or something else), and there's no standard mechanism for the two to talk about which virtual desktop you are looking at. This is also why you don't get different desktop icons on different virtual desktops.

The only simple way around that is tighter integration between the window manager and whatever is dealing with the desktop (which some desktop environments have done), but doing so would also mean that you wouldn't be able to switch those components to something else as easily.

For example I remember Compiz (the window manager) having a plugin for drawing different wallpapers for each desktop. However it wouldn't be able to swap what the file manager (Nautilus or whatever you were using) was drawing on the desktop, and would only be able to draw a custom background image *behind* the file manager's desktop window. Which basically meant that you had to switch off your file manager's desktop to see the custom wallpapers, and so you lost the support for desktop icons and right-click menu...

edit: Also, Ubuntu uses Gnome's file manager, Nautilus, and Gnome devs aren't exactly known for their willingness to add new features... ;)

---

### Post by liberatio-spero on 2016-05-26
I'm using the standard Ubuntu environment (Unity I guess).

Thanks for the detailed explanation..  I guess it's a little more complex to incorporate than I imagined.  

Too bad though..  hopefully it will appear in some future release.

Otherwise..  great user experience so far,  thanks to all you guys here working on Ubuntu that keep this project going  :)

---

### Post by RobGoss on 2016-05-27
Hello and welcome, I have seen a few post on this topic but never try it my self you might find this post helpful [http://askubuntu.com/questions/75998/is-it-possible-to-have-a-different-background-for-each-workspace](http://askubuntu.com/questions/75998/is-it-possible-to-have-a-different-background-for-each-workspace) I was trying to see if 16.04 would be on the list but it might be because it's so new it's worth a look

---

### Post by CantankRus on 2016-05-28
The process is fairly simple.
Install the **compiz-plugins** and **compizconfig-settings-manager** packages.
The compiz-plugins are not officially supported and a few of them don't work.
The wallpaper plugin works in Xenial.
**compizconfig-settings-manager** allows you to configure compiz plugins.

Using the terminal....
```
sudo apt install compiz-plugins compizconfig-settings-manager
```

In the dash search  for **ccsm** and open.
Enable the wallpaper plugin and set your 4 workspace pictures.
[ATTACH=CONFIG]269339[/ATTACH]

You must also enable the **JPEG** and **PNG** plugins in "image loading".
[ATTACH=CONFIG]269340[/ATTACH]

As you stated earlier you won't have desktop icons but with the unity dash and launcher you don't need
to clutter your desktop with icons.

I use this script to randomly change the 4 desktops at a set interval.
It has been edited to keep workspace1 at the same image so you instantly know where you are.

**_wallpaper-changer-compiz-cube.sh_**
```
#!/bin/bash
#set -x 
###############################################################################
#                                                                             #
#  A script to randomly change all 4 desktops when using the compiz cube      #
#  compiz-plugins needs to be installed                                       #
#  Enable the compiz wallpaper plugin and manually set 4 wallpapers in ccsm   #
#  before running this script                                                 #
#                                                                             #
###############################################################################

## custom user settings ##
directory="/home/glen/Pictures/wallpaper"   # set your wallpaper directory
desk1fixed=/usr/share/backgrounds/Cielo_estrellado_by_Eduardo_Diez_Viñuela.jpg # fixed image workspace1
interval=30  # interval in minutes between changes
## end custom user settings ##

while [ 1 ]; do
	find "$directory" -type f -iname '*.jpg' -or -iname '*.jpeg' -or -iname '*.png' | shuf -n 4 > ~/.4walls    # searches recursively

	desk1="$desk1fixed"  ## comment for random image in workspace1
	#desk1="$(awk 'NR==1' ~/.4walls)" ## uncomment for random image in workspace1        

	desk2="$(awk 'NR==2' ~/.4walls)"
	desk3="$(awk 'NR==3' ~/.4walls)"
	desk4="$(awk 'NR==4' ~/.4walls)"

	## sets the 4 desktop images in the compiz wallpaper plugin
	dconf write /org/compiz/profiles/unity/plugins/wallpaper/bg-image "['$desk1', '$desk2', '$desk3', '$desk4']"
	sleep ${interval}m
done
exit 0
```

---

