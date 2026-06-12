---
title: "Desktop Eyecandy / Tweaks"
date: 2006-02-07
forum: Desktop Environments
---

### Post by kverde on 2006-02-07
Just wanted some help on some small tweaks that I'd like to make to improve the look of the desktop.  If anyone has any tips, I'd greatly appreciate it.  

[LIST=1]
[*]If the desktop background is dark, this text is difficult to read.  Is there a way to make it white?
[*]This isn't fully transparent, and I'd like it to launch my own calendar program (web-based).
[*]I want this transparent, too!  Why can't the divider go away or be better with tranparency?
[*]I've seen some ppl's desktops that have terminals with no borders or menus.  they look really cool--how can I get that going?
[*]Sometimes this gdesklet has text that cuts off.
[*]same as 3 - improved transparency
[*]Same as 1 - change font color if possible
[*]Notice the corners -- I know I'm anal, but it doesn't look good to have those white pixels where transparency should be.[/LIST]

Any thoughts?  I'm especially curious about #4 --- the rest are small niggles.

Thanks for any help.

---

### Post by audax321 on 2006-02-08
For #4, check these out:

[HOWTO: True or Pseudo-Transparent Borderless Pop-up Terminals]("http://ubuntuforums.org/showthread.php?t=36811&highlight=transparent+terminal")
and
[HOWTO: Terminal for desktop background.]("http://ubuntuforums.org/showthread.php?t=81727&highlight=transparent+terminal")

I've used the first one before and it works nice, never used the second link.

---

### Post by mcmillan on 2006-02-08
The only one I can give really good suggestions is for #4. Some of the terminal s have options to remove the decorations as part of their options. But for most terminals it's probably easiest to to get Devil's Pie. This will let you specify some tweaks for how to make things look and where to position them. There's a decent explanation of how to use it on this forum, I think in the HOWTO section. 

For 5 you might take a look to see what's in a hidden folder in your home directory  probably called something like .gdesklet. There's probably some configuration files here. You might be able to edit the size to make it bigger.

---

### Post by kingsidy on 2006-02-08
for the borderless terminal here is the link [http://ubuntuforums.org/showthread.php?t=38938]("http://ubuntuforums.org/showthread.php?t=38938")

---

### Post by nursegirl on 2006-02-08
In terms of 1 and 7, I found it was easier to install gdesklets/adesklets and find nice taskbars, launchers and menus than it was to change the font on the menus.  That doesn't mean it's not possible, but I got frustrated with trying to figure it out and just used the 3rd party solution.

---

### Post by Peter41az on 2006-02-08
you could try, under system settings,appearance, then changing the text color from there. By default it is black but you could make it white.. Not sure if that would work but its only place i know

---

### Post by Perfect Storm on 2006-02-08
[QUOTE=kverde]Just wanted some help on some small tweaks that I'd like to make to improve the look of the desktop.  If anyone has any tips, I'd greatly appreciate it.  

[LIST=1]
[*]If the desktop background is dark, this text is difficult to read.  Is there a way to make it white?
[*]This isn't fully transparent, and I'd like it to launch my own calendar program (web-based).
[*]I want this transparent, too!  Why can't the divider go away or be better with tranparency?
[*]I've seen some ppl's desktops that have terminals with no borders or menus.  they look really cool--how can I get that going?
[*]Sometimes this gdesklet has text that cuts off.
[*]same as 3 - improved transparency
[*]Same as 1 - change font color if possible
[*]Notice the corners -- I know I'm anal, but it doesn't look good to have those white pixels where transparency should be.[/LIST]

Any thoughts?  I'm especially curious about #4 --- the rest are small niggles.

Thanks for any help.[/QUOTE]

3. The theme you are using is not supporting it.
5. the limitation of Gdesklets might improve in the future.
6. See answer 3.

You might get KDE instead if you go for full eye-candy.

---

### Post by audax321 on 2006-02-09
Hey, I looked into your font color issue and came up with a solution you might want. To use it just paste in gedit and save it in /home/username/.gnome2/nautilus-scripts and then access it using the right-click Scripts menu.

Here's the code:

```

#!/bin/sh

# Changes Nautilus/Desktop font color and removes shadow:

ApplyChanges()
{
	zenity --title="Apply?" --question --text="Nautilus must be killed to apply changes. Kill nautilus now?"
	
	if [ "$?" = "0" ]; then
		killall nautilus
	fi
}

GetColor()
{
	alpha=$(zenity --title="Alpha Transparency..." --entry --text="Please enter the level of transparency for the icon container background (0=transparent - 255=opaque; default=0)" --entry-text="0")
	
	if [ "$?" = "0" ]; then
		if [ "$alpha" = "" ]; then
			alpha="0"
		fi

		color=$(zenity --title="HTML Color Code..." --entry --text="Please input the HTML color code for the new font color:" --entry-text="#000000")

		if [ "$?" = "0" ]; then
			if [ "$color" = "" ]; then
				color="#000000"
			fi

			echo -e "style \042desktop-icon\042" > ~/.gtkrc-2.0
			echo -e "{" >> ~/.gtkrc-2.0
			echo -e "  NautilusIconContainer::frame_text = 1" >> ~/.gtkrc-2.0
			echo -e "  text [NORMAL] = \042"$color"\042" >> ~/.gtkrc-2.0
			echo -e "  NautilusIconContainer::normal_alpha = "$alpha"" >> ~/.gtkrc-2.0
			echo -e "}" >> ~/.gtkrc-2.0
			echo -e "class \042GtkWidget\042 style \042desktop-icon\042" >> ~/.gtkrc-2.0
		
			ApplyChanges
		fi	
	fi
}

if [ -f ~/.gtkrc-2.0 ]; then
	zenity --title="Reset?" --question --text="Would you like to reset the font properties (white with shadows)?"

	if [ "$?" = "0" ]; then
		rm ~/.gtkrc-2.0
		ApplyChanges
	else
		GetColor
	fi
else
	GetColor
fi

```

BTW, this will replace your /home/username/.gtkrc-2.0 file if you created your own or something. Otherwise it should do what you need it to. If you make a change and later want to revert to the default, just run the script again and it will ask you if you want to reset to default (which just removes the .grkrc-2.0 file).

---

### Post by kverde on 2006-02-09
Wow.. Thanks for all of the useful replies!

Its getting better.  

audax: That is cool and changed the color of the desktop icons, but I was more concerned with the color of the menu bar (Applications Places System) and the task bar.  But it is cool to be able to tweak the icons, too.  Thanks for the Eterm/Devils Pie thread, that is exactly what I wanted and it works great!  

Artificial Intelligence:  What theme would support that?  I tried many, but none of them seemed any better.

nursegirl: I could install gdesklets, but will windows cover up the gdesklets, or just as bad, will the gdesklets cover the windows?  I like how the task bar is always visible.

Thanks again everyone, I'll post a follow up picture if anyone is curious ...

---

