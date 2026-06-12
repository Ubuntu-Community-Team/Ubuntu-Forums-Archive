---
title: "Help  disable  ALT+right click"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by Xentric777 on 2007-09-19
If your have a window open (any window) and you hold ALT and right click your mouse, a menu comes up with   Maximize, Minimize, On Top.. etc.   I am hoping someone has an answer on how to disable this.  Going to   system > preferences > windows   and changing the 'movement key' does not help this situation ...   any help would be great    thanks

---

### Post by Sef on 2007-09-19
Try system > preferences > keyboard shortcuts

---

### Post by Xentric777 on 2007-09-19
:( no ... its not in there... either that or mine is somehow setup diff... but there is only keyboard shortcuts in that,  i cant find anything about disabling the ones associated with the keyboad and mouse... i mean there are articles about disabling ALT+left clikc ... but nothing on how to get rid of ALT+right click

---

### Post by Forlong on 2007-09-19
edit: sorry for the double post

---

### Post by Forlong on 2007-09-19
That's a feature of your window manager. If you're on GNOME using Metacity (default WM), you can go to *System &#8594; Preferences &#8594; Windows* and change the "Movement Key" (this will just map it to another combination, of course).

---

### Post by Xentric777 on 2007-09-19
yes... i can change the movement key... however that isnt the same as ALT+right click, chancing the movement key actually doesnt affect ALT+right click at all

---

### Post by Forlong on 2007-09-19
That's not correct. If you change the "Movement Key" to *Control*, there's nothing mapped to [Alt]+[right click] anymore.
It's mapped to [Ctrll]+[right click] then.

---

### Post by Xentric777 on 2007-09-19
well.. i have it set to super or windows key, and still ALT+right click brings up that menu.. but when changing that movment option... its stating that you are changing what key combo you would use if you were going to click and drag a window  wich is ALT+left click... unless of course you have your mouse setup for left hand user  ... ALT+right click does not move window, its just a menu

---

### Post by Forlong on 2007-09-19
Are you sure you're on Metacity? It does exactly what I'm telling you here.

If you change it to Super, can you move the window via [Win]+[left click]?

---

### Post by Xentric777 on 2007-09-19
right, i changed it now to CTRL and now i can  hit   ALT+left click and drag my window around... but when i ALT+right click a menu pops up, the same menu if you click the icon at the very ... left of the title bar of a window ...   minimize   maximize    On top   ect...   its just a small pop-up menu that comes up

---

### Post by Xentric777 on 2007-09-19
sorry edit... i meant now that i changed it to CTRL i can use CTRL+left clikc to drag window around

---

### Post by Forlong on 2007-09-19
> **Xentric777 said:**
> right, i changed it now to CTRL and now i can  hit   ALT+left click and drag my window around...
That's exactly what's wrong here!
If you change it to Control, *everything* will be mapped to [Ctrl] _including_ the menu.

Again: are you using Metacity or not?
In other words: are you using another window manager - other then the one that came with your install of Ubuntu?

Which version of Ubuntu are you running?

---

### Post by Xentric777 on 2007-09-19
any OS i have used has worked in this manner... Linux, windows, mac (with a pc mouse)  the left-click button (usually with index or pointer finger) is used to click a file to highlight it, dbl click to open, or click and drag to drag and drop... the right-click button is used to bring up a menu, for instance right-clicking on a file would bring up a menu with  Open  Cut  Copy  Paste  ect...   this is all of course assuming you are right handed, again if mouse is setup for left hand user this is all reversed

---

### Post by Xentric777 on 2007-09-19
ubuntu 7.04 fiesty ... as far as i know.. i installed linux and that was it... no changes at all like ... how would i check the file manmager?

---

### Post by Forlong on 2007-09-19
OK, now I read your edit. That's weird.

Additionally: are you using desktop effects?

---

### Post by Xentric777 on 2007-09-19
I am using effects, i have them both turned on and its all been runing fine.. i just REALLY hate that menu pop-up .... lemme turn them off a sec

---

### Post by Xentric777 on 2007-09-19
OOO thats unfortunate.. ok yesterday i did try to install that Compiz Fusion although i dont believe thats a file manager... anyway i had trouble and it wouldnt install  so i erased it.. but the CompizConfig menu option has taken over my  'desktop effects' menu option and i am not sure how to enable the old again to get into that menu...    
A note though : this issue with ALT+right click bringing up a menu was happening long before i tried to install Compiz Fusion

---

### Post by Forlong on 2007-09-19
OK, first of all: it's not an issue, it's a feature ;)

Then: desktop effects is using Compiz and that is a window manager.
So you are *not* on Metacity after all. That's why you can't just change this in GNOME's menu.

To configure this in Compiz you would have to open
```
gconf-editor
```
and change it *somewhere* there in /apps/compiz

Unfortunately I don't have the Compiz version of desktop effects installed, so I can't just tell you where this option is.

---

### Post by Forlong on 2007-09-19
Wait... I, think I found it:
**/apps/compiz/general/allscreens/options/window_menu_button**

Try changing that to something else.

---

### Post by Xentric777 on 2007-09-19
that does sound liek what i need... however in my post i was saying ... Compiz kept erroring while i was installing it.. and wouldnot install.. i do hoave SOME of the folders to that file path you listed... but the file is not there... there is nothing in that folder :(

---

### Post by Xentric777 on 2007-09-19
so.. immediately now i am using your thread you heve there to remove everything

---

### Post by Xentric777 on 2007-09-19
UGH!!! lol all this for a "feature" i want to "change" .... in your tutorial it is telling me to check everything for installing compiz... however 1 thing i am clicking is giving me an error now 

Could not mark all packages for installation or upgrade

The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences

compiz-gtk:
  Depends: compiz-core (=1:0.3.6-1ubuntu13) but 1:0.5.2+git20070829-0ubuntu1amaranth1 is to be installed

---

### Post by Forlong on 2007-09-19
I never said in my guide to install compiz-gtk - please follow the tutorial carefully.

---

### Post by Xentric777 on 2007-09-19
OMG LOL just tell me to shut up now... i didnt see tis line in the tutorial     

" The following packages (including dependencies) are the ones we are looking for: "

with it listing what i should check of course.... god.. im in bad shape , i cant even read anymore apparently

---

### Post by Xentric777 on 2007-09-19
Ok i have everything installed now.. works .... however i sitll dont have this path you were having me go to...    /apps/compiz/general/allscreens/options/window_men u_button    no hiddent filed named this.. also i opened up %gconf.xml   and there is no string in there that says  window_men u_button     so... im still at a loss for that

---

### Post by Forlong on 2007-09-19
Go to **System &#8594; Preferences &#8594; CompizConfig Settings Manager &#8594; General Options &#8594; Actions &#8594; General &#8594; Window Menu** and change the **Button** to whatever you like.

---

### Post by Xentric777 on 2007-09-19
OH MY GOD!   IT WORKED  if you double click that window menu option in there, there are 2 settings   "window menu key" (for keyboard) wich by default is set to ALT+space   and "window menu click" (for mouse) wich is set to button 3 (on mine) and removing the button 3 setting was for my right mouse button  so now alt+right click does NOTHING!!!! THANK YOUUUU  FORLONG!!!!!    wow stickin with me to the end amazing, thank you so much, it is unbelievable how happy i am to change that "Feature" ...   you should have like 50 esspresso cups by your name, cause no one on the other forums would touch that question

---

