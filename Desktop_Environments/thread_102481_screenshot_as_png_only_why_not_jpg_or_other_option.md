---
title: "screenshot as png only? why not jpg? or other options?"
date: 2005-12-12
forum: Desktop Environments
---

### Post by 0okami on 2005-12-12
or maybe im missing info how to do it :) Sure it has to be possible. 

Basicly, Id like to save my screenshots by default as JPG but still have other formats available if needed without having to save the file first, and then launc h gimp to convert to jpg... 

Anyone know how its done?

---

### Post by taurus on 2005-12-12
If you are using gimp to take a screenshot, you can save it in whatever format you want.

---

### Post by 0okami on 2005-12-12
no, im using the default of breezy.... not sure what it is. but it only offers PNG.

---

### Post by earobinson on 2005-12-12
Is this a problem, A png can be converted to a jpg, but a jpg can not be converted to a png due to lossy compresion. You could submit this as a usibility bug but IMO its not a big deal

---

### Post by 0okami on 2005-12-12
not really a problem :)  but would you happen to know how to change the default screenshot application to be gimp?

---

### Post by Bou on 2005-12-12
[QUOTE=earobinson]Is this a problem, A png can be converted to a jpg, but a jpg can not be converted to a png due to lossy compresion. You could submit this as a usibility bug but IMO its not a big deal[/QUOTE]

Sorry, but can anyone tell me the advantages of PNG over JPG or BMP, that justify the greater size of PNG images? Thanks.

---

### Post by welsh_spud on 2005-12-12
I think PNGs always have very good quality pictures. The size is down to the compression level you choose. A PNG that is 300kb, is the same quality as a 5Mb PNG. The difference is that the 5Mb PNG took half a second to make, whereas the 300Kb PNG probably took 10+ seconds to make.

How do you actually pronounce PNG? PEE-ENN-GEE or Ping or...?

---

### Post by earobinson on 2005-12-12
> JPEG will produce a smaller file than PNG for photographic (and photo-like) images since it uses a lossy encoding method specifically designed for photographic image data. Using PNG instead of a high-quality JPEG for such images would result in a large increase in filesize (often 5-10 times) with negligible gain in quality.

PNG is a better choice than JPEG for storing images that contain text, line art, or other images with sharp transitions that do not transform well into the frequency domain. Where an image contains both sharp transitions and photographic parts a choice must be made between the large but sharp PNG and JPEG artifacts around sharp transitions.

Finally, PNG is useful as a lossless format for images that are likely to undergo further editing and may need to be distributed in that lossless form, since it uses a better compression algorithm and is better supported than TIFF. JPEG is a poor choice for storing images that may need to be edited further as it suffers from generation loss issues.
[http://en.wikipedia.org/wiki/PNG#Comparison_with_JPEG](http://en.wikipedia.org/wiki/PNG#Comparison_with_JPEG)

---

### Post by 0okami on 2005-12-12
Also see this doc for comparisons... [[http://www.iceteks.com/articles.php/imageformats/1](http://www.iceteks.com/articles.php/imageformats/1)

---

### Post by earobinson on 2005-12-12
[QUOTE=welsh_spud]How do you actually pronounce PNG? PEE-ENN-GEE or Ping or...?[/QUOTE]

Acording to the wiki artical i poste above it "ping" yet I call it a "p""n""g" file.

---

### Post by anil_robo on 2005-12-12
I tried "gnome-screenshot --help" from terminal but didn't find the filetype option! I guess it allows only png images as of now!
 
A better workaround is to use GIMP to take the screenshots, (File-->Acquire-->screenshot) so that you save some time.
 
Still another option is to use a different program to take screenshots (someone please find one) and then bind it to the "print screen" key.

---

### Post by Bou on 2005-12-12
Thanks a lot for your answers, it's clear to me now.

What I usually do is just take the screenshot, save it as png, then convert it to jpg using the gimp. By the way, is there a way for the GIMP to save an image with a given size? for example, an image to be used as an avatar. Photoshop could do that.


P.S. I call it "jota pe ge", I'm Spanish.

---

### Post by ardchoille on 2005-12-12
**Here are some tips for screenshots:**

For more details on the utilities, also review their associated Linux "man" pages. For example, issuing the command "$ man ppmtojpeg" shows the Linux "manual" for the ppmtojpeg utility. Often, additional and similar utilities are listed at the end of the manual.


**Using XWD**

At the command line, type

```
$ xwd >mydump.xwd
```

you get a crosshair, which, when you click it in a window, captures the contents of the window, or if clicked on the root window (desktop), captures the whole screen. Now type

```
$ xwud -in mydump.xwd
```

to view the image, or type

```
$ convert mydump.xwd mydump.tiff
```

to change the screen dump to a better format for publishing. See also the man pages for convert and read up on the features of ImageMagick, and also try the GIMP. You could also combine functions using the pipe symbol:

```
$ xwd | xwdtopnm | ppmtojpeg >dump.jpeg
```


**Using XV**

This is the one to use in older distros if you wish to capture a window as it looks when it is the active one - title bar highlighted, complete with borders. Although not included in later distros, you can get it here

At the command line, type

```
$ xv
```

Click the GRAB button, and when the dialog box opens, enter a delay of 5 to 10 seconds and check the "Hide xv windows" checkbox. Click "Grab". Activate the window you wish to capture by clicking it, then after the delay time, click in the window again to grab it. Click on the root window (desktop) to capture the entire screen. The screen will flicker, as the captured image is displayed, and the XV windows will reappear. Click "Save". Enter a filename for the image and click "OK". Click "Quit".

You can now open the image in GIMP and edit it as desired.


**Using Import**

I showed you the xwd method first, because it is a legacy function from older distributions and Unix. This is even easier:

At the command line, type

```
$ import -pause 10 -window root screenshot.jpeg
```

to capture the whole screen after a 10-second delay (pause gives you time to do stuff like select the active window, change workspaces, show root menus, etc). Or type

```
$ import dump.jpeg
```

to save whatever window you click on (including the whole screen if you click on the background) as a jpeg file named "dump.jpeg". Change the file extension to change the type of file saved. Check the man pages for file types handled by import.

You can use "cmd-tab" to switch windows, hiding the terminal.

The beauty of import is that it is scriptable, and can be executed from programs or configurable menus as used in WindoMaker, Fvwm and other minimalist window managers.


**Using The GIMP**

Launch GIMP1.2 or newer. (I am still a Mac mouser, so I select "GIMP" from my Fvwm pop-up menu, but you can type gimp at the command line) and choose "Acquire>Screenshot..." from the GIMP toolbox "File" menu. Once you have a screen capture window, save it as a gif by right-clicking in the image to get a contextual menu at the pointer location. Name the image file with a ".jpg" extension, and GIMP will save it as a jpg. To save as other types, use GIMP menu commands to alter the file type before saving. 


**Via nautilus script**
If you have the import app installed, you can easily create a nautilus scripts for quick screenshots. Here's how to do that:

1. Open your favourite text editor and place the below code into a new file

```
#!/bin/sh
#
import -frame /home/username/screenshot.jpeg

```
Replace "username" in the last line above with your username.

2. Place this new file in ~/.gnome2/nautilus-scripts/filename and make it executable with chmod a+x filename

3. Right-click on the desktop or in nautilus and choose "Open Scripts Folder", this "activates" the script so nautilus knows it is there and available.

4. Now, right-click on the desktop or in nautilus, choose Scripts -> filename and you are presented with a crosshair cursor. Click the crosshair on the desktop for a full screenshot or click it on a window for a window screenshot.

5. Learn more about nautilus scripts from my recent post at: [http://www.ubuntuforums.org/showthread.php?t=101870](http://www.ubuntuforums.org/showthread.php?t=101870)  and  [http://www.ubuntuforums.org/showthread.php?t=101874](http://www.ubuntuforums.org/showthread.php?t=101874)

---

### Post by ranf on 2005-12-12
I usually run `scrot' from a terminal:

scrot test.jpeg

---

### Post by gilgongo on 2005-12-12
>How do you actually pronounce PNG? PEE-ENN-GEE or Ping or...?

It's supposed to be pronounced "ping," but everyone on planet earth says "pee en gee." I've work for graphic design agencies, web development shops, repro houses and just about all types of different image-handling outfits over the last five years, and everyone always calls them "pee en gees."

---

### Post by cantormath on 2006-08-25
> **0okami said:**
> not really a problem :)  but would you happen to know how to change the default screenshot application to be gimp?

what do you mean change it to gimp? like picture.gimp  :-)?

---

### Post by H.E. Pennypacker on 2006-09-01
The biggest difference between JPEGs and PNGs is that the latter (PNG) is open source format.  That is enough of a persuasion for Ubuntu to promote PNG over JPEGs.

If you are a  professional designer of some sort, you should not mess around with JPEGs.  The quality is terrible, and any editing will just result in a lower quality.  PNGs maintain the same quality regardless of whether a PNG is edited or not.

Anyhow, if you can, stick with PNGs.

---

### Post by gnube on 2008-03-12
Seems to me the thread misses the main point. 

At least for me, what I need is a fast screen capture that produces a jpg file for fast and efficient storage. Alt-PrintScreen works fine for me but forcing png for that function is not rational; nor is subsequently invoking Gimp to re-manufacture an image already captured just to change the format, for crying out loud. (Who is going to use Alt-PrintScreen to make a photo-quality "picture" when there are much more elegant tools available for that?)

Most solutions suggested here involve multiple steps, command line/terminal invocations, and larger files more suited to reproducing  photo quality images. I just want a fast method of recording a screen event with enough legibility to read numbers like amounts, receipts lables, etc. Photo quality is not needed and png supremely wastes space....large file usage by linux when a small file would serve the purpose is counter intuitive to claims of 'more efficient', faster, etc..usually made by the linux community. However multi-step processes involving the command line seem to be right in line with the geeksville subdivision of linux but not necessarily attractive to some who have real work to do beyond playing with the opsys.

Is there no way to force Alt-PrintScreen (which seems to invoke the same Gnome screen capture in the Gutsy Applications menu) to produce a jpg file?? Surely linux can do this?

Alternatively:
TechSmith's "Snagit" tool does precisely this with considerably more function all from a hot key but requires Windoze to run...no linux comparable? Are we parochial or going open-source proprietary?

---

### Post by apuglisi on 2008-03-12
I know this is an old thread, anyway i just read it today. First of all, scuse my english, it is not as good as i'd like, anyway...  to the point:

when you press PrintScreen in keyboard, the screenshot dialog appears...  if I write the name of the file with .jpg extension, a .jpg file is created instead of PNG one.

the jpg file created is compressed and all, but i cant seem to see it in gnome image viewer. 
I get this error:
"Not a JPEG file: starts with 0x89 0x50"

On the other hand, GIMP do show the contents of the jpg file. If you just "Ctrl+S" (save the file) with GAIM, it stores as readable for gnome image viewer (or whatever it is in english, my gnome is all in spanish anyway).

I guess that by now everyone know this basic tip due to the time since last post here in this thread.

Regards.

---

