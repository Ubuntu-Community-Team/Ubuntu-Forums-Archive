---
title: "[camgrab &amp; gqcam to capture single image] Problem of Color"
date: 2006-07-10
forum: Desktop Environments
---

### Post by patrick295767 on 2006-07-10
Hi, 
To capture a single image from the webcam, I am using : 
camgrab and gqcam
Unfortunately, only the camorama program has a decent color correction filter & gives great images (in terms of colors). It's unfortunately with a Gui.  

I need a program to get single webcam image to be used into a script. 
With gqcam, I coulndt find way with -s option for gqcam. 
With camgrab, there is no man, no options I guess.
  
I tried to change: 
```
cd /sys/module/spca5xx/parameters/
echo 5 > gamma
```
&```

modprobe spca5xx GRed=500 GBlue=500 GGreen=500 gamma=4
```
  
Not better

Has someone some ideas ?

Thank you

Patrick
(if no scripts, camstream has nice features)
==
:-({|=

> 
camgrab v0.1
------------

  camgrab is a simple application which will use the Video4Linux 
 API for grabbing a single image from a webcam device.

  This is useful for scripted image comparison, a simple upload of
 an image to a remote server or other tasks.


Options
-------

  As the software is designed to be simple, and straightforward, there
 are only a couple of options:

 	-device Name 
	  Use the specified device for grabbing, default is /dev/video

	-output file
	  Write the captured image to the given filename, default is "shot.jpg"

	-verbose
	  Increase status reporting.

	-version
	  Display the version string.

	-help
	  Display brief instructions.


Thanks
------

  This application was cobbled together with the aid of the bttv and
 came source code.
 

Steve
--
[www.steve.org.uk](www.steve.org.uk)




> #!/bin/sh
#
#  A simple webcam application using webgrab to produce a timestamped
# image.
#
#  This tool requires that the imagemagick package is installed to perform
# the time stamping of the image..
#
# Steve
# --
# [www.steve.org.uk](www.steve.org.uk)
#


#  The ultimate destination for the shot.
output=/var/www/shot.jpg

#  A temporary location.
tempfile=/tmp/cam.jpg



while true ; do
  # Remove any existing file
  /bin/rm "$tempfile"

  # Get a temporary file
  ./camgrab -device "/dev/video" -output "$tempfile"
  
  # Image stamp it if `convert` is installed.
  if [ -e /usr/bin/convert ]; then
     convert -font helvetica -fill black -draw "text 10, 280 '`date`'" "$tempfile"  "$tempfile"
  fi

  # Move it into position.
  /bin/mv "$tempfile" "$output"

  # Pause
  sleep 5;

done


---

### Post by patrick295767 on 2006-11-07
Someone maybe?

I used again camgrab and same results.

camstream gives really good image quality and colors for acquiring pictures.

Greet


this is nice to put the time on the pic.
> # Get a temporary file
./camgrab -device "/dev/video" -output "$tempfile"

# Image stamp it if `convert` is installed.
if [ -e /usr/bin/convert ]; then
convert -font helvetica -fill black -draw "text 10, 280 '`date`'" "$tempfile" "$tempfile"
fi


camgrab:[http://forum.ubuntuusers.de/topic/15291/#130914](http://forum.ubuntuusers.de/topic/15291/#130914)

---

### Post by patrick295767 on 2006-11-11
Ok, I found out A solution for this: 

I dont use camgrab but camE

my working config files:
to run it :
```
 camE -s -c .camErc 

```
  
  
the config file: 
```
[grab]
device = /dev/video0
# store temp image on local machine
temp_file = webcam01.jpg


# lag reduction, takes 5 shots, discards the first 4, thus clearing mmap
# buffers
lag_reduce = 5
# This goes at the bottom left, with the message from "infofile" appended.
# It is run through strftime, so date vars are expanded.
#text   = %d/%m/%Y %H:%M %Z - 
#width  = 352
#height = 288
text   = %d/%m/%Y %H:%M %Z - 
width  = 352
height = 288
# delay between uploading one shot and starting the next
delay  = 1
# do we want to correct the delay for a slow connect?
# (keeps the perpetually updating clients in sync)
correct = 1
# scale image resolution dynamically based on bandwidth?
# percentage of the delay to spend uploading the image,
# 100 disables, useful values are < 40
percent = 100

########################################################
# PWC specific features (only for philps cams right now)

# framerate of cam capture, lower fps -> less grainy image, more chance or
# blurred motion
framerate = 5

# image settings (0-100)
colour = 50
brightness = 50
contrast =10
hue = 50
whiteness = 50

# White balance mode
# can be "auto", "indoor", "outdoor", "fluorescent" or "manual"
pwc_wb_mode = auto
# if _mode is set to manual, these two controls affect the balance
# (0-100)
pwc_wb_red = 50
pwc_wb_blue = 50
########################################################


# where to log activity. comment out this line to disable logging
logfile = /home/gilbertt/.camlog
# gets the message text from here. one line allowed only. means you can do
# stuff like echo "sleeping and stuff" > ~/.caminfo
infofile = /home/gilbertt/.caminfo
# directory to archive pics in. They are datestamped and saved in here.
archive = /opt/images/webcam
# archive pics in datestamped subdirs
# (1 == with subdirs, 0 == without subdirs)
archive_subdirs = 0
# extension (determines type) of archived images.
archive_ext = jpg
# determines how many shots are taken before a pic is archived
# (1 == every pic, 0 == don't archive)
archive_shot_every = 1
# create archive thumbnails enable/disable flag and give width/height
archive_thumbnails_dir    = /opt/images/webcam/thumbnails
archive_thumbnails_create = 1
archive_thumbnails_width  = 120
archive_thumbnails_height = 90
# jpeg quality (you can save as png etc too, but then quality does squat)
quality = 80
input  = 0
# 0 for PAL, 1 for NTSC
norm   = 0
# Goes in the top right. strftime() is run on this too, so put date stuff in
# if you like
title_text = Giblet TV
# color/transparency of title text
title_r = 255
title_g = 255
title_b = 0
title_a = 255
# font for title text. fontname/size
title_font = arial/8
# fancy font styles
# title_style = /path/to/title.style
# color/transparency of message text
text_r = 255
text_g = 255
text_b = 0
text_a = 255
# font for message text. fontname/size
text_font = arial/8
# fancy font styles
# text_style = /path/to/text.style
# color/transparency of rectangle behind text
# make it 0,0,0,0 to disable.
bg_a = 0
bg_b = 0
bg_g = 0
bg_a = 100
# directory to look for ttf fonts in
ttf_dir = /usr/X11R6/lib/X11/fonts/TrueType
# file to check for before shooting. while this file exists, no shots will
# be taken.
blockfile = /home/gilbertt/BLOCKCAM
# image to upload when blockfile is first put in place
offline_image = /home/gilbertt/.block.jpg
# File to check before shotting, while this file exists, shots will be taken.
# but not uploaded. blockimage will not be uploaded if you set this.
uploadblockfile = /home/gilbertt/BLOCKUPLOAD
# Shots will only be taken/uploaded if the specified interface is active.  
#watch_interface = ppp0
# image to overlay
#overlay_image = /home/gilbertt/.lb.png
#overlay_x = 5
#overlay_y = 5
# do things. like play sounds or whatever. Each is a shell command.
#action_pre_shot
#action_post_shot
#action_post_upload
# image processing
# crop = 1
# crop_width = 320
# crop_height = 240
# crop_x = 20
# crop_y = 20
#
# scaling is applied after cropping, so you can
# remove borders then stretch up the result
# scale = 1
# scale_width = 640
# scale_height = 480
#
# Flip the image horizontally or vertically.
# Horizontal flipping is useful for some Philips cams
# which give a mirrored image when used with the pwc module.
# flip_horizontal = 1
# flip_vertical = 1
#
# Change the orientation of the image.
# Useful if your camera is on its side (for whatever reason).
# 1 rotates clockwise by 90 degrees, 2, rotates clockwise by 180 degrees, 
# 3 rotates clockwise by 270 degrees.
# orientation = 1;

```
contrast of 10-20 helped a lot

References/other links:
[http://linuxbrit.co.uk/camE/](http://linuxbrit.co.uk/camE/)
[http://fresh.t-systems-sfr.com/unix/src/privat2/camE-1.9.tar.gz:a/camE-1.9/example.camErc](http://fresh.t-systems-sfr.com/unix/src/privat2/camE-1.9.tar.gz:a/camE-1.9/example.camErc)
[http://www.mauiholm.org/ohana/camE_config.html](http://www.mauiholm.org/ohana/camE_config.html)
[http://www.mauiholm.org/ohana/webcam.html](http://www.mauiholm.org/ohana/webcam.html)

---

