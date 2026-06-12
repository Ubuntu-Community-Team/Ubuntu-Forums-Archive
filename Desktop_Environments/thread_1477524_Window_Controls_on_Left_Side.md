---
title: "Window Controls on Left Side"
date: 2010-05-08
forum: Desktop Environments
---

### Post by dondiego2 on 2010-05-08
I thought I read this somewhere else in the forum but when I upgraded to Lucid Lynx all my window controls went to the left side including Firefox.  Is there a way to move them back to the right side?

---

### Post by dondiego2 on 2010-05-08
I just went to System>Preferences>Appearance and clicked on a theme that I thought was already loaded and that took care of the problem.  Weird how this release automatically configured it to the left.

---

### Post by 3rdalbum on 2010-05-08
> **dondiego2 said:**
> Weird how this release automatically configured it to the left.

Not weird, it's by design, and it's been well-documented and debated over the last couple of months. I'd recommend you check the site [www.omgubuntu.co.uk](www.omgubuntu.co.uk) every day for the latest news on Ubuntu; that's where I heard about the button shift even before it came down in the updates.

You might want to switch them back over to the left anyway; there's new features coming to the right-hand side in Ubuntu 10.10. It should only take you maybe a week to get used to the left-hand controls, that's how long it took me.

---

### Post by dondiego2 on 2010-05-09
OK.  Now that I have them back over to the right, I can't figure out how to move them back to the left.  I checked System>Preferences>Appearance and all I get is a bunch of themes and I don't want to change the theme.

---

### Post by dondiego2 on 2010-05-09
OK I found it.  This is from another post from STAF0048:

Edit for # 2.  You can use gconf-editor to easily move the buttons to  the "standard" location.  Here's how:

Alt+F2

 	Code:
 	gconf-editor 
On the left hand side go to apps, metacity, general.  On the right  hand window find "button_layout."  Right click that and choose "Edit  Key"

copy and paste this in the highlighted field:

 	Code:
 	menu:minimize,maximize,close 
I changed the above to:

[B]menu, minimize, maximize, close:
[/B]
and it moved them back to the left side.

---

### Post by Mitchell Hale on 2010-05-09
[Ubuntu Tweak]("http://ubuntu-tweak.com/") has options to move window buttons.
You can configure them however you want, here's mine

left- minimize, maximize
right- menu, close

---

### Post by howefield on 2010-05-09
> **dondiego2 said:**
> OK I found it.  This is from another post from STAF0048:

Best way is to follow the sticky in the General Help forum. Extract from the posting by philinux...

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

> Minimize, Maximize and Close button placement.
A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.
[[Update ]http://www.markshuttleworth.com/archives/333

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.
Using gconf-editor is not the right approach as this could bork future themes. This change makes it easier for themes to do interesting things with window borders. Unfortunately, if the wrong approach spreads, they won't be able to do that.

---

### Post by dondiego2 on 2010-05-10
> **Mitchell Hale said:**
> [Ubuntu Tweak]("http://ubuntu-tweak.com/") has options to move window buttons.
You can configure them however you want, here's mine

left- minimize, maximize
right- menu, close


Thanks.  I downloaded and installed it.

---

### Post by blizok on 2010-07-17
> **dondiego2 said:**
> OK I found it.  This is from another post from STAF0048:

Edit for # 2.  You can use gconf-editor to easily move the buttons to  the "standard" location.  Here's how:

Alt+F2

 	Code:
 	gconf-editor 
On the left hand side go to apps, metacity, general.  On the right  hand window find "button_layout."  Right click that and choose "Edit  Key"

copy and paste this in the highlighted field:

 	Code:
 	menu:minimize,maximize,close 
I changed the above to:

[B]menu, minimize, maximize, close:
[/B]
and it moved them back to the left side.
Thanx dondiego2, it works!

---

### Post by psfal on 2010-12-17
> **howefield said:**
> Best way is to follow the sticky in the General Help forum. Extract from the posting by philinux...

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)
Thank you so much, in earlier releases I could where to change the location of the buttons, but I just upgraded to 10.10 and it's all gui interfaced, my buttons are back where I like them:-)

---

