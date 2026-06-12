---
title: "nvidia driver errors"
date: 2007-10-05
forum: Desktop Environments
---

### Post by kiuri on 2007-10-05
hello

i was trying to install beryl on my Linux and I needed to install the graphic card drivers, so I used this line to install it, as it is on the "how to install beryl post":
-------------------------------------------------------------------------------------------------------------------------------
drivers nvidia


sudo apt-get install nvidia-glx

sudo nvidia-xconfig --add-argb-glx-visuals --composite

Now you need to restart your X by logging out and in or by pressing ctrl+alt+backspace
-------------------------------------------------------------------------------------------------------------------------------

after I pressed the sequence above it gave me an error message:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" (on a blue screen)

I presses ok and it showed up this:
"
Markers: (==) probed, (**) from config file,(==) default setting,(++) from command line,(!!) notice,(II) informational,(WW) warning,(EE) error,(NI) not implemented,(??) unknown. ***<<this is the legend, I want to show exactly how it appeared.>>***

(==) Log file: "/var/log/xorg.0.log",
(==) Using config file:"/etc/x11/xorg.confg"
NVIDIA: could not open the device file/dev/nvidia0(input/output error).
(EE) Nvidia(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0.
(EE) Screen(s) found, but none have a usable configuration.
.
.
Fatal server error:
no screens found."
 <<preesed ok>>
--------------------------------------------------------------------------------------------------------------------------
The X server is now disabled. restart GDM when it is configured correctly.
Then it appears a console login(like when you start your pc in msdos).
------------------------------------------------------------END---------------------------------------------------------

What seems to be the problem? (Wrong drivers I guess, How to put it back to normal and install the correct drivers?)

thanks for the help in advance

---

### Post by greenstar on 2007-10-07
First, what kind of nVidia gfx card do you have? This will help determine which nvidia driver to use.

Now on to the fixin':

At boot, select the recovery console option to boot to terminal. If your system is a dual boot this option will be easy to see at boot, but if you only have Ubuntu installed, you will have something like 3 secs to hit <esc> which will give you a boot menu to choose the recovery console. Log in at the console, just as you would at the gui. This gets us a terminal.

The next command runs you through a ncurses video configuration wizard to set up your xorg.conf.

If you're unsure of a particular option, you can always just run the config again and select a better option.

Most of the things you might not understand in the wizard you can just hit enter to accept the default, including the video memory in kilobytes option - just leave it blank. The part we're concerned with is the video card driver, color depth, display resolutions and monitor type. If you know or can get your monitor's specs, either the "Intermediate" or "Advanced" config will probably be easy enough, otherwise choose "Simple".
 Don't worry, if you choose something wrong, just run the wizard command from the recovery console again, no biggie.

To start the ncurses wizard, do: ```
sudo dpkg-reconfigure xserver-xorg
```You can also edit /etc/X11/xorg.conf from the recovery console with:
```
sudo nano /etc/X11/xorg.conf
```I have had to leave out or comment out the "add-argb-glx-visuals" line from my xorg.conf to get compositing (Beryl/Compiz) to work on several of my nVidia cards. Try commenting that line out and see if it helps, it's near the end of the file. To comment out a line, just put a "# " (minus the quotes) in front of the line. That's a pound-symbol and a space in the quotes, btw.

I'll be watching in case you need more detailed help.

Greenstar

---

