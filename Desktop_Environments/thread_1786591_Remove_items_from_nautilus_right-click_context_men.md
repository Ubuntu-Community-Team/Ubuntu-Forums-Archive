---
title: "Remove items from nautilus right-click context menu?"
date: 2011-06-19
forum: Desktop Environments
---

### Post by tribble222 on 2011-06-19
I uninstalled xmms player quite a long time ago. I think when I had hardy heron. Currently I'm on 10.04. When I right click a .mp3 file I still have the option to play with xmms player showing up. Even if I choose an "other application" the xmms player option remains stickied to the top.

Does anyone know how I can remove this entry? I did a lot of searching but couldn't find a solution. 

Thanks!

---

### Post by jerrrys on 2011-06-20
you just did your searching in the wrong place.  **gksudo nautilus** and do a search for **xmms**.  then just delete the left-over files.  be careful what you do while in sudo

---

### Post by tribble222 on 2011-06-20
Wow that was really simple, thanks so much!

---

### Post by jayboe on 2011-11-28
UBUNTU 10.04 / FEDORA 13
I know it's a little late in the game, but this is a thread that I came across during my search for "How to".
Forget nautilus-actions for customizing built in menu selections. Works great for creating new ones though.
Ok, so here it is,
You're gonna have to get a little dirty in a .xml file

First  things first. If you're gonna make changes to a system file it is  best  to make a backup of the file before you get started, and you must  be  root. I like to work from the directory where the project is so  let's  get started by changing to that directory.

[COLOR=DarkRed]cd /usr/share/nautilus/ui[/COLOR]

Now let's get to work.

[COLOR=DarkRed] sudo cp nautilus-directory-view-ui.xml nautilus-directory-view-ui.xml.bak[/COLOR]

Now use your editor of choice e.g. (vi,nano, or a gui like gedit) Me, I like nano to do my bidding. :wink:

[COLOR=DarkRed]nano nautilus-directory-view-ui.xml[/COLOR]

Here  is a sample block of xml code from my system after the adjustment.  I  figure the easiest way to edit the file without deleting anything  like I  read in another post is to simply comment out the crap that you  don't  want.
Comments in xml must be preceded by <!-- and ended with -->
With  that being said take notice at the beginning and end of this block   where I placed the comment indicators. On this block I started at the   "placeholder" and ended on the "placeholder", but it is not limited to  commenting there. You can pick and choose "menuitem", too. By doing  it  this way with the comments it is also easy to just go back and   un-comment what you commented to undo changes verses the .bak approach   mentioned above which is more secure.

...............<!--placeholder name="Clipboard Actions">
........................<menuitem name="Cut" action="
........................<menuitem name="Copy" action="Copy"/>
........................<menuitem name="Paste" action="Paste"/>
................</placeholder-->
.................<!--placeholder name="Select Items">
.................<menuitem name="Select All" action="Select All"/>
.................<menuitem name="Select Pattern" action="Select Pattern"/>
.................<menuitem name="Invert Selection" action="Invert Selection"/>
.................</placeholder-->
................<placeholder name="File Items Placeholder">
........................<!--menuitem name="Duplicate" action="Duplicate"/-->
........................<!--menuitem name="Create Link" action="Create Link"/-->
........................<menuitem name="Rename" action="Rename"/>
........................<!--menu action="CopyToMenu">
................................<menuitem name="Copy to next pane" action="Copy to next pane"/>
................................<menuitem name="Copy to Home" action="Copy to Home"/>
................................<menuitem name="Copy to Desktop" action="Copy to Desktop"/>
........................</menu>
........................<menu action="MoveToMenu">
................................<menuitem name="Move to next pane" action="Move to next pane"/>
................................<menuitem name="Copy to Home" action="Move to Home"/>
................................<menuitem name="Copy to Desktop" action="Move to Desktop"/>
.........................</menu-->
....................</placeholder>
.................<!--placeholder name="Dangerous File Items Placeholder">
........................<menuitem name="Trash" action="Trash"/>
........................<menuitem name="Delete" action="Delete"/>
........................<menuitem name="Restore From Trash" action="Restore From Trash"/>
....................</placeholder-->

Run this command to restart nautilus if you feel so inclined.

[COLOR=DarkRed]nautilus -q[/COLOR]

COMMAND SUMMARY

[COLOR=DarkRed]cd /usr/share/nautilus/ui
sudo cp nautilus-directory-view-ui.xml nautilus-directory-view-ui.xml.bak
nano nautilus-directory-view-ui.xml
nautilus -q[/COLOR]

So,  now if you make a boo-boo, you can always run this next set of   commands  from within the /usr/share/nautilus/ui directory and then   start the  process over. That is assuming you went with the file backup.

[COLOR=DarkRed]rm -rf nautilus-directory-view-ui.xml
mv nautilus-directory-view-ui.xml.bak nautilus-directory-view-ui.xml[/COLOR]

To add custom commands back to the context menus, you can install;

[COLOR=DarkRed]apt-get install nautilus-actions[/COLOR]        via ubuntu
[COLOR=DarkRed]yum install nautilus-actions[/COLOR]            via fedora

Here is a link to nautilus-actions website tutorials. ENJOY! :wink:
[http://www.grumz.net/?q=taxonomy/ter...7e4d8147c0e42c]("http://www.grumz.net/?q=taxonomy/term/10/9&PHPSESSID=68a818f0046eed50167e4d8147c0e42c")

---

### Post by mc-rpg on 2011-12-03
I can't thank you enough!

I love how everything on linux has a configuration file that you can simply mess around with to configure things :D

---

