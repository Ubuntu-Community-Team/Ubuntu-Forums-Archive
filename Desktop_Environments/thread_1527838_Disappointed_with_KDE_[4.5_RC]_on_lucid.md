---
title: "Disappointed with KDE [4.5 RC] on lucid"
date: 2010-07-09
forum: Desktop Environments
---

### Post by Ekeluo on 2010-07-09
I am rather irritated right now. I managed to install kde 4.5rc alongside gnome 2.30. And the 1st impression is barely ok. It seems stable and fast, but because wi-fi doesn't work for me, it's really limited in where it can go. Considering I'm typing this logged in thru gnome on the exact same system, connected to the wi-fi network kde refused to connect to, it's rather baffling.

Update: Used networkmanager-gnome to get me connectd in before I login since network doesn't use security (even gnome doesn't play well with that.

KDE issues (some from 4.4.2 and still in 4.4.92).
Plasma:
1.Tooltips  aren't persistent, they shy away after a few seconds. Also they should update with data they're representing (yes system monitor, I'm looking at you);
2.Allow setting of colours for graphs e.g. ram monitor, cpu monitor. Was there but now gone;
3.A more convenient way to exit the plasma dashboard (right click on background perhaps?);
4.Individual wallpapers per desktop; (again, there before in 3.5)
5.Panel auto-hide show delay still not adjustable; choice for fade-in animation;

Kwin:
1.The present windows effect wastes a lot of space under 'natural' without 'presenting' the windows optimally; other setting (fixed & flexible grid) make programs like audacious look utterly horrible; the placement algorithm needs to be sorted;
2.Oxygen menus have too much border, give impression of bloat;
3.Kwin compositing freezes everytime I change decoration, style, font, etc. Have to use key shortcut to disable then re-enable. This is somehow connected to my system using more swap as time goes on, while mem usage remains ~40% (of 2gig)


Dolphin:
1.Ability to show basic media file metadata without need for nepomuk (as was possible in konqueror in 3.5.x), e.g resolution of jpeg/png/bmp images, id3 info from mp3/ogg/wma files; pdf [this marked as done in the feature plan, yet to see it)
2.More columns for sorting in details view (windows explorer excels in this). Above point will be needed before this is possible;

Amarok (2.3.1): 
1.Still no proper use of album artist tag (for compilation albums and such) and/or proper detection of various artists listed in the 'artist' tag;
2.All embedded album art is useless;
3.Album art isn't shown prominently in the collection browser (22px crap doesn't count, the art itself is >300px);
4.Can't queue files from collection. Can queue from playlist, albums applet but not collection. Why?;


It is a stable pre-release software but stable can only get us so far. The basic features users have clamored for aren't being provided, resulting in my playing music with banshee and viewing my pics with geeqie. Oh, and being logged into gnome right now.

---

### Post by Ekeluo on 2010-07-09
This shot should show what I mean

---

### Post by hikui on 2010-07-10
I have same issue on wifi. It happens not only in 4.5 rc, but also in some earlier versions. So I'm back to GNOME.

---

### Post by ankspo71 on 2010-07-11
Hi,
As long as you have the gnome desktop installed, you should be still able to use the gnome network manager by typing "nm-applet" in the terminal, even while running the KDE desktop. Edit: --> sgkudo might be required to run the network manager like this --> "gksudo nm-applet", but I don't remember. Anyways, the link below will help explain more...

IF that works good for you, you can follow this tutorial to make it a permanent change in the KDE desktop.
**"HOWTO: Use Gnome Network Manager in other DE"**
[http://jeffhoogland.blogspot.com/2010/04/howto-use-gnome-network-manager-in.html](http://jeffhoogland.blogspot.com/2010/04/howto-use-gnome-network-manager-in.html)

If gnome-network-manager doesn't help, try installing "wicd". I see the wicd network manager recommended by Kubuntu users often.

I'm not sure what is going on with your kde apps while running in Gnome. I haven't had that problem before, as far as I can remember. It would be a big disappointment for me too. Do you still have the same problems trying to run gnome applications in the KDE desktop?

Since you mentioned using the equalizer in Amarok, I want to let you in on something... there is a system wide graphical equalizer for pulseaudio now, but it is only available in a PPA repository. It really livens up my sound too. It can work in Gnome or KDE as long as Pulseaudio is installed and in use. Here is where I wrote about it: 
[http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html](http://sticky-bones.blogspot.com/2010/06/pulseaudio-grpahical-equalizer-for.html) 

If you install plasma-widget-smooth-tasks, it makes a great alternative to the KDE default taskbar widget. It will also give you persistent tooltips (but only for the tasks in the task bar area).

Hope some of the things I said makes your KDE experience a little better. ;)

---

### Post by Ekeluo on 2010-07-11
Thanks ankspo71, tried wicd, doesn't work either. Typing things from gnome now, about to set nm-applet to autostart to see if that works.

About the gnome apps, they use the qtcurve style just fine.

Now updating to RC2 to see if stuff improves. Kwin seems to freeze (i.e, stop repainting the UI) often when I change (or adjust) the style or effects). Have resorted to starting and then quiting warzone2100 (only game I have at the moment) to kick it in the shin.

About smoothtasks, that is an awesome widget, been using since karmic (~ October-ish). Wondering why it's not yet incorporated into the main task manager.

---

### Post by lexxonnet on 2010-07-12
Hi Ekeluo,

I can address a couple of issues that you posted. You can set different wallpapers per desktop by choosing a different activity per desktop. Right-click on the pager, select virtual desktops and select "different widgets per desktop". You should then be able to set an individual wallpaper for each desktop.

Not sure what you mean by the notification area icons being too big. All of mine are uniformly sized, and they don't get any bigger even if I resize the panel.

Not sure why WiFi isn't working for you? Are you connecting to a hidden network? If so, I believe knetworkmanager has some issues. Otherwise, it should work fine.

As to your colour issues in Gnome, I'm not too sure how I'd fix the KDE apps. I can however, guess why that is the case with dolphin etc, but not with VLC. VLC is a pure Qt4 app, while all KDE apps use libkde, which is governed by KDE settings. Not entirely sure how to get them to fit into gnome, but that might give you a point to start with.

Also, if you're peeved about something in KDE or Amarok, you'd be better off posting bugs/feature requests in the KDE bugzilla instead of on the Ubuntu forums. Its more likely that the problems will get fixed that way! :)

Pause/Unpause work almost instantaneously for me in Amarok (running 2.3.1). Not sure why you're having an issue.

A lot of your problems might disappear if you delete your .kde directory and start KDE again. Its very likely that you have an old bunch of settings conflicting with the newest version of KDE.

---

### Post by Ekeluo on 2010-07-12
Thanks for your reply lexxonnet, have been trying to file useful bugs/wishes where applicable. The amarok wishes for various artists and embedded art have been there for ages though see ([https://bugs.kde.org/show_bug.cgi?id=199483]("https://bugs.kde.org/show_bug.cgi?id=199483"), [https://bugs.kde.org/show_bug.cgi?id=90095]("https://bugs.kde.org/show_bug.cgi?id=90095") & [https://bugs.kde.org/show_bug.cgi?id=119539]("https://bugs.kde.org/show_bug.cgi?id=119539").

I already have my 2 activities setup the way I want with their peculiar widgets, can't start creating six copies just for desktop backgrounds.

About the kde apps colors in gnome, I changes the theme, then kde apps started behaving themselves. Funny cause when I changed back they were still ok, adapting fine. Guess the setting needed a refresh or something.

My kde install was done just last week, onto an Ubuntu 10.04 lts (installed the Kubuntu-desktop package), never installed 4.4.2, went straight to the 4.5rc, cause I wanted to see the improvements to strigi. It's much faster in indexing and providing results now. Still no adequate clients though.

The networking issue is really frustrating as I have to log out of kde everytime I want to get on the net (or I have to start a new session but most times the gnome won't connect if KDE is already running). I don't really know how to file a bug for that.

Still haven't upgraded to rc2, trying now.

---

### Post by lexxonnet on 2010-07-13
Yeah, its a bit sad when bugs/wishes get left behind. I wasn't the biggest fan of Amarok 2 when it came out, but it seems to have improved a large amount in the past few releases. I still prefer the amarok1 interface though, it was much faster and definitely a lot more streamlined IMO. Even though I've got my Amarok 2 setup to mimic Amarok 1's appearance rather closely, it doesn't quite have the same functionality.

There are a few alternatives worth trying, such as Clementine which is a port of Amarok 1.4 to Qt4. Not sure if it will address your problems, especially as it didn't have a Queue manager last time (3-4 months back) I checked it!

Yeah, unfortunately, it doesn't seem to be possible to change desktop backgrounds without having a separate activity. Although, I don't expect they'll change this since it was most likely intentional. 

I've turned off Strigi on my machine since it was a bit of a pain in 4.3. Never turned it on after that, but if its improved, it might be worth giving it a shot!

I'm really stumped on the networking issue however. It doesn't make sense that Gnome's network manager works, while the KDE one doesn't - especially since they use an identical backend. When you attempt to connect to a network using knetworkmanager, what does it say? Does it say "Unmanaged" or does it just fail to connect?

---

### Post by Ekeluo on 2010-07-16
Sorry for the long time 2 reply, erratic power supply still plagues this my country. Anyway...

Strigi works pretty well in this version (now on rc2, kwin still does the pseudo-freeze thing), it's only let down by the lack of a quickly available client. Dolphin's too slow to load on my system and krunner almost always shows me the same 10 documents regardless of the terms I type into it.

About knetworkmanager, it 'tries' to connect when I double click on the network of choice, but always fails. I uninstalled it in the hopes that the plasma widget would look and, more importantly, work better, but it does only one. Guess  which? Anyway I added gnome's nm-applet to start in kde. It doesn't actually open or show the tray icon, but the connection is made on login which I guess is okay for my immediate needs. If it disconnects, I have to re-connect manually (cli). Funnily, the widget detects all initiated connections and shows them, just can't make any itself.

---

