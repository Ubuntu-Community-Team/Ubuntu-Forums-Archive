---
title: "Gnome cannot change desktop background, cannot browse images"
date: 2008-04-22
forum: Desktop Environments
---

### Post by Toumal on 2008-04-22
Hello folks,

I'm having a strange problem here: Ever since I upgraded to 7.10 a long time ago, I cannot change my desktop background to anything I don't have in my backdrop list already. That means I CAN change alright, but if there's a new picture I want to add, that doesn't work. 

I have my .gnome2/background.xml in my home, and I guess I could add entries manually there, but why doesn't gnome control center do this anymore? After installing some additional wallpapers via a dpkg package I see them in the list, but I still cannot add mine! I even tried copying them to /usr/share/background but that didn't do the trick either...

Also, when I browse for new background images to add in the control center, it doesn't show me any files. Not png, not jpg, not gif. I have to select "All Files" as a filter, then it shows them. Even the preview thumbmail works, so I don't think it's a libpng or related library issue...

Anyone have any clues? I don't see any meaningful messages in the logs or the console. Even upgrading to the latest 8.04 didn't help!

---

### Post by mikessu on 2008-08-25
I'm having exactly the same problem. Anything new with this?

---

### Post by bracc0 on 2008-11-12
Hello, guys
I use a "face browser" login. I have a problem similar of yours guys when trying to browse for a "global faces directory" different from /usr, "Filesystem", CD-ROM and so.

I am using Intrepid Ibex.

Any hint is welcome!
Claudio

---

### Post by uughzee on 2009-04-01
i am having a similar problem, i had a remote session with a friend of mine and had set the rem. desktop to, do not show desktop background during session. after we were done i closed off the remote settings and unchecked the "do not show desk top bkgnd" went ino my background settings in appearances now theres a thumbnail there of an olive drab solid color screen and all of my personal bkgnd's as well but will not let me use my own, it stays on the green screen. although, on startup it will have the last screen i was previously using up for a second then blinks right back to the green one.           any tips please?????!!!!!!
 it's just annoying and would like my eyecandy back!!!;)

---

### Post by steeleyuk on 2009-04-01
I had this issue until the other day, same as uughzee, I selected do not show desktop and after disconnecting, the wallpaper was gone.

The fix is this:

Press <ALT>F2 and type gconf-editor. In the left hand pane click desktop, then gnome, then background. Click draw_background and the wallpaper should return.

---

### Post by sonicb00m on 2009-04-06
> **steeleyuk said:**
> I had this issue until the other day, same as uughzee, I selected do not show desktop and after disconnecting, the wallpaper was gone.

The fix is this:

Press <ALT>F2 and type gconf-editor. In the left hand pane click desktop, then gnome, then background. Click draw_background and the wallpaper should return.

Thanks, that's been driving me nuts!

---

### Post by Luis-for-um33 on 2009-11-03
I have a similar problem.

Yesterday, under Jaunty Jackalope, the background image was just fine. Today (11-2-09) I upgraded to Ubuntu 9.10 (Karmic Koala) and I noticed that the image I had as background had been replaced by a dark screen. Now I cannot display any of my other background images. The "Appearance Preferences" app doesn't seem to be working. Does anybody have a clue as to how to make it work?

Thanks for any help anybody can provide.

Luis

PS: I followed the instructions given by "Steeleyuk" above: [The fix is this: Press <ALT>F2 and type gconf-editor. In the left hand pane click desktop, then gnome, then background. Click draw_background and the wallpaper should return.]; but it didn't work for me. However, I did learned about <ALT>F2 and that's good to know. Thank you Steeleyuk.

PS: I realized this morning (11-3-09) that my image IS on the desktop; it just cannot be seen. 

If I move the mouse over the desktop and click the right button in the area where the image should be, the drop down menu tells me that there is an image there. 

Also, if I move the mouse over to the top left of the screen and press the right button, I get evidence that the two pdf files I had there before ARE still there; just invisible. 

Just what could be causing this?

---

### Post by chi2jjk on 2009-11-28
I also have this exact same problem.  PLEASE H E L P    M E ... . .  .  .

---

### Post by frosty007 on 2009-11-28
well u people are stupid lol, just install new ubuntu wayyy much better

Check out this thread for more info--- [http://ubuntuforums.org/showthread.php?t=1340305](http://ubuntuforums.org/showthread.php?t=1340305)

---

