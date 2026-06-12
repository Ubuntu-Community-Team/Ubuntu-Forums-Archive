---
title: "Latest Greybird theme"
date: 2012-08-05
forum: Desktop Environments
---

### Post by vasa1 on 2012-08-05
I'm thinking of trying this theme on my Xfce 4.10 sitting on 12.04 even though the link below refers to quantal. (I haven't tried any *bird theme before.)

I came across [http://xubuntu.org/news/xubuntus-default-theme-gets-a-refresh-for-quantal/](http://xubuntu.org/news/xubuntus-default-theme-gets-a-refresh-for-quantal/) which has a link to the tarball. Has anyone tried this out?

This quote promises interesting times ahead:
"After having had a tendency to soften colors and contrasts, I&#8217;ve decided to take a (bold?) step and counter this tendency. This is why the changes for the upcoming Quantal release might seem more drastic then between the releases before. After playing with it for a while, I realized that going this direction half-way wouldn&#8217;t work well, so while I&#8217;m aware that there might be quite a bit of whining (partly because people may miss the &#8220;old Greybird&#8221;, partly because change always provokes whining) I really hope that many and most of you will fall in love with the changes the way I did while working on it."

---

### Post by Toz on 2012-08-05
I've tried it out. It looks okay, but a little too bright for my liking. Note that the tarball referenced in that link doesn't work any more. You can grab the latest version directly from here: [https://github.com/shimmerproject/Greybird/downloads]("https://github.com/shimmerproject/Greybird/downloads").

---

### Post by vasa1 on 2012-08-06
Thanks for the response and the link. I've downloaded it, extracted to .themes and installed it.

Now to play with it :)

---

### Post by vasa1 on 2012-08-06
I'm obviously going to have a lot of questions!
My first one is this: In themerc, I want to turn off all shadows.
This one should be simple I hope:
title_shadow_active=**true**
I'm going to change it to **false**.

But I'm not sure about:
(in)active_text_shadow_color=#ececec
and
shadow_delta_height=2
shadow_delta_width=0
shadow_delta_x=0
shadow_delta_y=-10
shadow_opacity=50

Can I just delete those lines?

Edit: deleting doesn't break anything but it doesn't remove the shadow effect either.

---

### Post by Toz on 2012-08-06
If you have the compositor enabled (Settings Manager -> Window Manager Tweaks -> Compositor Tab), you can disable them there.

---

### Post by vasa1 on 2012-08-06
> **Toz said:**
> If you have the compositor enabled (Settings Manager -> Window Manager Tweaks -> Compositor Tab), you can disable them there.
Will enabling the compositor make things more heavy? I had that impression and so I didn't want to.

In any case, it looks like even simple changes to themerc aren't working. I changed to another theme and back. Do I have to log out and log in? That would make tweaking more laborious.

---

### Post by Toz on 2012-08-06
The themerc file is only for the window manager (not appearance) configuration and to make it take effect, change the window manager theme away from and back to Greybird ('xfwm4 --replace' may also work - not tested).

As for the compositor, I'm not sure of the load it will carry, but I don't believe its alot. Its not as performance-heavy as compiz. Try enabling it and seeing.

---

### Post by vasa1 on 2012-08-06
> **Toz said:**
> The themerc file is only for the window manager (not appearance) configuration and to make it take effect, change the window manager theme away from and back to Greybird ('xfwm4 --replace' may also work - not tested).

As for the compositor, I'm not sure of the load it will carry, but I don't believe its alot. Its not as performance-heavy as compiz. Try enabling it and seeing.

Good point! I was changing the appearance. I will try with the window manager. Now that you mention it, I remember you had pointed it out before as well. So most likely I won't have to enable compositing.

---

### Post by vasa1 on 2012-08-06
Worked perfectly.

I also changed these two *true*s to false:
title_shadow_active=**false**
title_shadow_inactive=**false**

(I don't like text shadows anywhere. I've even disabled them globally in my browsers.)

Now to explore further. Mainly, I want to darken anything brighter than #BBBBBB.

---

### Post by vasa1 on 2012-08-06
Editing just the first line of gtkrc```
#gtk_color_scheme	= "bg_color:#CECECE\nselected_bg_color:#398ee7\nbase_color:#fcfcfc" # Background, base.
gtk_color_scheme	= "bg_color:#999999\nselected_bg_color:#398ee7\nbase_color:#aaaaaa" # Background, base.

```
has made Thunar to my liking.

---

### Post by vasa1 on 2012-08-06
One task for the day is to sort out the title bars. I got the text color the way I want by editing themerc but I can't figure out whether it's possible to alter the background. Right now, it's pale grey with a gradient effect.
(I had the title bar sorted out in Ambiance and I *may* have kept notes.)

Other than that, I think I have my gtk2 stuff in order. gtk3 is pending :)

As a general observation, I feel that this gtk stuff is more complicated than web page css and browser chrome themes because in gtk, a lot of "elements" share the same "symbolic color". The knock-on effect of changing something can later be seen in an unexpected place.

And, in one case, I got the impression that **only** symbolic colors are accepted and not hex code or RGB or standard names.

---

### Post by Toz on 2012-08-06
> **vasa1 said:**
> One task for the day is to sort out the title bars. I got the text color the way I want by editing themerc but I can't figure out whether it's possible to alter the background. Right now, it's pale grey with a gradient effect.
These are made up of image files in the xfwm folder - you'll need to edit them individually to change the colour. For this particular theme, the image files for the title bar are only 1 pixel wide, so it makes it difficult to see. Have a look at some the other theme files and their xfwm folders for exampled.
> 
(I had the title bar sorted out in Ambiance and I *may* have kept notes.)

Other than that, I think I have my gtk2 stuff in order. gtk3 is pending :)

As a general observation, I feel that this gtk stuff is more complicated than web page css and browser chrome themes because in gtk, a lot of "elements" share the same "symbolic color". The knock-on effect of changing something can later be seen in an unexpected place.

And, in one case, I got the impression that **only** symbolic colors are accepted and not hex code or RGB or standard names.

Yes I agree. There is also a lack of documentation on how to do this, so I find its more investigation than configuration.

---

### Post by vasa1 on 2012-08-07
> **Toz said:**
> These are made up of image files in the xfwm folder - you'll need to edit them individually to change the colour. For this particular theme, the image files for the title bar are only 1 pixel wide, so it makes it difficult to see. Have a look at some the other theme files and their xfwm folders for exampled.

Yes I agree. There is also a lack of documentation on how to do this, so I find its more investigation than configuration.

Second point first: it's a relief that it's not just me :)
I was hoping to pick up some tips from here: [http://worldofgnome.org/making-gtk3-themes-part-1-basics/](http://worldofgnome.org/making-gtk3-themes-part-1-basics/)

Re. the xfwm folder, thanks for the pointer. I will poke around there.

---

### Post by vasa1 on 2012-08-07
Minor point about the title bar. The choices I have when I open Settings, Settings Manager, Window Manager are:
Default
Daloa
Greybird
Kokodi
Moheli

From my past experience with *Ambiance*, I remember being able to alter the color of the title bar relatively simply when I chose "Default". So I went back to *Default* instead of *Greybird* and the title bar color is controlled by selected_bg_color.

Edit:
I think Greybird is the only totally "problematic" one in this respect. The others do take up the selected_bg_color to a large extent.

---

### Post by vasa1 on 2012-08-08
> **Toz said:**
> I've tried it out. It looks okay, but a **little too bright** for my liking. Note that the tarball referenced in that link doesn't work any more. You can grab the latest version directly from here: [https://github.com/shimmerproject/Greybird/downloads]("https://github.com/shimmerproject/Greybird/downloads").
@Toz, I've managed to darken it to my liking. I don't like bright stuff either.

---

### Post by vasa1 on 2012-08-08
Incidentally, [http://shimmerproject.org/](http://shimmerproject.org/) is currently down for everyone, not just me. Have they moved? (I got this link from the github page.)

---

### Post by Toz on 2012-08-08
Not just shimmerproject, but all of Xfce (Xfce.org, Xfce Forums, Xfce git). I wonder whats up?

---

### Post by SantaFe on 2012-08-08
No wonder I got It's not just you! [http://www.xfce.org](http://www.xfce.org) looks down from here on [http://downforeveryoneorjustme.com](http://downforeveryoneorjustme.com) 

Boy, wish that had an easier web address. ;)

---

### Post by vasa1 on 2012-08-08
> **SantaFe said:**
> No wonder I got It's not just you! [http://www.xfce.org](http://www.xfce.org) looks down from here on [http://downforeveryoneorjustme.com](http://downforeveryoneorjustme.com) 

Boy, wish that had an easier web address. ;)
There is:
[http://www.isup.me/](http://www.isup.me/) ;)

---

### Post by vasa1 on 2012-08-08
I just solved a small issue.

Since my set-up is Xfce 4.10 on Ubuntu 12.04, I've gotten to like the overlay scrollbars on gtk3 apps (as expected) but also on Thunar.

With the Ambiance theme, both gtkrc and gtk-widgets.css had clear sections on the overlay scrollbar and I could tweak those sections.

But with Greybird, the gtkrc section is missing any mention of overlay scrollbars.

The workaround for that is to copy over
```
style "overlay_scrollbar"
{
	bg[SELECTED] = shade (1.0, @selected_bg_color)
	bg[INSENSITIVE] = shade (0.85, @bg_color)
	bg[ACTIVE] = shade (0.6, @bg_color)
}

```
and```
# Overlay scrollbar
widget_class "*<OsScrollbar>" style "overlay_scrollbar"
widget_class "*<OsThumb>" style "overlay_scrollbar"

```
from the Ambiance gtkrc and stick it into Greybird's gtkrc in roughly equivalent positions.

---

### Post by vasa1 on 2012-08-08
Now I need to figure out [how to tweak Sudoku's grid to make the squares we have to fill **less white**]("http://ubuntuforums.org/showpost.php?p=12055099&postcount=1").

---

### Post by SantaFe on 2012-08-08
Ask and Ye shall receive! Thanks for the link!:D

And Xfce is back up now. ;)  Still wondering why no announcement on the forums as to why it was down. {sniff} ;)

---

### Post by vasa1 on 2012-08-08
I tried to post a comment on the [http://shimmerproject.org/](http://shimmerproject.org/) site but I get "Dang, you didn't check the box indicating you are human". Dang!

---

### Post by vasa1 on 2012-08-08
Is ~/.themes/Greybird/gtk-3.0/settings.ini functional? I can put any colors in there without any effect at all.
What is its purpose?
IIRC, it was functional in 11.04 (and maybe even 11.10).

---

### Post by Toz on 2012-08-08
> **vasa1 said:**
> Is ~/.themes/Greybird/gtk-3.0/settings.ini functional? I can put any colors in there without any effect at all.
What is its purpose?
IIRC, it was functional in 11.04 (and maybe even 11.10).

Should be. Do you have a theme called Greybird in /usr/share/themes? If so, maybe that one is taking precedence.

---

### Post by vasa1 on 2012-08-08
> **Toz said:**
> Should be. Do you have a theme called Greybird in /usr/share/themes? If so, maybe that one is taking precedence.

No, I don't have a Greybird in /usr/themes. I unpacked this one into ~/.themes. And, I understand that anything in ~/.themes should take precedence over anything in /usr/share/themes.

BTW, as I mentioned a couple of posts earlier, I can't post a comment on this site: 
[http://shimmerproject.org/project/greybird/](http://shimmerproject.org/project/greybird/). The last entry (by Simon Steinbeiß) was on **January 4, 2012**. So maybe it's not just me? I get a Word Press error about not proving I'm human. I've even accessed that page with another browser and no ad or script or plug-in blockers of any sort.

---

### Post by Toz on 2012-08-08
I was going to suggest the #shimmer IRC channel, but I see you're already there.

EDIT: Just had a thought - the gtk3.0 config files only affect gtk3 apps. Are you testing the changes on a gtk3 app?

---

### Post by vasa1 on 2012-08-09
> **Toz said:**
> I was going to suggest the #shimmer IRC channel, but I see you're already there.

EDIT: Just had a thought - the gtk3.0 config files only affect gtk3 apps. Are you testing the changes on a gtk3 app?

This is aesthetically offensive but I wanted to see a difference!
```
[Settings]
gtk-color-scheme = "base_color:green\nbg_color:#cecece\ntooltip_bg_color:#000000\nselected_bg_color:#398ee7\ntext_color:#000000\nfg_color:#3c3c3c\ntooltip_fg_color:#e1e1e1\nselected_fg_color:green\nlink_color:#2c82dd"
gtk-auto-mnemonics = 1
```
And here's an image of gedit and its help screen:

---

### Post by vasa1 on 2012-08-26
Couple of points ... 

Greybird recently became [available via ppa]("http://www.webupd8.org/2012/08/greybird-default-xubuntu-theme-gets.html") and the authors feel it can be used for DEs other than Xfce as well.

The other is that, depending on circumstances, it is possible to avoid the use of **.gtkrc-2.0** for doing stuff like that described by VTPoet in [Changing Desktop Tile/Grid Spacing (Placement of Icons)]("http://ubuntuforums.org/showthread.php?p=12196490#post12196490").
Those entries can be placed in the Greybird's **gtkrc** file itself.

Other entries related to the panels can be found and modified if needed (or entered *de novo*) in **xfce-panel.rc**.

---

### Post by Toz on 2012-08-26
> **vasa1 said:**
> 
The other is that, depending on circumstances, it is possible to avoid the use of **.gtkrc-2.0** for doing stuff like that described by VTPoet in [Changing Desktop Tile/Grid Spacing (Placement of Icons)]("http://ubuntuforums.org/showthread.php?p=12196490#post12196490").
Those entries can be placed in the Greybird's **gtkrc** file itself.

I'm not a fan of editing the theme file directly because there is a chance that on an update, the file (and your changes) will get over-written. Better options include making a copy of the theme files and editing the copy, or placing the changes in /etc/gtk-2.0/gtkrc or /etc/gtk-3.0/* for system-wide effect.

For single-user changes, ~/.gtkrc-2.0 & ~/.config/gtk-3.0/* is the correct place to make the edits.

---

### Post by vasa1 on 2012-08-26
> **Toz said:**
> I'm not a fan of editing the theme file directly because there is a chance that on an update, the file (and your changes) will get over-written. Better options include making a copy of the theme files and editing the copy, or placing the changes in /etc/gtk-2.0/gtkrc or /etc/gtk-3.0/* for system-wide effect.

For single-user changes, ~/.gtkrc-2.0 & ~/.config/gtk-3.0/* is the correct place to make the edits.

But isn't it that the updates will affect only themes in /usr/share/themes and not those in ~/.themes?

While installing via the ppa, I don't think I was offered a destination. It installed in /usr/share/themes.

What I did then was to copy over the folder to ~/.themes where I renamed it to MyGreybird. I can mess around with that knowing that the original is always available in /usr/share/themes.

The ppa has updated twice already and it affects only the theme in /usr/share/themes.

My thinking behind not using .gtkrc-2.0 is that that file is available to any theme. And sometimes I log into a Unity session and use the Ambiance theme which I've set up differently.

(I think there's a way around that by adding theme-specific suffixes to .gtkrc-2.0.)

---

### Post by Toz on 2012-08-26
Yes you are right - updates won't affect themes in ~/.themes. Copying them over to ~/.themes is a good idea. 

I haven't come across any options for theme-specific settings in .gtkrc-2.0. That would be interesting though.

---

### Post by vasa1 on 2012-08-27
> **Toz said:**
> ...
I haven't come across any options for theme-specific settings in .gtkrc-2.0. That would be interesting though.

I'll try to describe what I mean by that. Let's say I have some Greybird-specific content I want to include in .gtkrc-2.0. Instead of doing so, I put the content in another file called /home/vasa1/.gtkrc.greybird. And then include just a line such as:
```
include "/home/vasa1/.gtkrc.greybird"
```
in .gtkrc-2.0.

GNOME Color Chooser does something like that as well. It creates a file called ".gtkrc-2.0-gnome-color-chooser" and modifies .gtkrc-2.0 to "include" it.

I guess the downside will be having to comment out the unwanted "include" when some other theme is to be used.

---

### Post by vasa1 on 2012-08-27
I'm attaching an image of part of Thunar's window. I want to know the technical name of the part marked red.

---

### Post by Toz on 2012-08-27
Its the GTKTreeView widget. Here is the relevant code from the Bluebird theme:

```

style "murrine-treeview-header" = "murrine-button"
{
	xthickness   = 2
	ythickness   = 1
	
	bg[NORMAL]	 = shade (1.14, @bg_color)  # Color for treeview headers.
	bg[PRELIGHT] = shade (0.98, @bg_color)  # Color for treeview header prelight.
	bg[ACTIVE]   = shade (0.85, @bg_color)  # Color for pressed-treeview.
  	
	engine "murrine" 
	{
		roundness = 0  # This makes treeview progressbars square.
	}
}
```
```

widget_class "*.<GtkTreeView>.<GtkButton>" style "murrine-treeview-header"

```

---

### Post by vasa1 on 2012-08-27
> **Toz said:**
> Its the GTKTreeView widget. Here is the relevant code from the Bluebird theme:
...
Thanks a lot. :)

That was one of the few remaining  aspects that was bugging me.

---

### Post by vasa1 on 2012-08-29
I was going nuts trying to compare the changes I make relative to the Greybird ppa each time it (it = ppa) updates.

Then I came across **sdiff**.

Now I use, for example,
```
alias diffgtkr='sdiff -s --width=148 /usr/share/themes/greybird-git/gtk-2.0/gtkrc /home/vasa1/.themes/NewGreybird/gtk-2.0/gtkrc > ~/Desktop/gtkrc-diff'

```
Then I can view the output in gedit (with wrapping turned off).

---

