---
title: "Screensaver: Pictures folder"
date: 2009-02-02
forum: General Help
---

### Post by bilijoe on 2009-02-02
In a totally default setup, when you select System>Preferences>Screensaver, and then select "Pictures Folder", where does the screensaver app look to decide where the images are located. It is not as simple as looking for a folder named "Pictures". :confused:

The situation I am in... Over time, I have changed the images my screensaver used (or so I thought) many times, but in all cases there were nearly 1,000 images in the folder, and only a few hundred were changed each time. This time, I intended to change the entire set, but when the screensaver came on, it was still using the old set of images. I went to System>Preferences>Screensaver, and both the small preview and the full screen preview were also using the old set of images. ](*,)

I changed so many times I don't remember exactly, but I'm pretty sure that sometimes I emptied the current "Pictures" folder and copied the new set of images in, and sometimes I renamed the "Pictures" folder to "Old Screensaver #", with a new # each time, and created a new "Pictures" folder. Since I didn't get the change I expected this time, I started trying to find out where, exactly, the screensaver was getting the images from. Unfortunately, I'm real sloppy when it comes to managing images, and there is so much redundancy in my system, I couldn't just search down a filename or two to locate the folder.

In desperation, I finally copied all the folders I thought had ever been used as [what I thought was] the source for the screensaver images, onto CD, and started deleting folders, one by one. When I got down to just one folder ("Pictures"), it was clear that this was still not the source for the images, as it was the new (now totally different) set, and the screensaver was still using an older (perhaps much older--maybe even the first set I ever used) set. But when I deleted that folder, the screensaver would only show a blank screen. Curious. :?:

So, I copied the folder out of the trash, back to where it had been. Still, all I got was a blank screen. I restored all the folders I had deleted--still, no screensaver/slideshow images. I then created a temporary new user, and fired up the screensaver for the new user, and set it to "Pictures folder". Worked fine.

Then, I noticed that when I was signed in as myself, not only did the screensaver not work, but the system was really sluggish. System monitor told me that the "slideshow" process was sucking up over 50% of the CPU, and when I checked the list of files it had open,it was huge (several hundred). Back to the new user. Checked the SysMon there... "Slideshow" was using only 4% of the CPU, and had only a hlaf dozen or so "Files" opened (most were pipes, etc.,not "real" files). 

I looked around at the running processes (all of which seemed to be sleeping, except the SysMon), and saw a "Gnome Screensaver", and "Gnome Screensaver Preferences" process (the preferences window was opened at the time). I could stop both the Gnome processes, and the preview of the screensaver would continue to run, but if I stopped the "Slideshow" process, the preview stopped changing images, and the entire preferences window became unresponsive (i.e., I couldn't change screensaver selections, or do anything else). When I restarted the "slideshow" process, the highlight jumped to the last screensaver type I had clicked on, and it began previewing.

So, it doesn't seem to be the gnome screensaver that's running the slideshow for the [default] screen saver, though the preferences window IS the gnome Screensaver Preferences window, but it is stopped by stopping the "slideshow process". 

Again, I am left wondering, where does "Slideshow" look to find the folder it should use for the images (and how does a sleeping process use up over 50% of the CPU)? The Xscreensaver or Xslideshow, or whatever the alternate is, is not installed on my system. It's not Picassa's slideshow that's being used... I'm lost! I can't figure out what controls "Slideshow", and I can't get the Screensaver->"Pictures folder" to work again, even though I have restored all the folders that were ever used as Pictures folders (regardless of renamings). 

Under the new user I created, the slideshow screensaver doesn't seem to be very picky about where the images are placed, as long as a folder named "Pictures" is somewhere in the path (well, since I didn't rename anything this time, it may be that it's the "original" Pictures folder that has to be in the path, regardless of it's name, I didn't think to try to rename things in the new user's environment).

So, does anybody have a simple answer for me? It seems like the answer should be simple. Is there an environment variable or something that points "slideshow" (whatever that is, exactly) to a folder, or a path, in which it can find the images it is to use? Oh, and it's not F-Spot's slideshow that's running the show either--I did check that. :biggrin:

I've checked everything I can think of, until my brain hurts, and I still cannot get my screensaver to work again. And apparently, it keeps trying desperately to find images somewhere, because when it first starts up, its list of files is only a dozen or so long, and it only uses 5% or so, of the CPU.  But rather quickly, the file list (as given by SysMon), and the CPU usage begin to skyrocket.

Have I killed my Screensaver? Does anyone know how the "default" Screensaver/slideshow works? Should I just shoot my monitor? Or drink enough Scotch that I see a series of images on the screen when it goes blank, even though they aren't really there? Aaaagggghhhhhhhhhhr umph.](*,)

I'm going to go do something else now, for a while, and hope that, as is almost always the case, when I return, some kind and knowledgable soul will have provided me with an answer to what in Tarnation is going on. 

(BTW, when I try {gently} to win converts to Linux, I always tell them Ubuntu is the ONLY way to go, because of the nature of the community that drives the Forums, which I always tout as the best Technical Support EVER. Then I mention {again} that, like everything else Linux, the Ubuntu (tech support) forums are also... FREE. What a great OS/community this is. Why don't more people get it? Anyway, I've got my fingers crossed that, as usual, I'll find an answer here when I return in a bit. [COLOR=RoyalBlue]And thanks again to all those out there who have provided help in the past, and helped educate me {and, I'm sure thousands of others} in the ways of Linux and Ubuntu[/COLOR].)

---

### Post by PhilCash on 2009-02-05
G'day bilijoe,

I'm not 100% sure this is what you're after, but in my struggles to make a screensaver behave as I would like I've found that the default gnomescreensaver using GLSlideshow gets its default images from
 /usr/share/backgrounds/ 
I've had success symbolically linking other directories of my photos to that default directory using
sudo ln -s /usr/share/backgrounds/ /home/phil/Photos/MyPhotoDirectory/

This allows the screen saver to use those images as though they were in the default directory.

Good luck!

I've given up on gnomescreensaver and have nearly got xscreensaver to work - it just has little text attacks each time it changes image...see my plea for help in this forum...

Cheers,
Phil

---

### Post by bilijoe on 2009-02-05
G'day Phil,

Thanks, but that doesn't seem to be the case on my system--or else something else is broken. There are plenty of images in my /usr/share/backgrounds directory, but my screensaver still only shows a blank screen when I select "Pictures folder" from the list of available screensavers. Good try though. It kind of makes sense. Certainly nothing else seems to make sense here.

Thanks again,
BiliJoe

---

### Post by bilijoe on 2009-02-05
G'day again Phil,

I see. If I select GLSlideshow, I do get the images in /usr/share/backgrounds. However, the screensaver I was using and seem to have broken is the one entitled "Pictures folder". Initially, it did use the images in my Pictures folder, but, either it continued to use that folder, even after it was renamed, or, once all folders named [anything]Pictures[anything] are removed from the system, it looses its bearings and can never locate the [new] Pictures folder again. So you are right, we were just using different screensavers.

Thanks again,
Cheers,
BiliJoe

---

### Post by TylerBraun on 2009-03-04
I have the same problem described here, but something I noticed with mine that may help someone more knowledgeable than I figure this out is that before mine broke, it was using pictures, both from the Pictures folder in my Home directory (anything I moved there would appear in the screensaver) and from (I think) Firefox's cache. Pictures from anywhere I had been recently on the internet would show up in the screensaver as well. I really liked that little twist and would like to get it back.

---

### Post by bilijoe on 2009-03-04
That is kind of a slick little glitch. For several reasons, I did a clean install of 8.10 (had been using 8.04), so mine works "normally" again.

Before I did the full, clean install though, I did an install where I left my /Home partition alone (to preserve all my settings, keep pix and movies, etc), and in that case, I still had the problem of not being able to find where the folder was that the screensaver was using.

Something feels glitchy in this install, so I may decide to redo it. If I do, I'll play around some to see if I can figure out what the real deal here is. If I find out anything, I'll post it in this thread.

---

### Post by Nilesh Salunke on 2009-03-17
well this worked for me in ubuntu Intrepid Ibex , Ubuntu 8.10.

1)Go to System->Preference->Screensaver

2)Select "Pictures folder" and close

3)    * Create a new folder somewhere (it doesn’t have to be under the ‘Pictures’ folder)
    * Open a terminal window (select Terminal under Accessories)
    * enter the following:

      gksu gedit /usr/share/applications/screensavers/personal-slideshow.desktop

      (enter your password if prompted)
    * Scroll down to the line (near the end) that begins

      Exec=slideshow

    * Add the following after this command:

      --location=<your pictures path>

      (You will have to use standard escape sequences if you have spaces in the path.)
    * Here’s an example:

      Exec=slideshow --location=/home/myusername/Pictures/My\\ Screensaver

---

### Post by TylerBraun on 2009-03-19
Firstly, thanks for the info. I have a few more questions though. Can I list two location in this manner? I liked having the screensaver show the FireFox Cache, but I also want my 'Pictures' folder. Also, will this be recursive? I have the pictures in my 'Pictures' folder sorted into many folders and would like them all to show up in the screensaver.
Thank again.

---

### Post by TylerBraun on 2009-03-19
I tried the gedit and I think I found my problem. I decided to run slideshow --help in terminal to learn more about the executable that the file was trying to run and my computer said it wasn't installed. I am installing it now to see what that fixes. I hope it's the right thing.
I'll let you all know how it went when it is done.

---

### Post by TylerBraun on 2009-03-19
A little extra info: terminal said I needed to install drscheme. Do not do this. It won't ruin your computer or anything, but it is definitely not what we are looking for, so yeah, I'm still stuck. The slideshow command doesn't seem to exist on my primary desktop. The wierd part is that my other desktops are having no problem with it. Very odd. That last chunk of info was still very helpful for a few other things though, so thanks Nilesh.

---

### Post by e.m.fields on 2009-10-08
@Nilesh:  :guitar:
You rock. 
This one has bugged me forever.

> **Nilesh Salunke said:**
> well this worked for me in ubuntu Intrepid Ibex , Ubuntu 8.10.

1)Go to System->Preference->Screensaver

2)Select "Pictures folder" and close

3)    * Create a new folder somewhere (it doesn’t have to be under the ‘Pictures’ folder)
    * Open a terminal window (select Terminal under Accessories)
    * enter the following:

      gksu gedit /usr/share/applications/screensavers/personal-slideshow.desktop

      (enter your password if prompted)
    * Scroll down to the line (near the end) that begins

      Exec=slideshow

    * Add the following after this command:

      --location=<your pictures path>

      (You will have to use standard escape sequences if you have spaces in the path.)
    * Here’s an example:

      Exec=slideshow --location=/home/myusername/Pictures/My\\ Screensaver

---

### Post by bilijoe on 2009-10-08
Well, this one did take a while. But, as I knew they would, the good people (all of you) who are the forums, came through for me again. Thanks [B]Nilesh! :popcorn::popcorn::popcorn:
[/B]

---

### Post by Lessss on 2009-11-11
I gave up on this route and instead selected in the screen saver to use F-spot photos. Then in Fspot I imported the drive folder location and it imported all the picture locations ( not the pics).  When I want to add a photo, I open Fspot and drag the photo into fspot and it creates a new link.  It took a while to import my 20,000 pics but it didn't crash the screen saver like the other methods I tried.

---

### Post by vxd240 on 2009-12-05
You might also try this to ensure sensitive pictures don't get displayed.

As per bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/145152](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/145152)

It's a little known "feature", but to set your Pictures directory, you need to define the directory in this file: ~/.config/user-dirs.dirs

From a terminal:

Take a look:
cat ~/.config/user-dirs.dirs

You can edit it manually, or try:
xdg-user-dirs-update --set PICTURES /home/ted/Pictures

take a look again to confirm the change:
cat ~/.config/user-dirs.dirs

---

### Post by cbpxy on 2010-01-28
Thank you vxd240!  This is something that's been bugging me  for a while, and I didn't know about this "feature".  Thanks very much!

---

### Post by melkespreng on 2010-04-11
> **vxd240 said:**
> You might also try this to ensure sensitive pictures don't get displayed.

As per bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/145152](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/145152)

It's a little known "feature", but to set your Pictures directory, you need to define the directory in this file: ~/.config/user-dirs.dirs

From a terminal:

Take a look:
cat ~/.config/user-dirs.dirs

You can edit it manually, or try:
xdg-user-dirs-update --set PICTURES /home/ted/Pictures

take a look again to confirm the change:
cat ~/.config/user-dirs.dirs



That the linux I want to know. Someone sticky this please, this is genious.

---

### Post by Phil Hansen on 2010-04-11
> **Nilesh Salunke said:**
> 
Exec=slideshow --location=/home/myusername/Pictures/My\\ Screensaver


Thanks, that works  for me.
Now does anybody know what to add to the file to change the time delay between pictures. I find it too short.

---

### Post by doublewitt on 2010-05-02
**Ubuntu 10.04**

My gedit file looks like this:

[SIZE="1"][Desktop Entry]
Name=Pictures folder
Comment=Display a slideshow from your Pictures folder
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver[/SIZE]

If I put the line (--location=<your pictures path>) in after "Exec=/user/lib...,
nothing changes. This stuff is new to me - so - please can someone tell what to do?
thx

---

### Post by Fi1618 on 2010-05-08
> **doublewitt said:**
> **Ubuntu 10.04**

My gedit file looks like this:

[SIZE=1][Desktop Entry]
Name=Pictures folder
Comment=Display a slideshow from your Pictures folder
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver[/SIZE]

If I put the line (--location=<your pictures path>) in after "Exec=/user/lib...,
nothing changes. This stuff is new to me - so - please can someone tell what to do?
thx

See the post #14, I am using the latest Ubuntu version 10.04. and #14 way works for me perfectly.

---

### Post by Ozdemon on 2010-05-17
> **vxd240 said:**
> You might also try this to ensure sensitive pictures don't get displayed.

As per bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/145152](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/145152)

It's a little known "feature", but to set your Pictures directory, you need to define the directory in this file: ~/.config/user-dirs.dirs

From a terminal:

Take a look:
cat ~/.config/user-dirs.dirs

You can edit it manually, or try:
xdg-user-dirs-update --set PICTURES /home/ted/Pictures

take a look again to confirm the change:
cat ~/.config/user-dirs.dirs

Tks for the great tip.

---

### Post by zabuch on 2010-07-10
I was having similar problem and decided to package images as .deb - so other can use simply install new screensaver like any other package. I've documented it on [http://techblog.zabuchy.net/2010/how-to-create-simple-theme-for-gnome-screensaver/](http://techblog.zabuchy.net/2010/how-to-create-simple-theme-for-gnome-screensaver/) if you're interested.

---

### Post by Sandy106 on 2010-10-02
> **vxd240 said:**
> You might also try this to ensure sensitive pictures don't get displayed.

As per bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/145152](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/145152)

It's a little known "feature", but to set your Pictures directory, you need to define the directory in this file: ~/.config/user-dirs.dirs

From a terminal:

Take a look:
cat ~/.config/user-dirs.dirs

You can edit it manually, or try:
xdg-user-dirs-update --set PICTURES /home/ted/Pictures

take a look again to confirm the change:
cat ~/.config/user-dirs.dirs

Sorry for bumping an old thread, but does this technique change the directory only for the screensaver, or the shortcuts for the pictures folder and everything else associated with it? I'd like to change where the screensaver gets pics from but not any shortcuts or anything else.

---

### Post by aigarius on 2011-03-24
What helped me is to edit the file /etc/X11/app-defaults/XScreenSaver and change the line to:
```

*imageDirectory:<------>/home/aigarius/Pictures

```

---

