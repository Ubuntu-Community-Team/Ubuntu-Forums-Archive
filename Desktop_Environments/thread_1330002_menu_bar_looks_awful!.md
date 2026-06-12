---
title: "menu bar looks awful!"
date: 2009-11-17
forum: Desktop Environments
---

### Post by chinmaya_n on 2009-11-17
Hi

please see the picture attached, It is my menu bar.. When i applied some gtk theme.... it turned like that !
How to completely paint that?
And i would like to change that color to white (modify the theme).. How Can i do that?

---

### Post by Giant Speck on 2009-11-18
Navigate to wherever the theme is.  It should be something like this:

/home/<your-username>/.themes/<name-of-theme>/gtk-2.0/gtkrc

Open that file in a text editor and look for a line that says:

```
include "panel.rc"

```
Put a # in front of it, so that it looks like this:

```
#include "panel.rc"

```
Then save the file and restart the panel:

```
killall gnome-panel
```

That should get rid of the background image.

---

### Post by lidex on 2009-11-18
You can modify the panel background to some degree by right-clicking on it and selecting "properties". Click to select the "background" tab. Have fun.

---

### Post by chinmaya_n on 2009-11-18
you can see in the attached picture... 
i changed as you said ... but didnt work (#include "panel.rc")

!! ..
What should i do now ?

---

### Post by Giant Speck on 2009-11-18
Well, the background image is gone, at least.

The first thing you need to do is right-click the panel and go to Properties.  Click on the Background tab.  You should have three options:

1. None (use system theme)
2. Solid color
3. Background image

Try each one and see if they work.  If none of them fixes the problem, just set it to "none" and then follow the next few steps.

Open the file I had you open up before:
/home/<your-username>/.themes/<name-of-theme>/gtk-2.0/gtkrc

Look for something that says:
```
style "panel" {
```

It might not say that exactly, but as long as it says "panel," you should be at the right part of the file.  If you need to, you can also just search for the word "panel" and it should bring you to this section of the file.

Chances are, it might look something like this:
```
style "panel" {
	xthickness = 3
	ythickness = 3
	bg[NORMAL]        = <color-code>
	bg[PRELIGHT]      = <color-code>
	bg[ACTIVE]        = <color-code>
	fg[NORMAL]        = <color-code>
	fg[PRELIGHT]      = <color-code>
	fg[ACTIVE]        = <color-code>
}
```

Check to make sure each of these lines does not have a # in front of them.  If they do, remove the # from each line.  Where I have typed "<color-code>" there should be a hexidecimal color code, such as #000000 (which is black) or #FFFFFF (which is white).

bg[NORMAL] sets the background color of the panel
bg[PRELIGHT] sets the color you see when you hover over something on the panel
bg[ACTIVE] sets the color you see when you click on something on the panel
fg[NORMAL] sets the text color of items on the panel
fg[PRELIGHT] sets the color of text that is hovered over
fg[ACTIVE] sets the color of text that is clicked

Now, you said you wanted something white.  Try replacing whatever is in the file with this:

```
style "panel" {
	xthickness = 3
	ythickness = 3
	bg[NORMAL]        = "#FFFFFF"
	bg[PRELIGHT]      = "#999999"
	bg[ACTIVE]        = "#999999"
	fg[NORMAL]        = "#000000"
	fg[PRELIGHT]      = "#FFFFFF"
	fg[ACTIVE]        = "#FFFFFF"
}
```

If you do not end up liking that color combination, try entering other color codes and see what you like.

Finally, we have to make sure the theme knows to apply these settings. Scroll to the bottom of the file and look for any line that includes the words "style" and "panel"

For example:
```
class "*Panel*" style "panel"
widget "*PanelWidget*" style "panel"
```

Make sure none of these lines have a # before them.  If they do, remove them, UNLESS it's a line that says nothing but "#Panel style"  That is simply a comment, the title of the section.  Removing the # will screw up the theme.

When you're finished, save and then restart the panel again.

---

### Post by chinmaya_n on 2010-01-24
Hey, I got a way!
If we remove or cut the image responsible(from the theme, /home/<username>/.themes/<themename>/) for that image in the panel we can clear that!
I mean dont delete that image but misplace it!!

---

