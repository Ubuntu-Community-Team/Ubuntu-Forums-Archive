---
title: "Need Tweaking For My Fresh KDE S&amp;L Desktop"
date: 2011-03-25
forum: Desktop Environments
---

### Post by GraysonPeddie on 2011-03-25
Hi, everyone. I almost got my freshy-looking desktop setup the way I want for my 50" screen and I need to do some tweaking. One of them is the applications within the Multimedia folder.

[[IMG]http://img853.imageshack.us/img853/2373/kdesnlmultimediaorganiz.th.png[/IMG]](http://img853.imageshack.us/i/kdesnlmultimediaorganiz.png/)

I have organized the Kickoff menu the way I want, but I have removed it because I purely want to get the most out of search and launch, as I like it a lot better than the Kickoff launcher with a white background in it (lock/power button not shown but added it later after the screenshot).

Is there any way to organize the multimedia folder into groups of folders (one for mixers and controllers, audio production, video production, JACK, Utilities, and players, for example).

For window decoration, I am using Win7-bright, but I want to make some touchups but I don't know how. What I want to do is soften the white background to give it more transparency, but maybe not too transparent as to not make it hard for me to read text unless there's a way to make the text glow in the title bar. Last, but not least, I want to squish the close button to make the width equal to that of restore/maximize and minimize buttons. I could go with Win7-Dark but then the title bar is too dark for me, though.

Can my listed theme customization be done in .kde folder within my /home/username folder? I can do some photo editing using GIMP to make the titlebar background more transparent and narrow the width of the close button, but then my question is, where do I find those files at?

---

### Post by ankspo71 on 2011-03-25
Hi,
Just in case you aren't aware of it, hover over any application icon and click on the little star to add them to your S&L panel. They can be removed just as easily.

New categories can be created for your search and launch desktop to suit your needs. You will need to use KDE's start menu editior again, and use it to create a new submenu (be sure it is a top level submenu, not a submenu within a submenu), then add/remove/move application entries around into the newly created submenu, logout then log back in, right click on the desktop, select "Configure Search and Launch", then in the "Main Menu" category, enable your new submenu in the list of available submenus. You can disable any submenus you don't need too. 

The image editing software that should work best for KDE/plasma themes are inkscape and karbon. Unfortunately... that is all I know for now, because the KDE themes are not made from ordinary images, instead they are using *.svg and *.svgz images, and I haven't learned how to edit them yet. Gimp can be used for the rest of the images.

Themes that you installed personally should be located in your hidden .kde folder inside your home menu. The locations that I am aware of are:

/home/yourname/.kde/share/icons/
/home/yourname/.kde/share/apps/desktoptheme/
/home/yourname/.kde/share/apps/color-schemes/
/home/yourname/.kde/share/apps/QtCurve/ 
/home/yourname/.kde/share/apps/aurorae/ 
etc...

System themes can be found in:
/usr/share/icons/
/usr/share/kde4/apps/color-schemes/
/usr/share/kde4/apps/desktoptheme/
etc...

Hope this helps.

---

### Post by GraysonPeddie on 2011-03-25
Then wouldn't it be nice to have submenus within a submenus? Besides, having something like "Audio Production," "Soft Synths," "Audio Effects," "Video Production," "Players," etc. can be a big mess! I'll just keep it the way it is for now.

Thanks for your help. I'll give theming customization a try.

---

### Post by ankspo71 on 2011-03-25
Hi,
This article might help you when you go to edit your theme.

[http://techbase.kde.org/Development/Tutorials/Plasma/Theme](http://techbase.kde.org/Development/Tutorials/Plasma/Theme)

It mentions how to tweak the font colors of the plasma theme too.

---

### Post by ankspo71 on 2011-03-25
> **GraysonPeddie said:**
> Then wouldn't it be nice to have submenus within a submenus?

Yeah I agree, I think it would be nicer to have submenus within submenus too, but those submenus are automatically hidden from view on the S&L desktop, and I think it is designed that way to reduce the number of clicks. Only the top level submenus actually show up on the S&L desktop.

---

### Post by GraysonPeddie on 2011-03-25
Okay. I have one more question and this is concering those who know ins and outs of Inkscape. When I went to edit the elements for the close.svgz and minimize.svgz (I've backed up the two files with "_orig.sgvz"), I've tried to drag the right handle of each element to the left to make the elements looked reversed (am I correct that the width does not matter, since it's vector-based?) but when I relog myself back in, the curves in the close and minimize button have not been reversed.

So with the curves not been reversed, here's how I see it

[list]
[*]The minimize button goes to the left with the left curve in the bottom left corner.
[*]The maximize/restore button stays in the middle, as expected.
[*]The close button goes to the right with the right curve in the bottom right corner of the button.
[/list]

The design of the buttons looked very similar to that of Windows Vista and Windows 7. But I do have my arrangement, as shown here:

[[IMG]http://img546.imageshack.us/img546/332/closemaxmincurve.th.png[/IMG]](http://img546.imageshack.us/i/closemaxmincurve.png/)

Well, this is what I've done:

[[IMG]http://img827.imageshack.us/img827/7225/closebuttonlefthandle.th.png[/IMG]](http://img827.imageshack.us/i/closebuttonlefthandle.png/)

But it seems like non-reversed image stays the same. I don't know what will happen if I skew/rotate the image... Well, I really don't want to mess it up, though. :)

Let me just say that I've been used to Adobe Illustrator when I was in class last semester when I've been tought graphics design (I think it's all about printing/scanning, even though I'm into game development) and that I'm very familiar with GIMP, so when it comes to working with vector-based images, transitioning from Adobe Illustrator to Inkscape is not that easy for me. But I'm not going to purchase it in the future since

---

