---
title: "Top-right  single pixel is no longer part of &quot;Close&quot; X"
date: 2010-10-28
forum: Desktop Environments
---

### Post by darkhelmetchris on 2010-10-28
Recently, I loaded the new Ubuntu 10.10 - the Maverick Meerkat

Like many others, I'm sure, I run my mouse with the speed of light.  So, I often zip my pointer up to the top right corner, hitting the virtual "wall" and landing on the very top right pixel, and click - expecting that the window will close.  In the new 10.10, the top right pixel is not included in the mighty "X" button in any theme I have tried.  So, now I have to exercise some precision and move a little down/left to click my close button.  It is an annoyance that I'm simply not willing to accept any longer.

For the life of me, even though I am a 4-year Ubuntu user, I have never had much reason to play with the themes or make a change like this, and I can't seem to figure out how to fix it.

Does anyone know how to adjust the theme / border / title bar such that the close-window "X" includes the top right pixel?

---

### Post by darkhelmetchris on 2010-10-29
Update:

Okay, upon further investigation, it is not just the top-right pixel.  When I have a window maximized, there is clearly a 2-pixel wide unclickable region spanning the entire right side of the desktop.  If my mouse is at the extreme right (or one pixel in from the right) I can not click on Close, nor can I click on scroll arrows, scroll bar, or inside the page-at-a-time scroll region.

This is not consistent with previous versions of Ubuntu, as I can do these things just fine with Ubuntu 9.10 and Ubuntu 8.10.

Does anyone have some ideas on how to regain this functionality?

---

### Post by chrisstankevitz on 2010-11-06
> **darkhelmetchris said:**
> Like many others, I'm sure, I run my mouse with the speed of light.  So, I often zip my pointer up to the top right corner, hitting the virtual "wall" and landing on the very top right pixel, and click - expecting that the window will close.

Yes yes YES!  Very well said.  Please post if you know how to restore this behavior.

Chris

---

### Post by darkhelmetchris on 2010-11-11
Phew, I'm glad it's not just me.  I was starting to think that no one else was experiencing this little glitch

---

### Post by piquat on 2010-11-11
Nope, I thought maybe it was all of Ubuntu.  But now I find it's just 10.10.  Maybe there's a fix?

<---  New user who hates this also.

---

### Post by piquat on 2010-11-11
Just remembered something.  If you have the SimpleCompiz Config Settings Manager installed then right click your desktop and choose Change Desktop Background then Visual Effects and next to Custom choose Preferences.  In the menu that opens choose Edges.

Do these Edges settings have something to do with this?  I have mine set to None for the upper right corner.  I wonder if it just doesn't pay attention to clicks up there because this Edges function is supposed to handle them?

Edit:  I don't think this is only the close button.  In windows I love to whip the mouse to the right of the screen and click to page down, not happening...

---

### Post by piquat on 2010-11-15
I'm going to bump this because since it's been pointed out, it's driving me nuts.

Ugh, I wish I wouldn't have seen this thread to begin with.   LOL

---

### Post by chrisstankevitz on 2010-11-16
> **piquat said:**
> I'm going to bump this because since it's been pointed out, it's driving me nuts.

Ugh, I wish I wouldn't have seen this thread to begin with.   LOL

The people who know how to fix this problem are not reading this ubuntu forum.  We probably need to more actively seek out those who know the answer.  I just signed up fro the Gnome forums, but they require administrator approval so I'm awaiting that.

---

### Post by piquat on 2010-11-16
Did a little searching there and found:

This thread:
[http://gnomesupport.org/forums/viewtopic.php?t=11477&highlight=corner](http://gnomesupport.org/forums/viewtopic.php?t=11477&highlight=corner)

Which lead to this bug report:
[https://bugzilla.gnome.org/show_bug.cgi?id=97703](https://bugzilla.gnome.org/show_bug.cgi?id=97703)

Which also talks about this bug report:
[https://bugzilla.gnome.org/show_bug.cgi?id=97703](https://bugzilla.gnome.org/show_bug.cgi?id=97703)


If I'm reading all this right, it's a theme problem that's been around since 2002.  It was fixed at one point, mostly, and now it's back again.

There are links to some code to apply a patch but compiling and applying that is beyond me.  Plus, it's really old, probably wouldn't work anyway and may even damage something.  :(

---

### Post by piquat on 2010-11-16
If I run any one of the three "Human" themes, the close button works properly.  Using something like clear looks with human controls doesn't do it.

Edit:  Aaaaand now I understand why most newbies don't complain about this.  Human IS the default theme.  Works fine if you stick with that...

---

### Post by chrisstankevitz on 2010-12-28
> **piquat said:**
> Edit:  Aaaaand now I understand why most newbies don't complain about this.  Human IS the default theme.  Works fine if you stick with that...

Also, most users have a GNOME Panel across the top of their screen.  The close button is never the upper-right pixel for them.  These users always have to perform a precision maneuver to click the X.  Poor saps.

Chris

---

### Post by darkhelmetchris on 2010-12-29
> **piquat said:**
> If I run any one of the three "Human" themes, the close button works properly.  Using something like clear looks with human controls doesn't do it.

Edit:  Aaaaand now I understand why most newbies don't complain about this.  Human IS the default theme.  Works fine if you stick with that...

Interesting.  So I opened up my Appearance menu, and go to choose the "Human" theme and ... it's not there.  That's interesting.  I certainly do not remember removing that.  I will have to hunt down the package to install that; I'm sure it's around somewhere.  I can live with changing to the Human theme as a workaround.  It would be nice to see this actually solved, since it appears that this bug has been around for a few years.

---

### Post by darkhelmetchris on 2010-12-29
> **chrisstankevitz said:**
> Also, most users have a GNOME Panel across the top of their screen.  The close button is never the upper-right pixel for them.  These users always have to perform a precision maneuver to click the X.  Poor saps.
Chris

Yes, that is certainly a side-effect to my choice of real estate layout.  I'm not one to have more than one panel like the default of top/bottom comes already.  And, I admit even though I have switched to Ubuntu more than 3 years ago, I do still prefer my main panel at the bottom.  Curse me for ever adopting such a habit.

---

### Post by darkhelmetchris on 2010-12-29
Okay, so I have done some playing around and noticed:  this is not just the right side, or the top-right corner.  Try this:  since you probably happen to be in Firefox right now, like me, you might notice that if you maximise this window, the web page will extend all the way to the left side of your screen.  I can not right-click to bring up the Firefox context menu here.  If I move in one single pixel from the left "wall", I still can not right-click.  However, if I move in TWO pixels from the left, I can bring up the right-click menu.  Note, the window is maximised and I should be able to run my mouse point over to the very left of the screen anywhere inside the main web page window, and hit the context menu.  That is not the case.  Again, I think this shows it's a window/theme manager problem, and I am not accusing Firefox of having a problem.

Also, as another test, I can SEE these borders if I use OpenOffice Writer -- note that I am not accusing OpenOffice, it's just that OO helps me see the lost border space.  In OO Writer, if I turn off the ruler, you'll notice a 2 pixel border on the left and right sides of a maximised app.  This makes me think that OO is detecting the border (perhaps a different way) from the window/theme manager, whereas Firefox didn't seem to do that.  I just thought it was interesting to see it more clearly defined in another app.

When I get the Human theme back, I'll check to see if this behavior goes away.  Anyone else notice this?

Update:  with the Human theme installed (v 0.39.1 in Maverick) the close button in the top right DOES work.  However, the 2-pixel margins at the left and right of the screen are still there, so I can't run over to the right and grab my window slide bar easily.  Pretty close for a workaround, but only 1/3 there.

---

### Post by darkhelmetchris on 2010-12-29
> **piquat said:**
> ...
[http://gnomesupport.org/forums/viewtopic.php?t=11477&highlight=corner](http://gnomesupport.org/forums/viewtopic.php?t=11477&highlight=corner)
Which lead to this bug report:
[https://bugzilla.gnome.org/show_bug.cgi?id=97703](https://bugzilla.gnome.org/show_bug.cgi?id=97703)
Which also talks about this bug report:
[https://bugzilla.gnome.org/show_bug.cgi?id=97703](https://bugzilla.gnome.org/show_bug.cgi?id=97703)
...
:(

I will be reading up on these, thanks.

Updates:

I have read through the various threads suggested.  There seems to be much talk about the top right corner or button "sizes" and, to me, they are missing the left/right side problems that appear (to me anyway) to be directly linked to this.  Some posts talk about a "visual" and "clickable" area - which I think is a bad idea as I think the borders of a button should be the button itself, and not "bleed" over on to neighboring space or more seriously onto nearby controls.  Mind you, that is just my 2 cents.

Also, some posts talk about modifying the theme to fix the borders.  While this appears undesirable, as there are lots of themes that would need to be altered, I think this might actually be the answer, but I am uncertain.  Adding the "Human" theme did fix the "Close" button in the top-right corner, but left out the left/right margins for things like context menu clicking and window-slider dragging.  Since the "Close" button did start working, it does appear to me to be a theme-specific problem for maximized windows.  The buttons do seem to work intuitively when not maximized.

---

### Post by rvchari on 2010-12-29
try this, i am sure you will be pleased with the outcome.

for the particular theme installed, go to /usr/shre/themes and copy that theme folder to your home folder, `/.themes
then go to `/.themes/YOUR THEME/metacity. once that folder is open, use gedit to edit the metacity-theme-xml file.
edit that file by replacing "2" or "6" all numbers in top title bar edge border to "0". i usually keep all to "0" to get the effect you asked.
then save the file and exit. logout and log in to see the difference. your top right will have the x button in the closest proximity and your mouse click should work !!!

my sample xml file for murrine-unity

<?xml version="1.0"?>

<metacity_theme>
<info>
    <name>Murrine-Unity</name>
    <author>Tony Upton</author>
    <copyright>GPL</copyright>
    <date>July 31, 2010</date>
    <description>Metacity theme based on Benjamin Hardy's "Masa-Colors-Unity" theme</description>
</info>


<!--
    General window layout (geometric stuff)
-->
<frame_geometry name="frame_geometry_normal"  rounded_top_left="true" rounded_top_right="true">
    <distance name="left_width" value="0"/>
    <distance name="right_width" value="0"/>
    <distance name="bottom_height" value="0"/>
    <distance name="left_titlebar_edge" value="0"/>
    <distance name="right_titlebar_edge" value="2"/>
    <distance name="button_width" value="16"/>
    <distance name="button_height" value="16"/>
    <distance name="title_vertical_pad" value="0"/>
    <border name="title_border" left="0" right="0" top="0" bottom="0"/>
    <border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>

<frame_geometry name="frame_geometry_abnormal" title_scale="medium" rounded_top_left="true" rounded_top_right="true">
    <distance name="left_width" value="0"/>
    <distance name="right_width" value="0"/>
    <distance name="bottom_height" value="0"/>
    <distance name="left_titlebar_edge" value="0"/>
    <distance name="right_titlebar_edge" value="2"/>
    <distance name="button_width" value="16"/>
    <distance name="button_height" value="16"/>
    <distance name="title_vertical_pad" value="0"/>
    <border name="title_border" left="0" right="0" top="0" bottom="0"/>
    <border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>



<!--
    Window Title
-->

<draw_ops name="draw_title_text_normal">
    <title x="(((width - title_width) / 2) `max` 2)" y="(((height - title_height) / 2) `max` 2) - 2" color="gtk:text[NORMAL]"/>

</draw_ops>

<draw_ops name="draw_title_text_inactive">
    <title x="(((width - title_width) / 2) `max` 2)" y="(((height - title_height) / 2) `max` 2) - 2" color="shade/gtk:bg[NORMAL]/0.74"/>
</draw_ops>

<!--
    Construct titlebar from rectangles instead so we can pick up the GTK theme
-->

<draw_ops name="draw_title">
 

   <!-- Background gradient -->
    <gradient type="vertical" x="0" y="0" width="width+9" height="height">
        <color value="shade/gtk:bg[NORMAL]/1.05" />
        <color value="shade/gtk:bg[NORMAL]/1.00" />
    </gradient> 

    
    <!-- Topmost dark line -->
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="width" y1="0" y2="0"/>
    
    <!-- Darkening of the left arch -->
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="4" y1="1" y2="1"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="2" y1="2" y2="2"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="1" y1="3" y2="3"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="1" y1="4" y2="4"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="0" y1="5" y2="30"/>
    
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-5" x2="width" y1="1" y2="1"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-3" x2="width" y1="2" y2="2"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-2" x2="width" y1="3" y2="3"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-2" x2="width" y1="4" y2="4"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-1" x2="width" y1="5" y2="90"/>
    
    <!-- Top highlight -->
    <!-- This uses <tint> (which supports alpha) instead of <line> (which doesn't) -->
    <tint color="#ffffff" alpha="0.55" x="5" y="1" width="width - 10" height="1"/> 
    <tint color="#ffffff" alpha="0.15" x="5" y="2" width="width - 10" height="1"/> 
    
</draw_ops>



<draw_ops name="draw_title_inactive">
    <!-- Background gradient -->
    <gradient type="vertical" x="0" y="0" width="width+9" height="height">
       <color value="shade/gtk:bg[NORMAL]/1.05" />
       <color value="shade/gtk:bg[NORMAL]/1.00" />
    </gradient>
    
    <!-- Topmost dark line -->
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="width" y1="0" y2="0"/>
    
    <!-- Darkening of the left arch -->
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="4" y1="1" y2="1"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="2" y1="2" y2="2"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="1" y1="3" y2="3"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="1" y1="4" y2="4"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="0" y1="5" y2="30"/>
    
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-5" x2="width" y1="1" y2="1"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-3" x2="width" y1="2" y2="2"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-2" x2="width" y1="3" y2="3"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-2" x2="width" y1="4" y2="4"/>
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="width-1" x2="width" y1="5" y2="90"/>
    
    <!-- Top highlight -->
    <!-- This uses <tint> (which supports alpha) instead of <line> (which doesn't) -->
    <tint color="#ffffff" alpha="0.55" x="5" y="1" width="width - 10" height="1"/> 
    <tint color="#ffffff" alpha="0.15" x="5" y="2" width="width - 10" height="1"/> 
    
</draw_ops>

<draw_ops name="draw_title_maximized">
    <!-- Background gradient -->
    <gradient type="vertical" x="0" y="0" width="width+9" height="height">
        <color value="shade/gtk:bg[NORMAL]/1.05" />
        <color value="shade/gtk:bg[NORMAL]/1.00" />
    </gradient>
    
    <!-- Topmost dark line -->
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="0" y1="0" y2="0"/>
    
    <!-- Top highlight -->
    <!-- This uses <tint> (which supports alpha) instead of <line> (which doesn't) -->
    <tint color="#ffffff" alpha="0.55" x="0" y="1" width="width" height="1"/> 
    <tint color="#ffffff" alpha="0.15" x="0" y="2" width="width" height="1"/> 
</draw_ops>

<draw_ops name="draw_title_maximized_inactive">
    <!-- Background gradient -->
    <gradient type="vertical" x="0" y="0" width="width+9" height="height">
        <color value="shade/gtk:bg[NORMAL]/1.05" />
        <color value="shade/gtk:bg[NORMAL]/1.00" />
    </gradient>
    
    <!-- Topmost dark line -->
    <line color="shade/gtk:bg[NORMAL]/0.74" x1="0" x2="width" y1="0" y2="0"/>
    
    <!-- Top highlight -->
    <!-- This uses <tint> (which supports alpha) instead of <line> (which doesn't) -->
    <tint color="#ffffff" alpha="0.55" x="0" y="1" width="width" height="1"/> 
    <tint color="#ffffff" alpha="0.15" x="0" y="2" width="width" height="1"/> 
</draw_ops>

<!--
    The frame around windows
-->

<draw_ops name="draw_frame">
	<rectangle color="shade/gtk:bg[NORMAL]/0.74" x="0" y="0" width="width" height="height" filled="true"/>
</draw_ops>

<!--Borderless only: make bottom border less apparent. We can do this now since our statusbars are light.-->
<draw_ops name="bottom_edge">
    <rectangle color="shade/gtk:bg[NORMAL]/0.74" x="0" y="0" width="width" height="height" filled="true"/>
    <gradient type="vertical" x="1" y="height-6" width="width-2" height="5">
        <color value="shade/gtk:bg[NORMAL]/0.85"/>
        <color value="shade/gtk:bg[NORMAL]/0.74"/>
    </gradient>
</draw_ops>


<!-- :::Buttons:::-->

<draw_ops name="button_bg_prelight">
	<image filename="prelight.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_bg_pressed">
	<image filename="pressed.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_bg_unfocused_prelight">
	<image filename="prelight_unfocused.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_bg_unfocused_pressed">
	<image filename="pressed.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>
<!-- menu button -->
<!--
<draw_ops name="button_menu_normal">
<image filename="button_menu_normal.png" x="0" y="2" width="object_width" height="object_height"/>
</draw_ops>
<draw_ops name="button_menu_prelight">
<image filename="button_menu_prelight.png" x="0" y="2" width="object_width" height="object_height"/>
</draw_ops>
<draw_ops name="button_menu_unfocused_prelight">
<image filename="button_menu_prelight.png" x="0" y="2" width="object_width" height="object_height" alpha="0.3"/>
</draw_ops>
<draw_ops name="button_menu_pressed">
<image filename="button_menu_pressed.png" x="0" y="2" width="object_width" height="object_height"/>
</draw_ops>
<draw_ops name="button_menu_unfocused">
<image filename="button_menu_normal.png" x="0" y="2" width="object_width" height="object_height" alpha="0.3"/>
</draw_ops>-->

<!-- menu icon -->
<draw_ops name="button_menu_normal">
<icon x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>
<draw_ops name="button_menu_prelight">
<icon x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>
<draw_ops name="button_menu_unfocused_prelight">
<icon x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height" alpha="0.3"/>
</draw_ops>
<draw_ops name="button_menu_pressed">
<icon x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height"/>
</draw_ops>
<draw_ops name="button_menu_unfocused">
<icon x="(width-mini_icon_width)/2" y="(height-mini_icon_height)/2" width="mini_icon_width" height="mini_icon_height" alpha="0.3"/>
</draw_ops>

<!-- close icon -->
<draw_ops name="button_close_icon">
	<image filename="close.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_close_icon_unfocused">
	<image filename="close_unfocused.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_close_normal">
	<include name="button_close_icon"/>
</draw_ops>
<draw_ops name="button_close_prelight">
	<include name="button_bg_prelight"/>
	<include name="button_close_icon"/>
</draw_ops>
<draw_ops name="button_close_pressed">
	<include name="button_bg_pressed"/>
	<include name="button_close_icon"/>
</draw_ops>
<draw_ops name="button_close_unfocused">
	<include name="button_close_icon_unfocused"/>
</draw_ops>
<draw_ops name="button_close_unfocused_prelight">
	<include name="button_bg_unfocused_prelight"/>
	<include name="button_close_icon_unfocused"/>
</draw_ops>
<draw_ops name="button_close_unfocused_pressed">
	<include name="button_bg_unfocused_pressed"/>
	<include name="button_close_icon"/>
</draw_ops>

<!-- maximize icon -->
<draw_ops name="button_max_icon">
	<image filename="maximize.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_max_icon_unfocused">
	<image filename="maximize_unfocused.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_max_normal">
	<include name="button_max_icon"/>
</draw_ops>
<draw_ops name="button_max_prelight">
	<include name="button_bg_prelight"/>
	<include name="button_max_icon"/>
</draw_ops>
<draw_ops name="button_max_pressed">
	<include name="button_bg_pressed"/>
	<include name="button_max_icon"/>
</draw_ops>
<draw_ops name="button_max_unfocused">
	<include name="button_max_icon_unfocused"/>
</draw_ops>
<draw_ops name="button_max_unfocused_prelight">
	<include name="button_bg_unfocused_prelight"/>
	<include name="button_max_icon_unfocused"/>
</draw_ops>
<draw_ops name="button_max_unfocused_pressed">
	<include name="button_bg_unfocused_pressed"/>
	<include name="button_max_icon"/>
</draw_ops>

<!-- restore icon -->
<draw_ops name="button_restore_icon">
	<image filename="restore.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_restore_icon_unfocused">
	<image filename="restore_unfocused.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_restore_normal">
	<include name="button_restore_icon"/>
</draw_ops>
<draw_ops name="button_restore_prelight">
	<include name="button_bg_prelight"/>
	<include name="button_restore_icon"/>
</draw_ops>
<draw_ops name="button_restore_pressed">
	<include name="button_bg_pressed"/>
	<include name="button_restore_icon"/>
</draw_ops>
<draw_ops name="button_restore_unfocused">
	<include name="button_restore_icon_unfocused"/>
</draw_ops>
<draw_ops name="button_restore_unfocused_prelight">
	<include name="button_bg_unfocused_prelight"/>
	<include name="button_restore_icon_unfocused"/>
</draw_ops>
<draw_ops name="button_restore_unfocused_pressed">
	<include name="button_bg_unfocused_pressed"/>
	<include name="button_restore_icon"/>
</draw_ops>

<!-- minimize icon -->
<draw_ops name="button_min_icon">
	<image filename="minimize.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_min_icon_unfocused">
	<image filename="minimize_unfocused.png"
		x="(width - object_width) / 2"
		y="(height - object_height) / 2"
		width="object_width"
		height="object_height"/>
</draw_ops>

<draw_ops name="button_min_normal">
	<include name="button_min_icon"/>
</draw_ops>
<draw_ops name="button_min_prelight">
	<include name="button_bg_prelight"/>
	<include name="button_min_icon"/>
</draw_ops>
<draw_ops name="button_min_pressed">
	<include name="button_bg_pressed"/>
	<include name="button_min_icon"/>
</draw_ops>
<draw_ops name="button_min_unfocused">
	<include name="button_min_icon_unfocused"/>
</draw_ops>
<draw_ops name="button_min_unfocused_prelight">
	<include name="button_bg_unfocused_prelight"/>
	<include name="button_min_icon_unfocused"/>
</draw_ops>
<draw_ops name="button_min_unfocused_pressed">
	<include name="button_bg_unfocused_pressed"/>
	<include name="button_min_icon"/>
</draw_ops>

<draw_ops name="blank">
<!-- nothing -->
</draw_ops>

<!-- :::Frame styles::: -->

<!-- normal -->
<frame_style name="frame_style_normal_focused" geometry="frame_geometry_normal">
   
<piece position="title" draw_ops="draw_title_text_normal"/>
   <piece position="titlebar" draw_ops="draw_title"/>
   <piece position="left_edge" draw_ops="draw_frame"/>
   <piece position="right_edge" draw_ops="draw_frame"/>
   <piece position="bottom_edge" draw_ops="bottom_edge"/>
   <button function="close" state="normal" draw_ops="button_close_normal"/>
   <button function="close" state="prelight" draw_ops="button_close_prelight"/>
   <button function="close" state="pressed" draw_ops="button_close_pressed"/>
   <button function="minimize" state="normal" draw_ops="button_min_normal"/>
   <button function="minimize" state="prelight" draw_ops="button_min_prelight"/>
   <button function="minimize" state="pressed" draw_ops="button_min_pressed"/>
   <button function="maximize" state="normal" draw_ops="button_max_normal"/>
   <button function="maximize" state="prelight" draw_ops="button_max_prelight"/>
   <button function="maximize" state="pressed" draw_ops="button_max_pressed"/>
   <button function="menu" state="normal" draw_ops="button_menu_normal"/>
   <button function="menu" state="prelight" draw_ops="button_menu_prelight"/>
   <button function="menu" state="pressed" draw_ops="button_menu_pressed"/>
</frame_style>

<frame_style name="frame_style_normal_unfocused" geometry="frame_geometry_normal">
   <piece position="title" draw_ops="draw_title_text_inactive"/>
   <piece position="titlebar" draw_ops="draw_title_inactive"/>
   <piece position="left_edge" draw_ops="draw_frame"/>
   <piece position="right_edge" draw_ops="draw_frame"/>
   <piece position="bottom_edge" draw_ops="bottom_edge"/>
   <button function="close" state="normal" draw_ops="button_close_unfocused"/>
   <button function="close" state="prelight" draw_ops="button_close_unfocused_prelight"/>
   <button function="close" state="pressed" draw_ops="button_close_unfocused"/>
   <button function="minimize" state="normal" draw_ops="button_min_unfocused"/>
   <button function="minimize" state="prelight" draw_ops="button_min_unfocused_prelight"/>
   <button function="minimize" state="pressed" draw_ops="button_min_unfocused"/>
   <button function="maximize" state="normal" draw_ops="button_max_unfocused"/>
   <button function="maximize" state="prelight" draw_ops="button_max_unfocused_prelight"/>
   <button function="maximize" state="pressed" draw_ops="button_max_unfocused"/>
   <button function="menu" state="normal" draw_ops="button_menu_unfocused"/>
   <button function="menu" state="prelight" draw_ops="button_menu_unfocused_prelight"/>
   <button function="menu" state="pressed" draw_ops="button_menu_unfocused"/>
</frame_style>

<frame_style name="frame_style_maximized_focused" geometry="frame_geometry_abnormal">
   <piece position="title" draw_ops="draw_title_text_normal"/>
   <piece position="titlebar" draw_ops="draw_title_maximized"/>
   <piece position="left_edge" draw_ops="draw_frame"/>
   <piece position="right_edge" draw_ops="draw_frame"/>
   <piece position="bottom_edge" draw_ops="bottom_edge"/>
   <button function="close" state="normal" draw_ops="button_close_normal"/>
   <button function="close" state="prelight" draw_ops="button_close_prelight"/>
   <button function="close" state="pressed" draw_ops="button_close_pressed"/>
   <button function="minimize" state="normal" draw_ops="button_min_normal"/>
   <button function="minimize" state="prelight" draw_ops="button_min_prelight"/>
   <button function="minimize" state="pressed" draw_ops="button_min_pressed"/>
   <button function="maximize" state="normal" draw_ops="button_restore_normal"/>
   <button function="maximize" state="prelight" draw_ops="button_restore_prelight"/>
   <button function="maximize" state="pressed" draw_ops="button_restore_pressed"/>
   <button function="menu" state="normal" draw_ops="button_menu_normal"/>
   <button function="menu" state="prelight" draw_ops="button_menu_prelight"/>
   <button function="menu" state="pressed" draw_ops="button_menu_normal"/>
</frame_style>

<frame_style name="frame_style_maximized_unfocused" geometry="frame_geometry_abnormal">
   <piece position="title" draw_ops="draw_title_text_inactive"/>
   <piece position="titlebar" draw_ops="draw_title_maximized_inactive"/>
   <piece position="left_edge" draw_ops="draw_frame"/>
   <piece position="right_edge" draw_ops="draw_frame"/>
   <piece position="bottom_edge" draw_ops="bottom_edge"/>
   <button function="close" state="normal" draw_ops="button_close_unfocused"/>
   <button function="close" state="prelight" draw_ops="button_close_prelight"/>
   <button function="close" state="pressed" draw_ops="button_close_unfocused"/>
   <button function="minimize" state="normal" draw_ops="button_min_unfocused"/>
   <button function="minimize" state="prelight" draw_ops="button_min_prelight"/>
   <button function="minimize" state="pressed" draw_ops="button_min_unfocused"/>
   <button function="maximize" state="normal" draw_ops="button_restore_unfocused"/>
   <button function="maximize" state="prelight" draw_ops="button_restore_prelight"/>
   <button function="maximize" state="pressed" draw_ops="button_restore_unfocused"/>
   <button function="menu" state="normal" draw_ops="button_menu_unfocused"/>
   <button function="menu" state="prelight" draw_ops="button_menu_unfocused"/>
   <button function="menu" state="pressed" draw_ops="button_menu_unfocused"/>
</frame_style>

<frame_style_set name="frame_style_set_normal">
  <frame focus="yes" state="normal" resize="both" style="frame_style_normal_focused"/>
  <frame focus="no" state="normal" resize="both" style="frame_style_normal_unfocused"/>
  <frame focus="yes" state="maximized" style="frame_style_maximized_focused"/>
  <frame focus="no" state="maximized" style="frame_style_maximized_unfocused"/>
  <frame focus="yes" state="shaded" style="frame_style_normal_focused"/>
  <frame focus="no" state="shaded" style="frame_style_normal_unfocused"/>
  <frame focus="yes" state="maximized_and_shaded" style="frame_style_maximized_focused"/>
  <frame focus="no" state="maximized_and_shaded" style="frame_style_maximized_unfocused"/>
</frame_style_set>

<window type="normal" style_set="frame_style_set_normal"/>
<window type="dialog" style_set="frame_style_set_normal"/>
<window type="modal_dialog" style_set="frame_style_set_normal"/>
<window type="menu" style_set="frame_style_set_normal"/>
<window type="utility" style_set="frame_style_set_normal"/>
<window type="border" style_set="frame_style_set_normal"/>

<menu_icon function="close" state="normal" draw_ops="button_close_normal"/>
<menu_icon function="maximize" state="normal" draw_ops="button_max_normal"/>
<menu_icon function="unmaximize" state="normal" draw_ops="button_max_normal"/>
<menu_icon function="minimize" state="normal" draw_ops="button_min_normal"/>


</metacity_theme>

---

### Post by rvchari on 2010-12-29
if you want the window buttons on the top right, then i think you have to go to gconf-editor.
issue the command gconf-editor in terminal and editor is open. go to apps > metacity  > general. in the right side you should find button layout. right click on the key and edit it to look like this:
menu:minimize,maximize,close.
exit and you will habe buttons in top right. you can also set this as mandatory so that you need not edit this file every now and then you change your theme.
i hope you will get the feel of what you were looking for

---

### Post by darkhelmetchris on 2010-12-29
> **rvchari said:**
> if you want the window buttons on the top right, then i think you have to go to gconf-editor.
issue the command gconf-editor in terminal and editor is open. go to apps > metacity  > general. in the right side you should find button layout. right click on the key and edit it to look like this:
menu:minimize,maximize,close.
exit and you will habe buttons in top right. you can also set this as mandatory so that you need not edit this file every now and then you change your theme.
i hope you will get the feel of what you were looking for

Thanks for trying rvchari, but this is a different problem.  I already have the buttons arranged so that minimize/maxmize/close are in the top right.  The problem is that there is an unclickable border around the left/top/right of a window when it is maximized and the existing buttons do not behave intuitively.  ;)

---

### Post by rvchari on 2010-12-29
it works for me. title border value to "0" does the trick. inface the border is so reduced that only the "x" button occupies there and hence all area is covered by mouse click. thats what i feel.
edit the metacity-1 xml file, may be you ll get the answer ?

---

### Post by rvchari on 2010-12-29
if the top panel is the culprit that doesnt let you go right in the corner then netbook edition doesnt have the feature of auto hide (atleast to the extent of what i have been fiddling with mine) best is to switch to desktop edition, install global menu applet if you need a global menu and you problem must be fixed ?

---

### Post by darkhelmetchris on 2010-12-29
> **rvchari said:**
> it works for me. title border value to "0" does the trick. inface the border is so reduced that only the "x" button occupies there and hence all area is covered by mouse click. thats what i feel.
edit the metacity-1 xml file, may be you ll get the answer ?

Thank-you rvchari, this is close.  But, it is incomplete.  I have noticed that by changing:
```
<frame_geometry name="normal" ... >
...
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>

```
these to "0" instead of the default "3" that the top-right corner and top-left corner do work.  However, ONLY the top-right and top-left pixel seem to be fixed.  the right-side of the close button still doesn't work.

Also, this does not affect the missing left and right margins - I can still not get a right-click context menu in a maximized screen when my mouse is anywhere along the left edge of the window, and I can not drag the window-slider along the right edge of the window.  I still have to come inward 2 pixels.

...good thoughts though.

---

### Post by darkhelmetchris on 2010-12-29
Hmm, actually, now I am a bit confused.  When I look at the theme's xml file, I notice this:
```
<frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <!-- strip frame spacing off the normal geometry when maximised -->
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="1"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
</frame_geometry>
```
..and the comment in there says it's supposed to strip off the frame spacing.  It seems to me that the frame spacing is still present when my windows are maximized.  Now I am actually wondering, maybe, if that stripping is being ignored?

---

### Post by rvchari on 2010-12-29
try to change top left and right window borders to squared instead of round. i think the matter lies in the numbers that we give. i usually keep doing all sorts of permutations / combinations to my .theme xml file (knowing very well that if nything crashes or stops to function, i can revert back by copying the original xml from /usr/share/themes to my .themes home folder !!!

hop you get what you aim... as the saying goes, the thirst for excellence never dies !!!

---

### Post by rvchari on 2010-12-29
i think you have to change the window borders distance value to "0" too for top, left, right, bottom. that pixel will come in handy for you probs to get solved.

check out my sample xml file, i did "0" to almost everything. the window and terminal looks good without the dumb borders !!!

---

### Post by darkhelmetchris on 2010-12-29
> **rvchari said:**
> try to change top left and right window borders to squared instead of round. i think the matter lies in the numbers that we give. i usually keep doing all sorts of permutations / combinations to my .theme xml file (knowing very well that if nything crashes or stops to function, i can revert back by copying the original xml from /usr/share/themes to my .themes home folder !!!

hop you get what you aim... as the saying goes, the thirst for excellence never dies !!!

I believe that my maximized windows are already square (not round) as this line shows it:
```
<frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">

```
so setting them for square was not an option.

I like the idea that I can just remove the ~/.themes/Human folder to get back to the default, that's handy.

---

### Post by darkhelmetchris on 2010-12-29
Okay, I no longer believe that this is a theme-specific problem.  Here's why:

In the last few posts, there has been talk about updating the XML file for the theme.  Using the "Human" theme as a baseline, I find this code:
```
<frame_geometry name="normal_maximized" parent="normal" rounded_top_left="false" rounded_top_right="false" rounded_bottom_left="false" rounded_bottom_right="false">
  <!-- strip frame spacing off the normal geometry when maximised -->
  <distance name="left_width" value="0"/>
  <distance name="right_width" value="0"/>
  <distance name="bottom_height" value="1"/>
  <distance name="left_titlebar_edge" value="0"/>
  <distance name="right_titlebar_edge" value="0"/>
  <border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>
```Now, when I update this line in that section:
```
  <distance name="left_width" value="0"/>
```to read this instead:
```
  <distance name="left_width" value="8"/>
```I get an 8-pixel border on the left of my maxmized windows (as expected).  It's original value is zero, and so that *should* mean that there is no border, and yet there is definitely a 2-pixel-wide border left when this value is set to 0.

Also, I have tried this for multiple themes, and the result is the same.

AND.. it should be noted that this problem does NOT exist in Ubuntu 9.10 where the left/right sides of a maximized window DO operate correctly.

I now believe this to be specific to Ubuntu 10.10.

...thoughts?

---

### Post by rvchari on 2010-12-29
try to # that strip off line and see how it works....
if you can decipher each and ever line in the xml file and try editiong it line by line with due noting on what we do, we should arrive at the solution of what we seek....

in a way its atleast a partial victory of nearing to where you wish to go !!! if i m not mistaken.

try posting a thread or follow the thread of "perfect desktop"

---

### Post by rvchari on 2010-12-29
try following this thread...
lots of comments are there on what guys r using....
[http://ubuntuforums.org/showthread.php?t=953775](http://ubuntuforums.org/showthread.php?t=953775)

---

### Post by darkhelmetchris on 2010-12-29
> **rvchari said:**
> try following this thread...
lots of comments are there on what guys r using....
[http://ubuntuforums.org/showthread.php?t=953775](http://ubuntuforums.org/showthread.php?t=953775)

Thanks rvchari, but I think we're a little off-topic now and I would just like to steer this back to the heart of the problem.

I now believe that there is a 2-pixel margin around maximized windows in Ubuntu 10.10 and this does not appear to be related to any specific theme or the related XML files for them.  The problem does not exist in Ubuntu 9.10.

In my previous post, by editting the xml files, I updated the left margin to be 8-pixels and saw that it did make an 8-pixel margin; however, setting it to zero does not make the margin zero.  This problem seems to affect multiple (if not all themes) and has the following noticeable problems:

- if you have your minimize/maximize/close buttons configured for the top-right of your windows, then when you use a maximized window, the very top-right pixel is not sensitive to the close button -- this makes it difficult to quickly jump up to the top right corner of your screen and hit the close button when you're moving around quickly, and forces you to come inward with slow precision to use the window manager buttons.

- regardless of the title bar customizations, there is a 2-pixel-wide non-clickable region at the extreme left, top, and right of all maximized windows -- you can not zip your mouse up to the top of your titlebar and drag a window, you can not get a context menu by right clicking on the extreme left/right of a maximized window, and you can not drag the window-slider using the right-most 2 pixels -- this means you must move inward 2 pixels to do these tasks -- losing much of your mousing speed to do this.

- these problems do not appear to be theme-specific, they are present in many themes and this problem does not show in Ubuntu 9.10, and after trying a previous machine, nor does it exist in Ubuntu 8.10 - it appears to be new to 10.10.

---

### Post by piquat on 2010-12-29
I see my nagging spurred someone else.  :)

The reason I suggested the Human theme:

I have a second machine that is set up for torrents.  I didn't do anything to the desktop except moving the upper panel.  When I did that, I noticed the close button problem.  I tried a few themes and Human worked.

Unfortunately, I have since formatted that drive and now can't look at that xml file to compare differences.:frown:

---

### Post by chrisstankevitz on 2010-12-30
> **darkhelmetchris said:**
> 
```
  <distance name="left_width" value="0"/>
```to read this instead:
```
  <distance name="left_width" value="8"/>
```I get an 8-pixel border on the left of my maxmized windows (as expected).  It's original value is zero, and so that *should* mean that there is no border, and yet there is definitely a 2-pixel-wide border left when this value is set to 0.


This is excellent detective work.  Is there a "2" hiding anywhere else in the file?

Chris

---

### Post by rvchari on 2011-01-02
even after allocating left/right top/bottom border width value as "0" there seems to be one pixel left on the window end. the title bar end shrinks but window doesnt. i tried editing after installing minimalista metacity and editing the metacity xml file.
the top face of the window title bar works but extreme right / left doesnt. when i noticed it more keenly, i found that the extreme borders touch the edges of our monitor but top title bar left and right corner is shrunk (coz of the "0" value) may b this is the problem that extreme left and right side doesnt really reach value "0" where as window title bar configures.

i hope u guys r getting what i mean to describe. i ll give a screen shot of my window border.

zoom in to have a closer look at the top left part of my window to get what i mean to say.

any solutions for this ?

---

### Post by chrisstankevitz on 2011-01-02
How about specifying -1 instead of 0?

---

### Post by rvchari on 2011-01-02
but the current behaviourial logic wont work.
when value "0" is given for all, title bar width shrinks but window width doesnt seem to as shown in the screen shot i posted earlier,
the same will hold true for "-1" as i dont think "-1" can be specifically given for windows and "0" for title bar ?

still its worth giving a try and wait for the appearance and performance

---

### Post by darkhelmetchris on 2011-01-04
> **chrisstankevitz said:**
> This is excellent detective work.  Is there a "2" hiding anywhere else in the file?
Chris

Thanks. I have searched the files for the "2"s and can find none.  However, that is no surprise to me, as I really don't think this is a theme xml problem.  I believe that the window manager is actually responsible for the "dead margins" (as I am starting to call them).

---

### Post by darkhelmetchris on 2011-01-04
> **chrisstankevitz said:**
> How about specifying -1 instead of 0?

I tried using -1 and -2 and -8 also, just for fun.  In each case, the window manager didn't like that, and refused to display title bars at all, for all application windows.  Restoring the value to 0 reinstated the title bars.

Each theme's .xml config file (that I have tried, and I have tried quite a few) gives the same result.

I am reasonably confident that this is a window manager problem.  But I am a little uncertain how to proceed.  Perhaps there is someone that can explain how to temporarily substitute an older version of metacity to test it in-place?

(annotation)
Also, please note that I have not tried this with Ubuntu 10.04 as I don't have that version available.  I can, however, confirm that this problem does not exist in 9.10 or 8.10 and only shows up in 10.10

You just go over to the extreme left or right of your desktop and you can not right-click to get the desktop's context menu.  Moving inward 2 pixels from the right or left side of the desktop then allows you to right-click and get the context menu.

---

### Post by chrisstankevitz on 2011-01-04
> **darkhelmetchris said:**
> I am reasonably confident that this is a window manager problem.  But I am a little uncertain how to proceed.

I understand and I am also uncertain how to proceed.  What does this tell us:

Add a top panel (if one does not exist).  Move the controls so that the "close/shutdown/logout" control (circle icon) is in the upper-right corner.  This control can be activated by moving your mouse to the upper-right-most pixel.

Chris

---

### Post by darkhelmetchris on 2011-01-08
I believe I have solved this problem.  For me, this was NOT a metacity or theme problem; it was a side-effect of enabling a particular part of Compiz.

The 2-pixel-wide unclickable margin around the left and right edges of the screen is caused by the "Rotate Cube" portion of Compiz.  Specifically the "Rotate Flip Left" and "Rotate Flip Right" options.

In the CompizConfig Settings Manager, navigate to:
Category:  Desktop
Section:  Rotate Cube
Tab:  Bindings
SubSection:  Rotate Cube
in "Rotate Flip Left" click the button to the left of the edit-pencil, turn off all edges
in "Rotate Flip Right" do the same.

This has now restored my desktop margins and I can click inside them.  Noted:
- for a bare desktop, right-click context menus now work at extreme left and right
- for maximized windows, the close-window "X" in the top right now works properly
- for maximized windows, the window slider now works all the way to the right edge

The downside (which I am quite willing to accept):
- dragging windows off the side of the desktop to rotate the desktop cube is no longer possible.  (Other types of desktop cube rotation still work fine)

I hope this helps the rest of you out!  It puzzled me for .. two and a half months.

---

### Post by darkhelmetchris on 2011-01-08
> **piquat said:**
> Just remembered something.  If you have the SimpleCompiz Config Settings Manager installed then right click your desktop and choose Change Desktop Background then Visual Effects and next to Custom choose Preferences.  In the menu that opens choose Edges.  Do these Edges settings have something to do with this?...

Kudos must also go to user piquat for being very close to solving this  way-back-when.  SO close!  I did not have the "simple" compiz manager, I  had the full one, so originally I couldn't navigate to where you  suggested, and thus I abandoned your idea.  I should have listened more closely and thought about edge detection, then I wouldn't have had to suffer for so long.  I don't know what made me think to  check compiz today, but I got to playing around and found this quite by  accident!  A quick review of the posts showed me that you were close to this solution weeks ago.  In Homer's words:  Doh!

---

### Post by rvchari on 2011-01-08
hmmmmmmm 2-1/2 months of result did bear fantastic result....
are the guys who initially wrote compiz ever test it like how you did ? m sure no....
i did it and its fine. desktop switcher will come in handy for disabled effects... right ?

---

