---
title: "Mac OSX bar"
date: 2005-08-16
forum: Desktop Environments
---

### Post by speedemonV12 on 2005-08-16
Hey guys, i am looking for a bar that is like the mac os x bar for gnome...something that is easily configured....you know, somehting like Y'z bar  for windows ....thanks

speedy

---

### Post by pixelnate on 2005-08-16
I would also like to know if there is anything that will allow you to view your file tree like the column view in OSX.

And also, are there anything like Dashboard widgets in Gnome?
Thx.

---

### Post by danns on 2005-08-16
[QUOTE=speedemonV12]Hey guys, i am looking for a bar that is like the mac os x bar for gnome...something that is easily configured....you know, somehting like Y'z bar  for windows ....thanks

speedy[/QUOTE]

What about gdesklets:  [http://gdesklets.gnomedesktop.org?](http://gdesklets.gnomedesktop.org?)  It's only a synaptic/apt-get away.

---

### Post by varunus on 2005-08-16
> I would also like to know if there is anything that will allow you to view your file tree like the column view in OSX. 

I don't think so...

> Hey guys, i am looking for a bar that is like the mac os x bar for gnome...something that is easily configured....you know, somehting like Y'z bar for windows ....thanks 

One solution is Engage, you can get it from the enlightenment17 repository...search the forum for "smoon" "enlightenment".  Add that repository to synaptic and try installing "engage"...

But engage is hard to configure.  Check below for an easier (but not as powerful) method...

> And also, are there anything like Dashboard widgets in Gnome? 

Yes and yes.  Both questions are answered with gdesklets (very similar to dashboard...in fact, they existed before dashboard...hmm.... ;-) )

You can install gdesklets from synaptic, its the "gdesklets" package.  Though there has been talk in the backports forum to get the newest version, which is much better, in Ubuntu...so you may want to go check that thread.  (Search for it.)

DO NOT install gdesklets-data; if you check the version numbers, you'll see that the data package is old.  And it is.  It doesn't work too well...instead get any desklets you want from here: [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

If you want a MacOS like Dock, you'll want the "starterbar" desklet.  Unfortunately, it doesn't work as a taskbar, just a launcher.  Engage, however, works as both a taskbar and a launcher ala macosX.  (But you need to configure it with text files...)

---

### Post by speedemonV12 on 2005-08-16
So you think that starter bar for gdesklets would be the best?

best i mean...easy to configure?

---

### Post by varunus on 2005-08-16
Yes, its menu-based and drag-and-drop to configure.

But it won't work as a taskbar, just as a launcher.  Engage can also show what programs are open with the little black arrow like MacOS does...

---

### Post by speedemonV12 on 2005-08-16
Okay, all i wanted was a launch bar...so do you know how you can change the background, or make it transparent?

---

### Post by varunus on 2005-08-16
Yep, in the starterbar, you can right click and choose "properties" or "preferences" (one of those) can change transparency or background image for the starterbar.

---

### Post by mcduck on 2005-08-16
I made my launch bar the easy way: First I moved everything from gnome's bottom panel to top panel. Then I opened bottom panes properties, unchecked 'Expand, resized the panel to 48px (feel free to choose your own size ;), and just dragged all shortcuts I wanted to that new panel. Then I moved it to the middle of screen bottom, and it even snapped there automaticly.

Next I set it to autohide, so it wont limit windows, and then i checked 'Show hide buttons' and unchecked 'Arrows on hide buttons', just because it looks better now :)

Then I set it transparent, and adjusted the autohide timing from Applications/System Tools/Configuration Editor/apps/Panel/Global.

No need for installing anything, and I can just drag there all shortcuts or panel applets I want.

---

### Post by speedemonV12 on 2005-08-16
ya ive done that before...but i dont like the hidding of it....can anyone tell me how to make the background transparent with starter bar?

---

### Post by SSTwinrova on 2005-08-16
[QUOTE=varunus]Yep, in the starterbar, you can right click and choose "properties" or "preferences" (one of those) can change transparency or background image for the starterbar.[/QUOTE]

Did that solution not work for you?

---

### Post by Chareos on 2005-08-17
[QUOTE=SSTwinrova]Did that solution not work for you?[/QUOTE]
 I'll try KXDocker instead. You can find it on kde-apps.org
I think that could be excellent, with launcher and taskbar.

Also, I think that's an application, not a desktop widget,  so similar to yz'dock.

Maybe it also have abilities to popup in front of other wondows  and auto-hide, features missing in starterbar.

---

### Post by speedemonV12 on 2005-08-17
No that solution did not work...when i right cllick on it...the option i have is configure desklet...then i do...and there are a background and foreground options..but i cant figure out how to get transparent



and the kxdocker i thought was only for kde....

---

### Post by rama on 2005-08-17
[QUOTE=varunus]One solution is Engage, you can get it from the enlightenment17 repository...search the forum for "smoon" "enlightenment".  Add that repository to synaptic and try installing "engage"...[/QUOTE]

Im using Gnome/metacity. Can I use engage with those? 
If that is a "yes" ... What's the repository I should add to find engage with synaptic?

---

### Post by speedemonV12 on 2005-08-17
Yes you can do that....i was just looking at it a minute ago...you can search the forums..i think the is a how to..on it...but it can be done....and it is smoon's repository...search for that and you will find the right one...then just apt-get install engage


P.S.  do you know how to make starter bar transparent?

---

### Post by rama on 2005-08-17
[QUOTE=speedemonV12]P.S.  do you know how to make starter bar transparent?[/QUOTE]

Kind of yes ... but I 'm at work right now (Win 2k). I 'll get back to you from home with my settings. It's not 100% transparent though.

---

### Post by speedemonV12 on 2005-08-17
But there has got to be a  way grrrrr.....

---

### Post by rama on 2005-08-18
Finally looked at it ... well hm... I guess I cant really help you. Mine is semi transparent by default. Sorry.

Im currently experimenting with engage ... what a mess!!!

---

### Post by speedemonV12 on 2005-08-18
Yes i have tried out engage and it is very hard to configure...the starterbar is just fine...but i just wanted to make thebackground transparent

---

### Post by rejser on 2005-08-30
[QUOTE=pixelnate]I would also like to know if there is anything that will allow you to view your file tree like the column view in OSX.

And also, are there anything like Dashboard widgets in Gnome?
Thx.[/QUOTE]
in gconf-editor
apps- > nautilus -> sidebar_panels --> 
uncheck show only directories

then you will see all files in tree view in the left sidepanel
I've pulled the left side-panel to take upp the entire window-space so it looks like it is the only window in nautilus

---

### Post by Chareos on 2005-09-15
If anyone still interested, now kxdocker works on gnome too

---

### Post by bionnaki on 2005-09-15
I dont see KXDocker in synaptic.

---

### Post by Eversmann on 2005-10-12
Anyone installed it on gnome? i tried but i quickly got lost on the packages i have to install.

Anyone how installed could give us some clues?

Thanks in advance ;-)

---

