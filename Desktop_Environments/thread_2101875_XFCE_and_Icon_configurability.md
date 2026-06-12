---
title: "XFCE and Icon configurability"
date: 2013-01-05
forum: Desktop Environments
---

### Post by benett on 2013-01-05
I've been experimenting recently with CrunchBang, but am dismayed at the frustratingly difficult task of configuring which icons applications display on the (Tint2) panel and in the system tray.

There are literally countless locations for each application, and even when the old icons are replaced with the new, errors abound.

I am looking for a lightweight desktop with access to APT-GET and DEBs, and thought I would look at Xubuntu.

But I will only do this if I can be satisfied that the panel and systray icons can be configured easily and in a logical fashion.

Can anyone shed any light on how easy it is to do?

Thanks.

---

### Post by ajgreeny on 2013-01-05
You can certainly change those icons in Xubuntu to whatever you want by using the launcher properties dialog which I think you get to from a right click (I'm on ubuntu 10.04 at the moment with gnome, and can't remember exactly) and then clicking on the icon that shows in the dialog and choosing from the huge icon choice that will appear.

As an example, I have changed the blue "browser" icon in the bottom auto-hidden panel or dock to the normal orange firefox icon.

---

### Post by Bucky Ball on 2013-01-05
Yep, xfce4 is extremely configurable. Give Xubuntu a shot from the LiveCD and see what you think is probably the best bet (you can always do this rather than having to install to find out). Good luck.

---

### Post by benett on 2013-01-05
Ok I installed Xubuntu, and installed my icon set. However, the same problem exists as with Crunchbang, that some applications just aren't using the icons I want them to.

See [this picture]("http://img39.imageshack.us/img39/6743/screenshot050113235730.png") (also attached).

In this case, the 'Start' button, and 'Pidgin' refuse to use the icon theme and are using their own.

The problem I face is that I cannot find out which icons are being used, in which locations. 

I guess this problem is common to nearly all Linux distributions, but since I like many other things about Xubuntu, I might as well try to resolve this here.

Does anyone know for sure which icons are used on the taskbar/panel/system tray by applications, so that I can change them?

[EDIT: I'd also like to get rid of the MAC-style dock at the bottom and add a quick launch bar on the top panel, but can't seem to work out how. If you really want I can start a new thread but I suspect I am just missing something and this could be explained easily along with the icons thing]

[EDIT 2: The Desktop Configuration Settings files in /usr/share/applications/ indicates a file - e.g. "skype.png" but no path. How does the panel work out which skype.png to use? (I realise this is just a way of posing the same question different ways, but I wanted to show that I am doing SOME investigation! :P) ]

[EDIT 3: Could it be the .XPM files in /usr/bin/pixmaps/ ? ]

---

### Post by Bucky Ball on 2013-01-05
Right click the bottom bar and 'Remove'. That simple.

When you find Skype (or anything else) in the Applications menu simply drag it directly from there to the top bar. You shouldn't need to go changing config files. Keep it simple because xfce4 is.

You can also right click the to bar and 'Panel>Add New Items'. 

I only use a top bar, I like it simple with no bells and whistles, and that is set to autohide. A totally clean desktop. ;)

---

### Post by benett on 2013-01-06
> **benett said:**
> In this case, the 'Start' button, and 'Pidgin' refuse to use the icon theme and are using their own.

The problem I face is that I cannot find out which icons are being used, in which locations.

Update: 

I discovered that each application pretty much does whatever it wants. I know there are some people that would say this is purely because they need to keep the app compatible with a wide range of OSs and DEs, but I would seriously urge developers to, well...develop...a standard regime, at least across the Linux platform for directory structures.

In Xubuntu, even though one might choose a certain icon theme in the GUI settings, some icons will still use icons from other locations such as /usr/share/icons/hicolor.

Anyway, I changed the XFCE start icon by saving the theme's PNG as an XPM and overwriting the one in /usr/share/icons/hicolor.

I changed the tray icon for Pidgin, though I cannot locate which icon is being used on the Taskbar/Window Buttons panel for individual conversations. This is still an ugly green circle that doesnt fit with my theme.

Skype I cannot change any of the icons - panel or tray - despite having searched the entire system for files containing 'skype' and having replaced them all.

I found a few threads talking about binary cache files, and the system using these, but this is not obviously true as a rule, because I managed to change many icons just by replacing them. Maybe some apps use the cache, and others don't. It's all a bit crazy really. This is an area where Windows has a huge advantage on Linux :(

For now, I'm going to keep perservering with my investigations. If anyone can shed any light on how icons work (even just within Xubuntu, but ideally within Linux more broadly) that would be great.

[EDIT: Actually, change of plan. I installed Empathy in place of Pidgin, which plays ball with my chosen icon theme. I can then dump Skype, which is an awful piece of software anyway, and use mplayer instead of VLC. Problem solved. Enough icon shenanigans.]

---

### Post by Bucky Ball on 2013-01-06
Please mark thread as Solved to help others. ;)

---

### Post by benett on 2013-01-07
> **Bucky Ball said:**
> Please mark thread as Solved to help others. ;)

It's not solved. I gave up. I have tried a number of forums and it seems noone knows how to find out which icon is in use.

---

### Post by Bucky Ball on 2013-01-07
Sorry, my mistake. Please mark as 'unresolvable'. You make is quite clear in post #6, though, that you

[QUOTE=benett] ... installed Empathy in place of Pidgin, which  plays ball with my chosen icon theme. I can then dump Skype, which is an  awful piece of software anyway, and use mplayer instead of VLC. _***Problem  solved. ***_Enough icon shenanigans.;)[/QUOTE]

... (italics mine) so you might understand my confusion ...

---

### Post by benett on 2013-01-07
> **Bucky Ball said:**
> Sorry, my mistake. Please mark as 'unresolvable'. You make is quite clear in post #6, though, that you



... (italics mine) so you might understand my confusion ...

If you read the whole of post #6 it is clear that the original problem is not solved and that there was more than a trace of sarcasm in it. Would you ask someone to mark a post as solved if they said "I solved my problem with ndiswrapper by installing Windows 8 over the top of my previous Linux installation." ?? ;)

I will not mark this thread as solved, so that it remains open, so that if anyone with a clue as to a way of finding out which icons are in use at any given time, can respond and answer the question. I did a lot of investigation into this, investigation which could feasibly benefit someone else in the future. But equally, I dont want people NOT to add to this thread because someone has mistakenly marked it as solved.

In the mean time, I have ameliorated my problem by using different applications.

The problem, however, is not solved.

---

### Post by cottfcfan on 2013-01-07
Not sure if this will help as I am using ubuntu/unity.
but I managed to change my unity bar icons by navigating to /usr/share/applications (as root), finding the application icon i want to change, right clicking it, go to properties, click the icon & navigate to the path of the icon you want to use.
Might work the same in XFCE.

---

### Post by benett on 2013-01-07
> **cottfcfan said:**
> Not sure if this will help as I am using ubuntu/unity.
but I managed to change my unity bar icons by navigating to /usr/share/applications (as root), finding the application icon i want to change, right clicking it, go to properties, click the icon & navigate to the path of the icon you want to use.
Might work the same in XFCE.

Thanks for the suggestion, but I'm afraid it doesn't work. It obviously changes the icon in /usr/share/applications folder, but not on the taskbar/window switcher.

Thanks anyway.

---

### Post by Peripheral Visionary on 2013-01-07
You don't have to settle for whatever icons the default offers.  Let's say you want to change the icon for Firefox in your panel.  **Right-click** on the icon, then select **Properties** and then choose **Edit** (it might be a little pencil or quill icon - hover over it and it says "edit").  The selected icon appears below a dialog box. Single-left click on it and "application icons" appears. You can choose from there, OR you can go to the top of that window and choose** All Icons** rather than the "application icons" or "location icons" you are offered at first.  There will be about a zillion to choose from under "all icons."  

If you go to Synaptic Package Manager and search for "icons" you'll find other icon collections you can download.  They will be added to that huge collection to choose from.

I hope this helps a little.

---

### Post by benett on 2013-01-07
> **Peripheral Visionary said:**
> You don't have to settle for whatever icons the default offers.  Let's say you want to change the icon for Firefox in your panel.  **Right-click** on the icon, then select **Properties** and then choose **Edit** (it might be a little pencil or quill icon - hover over it and it says "edit").  The selected icon appears below a dialog box. Single-left click on it and "application icons" appears. You can choose from there, OR you can go to the top of that window and choose** All Icons** rather than the "application icons" or "location icons" you are offered at first.  There will be about a zillion to choose from under "all icons."  

If you go to Synaptic Package Manager and search for "icons" you'll find other icon collections you can download.  They will be added to that huge collection to choose from.

I hope this helps a little.

I think that you might be under the impression that I am referring to launcher icons? I am talking about the ones that appear in the taskbar/window switcher. When these are right-clicked one sees minimise / maximise etc. Its not about choosing the icons I want. I have a whole theme (AwOkenWhite) installed. Its about teaching my apps to use the icons I want. All of the suggested methods to date have not convinced them! :P

---

### Post by Peripheral Visionary on 2013-01-07
> **benett said:**
> I think that you might be under the impression that I am referring to launcher icons?

Yes, I'm afraid I was. Sorry I misunderstood.

Icons in window switching and taskbar are theme-dependent, as I understand it. Perhaps the theme you have chosen (AwOkenWhite) is incomplete or had some unsatisfied dependency.  If that theme is not in the Ubuntu repositories, perhaps you added a PPA or got it in a deb package from another source.  My best guess is that the theme is incomplete.  But I must admit, I have little experience in tweaking themes and such.  I simply added Faenza icons for my panel through a PPA.

I'm sorry I misunderstood the issue, and I'm sorry I can't offer help with the theme icon issue, other than to guess that the theme is incomplete, missing some element or dependency.

---

### Post by benett on 2013-01-07
> **Peripheral Visionary said:**
> Yes, I'm afraid I was. Sorry I misunderstood.

Icons in window switching and taskbar are theme-dependent, as I understand it. Perhaps the theme you have chosen (AwOkenWhite) is incomplete or had some unsatisfied dependency.  If that theme is not in the Ubuntu repositories, perhaps you added a PPA or got it in a deb package from another source.  My best guess is that the theme is incomplete.  But I must admit, I have little experience in tweaking themes and such.  I simply added Faenza icons for my panel through a PPA.

I'm sorry I misunderstood the issue, and I'm sorry I can't offer help with the theme icon issue, other than to guess that the theme is incomplete, missing some element or dependency.

It's OK, I appreciate you trying to help. The issue is certainly not one of incompleteness. There are icons for all of the applications, but I can't make the panel use the themed ones for these specific applications because they won't play ball. 

I've been through my system to find all the VLC, Skype and Pidgin status symbols that I can, and replaced them with the theme equivalents. Alas, these three problem applications will not play by any rules. 

If only I could find a way to discover which icons are in use when these apps are running in the window switcher!

---

### Post by Peripheral Visionary on 2013-01-08
Some themes don't play nicely with GTK3 that were fine on GTK2.  I've read elsewhere that the Redmond theme, for example, works on GTK2 but messes up on GTK3.  

If you are using an older theme on the newest version of Xfce (GTK3) then that may account for your trouble.  You may simply have to choose a different theme, or use a different (older or newer) version of Xfce4.

---

