---
title: "[SOLVED] GNOME Art Manager"
date: 2008-02-13
forum: Desktop Effects &amp; Customization
---

### Post by leehach on 2008-02-13
I installed GNOME Art Manager.  When I browse for art (say, desktop backgrounds) I have the choice to Install or Download.  When I click Install, nothing seems to happen, although the selected JPG does get copied to /home/[username]/.gnome2/[something?]/desktop/backgrounds.  But it doesn't appear in the list of backgrounds.  When I click the Add button, I try to navigate to the downloaded background, but since .gnome2 is a hidden directory, I can't navigate there.

What is *supposed to* happen when I click Install or Download?  Should I make a nonhidden directory somewhere to save all of my backgrounds?  How else can I get the backgrounds to appear in GNOME Art Manager?

---

### Post by zami on 2008-02-14
When I hit "install" it's saving to the directory you mentioned, and it doesn't change the desktop right away.  But, if I right click on my desktop, then "change desktop background" the picture I just downloaded is there.  Have you tried this? 

If the wallpaper isn't there waiting for you in the "change desktop background", you can click on "add" and then browse to the folder where you just saved the wallpaper to.  In this browse mode it shouldn't matter that .gnome2 is "hidden", it still shows up on the list.

Also, just for reference, if you ever need to browse your way into a "hidden" folder, click "View" then "Show Hidden Files".  Or hit CTRL-H.  So if you are in your home folder, hitting CTRL-H will show a bunch of directories with . in front of them.  .wine  .gnome2 and so forth. 

Hope something in here helps.  This Gnome-Art browser is kinda funky but I think I like it.  I just installed it today myself.

-zami

---

### Post by leehach on 2008-02-15
Thanks, will try all this later today or tomorrow and report back.

---

### Post by leehach on 2008-02-16
Well, the backgrounds are not showing up automatically, but the Ctrl+H is working to show the hidden directories and navigate to the downloads.  It's somewhat annoying because you have to navigate several directories deep every time.  Should this be reported as a bug?  I assume Download is supposed to download, but Install is supposed to download and have them show up in in the list of backgrounds, as you say?

---

### Post by zami on 2008-02-20
Hi Leehach,

I think you've got it right.  When I hit "Download Only" it lets me pick a directory to save the file to.

When I hit "Install" it saves it to the /.gnome (etc) directory and it's just right there when I open up "Apperance Preferences".

This is very convenient so it seems the way it's supposed to work, so yeah, if I were you I'd "bug" that it's not.

In the meanwhile!  Instead of using "Add" while in Appearance Preferences, try this.
Open up Appearance Preferences
Also open up /.gnome2/gnome-art/download/backgrounds
And just drag the image files over.   This way you could do a bunch at a time much quicker then using "Add" and browsing allll the way over to the directory.

I really am enjoying this Art Manager for installing buttons and icons, but I think for wallpaper I'm better off just using my browser at 
[www.gnome-look.org](www.gnome-look.org)
and
[http://art.gnome.org](http://art.gnome.org)
For me it's faster because I'm usually opening up a few pictures at a time, where as Art Manager only lets you preview one at a time.

Good luck to ya!

-zami

---

