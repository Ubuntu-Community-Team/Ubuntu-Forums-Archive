---
title: "icon description"
date: 2007-04-11
forum: Desktop Effects &amp; Customization
---

### Post by BlaineM on 2007-04-11
Just a question...

On dapper I used to be able to remove the description when I mouse over the icons on my panel... I just upgraded to 6.10 and this option will not allow me to change the description to containing no information.

The previous way was to right click and properties, then erase the description.

I dont want a description when I mouse over, just the name of the program.

Is there a way to manually do this? or am I just not being patient in looking for an answer?  I am not opposed to opening a text file and changing things...

thanks,
Blaine

---

### Post by reclusivemonkey on 2007-04-12
There is a "Tool Tips" setting gconf, but the last time I checked, it wasn't honoured.

---

### Post by mcduck on 2007-04-12
just put a empty space (" ") as the description for your panel launchers ;)

---

### Post by BlaineM on 2007-04-12
It wont leave an empty space for the description... thats what I used to do in dapper.  After I delete the comment, and then close the box, it is there again when I mouse over the icon.  Which makes me wonder where the "default" comment is coming from... there has to be a way to change this...

---

### Post by BlaineM on 2007-04-12
I can make a space (as in hitting the space bar) but then it leaves the box bigger once I mouse over the icon... not what I want to do.

---

### Post by reclusivemonkey on 2007-04-12
Well its seems the tooltips setting is honoured on some panels. I have an "OSX" style panel on the bottom of my screen. Unticking the tooltips works for that, but not on the top panel where my window list applet is.

The key name is /apps/panel/global/tooltips_enabled

---

### Post by BlaineM on 2007-04-13
> **reclusivemonkey said:**
> Well its seems the tooltips setting is honoured on some panels. I have an "OSX" style panel on the bottom of my screen. Unticking the tooltips works for that, but not on the top panel where my window list applet is.

The key name is /apps/panel/global/tooltips_enabled

sweet.. that was exactly what I was looking for.  I had forgotten about the configuration editor.

thanks alot... a new thought added to my linux experience.

---

### Post by Hmarroqu on 2007-11-14
how do you open configuration editor?

---

### Post by mcduck on 2007-11-14
> **Hmarroqu said:**
> how do you open configuration editor?

run 'gconf-editor' from a terminal (or hit Alt-F2 and run it from there).

---

### Post by BlaineM on 2007-11-15
I believe that it is also under Applications --> System Tools --> Configuration Editor

I think that in the last release of Ubuntu, it was not available default in the menu, so I had to go under the main menu section, where you choose what is in the menu, and check that I wanted it displayed.

There are various values under each section that when you edit, change the files that they are linked to which control the various options in the OS.  I think it works like an interface to the conf files that control the different programs that make up the OS.  You can use this instead of manually editing text files.  It takes care of that part for you.

---

