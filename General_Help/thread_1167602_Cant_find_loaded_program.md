---
title: "Cant find loaded program"
date: 2009-05-23
forum: General Help
---

### Post by noelc on 2009-05-23
Hi I,m using Ubuntu 8.1. I loaded a program via the synaptic package manager but I don't know where the program is?  Its not listed under the applications menu.

I also looked in add/remove programs and assume this is similar to synaptic but the program is not listed their. 

Can any one help

---

### Post by hansdown on 2009-05-23
Hi noelc.

It would help if you identified the package you installed.

---

### Post by noelc on 2009-05-23
Sorry

The program is called DVD-Slide show.

It allows you to select digital photos and created a movie DVD of them

---

### Post by x33a on 2009-05-23
try
```
killall gnome-panel
```

and see if it shows up in the menu.

otherwise try starting it from the terminal.

---

### Post by kiridude on 2009-05-23
First type the name of the program in a terminal to run it and see if you installed it correctly. Then go to system > preferences > main menu and you can select what programs appear in your menus.

---

### Post by noelc on 2009-05-23
Ok Thanks tried kill all gnome-panel which didnt help

I then tried noel@noel-desktop:~$ dvd-slideshow
 And got the below however still cant icons or start program. So I,m guessing its there?

[dvd-slideshow]            dvd-slideshow 0.8.2
[dvd-slideshow]            Licensed under the GNU GPL
[dvd-slideshow]            Copyright 2003-2007 by Scott Dylewski
[dvd-slideshow]            
[dvd-slideshow] ERROR: Too few arguments
dvd-slideshow Version 0.8.2 
[http://dvd-slideshow.sourceforge.net](http://dvd-slideshow.sourceforge.net)
Copyright 2003-2006 Scott Dylewski <scott at dylewski.com>

Description: 
	Creates a dvd-compatible mpeg2 video from a bunch of images.
	You can add music if you want also. Supports several effects
	like fadein/fadeout/crossfade/crop/kenburns.  

Usage:
 dvd-slideshow [-n <slideshow_name>] [-o <output_directory>] [-b <background_jpeg>] 
  [-a <audio_file1> -a <audio_file2> ... -a <audio_fileN>] 
  [-p] [-L | -H] [-mp2] [-r] [-smp] [-border <bordersize>] [-theme <themefile>] -f input_file.txt
	
Options: 
 [-n slideshow_name]
	  The program uses this
	  string as the filename base for the output files
	  so you can distinguish it from other slideshows
	  that you can send to the same output directory.

 [-o <outupt directory>]
	  Directory where the final .vob and dvdauthor .xml files
	  will be written.  Default is to write in the directory
	  where dvd-slideshow was run.
 		
 [-b <background jpeg>]
	  Image to use for the background of the slideshow.
	  All of the pictures will be
	  overlaid on top of this background image. If no file 
	  is specified, black will be used for the slideshow
	  and a blue gradient for the title slide.
	  
 [-a <audio file>]
          Audio file to play in background during the slideshow.
          It will be faded out at the end.  Supports mp3, ogg, 
	  aac, mp4, or wav formats at this point.
	  Multiple files will be joined.
	  See also the more flexible text file input method.
	  To pass multiple files, use the -a switch again.

 [-p]
	Use PAL output video format instead of NTSC

 [-mp2]
	Use MP2 audio instead of AC3.
	Default audio format is now AC3 because it seems to be more
	compatible with the DVD hardware players.

 [-L]
	Render a low-quality video suitable for debugging.
	This sets the resolution to 1/2 of full resolution and
	decreases the quality of fades/transitions.

 [-H]
	(Beta) Render a higher-quality video.  
	This uses the default dvd resolution and keeps all other output
	parameters the same, but enables some pixel-sampling methods
	that make the scroll effect look better at very slow velocities.
	This will make dvd-slideshow take up to 4x longer to process the
	scroll effect. Only applied when needed; the output will explain. 

 [-theme <themefile>]
 	Use the given theme when setting variables/colors/etc.
	Themes are installed in /opt/dvd-slideshow/themes or
	in a local directory ~/.dvd-slideshow/themes

 [-border N]
 	Make a border of N pixels around each image.  

 [-sharpen]
 	Sharpen images

 [-r]
 	Autocrop horizontal images to fill the full size of the screen.

 [-w]   Alpha! 
 	Render widescreen output (16:9) instead of standard (4:3) 
	Please send bug reports to scott at dylewski dot com

 [-smp]
 	Enable more processes to run at the same time for multiprocessor
	machines.  Basically, this just renders each frame of a transition
	in the background at the same time, and then waits for them to be finished.
	Use this at your own risk on slower machines! If you do not have enough
	memory to hold all the frames for one "crossfade" or "kenburns" effect,
	then linux starts swapping to disk, and your machine may seem to lock
	up for a while.  USE THIS AT YOUR OWN RISK!

 [-nocleanup]
 	Leave temporary files in the temporary directory.  Useful for debugging.

 -h or -help 
   Prints this help. 

 -v or -version 
   Prints dvd-slideshow version number. 

 [-f] input_file.txt  (-f is optional if the file is the last argument)
          File to specify all the parameters and order easily
          for bigger slideshows. It uses the : character as a 
	  separator for the fields:
          [image.jpg|keyword]:duration:subtitle:effect:effect_params
          with each line being separate.  File options
          will override the ones passed on the command line.

	  NOTE: the effect parameters are separated by a semicolon ;
	  instead of a colon :

	  You can escape a colon with a backslash in subtitle text.

	  Durations can be specified in seconds with
	  up to three decimal points, like 5.583 seconds.

	  Keywords:
            title:duration:Title_text
                makes a title slide. Text is centered on the screen.
            titlebar:duration:Upper_Title:Lower_Title
                makes a title slide.  Upper and lower titles are
                optional; if one is missing, only the other will
                be displayed. White bands are underlayed behind
                the text.
	    musictitle:duration:subtitle:Title;Artist;Album
	   	makes a black frame with the song info 
		printed in the bottom left corner.
	    background:duration:subtitle:image 
	    	makes a slide with the current background 
		or it resets the current background image to a new one:
		"background:2:"  will display the current background
		for 2 seconds. 
		"background:2::image.jpg"  will set the background to
		image.jpg and also display it for 2 seconds.
		"background:0::image.jpg"  will set the background to 
		image.jpg, but will not use it until the next picture. 
		"black" or "white" can be used instead of an image 
		name to display a black or white background.
		You can also use a hex RGB code as the background color.

	    fadein:duration:subtitle
	    	fades in to the next slide
	    fadeout:duration:subtitle
	    	fades out to the background
	    crossfade:duration:subtitle
	    	fades from one picture to the next.
	    wipe:duration:subtitle:[up|down|left|right]
	    	wipes from one picture to the next.  Defaults to left.

	    chapter
	  	Force manual chapter marker timing.  Chapter markers will
	  	only be created where the "chapter" keyword occurs.
		The default is to add chapter markers at every slide.
	    include:includefile.txt
	  	Other input files can be included in the input .txt file.
	  	The file includefile.txt will be concatenated in the
	  	place where the line occurs.
		Useful for setting up a bunch of variables, fonts, etc
		and then just including one standard file at the start of
		your input .txt file.
	    exit
		Stops the slideshow at the current point as if the input
		.txt file ended at this point. Useful for debugging.

	  Effects:
	    Effects are only used with images, not keywords.
	    In the following effects, x0,y0 represents the
	    top left corner of a defined box, and x1,y1 is
	    the bottom right corner. 
	    NOTE: the effect parameters are separated by a
	    semicolon ; instead of a colon :
            crop:
	    	image.jpg:dur:sub:crop:x0,y0;x1,y1
		Crops the image about the coordinates specified.
		Full box description:
	    	  x0,y0;x1,y1
		  Specifies the top-left(0) and bottom-right(1) points.
		Keyword description:
		  frame_size;frame_location
		  where frame_size indicates the fraction of the final 
		  dvd window width/height, and frame_location refers
		  to the CENTER POINT of the picture,
		  and can be any of the following keywords:
		 	topleft		top		topright
			left		middle		right
			bottomleft	bottom		bottomright
		   or
		 	x%,y%
			where % is a percentage of the window width,height
			starting from the top left corner of the dvd window.
		   or
		 	imagewidth | imageheight
			where the image width or height will be scaled to 
			fill the full width or height of the dvd screen.
		Crop examples:
	    	image.jpg:dur:sub:crop:651,390;1134,759
		image.jpg:dur:sub:crop:30%;60%,60%
		image.jpg:dur:sub:crop:50%;topleft
		image.jpg:dur:sub:crop:imageheight;left
	    kenburns:
	    	image.jpg:dur:sub:kenburns:start_box;end_box
		The kenburns effect will crop/zoom from the start
		to the end box.
	    	Where now we have start and end boxes, defined in
		the same way as in the "crop" function, but now
		we have two boxes defined.
		Full box description:
	    	  xs0,ys0;xs1,ys1;xe0,ye0;xe1,ye1
		  Specifies the top-left(0) and bottom-right(1) points.
		Keyword description:
		  start 0%-100%;start_location;end 0%-100%;end_location
		Kenburns examples:
	    	image.jpg:dur:sub:kenburns:651,390;1134,759;372,330;1365,1089
		image.jpg:dur:sub:kenburns:30%;60%,60%;75%;40%,50%
		image.jpg:dur:sub:kenburns:50%;topleft;50%;bottomright
		image.jpg:dur:sub:kenburns:100%;left;0,0;720,480
		image.jpg:dur:sub:kenburns:100%;left;imageheight;left
		kenburns note:  if you find yourself using a lot of lines like:
		crop, kenburns, crop
		where the crop coordinates are the same as the start & end
		of the kenburns, you can use a duration like 1,5,1 for one
		second of crop, followed by a 5 second kenburns, followed by
		another one second of crop (times are adjustable).  (alpha)
	    scroll:
	    	image.jpg:dur:sub:scroll:[left|right|up|down]
		This is most useful for displaying panorama-style
		pictures that are much wider than they are tall.
		This will automatically resize the picture so that
		the image height is equal to the video display 
		height (480) before scrolling (or conversely for tall
		images).

	    The subtitle field is optional, but if you are passing
	    effects after the subtitle field, be sure to include 
	    all the colons :: in order for the parser to get the
	    correct info.
	    Two subtitle tracks are possible (alpha).  Separate them
	    using a semicolon ;. 

	    When passing a picture, you can optionally use the
	    keyword "audio" instead of the integer duration in 
	    seconds.  What this does is force the duration of
	    that image to be the length of the previous audio 
	    track.  This is useful for making a music video dvd.

	  Audio:
	    Audio tracks can be inter-mixed with the video.  If 
	    an audio track is placed between two different images,
	    that audio track will begin playing at the start of the
	    second image.  When placing audio, use the syntax:

            audiofile:track:effect1:effect1_params:effect2:effect2_params

	    The audiofile can be an ogg, mp3, aac/mp4 or wav file.
	    Track is the resulting dvd audio track.
	    Effects are audio effects where
	    you can specify things like fadein/fadeout
	    for the audio.  Example:
            audiofile.ogg:1:fadein:3:fadeout:2

	    If you want to concatenate two audio files, just place them
	    one right after another.  

	  Video: [alpha]
	    You can add video (.avi only) files and either use 
	    the audio from the video or ignore it and use your own
	    from the slideshow:
	   
	    To just play the video in the middle of a slieshow, use:
	    videofile.avi
	    To ignore the audio from the video, and use your own, use:
	    videofile.avi:noaudio
	    To use the audio in the video but fade it in or out, use:
	    videofile.avi::fadein:1:fadeout:2

	Configuration file and variables:
	  You can configure some of the variables and settings
	  that control dvd-slideshow through keywords in the input
	  .txt file or through a ~/.dvd-slideshow/dvd-slideshowrc file.  The heirarchy
	  is as follows: 
	  program defaults --> ~/.dvd-slideshow/dvd-slideshowrc --> theme settings --> command-line --> input file variables
	  So the input file will over-ride your personal settings, etc.
	  The following variable are supported (with this syntax):
	   
	  debug=1       # 0 (low=default), 1 (some debug info), 2 (per frame info), 3 (function info)
	  pal=0  	# 0=ntsc 1=pal
	  ac3=1         # 0=mp2 audio 1=ac3 audio
	  copy=0        # add copies of original images to the output directory
	  autocrop=1    # autocrop images to fill full screen
  	  high_quality=0	# set high-quality mode
	  border=0	# change to number of pixels around the image that is filled in with background
	  sharpen=0	# change to 1 to enable image sharpening
	  widescreen=0	# set output to widescreen mode (16:9) instead of 4:3 (alpha)

#	  font_dir="/usr/share/fonts"
#	  font_name=n019004l.pfb # helvetica bold URW font is default
	  font=/usr/share/fonts/default/Type1/n019004l.pfb # Helvetical bold URW font
#	  font=/usr/share/fonts/default/Type1/n0190241.pfb # Helvetical bold oblique
#	  font=/usr/share/fonts/default/Type1/a0100151.pfb # AvantGarde DemiBold
#	  font=/usr/share/fonts/default/Type1/n0220041.pfb # Courier Bold

	  ## Subtitle:
	  subtitle_type="dvd"  # use "render" to force rendering of text.
	  subtitle_font_size=24
	  subtitle_font=/usr/share/fonts/default/Type1/n019004l.pfb # Helvetical bold URW font
	  subtitle_color="white"
	  subtitle_outline_color="black"
	  subtitle_location="bottom"
	subtitle_location_x=0
	subtitle_location_y=105

	  ## Title:
	  title_font_size=48
	  title_font_color="black"  # or use hex "#RRGGBB"
	  title_font=/usr/share/fonts/default/Type1/n019004l.pfb # Helvetical bold URW font

	  ## top title:
	  toptitle_font_size=48
	  toptitle_font_color="black"  # or use hex "#RRGGBB"
	  toptitle_bar_height=125  # 0 for no 50% white behind text
	  toptitle_text_location_x=80
	  toptitle_text_location_y=50

	  # bottom title: 
	  bottomtitle_font_size=36
	  bottomtitle_font_color="black"  # or use hex "#RRGGBB"
	  bottomtitle_bar_location_y=156 # relative to bottom of image
	  bottomtitle_bar_height=55  # 0 for no 50% white behind text
	  bottomtitle_text_location_x=0
	  bottomtitle_text_location_y=155
	  
	  # kenburns:
	  kenburns_acceleration=1 # in seconds, or:
	  kenburns_acceleration=25%  # as a percentage of the total kenburns effect time

  
noel@noel-desktop:~$

---

### Post by JC Cheloven on 2009-05-23
That you got there is the default help text provided by the program when it's called with bad syntax (not enough arguments in this case). The good news is that it's installed. Otherwise it wouldn't say anything ;-)

So, do as kiridude says: go to system > preferences > main menu, and either:
1) tick the program if it is there, so that it appear in the menu.
2) if your program isn't listed there, you can always add your own icon. Check the help to find out. You'll need to know the name of the executable, and where is it (most likely in /usr/bin).

---

### Post by ad_267 on 2009-05-23
This is a command line application, it doesn't have a graphical user interface, so it won't appear in your menus.

Kdenlive is a good video editor which will allow you to create a slideshow from images, although it may be too advanced for your needs. There's probably other options out there that are more suited to this.

---

### Post by colau on 2009-05-23
Command line program does not have graphical icon.

---

### Post by noelc on 2009-05-26
Would appreciate to know the command line script to run command line programs

---

### Post by ad_267 on 2009-05-26
You can open up a terminal and enter "man dvd-slideshow" or "dvd-slideshow --help" to get information on how to run this application. It might be easier to use a graphical application like kdenlive.

---

