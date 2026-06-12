---
title: "tom.swartz07 Custom Conky Desktop!"
date: 2010-01-28
forum: Desktop Environments
---

### Post by tom.swartz07 on 2010-01-28
Hi all, 

Ive seen some great questions asking me how I got my desktop to look so cool. Specifically, people would ask for my .conkyrc and other scripts that I use to get my desktop looking so slick.


Ive decided to head off all of these PM's and just post a thread with a complete guide to getting your desktop similar to mine!


_**Background Images**_
Throughout the past few months, Ive created a few custom scripts to grab images from the internet and update on a regular basis. 

***Bing Desktop***
Ive had several requests for this one. Heres a screencap with it:[IMG]http://lh5.ggpht.com/_tORug_uHNu4/Szlhf10IO-I/AAAAAAAAAKM/DZEXzJaomp4/s800/Screenshot.png[/IMG]

Basically, its a simple shell script that I added to my startup programs. When I boot the computer in the morning, it hits Bing.com and grabs the image. 

Heres the code: 
```
#!/bin/bash
# bing wallpaper downloader by YoungJesus, 2009. 
# based on Siddharth Prakash Singh (http://www.spsneo.com/blog) php bing wallpaper downloader

# modify this, if you want to save to other place
#  - $HOME: your home dir
#  - %F: full date (%Y-%m-%d)
#  - other date format: man date :P
OUTPUT=`date "+$HOME/Pictures/bing/bing_bg.%F.jpg"`

# get the bing.com page, and separate the background image (DONT touch this)
IMG=`wget -q http://www.bing.com -O- | sed -r "s/[\]//g;s/.*g_img=\{url:'([^']+)'.*/\1/gp;d"`

# get the background image to the output (DONT touch this)
wget -q "http://www.bing.com$IMG" -O "$OUTPUT"
# error handle
if [ $? -gt 0 ]; then
	echo "there is a problem with downloading.."
	exit 1
fi

# setup the background
gconftool-2 -s -t string /desktop/gnome/background/picture_filename "$OUTPUT"
# set the background position
gconftool-2 -s -t string /desktop/gnome/background/picture_options "centered"
# set the background color
#gconftool-2 --type string --set /desktop/gnome/background/primary_color "black"

exit 0
```

Simply place this file (saved as bing.sh) in your home folder, and add it to your startup applications. You could set it up with cron if you dont turn your computer off at night, but we could leave that one for the comments.


***Live Earth View Background***
This is one that Im most pleased about. It grabs a live image of the Earth, complete with clouds and sunlight pattern and sets it as your background, updating BY ITSELF every 5 minutes or so. Heres a screencap: [IMG]http://lh5.ggpht.com/_tORug_uHNu4/S2HF281EUFI/AAAAAAAAAM8/YxSg_cmYWP0/s800/Screenshot.png[/IMG]

Again, this script follows a similar pattern from the previous one, it connects to a website and grabs the image, then sets it as the background. The temporary storage is located in .gnome2 in your home folder. I did this because if a download would fail, you would end up with no image for a background.

In order to set this up, make a new folder titled 'earthwallpaper' in your home folder and then save the following code into it;

```
#!/bin/bash
# Earthview wallpaper changer. Created by Tom Swartz 2009/2010
cd ~/.gnome2/
while [[ 1 ]]; do
	COUNTER=0
	while [[ COUNTER=$[ $COUNTER + 1 ] -lt 60 ]]; do
		wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O world.jpg
		if [[ $(file world.jpg | grep JPEG) ]]; then
			mv world.jpg world_sunlight_Wallpaper.jpg
			break
		fi
		sleep 5
	done
	sleep 300
done
```

_**Conky!**_
This is one that Ive gotten the most requests for. Ive spent the better part of 10 hours tweaking this code to get it show up just right on my screen, and I really appreciate the outpouring of interest for it! :D

You will need several scripts that I have both assembled and created myself to get it just as you see in the above screencaps. 

Ill host the files on my public Dropbox folder for right now, until I get my home server set up (hopefully in the near future!)
The scripts and .conkyrc are all loaded in a .zip file here: [CONKY]("http://dl.dropbox.com/u/1864354/Shared%20Conky.zip")

Located in this .zip file is everything you need to get started. Unfortunately, you will have to do some tweaking of the .conkyrc file as I still left most of the paths from my machine here. I would suggest setting up a specific 'conky' folder in either your /home folder or in a Dropbox folder (If you dont have Dropbox, you could get a free 2GB account by clicking the link in my sig) 

I would highly recommend the Dropbox route, as you dont need to worry about any files 'missing' if your computer crashes- its all safe and password protected online.

**_DOCKS! DOCKS! DOCKS!_**
Another interesting point on my desktop are my docks. I use both Avant-Window-Navigator (trunk) and Docky.


*AWN*
The version of AWN from the software center does not have all of the functionality that you see in my images; you must add the AWN repo. If youre using Karmic, its as easy as typing in a terminal ```
sudo add-apt-repository ppa:awn-testing/ppa
```
Then in synaptic, add all packages that say "awn trunk", there are quite a few, including neat new plugins and applets. My favorite are Pandora and a media changer applet. The media changer applet uses the whole dock! Like this: [IMG]http://lh5.ggpht.com/_tORug_uHNu4/S2HK32kQrAI/AAAAAAAAANE/y3dTW7_oA4o/s800/Screenshot-1.png[/IMG]
Again, its just a matter of adding the PPA and downloading the correct packages.

*Docky*
Docky is a spin-off project from Gnome-Do. Its a very powerful little dock, and it has much more functionality than I actually use. haha.
You could add docky from the ppa here: ```
sudo add-apt-repository ppa:docky-core/ppa
``` Then you could install docky from your favorite package manager.





I guess that about sums it up! If there are any more questions, I would be more than happy to address them! I will continue to update this post as I get more and more tweaks put on my system, and I will update to address any questions that people have!

Thanks a ton again for all of your interest! Enjoy!

---

