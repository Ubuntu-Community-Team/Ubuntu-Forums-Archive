---
title: "Gnome menu bar width problem"
date: 2007-03-07
forum: Desktop Environments
---

### Post by xavier_r on 2007-03-07
I dont know why...
But the gnome top panel size is not getting lower than 30 size...( i do not have any bottom panel)
Previoulsy it used to be 23...
Also now  gnome applications have this wider menu bar...

I have tried changing fonts, font-sizes, icon-themes, themes, etc.... but none seem to work

How do i reduce the width of the menu-bar of gnome applications, as well as the gnome panel on the top...

I love ubuntu
Can anyone help plz?

---

### Post by ComplexNumber on 2007-03-07
can you make a screenshot to show what you mean? 

you're using different terminology to what i'm used to. a menu bar is what is shown in the screenshot circled in red.

---

### Post by xavier_r on 2007-03-07
Yes yes that is what I mean by menu bar... the picture you posted

---

### Post by xavier_r on 2007-03-07
This is a sample image of the menubar of terminal...
It has become thicker...
Also note the panel size in panel properties
It cant be reduced below 30

---

### Post by augur80 on 2007-03-07
Try un-checking the "Expand" checkbox.  This tells gnome-panel to make room for all of those icons you have in your panel, which seem to be taking up almost the entire thing.  Also, Gnome may have a failsafe check to make sure you can't make the bar smaller than what the  items in the panel require.  Right now, I'm in the process of reinstalling, so I can't verify this myself.

As to the gnome menu size, that is set in the menu editor, not the panel config.

I'll try to get into Gnome here soon to verify this info, but it will give you some ideas as to where to look for a resolution.

---

### Post by xavier_r on 2007-03-07
I tried unchecking expand that doesnt help...
I created a new  different account and there i can set the panel size below 30(till 23)...
it seems the problem is with my configuration only...

Where is the menu-editor?
I went to 
System->Preferences->Menus and Toolbars
And it doesnt have anything for setting size

I tried looking in gconf-editor for all entries with the name Menu or Panel, and couldnt find any variable for setting size

Do you think the problem might be with some configuration files?
Where is this value of panel size = 30 stored?

---

### Post by ComplexNumber on 2007-03-07
> **xavier_r said:**
> This is a sample image of the menubar of terminal...
It has become thicker...
Also note the panel size in panel properties
It cant be reduced below 30
that doesn't look right at all. i see what you mean. it almost looks like its a theme engine problem. can i assume that you're using the regular Human theme?
i don't think i know the answer other than to adjust the height of the menubar in the gtkrc file....but you shouldn't have to do this.

---

### Post by augur80 on 2007-03-07
> **xavier_r said:**
> This is a sample image of the menubar of terminal...
It has become thicker...
Also note the panel size in panel properties
It cant be reduced below 30

I have no idea on the menubar problem...

In my installation, the panel size can't be brought down below 23.  I don't know why you would need a smaller panel size than that though.

---

### Post by augur80 on 2007-03-07
Here is what my gconf-editor settings are:

[ATTACH]26810[/ATTACH]

Hopefully that helps.

---

### Post by xavier_r on 2007-03-07
Thanks guys for all your help... :)

I just need to know one thing
where is this gtkrc file ?

I think maybe gtkrc settings would have to be tweaked...

---

### Post by xavier_r on 2007-03-07
Hi Guys, Thanks for all your help :popcorn: 

I have resolved the issue now...
From a previous installation of KDE there were some .gtkrc files in my home directory...
And those were interferring...
I renamed those files to something else, so they wouldnt be active in the next session...
Then I restarted my X-Server, and ola... :) (things look much more sleek now)

---

