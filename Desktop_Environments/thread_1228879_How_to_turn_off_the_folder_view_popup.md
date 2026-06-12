---
title: "How to turn off the folder view popup?"
date: 2009-08-01
forum: Desktop Environments
---

### Post by t.rei on 2009-08-01
Hi,

I am just getting used to the many many nice features of kde4, and slowly but inevitably the "browse folder" popup of the folder view plasmoid is driving me nuts!

I can't seem to find any option in the configuration to either:

a) Set the delay until it comes up to something around 2-5 Sekonds 
So I can click on my home folder to get a dolphin without having to wait fot the popup to disappear to start working again. This is necessary to go into hidden folders and such. 

b) just turn it off completely.
It might be handy every now and then, but on the long run its just not worth the hassle to me.

Has anyone got any pointers (not the c ones!)?

thanks.

---

### Post by t.rei on 2009-08-07
It seems this can't be done. Too bad, this "feature" is getting in my way more than it helps. 

Making the folder view close to unsuable for drag-n-drop work. :(

---

### Post by Zorael on 2009-08-08
I managed to disable this (fairly easily) in the source, but I haven't figured out how to single out the widget and upload it to my ppa without uploading the entirety of KDE 4.3's kdebase.

```
diff --git a/apps/plasma/applets/folderview/iconview.orig b/apps/plasma/applets/folderview/iconview.cpp
index 87e598b..07cca40 100644
--- a/apps/plasma/applets/folderview/iconview.orig
+++ b/apps/plasma/applets/folderview/iconview.cpp
@@ -1293,11 +1293,12 @@ void IconView::focusOutEvent(QFocusEvent *event)
 
 void IconView::triggerToolTip(ToolTipType type)
 {
-    if (type == FolderTip && m_hoveredIndex.isValid()) {
-        if (!m_popupView || m_hoveredIndex != m_popupIndex) {
-            m_toolTipShowTimer.start(500, this);
-        }
-    } else {
+    // Disabling folder popup
+    // if (type == FolderTip && m_hoveredIndex.isValid()) {
+    //    if (!m_popupView || m_hoveredIndex != m_popupIndex) {
+    //        m_toolTipShowTimer.start(500, this);
+    //    }
+    //} else {
         // Close the popup view if one is open
         m_toolTipShowTimer.stop();
         m_popupCausedWidget = 0;
@@ -1311,7 +1312,7 @@ void IconView::triggerToolTip(ToolTipType type)
         } else {
             m_toolTipWidget->updateToolTip(QModelIndex(), QRect());
         }
-    }
+    //}
 }
 
 // Updates the tooltip for the hovered index
```
It's those damn cmake files, I don't even know where to begin. It's possible to just make a deb with the binary .so file, I guess.

---

### Post by t.rei on 2009-08-09
Ah. Very good. "Use the source, luke!"

Ok, do you know how to go about doing a toggle for this (so the author might actually use it?) 
Maybe a simple Option in the configure folder view dialog "Disable Popup Browsing". Something along the lines.

Oh well, maybe I find it myself... can't be THAT well hidden. ;)

Thanks.

---

### Post by t.rei on 2009-08-28
Ok, so I have changed the lines you mentioned. Still the annoying popups. I changed some more lines... it's just not going away. 

I guess I'll leave it to the pro's and hope desperatly for a toggle. This makes folderview a pain in the ***, if you know what I mean. ;)

---

### Post by Zorael on 2009-08-29
Huh, I managed to get mine to go away. ;/

I actually managed to get a deb and a source deb to build, but at some point during the process of trying to get it all to build on launchpad I deleted them.

I'll try to rebuild them as soon as I have access to that machine.

---

### Post by t.rei on 2009-08-30
That would be awesome!

I seriously don't see what I am doing wrong. I manually edited the posted diff into the file (that part of the sources seem to be 100% identical, still) and ran cmake and checkinstall. No errors, everything installed without any trouble.

logged out and back in - still popups.
reboot (welcome windows?) - still popups.

It's sad, as this is really getting in my way of using the desktop - well the folderview - efficiently.

---

### Post by DrCrispPacket on 2009-09-27
You guys are lucky - I can't even get a FolderView widget to appear. 

Kubuntu on Mythbuntu 9.04, supposed to be KDE4.2.2; right click on desktop -> Appearance Settings -> Desktop Activity gives only one item on drop-down for Type: this is Desktop (ie no FolderView). 

Right click on desktop -> add widget: list of widgets available does not contain FolderView. 

Am I doing something wrong, or is KDE misconfigured, or can I get the appropriate file from somewhere?

---

### Post by t.rei on 2009-09-28
Hm, strange. 

What you should be able to do is: Drag and Drop any Folder on your desktop. You should then be asked wether you want to create a link or a folder-view item.

Try that - if it does not work you might want to check if all of kubuntu is installed that is required (just rerun "sudo apt-get install --reinstall kubuntu-desktop" in a terminal and see what it says.

I am currently back to gnome, as this and some other issues on KDE were very disruptive during my working time. But I keep checking if there is an option available.

---

### Post by DrCrispPacket on 2009-09-29
Thank you - the --reinstall worked. There were a lot of packages not previously installed: mythubuntu by default evidently only installs a subset of the KDE desktop when you ask it to create a kubuntu desktop.

---

### Post by t.rei on 2009-09-29
Glad it helped.

On the topic on this thread:

Someone started a wishlist item on the kde-bugzilla: Please upvote it! 
[https://bugs.kde.org/show_bug.cgi?id=192821](https://bugs.kde.org/show_bug.cgi?id=192821)

Thanks

---

### Post by Gen2ly on 2009-09-29
Voted.  Appreciate the heads up.  Wondering if this was getting in the way of anybody else.

---

### Post by t.rei on 2009-10-05
I really hope this gets implemented soon(ish). I want my Desktop to do stuff if I tell it to, and not quess what I might want to be doing.

---

### Post by t.rei on 2009-10-10
Another big upgrade, another day of this not being fixed. 

This is really really getting annoying - the amount of "you cannot drop a folder on itself" messages I have to cancel is rediculous. I have less popup dialogues running windows7! 

The folderview Idea is wonderfull! Too bad this 'feature' that is forced on us makes it such a pain to actually use. :(

---

### Post by t.rei on 2009-10-15
Ok, here is what I have done and because it was driving me NUTS:

```
apt-get source kdebase
cd kdebase-4.3.2
vim apps/plasma/applets/folderview/iconview.cpp
```I edited the following lines (inspired by Zorael):
1297+
```
//    if (!m_popupView || m_hoveredIndex != m_popupIndex) {
//        m_toolTipShowTimer.start(500, this);
 //    }
...
```1338+
```
if (item.isDir()) {
   //type = IconView::FolderTip;
   return;
} else if (item.isDesktopFile()) {
...
```then ran:
```
mkdir kdebase
cd kdebase
cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
make -j 2
sudo make install
```

Then restarted plasma (krunner: killall plasma-desktop and restarting doing plasma-desktop as kbuildsycoca4 wasn't sufficient)

Now it is working - I think - until the next upgrade. I hope that the next dist-upgrade won't give me hell. ;)

---

### Post by GeneralZod on 2009-10-15
I'll see if I can track down fredrikh.  Failing that, I'll ask on the Plasma mailing list whether this is a WONTFIX or not and offer to write a proper patch - hopefully with a GUI option, but with a hidden config option otherwise.

No timescale on this, though: I'm hugely busy at the moment.  If someone else wants to try and beat me to it, be my guest ;)

---

### Post by Gen2ly on 2009-10-16
Lol, figured an end would come to this :).  Yeah, this behavior definitely can be intruding at times.  I'd patch this myself but figure the next update would byonk it.  Hopefully a developer can get some time and be able to do something.

---

### Post by GeneralZod on 2009-10-16
Oh, a quick update: I raised the issue briefly with aseigo and fredrikh on IRC, and they both seemed open to the idea, including offering a GUI option.  The actual details of UI and implementation need to be hammered out on the mailing lists, though.

One interesting proposal was to not have the folder open on hover by default (but provide an option in the Advanced section to re-enable this) and instead to have a "item action" (like the selection dealie in Dolphin, used to select items in single-click-to-open mode) that opens the folder when clicked, instead.

---

### Post by t.rei on 2009-10-16
Yes, that sounds like a valid option, but keep KIS in mind. After all it could get messy if this "clickable thingy on hover action" gets out of hand. I'm shure you can imagine what I am talking about. 
 
And not to forget one thing: there already is a "One click to show the folder contents" option in kde - "open in dolphin".  I am not quite shure if there are colliding interests in "simple" and "anything is possible".  I like to have things configurable, and am used to have everything available as an option in kde. 
 
I'm still in favor of an option to turn the folderview popup off completely. Because it unclutters the workflow of moving and sorting files on the desktop. But still some might like it. 
 
One thing I noticed: when hovering over a file - like a txt - the tooltop is show below the file. 
When hovering over a folder having the folder-preview-popup (what IS this called?) enabled - the tooltop covers most of the folder-icon, thus obstructing access. 
 
I am not shure if it would be less disturbing if the folder-preview-popup-thingy would also be completely below the folder it represents?

---

### Post by Gen2ly on 2009-10-19
> **GeneralZod said:**
> Oh, a quick update: I raised the issue briefly with aseigo and fredrikh on IRC, and they both seemed open to the idea, including offering a GUI option.  The actual details of UI and implementation need to be hammered out on the mailing lists, though.

One interesting proposal was to not have the folder open on hover by default (but provide an option in the Advanced section to re-enable this) and instead to have a "item action" (like the selection dealie in Dolphin, used to select items in single-click-to-open mode) that opens the folder when clicked, instead.

Hey that's good news.  I thought it was a cool feature at first, just like the devs probably did too.  Then it becomes, I can't get to my f!@#$'n folder.  :)  I also find it disturbing in the System Settings panel too - clicking on a control panel then the back button is rough.  Been thinking if the hover effects default was off, maybe like a middle-click of the file/folder would open addtional information/subdirectories.  I think that could be pretty useful.

---

### Post by t.rei on 2009-10-19
One more 'Inconsistency' about the interactiveness of popup-tooltips I found:
When hovering the mouse on the desktop-switcher applet a list of all open windows on that desktop is shown. Yet - when you instinctively want to click an item in the list it turns out to be a purely informational popup. So, I am already getting incoherent "conditioning" when using my kde desktop. *g*

But at least the steps I posted removed the folder-view-popup for me, and if you find it hard to believe: try it. It actually makes a huge difference when using the desktop. :) 

This sort of feature should be optional. I am shure there are those out there who actually like, use, maybe even love this little gimmik.

---

### Post by t.rei on 2009-11-05
[http://ubuntuforums.org/showpost.php?p=8109195&postcount=15](http://ubuntuforums.org/showpost.php?p=8109195&postcount=15)

Just wanted to report this as still being a working solution on kdebase-4.3.3-0ubuntu1~ppa1.

---

### Post by Gen2ly on 2009-12-05
Just read this [article](http://www.harshj.com/2009/11/18/kde-4-4-desktop-an-early-preview/), and it looks like a 'folder-preview' option hasn't made it into 4.4.

A tear. :(

---

### Post by t.rei on 2009-12-06
Hm, too bad. So I'll keep on dirty-patching my kdebase until it gets a proper option.

thanks for the heads up.

---

### Post by GIdervish on 2010-03-15
Thanks for posting the workaround t.rei, it works great, and definitely a big relief to get rid of that popup. I assumed I just couldn't find the option in system settings, as you'd expect it to be there for such a potentially annoying feature.

---

