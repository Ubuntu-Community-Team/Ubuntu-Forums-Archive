---
title: "Aaargh.... Tried and tried and tried but still can't get beryl to work with xgl"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by djrobthaman on 2007-04-30
Hi,

Currently I have in my xorg file  Option "Composite" "0" because that's what the insructions told me to do.  xgl looks fine when I log in but beryl doesn't work properly.  If I change my xorg file to have in it Option "Composite" "Enable" (which is how I had it in edgy where I got beryl working perfectly) the xgl session looks like what is shown in the screenshot I attached.

Also can't get the desktop effects to repond at all to beryl-manager.  It responds to the changes made n the drop down menu, but nothing gets changed based on settings altered in the beryl settings manager.

By the way, I'm using an ATI Radeon X1300.

If anybody knows anything I can try to get it working I'd really appreciate it,   Thanks.

---

### Post by lbyrd33 on 2007-04-30
I found this thread particularly useful: [http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643).

---

### Post by djrobthaman on 2007-05-01
Thanks,

I pretty much used that method to install (not 100%, but essentially, did the same things initially for getting the xgl session and downloaded all the files from that repository... ) the only difference is that I didn't  turn off the universe repository while I was doing it.  I started over using those instructions anyway and came up with the same end result.  By, the way, I hadn't actually thought of running beryl-manager through the terminal.  Stupid me.  When I do that I get the following response

```

** (beryl-manager:23974): CRITICAL **: can't execute beryl-xgl: Success

```

over and over and over again.

Does this suggest a way to fix it?  I've seen some posts talking about the latest beryl-core package not having headers or something like that for beryl-xgl and the solution is to force a different version (something like berylfeisty~ 0.20).  I've tried this already (a few times actually) and once I do this, whenever I run beryl-manager the screen goes white and that's it.  I need to press ctrl+alt+backspace and log in to the regular gnome session to revert to the other beryl-core version before the xgl session will give any output other than a white screen.  

I'ts kinda frustrating cuz I had beryl working on edgy.  grrrr.  Anyway, what do you suggest???

And thanks again

---

### Post by djrobthaman on 2007-05-01
Whoa!!!!

I spoke way to soon.  Thank you so much.  I found the answer on page 5 [here]("http://ubuntuforums.org/showthread.php?t=399643&page=5").  Just run 

```

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl --replace &

```

before beryl-manager.

Quick question though.  I can't get it to run by pressing alt+f2.  If i try i get

```

Could not open location 'file:///LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl --replace &amp;'

```

I've tried inserting the whole thing without the ampersand at the end but I got a similar error message.

And I can't get it to load with the session automatically

I went to System > Preferences > Sessions > Startup Programs > New  and inserted that whole length of command in the command box, but I don't think it loads because when I execute beryl-manager after the login it goes to the white screen again.

The only way I can do it so far is to run the command in the terminal (that way it works and does it's thing) and then run beryl-manager otherwise.  But this leaves me with a window I can't close without worrying about the consequences that I might just close anyway by accident.  Do you know of any way to get the command to invoke itself automatically on login otherwise??????

Thank you again for all your help.

---

### Post by djrobthaman on 2007-05-01
Hmmm... this fix is actually quite buggy... so far a couple of time the screen has gone white anyway... and now I'm looking at all the fixins of beryl but a white space where the top gnome panel once was.  It just went white randomly.  One second it's there the next second all white.  If i click where the applications button should be the sub menu pops up and such but I can't see anything actually on the panel.  Man that sucks.

I can live with this fix for now but do you know of another???

Thanks

---

### Post by KoolPenguin on 2007-05-01
I'm having the same problem and have not found a complete fix yet.  If I find anything I will post it here.

- Chris

---

### Post by djrobthaman on 2007-05-01
Thanks Chris... I'll do the same if I find anything too.

---

### Post by KoolPenguin on 2007-05-01
> **djrobthaman said:**
> Thanks Chris... I'll do the same if I find anything too.

Ok, here is what I did to fix my problem and I hope it works for you and others also.  Note my computer specs and adjust if needed.

During this process you may or may not have Beryl Updates available.  If it appears, do the updates.  I had 3 Beryl related updates.

Write a script so Xgl can start on its own: 

> sudo gedit /usr/local/bin/startxgl.sh

Enter and save this script information: 

> #!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

Make the script executable: 

> sudo chmod a+x /usr/local/bin/startxgl.sh

Now, we need to put in a Xgl option in our GDM login screen: 

> sudo gedit /usr/share/xsessions/xgl.desktop

Enter and save this script information: 

> [Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

Also make this script executable: 

> sudo chmod a+x /usr/share/xsessions/xgl.desktop

Disable the universe repositories (these provide Beryl software that is incompatible with the fglrx driver). 

> Go to System > Administration > Software Sources 
Uncheck Community-maintained Open Source software (universe)
Click Close

Add the correct repository to the top of your apt source list: 

> sudo gedit /etc/apt/sources.list
Enter: deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
Save and close gedit

Update your apt sources: 

> sudo apt-get update

Add Beryl and the Emerald themes to your start-up programs: 

> Go to System > Preferences > Sessions
Click the New button
Type "Beryl" (no quotes) for the Name text box
Type "beryl-manager" (no quotes) for the Command text box
Click the OK button

Click the New button
Type "Emerald Themes" (no quotes) for the Name text box
Type "emerald --replace" (no quotes) for the Command text box
Click the OK button

Do the Beryl Manager (Red Diamond):

> Goto Beryl Manager > Select Window Decorator > Standard Beryl Decorator (Emerald)

> Goto Beryl Manager > Select Window Manager > Metacity (Gnome Window Manager)

Restart your system and login using Xgl session.  Open a terminal and do:

> LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl

I haven't found a way around the LD_PRELOAD yet but if I do I will post it here also.  I'm thinking I might just have to make a script run this in a terminal during startup.

* UPDATE * If all this works you may try:

> Goto Beryl Manager > Select Window Manager > Beryl

Restart your system, login Xgl session and you should see the Beryl splash.  No need to enter LD_PRELOAD in terminal.

Most of this information was from the Ubuntu Guide and some was what I figured out that worked for my system.  Let me know if it works for you.

- Chris

---

### Post by Smidley on 2007-05-04
Everything worked (except for white borders instead of shadows under menus and tool tips) after following your instructions and running "LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl" in the terminal, so I set the Window Manager to Beryl and restarted, but it didn't do anything.

:mad: Grrr!!!

I'm using a Dell Inspiron E1705 with an ATI Radeon Mobility X1400.

Thanks for your helpful input anyhow.

---

### Post by Smidley on 2007-05-04
Yay!  I solved the problem with the help of this [guide](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29).

I had already completed almost everything in the guide except for this one note specific to ATI card owners:

> *  If you are using ATI with XGL, you'll get an error that beryl-xgl is missing. Solution is not elegant, but it's working:

Download beryl-core deb from [http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-core_0.2.0~0beryl1_i386.deb](http://ubuntu.beryl-project.org/pool/feisty/main/0.2.0/beryl-core_0.2.0~0beryl1_i386.deb)
Unpack beryl-xgl from archive to ie. ~/Desktop
From terminal run: sudo cp ~/Desktop/beryl-xgl /usr/bin/beryl-xgl

I never saw an error saying that beryl-xgl was missing, but I did this, and now it works.

---

### Post by KoolPenguin on 2007-05-04
I'm glad you got it working!  I never received an error that beryl-xgl is missing either and I must of tried half a dozen different ways until the one I mentioned worked for me.  The only thing I still cannot get to work in Beryl is Google Earth, it pauses at initializing and I have to force quit but no biggy.

- Chris

---

### Post by rygar on 2007-05-09
this thread is very helpful

but has anyone figured out how to stop the white gnome-panel problem yet?
or avoid the LD_PRELOAD?

---

### Post by MattiViljanen on 2007-05-10
I have Acer Ferrari 3400 and Mobility Radeon 9700, with fglrx 8.36.5 (newest) drivers, and Feisty.

Copying beryl-xgl from older package is as ugly a fix as it can be, but it works... Haven't checked Beryl forums yes to see if this has been fixed. Well I'm happy to use fglrx, Xgl and Beryl. Google Earth hangs for me too, but then again I can just use xorg for that.

Oh, and it seems that by default (read: all the tweaks to get it working) I can watch videos with Beryl enabled; no black screen in Totem anymore! :popcorn:

EDIT #1: It is possible to run Google Earth (and other OpenGL apps) like this:
*DISPLAY=:0 googleearth*
It's quite ugly as resizing doesn't work and it is always on top, but it's better than nothing ;)

EDIT #2: [Bug]("https://bugs.launchpad.net/ubuntu/+source/beryl-core/+bug/95394") has been filed for this.

---

### Post by jet2230 on 2007-06-05
the version of beryl installed was the problem for me.

i got this fixed by using this guide [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29) look under ' Alternate method: Using closed source FGLRX drivers from ATI ' for full guide. the guide shows how to uninstall current beryl and install version 0.2.0 instead of 0.2.1. 

this is only for ati chipsets

---

### Post by Kralizec on 2007-07-11
I'd just like to add support...I struggled with this for a long time and this post helped me figure it out. The final solution for me was to install the older version (0.2.0) rather than the newest (0.2.1).

For others who stumble onto this...I have an ATI RADEON EXPRESS Series card and I'm using the newest fglrx drivers.

---

