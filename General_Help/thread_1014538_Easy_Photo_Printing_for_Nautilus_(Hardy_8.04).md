---
title: "Easy Photo Printing for Nautilus (Hardy 8.04)"
date: 2008-12-17
forum: General Help
---

### Post by judasg0at on 2008-12-17
**Hello all,**

I wanted to set up a simple interface for printing multiple pictures in ubuntu, something similar to what windows has when you right click on an image and can select print and then add and change the orientation of the images. I set it up and thought I would place my findings here.


**Special Note:**
I decided to write this because my wife had to print some pictures and we had to boot into Vista (cringe) in order to print multiple (different) pictures at the same time. Try searching on this topic for hardy, its a pain in the butt!

**Instructions:**
All that is needed is already available for Hardy, we will need to install PhotoPrint and Natilus Actions Configuration (manager thingy) that lets you edit the right click menu in Nautilus

sudo apt-get install photoprint nautilus-actions

Goto System --> Preferences --> Nautilus Actions Configuration (Yours may have a different name) 

Here is were we add the new menu option. 
(The menu you see when you right click on files in the File Explorer a.k.a. Nautilus) 
Click the "Add" button
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96760&stc=1&d=1229571813[/IMG]

Then...
We fill out the label as follows:
Label: Print
Be sure to set the path and the parameters as they are shown:
Path: photoprint
Parameters: %M
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96761&stc=1&d=1229571813[/IMG]

Then...
Setup the File name paths, maybe someone knows how to add mime type extensions to this... I dont know how though.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96762&stc=1&d=1229571813[/IMG]

Then we have to be sure we export the settings in order for them to take effect. It took me a few tries to get this right.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=96764&stc=1&d=1229572531[/IMG]

The end result will be that "photoprint" will get passed the command when you right click on an image to print. From there you can select the layout and drag more pictures onto the photoprint dialog box in order to complete the effect.

-Judasg0at

PS - Although its only an opinion, I really think that Ubuntu should come with this by default. Having this enabled would be one of the small things that I feel would make Ubuntu a better desktop OS. Even if it were implemented in a different way or with other programs, I think it is a really good idea. Windows has had this since 2000 I think. Anywho, I hope this helps someone.

---

### Post by seshomaru samma on 2009-11-09
THANK YOU SO MUCH
I have searched for years (literally) for a solution 
(for anyone interested , read [this]("http://ubuntuforums.org/showthread.php?t=1010194") as well)

:smile:

---

