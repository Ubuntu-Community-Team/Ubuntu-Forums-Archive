---
title: "TwinView random wallpaper per monitor"
date: 2011-03-05
forum: Desktop Environments
---

### Post by guyverix on 2011-03-05
I have been searching for the last several days for a decent way to have different wallpapers on each of my monitors in Gnome and have them rotate on a timer.  I have not found anything that really worked the way I hoped.  So last night I wrote a switcher in bash, and thought it might be useful for others..

edit dual.cfg so that it knows:
1) the monitor resolution (They should both be the same in twinview) (var size)

If you cannot find it, try xrandr -q and divide the larger number by 2 for your real resolution per monitor.

2) the path to look in for wallpapers. (var index)
3) How often to change the wallpaper. (var timer)
4) The background color if you dont like black.. (var bg_color)

** Some of the code is stubbed and does not actually do anything yet, but the options listed work just fine. Just make sure you have installed imagemagick before trying to run this.

Then run multi_wallpapers.sh

The first time it runs it will take some time as it is indexing your images with imagemagick making sure that the jpg files that it finds are bigger that 640x480.

I would recommend making a dir in your home directory and running this from there commandline for now. I am writing a new version so that the wallpapers that are really big and would fit with span are NOT stitched together but actually spanning. In the meantime you are more than welcome to use the script.

Right now, the system is kind of brainless, so if you add new wallpapers it will not know it, and add to the index.  If this happens, just delete the images.lst file, and let it generate a new one.

Let me know of any deficiencies in the code, or any problems that you come across, since I think many people would be interested in a good solution for this problem.  ( unless I missed someone else's solution when I googled for it :D )

---

### Post by flagrant on 2011-12-17
Maybe putting INDEX into "" in find in multi_wallpapers.sh line 51 would be helpful if someone has folder with spaces in path....solved my problem

---

