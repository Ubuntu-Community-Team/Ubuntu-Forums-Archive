---
title: "Standard KDE Filemanager/Control Center"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Dormous on 2005-10-13
:confused: Is there an easy way to get the *standard* KDE filemanager (i.e. the default one that ships with kde, that resembles windows explorer)?  I don't much care for the way that the kde file manager works by default in kubuntu.

Also, is there a way to get the default KDE Control Center (once again, the one that ships with standard KDE)?

Not new to Debian, but new to Kubuntu.

Dormous

---

### Post by aysiu on 2005-10-13
I'd imagine you install [KControl](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=kcontrol&sourceid=mozilla-search). I'm not sure what the deal is.

---

### Post by pistoli on 2005-10-13
Go to your panel, right click and select "Configure panel".  Go to the "Menu" icon and check the box next to "Settings".  This will enable the old style control panel ion your Kmenu.

---

### Post by asimon on 2005-10-14
[QUOTE=aysiu]I'd imagine you install [KControl](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&subword=1&version=breezy&release=all&keywords=kcontrol&sourceid=mozilla-search). I'm not sure what the deal is.[/QUOTE]
The deal is that kcontrol doesn't appear in the menu, only that new "System Settings" panel, which some people don't like.

To start kcontrol, just enter hit ALT+F2 and enter kcontrol oder start kcontrol from a terminal.

And the same seems to be true for Konquerer the file browser. I can't find any entry for it in the K menue, only for starting konquerer in webbroser mode.

Regarding the comment from pistoli: The check item is called "Preferences" not "Settings". ;-)
PS: If you follow pistoli's tip, a kcontrol menu item will appear in the "Preferences" submenu.

---

### Post by bailout on 2005-10-14
Have you tried opening konq and going settings/load view profile/file management? This may give you the layout you want.

---

### Post by Freddy on 2005-10-14
> Is there an easy way to get the standard KDE filemanager (i.e. the default one that ships with kde, that resembles windows explorer)? I don't much care for the way that the kde file manager works by default in kubuntu.
I'm not really sure what you meant there but if it's the regular konqueror filebrowser you're after, just open up your konqueror through a filelink and press F9 and you should get the sidebar back.
Maybe you need to save the profile for filemanegment after this.   /// Freddan

---

### Post by Freddy on 2005-10-14
> Also, is there a way to get the default KDE Control Center (once again, the one that ships with standard KDE)?
Sorry didn't see this question at first.
Yeah you could just open a konsole or a "run command" and write kcontrol or you could make a command for that on you kmenu, just make a new one in system for example and write kcontrol into the commandline, for admin mode use kdesu before the command.   /// Freddan

---

### Post by Dormous on 2005-10-14
[QUOTE=bailout]Have you tried opening konq and going settings/load view profile/file management? This may give you the layout you want.[/QUOTE]

Yes, as a matter of fact I have.  While this worked to solve the problem in Hoary, it does not work in Breezy.  The file management profile has already been tweaked by the developers.  This is the problem that I'm trying to find the answer to in this thread.

[QUOTE=Freddy]I'm not really sure what you meant there but if it's the regular konqueror filebrowser you're after, just open up your konqueror through a filelink and press F9 and you should get the sidebar back.
Maybe you need to save the profile for filemanegment after this.   /// Freddan[/QUOTE]

:cool: 
Ah, the F9 thing!  I've been using KDE for years now and I've never seen that command key.  That is exactly the answer I was looking for.  

On these thoughts, is there a way to remove *ALL* the Kubuntu team customizations for KDE and reset them to the KDE standard defaults?

Thanks for all your help all!

Dormous

---

### Post by Freddy on 2005-10-14
No probs, just glad I could help :).   /// Freddan

---

### Post by tagbre on 2005-10-14
[QUOTE=Freddy]I'm not really sure what you meant there but if it's the regular konqueror filebrowser you're after, just open up your konqueror through a filelink and press F9 and you should get the sidebar back.
Maybe you need to save the profile for filemanegment after this.   /// Freddan[/QUOTE]

Thank you so much for this! I went crazy yesterday trying to get my sidebar back. It's supposed to be in the menu, don't know why they took it out...

---

### Post by Jonathan2007 on 2005-10-14
I also wanted the sidebar back. The F9 did the trick but I had to save the profile after that so it would stay. Thanks.

---

### Post by Freddy on 2005-10-14
> but I had to save the profile after that so it would stay.
Hmm, yes that was what I said :).   /// Freddan

---

### Post by Marcos.Rufino on 2005-10-14
Gosh! I really don't know why the things need to be so difficult. Why the heck the Control Center was not visible in the menus?? I was without internet access and trying to change my mouse button for ages. Only some hours later, with internet access that I could discover here the Kcontrol thing.
I can't understand the reason to hidden that.

---

### Post by angrykeyboarder on 2005-10-14
[QUOTE=Marcos.Rufino]Gosh! I really don't know why the things need to be so difficult. Why the heck the Control Center was not visible in the menus?? I was without internet access and trying to change my mouse button for ages. Only some hours later, with internet access that I could discover here the Kcontrol thing.
I can't understand the reason to hidden that.[/QUOTE]

Because KDE has been planning to get rid of KControl for some time now.  Many think it's an awkward interface.

First they came out with the settings:/ thing in Konqueror (which I rather like, but many don't) and now they've also added "System Settings".

Frankly I'm for dumping Kcontrol and keeping the other two.

I wouldn't get *too* comfortable with anything though....

[http://appeal.kde.org/wiki/Appeal](http://appeal.kde.org/wiki/Appeal)

---

### Post by ykpaiha on 2005-10-14
there is as well a very easy and more comfortable way to get your system :
go to /usr/share/apps/systemview
You can from there copy any "".desktop you wish where ever you want.
I personaly don't like to go in the kiker to get a small icon with 5 choices.
so I copy the full systemview on my destkop i call (rename) it "workshop" and then i get a nicer way to handle my home trash etc...
...:razz:

It is so easy that I think to make a howto of it ...just fot fun!! lol

---

### Post by Freddy on 2005-10-14
> Gosh! I really don't know why the things need to be so difficult. Why the heck the Control Center was not visible in the menus?? I was without internet access and trying to change my mouse button for ages. Only some hours later, with internet access that I could discover here the Kcontrol thing. I can't understand the reason to hidden that.
Since Breezy, there is no more kcontrol, there's systemsettings and that you can find in the menus. Many is still used to Kcontrol though and asking for a way to still use it. There's the reason for this thread. All the things you can do inside Kcontrol you could also do inside systemsettings.   /// Freddan

---

### Post by Dormous on 2005-10-15
[QUOTE=Freddy]Since Breezy, there is no more kcontrol, there's systemsettings and that you can find in the menus. Many is still used to Kcontrol though and asking for a way to still use it. There's the reason for this thread. All the things you can do inside Kcontrol you could also do inside systemsettings.   /// Freddan[/QUOTE]

Problem with Systemsettings is that it is buggy.  When you try to return to the "control panel" interface from one of the modules, it doesn't always return you cleanly, sometimes, the controls on the page simply go away, and you have to close the window and re-launch systemsettings.

---

### Post by Freddy on 2005-10-15
> Problem with Systemsettings is that it is buggy. When you try to return to the "control panel" interface from one of the modules, it doesn't always return you cleanly, sometimes, the controls on the page simply go away, and you have to close the window and re-launch systemsettings.
Yes I agree with you 100%. Systemsettings is far worse then kcontrol ever was but remember that it's a fairly new app and hopefully it will become more stable and useful after some work on it. I belive that systemsettings layout is far more simple and handier but not yet fully operational. Maybe it was a little to early to implement it but if you want to be on the bleeding edge this types of problems will arise, you can't have it both ways.   /// Freddan

---

### Post by angrykeyboarder on 2005-10-15
[quote=ykpaiha]there is as well a very easy and more comfortable way to get your system :
go to /usr/share/apps/systemview
You can from there copy any "".desktop you wish where ever you want.
I personaly don't like to go in the kiker to get a small icon with 5 choices.
so I copy the full systemview on my destkop i call (rename) it "workshop" and then i get a nicer way to handle my home trash etc...
...:razz:

It is so easy that I think to make a howto of it ...just fot fun!! lol[/quote]

I ***love*** that theme of yours! Where might find it?

---

### Post by angrykeyboarder on 2005-10-17
[quote=pistoli]Go to your panel, right click and select "Configure panel". Go to the "Menu" icon and check the box next to "Settings". This will enable the old style control panel ion your Kmenu.[/quote] 
Where is "Settings"?

---

### Post by pistoli on 2005-10-17
I am running KDE 3.5 and have the following when I right click on the panel and select "Configure Panel"

---

