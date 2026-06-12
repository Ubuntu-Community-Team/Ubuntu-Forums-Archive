---
title: "Working with pictures in GNOME Nautilus drives me crazy... Any solutions?"
date: 2010-07-22
forum: Desktop Environments
---

### Post by KonfuseKitty on 2010-07-22
I have a folder with over 1000 images and I'm finding it difficult to use with Nautilus, there are problems:

* When I click on the folder bookmark in the side pane to quickly open that folder, the focus remains on the side bar: pressing PageUp or PageDown to scroll the folder serves only to highlight icons in the side bar.  Is there any way of setting it so that on opening of a folder from the side pane, focus is moved to the folder contents?

* When I open the folder for the first time during a session, I can't do anything with it until it has finished updating the previews, which takes a long time.  There seems to be no 'interrupt', and no caching of previews across sessions.  Has anyone found a solution?

* Even though the preference setting to show folders first in the list of contents is not ticked, when the previews are done, the contents of the folder are always scrolled down to where it contains a folder.  There seems no way of having it scrolled to the top of the list.  What can I do to stop it scrolling down to the first folder?

* Is there some way of having a folder that was open at the end of a session also open at the start of a new session, across a restart?  I would like to have my pictures folder always open.  Can this be done on Ubuntu?

Whatever help you can offer will be greatly appreciated. :)

---

### Post by gordintoronto on 2010-07-22
In Nautilus, you can Edit/Preferences, select the Preview tab, you can change the "only for files smaller than" to speed up the folder display.

---

### Post by KonfuseKitty on 2010-07-22
I need the previews to identify files, so turning them off isn't a solution.  I wonder if another desktop environment would handle this better than GNOME?

---

### Post by WinRiddance on 2010-07-22
I really don't understand what your problem is ... unless perhaps it has something to do with the permissions that you may or may not have in order to view the contents in a folder? I work with the Ubuntu file manager (Nautilus) just as intensely as I did with Windows file manager and find this one to be easier, faster, and better.

Assuming that you have full administrative privileges, you should be able to open Nautilus without changing anything at all in the preferences, with exception to single click behavior if that's what you want, and the ability to view hidden files if that's what you need.

When you click on a folder **bookmark on the lower left side** of your Nautilus screen, this should display the contents of that folder in the right side. You can also adjust those panes for yourself or just maximize the entire Nautilus window to see more contents.

**By default, all standard pictures already show up as viewable thumbnail images.** Again, this is default behavior so if that's not working for you then you've either changed a setting or you don't have access privileges to view the contents of that folder. If you do see the contents with images but the images aren't viewable enough for you, then simply click on the plus/minus zoom symbol at the top of Nautilus _to increase or decease the view size of the contents_ that you're looking at.

Now there is one more default setting which prevents the "picture symbol view" on any files larger than 10 MB. So if you have some insanely large images which are larger than 10 MB then you won't be able to see those in the preview mode at all ... unless you change that setting under preferences ... **which may at the same time slow down your system** since you'll now be using more system resources to view substantially larger images and files.

I hope this helps. :D
I think Nautilus is perfect in every way, at least for me and I work with it daily.

---

### Post by KonfuseKitty on 2010-07-22
WinRiddance, maybe I should have been clearer: I have Preferences set to show previews for files under 1Gb, which will cover all sizes of files I might have by a wide margin.  However, in the folder I'm talking about, most files are under 10Mb, while a handful are larger, none more than 30Mb.

Now, yes, there is a correlation between file size and drawing of previews, made worse by the fact that the drawing is not very effectively computed.  I've run System Monitor and I get an average load of about 30% on my 4 core CPU, with one core being at the high end of the range, the other three near idle.  So there's a performance issue with the previews, but this wasn't so much the subject of my post.

With that out of the way, please re-read my first post and you might be able to help.  Though if Nautilus is perfect for you, I won't hold a grudge if it turns out you can't help. ;)

To sum it up, my problem is where the focus is after clicking on a bookmark in the side pane, and the fact that previews are re-drawn every session.  Like I said, please read the original post.

Still looking forward to solutions.... please keep them coming. :)

---

### Post by PhilGil on 2010-07-22
I'm not knowledgeable enough about Nautilus thumbnails to help you with your immediate problem, but perhaps you should consider sidestepping it by using a photo browser/manager. 
 
Most photo managers have persistent thumbnails, some can remember the folder you were browsing on restart and it's easy to set a program to auto-load on boot. 
 
There are numerous photo organizer/managers available in the repos, a few that come to mind are: F-Spot, Shotwell, Geeqie (formerly gqView), Picasa, Gwenview (for KDE) and DigiKam (also for KDE).

---

### Post by KonfuseKitty on 2010-07-22
The problem with dedicated photo applications is that they aren't Nautilus... I mean, when a file is saved to the folder, Nautilus immediately displays it whereas photo programs use Import functionality of some sort.  In general, I have found photo cataloguing/managing software to be a middle-man I don't need, I have always preferred to use my desktop as my photo asset manager and database.  This worked very well on the Mac, the Finder window was useable even while the previews were being re-drawn.

Now that I've switched to Linux, I've gone even further with this approach, I've given up on using dedicated RAW converters.  I do it in Nautilus, with a script run with Nautilus-Actions, using dcraw, ImageMagick and GraphicsMagick commands to do the conversion.  So now after having set this up very successfully, and having validated my approach, I'm not really keen to give it up and go to using photo software.  I guess I'm a bit biased as well, my attitude is if it worked on the Mac, why shouldn't it work on Linux.

Besides all that, I think at least some of my concerns are of a more general nature and applicable overall, not just to photo management.  Like the focus issue with clicking in the side pane, for instance.

Any other ideas? :)

---

### Post by dtzortzis on 2012-08-09
I have the same issue. Any chance you have set the default Pictures folder to be another folder in your home folder other than ~/Pictures?
eg. I have set ~/Dropbox/Pictures to be my default Pictures folder for Ubuntu.

I think that's an issue. Let me know...

---

### Post by coffeecat on 2012-08-09
Old thread closed.

---

