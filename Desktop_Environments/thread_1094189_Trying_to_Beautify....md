---
title: "Trying to Beautify..."
date: 2009-03-12
forum: Desktop Environments
---

### Post by AICollector on 2009-03-12
I admit it, I'm shallow; I've been trying to make my desktop look quite futuristic. But I'm having a few problems;

I'm using a theme which 'should' provide a neon/glow outline to windows and menus. Apparently, it uses 'ubuntulooks' which I've installed, but dosent seem to be working.

I'm also trying to find a way to make the menus transparent. (Permanatly, not just when I dont have my mouse over them) which is something I've seen many times on GNOME Look.org

The next is even odder, I'm not a big fan of feet and thus I want to change the GNOME logo found on the top-bar menu from a foot onto another icon.

If anyone can provide assistence, I'd be most grateful!

---

### Post by Therion on 2009-03-12
Nothing shallow about wanting to customize your rig.  I might question your *taste* but I won't.

What theme is it you're trying to install exactly?  Link?  So I can see what we're working with.

For transparent menus go to:

System>Preferences>Advanced Desktop Settings>General>Opacity Settings

Add two entries... One for **dropdownmenu** and one for **popupmenu**.

Set the Opacity settings for both to something around, ohhhh, say 250-300 or so depending how much transparency you want.  Adjust to your preference.

As for the Gnome Foot icon... You can change your icon set in System/Appearance using the theme manager "Customize" button.  Click on the Icons tab and change it to something that doesn't use the Gnome Foot.  You can add new Icon sets as well from places like Gnome-look and so forth.  

Adjusting individual icons from within an icon-set is a little more involved.

---

### Post by AICollector on 2009-03-12
Uhh....I dont have 'Advanced Desktop Settings'. I dont even have a 'Desktop Settings'. I'm going to assume you mean the CompizFusion settings manager. Which means I cant do what you suggested. :/



[http://gnome-look.org/content/preview.php?preview=1&id=74813&file1=74813-1.jpg&file2=74813-2.jpg&file3=74813-3.jpg&name=Overglossed](http://gnome-look.org/content/preview.php?preview=1&id=74813&file1=74813-1.jpg&file2=74813-2.jpg&file3=74813-3.jpg&name=Overglossed) are the button

---

### Post by Therion on 2009-03-12
> **AICollector said:**
> Uhh....I dont have 'Advanced Desktop Settings'. I dont even have a 'Desktop Settings'. I'm going to assume you mean the CompizFusion settings manager. Which means I cant do what you suggested. :/
No, I mean Compiz Config Settings Manager.  You don't have that installed so let's fix that right now.

Open Synaptic.  Search on, and install, the **compizconfig-settings-manager** package.  *Voila!*

NOW go to System/Appearance/Advanced Desktop Settings and do as directed.

> **AICollector said:**
> [http://gnome-look.org/content/preview.php?preview=1&id=74813&file1=74813-1.jpg&file2=74813-2.jpg&file3=74813-3.jpg&name=Overglossed](http://gnome-look.org/content/preview.php?preview=1&id=74813&file1=74813-1.jpg&file2=74813-2.jpg&file3=74813-3.jpg&name=Overglossed) are the button
The "glow" effect is provided by the Emerald portion of the theme which you probably did not download or install.  Go back to the download page for the "Overglossed" theme and download the Emerald Theme section.  I don't use Emerald so I can't tell how to install that particular window decoration but someone around here will be able to help you do that.  At any rate, that's why your windows are not "glowing" like in the screenshots.

---

### Post by HammerOfDoubt on 2009-03-12
I wold love to know how to mess around with an icon set as well. There are so many themes in Gnome I would use if I could get rid of that damn foot.

---

### Post by Therion on 2009-03-12
> **HammerOfDoubt said:**
> I wold love to know how to mess around with an icon set as well. There are so many themes in Gnome I would use if I could get rid of that damn foot.
Well fortunately it ain't rocket science.

The easy thing to do is to go to [gnome-look](http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=120x121) and download an icon set you like.  
Save it to your desktop.  
Open the Appearance Manager (System/Preferences/Appearance (don't go any further)).
Drag and Drop the icon file you just downloaded onto the Theme Manager.  
If you're NOT on the Theme tab when you do this, you need to be.
You'll be prompted to apply the new "theme" immediately.  Doing so will, obviously, switch you to the new icon theme.  

Some icon themes use the Gnome foot, some don't... See pics.

---

### Post by Psyphre on 2009-03-12
**Customizing icons:**
when you install an icon set it will be installed to your home folder under .icons (press ctrl+h to show hidden folders)

Just go to that folder then to the icon folder name and all the icons are there for you to fiddle with :)
Most should be png files so easily editable. Keep looking around and there should be the gnome foot icon too.

**Emerald:**
To install emerald do the same as you did to install compiz settings.
or do this:
sudo apt-get install emerald

Then press alt+f2 and type this:
replace --emerald

In your menu>system>preferences you should now see an emerald option.

**@therion:**
Whats the icon set in your first screen shot? The one that has the multicoloured icon for the gnome menu? Looks cool.

---

### Post by AICollector on 2009-03-12
Ahh...emerald...thats troublesome, I've posted elsewhere about my troubles with emerald, the damn thing is slow...

Oh, about the foot; you can take it out but you'll need to edit the theme's files. I'm using hydroxygen, which has some nice instructions on how to customize the theme, but most of the time you'll have to look for the image in 'Places' in the theme's folders.

---

### Post by Therion on 2009-03-13
> **Psyphre said:**
> **@therion:**
Whats the icon set in your first screen shot? The one that has the multicoloured icon for the gnome menu? Looks cool.
Well a simple question calls for a simple answer.  It's called... **Simple**.  Gnome-Look has it:

[http://www.gnome-look.org/content/show.php/Simple?content=99470](http://www.gnome-look.org/content/show.php/Simple?content=99470)

> **AICollector said:**
> Ahh...emerald...thats troublesome, I've posted elsewhere about my troubles with emerald, the damn thing is slow...
Personally I have a deep and abiding Love/Hate relationship with Emerald.  Damn thing had (has?) a nasty habit of wanting to wrest control away from any other window decorator and either make my title bars disappear, or use it's own default window decoration.  About drove me nuts till I purged it out of my system.

---

### Post by Psyphre on 2009-03-13
thx therion.

---

