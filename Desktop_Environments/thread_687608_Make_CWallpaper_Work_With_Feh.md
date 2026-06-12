---
title: "Make CWallpaper Work With Feh"
date: 2008-02-04
forum: Desktop Environments
---

### Post by Mark76 on 2008-02-04
As part of my on-going adventures in Openboxland I installed Feh as the default background app and cwallpaper as the graphical front end for it.  When I try to run Cwallpaper, however, this is what I get

> :~$ cwallpaper
Attempting to use the config file: /home/mark/.config/cwallpaper/config.
Config file was not found, using internal defaults (Hope you have fbsetbg :D ).
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Loading

(cwallpaper:7095): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Setting the wallpaper to: "/usr/share/xfce4/backdrops/bluemoon.jpg"
sh: fbsetbg: not found



I had to create my own cwallpaper folder in home/mark/.config and a .config file therein. Sadly I've no idea how to write a .config file yet, so it's blank.

---

### Post by urukrama on 2008-02-04
> **Mark76 said:**
> I had to create my own cwallpaper folder in home/mark/.config and a .config file therein. Sadly I've no idea how to write a .config file yet, so it's blank.

You need to create a configuration file in /home/username/.config/cwallpaper/. You should have a default configuration file (using fbsetbg) in /usr/share/cwallpaper or /usr/local/share/cwallpaper depending on your installation method.


Here is what a configuration file for Feh would look like:

> 
program: feh
s: --bg-scale
t: --bg-tile
c: --bg-center
default: s


Save the file in the above mentioned directory as 'config', and restart CWallpaper. It should work fine now.

You'll also have to set a list of wallpapers before you can use it. These are set in the file ~/.config/cwallpaper/wallpapers by entering the full path to the image (including the image name!). This is rather a lot of work if you have a lot of wallpapers, but luckily CWallpaper comes with a handy script to accomplish this task nearly effortlessly. In /usr/share/cwallpaper you will find a script makelist.sh. Copy this anywhere in your home directory (I keep it in the ~/.config/cwallpaper/ directory). Open the file with your favourite text editor and change all the &#8220;$1&#8243; with the path to your desktop wallpapers directory. Make the script executable (chmod a+x /path/to/script) and run it. It will automatically generate a wallpapers file in the ~/.config/cwallpaper/. (Note that the script also scans for image files in the subdirectories of the directory specified.) Now run cwallpaper and you will be able to set the wallpaper of your choice.

(I've written about cwallpaper and other programs to set desktop backgrounds [here]("http://urukrama.wordpress.com/2007/12/05/desktop-backgrounds-in-window-managers/"). Perhaps you'll find it useful.)

---

### Post by Mark76 on 2008-02-04
Okay. So I change this line (and the other ones like it) 

> find $1 -name '*jpg' > /tmp/cwallpapersjpg

to

> find usr/share/nameoffolderwithwallpaperinjpg

Right?

---

### Post by urukrama on 2008-02-04
> **Mark76 said:**
> Right?

You refer to the wallpaper script, right? You just need to replace the $1 with the path to your wallpapers. So the following line:

> find $1 -name '*jpg' > /tmp/cwallpapersjpg

should be

> find /path/to/wallpaper/folder -name '*jpg' > /tmp/cwallpapersjpg

Do the same with the other occurences of $1 in that file.

---

### Post by Mark76 on 2008-02-04
Okay. Am I on the right track now?

e> cho Making the wallpaper list from the files in: $1
find usr/share/xfce4/backdrops '*jpg' > /tmp/cwallpapersjpg
find usr/share/xfce4/backdrops '*png' > /tmp/cwallpaperspng
find usr/share/xfce4/backdrops '*gif' > /tmp/cwallpapersgif
find usr/share/xfce4/backdrops '*bmp' > /tmp/cwallpapersbmp
echo Placing in file

---

### Post by urukrama on 2008-02-04
Yes, though there is a $1 before that, at the top of the file. Here is what the file should look like if your wallpapers are in  /usr/share/xfce4/backdrops (as you indicated in your previous post):

> #!/bin/sh
if [ -z /usr/share/xfce4/backdrops ]; then
	exit 0
fi
echo Making the wallpaper list from the files in: /usr/share/xfce4/backdrops
find /usr/share/xfce4/backdrops -name '*jpg' > /tmp/cwallpapersjpg
find /usr/share/xfce4/backdrops -name '*png' > /tmp/cwallpaperspng
find /usr/share/xfce4/backdrops -name '*gif' > /tmp/cwallpapersgif
find /usr/share/xfce4/backdrops -name '*bmp' > /tmp/cwallpapersbmp
echo Placing in file

cat /tmp/cwallpapersjpg /tmp/cwallpaperspng /tmp/cwallpapersbmp /tmp/cwallpapersgif >  /tmp/cwallpapersall
mkdir ~/.config
mkdir ~/.config/cwallpaper
sort /tmp/cwallpapersall -o ~/.config/cwallpaper/wallpapers
echo Cleaning up
rm /tmp/cwallpapersjpg /tmp/cwallpaperspng /tmp/cwallpapersbmp /tmp/cwallpapersgif /tmp/cwallpapersall

Run the scripts, and you should have a wallpapers file in ~/.config/cwallpaper/

---

### Post by Mark76 on 2008-02-04
Okay, I changed that line and ran  sudo chmod a+x /home/mark/.config/cwallpaper/makeList.sh but nothing happened. Because I don't have anything in the tmp folder perhaps?

---

### Post by urukrama on 2008-02-04
The chmod action just makes the file executable. Now you need to run the script either by double clicking on it, or with the following command in a terminal:

> /home/mark/.config/cwallpaper/makeList.sh

The script will run, and will create a wallpapers file in /home/mark/.config/cwallpaper/

When you run Cwallpaper after this, you should have a list of wallpapers on the right.

---

### Post by Mark76 on 2008-02-04
It just doesn't seem to be doing anything :(

Should it make any difference that I'm on a 64 bit machine?

---

### Post by Mark76 on 2008-02-04
I have two identical makeList.sh files. One in .config/cwallpaper and the other in usr/local/share/cwallpaper.

Maybe I should delete one of them.

---

### Post by urukrama on 2008-02-04
You don't need to delete any of them. Just run the one in ~/.config/wallpaper/makeList.sh. Copy and paste what I posted 4 posts ago into that file (delete everythin in the file, and add all of it from that post in the file). Then try to run it again in the terminal with this command:

> /home/mark/.config/cwallpaper/makeList.sh

What messages do you get in the terminal? Post here whatever output you get from this command.

---

### Post by urukrama on 2008-02-05
Did you get CWallpaper to work for you?

---

### Post by Mark76 on 2008-02-05
Here's the terminal output

> $ cwallpaper
Attempting to use the config file: /home/mark/.config/cwallpaper/config.
Program = feh
Default = Scale
Fontconfig error: "~/.fonts.conf", line 1: XML declaration not well-formed
Loading

(cwallpaper:6220): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


---

### Post by urukrama on 2008-02-05
That doesn't look too good. Seems like you have some Glib problems. Unfortunately I don't know how to fix those. You could try reinstalling libglib2.0, but I'm not sure that will help.

This error message comes up regularly on these forums, but I haven't seen a working solution yet. [Here]("http://ubuntuforums.org/showthread.php?t=685804") is a recent thread with the same error. Perhaps someone will post a solution there.

---

### Post by Mark76 on 2008-02-05
Can you recommend a good alternative GUI for feh?

---

### Post by urukrama on 2008-02-06
There isn't, as far as I know, but you could use [Nitrogen]("http://projects.l3ib.org/nitrogen/"). 

If you would like to keep Feh, there are a few other things you can without using the command line:

* If you open an image with Feh (I use it as my default image viewer), you can right click on the image got to File > Background and click on the way you want to set up the image as a background.

* If you use Thunar, you can create a ['custom action']("http://thunar.xfce.org/pwiki/documentation/custom_actions") for Feh. Go to Edit > Configure custom actions and click on the + sign (on the right). A new window will appear (there are screenshots in the above link). In the "Name' box, type something like 'Set as background', in the Description box "Set this image as background with Feh", and in the command part "feh --bg-scale %f" (use feh --bg-center %f or feh --bg-tile %f if you would like to tile or center the image). In the 'appearance condition tab, select Image file (and deselect all the rest). Now you can right click on an image in Thunar, select in the menu 'Set as background' and Feh will set the image as your desktop background.

I hope this helps.

---

### Post by Mark76 on 2008-02-07
From what I understand Rox can be used to set both the background and desktop icons, but I can't find any command to do either. 

I tried thunar, but that only works so long as you keep thunar open

---

### Post by Mark76 on 2008-02-07
You know, I'm beginning to think cwallpaper is a broken application.  It doesn't matter how I edit the .config file in the folder it keeps insisting that I should have fbsetbg.

---

### Post by urukrama on 2008-02-07
> **Mark76 said:**
> You know, I'm beginning to think cwallpaper is a broken application.  It doesn't matter how I edit the .config file in the folder it keeps insisting that I should have fbsetbg.

Cwallpaper works fine all the computers I have tried it on. Are you sure the file is named properly and saved in the proper location? It should be in /home/USERNAME/.config/cwallpaper/

Can you post your config file here?

---

### Post by Mark76 on 2008-02-07
Yeah, it is.  But I've switched to gsetroot now (much easier to handle). Cwallpaper is more trouble than it's worth.

---

### Post by Mark76 on 2008-02-08
I tried to install Nitrogen and the terminal output looked like this
> 
~/Desktop/nitrogen-1.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

What does that mean: "C compiler cannot create executables"?

---

### Post by urukrama on 2008-02-08
Do you have the package 'build-essential' installed?

---

### Post by Mark76 on 2008-02-08
I do now :)

---

### Post by xentalion on 2008-03-04
> **urukrama said:**
> That doesn't look too good. Seems like you have some Glib problems. Unfortunately I don't know how to fix those. You could try reinstalling libglib2.0, but I'm not sure that will help.

This error message comes up regularly on these forums, but I haven't seen a working solution yet. [Here]("http://ubuntuforums.org/showthread.php?t=685804") is a recent thread with the same error. Perhaps someone will post a solution there.

Actually, it's not as big a problem as it sounds like. Usually this pops up if you have an empty line in the cwallpaper wallpaper list and you select it.

---

### Post by xentalion on 2008-03-04
Mark76, 

Which version of CWallpaper were you using? Did you build it from source?
Did you save your config file as /home/USERNAME/.config/cwallpaper/config ?
Is your wallpaper list empty?

---

### Post by Mark76 on 2008-03-04
I gave up with CWallpaper and switched to ROX 8)

---

### Post by xentalion on 2008-03-04
> **Mark76 said:**
> I gave up with CWallpaper and switched to ROX 8)

CWallpaper works with Rox too :)

I'm the author of CWallpaper, so if I can figure out what is wrong with your version, I can fix it in the next release.

---

