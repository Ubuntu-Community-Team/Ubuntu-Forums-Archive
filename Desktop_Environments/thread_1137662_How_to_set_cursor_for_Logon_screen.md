---
title: "How to set cursor for Logon screen?"
date: 2009-04-25
forum: Desktop Environments
---

### Post by ljerabek on 2009-04-25
First let me say thanks to anyone who is willing to reply to this question.

I recently upgraded from Intrepid to Jaunty however now my cursor a the Login prompt is not the same as the one I have set for my theme. It appears to be the default X windows cursor and watch (when processing). 

I'm pretty familiar with how to modify the theme settings from the gui and even gconftool-2 but this doesn't seem to have an effect on the pre-logon mouse cursor.

I was trying to see if there is a way to modify the pre-logon mouse cursor to match what I am using in my themed logged on. I just don't think I am modifying the right settings for the pre-logon mouse cursors.

Thanks,

Lu

---

### Post by yabbadabbadont on 2009-04-25
There is a way, but it is rather involved and I don't have Ubuntu installed any longer so I would be trying to do this from memory...

Anyway, the cursor theme would need to be installed in /usr/share/cursors or, if that directory doesn't exist on Ubuntu, in /usr/share/icons.  (yes, really :D)

Then you have to copy one of the existing theme files in /etc/X11/cursors (I think that is correct) and give it a new name for your theme.  Then edit that file and change the name of the theme in it to match your new one.

Now you have to use update-alternatives to add the new theme to the list of valid cursor theme alternatives.  The command to do so is not intuitive and I'm not going to try to remember the exact syntax.  I'm sure that I have posted the exact instructions for this before, but I haven't been able to find them yet.  You may want to search too while I keep looking for them.  :D

Finally, you use update-alternatives to set your new cursor theme as the system default.  Then reboot.

---

### Post by yabbadabbadont on 2009-04-25
Found it:

[http://ubuntuforums.org/showpost.php?p=3935199&postcount=13](http://ubuntuforums.org/showpost.php?p=3935199&postcount=13)

---

### Post by ljerabek on 2009-04-25
Worked great for setting the arrow. How do you change the cursor which shows processing? ie. hourglass or the wrist watch for a brief moment when you exit X or at startup when it's loading the login screen the icon is an ugly wrist watch. It is the default X windows uses. After I get that fixed I am golden.

Thanks again for any input.

---

### Post by yabbadabbadont on 2009-04-26
Those are part of the cursor theme that you have installed.  If it is showing the default used by X, then the theme you installed doesn't provide those specific cursors, is broken, or has copied the default ones.  Unless they work once you are in Gnome, in which case something very strange is going on...

---

### Post by ljerabek on 2009-04-26
Cool that is all I needed to know. Thanks for your help. It's not but just a little annoying now. I still would take Linux to Windows any day.

---

### Post by ljerabek on 2009-04-26
NOTE: The following process must be done with root permissions.

Here was the issue which caused me tons of trouble but after digging in I found the problem. 

The link /usr/share/icons/default/index.theme would not be created without me manually creating the link.

ln -s /etc/alternatives/x-cursor-theme /usr/share/icons/default/index.theme

So here is a two step method to get the default cursor theme to work.

Make a link for the x-cursor-theme you want as default replace {path to your theme} see below
ln -s {path to your theme} /etc/alternatives/x-cursor-theme 
ln -s /etc/alternatives/x-cursor-theme /usr/share/icons/default/index.theme

// Cursor themes are located under /usr/share/icons/
// There are associated {theme}/index.theme files for cursors
// For example I want the default not logged on theme to be DMZ-White
ln -s /usr/share/icons/DMZ-White/index.theme /etc/alternatives/x-cursor-theme 
ln -s /etc/alternatives/x-cursor-theme /usr/share/icons/default/index.theme

That is it.

If you have the following symbolic link [/usr/share/icons/default/index.theme --> /etc/alternatives/x-cursor-theme]. The steps in stated in yabbadabbadont's post below work without error.

Here is the link again to his post:
[http://ubuntuforums.org/showpost.php?p=3935199&postcount=13]("http://ubuntuforums.org/showpost.php?p=3935199&postcount=13")

---

