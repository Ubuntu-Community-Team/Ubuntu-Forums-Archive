---
title: "Bitmapped fonts in Gnome"
date: 2004-12-04
forum: Desktop Environments
---

### Post by calamari on 2004-12-04
Hi,

I have a particular Windows bitmapped FON font file that I generated that I've come quite used to over many years of use.  I've converted it to BDF and PCF.  I've attempted to manually convert it to TTF, but I was not successful due to lack of TTF knowledge (although I've studied a bit on it).  However, I think even if I was able to draw the font it would look bad because the edges would be smoothed out where I'd want the crisp edges I'm used to.  

I've heard that using bitmapped fonts in Gnome is deprecated.  But, I want to do it anyways, because I really want to be able to use this font in Eclipse and all my text editors.  

An alternative that I'm not sure would work (but I'd be willing to try if I knew how), is to embed the bitmapped font inside a TTF.  I saw a few pages about it, one from Microsoft in particular, but it assumed access to programs that I do not own (Fontographer).  Do these embedded bitmapped fonts work in Gnome?  Does the autohinter touch them and make them all smoothed out and soft and yucky?  

As a sidenote, I moved several TTF's from Windows to Gnome, and the versions in Windows were well hinted.  At small pixel sizes there was no need for smoothing of the font.  An example is "Times New Roman" used in IE.  It is nice and easy on my eyes for extended reading.  After a while of reading the same exact font in Gnome my eyes get tired because of the smoothed edges.  Turning off the greyscale smoothing isn't an option, though, because then the fonts look horribly bad (I understand that the hinting is not used for copyright reasons (and so we have the autohinting), is there a non-free way to enable real hinting?.  If I could somehow fix this hinting problem then I might give manually drawing my FON -> TTF another shot because then I'd know my efforts wouldn't be in vain.

Any help would be very much appreciated.

Thanks,
Jeff

---

### Post by calamari on 2004-12-06
With the friendly help of freenode #gnome I was able to get the font installed.  I made a small script so that I could automate the process of installing BDF fonts in the future.

I'm not sure what the "sudo dpkg-reconfigure fontconfig" does, but I'm hesitant to run it now that things are working.  Thanks tho :)

Jeff

[HTML]
#!/bin/sh
# filename: install-font

# Shell script to install bitmapped fonts in Ubuntu Linux
# Programmed by Jeffry Johnston, 2004
# Special thanks to BRPocock on freenode #gnome for font guidance

# Instructions
# ============
# To convert a Windows FON file to BDF:
# 1) Install and load fontforge
# 2) Open the FON font in fontforge
# 3) Go to the "Element" menu, choose "Font Info..."
# 4) Go to the "Encoding" tab.
# 5) Click the box next to Encoding (probably reads Windows Latin ("ANSI")"
# 6) Choose "ISO 8859-1 (Latin1)"
# 7) Click "OK"
# 8) Go to the "File" menu, choose "Generate Fonts..."
# 9) The right hand box should be set to BDF, change it to BDF if not
# 10) Click "Save"
# 11) 96 dpi is probably correct, hit "OK"
# 12) Now go to where you saved the font and rename it to exactly what you'd
#     want it to show up as in a font list, example: Console.bdf
# 13) Run this script to install the font, example: ./install-font Console
# 14) Close and reopen any apps that you want to change the font in

# check command line arguments
if [ $# != 1 ] ; then
  echo "Usage: $0 FONTNAME (an extension of .bdf is assumed)"
  echo "For font conversion info, view the contents of this script"
  exit
fi

# convert the font from BDF to PCF format
bdftopcf -o $1.pcf $1.bdf 
if [ $? != 0 ] ; then
  echo "Error converting BDF font to PCF format, install aborted"
  exit
fi  

# create a bitmaps font directory if it doesn't exist
if [ ! -d /usr/share/fonts/bitmaps ] ; then
  sudo mkdir /usr/share/fonts/bitmaps && sudo xset fp+ /usr/share/fonts/bitmaps
  if [ $? != 0 ] ; then
    echo "Error creating the font folder /usr/share/fonts/bitmaps, install aborted"
    exit  
  fi  
fi 

# copy and install the font 
sudo cp $1.pcf /usr/share/fonts/bitmaps && sudo mkfontdir /usr/share/fonts/bitmaps
if [ $? != 0 ] ; then
  echo "Error copying and installing the font, install aborted"
  exit  
fi  

# refresh the font server so that the font shows up
sudo xset fp rehash
[/HTML]

---

### Post by az on 2004-12-06
sudo dpkg-reconfigure fontconfig

---

### Post by calamari on 2004-12-06
Anyone know what that line does?  Does it help me solve my hinting problem or was it for the bitmapped fonts?  If I run it, what files does it modify?  I'd like to make a backup first in case it messes me up.

Thanks,
Jeff

---

### Post by az on 2004-12-06
It reconfigures fontconfig.  It does nothign you cannot reverse by re-running the command.  

You can enable bitmapped fonts with it.

---

### Post by drx on 2006-07-24
Yiiihhaaaa, this is what i have been searching for!
Finally sharp bitmap fonts in my console :)

---

