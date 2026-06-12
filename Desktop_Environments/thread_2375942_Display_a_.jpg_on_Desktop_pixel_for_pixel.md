---
title: "Display a .jpg on Desktop pixel for pixel"
date: 2017-10-28
forum: Desktop Environments
---

### Post by mark bower on 2017-10-28
I want to resize a .jpg and place the resized image on the Desktop to display in its resized, size.  For instance, take a .jpg which is 1280 x 960 pixels, resize it proportionately to say 400 x 300 pixels, then have it display at 400 x 300 pixels on the Desktop.  (I use Irfanview for all my photo editing)

When a .jpg is placed on the Desktop, it is treated as an icon; it can be resized by right-clicking on it.  However, resizing (expanding) the icon to the desired size results in the icon not being crisp, it noticeably picks up blur.

So, how might I do this:  display a .jpg in its actual pixel size on the Desktop pixel for pixel?

---

### Post by ajgreeny on 2017-10-29
I think the easiest way will be to incorporate the small image at 400x300 pix into a larger image at your full desktop size of whatever you want as the wallpaper for the remainder of your desktop.

I do not now know irfanview any more, though I did use it in my WinXP days, and therefore I'm not sure if you can use that to create the new wallpaper that you want, but if that won't do it there are plenty of apps in the Ubuntu repos that can do it easily for you.

There may be other ways to do this using an image window that can be moved around on the desktop but I am not sure how without it showing all the window decoration; it may well also be possible depending on your DE by adding a widget of some sort, as I believe was possible in KDE, and may still be possible.

---

### Post by mark bower on 2017-10-29
I am not sure what you mean?  Just in case though to be clear, I do not want the photo.jpg to display as background wallpaper.  I want the photo to display with a vertical of about .3 x the screen vertical, which is 1024 pixels.  Attached is what my desktop looks like, just want to be able to have a crisper image in the upper right hand corner.  That is, crisper than the photo starting out as an icon then resizing it as an icon.  And, the icon comes from copying the photo onto the desktop

---

### Post by again? on 2017-10-29
If you just want to display an image on the desktop you can use conky.
Conky can resize images. Keep the same ratio though.
eg an 800x600 image can be displayed in conky with
```
${image /path/to/image -s 400x300}
```
If this is what you want let me know and I'll post a conky config.

---

### Post by mark bower on 2017-10-30
@guber2

o.k. that looks good - definitely the "form-fit-function" I would like to achieve.  the resolution of the foreground dog hairs indicate that good resolution is in effect.

To get the image on the desktop, do you have to do more than just drag/copy it there?  I am guessing that is the case?

Resizing is not a problem for me, but let me play with Irfanview a bit more and see if I can achieve what you did.  If not, I will come back for Conky help(an app I have never used)

thanks
mark

---

### Post by mark bower on 2017-10-30
o.k. How to I get the .jpg from a directory to the Desktop. I installed Conky via "sudo apt-get install conky-all".  It appears to be command line use only?

Per your example, where the image of interest resides at /home/mark/Wallpapers/5pattysep03.JPG, I entered the following:
```
${image ~/Wallpapers/5pattysep03.JPG -s 400x300}
```

I get the response "no cmd image found"?   With $image and no arguments, a black box opens with system info.  What to do next?

---

### Post by again? on 2017-10-30
Conky loads  a config file.
```
gedit ~/.conkyrc
```

Copy and paste this into gedit...
```
conky.config = {
	background = false,
	update_interval = 30,
	total_run_times = 0,

	use_xft = true,
	font = 'Ubuntu:size=10',
	xftalpha = 1.0,

	own_window = true,
	own_window_type = 'normal',
	own_window_hints = 'undecorated,below,skip_taskbar,skip_pager,sticky',
	own_window_transparent = false,
	own_window_colour = '#2E3436',
	
	[COLOR="#008000"]minimum_width[/COLOR] = 400, [COLOR="#008000"]minimum_height[/COLOR] = 300, -- set these the same as your ${image -s} values
--	maximum_width = 400,
	alignment = 'top_right',
	gap_x = 20,
	gap_y = 50,

	
	default_color = '#8F979D', -- text color
	double_buffer = true,
	no_buffers = true,
	override_utf8_locale = true,

	imlib_cache_size = 0,
};

conky.text = [[
${image [COLOR="#FF0000"]/home/glen/Downloads/cutePuppy.jpg[/COLOR] -p 0,0 -s [COLOR="#FF8C00"]400x300[/COLOR]}
]];
```

[LIST]
[*]Change for [COLOR="#FF0000"]your image path[/COLOR]
[*]Change for [COLOR="#FF8C00"]your image display size[/COLOR]
[*]Match [COLOR="#008000"]window size[/COLOR] to image display size
[*]
[/LIST]

Save and close.
In terminal run..
```
conky
```

You can position the conky window by altering the following values in the config
```
alignment = 'top_right',
gap_x = 20,
gap_y = 50,
```

In startup applications add
```
conky -p 10
```
The "-p 10" option pauses the starting of conky for 10secs to allow the desktop to load.

Depending on your window manager, you may have to change
```
own_window_type = '**normal**',
```
to
```
own_window_type = '**desktop**',
```
to prevent the conky window from being minimized when you show the desktop.
In Ubuntu-gnome 17.04 I use "desktop".

---

### Post by mark bower on 2017-10-30
I'm going to need a "little hand holding" - per the following 3 lines,

    > Change for your image path
    Change for your display size
    Match window size to image display size

1) for "Change for image path" are you still talking re cmd line entry, eg ${image ~/Wallpapers/5pattysep03.JPG -s 400x300}
2) could you define "display size"  (image size? like 400 x 300) ?
3) could you define "window size" (screen size? like 1280 x 960 pixels) ?
4) where do I Match window size to image display size?

I have never modified start-up applications - could you tell me where how that is done?  I am sure I show a bit of confusion with these questions but not at all familiar with doing this sort thing.

Also, I see that after "sudo apt-get install conky-all", conkyrc did not install to ~/.conkyrc.  Synaptic says conky-all is installed.  I deleted conky-all from Synaptic.  The Ubu Software Ctr does not list it as available to install.  Can you recommend best way to install it.  Ouch - this is becoming a bit complicated.

thanks

---

### Post by again? on 2017-10-30
1) Forget about command line entry. ${image ~/Wallpapers/5pattysep03.JPG -s 400x300} is the line you use in the conky config(~/.conkyrc)
2) Image  display size is defined by **-s 400x300** in the section of the .conkyrc "${image ~/Wallpapers/5pattysep03.JPG **-s 400x300**}"
3) Conky draws a window without decorations. This is the size of the actual conky window where the image is placed.
4) Values for "minimum_width = 400, minimum_height = 300" should be set the same as  **-s 400x300**
i.e. you want the conky window "minimum_width" and "minimum_height" to match the size of the image displayed
I colour coded in previous post to show what related to what in config.

If you want your image to display at 400x300 all you need to change is the image path at the bottom of the config I posted.

To autostart, search for "startup applications" and add an entry using in the command box
```
conky -p 10
```

---

### Post by mark bower on 2017-10-30
o.k. Dense, but I believe I understand now - I'll proceed tomorrow.!  But what about best way to install conky it so it lands at ~/.conkyrc?  Note I said it did not show there with my my sudo apt-get ... install.  BTW, I am using 16.04LTS with Gnome Classic should that make any difference.

mark

---

### Post by again? on 2017-10-31
~/.conkyrc is a config you must create or download someone elses and adapt for your use.
If there is no ~/.conkyrc file or it is faulty, when you run conky it will use the config @ /etc/conky/conky.conf
which is the black background sysinfo window you viewed.

You can also start conky using any config you like with the "-c" option.
eg if you wanted 2 pics on the desktop you create another config with a different name using a different window placement and image to load.
So you can use the config @ ~/.conkyrc by just running 
```
conky
```
and/or show another image with
```
conky -c */path/to/different/config*
```

or load the config installed with conky
```
conky -c /etc/conky/conky.conf
```



The config file has recently changed to using lua syntax which makes it look more complicated than it is.
Basically, the config file consists of two parts.
[LIST=1]
[*]**conky.config** section.... which contains the options/settings including type, size, color, placement of the window etc
[*]**conky.text** section.... contains objects/variables to display (text, images, graphs etc)
[/LIST]

See "man conky".

---

### Post by mark bower on 2017-10-31
I tried different combos for the 1st line, but cannot get the ~/.conkyrc syntax correct.  Pls see following and tell me where I am wrong,
	```
conky.config = 
        ${image ~/Wallpapers/pattysep03_400x300.JPG -s 400x300}
	background = false,
	update_interval = 30,
	total_run_times = 0,

	use_xft = true,
	font = 'Ubuntu:size=10',
	xftalpha = 1.0,

	own_window = true,
	own_window_type = 'normal',
	own_window_hints = 'undecorated,below,skip_taskbar,skip_pager,sticky',
	own_window_transparent = false,
	own_window_colour = '#2E3436',
	
	minimum_width = 400, minimum_height = 300, 
	maximum_width = 400,
	alignment = 'top_right',
	gap_x = 20,
	gap_y = 50,

	
	default_color = '#8F979D', -- text color
	double_buffer = true,
	no_buffers = true,
	override_utf8_locale = true,
```

---

### Post by again? on 2017-10-31
What is the original size of the image?
Patty may look fat or skinny if it's not a 4x3 ratio. :)

What you want displayed goes in the [COLOR="#FF0000"]conky.text[/COLOR] section at the bottom.
Use this one.(Make sure to scroll the code box so you are copying everything)
```
conky.config = {
	background = false,
	update_interval = 15,
	total_run_times = 0,

	use_xft = true,
	font = 'Ubuntu:size=12',
	xftalpha = 1.0,

	own_window = true,
	own_window_type = 'desktop',
	own_window_hints = 'undecorated,below,skip_taskbar,skip_pager,sticky',
	own_window_transparent = false,
	own_window_colour = '#516E7C',
	
	minimum_width = 400, minimum_height = 300, -- set these the same as your ${image -s} values
--	maximum_width = 400,
	alignment = 'top_right',
	gap_x = 20,
	gap_y = 50,
        border_inner_margin = 1,
	
	default_color = '#ffffff', -- text color
	double_buffer = true,
	no_buffers = true,
	override_utf8_locale = true,

	imlib_cache_size = 0,
};

[COLOR="#FF0000"]conky.text[/COLOR] = [[
**${image ~/Wallpapers/pattysep03_400x300.JPG -s 400x300}**
]];
```

---

### Post by mark bower on 2017-10-31
BIG APOLOGY.  I did not scroll to bottom of script, sorry for extra time on your part to help me get it right. ** I have ignition**, displayed image on Desktop via cmd line - just perfect.  I will now proceed to the automatic launch entry of the image.  I am thrilled to get the nice crisp picture to the Desktop, sized to desire.  And yes, original picture is a 4:3, 1280 x 960.

---

### Post by mark bower on 2017-10-31
The image does not display to the Desktop upon boot.  I have entered in the Startup Applications the path "/home/mark/conky -p 10".  When I launch conky on the cmd line, the image displays and the terminal presents the following, with hanging at "drawing to double buffer":

```
mark@mark:~$ conky
conky: desktop window (1a0000a) is subwindow of root window (4a7)
conky: window type - desktop
conky: drawing to created window (0x2e00001)
conky: drawing to double buffer
```

When it hangs, the cursor stops blinking after about 12 sec.;  if I hit return, the cursor starts blinking again for about 12 sec - this sequence repeats.  When I close the terminal, the image disappears, but then usually reappears after a few seconds.

Suggestions?

---

### Post by again? on 2017-10-31
In startups you only need
```
conky -p 10
```

---

### Post by mark bower on 2017-11-01
Bingo. That did the trick!  I am elated.  Booted a few times and everything seems solid.  Never having used Startup Applications I wrongly assumed the full path was necessary; if only I had exactly followed what you had posted.  I really appreciate the patience on your part to compensate for some of my short sightedness.  Except for key code item that showed purple, I could not find the red and orange color identified entries - and this was only due to my observing the down scrolling.  (And I like and use color code identifiers)

I admit, and you might expect, that I do not easily follow how to make two or more displays.  However, for the time being, I am very satisfied with the single display as discussed above, and I believe that is probably all I will use.

And as I always do in cases such as this one, I will copy most of your posts into a word document for future reference.

So thanks ever so much again for getting me up and running with a quality desktop image.

mark

---

### Post by vasa1 on 2017-11-01
[How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by mark bower on 2017-11-04
A bit of a problem.  The Desktop image is removed when clicking on any Desktop file or application, or just clicking on the window.  On the other hand, launching applications from the Gnome-Panel or from the Applications drop down menu does not affect the image.  I removed [Solved] from the thread.

The problem seems to be resolved by changing in the config file "own_window_type = 'desktop' " to "own_window_type = 'normal' ".  If no more issues in the next few days, then I will return and mark solved.

---

### Post by again? on 2017-11-04
How "own_window_type" behaves depends on your window manager.
It's usually a choice between **desktop**, **normal** and **override**. Just use what works for your situation.
From man conky:
> **own_window_type**
if own_window is yes, you may specify type normal, desktop, dock, panel or override (default: normal). 
Desktop windows are special windows that have no window decorations; are always visible on your desktop; do not appear in your pager or taskbar; and are sticky across all workspaces. 
Panel windows reserve space along a desktop edge, just like panels and taskbars, preventing maximized windows from overlapping them. The edge is chosen based on the alignment option. 
Override windows are not under the control of the window manager. Hints are ignored. This type of window can be useful for certain situations.

---

