---
title: "gedit: How to enable column mode?"
date: 2009-01-18
forum: General Help
---

### Post by abcuser on 2009-01-18
Hi,
in Ubuntu 8.10 I would like to enable "column mode". Column mode is selection of block inside each row. This is one of the best features in UltraEdit I have used on Windows XP (see attachment).

How to enable "column mode" in Gedit?

As I looked to the all settings from menus this settings is not available by default.
1. I looked for plugins and found the following plugin web page [http://live.gnome.org/Gedit/Plugins/ColumnMode](http://live.gnome.org/Gedit/Plugins/ColumnMode)
2. I have downloaded columnmode-0.1.1.tar.gz (also tried with columnmode.tar.gz file)
3. Untar the file: tar zxvf columnmode-0.1.1.tar.gz
4. Copy two untared files to ~/.gnome2/gedit/plugins/ directory
5. Start gedit program
6. Edit | Preferences | Plugins and check Column Mode checkbox
7. Now in Edit menu "Column Mode" option is available. So I checked this option and try using column mode by pressing keys <Shift>+<Up> or <Shift>+<Down> or using mouse. None of the features works.

Any idea how to enable column mode in Gedit? If not, do you know for any other text editor in Ubuntu that can edit text via column mode feature? I tried UltraEdit in Wine, but it just works too slow to be useful.

Regards

---

### Post by voxra on 2009-01-24
> **abcuser said:**
> do you know for any other text editor in Ubuntu that can edit text via column mode feature?
I like gedit, but, like you, I very much miss the ability to edit in column mode. Also, for some tasks, gedit is just too basic.

The good news is that Kate has a block mode*, the bad news (as I see it) is that she is very KDE (she would be, of course).

Vox

* Ctrl+Shift+B. You might have Kate installed already, look under "Applications -> Accessories". If not, search for Kate in "System->Administration->Synaptic Package Manager" and install it form there (or even easier;

sudo apt-get install kate ).;)

---

### Post by abcuser on 2009-01-25
Hi,
I have installed Kate and execute Ctrl+Shift+B shortcut to get column mode, but it looks this column mode is not working as it should. Please see attachment. <Tab> characters makes Kate totally disoriented.
Regards

---

### Post by jespdj on 2009-01-25
> **abcuser said:**
> 
1. I looked for plugins and found the following plugin web page [http://live.gnome.org/Gedit/Plugins/ColumnMode](http://live.gnome.org/Gedit/Plugins/ColumnMode)
If you look at the comments on that page, you'll see:
> The plugin is useful as is, but perhaps it does not what is expected. Once in "column-mode" (Alt-C), you can hold SHIFT and move the cursor, but only in vertical. It does not allow to select a rectangular section, but only a "vertical insertion point". Then, all you type is added to several lines at once, at the selected point.
and:
> Sorry for my late reply and thanks for all your interest. I did not expect that some people actually use the plugin because it is unfinished and very buggy. I don't think that I will implement 'real' column mode with block selection in the near future because of lack of time and right now I don't have a good idea how to do it (maybe somebody else has?).
Looks like the original author didn't really intend this plugin to be used by anyone and he is not willing / able to make something that works. :(

---

### Post by gjoellee on 2009-01-25
In gedit? Easy peasy: open gedit then inside Gedit follow this menu Edit->Preferences and you can check Highlight current line.

---

### Post by jespdj on 2009-01-25
> **gjoellee said:**
> In gedit? Easy peasy: open gedit then inside Gedit follow this menu Edit->Preferences and you can check Highlight current line.
That does not enable block selection mode, which is what abcuser is looking for.

---

### Post by abcuser on 2009-01-25
> **gjoellee said:**
> In gedit? Easy peasy: open gedit then inside Gedit follow this menu Edit->Preferences and you can check Highlight current line.
Hi,
this is not "column mode". Please see attached picture in my first post, to see what I think about "column mode".
Regards

---

### Post by abcuser on 2009-01-25
Hi,
I have filed the idea in Brainstorm at: [http://brainstorm.ubuntu.com/idea/17656](http://brainstorm.ubuntu.com/idea/17656)

I hope it will get two approvals (one has already gotten). And then anyone who needs this functionality can vote to make it working.
Regards,
Abcuser

---

### Post by voxra on 2009-01-25
> **abcuser said:**
> <Tab> characters makes Kate totally disoriented.
They do, indeed. If my data was structured as in your second example (the one with tabs), I would paste it into gnumeric*, do whatever I needed to the column(s), then copy/paste it back. Not ideal, but it works.

It would be great if there was a text editor that could handle this, though.

Vox

* or OpenOffice.org's Spreadsheet - but that takes ages to load, unless you've already got an OOo application running

---

### Post by abcuser on 2009-01-25
Hi,
my idea was approved and moved to "Popular ideas".
So please vote for idea at Brainstorm: [http://brainstorm.ubuntu.com/idea/17656](http://brainstorm.ubuntu.com/idea/17656)
It has +1 vote at the moment.
Regards

---

### Post by stupidsing on 2009-03-02
FYI, I found a text editor that features column mode.

[http://madedit.sourceforge.net/](http://madedit.sourceforge.net/)

This is not in repo yet (but has .deb download), is a bit slow, has column mode (alt-2), default appearance is ugly and display settings are tricky, but usable for me.

---

### Post by shadow_code on 2009-03-26
You might be interested in a plugin I made: [Multi-edit]("http://jon-walsh.com/journal/multi-edit/")

It's basically an advanced column edit.

Though selections are still in development.

---

### Post by abcuser on 2009-03-28
shadow_code, thanks I have tested it and it is very promising. I would love to see multi row selection with:
1. use button (or option from menu) to turn on column mode
2. use some kind of key + mouse click to use select multiple lines (example using <alt>+mouse selection or <ctrl>+mouse selection or maybe the best logical one <shift>+mouse selection.

---

### Post by Claus7 on 2009-03-28
Hello,

this is an old discussion. From my humble experience, column mode doesn't work in gedit. Vi(m) on the other hand has this feature.
[http://ubuntuforums.org/showthread.php?t=314526&highlight=column](http://ubuntuforums.org/showthread.php?t=314526&highlight=column)
[http://ubuntuforums.org/showthread.php?t=863977&highlight=column](http://ubuntuforums.org/showthread.php?t=863977&highlight=column)

I had dealt with the issue years ago, so the above threads might be helpful. If someone manages the column mode in gedit I would be glad to know.

Regards!

---

### Post by paxmark1 on 2009-07-07
I used Kate a lot for tables in Dist Proof in past.  I bailed on KDE doing Alpha RC with kde 4.0 on an underpowered machine awhile back, it was not good, I wanted to stay with 3.5.9.  I moved to Gnome and have not looked back (Love K3B still however.)  But to get Kate for Ubuntu is 114 mb.  BTW Konqueror is only 18 mb more.  

However Geany's key bindings do not work for me in Ubuntu for column mode.  I cannot find in the drop down a way to rekey, (they have almost everything else to rekey there.  

Gedit does not have column mode and all the googling yields poor outcomes.  

Nedit is not nirvana for column mode either.

So it is either relearning vim for Gvim or Kate.  Sigh.

---

### Post by mcg130 on 2009-09-24
Column mode is available in the similar nedit editor. Having marked the starting position by clicking the left mouse button, hold down ctrl-shift, then mark the desired block of text.

---

### Post by swdinesh on 2009-11-17
The plugin described in this articole expands the cursor. It isn´t a block selector, but it is only a cursor expander so you can act on the text with a big cursor ( like a multirow cursor). It´s useful but it doesn´t replace a block selection. Gedit unfortunately is too simple so maybe if you install a different editor is a better solution.

bye
Alex

---

### Post by macrules on 2009-12-04
This gives me a deb link for MadEdit , it seems to support column mode (it installs en starts on my 9.10):
[http://sourceforge.net/projects/madedit/files/](http://sourceforge.net/projects/madedit/files/)

Others advise to use this with wine:
[http://www.crimsoneditor.com/](http://www.crimsoneditor.com/)
which has been superseeded by :
[http://www.emeraldeditor.com/](http://www.emeraldeditor.com/) (also for Linux).

Or try a gedit plugin (i did not try the column mode but plugin worked):
[http://jon-walsh.com/journal/multi-edit/](http://jon-walsh.com/journal/multi-edit/)

hope that helps anyone!

---

### Post by jpka on 2010-07-06
> **abcuser said:**
> [http://brainstorm.ubuntu.com/idea/17656](http://brainstorm.ubuntu.com/idea/17656)


+1
really need it.

---

### Post by ionospheric on 2010-07-06
> **jpka said:**
> +1
really need it.

same here.

---

### Post by luigi_mb on 2010-07-06
> **ionospheric said:**
> same here.

SciTE and Nedit are two excellen t editors which support column-mode.

/luigi

---

### Post by u2nTu on 2011-02-12
This is a  must-have feature. Spent a lot of time tinkering with the ColumnMode  plugin for Gedit; success appeared distant. (Thanks to devs of ColumnMode plugin -- it *does* allow vertical lengthening of cursor to simultaneously edit multiple lines, and works well for that. But OP wanted block selection, not the same thing.)

Put more time into researching text editors and came up with jEdit, in  which block selection is native ([www.jedit.org/users-guide/selection.html]("http://www.jedit.org/users-guide/selection.html")), and it's in the repo, "jedit."

So far it's quick and powerful, and has an array of plugins. (New user, but I've already installed Whitespace and BufferTabs.)

jEdit appears to be the best text editor I've ever used. Would like to see at least the block selection feature incorporated into Gedit.

---

### Post by jvdurme on 2011-02-13
Column mode works flawlessly (except block selection) in gedit.

Get the latest plugin ([columnmode-0.1.1.tar.gz]("http://live.gnome.org/Gedit/Plugins/ColumnMode?action=AttachFile&do=view&target=columnmode-0.1.1.tar.gz")) from [http://live.gnome.org/Gedit/Plugins/ColumnMode](http://live.gnome.org/Gedit/Plugins/ColumnMode).
Unzip and apply the patch you can get on the same site.
Then copy the two files to /usr/lib/gedit2/plugins and enable the plugin in gedit.

Then go to Edit > Column mode to activate
Press left-shift and down-arrow at same time to mark the lines for column insert/delete.

Voila.

---

### Post by ThomasNovin on 2011-02-23
Actually there is a better plugin called Multi Edit. Install gedit-plugins and then just enable the plugin. The column-mode plugin is obsolete.

Edit: There was actually two plugins called that, one with a hyphen. This was the one you want.

[http://jon-walsh.com/journal/multi-edit/](http://jon-walsh.com/journal/multi-edit/)

---

### Post by swdinesh on 2011-02-25
I've used the column plug-in in gedit but it's not very user-friendly.
I have to admit that jedit works very well. I changed to it from gedit.

---

### Post by sabajamalian on 2011-10-06
I simply used Geany instead of Gedit .
It has this feature and so many others . . . ;)

---

### Post by macropanther on 2012-11-21
Way late, but valuable, there are two other editors you may wish to examine.

THE (The Hessling Editor) is a copy of VM/CMS Xedit used on IBM mainframes.  It has hundreds of built in functions and supports EASY macroing.

X2 is a text window cousin of SlickEdit (they have common ancestors).  Again, hundreds of builtin functions and almost identical macroing to THE.   www,tangbu.com

For both of these editors, the ease of macro writing is that the macros are written in Rexx (Regina or ooRexx) both also free.  Truthfully, once you use Rexx, you'll laugh at the other scripting languages.  

Wes

---

### Post by nothingspecial on 2012-11-21
Old thread.

Closed.

---

