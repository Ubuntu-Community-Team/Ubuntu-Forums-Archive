---
title: "KDE 4.0.0  is in the repo now. If u are using it, how is it working for you?"
date: 2008-01-10
forum: Desktop Environments
---

### Post by exactopposite on 2008-01-10
I installed it a few hours ago and i'm using it now. When i try to use something that needs root access  (like synaptic) it won't take my password.  I found this fix for that on the kubuntu forums ```
sudo passwd
```

Kopete doesn't blink to give any notification of incomming messages. Pidgin gives notification but the icons for it that show on the panel are screwed up. At least i know i have incoming messages tho.

During the installation I was promted to chose gdm of kdm-kde4. I chose the latter but it's not working for me. When i login i just get a blank blue screen with a terminal. From the terminal i can make gdm start and use that to log in. i need to find out how to set gdm back at the defualt for now.

I love the overall look of it, but the funtionality of the panel leavs a lot to be desired for now. I plan on using it full time and watching the improvments happen over time. If the glitches get to be too much i can go back to gnome for a while. I did have it freeze on me one time already. I left it alone for about 10 minutes to see if it would come around but it never did. The music in amarok kept playing, and the mouse would move, but i couldn't do anything at all. 

For those of you who have it installed, how's it going for you?


*EDIT*
Just to be clear, i know the official release date is 2moro. Below is a screenshot of synaptic showing 4.0.0 as the version of the kdebase-kde4 package. This is a package from the repo listed on the kubuntu website for rc2 packages right here: [http://kubuntu.org/announcements/kde4-rc2.php](http://kubuntu.org/announcements/kde4-rc2.php) 
I had kde4 rc2 installed, and today all the packages updated to 4.0.0 which should indicate that they are the release pacakges.

*SCREENSHOT*
[http://i19.tinypic.com/7x0glyt.jpg](http://i19.tinypic.com/7x0glyt.jpg)

[B]
[COLOR="Red"]FOR THOSE THAT WANT TO INSTALL THE INSTRUCTIONS ARE HERE:[/COLOR][/B]
[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

---

### Post by erginemr on 2008-01-10
I am also one of those wondering what KDE4 has to offer but are you sure that KDE version 4 has been released? My Synaptic still lists ver.3.94 for KDE4 packages and their web site gives the release date as Jan 17th-19th:
[http://www.kde.org/kde-4.0-release-event/](http://www.kde.org/kde-4.0-release-event/)

Granted they have released "release candidates", but not the final package yet I believe?

---

### Post by GeneralZod on 2008-01-10
> **erginemr said:**
> I am also one of those wondering what KDE4 has to offer but are you sure that KDE version 4 has been released? My Synaptic still lists ver.3.94 for KDE4 packages and their web site gives the release date as Jan 17th-19th:
[http://www.kde.org/kde-4.0-release-event/](http://www.kde.org/kde-4.0-release-event/)

Granted they have released "release candidates", but not the final package yet I believe?

17th-19th is the Release Party - the official release date of 4.0.0 is tomorrow (11th).  4.0.0 was tagged for packagers on the 5th, I think.

---

### Post by HeavyAl on 2008-01-10
I tried RC2 and I don't want to sound like a hater but it kinda blew chunks! But then again, it's been said numerous times that this is more of a development release so applications can start being written for it and further work can be done on the interface. It's likely not going to be totally useful until 4.1-4.2, at least for the common user (have we gotten to the point where there are common linux users? I'd like to think so ..)

All that said, I'm actually looking forward to what this thing will do once there is some spit and polish applied to it.

---

### Post by exactopposite on 2008-01-10
> **erginemr said:**
> I am also one of those wondering what KDE4 has to offer but are you sure that KDE version 4 has been released? My Synaptic still lists ver.3.94 for KDE4 packages and their web site gives the release date as Jan 17th-19th:
[http://www.kde.org/kde-4.0-release-event/](http://www.kde.org/kde-4.0-release-event/)

Granted they have released "release candidates", but not the final package yet I believe?

on the  they kubuntu site listed a repo to get the rc2 pacakges from. link: [http://kubuntu.org/announcements/kde4-rc2.php](http://kubuntu.org/announcements/kde4-rc2.php)

I already had rc2 installed ad as of today all those pacakges updated from 3.98 to 4.0.0. I'm sure if they weren't the release pacakges they would not be labeled 4.0.0


the pacakges in the gutsy repo are older, but the ones in the  repo listed on the kubuntu page linked above are 4.0.0

---

### Post by roberthr on 2008-01-10
It's awesome. Except that dualhead users will not be able to use it because of this bug: [http://bugs.kde.org/show_bug.cgi?id=152676](http://bugs.kde.org/show_bug.cgi?id=152676)

Tried it, tried workaround and it's still useless :-(

---

### Post by Frenezo on 2008-01-10
When I use GDM as a default window manager I cant choose to start KDE and when I use KDM-KDE4 as a default I only get a command-line. :confused:

---

### Post by benerivo on 2008-01-10
It works much better than 3.98.0, but it doesn't offer much to the desktop user as yet.

It doesn't seem very fast. I had read a few articles saying that it would be faster and use less memory than kde3, but it doesn't seem to. I'm sure by the time kubuntu hardy is released it will have improved so much that 4.0.0 will seem like a beta version at best.

---

### Post by RegT on 2008-01-10
Probably a stupid question, but what packages do i need to install to get kde4 up and running?

---

### Post by benerivo on 2008-01-10
[This]("http://kubuntu.org/announcements/kde4-rc2.php") is the best place for you to get kde4 running. Ignore the RC2 title, and just follow the instructions.

---

### Post by exactopposite on 2008-01-11
i guess i like living on the edge. i have upgraded to hardy AND i'm running kde4. this should be interesting

---

### Post by Sokraates on 2008-01-11
The 4.0.0-packages are indeed the final ones. They have been built and added to the repository yesterday and today. You can verify this by checking [https://launchpad.net/ubuntu/gutsy/+queue?queue_state=3&queue_text=](https://launchpad.net/ubuntu/gutsy/+queue?queue_state=3&queue_text=) So I don't thik they will rebuild everything again today. ;)

I've upgraded yesterday evening (UTC+1 here), when the majority but not all of the packages were updated. So I will probably purge everything and do a "fresh" install once the official release announcement is out. I thought about doing a clean install of Kubuntu with KDE4 from the final Live-CD but decided against this, mostly due to my the problems I expect when setting up my BCM4318 wireless.

I've been using KDE4 as my main desktop since RC2 and I quite impressed. Plasma is deffinitely the weak point, but that will change over time. The patch to easily resize the widget unforunaetly didn't make it into the final. 

I've also encountered the root-password problem, but at least you can start all those apps over the command line with sudo. I also tried kdesu and kdesudo and the password always worked. Maybe the KDE4-app expects a real root password?

A rather serious glitch I encountered involved languages. I used english before and installed the German langpack yesterday. The next thing I saw was that all keyboard shortcuts (even ALT+F2 or ALT+TAB) have stopped working. I've found the reason when I added Ctrl+F8 as a shortcut to Desktop Grid (in German "Arbeitsflächen-Gitter", I think): no shortcurt was listed and after adding Ctrl+F8 a message popped up that this shortcut was already associated with "Desktop-Grid". So the German version calls up the German names (and they work) but the shortcuts are still associated to the english names. I never even this was possible! Well, another reason to reinstall (with the langpack installed from the beginning).

---

### Post by roach of discord on 2008-01-11
I was running kde4 on hardy..and kde4 is pretty damn cool.  Hardy is absolutely bug-filled..so i'll be installing gutsy very soon..but dang, kde4 surprisingly has shaped up since the last so called "rc". I didn't have much faith in the kde 4.0 after seeing the last RC..but wow. It seems really stable and usable considering.  Still, some limits..such as the panel..but im sure that will be changed in 4.1 and greatly improved. But really..it seems very very stable (so far).

---

### Post by gurth4ng on 2008-01-11
i'm on ubuntu 7.10, can u tell me how i can install KDE4? i heared i have to add some repo to do it. As it is, my Synaptic shows 3.92 (or soemthing) as the last version of kde4base

---

### Post by roach of discord on 2008-01-11
I'm not sure about synaptic..but I followed this:

[http://kubuntu.org/announcements/kde4-rc2.php](http://kubuntu.org/announcements/kde4-rc2.php)

Follow that link and install the files it tells you to. It says rc2..but it's updated now. The files in the repo are 4.0 :).  I didn't have to add any repo or anything.

-edit

Did you try refreshing your sources on synaptic?

-edit -edit..lol

Okay, that article says gutsy-backports . Check your synaptic settings. I'm not sure how synaptic works..but it should have an option to enable the gutsy-backports repo.

---

### Post by wh0rd on 2008-01-11
[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

---

### Post by Sokraates on 2008-01-11
> **wh0rd said:**
> [http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

\\:D/ \\:D/ \\:D/

this could become the official fandance. :)

---

### Post by Gigamo on 2008-01-11
How would I go with installing/trying KDE4 on Xubuntu? Will it **** up my GDM? Since I hear you have to use KDM to hop into KDE4, and people having problems with that. I haven't used multiple *DM's yet and I'm only familiar with GDM so I'm kinda scared :D

---

### Post by Mr. Swiveller on 2008-01-11
I installed KDE4 today. It's quite a good desktop environment. The KDE media manager is much more stable than if I run KDE 3.5 and most of the functions from the 3.x branch are there. 

The taskbar I'm not too fond of - it's too big, and it doesn't hide when I run a fullscreen ap (anyone know whether / how auto-hiding can be enabled?). I also think it rather odd that I cannot hide/remove the 'add widget' applet which appears in the upper right corner. I don't run any desktop applets apart from the taskbar itself, and do not, therefore, require the widget.

All in all, I think I'll be running KDE4 more often than 3.5. I often use external harddrives, so the enhanced support for external media is a great bonus.

Swiveller

---

### Post by proalan on 2008-01-11
Fairly decent, a few quirks about most noticeably the shortcut keys not working or unassigned. 

I've always thought the taskbar have always been too big in previous kde versions and now its even bigger. 

No problems here so far

---

### Post by GeneralZod on 2008-01-11
> **Mr. Swiveller said:**
> 
The taskbar I'm not too fond of - it's too big, and it doesn't hide when I run a fullscreen ap (anyone know whether / how auto-hiding can be enabled?). I also think it rather odd that I cannot hide/remove the 'add widget' applet which appears in the upper right corner. I don't run any desktop applets apart from the taskbar itself, and do not, therefore, require the widget.


The panel was slated to have UI configurations (including auto-hide) for 4.0 but, alas, it didn't make it, so you'll have to wait until 4.1 (unless someone writes an alternative panel using libplasma first, which would not surprise me in the slightest).

The thingy in the corner will undoubtably be the subject of a lot of heated debates: aseigo wants it there; many other people don't. We'll have to see what happens when the dust has settled :)

---

### Post by snakeeyes on 2008-01-11
So is everyone sure that KDE 4 is stable enough to use, can u tell me something about the panel, I know its big but I hope it doesn't have that transparent ring around it like RC 2, and its not flat is it?

---

### Post by proalan on 2008-01-11
Maybe its just me, but kde4 doesn't seem as customizable as its predecessors. I'm unable to resize the taskbar. Right click on it only pops up 'tool tips on'.

Not a fan of the 'vista style scroll' with the kmenu.

---

### Post by Mr. Swiveller on 2008-01-11
> **GeneralZod said:**
> The panel was slated to have UI configurations (including auto-hide) for 4.0 but, alas, it didn't make it, so you'll have to wait until 4.1 (unless someone writes an alternative panel using libplasma first, which would not surprise me in the slightest).

The thingy in the corner will undoubtably be the subject of a lot of heated debates: aseigo wants it there; many other people don't. We'll have to see what happens when the dust has settled :)

Thank you for your reply, GeneralZod.

Swiveller

---

### Post by Eruaran on 2008-01-11
> **RegT said:**
> Probably a stupid question, but what packages do i need to install to get kde4 up and running?

Remove previous KDE 4 packages (if you have them), they are not compatible (apt-get remove kdelibs5 kde4base-data kde4libs-data)

Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main to your /etc/apt/sources.list

Install kde4-core, note that PPAs aren't authenticated so you will likely get a warning when installing

KDE 4 apps should appear in your KDE 3 K-menu or you can run a full session by selecting "KDE 4" from your login manager.

To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 then  and run /usr/lib/kde4/bin/startkde in the Xerphyr xterm.

([http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php))

---

### Post by diskace on 2008-01-11
I have a bug with KDE 4.0 on kubuntu 7.10

I tried modifying the desktop taskbar (for removing multiple desktop) and while playing there plasma crashed. I rebooted the pc but now the taskbar is not loading.

Any ideas ?

Thanks

---

### Post by Plasticman on 2008-01-11
Ok somehow i have managed to remove the currently open windows on my panel, anyone know how to get it back have looked everywhere with no look :(
Also how can i move plasmoids on the panel? At the moment when i add it to the panel its lumped down the bottom left and looks pretty bad with no option to move it anywhere else on the panel.

Is looking good so far. I also had the gui root password bug. Sorted it by sudo passwd and resetting in terminal.

---

### Post by metaloid on 2008-01-11
I've installed it.

Questions:
1- how to deactivate desktop event sounds?
2- how to control sound volume....?
3- It's just me.. Or is someone also experiencing permission problems when trying to save personal Desktop Settings and stuff... ?

4- Oh, yes... How the hell can I get the KControl classic confguration center. This one just sucks... Almost no configuration options at all

Best regards,
Pedro

---

### Post by Sokraates on 2008-01-11
> **metaloid said:**
> I've installed it.

Questions:
1- how to deactivate desktop event sounds?
2- how to control sound volume....?
3- It's just me.. Or is someone also experiencing permission problems when trying to save personal Desktop Settings and stuff... ?

4- Oh, yes... How the hell can I get the KControl classic confguration center. This one just sucks... Almost no configuration options at all

Best regards,
Pedro

Sound volume should be controlled via KMix. 

Bringing back KControl wouldn't help , since the reason for the missing config options is that they have not been ported yet. ... Story of KDE4.0.0's life. :rolleyes:

---

### Post by Sokraates on 2008-01-11
> **Plasticman said:**
> Ok somehow i have managed to remove the currently open windows on my panel, anyone know how to get it back have looked everywhere with no look :(

Have you tried Ctrl+F8 to view all your desktops? This only works, if you have enabled desktop effects.

> **Plasticman said:**
> Also how can i move plasmoids on the panel? At the moment when i add it to the panel its lumped down the bottom left and looks pretty bad with no option to move it anywhere else on the panel.

Open the "Add Widget"-dialog and drag the widget from there directly to the panel. Dropping it on the desktop first and dragging it on the panel afterwards won't work yet.

> **Plasticman said:**
>  Is looking good so far. I also had the gui root password bug. Sorted it by sudo passwd and resetting in terminal.

The bug report is found here:     [FONT=Arial][SIZE=2][FONT=Arial][http://bugs.kde.org/show_bug.cgi?id=154355](http://bugs.kde.org/show_bug.cgi?id=154355)[/FONT][/SIZE][/FONT]

Post your results, so that the devs will have something to work with to solve this.

---

### Post by metaloid on 2008-01-11
> **Sokraates said:**
> Sound volume should be controlled via KMix. 

Bringing back KControl wouldn't help , since the reason for the missing config options is that they have not been ported yet. ... Story of KDE4.0.0's life. :rolleyes:
This is not by all means a stable release. It should be tagged BEta... This is very disapointing. :P Also I cannot install kde4addons package...

---

### Post by Frenezo on 2008-01-11
I started the 4.0 Kubuntu LiveCD and installed it on my notebook. Here are my experiences:

+ it looks fresh

- I can't get WLAN to work
- I always got a high temperature/CPUusage cause the process "knotify4" polls about 700interupts per minute
- the default-pakagemanager isnt working, I had to install synaptic
- I can't restart kdm
- some widgets are using konquerer instead of the new default dolphin. it is really annoying to have 2 file-managers opened
- it doenst show the battery usage...

my conclusion: all those bugs after 30minutes of testing! KDE "4.0" still should be considered as a early beta.

---

### Post by Sokraates on 2008-01-11
> **Frenezo said:**
> I started the 4.0 Kubuntu LiveCD and installed it on my notebook. Here are my experiences:

+ it looks fresh

- I can't get WLAN to work
- I always got a high temperature/CPUusage cause the process "knotify4" polls about 700interupts per minute
- the default-pakagemanager isnt working, I had to install synaptic
- I can't restart kdm
- some widgets are using konquerer instead of the new default dolphin. it is really annoying to have 2 file-managers opened
- it doenst show the battery usage...

my conclusion: all those bugs after 30minutes of testing! KDE "4.0" still should be considered as a early beta.

Is the CD based on Hardy or Gutsy?

---

### Post by Frenezo on 2008-01-11
> **Sokraates said:**
> Is the CD based on Hardy or Gutsy?

gutsy

---

### Post by Plasticman on 2008-01-11
> **Sokraates said:**
> Have you tried Ctrl+F8 to view all your desktops? This only works, if you have enabled desktop effects. 

Yes ctrl+F8 works fine and is nice, whats missing though on the panel is the small tab with the running applications you can click on to bring it back into focus (hope that makes sense)

> Open the "Add Widget"-dialog and drag the widget from there directly to the panel. Dropping it on the desktop first and dragging it on the panel afterwards won't work yet.

Im dragging it onto the panel directly from the add widget dialog but wherever on the panel i place it goes to the far left hand side and cant seem to drag it back anywhere else on the panel.

> The bug report is found here:     [FONT=Arial][SIZE=2][FONT=Arial][http://bugs.kde.org/show_bug.cgi?id=154355](http://bugs.kde.org/show_bug.cgi?id=154355)[/FONT][/SIZE][/FONT]

Post your results, so that the devs will have something to work with to solve this.

Will post it as soon as its back up. Getting "bugs.kde.org is temporarily offline to celebrate KDE 4.0.0 launch." at the moment.

---

### Post by exactopposite on 2008-01-11
> **Sokraates said:**
> The 4.0.0-packages are indeed the final ones. They have been built and added to the repository yesterday and today. You can verify this by checking [https://launchpad.net/ubuntu/gutsy/+queue?queue_state=3&queue_text=](https://launchpad.net/ubuntu/gutsy/+queue?queue_state=3&queue_text=) So I don't thik they will rebuild everything again today. ;)


I've also encountered the root-password problem, but at least you can start all those apps over the command line with sudo. I also tried kdesu and kdesudo and the password always worked. Maybe the KDE4-app expects a real root password?



I found this fix on the kubuntu forums for the root password problem

```
sudo passwd
```

It'll ask for your password and ask u to confirm it. Then the problem is gone. I'll add it to the original post.

---

### Post by roberthr on 2008-01-11
A little more in depth usage of KDE4 I am getting more and more dissaponted:[LIST]
[*]kppp keeps looping on ATZ (yes, modem response is OK and configured properly)
[*]as mentioned before, you can't get around dualhead bug
[*]kdm4 does not start KDE but only X with single terminal
[*]you can't have something like quicklaunch. Tried drag'n'drop which does put an icon, but you can't do anything with it like changing icon or even start that app.
[*]lots of KDE4 apps doesn't use scrollbars which makes impossible to show whole windows (OK is usually at the bottom and you can't see it) on 1024x768.
[*]you can't control many things which we are used to
[*]better use synaptic for package manager, KDE version works horrible[/LIST]I am surprised that this is called final release. Alpha state would  be proper naming.  Why making KDE 4 which doesn't have even 1/4 functionality of KDE 3.5?

---

### Post by exactopposite on 2008-01-11
> **roberthr said:**
> A little more in depth usage of KDE4 I am getting more and more dissaponted. I am surprised that this is called final release. Alpha state would  be proper naming.  Why making KDE 4 which doesn't have even 1/4 functionality of KDE 3.5?

from a kde dev [http://aseigo.blogspot.com/2008/01/talking-bluntly.html](http://aseigo.blogspot.com/2008/01/talking-bluntly.html)

---

### Post by Plasticman on 2008-01-11
> **Plasticman said:**
> Yes ctrl+F8 works fine and is nice, whats missing though on the panel is the small tab with the running applications you can click on to bring it back into focus (hope that makes sense).

Ok got this bit sorted. Someone on a mailing list pointed out that i had missed the task manager applet. My bad doh!

---

### Post by Captain_Redbeard on 2008-01-11
> **roberthr said:**
>  Why making KDE 4 which doesn't have even 1/4 functionality of KDE 3.5?

I must agree on that kde4.0 isn't a stable release but it is released as is due to the plasma developers messing up and missing deadline after deadline, I suppose they had to release it at some point, no matter what state it is in. 
What one must remember though is that KDE4 is completely rebuilt from the ground up, It is the first of a new series and if I recall correctly KDE 3.0 was fairly buggy and crappy as well when it was released. Not to this extent but still. 
If you have to blame someone for the unstable desktop release, blame the plasma team as plasma is basically the only part which is really broken. The rest is fairly stable.
For me plasma hangs, crashes and renders weird stuff on the screen but even so I'm happy for the release :)

---

### Post by exactopposite on 2008-01-11
> **Captain_Redbeard said:**
> I must agree on that kde4.0 isn't a stable release but it is released as is due to the plasma developers messing up and missing deadline after deadline, I suppose they had to release it at some point, no matter what state it is in. 
What one must remember though is that KDE4 is completely rebuilt from the ground up, It is the first of a new series and if I recall correctly KDE 3.0 was fairly buggy and crappy as well when it was released. Not to this extent but still. 
If you have to blame someone for the unstable desktop release, blame the plasma team as plasma is basically the only part which is really broken. The rest is fairly stable.
For me plasma hangs, crashes and renders weird stuff on the screen but even so I'm happy for the release :)

and now we get to watch it grow

---

### Post by Plasticman on 2008-01-11
> **Plasticman said:**
> Im dragging it onto the panel directly from the add widget dialog but wherever on the panel i place it goes to the far left hand side and cant seem to drag it back anywhere else on the panel.

Ok found a way to hack around this in the mean time.
After adding enough widgets to the panel they will default to going to the right hand side of the screen. Can then add what you want eg clock and pager. Previous widgets which have been added as padding to take up space can then be removed and the others will stay in place at the bottom right.

---

### Post by madflyguy on 2008-01-11
I'd like to try KDE 4 without having to do a fresh install from a kubuntu image; just have it as an optional gui. Like others have said, for me Synaptic lists KDE 3.x.x, what options do I need to include with a  "apt-get install" command to force KDE v4 to install?  :KS

---

### Post by Plasticman on 2008-01-11
> **madflyguy said:**
> I'd like to try KDE 4 without having to do a fresh install from a kubuntu image; just have it as an optional gui. Like others have said, for me Synaptic lists KDE 3.x.x, what options do I need to include with a  "apt-get install" command to force KDE v4 to install?  :KS

First add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)  gutsy main to /etc/apt/sources.list.
Run sudo apt-get update
Sudo apt-get upgrade
Sudo apt-get install kde4-core

Log out and then select kde4 from the log in menu.

---

### Post by exactopposite on 2008-01-11
> **Plasticman said:**
> Ok found a way to hack around this in the mean time.
After adding enough widgets to the panel they will default to going to the right hand side of the screen. Can then add what you want eg clock and pager. Previous widgets which have been added as padding to take up space can then be removed and the others will stay in place at the bottom right.

DO you mind elaborating on this? I'm a bit confused as to exactly  what u were trying to do in the first place.

---

### Post by madflyguy on 2008-01-11
thanks for the help, I'll try it out. Doing it through Synaptic, I'll report back on how it works.
BTW I added the source "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main" to the list of repositories, reloaded Synaptic, and am now d/l'n and installing KDE4-core. Thanks plastic.

---

### Post by Plasticman on 2008-01-11
> **exactopposite said:**
> DO you mind elaborating on this? I'm a bit confused as to exactly  what u were trying to do in the first place.
I wanted to add the digital clock and pager widgets to the bottom right hand side of the panel.
When trying to add them to the panel with nothing else on it they default to being in the far left hand corner with no way to move them.
When the panel is roughly half full it defaults to adding them to the right hand side. So if you wish to add widgets to the right hand side if you add unneeded widgets to fill up some space until they default to going to the right side of the panel.
When the extra apps that where added as padding are removed the widgets which went to the right will stay there.

Hope that makes it clearer.

---

### Post by ErikTheRed on 2008-01-11
So I installed KDE4 this morning and I am liking it so far. It's a shame that plasma is in such a poor state but most other things seem to works fine. Also it seems like Oxygen is missing a few icons for certain things. Finally, the desktop effects seem awful sluggish, I'm running an 8800GTS so they should be fast I would think!

Aside from those problems everything appears to be working very well. I look forward to seeing KDE4 mature into a more polished product.

---

### Post by exactopposite on 2008-01-11
> **Plasticman said:**
> I wanted to add the digital clock and pager widgets to the bottom right hand side of the panel.
When trying to add them to the panel with nothing else on it they default to being in the far left hand corner with no way to move them.
When the panel is roughly half full it defaults to adding them to the right hand side. So if you wish to add widgets to the right hand side if you add unneeded widgets to fill up some space until they default to going to the right side of the panel.
When the extra apps that where added as padding are removed the widgets which went to the right will stay there.

Hope that makes it clearer.

ah ok. i got you now

---

### Post by kryliss on 2008-01-11
Just got KDE4 installed, I still have KDE3 installed.. I've created a new user on the system. Now, how in the heck do I get this working through VNC? my xstartup is as follows.

#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid black
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

startkde &

This only brings up KDE3, what is the command to startup kde4?

Thanx.

---

### Post by rattking on 2008-01-11
Hi 
I haven't been able to get kopete-kde4 to connect to gtalk 
I get an SSL error most likely because the QCA TLS plugin is missing
anyone have any luck with google talk support?
btw I do have qca-tls 1.0-3build1 installed as required for kopete on kde3

---

### Post by madflyguy on 2008-01-11
So far it feels REALLY slugish compared to gnome/compiz setup. Using firefox with the same tabs I just had open in gnome is taking forever, typing alone takes about a second per stroke   >_<
I understand that KDE uses its own browser, I'll try it out real quick

---

### Post by madflyguy on 2008-01-11
I've read that Firefox doesn't run well in KDE and my experience confirms it. Started using Konqueror instead which worked as expected.

KDE crashed twice on me when I was trying to make this exact post. While using Konqueror and typing this post, KDE crashed and I was left with a mouse pointer and the peach-colored solid background that one sees just after logging in. Both crashes happened just like this. I had to power down both times (there might have been another way but I'm not that savvy with Linux). So that was a short lived experience.

From what I did get to use, KDE 4 resembles Vista quite a bit. Similar UI, widgets on the right, etc...

---

### Post by Pandemic187 on 2008-01-11
Gosh...am I the only one who thinks the included window decorations are hideous? I mean, I'm very annoyed by this.

---

### Post by kgeekworking on 2008-01-11
I have one issue that I am not sure if it is a bug or done by design, but I cannot drag and drop icons between my Desktop and a Dolphin KDE4 folder.  Files and folders on my desktop are now widgets and no longer behave like files. The desktop icons will drag under the open Dolphin Windows.  Deleting the desktop file icons (widgets?) will not change the underlying file.

Does anybody know if this is the way that the new desktop is supposed to work or if this is just one of the loose ends that needs to be tied up?

I am running KDE4 installed as a separate session on Gutsy AMD64.

---

### Post by wxnker on 2008-01-11
> I've read that Firefox doesn't run well in KDE and my experience confirms it

I've been using Firefox every day with KDE for a long time. No problems at all. From my experience it runs just as fast as in Gnome.

> Does anybody know if this is the way that the new desktop is supposed to work or if this is just one of the loose ends that needs to be tied up?

I don't know about this exact issue, but keep in mind that this is the first release. We'll probably have to wait to something like KDE 4.1 to see the full potential of the new system.

---

### Post by osiris2258 on 2008-01-11
I can't find KDE4 in the repo. I proceeded exactly as on the KUbuntu site, but 'KDE4-core' is nowhere to be found in synaptic. There are just a bunch of test files.

---

### Post by getaceres on 2008-01-11
> **rattking said:**
> Hi 
I haven't been able to get kopete-kde4 to connect to gtalk 
I get an SSL error most likely because the QCA TLS plugin is missing
anyone have any luck with google talk support?
btw I do have qca-tls 1.0-3build1 installed as required for kopete on kde3

For me it's worse. When I try to add an account I get an empty list where it must show a list of protocols. 
It was working in the RC2 version but it's true that I couldn't connect to GTalk due to the missing TLS plugin.

---

### Post by Elotero on 2008-01-11
Remove previous KDE 4 packages, they are not compatible (apt-get remove kdelibs5 kde4base-data kde4libs-data) 
**Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main to your /etc/apt/sources.list ** Does this mean to type in a terminal?? Do i navigate to Sources and type this?? 

**Install kde4-core, note that PPAs aren't authenticated so you will likely get a warning when installing ** Im guessing this appears after step 2? And when i get to this step should i run: sudo apt get KDE4-core??

KDE 4 apps should appear in your KDE 3 K-menu or you can run a full session by selecting "KDE 4" from your login manager. 

**To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 then and run /usr/lib/kde4/bin/startkde in the Xerphyr xterm.** Do I run this only if i use Xubuntu?? 

 I know im a noob BUT the way this is worded just throws me off big time.

Can anyone make this a little simpler? Any assistance is always appreciated.

---

### Post by Tryke on 2008-01-11
> **Elotero said:**
> Remove previous KDE 4 packages, they are not compatible (apt-get remove kdelibs5 kde4base-data kde4libs-data) 
**Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main to your /etc/apt/sources.list ** Does this mean to type in a terminal?? Do i navigate to Sources and type this?? 

**Install kde4-core, note that PPAs aren't authenticated so you will likely get a warning when installing ** Im guessing this appears after step 2? And when i get to this step should i run: sudo apt get KDE4-core??

KDE 4 apps should appear in your KDE 3 K-menu or you can run a full session by selecting "KDE 4" from your login manager. 

**To avoid having to start a second X server for a full session install xserver-xephyr and run Xephyr :1 then and run /usr/lib/kde4/bin/startkde in the Xerphyr xterm.** Do I run this only if i use Xubuntu?? 

 I know im a noob BUT the way this is worded just throws me off big time.

Can anyone make this a little simpler? Any assistance is always appreciated.
1) If you have previously installed KDE 4 test versions, remove them with the following command (in a Terminal). Otherwise, skip to step 2.
```
apt-get remove kdelibs5 kde4base-data kde4libs-data
```

2) Open the file named "/etc/apt/sources.list" in the text editor of your choice. You'll have to be root to do this, as with all files outside of /home. Try typing this in a terminal:
```
sudo gedit /etc/apt/sources.list
```
Add the following text to the bottom of the file:
```
# KDE 4 Repository
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```

3) Run the following commands:
```
sudo apt-get update
sudo apt-get install kde4-core
```
Ignore any warnings about unauthorized packages.

4) At your login screen, go to the Options and change your "Session" to KDE 4. Ignore the Xephyr instructions unless you want to run KDE 4 inside a window on top of your current environment.

Note: I haven't actually installed KDE 4 yet (still at work), I've just embellished on the instructions provided on the Kubuntu website.

---

### Post by wvmac on 2008-01-11
type   "sudo gedit /etc/apt/sources.list"  in the terminal (without the quotes). enter password

in the gedit window that opens paste "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main" (no quotes) at the bottom of the list. hit enter (sometimes you will get a complaint about no new blank line at the end of the sources.list if you don't create one) then save file.
close gedit
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kde4-core
or if no kde4-core listed
sudo apt-get install kdebase-workspace kdebase-kde4 kdebase-runtime


*beat me to the post. the answer above is better

---

### Post by Rob500 on 2008-01-11
I installed KDE 4.0 earlier and I have to say it is working very well indeed, very smooth operation, very quick and it actually uses less memory than KDE 3 did. I like the sounds and integrated desktop effects (although I still use GL Desktop for the cube).

My desktop: [http://i130.photobucket.com/albums/p242/2007dmc122007/JanuaryDesktop2.jpg](http://i130.photobucket.com/albums/p242/2007dmc122007/JanuaryDesktop2.jpg)

---

### Post by andrewsomething on 2008-01-11
A few things... So, I've got a KDE 4 session up and running using the PPA repo, but there are ofcourse some issues.

First, where do I file a bug against packages from the PPA repo?

Also, has anyone been able to enable the Kwin desktop effects? When I do so through system settings>desktop>desktop effect, I get no errors, but they don't actually seem to be enabled.

---

### Post by Rob500 on 2008-01-11
> **andrewsomething said:**
> Also, has anyone been able to enable the Kwin desktop effects? When I do so through system settings>desktop>desktop effect, I get no errors, but they don't actually seem to be enabled.

I managed to enable them the way you said, there should be no problems. Have you tried restarting?

---

### Post by Pandemic187 on 2008-01-11
Can the Emerald Theme Manager be used on KDE4? Because I believe imported themes are supposed to be in .tar.gz format; if I'm right, it's not recognizing themes in the file browser when in KDE.

And here's a bug...I've noticed that sometimes when a drag an icon on the desktop, the wallpaper will actually drag along with it, exposing a white space behind it.

And...call me crazy, but I can't figure out how to delete things from the desktop. Am I missing something really obvious here?

---

### Post by andrewsomething on 2008-01-11
> **Rob500 said:**
> I managed to enable them the way you said, there should be no problems. Have you tried restarting?

I've restarted X, but I haven't done a full reboot. I'll try that.

BTW: Compiz work under Gnome, so it shouldn't be any kind of video card issue.

So how do you like them? How do the compare to compiz?

EDIT: Nope, full reboot didn't do it either. Any ideas?

---

### Post by kag9000 on 2008-01-11
> **andrewsomething said:**
> I've restarted X, but I haven't done a full reboot. I'll try that.

BTW: Compiz work under Gnome, so it shouldn't be any kind of video card issue.

So how do you like them? How do the compare to compiz?

Pretty badly, the desktop effects are awfully laggy (using a 7600GT) so much so that kde4 is pretty much useless with it running.

---

### Post by Rob500 on 2008-01-11
> **andrewsomething said:**
> I've restarted X, but I haven't done a full reboot. I'll try that.

BTW: Compiz work under Gnome, so it shouldn't be any kind of video card issue.

So how do you like them? How do the compare to compiz?

I do like the desktop effects, especially exploding windows, but I still have Compiz (GL Desktop) installed for the cube.

Runs quite well, I've got loads of effects enabled and I only have on board graphics currently at 64MB. I might upgrade the RAM and crank up the GPU to 128MB for a bit of extra oomph.

> **Pandemic187 said:**
> Can the Emerald Theme Manager be used on KDE4? Because I believe imported themes are supposed to be in .tar.gz format; if I'm right, it's not recognizing themes in the file browser when in KDE.

And here's a bug...I've noticed that sometimes when a drag an icon on the desktop, the wallpaper will actually drag along with it, exposing a white space behind it.

And...call me crazy, but I can't figure out how to delete things from the desktop. Am I missing something really obvious here?

Hmm, I don't have the problem with the wallpaper dragging, low on resources maybe?

I have no idea how to delete things from the desktop the way we're used to. What I did was use Dolphin and delete them from the desktop folder (/home/myname/desktop). There must be a quicker and simpler way though.

---

### Post by usien on 2008-01-11
well i have been a sincere gnome user since i have started using linux (more than a year now).i did try kde a lot and tryed to adjust but i couldn't let go the feeling that gnome was better.having said that i have been anxiously waiting for kde 4 and have been trying the betas.i have to say that i love it to the every bit.as far as i am concerned it totally throws gnome out of the window where it stands today.unless gnome people catch up with kde 4, kde 4 is bound to become the linux industry standard soon.the linux revolution is already here...

---

### Post by GeneralZod on 2008-01-11
> **Pandemic187 said:**
> 
And here's a bug...I've noticed that sometimes when a drag an icon on the desktop, the wallpaper will actually drag along with it, exposing a white space behind it.


This is a bug that was fixed a few days back, but not in time for 4.0.0 tagging.  

> 
And...call me crazy, but I can't figure out how to delete things from the desktop. Am I missing something really obvious here?

How do you mean exactly? The red cross should remove widgets.

> **kag9000 said:**
> Pretty badly, the desktop effects are awfully laggy (using a 7600GT) so much so that kde4 is pretty much useless with it running.


Can you try this and see if it makes a difference?

[http://dot.kde.org/1200050369/1200083018/1200090433/](http://dot.kde.org/1200050369/1200083018/1200090433/)

If so, I'll add it to 

[http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Why_is_KWin.27s_3D_stuff_slower_than_Compiz_Fusion.3F](http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Why_is_KWin.27s_3D_stuff_slower_than_Compiz_Fusion.3F)

---

### Post by MacUntu on 2008-01-11
Too buggy for a major release imho (crashes, focus stealing, weird default font settings, laggy even on newer hardware). Why didn't they wait until it's more polished and properly tested? Nowadays everything seems to get rushed...

I hope 4.1 will be the real 4.0 and I finally can abandon the millstone gnome.

---

### Post by Rob500 on 2008-01-11
> **GeneralZod said:**
> How do you mean exactly? The red cross should remove widgets.

Nope, icons are also displayed as widgets and return whenever you reboot.



After reading some of the replies, am I the only person who's not had any problems whatsover with KDE 4.0?

---

### Post by exactopposite on 2008-01-11
> **Rob500 said:**
> 
After reading some of the replies, am I the only person who's not had any problems whatsover with KDE 4.0?

the rest of those people are too busy using it to talk about it lol

---

### Post by usien on 2008-01-11
> **Rob500 said:**
> Nope, icons are also displayed as widgets and return whenever you reboot.



After reading some of the replies, am I the only person who's not had any problems whatsover with KDE 4.0?

i have installed kde 4 over ubuntu (gnome) 7.10 and i havn't had any major problems at all.i have a few very minor problems which i think are because of gnome, so i will get rid of it and install kde 4 over kubuntu 7.10.i do have a few reservations about konquror as a web browser though.

---

### Post by SunnyRabbiera on 2008-01-11
dang why dont people wait till things are stable??????

---

### Post by GeneralZod on 2008-01-11
> **Rob500 said:**
> Nope, icons are also displayed as widgets and return whenever you reboot.


Oh, you mean the contents of ~/Desktop? Yeah, that's a known issue, I think.  The whole "~/Desktop on your Desktop" is something that doesn't really fit well with Plasma (aseigo, in particular, strongly dislikes the idea of it), and it shows.  I'd expect this to be *somewhat* better with future releases.

> After reading some of the replies, am I the only person who's not had any problems whatsover with KDE 4.0?

Sounds like you've had at least one ;)

> **SunnyRabbiera said:**
> dang why dont people wait till things are stable??????

Blessed be the Early Adopters, for they shall clear a path for the rest of us :)

---

### Post by okpmichelangelo on 2008-01-11
I'm running it in Parallels. I had installed Ubuntu 7.10 a few weeks ago and Gnome works great but I can't connect to the internet in KDE 4. Ugh.

---

### Post by Rob500 on 2008-01-11
> **usien said:**
> i have installed kde 4 over ubuntu (gnome) 7.10 and i havn't had any major problems at all.i have a few very minor problems which i think are because of gnome, so i will get rid of it and install kde 4 over kubuntu 7.10.i do have a few reservations about konquror as a web browser though.

I installed it on Kubuntu 7.10 and I use Firefox as the web browser, no need for Konqueror :)

> **okpmichelangelo said:**
> I'm running it in Parallels. I had installed Ubuntu 7.10 a few weeks ago and Gnome works great but I can't connect to the internet in KDE 4. Ugh.

1. Alt+F2
2. Type "knetworkmanager" without the "
3. Connect

It should work..

---

### Post by Serpentus on 2008-01-11
Please don't think that I feel mad and disapprove KDE developers work and everything, I know these things happen and that they put there best work to this and make this at their free time so all of us can enjoy. So yeah, I'll be patient cause I know they will get a great product, they have proven to be good at what they do.

Hope to see a better kde in the next update. I know this is the first 'stable' version and almost always with the first versions there are lots of problems.

I don't know, all in all this looks like a temporal reverse in kde, I think this should have been marked as Beta3. But oh well, with all the bugs people are going to open they are going to improve very fast and kick the butt of every Window manager out there because this looks very promising once the bugs are fixed!

Here are my problems (Maybe this happens because I still have kde3 installed??):

Fist of all, You need a MEGA PC to get things working fast (I have an AMD 64 2.2GHz, 1.5 GB RAM, and an ATI x1650 with 256MB maybe the ATI is the problem, cause the drivers suck BIG time). I can't listen to my music and navigate at the same time, IT IS SO SLOW!, I can just do one thing at a time, forget about multitasking! Hell, even the mouse moves with lots of jumps.

The biggest problem I see is that the kde configuration is to basic, I would of like something like previous versions. I would of like to see something similar to kcontrol (Maybe I can't find it, can someone tell me if there is one?)

The panel has a huge bug, It has disappear and can't get it back. So I'm currently unable to use KDE4, my experience lasted like 30 min. before this happened T_T. ii also looked around for an option to hide the panel automatically, but to my surprise, didn't find it anywhere, you can't even right click the panel, it feels like they chained down the configs.

The start menu, is horrible, to difficult to navigate and can't make it bigger. Would love to see an option to let it like it was in KDE 3.x

Can't sort the icons on my desktop by type, and there is also a Bug, if you put your mouse over an icon and then take it off, sometimes the "square" with options won't go away, and if you sort your icons with that "square" on, it gets all messy.

Konquest, the game, is a big NO! this game was great, now it isn't. I liked how the properties of the planets were shown at the left, AND there is also a bug, even if you select to play against a computer player, it plays like a human.

Get a crash when trying to open most of the apps.

Ok, that was my short experience before the panel disappeared. Maybe all this happens because I still have KDE 3?

Even if what I'm going to type next sounds ironic, It isn't, it's the truth, [cause I know it is really hard to write a program, If I knew how to program better (just know basic C and Assembly, not even C++ T_T) I would help this great community. Unfortunately I only can fill up bug reports T_T and seems like I'm only complaining about things.]

Keep up the great work!!! Keep kicking butts like you've always done! =D
Serpentus

---

### Post by Rob500 on 2008-01-11
I just found a neat little feature with the tooltips you get when you hover over the application in the taskbar - the tooltips are live and displays everything in that application in real-time, I've just been typing a document in OpenOffice while watching a miniature Youtube video in the tooltip :)

---

### Post by okpmichelangelo on 2008-01-11
> **Rob500 said:**
> 



1. Alt+F2
2. Type "knetworkmanager" without the "
3. Connect

It should work..

I don't get anything when i type knetworkmanager in.

[http://i17.tinypic.com/72v03nl.png](http://i17.tinypic.com/72v03nl.png)

---

### Post by dasunst3r on 2008-01-11
I gave KDE4 a shot when I used openSUSE for one day.  If you are facing problems with KWin being choppy with effects, go into the settings (I don't remember where) and try unticking "Sync to VBlank."  It made things faster for me.

As for my impression, it left me with lots of things to be desired for, so I'm leaving it to bake for a few more months.

---

### Post by Rob500 on 2008-01-11
> **okpmichelangelo said:**
> I don't get anything when i type knetworkmanager in.

[http://i17.tinypic.com/72v03nl.png](http://i17.tinypic.com/72v03nl.png)

In a terminal type:

```
sudo apt-get install knetworkmanager
```

Then give it a shot :)

EDIT: I started with Kubuntu anyway so I had it under KDE 3, not sure about GNOME.

---

### Post by Case_f on 2008-01-11
> **GeneralZod said:**
> 
Can you try this and see if it makes a difference?

[http://dot.kde.org/1200050369/1200083018/1200090433/](http://dot.kde.org/1200050369/1200083018/1200090433/)

If so, I'll add it to 

[http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Why_is_KWin.27s_3D_stuff_slower_than_Compiz_Fusion.3F](http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Why_is_KWin.27s_3D_stuff_slower_than_Compiz_Fusion.3F)

It DID help somehow here, but nothing really major, still quite unusable. AMD64 3000+, Gutsy 64bit, 7600GS, 1.2GB RAM. Thanks anyway.

---

### Post by Pandemic187 on 2008-01-11
> **benerivo said:**
> [This]("http://kubuntu.org/announcements/kde4-rc2.php") is the best place for you to get kde4 running. Ignore the RC2 title, and just follow the instructions.
Thank you for posting that link for about the third time or so in this thread.

Anyway, I'm back to good ol' GNOME. It seems like there are far too many bugs to make using KDE4 realistic right now. Heck, I even read an article about a month ago saying it was being released too soon. Guess whoever wrote that article was right, because there are just too many problems with it. Besides, I have plenty of eye candy going on my GNOME desktop with Compiz and Beryl Emerald themes. Guess I'll just wait until KDE4 is a little bit more ready for consumers...

---

### Post by okpmichelangelo on 2008-01-11
> **Rob500 said:**
> In a terminal type:

```
sudo apt-get install knetworkmanager
```

Then give it a shot :)

EDIT: I started with Kubuntu anyway so I had it under KDE 3, not sure about GNOME.

Yep that did it! I was able to download it in Gnome and it worked in KDE. Thanks.

---

### Post by sports fan Matt on 2008-01-11
It doesnt.  It boots up then automatically restarts (displaying like where a tv station is off the air and all u see is snow)..I cant even get it to where I can click on a program to launch it..Any idea why it would auto restart but gnome woks perfectly..? KDE 3 worked when I had it....Any ideas?

---

### Post by okpmichelangelo on 2008-01-11
ok now the display is all ****** up:

[http://img.skitch.com/20080112-p2uemd9s193xd2bke11439jq3j.jpg](http://img.skitch.com/20080112-p2uemd9s193xd2bke11439jq3j.jpg)

lol

---

### Post by Rob500 on 2008-01-11
> **okpmichelangelo said:**
> ok now the display is all ****** up:

[http://img.skitch.com/20080112-p2uemd9s193xd2bke11439jq3j.jpg](http://img.skitch.com/20080112-p2uemd9s193xd2bke11439jq3j.jpg)

lol

Just click defaults, then apply :)

---

### Post by Rob500 on 2008-01-11
> **sox fan Matt said:**
> It doesnt.  It boots up then automatically restarts (displaying like where a tv station is off the air and all u see is snow)..I cant even get it to where I can click on a program to launch it..Any idea why it would auto restart but gnome woks perfectly..? KDE 3 worked when I had it....Any ideas?

Can you get as far as the logon screen?

---

### Post by sports fan Matt on 2008-01-11
yeah, i can do that, enter my login and password and hit enter then the above happens..i select use for this session only then its like i said where a TV goes snowy..etc

---

### Post by funnypanks on 2008-01-12
i installed kde4 and in 5 minutes i was briskly reminded why i moved to gnome 2 years ago, after using kde for 1 day back then lol. gnome ftw!!!!
can someone be a gnome fanboy?

---

### Post by Phil Urich on 2008-01-12
I am also getting the bug where the panel is missing, is there any way to re-add it to the desktop? It doesn't appear to be with the other widgets....

---

### Post by exactopposite on 2008-01-12
> **funnypanks said:**
> i installed kde4 and in 5 minutes i was briskly reminded why i moved to gnome 2 years ago, after using kde for 1 day back then lol. gnome ftw!!!!
can someone be a gnome fanboy?

i'm a gnome user myself. basing your opinions of kde on this release of kde4 isn't exactly giving it a fair shake. It's not ready for primetime, and the kde people were clear that this would be the case. They just built the entire DE from the ground up. Now that it's out there and some people are using it and finding bugs, it should improve quickly. This is one instance where KDE is showing innovation, and that is good for the open source community as a whole.

If you prefer gnome, there is nothing wrong with that. I have been a gnome guy for a long time myself. However, I must ask, when was the last time gnome did something this big? This isn't an occasion to bash KDE for releasing something in the condition they said it would be in. This is a time to witness the birth of something that will benefit the entire linux desktop userbase.

---

### Post by Pandemic187 on 2008-01-12
> **exactopposite said:**
> i'm a gnome user myself. basing your opinions of kde on this release of kde4 isn't exactly giving it a fair shake. It's not ready for primetime, and the kde people were clear that this would be the case. They just built the entire DE from the ground up. Now that it's out there and some people are using it and finding bugs, it should improve quickly. This is one instance where KDE is showing innovation, and that is good for the open source community as a whole.

If you prefer gnome, there is nothing wrong with that. I have been a gnome guy for a long time myself. However, I must ask, when was the last time gnome did something this big? This isn't an occasion to bash KDE for releasing something in the condition they said it would be in. This is a time to witness the birth of something that will benefit the entire linux desktop userbase.
Good point here. I will, however, say that I have in my experience of Linux preferred GNOME to KDE because of the simplicity of it. I find that those who use KDE tend to say their reason for doing so is because of the configurability of it. That's very understandable - and let's be honest, any distribution of Linux is more customizable than Windows, and probably moreso than Mac OS as well. Still, I find GNOME to be very customizable, and for some reason KDE just never clicked with me. I could never quite explain it, but I've just always liked GNOME better.

Still, KDE4 shows definite promise, and I have already tried it out because any major advancement in the world of Linux deserves a look-see, at the very least. There are bugs, but those will be ironed out with time. When they are, KDE4 will really be a major improvement, really setting the bar high for the next release of GNOME.

---

### Post by phinn on 2008-01-12
So far I hate to say it but I'm disappointed.  It crashed on my once (like came completely unresponsive) when I was trying to change the theme.

Most of the icons don't have actual icons they have question marks.

Also its just all around ugly, the big black bar at the bottom I haven't figured out how to customize. Then the cheap Windows Vista rip-off start menu thing is just not good or innovative. If your gonna rip-off something at least ripoff something like Mac OS X.

Its also currently using quite a bit of RAM, I thought it was supposed to be a lot less?

The performance however is pretty snappy.

The interface has a ton of potential and in some areas looks nice but it just feels unpolished.

Oh and some of the apps aren't KDE4 (QT4) yet obviously, thats one of the biggest things, like Amarok for example.

KNetworkManager wouldn't start and connect to the wireless (if there is even one there) so I loaded the KDE3 one and it worked.

Hopefully they'll work out some of the early stuff by the time Kubuntu 8.0x comes out and it'll work.

I'm guessing by KDE 4.1 it'll be ready for prime time. But 4.0 is disappointing so far.

---

### Post by exactopposite on 2008-01-12
> **Pandemic187 said:**
> Good point here. I will, however, say that I have in my experience of Linux preferred GNOME to KDE because of the simplicity of it. I find that those who use KDE tend to say their reason for doing so is because of the configurability of it. That's very understandable - and let's be honest, any distribution of Linux is more customizable than Windows, and probably moreso than Mac OS as well. Still, I find GNOME to be very customizable, and for some reason KDE just never clicked with me. I could never quite explain it, but I've just always liked GNOME better.

Still, KDE4 shows definite promise, and I have already tried it out because any major advancement in the world of Linux deserves a look-see, at the very least. There are bugs, but those will be ironed out with time. When they are, KDE4 will really be a major improvement, really setting the bar high for the next release of GNOME.

As stated above, I use gnome. I have prefered it over KDE for a long time now.  I was really looking forward to this KDE release though. It will replace gnome on my desktop when it's a bit more stable. The ability to make such a choice is one of the reasons i use linux. As of now my custom gnome/compiz/awn setup is serving me very well. The first time i tried linux, i started with kde and i liked it pretty well. I tried gnome to give it a fair shake, and ended up liking it better. 

KDE is showing real innovation with the new version. It's a new way of doing things. It's good to shake things up a bit sometimes. Even users of gnome or other DE/WM setups can benefit from it because devs on other projects can learn from it, or get new ideas from it for example. Also of note with kde4 is that they are porting apps to windows and osx, which can expose more users to open source and get more people interested and involved. That's also good for the whole community.

There are some gnome users who would never use kde and vice versa. I try to be more open minded about it myself, but the competition can't hurt.

---

### Post by andrewsomething on 2008-01-12
I really wish that some one could tell me where bugs should be filed against the Kubuntu PPA repo's packages. It's not the normal Ubuntu repo so I shouldn't file them against the Ubuntu Hardy packages. Many of the issues I'm having seem to be with the distro not with KDE 4 its self. For instance, KPackageManager using su instead of sudo. I don't have a root password, I use Ubuntu...

---

### Post by Tanker Bob on 2008-01-12
I've been using KDE 3.5.x and find 4.0 interesting but obviously a work in progress. The worst problem is the loss of the task bar at the bottom in a nasty crash. Had to uninstall 4.0, purge its settings, then reinstall to get the task bar back. The icons on the taskbar are huge and the default menu takes too many clicks to get to apps. Lots of other annoying issues. Hopefully 4.1 smooths out the desktop. It definitely has possiblities.

Does anyone know how to get the taskbar back after the window handler crashes without uninstalling, purging the settings, then reinstalling kde 4.0?

---

### Post by thamood on 2008-01-12
well..i installed it didnt last 10 mins without the 1st crash. plus when i turned on the effects it became reaaaaaaaaaaaallllly slow ( i have a 3 GHZ and 1500 MB RAM and and Nevidia 5750 PCX) plus it really looks a lot like vista and i hate VISTA....so after spedning one hour with KDE 4.0 i went back to my beloved clean GNOME desktop.

but thanks for the KDE team for the gr8 effort hope you resolve all the probelms..

---

### Post by Starlight on 2008-01-12
It seems to me that almost none of the KDE 4 apps have icons... there's always a blank space next to them in the K menu. Does anyone else have that problem?

---

### Post by MacUntu on 2008-01-12
Occasionally. Sometimes there are icons, sometimes there aren't. :-/

---

### Post by snakeeyes on 2008-01-12
I just installed it and found many bugs. I could list the bugs I encountered if u like!

---

### Post by leftfield technology on 2008-01-12
I'm not really sure what people are expecting.. I'm been a regular gnome user since I started linux - I didn't like the look and feel of kde to start with. I've also been helping develop the leftdesk OS for our upcoming range of pcs, thin clients and servers based around gnome/ubuntu core. 
We had a look at the RC versions and weren't overly impressed, but the latest release is promising.. to the point that we now have kde4 and gnome development machines running side by side.
What KDE4 lacks at the moment are finished apps. There are also a few wrinkles to iron out in the UI, however we're excited enough to consider holding off our initial release by a month or so to enable kde4 to get into shape (The current plan is april/may)
KDE4 isn't really fully ready as a mature desktop just yet.. It won't be for a while. It's like upgrading to Hardy now and expecting everything to be fully functional.


Personally.. Amarok2 could be the clincher.

---

### Post by julian67 on 2008-01-12
tried the kubuntu kde4 live CD.....definitely not one to install but I guess it's just a showcase, not a release intended for use. Looks nice but massive lack of functionality atm..... no front end to network manager, no package manager (requires Smart to be installed....couldn't do it cos no network manager front end means no wpa means no network), and was surprised at how many applications are not ready/available from the CD...no digikam for example.  Dolphin looked like a decent file manager, Konqueror was the usual crippled Kubuntu version (easily fixed). It was very quick for a live CD and applications opened quickly, particularly Konqueror.  I'll have another look when Hardy is released....meanwhile Xfce rules :)

---

### Post by Pandemic187 on 2008-01-12
I'll agree with network problems as well. The way I get my network to work on KDE4 is I start up a GNOME session, logout, then login to KDE4, because my network connectivity that I had in GNOME will transfer over to KDE.

---

### Post by Starlight on 2008-01-12
It seems that there's no "create new folder" option in KDE4's Dolphin... :shock:

---

### Post by aj_ on 2008-01-12
It is really, really slow. Feels like running a liveCD. I also wasn't too impressed with Adept's constant crashing. And the menu is absolutely the worst UI design I have ever seen. If you wanted to mimic Vista, at least you could have done it right and added the fold/unfold feature on a single menu instead of forcing us to navigate back and forth through a labyrinth of nested menus.

I really appreciate the enormous effort put into this, but it shouldn't have been released to the public in this state.

---

### Post by julian67 on 2008-01-12
agree that the menu sucks very very badly.  You have to already know where things are to be able to find them....doh! Is like walking in a maze.

---

### Post by rune0077 on 2008-01-12
> **julian67 said:**
> agree that the menu sucks very very badly.  You have to already know where things are to be able to find them....doh! Is like walking in a maze.

Actually, the menu is what I like about it. This is my first try at KDE, but the menu seems much better than Gnome (please don't shoot me). You just need to know the name of the app, then type it in the search field and it pops up. No need to navigate at all.

---

### Post by julian67 on 2008-01-12
> **rune0077 said:**
> Actually, the menu is what I like about it. This is my first try at KDE, but the menu seems much better than Gnome (please don't shoot me). You just need to know the name of the app, then type it in the search field and it pops up. No need to navigate at all.

I'm familiar with the slab menu from when I used opensuse and it hasn't improved even a little. Yes you need to know the name of the app or exactly which tree branch to go searching down to find it.  A good menu should make it easy to find what you need without you knowing the exact name, and more importantly without sending you down a series of dead ends because the menu doesn't expand. The Gnome menu is better, though I don't use it, preferring Xfce...whose menu is ideal imo....right click on the desktop and then just hovering the mouse over the categories reveals all. You get to any application on the system very easily, no hunting for the correct path, 2 clicks.  The KDE4 slab has the disadvantages of both gui and cli in one awful mess.

---

### Post by frenchtomytoast on 2008-01-12
Well, as everyone as said it is a bit buggy. 

That said, I am really enjoying the new look. Great job everyone who worked on it.

I have one question. Screwing around with widgets I managed to remove my clock from next to the system tray. Whenever I add it back, it just wants to hang out on the desktop. Solution for getting it back next to the system tray?

---

### Post by wilberfan on 2008-01-12
My impressions so far:

It definitely feels incomplete. 

I've been having the missing-icon-in-the-menu thing.

Swiftdove often crashes on startup.

Running swiftweasel will occasionally give me this weird, gray, semi-transparent box in the upper-left corner of my monitor.  It will have a frozen capture of whatever was under it when it rendered. (I'm beginning to suspect it's the 'shadow' of a cookie pop-up notification window or something?  Only, the window itself it not displaying--and maybe I'm seeing the drop shadow?

Firefox and Thunderbird are kind of 'ugly' now...

All my fonts are REALLY small.  On everything (except the digital clock on the taskbar!)

Icons in the systray sometimes get the right 1/3 cut off.

I've experienced the drag-a-file-to-the-desktop-but-only-get-this-weird-widget thing.

Can't figure out how to put a KMix icon on the taskbar yet.  My volume-control keyboard shortcut worked for awhile...but doesn't anymore.

It seems to load very quickly, and seems to be peppy enough on my AMD64x2 Gutsy install.

I always like playing with new apps, etc, but this doesn't feel ready-for-prime-time yet...  I don't really mind, at this point, though... It will be fun watching it improve!  :)

---

### Post by megamania on 2008-01-12
> **rune0077 said:**
> Actually, the menu is what I like about it. This is my first try at KDE, but the menu seems much better than Gnome (please don't shoot me). You just need to know the name of the app, then type it in the search field and it pops up. No need to navigate at all.
That sounds like "I like the menu because I don't have to use it".  :-)  I'd say you like the search feature.

I'm a (k)ubuntu user (i.e. I have gnome, kde 3 and kde 4 on the same computer), but *that* menu system is terrible... Looks nice, but it's completely unusable.

---

### Post by rune0077 on 2008-01-12
> **megamania said:**
> That sounds like "I like the menu because I don't have to use it".  :-)  I'd say you like the search feature.


That is probably exactly true. Menus always strike me as being fairly annoying, and if someone could make me a system that didn't require them at all, while still being functional, I would be sold.

---

### Post by stucky on 2008-01-12
> **rune0077 said:**
> if someone could make me a system that didn't require them at all, while still being functional, I would be sold.

TTY3 is perfectly funtional.

I've tried 4 now. Eyecandy is nice. I'd rather have functionality and customizability. Going back to straight Debian with fluxbox now.

---

### Post by ferd on 2008-01-12
I installed it this morning. I stopped using it because it would not accept my password to open Synaptic. Also, it does not have enough configuration options to be useful to me.

---

### Post by adhesivesynergy on 2008-01-12
> **Pandemic187 said:**
> I'll agree with network problems as well. The way I get my network to work on KDE4 is I start up a GNOME session, logout, then login to KDE4, because my network connectivity that I had in GNOME will transfer over to KDE.

I have the same problem, but its easier to fix, instead of going through all the trouble of entering another session, exiting, and then going back to KDE4 you can just enter in a command prompt the command for either the GNOME or KDE3 networkmanager frontends

GNOME: nm-applet or if that doesn't work use network-admin and restart your network manually
KDE3: knetworkmanager

I installed KDE4 on top of kubuntu so I just have my session autostart knetworkmanager and I"m good to go, I'm sure you could do the same.

This also works like a charm for using wms like say openbox if you are feeling too lazy to manually configure the network (like me) then just pop one of these into your autostart and you're set

---

### Post by rattking on 2008-01-12
> **rattking said:**
> Hi 
I haven't been able to get kopete-kde4 to connect to gtalk 
I get an SSL error most likely because the QCA TLS plugin is missing
anyone have any luck with google talk support?
btw I do have qca-tls 1.0-3build1 installed as required for kopete on kde3

Hey again 
I got bored and compiled libqca2-plugin-ossl from hardy for gutsy amd64.. more info on that package here
[http://packages.ubuntu.com/hardy/libs/libqca2-plugin-ossl](http://packages.ubuntu.com/hardy/libs/libqca2-plugin-ossl)

gtalk works now
warning.. I don't know much about building debs and so I'm not really sure how apt will handle upgrading this package when an official libqca2-plugin-ossl appears
so I dont recommend installing this unless you're comfortable using dpkg to fix any conflict or remove this package first

hope this helps

---

### Post by Elotero on 2008-01-12
> **wvmac said:**
> type   "sudo gedit /etc/apt/sources.list"  in the terminal (without the quotes). enter password

in the gedit window that opens paste "deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main" (no quotes) at the bottom of the list. hit enter (sometimes you will get a complaint about no new blank line at the end of the sources.list if you don't create one) then save file.
close gedit
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kde4-core
or if no kde4-core listed
sudo apt-get install kdebase-workspace kdebase-kde4 kdebase-runtime


*beat me to the post. the answer above is better
Its installing. Muchas gracias amigo. This is working nice.:guitar:

---

### Post by Pandemic187 on 2008-01-12
> **adhesivesynergy said:**
> I have the same problem, but its easier to fix, instead of going through all the trouble of entering another session, exiting, and then going back to KDE4 you can just enter in a command prompt the command for either the GNOME or KDE3 networkmanager frontends

GNOME: nm-applet or if that doesn't work use network-admin and restart your network manually
KDE3: knetworkmanager

I installed KDE4 on top of kubuntu so I just have my session autostart knetworkmanager and I"m good to go, I'm sure you could do the same.

This also works like a charm for using wms like say openbox if you are feeling too lazy to manually configure the network (like me) then just pop one of these into your autostart and you're set
That's true, but the fact that it's necessary to do that, and that this sort of functionality isn't already integrated, shows how incomplete KDE4 is right now.

---

### Post by tmth on 2008-01-12
I am one of the unfortunate ones that experience bug #154118.  Its the one that crashes plasma every time you start an application from the menu.  The only way to get it back on is by manually running plasma in whatever command input place (console or Alt-F2 dialog for example).

According to [https://bugs.kde.org/show_bug.cgi?id=154118](https://bugs.kde.org/show_bug.cgi?id=154118), its their coding problem and apparently its already fixed in svn.  But by the time that svn stuff gets into stable release its going to be months.  So am i suppose to see my desktop crash until they decide its time to release another stable version???  How is this bug process suppose to work?

Overall, KDE has been generally good with me for past few years, but only because i have enough patience to ignore endless crashes.  Is it just me?? Will there ever be release of ANYTHING that will actually work 100%.

---

### Post by uzd4ce on 2008-01-12
> **exactopposite said:**
> 

During the installation I was promted to chose gdm of kdm-kde4. I chose the latter but it's not working for me. When i login i just get a blank blue screen with a terminal. From the terminal i can make gdm start and use that to log in. i need to find out how to set gdm back at the defualt for now.

I'm having the same problem.  Have you figured out a fix yet?  And how do you start GDM from the terminal?

Thanks

---

### Post by mrbones on 2008-01-12
Ok well as far as it goes all above issues, I have had EXCEPT crashing and being slow, The system is as fast if not faster than my KDE3 setup, The sudo issue was nothing, but the strangest thing I have had now is as someone above had mentioned, NO ability to make new folder in Dolphin for KDE4 Whats going on there? I understand issues in KDE4 this is the first release, I didn't start using KDE4 thinking it was instantly better than my 3.5.8 but this is a bit strange. However I definitely will not be switching back to 3.5.8 anytime soon unless I have a huge issue that impairs my use and my girlfriend, who is not nearly as computer/Linux savvy as myself:P 
Over all a damn good start to KDE4 and cant wait, but yeah some strange issues.

And if making a folder is a huge problem just deal for now using Dolphin for KDE 3.

---

### Post by rcmn on 2008-01-13
Tried kde4 on a kubuntu gusty and i already switch as many KDE4 apps i could. Very nice start indeed. Like everyone else i experience few issues but not enough to make me go back to 3.5 !!! Nice work and thank you to KDE devs and community.

---

### Post by fuji on 2008-01-13
Just wanted to throw in my comments.

I've been running kde4 for the past few days and I love it.  There are a number of quirks, bugs and other things that leave me scratching my head (like the dolphin new folder thing).  However, I also see potential in just about every facet of the system.  I see it everywhere and that is very exciting to me.  Great work developers!

I'm going to stick with KDE4 and look forward to the day all my apps are ported to the new libraries.  


RE the kdm-kde4 issue:

I think it may have something to do with the PATH variable not being configured properly. When you login `echo $PATH` was kinda empty for me missing the kde4/bin stuff.  I haven't looked into it much

As well, there is no kdmrc file and it appears the k/ubuntu package is missing a bunch of config files as, at least for me, /etc/kde4/kdm/ or whatever the path is, was missing some files.  I went back to KDM (kde3) for now since I still use KDE3 apps anyway (kmail, amarok, k3b, yakuake, etc).

---

### Post by mutzinet on 2008-01-13
> **fuji said:**
> Just wanted to throw in my comments.

I've been running kde4 for the past few days and I love it.  There are a number of quirks, bugs and other things that leave me scratching my head (like the dolphin new folder thing).  However, I also see potential in just about every facet of the system.  I see it everywhere and that is very exciting to me.  Great work developers!

I'm going to stick with KDE4 and look forward to the day all my apps are ported to the new libraries.  




Same here. Looking forward to the improvements and more cutomization options but it's faster and as stable as my KDE 3.5 + compiz.

Some real funny behaviours around: I have two jpg pictures on my desktop. Clicking on them launches Thunderbird. :)

---

### Post by exactopposite on 2008-01-13
> **uzd4ce said:**
> I'm having the same problem.  Have you figured out a fix yet?  And how do you start GDM from the terminal?

Thanks

sudo gdm was how i started gdm

i ended up uninstalling and reinstalling kde (long story) in in that process i had the opporntunity to choose gdm as the default. i would imagine there is a simple command to switch form kdm-kde4 to gdm (or kdm) as the default, but i don't kow how

---

### Post by mrbones on 2008-01-13
Ok, I think this was asked before in this thread,  but didn't see this answered.
I was just wondering looking back at it, is there anyway to take off 3.5.8 but leave the 4.0.0?
If not obviously no issue there, just a thought.

---

### Post by iAppleuser on 2008-01-13
I've just installed it! It is gorgeous! It seem like this is Hardy Heron already!

---

### Post by GeneralZod on 2008-01-13
The "no option to create folders" thing seems to be a packaging issue - I've just tried it with KDE4Daily:

[http://etotheipiplusone.com/kde4-dolphin-create-menu.png](http://etotheipiplusone.com/kde4-dolphin-create-menu.png)

---

### Post by maya9 on 2008-01-13
Having a terrible time.  Mayday!

Installed KDE 4 last night on top of Gutsy.  When it came time to start things up, I got a half screen of snow, then a blue screen with an off center box saying "Welcome to Debian" and a log in.  I tried logging in using every option (gnome, kde, kde 4.0) and it always took me to a flat blue screen with a terminal window.  

So I restart in recovery mode to a command line, do sudo gdm, and get a ubuntu login screen with system options.  I try the kde 4.0 and it runs, though VERY buggy.  At this point I just want to get it OFF my system and get back to my lovely gutsy.  Restart in similar manner and choose gnome and things are good (except I can't go online).

I then try various remove strategies, 
sudo aptitude remove kubuntu-desktop
sudo apt-get remove kubuntu-desktop
going into synaptic and searching for kde files

Sorry, I don't know enough to know what I'm doing.
Anyway, restarting  now takes me past the grub screen and then to a black screen and then nothing.  Just black.  I can still reboot in recovery mode as I did before and it appears that KDE is gone--it isn't showing up in the login screen's options.  What happened?  How do I get a normal start up into gutsy?  

KDE looked really cool and sexy but it did NOT work at all on my system.

Thanks!

(Please let me know if there is a better place to post this.)

---

### Post by wilberfan on 2008-01-13
I was REALLY excited about being able to use the new release, but after only an hour or two, I'm back to using 3.5.8 --  4.0 just feels too beta to me.  Too incomplete, too buggy...  Really odd that they would release it in this state...

---

### Post by Freddy on 2008-01-13
> **wilberfan said:**
> I was REALLY excited about being able to use the new release, but after only an hour or two, I'm back to using 3.5.8 --  4.0 just feels too beta to me.  Too incomplete, too buggy...  Really odd that they would release it in this state...
They have expalined multiplie times why they did release this though. I can agree with you that they should have just called it a RC, even if they would have released 10 RC's before it was useable enough for a 4.0 release. When I use it I can see the future of KDE and it looks quite good but we are not there yet and we won't be before summer atleast.

---

### Post by flange on 2008-01-13
Some of you need to learn about the "release early, release often" philosophy.  The open source world does not work the same as the closed source, Windows/OSX world.  Nor should it.  The following link should help you understand why the KDE team did the right thing in releasing KDE4 now.

["Release Early, Release Often" from Eric S. Raymond's "The Cathedral and the Bazaar"]("http://www.firstmonday.org/issues/issue3_3/raymond/#d4")

Relax.  KDE has released 4.0.0 so that all of us can share in its development and help it grow.  Enjoy the ride.  :)

---

### Post by Tanker Bob on 2008-01-13
Although 4.0 looks good for the most part, I'm back to 3.5.8 for the basic functionality. The blog linked earlier in this thread explained why they released 4.0 now, but I think they missed an important point. My, and I believe most folks, definition of "ready" would be when you at least have the capability of the version that you are replacing. KDE 4.0 isn't even close to having the capability of 3.5.8 for daily use. Mabye 4.1 will be release quality, but 4.0 isn't ready for production or mission-critical use in my opinion.

That said, my hat is off to those who contributed to the work so far. The integration of a composite manager with the desktop manager is very nicely done. When mature, this will be the desktop system to beat.

---

### Post by flange on 2008-01-13
> **Tanker Bob said:**
> My, and I believe most folks, definition of "ready" would be when you at least have the capability of the version that you are replacing. KDE 4.0 isn't even close to having the capability of 3.5.8 for daily use.

Maybe I read a different blog post than you, but the message I got from asiego was that KDE4 is a long way from replacing KDE3 in production environments.  The KDE team knows this, but KDE4 will never get there without widespread use and lots of bug reports.  They need more users in non-production environments to help them make it better, faster.

---

### Post by tmth on 2008-01-13
After switching to traditional application launcher widget crashes seemed to stop.

Another problem i have now is that almost everything opens up twice when clicking on them.   Especially from Dolphin or Konqueror.  Right click often doesn't work at all, ends up opening instead the file instead (right click menu flashes for a second after that).  Does any one experience this?

I also get loads of DBus errors:
KLauncher could not be reached via D-Bus, error when calling start_service_by_desktop_path: empty

Desktop effects are really good, but slow things down so i had to turn them off (may be my geforce 6800 is configured wrong) :(.


Other than that i really like KDE4 (despite my comment yesterday).  I love the way konqueror is now not only be able to preview things in embedded editor, but also edit without having to open up kwrite which is a huge speed up for some of the things i do.
Mini menu next to icons when hovering over is also amazing.  I wonder if it will ever be possible to put custom buttons on it, instead of just properties and delete.  Perhaps something like copy or cut should be added or let me chose what i want there.

---

### Post by Tanker Bob on 2008-01-13
> **flange said:**
> They need more users in non-production environments to help them make it better, faster.

I'm not looking to start a flame war, but you just gave one of the most compelling arguments why Linux may never get to be a mainstrean operating system on the desktop. The "average" user isn't interested in being a beta tester for core operating system components.

---

### Post by getaceres on 2008-01-13
> **Tanker Bob said:**
> I'm not looking to start a flame war, but you just gave one of the most compelling arguments why Linux may never get to be a mainstrean operating system on the desktop. The "average" user isn't interested in being a beta tester for core operating system components.

Like it or not. The average user IS a beta tester. Look at Windows Vista and the initial problems that some users are having with OSX Leopard.
Anyway, it's up to the distributors to decide what desktop environments are default in their distributions and given that KDE 4.0 is more a beta than a final product, I'd not include it by default in any distribution until at least, the 4.1 release but it's better to include it optionally for power users like me, willing to help reporting bugs.

---

### Post by flange on 2008-01-13
> **Tanker Bob said:**
> I'm not looking to start a flame war, but you just gave one of the most compelling arguments why Linux may never get to be a mainstrean operating system on the desktop. The "average" user isn't interested in being a beta tester for core operating system components.

I'm not trying to flame either., I just hoped to temper some expectations here that seemed unrealistic.  KDE4 needed to get into the repos to get the next level of users testing it.  Personally, I would not install something as big as KDE4 from source, because I don't want to risk hosing my package management.  I do want to try it out, though.

I also disagree with you that my statement is an argument for why Linux can never succeed in the mainstream.  You and I, sitting here in a Linux forum talking about trying out new a spanking new desktop environment, are not mainstream users.  Even the "noobs" around here are not mainstream users.  My mom is.  She hasn't got a clue what a desktop environment is, or that it can be changed independently of the core operating system.

When you see Dell pushing a Linux system with KDE4 as the default DE, then KDE4 better be ready for mainstream users.  I have a feeling that day is several years down the road, though.

---

### Post by dancantong on 2008-01-13
Hi!
I have installed KDE 4.0 over Ubuntu 7.10 and even though I have enabled desktop effects in System Settings - Desktop, I can't get any effect working.

I previously had Compiz Fuzion working with Ubuntu,.

Does anybody know If I have to do anything more to enable KDE effects?

---

### Post by flange on 2008-01-13
> **getaceres said:**
> Like it or not. The average user IS a beta tester. Look at Windows Vista and the initial problems that some users are having with OSX Leopard.
Anyway, it's up to the distributors to decide what desktop environments are default in their distributions and given that KDE 4.0 is more a beta than a final product, I'd not include it by default in any distribution until at least, the 4.1 release but it's better to include it optionally for power users like me, willing to help reporting bugs.

I agree with most of what you said.  What I take issue with is with regard to Vista and Leopard users being beta testers.  Closed source development models are (and should be) different.  When you're charging customers for a product, bugs should be minor, and most customers should never encounter them.  Microsoft and Apple both have a budget set aside for QA testing, and while bug free is impossible, the software they sell should be solid on release day.  The wise administrator will still wait for SP1, but Microsoft and Apple should be confident that their software is production-ready.

Open source is different because it needs advanced users to help out with QA.  At some level, each of us fits in to that "advanced user" category.  If you don't want to play that game, or aren't prepared to encounter significant bugs, you should wait until a respected production distro (Red Hat Enterprise, etc.) makes KDE4 the default.

---

### Post by exactopposite on 2008-01-13
> **Tanker Bob said:**
> I'm not looking to start a flame war, but you just gave one of the most compelling arguments why Linux may never get to be a mainstrean operating system on the desktop. The "average" user isn't interested in being a beta tester for core operating system components.

Who said that the people behind linux want it to be mainstream though? Linux isn't a busniess, and as such there is no incentive for it to grow market share.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by flange on 2008-01-13
> **exactopposite said:**
> Who said that the people behind linux want it to be mainstream though? Linux isn't a busniess, and as such there is no incentive for it to grow market share.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Not everyone involved with Linux might want that, but Red Hat, Canonical, and Novell certainly do.

[Ubuntu's Bug #1]("https://launchpad.net/ubuntu/+bug/1")

---

### Post by Tanker Bob on 2008-01-13
> **flange said:**
> When you see Dell pushing a Linux system with KDE4 as the default DE, then KDE4 better be ready for mainstream users.  I have a feeling that day is several years down the road, though.

I appreciate your thoughts. I certainly agree with that last assessment.

---

### Post by exactopposite on 2008-01-13
> **flange said:**
> Not everyone involved with Linux might want that, but Red Hat, Canonical, and Novell certainly do.

[Ubuntu's Bug #1]("https://launchpad.net/ubuntu/+bug/1")

how about somebody make another post for this discussion. while it is relevant to kde4, we'll end up with this post way off course at this rate.

---

### Post by Fedup on 2008-01-13
Why no KMail/Kontact etc. in KDE4? I'm stuck with the KDE3 version and trying to install the KDE4 one just brings up an error about broken packages :confused:


Other than that... I've been using KDE4 all day and so far its working. It needs a bit more work and ideally a huge speedup on the graphic redraw speed side of things... but its looking promising.

---

### Post by GeneralZod on 2008-01-13
> **Fedup said:**
> Why no KMail/Kontact etc. in KDE4? I'm stuck with the KDE3 version and trying to install the KDE4 one just brings up an error about broken packages :confused.

[http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Is_KDEPIM_.28Kontact.2C_KMail_etc.29_Available_for_KDE_4.0.0.3F](http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ#Is_KDEPIM_.28Kontact.2C_KMail_etc.29_Available_for_KDE_4.0.0.3F)

---

### Post by Fedup on 2008-01-13
Hmmm.. replying to my own post, according to [http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ](http://software-libre.rudd-o.com/KDE_4.0.0_emergency_FAQ) KMail etc. for KDE4 didn't make it.

Strange, I'm sure it was in RC2??

---

### Post by proalan on 2008-01-13
Was fine on desktop machine but unworkable on laptop, had to revert back to previous kde release.

It does feel like a beta, its certainly the most resource hungry graphical desktop I've tried so far.

I'm sure it will come good in future releases though.

---

### Post by catanzag on 2008-01-14
> **Starlight said:**
> It seems to me that almost none of the KDE 4 apps have icons... there's always a blank space next to them in the K menu. Does anyone else have that problem?

I got the same, most KDE4 application have *blank* icons, while most of categories (except Education) have *question mark* icon (does it make sense to submit a bug to launchpad or it should be submitted to kde?). 

I installed KDE 4.0.0 last saturday. After playing for an hour, apart missing icons, I had a complete crash which removed the menubar, I had to *rm -r ~/.kde4* to have all again; btw, I had to install KDE twice, as italian localization made missing some dialog items, for instance it was impossible to reconfigure shortcuts for desktop effect. 

I've never tried the betas or RCs, but, in spite of the bugs, I'm very impressed, it will be great, but, for now, I will only *play* with it till a more debugged version.

---

### Post by leisuresuitgreg on 2008-01-14
I am attempting to use KDE4 as a full time front end for gutsy. I like it. Sure some of the icons do not have descriptions, and I can't get the widgets running but it's generally very good on my setup, and incredibly pretty.

Out of the box I give it 7/10 so far.

Greg

---

### Post by wilberfan on 2008-01-14
I'm not sure if this has been covered yet, but apparently KDE4 is NOT the same as KDE 4.0?

I found this post very helpful (and it explains why my 4.0 experience was underwhelming):  [http://linux.wordpress.com/2008/01/14/about-kde4-and-kde-4-and-little-more/](http://linux.wordpress.com/2008/01/14/about-kde4-and-kde-4-and-little-more/)

---

### Post by exactopposite on 2008-01-14
> **wilberfan said:**
> I'm not sure if this has been covered yet, but apparently KDE4 is NOT the same as KDE 4.0?

I found this post very helpful (and it explains why my 4.0 experience was underwhelming):  [http://linux.wordpress.com/2008/01/14/about-kde4-and-kde-4-and-little-more/](http://linux.wordpress.com/2008/01/14/about-kde4-and-kde-4-and-little-more/)


really it's semantics. kde4 is the new platform. kde 4.0.0 is the first release of it. kde 4.1 will be a newer version of kde based ont he same platform. 

i think it's just their way of saying that there is more to come.

---

### Post by funnypanks on 2008-01-14
> **exactopposite said:**
> i'm a gnome user myself. basing your opinions of kde on this release of kde4 isn't exactly giving it a fair shake. It's not ready for primetime, and the kde people were clear that this would be the case. They just built the entire DE from the ground up. Now that it's out there and some people are using it and finding bugs, it should improve quickly. This is one instance where KDE is showing innovation, and that is good for the open source community as a whole.

If you prefer gnome, there is nothing wrong with that. I have been a gnome guy for a long time myself. However, I must ask, when was the last time gnome did something this big? This isn't an occasion to bash KDE for releasing something in the condition they said it would be in. This is a time to witness the birth of something that will benefit the entire linux desktop userbase.

sorry my goal wasn't to poopoo kde, it was just to say i prefer gnome, i just like how the panel is arranged in gnome and i don't like how huge the bar in kde either. but yea, i did sound douchy and for that i am sorry and i like the innovation their making, its pretty much why i moved to linux, even mac only in leopard got spaces, where we've had it for years. and the widgets button is cool in kde. i think its just the panel, and the arrangement of the menus that gets to me. its the same thing that kept me from using suse for more than a week, but it's always better to know more, and i will definitly check back in with kde come summertime.

---

### Post by funnypanks on 2008-01-14
o and is amarok 2.0 release date announced yet?

---

### Post by accessd on 2008-01-15
Has anyone figured out how to autostart applications or manually save a session in KDE4? I cannot figure it out for the life of me. Putting scripts, .desktop files, and links in ~/.kde4/Autostart seems to have no effect.

---

### Post by Elotero on 2008-01-15
KDE4 looks very nice but is still a little too buggy for me to play with until some bugfixes are out so im bavk to Gnome for the minute. 


BUT

After I installed KDE4, Kooldock doesnt run anymore on Gnome! Initially Amarok wouldnt run either in Gnome butr after restarting it came back. Is there a way to reverse all this or fix the Amarok/Kooldock problem? 

Is there a way to get system/bugfix updates for KDE4 from Gnome? Or is it all the same when i run Update manager?

THANK YOU ALL!!!!!

---

### Post by notmatt on 2008-01-15
It isn't perfect by any stretch, but I do find it to be very nice.  I'm really looking forward to the 4.1 release.  It should be really good once they've had a good chance to iron out all the bugs.

---

### Post by Shin_Gouki2501 on 2008-01-15
more to come *_*
3rd quarter 2008 kde 4.1 planed hm...
why they release a "beta"- resource hungry unfinished DE?
hmm anyways maybe 4.1 is better :O

---

### Post by ferd on 2008-01-15
I could not log into synaptic and although a fix has been posted I chose to go back to 3.5 because there are not enough configuration options available to make 4.0 a useful option for me.

---

### Post by soulfly7x on 2008-01-15
My first thoughts were, "What did they do to my beautiful KDE?"
 They appear to have ruined it. Completely.

I couldn't move the panel to the top where I want it. Then, trying to go through the menus is a chore. Instead of waving my mouse over a point to select a program, I have to go through this atrocious process of clicking each subcategory and waiting for it to slide over into view. It took me 5 minutes to notice the back arrow to get out of the ""Internet" subcategory.

The second thing I always do is add a shell icon to the panel, and when I finally figured out how to do that, the shell wouldn't open. 

This is worse than Vista. It's the worst monstrosity I've ever seen. If it was my first impression of Linux, I would run screaming to Bill Gates to take me back. 

What's with all the comments about how it looks pretty? It doesn't look pretty. It looks STUPID. With an enormous taskbar, that I can't seem to customize, and a gigantic clock for the legally blind. 

I logged out and went back into my default KDE session, and removed kde4, and it broke my system. Now I have the pleasure of fixing a broken system. I get nothing but command line. It tells me that somehow kubuntu-desktop is "not installed and therefore not removed" but if I try to install it, it won't.

I'm backing up the home folder right now, and when that's done, it's time for a reinstall. If this is where KDE is going, I'm done with it. Maybe this time I'll just go with the horrid GNOME version of Ubuntu.

---

### Post by telepete on 2008-01-15
hope one of u guys wouldn't mind answering a (hopefully) quick question. I am on Kubuntu 64 7.10. I installed KDE 4 as per the directions at the Kubuntu web site and the installation appears to have gone smoothly. I can see all the KDE 4 apps on the menu in KDE 3 and there were no errors when installing. The instructions say that when i log out i can choose to log back in via the 'KDE 4.0' option in the Session Type menu. All i have got in that menu is 'default', 'kde' (3.5), and 'failsafe'. Why is KDE 4 not in that menu? i am dying to try it.

Thanks.

---

### Post by soulfly7x on 2008-01-16
Did you 

"Add **deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main** to your /etc/apt/sources.list"

[http://kubuntu.org/announcements/kde-4.0.php](http://kubuntu.org/announcements/kde-4.0.php)

---

### Post by Asraniel on 2008-01-16
> **soulfly7x said:**
> My first thoughts were, "What did they do to my beautiful KDE?"
 They appear to have ruined it. Completely.

I couldn't move the panel to the top where I want it. Then, trying to go through the menus is a chore. Instead of waving my mouse over a point to select a program, I have to go through this atrocious process of clicking each subcategory and waiting for it to slide over into view. It took me 5 minutes to notice the back arrow to get out of the ""Internet" subcategory.

The second thing I always do is add a shell icon to the panel, and when I finally figured out how to do that, the shell wouldn't open. 

This is worse than Vista. It's the worst monstrosity I've ever seen. If it was my first impression of Linux, I would run screaming to Bill Gates to take me back. 

What's with all the comments about how it looks pretty? It doesn't look pretty. It looks STUPID. With an enormous taskbar, that I can't seem to customize, and a gigantic clock for the legally blind. 

I logged out and went back into my default KDE session, and removed kde4, and it broke my system. Now I have the pleasure of fixing a broken system. I get nothing but command line. It tells me that somehow kubuntu-desktop is "not installed and therefore not removed" but if I try to install it, it won't.

I'm backing up the home folder right now, and when that's done, it's time for a reinstall. If this is where KDE is going, I'm done with it. Maybe this time I'll just go with the horrid GNOME version of Ubuntu.

Hi, i see alot of frustration in your post.
Don't worry, kde4 won't be what you have experienced with kde 4.0.0
The version you tested was the first, nearly everything has been developed from scratch, so not all features from kde 3.5 could been redeveloped.
Kde 4.0.0 was meant to be a base for the future release, making it easier to develop for kde. And if you are not a developer, just beliieve me that they did a great job with that, so expect kde 4 to be at the same level as kde 3.5 at version 4.1 or 4.2.

So dont worry, kde won't become something like gnome, but it will be even more configurable than kde 3.5. Kde 4.0.0 just wasn't meant for the big public (well yes, so that they get many bugreports and can get things stable).

My advice, wait 6 months and take a look at kde 4 again, you won't be disapointed

---

### Post by tekknokrat on 2008-01-16
I tested kde4 2 days ago and am just downloading the (todays(?)) updates...

My impression of kde4 in general:

- nice simple design which was mostly the argue to stay with it for some longer
- start menu sux. It has completely white background - i hope its a bug or will develop.
- old qt and gtk apps works mostly and don't behave such strange

When I changed resolution with xrandr the panel chrashes and now way to restart it.
Multidisplay supprt isn't even developed, yet.

After some time icons get fragemented and mixed with neighbour icon.

If you type name of program in search and press immidiately enter you get the program open selected.

The ones which are willing to test are also the one who write bug reports. The users which were blended from the stable state of kde4 and tested it mostly don't have the attitude or skills to post a bug.

All in all I like the release politic of e.g. e17 because it is more decent.  
Although they still claim it as an early alpha it is running very stable and looks very mature.

---

### Post by soulfly7x on 2008-01-16
> **Asraniel said:**
> My advice, wait 6 months and take a look at kde 4 again, you won't be disapointed

I hope you're right, because I've always loved KDE.

---

### Post by roderick on 2008-01-16
It would be useful for some people to read the developers blog on KDE, specifically this entry:

[http://aseigo.blogspot.com/2008/01/talking-bluntly.html](http://aseigo.blogspot.com/2008/01/talking-bluntly.html)

KDE 4.0.0 was never meant to be an immediate replacement or upgrade to KDE 3.5.X. KDE 4.0.0 is a restart of KDE, where everything is being built from the ground up.

Ok, so now that that is out of the way... 

1) Both KDE 3.5 and 4.0 can CO-EXIST in the same install. So, you shouldn't remove 3.5.
2) You can start KDE 4 apps in two ways 
   a) From within a KDE 3.5 session - most stable way to test/use KDE 4 apps
   b) From within a KDE 4.0 session - least stable but you get the complete feel

For me, KDE 4.0 is EXACTLY what I expected it to be. Reading the posts, blogs, warnings, etc, prepared me and set my expectations appropriately.

Hope this helps clarify for some.

---

### Post by BackwardsDown on 2008-01-16
I'm working full time in kde4. I can't say its as good as kde3, but I bet it will in the future.

And the blog post Roderick posted ([http://aseigo.blogspot.com/2008/01/talking-bluntly.html](http://aseigo.blogspot.com/2008/01/talking-bluntly.html)) is very good, it just sums it all out.

So I sit back and enjoy the ride while kubuntu gives me an update once in a while :popcorn:

---

### Post by litemotiv on 2008-01-16
don't know if this was posted before, but for people like myself who are not too fond of the new startmenu:

- open the Add Widgets panel
- drag the classic start menu widget to the base panel

and you'll have your old startmenu back.

personally, apart from the many quirks and shortcomings (most of the oxygen interface and window decorations are just plain hideous in my opinion), i think it all looks very promising. the composite base also feels quite solid and smooth, and man, do those wallpapers look great. ;-)

---

### Post by romana on 2008-01-16
My major grip is the fact i cannot get wallpapers to set - just white space..is sufficiently annoying that i just dont want to work in it. also, many oxygen icons are missing. Otherwise, is very blingy and shiny, isnt it:)

Suspect 4.1 will be big improvement.

---

### Post by emerson999 on 2008-01-16
I'm mostly just happy to get everything moving over to QT4. 4.4's looking amazing, and it'd be nice to get kde moving alongside it. The actual desktop isn't that bad once I got rid of the panel and just ran an instance of the kde3 kicker.

---

### Post by c_martini on 2008-01-17
I am experiencing the dual head bug with the final release over Kubuntu Gutsy and two Nvidia cards (2 separate x screens, 1 to monitor, 1 to tv-out). Damn. KDE 4 is nearly unusable for me this way. Hate going back to 3.5.8 now that 4 is sitting there unused :( Was sooo looking forward to this release too. One of the developers said there won't be dual head support in KDE 4. Maybe 4.1. Oh well...  

Hmm, dual head works flawlessly in KDE 3.5.x (and Windows) though...

:(

---

### Post by venik212 on 2008-01-17
I detest the menu as well.  Is there a way to use KDE4 but with the old, convenient menu?  It requires fewer mouse movements by far.

---

### Post by getaceres on 2008-01-17
> **venik212 said:**
> I detest the menu as well.  Is there a way to use KDE4 but with the old, convenient menu?  It requires fewer mouse movements by far.

It's just a little up from your post:

[http://ubuntuforums.org/showpost.php?p=4147893&postcount=171](http://ubuntuforums.org/showpost.php?p=4147893&postcount=171)

---

### Post by GeneralZod on 2008-01-17
> **romana said:**
> My major grip is the fact i cannot get wallpapers to set - just white space..is sufficiently annoying that i just dont want to work in it. also, many oxygen icons are missing. Otherwise, is very blingy and shiny, isnt it:)

Suspect 4.1 will be big improvement.

This is fixed in SVN and has been backported to the 4.0.x branch, IIRC.  I'm fairly surprised that the fix hasn't made it into the Kubuntu packages.

Clicking "Apply" on the wallpaper dialog multiple times should work - it's a race condition, so you should get lucky eventually :)

---

### Post by magikx21 on 2008-01-17
I installed KDE4 on the 11th and gave it a try and went back to using 3.5. Looking at KDE4 though, it has a lot of potential but at this point I'm quite content with the way I configured 3.5 and the inability to configure KDE4 to my liking is deal breaker. Hopefully 4.1 will incorprate the new look with the old configurability.

---

### Post by The Cog on 2008-01-17
> **Rob500 said:**
> 
I have no idea how to delete things from the desktop the way we're used to. What I did was use Dolphin and delete them from the desktop folder (/home/myname/desktop). There must be a quicker and simpler way though.

Click the icon then type Shift-Delete

---

### Post by The Cog on 2008-01-17
I tried the Kubuntu KDE4 live CD on my lappy. Awful. My first impressions:

Right-clicking a file in Dolphin and using Open With... invariably produced a popup "could not open..." dialog in addidion to the file opening properly in the chosen application.

Turning on desktp effects produced a black screen that only  **rm -rf .kde***  from a text console would fix. 

Dragging a widget somethins dragged the wallpaper too. Others have reported this, and apparently a fix will come later.

Desktop freeze while changing themes. 

Taskbar disappeared. Ctrl-Alt-Backspace doesn't fix it.

The new launcher is awful. It's pretty, and seems designed to trap you looking at it for as long as possible by making it as difficult to use as possible. Also, hiding the hierarchy from view makes it hard to remember where things can be found, so you have to hunt again next time, and next...

Dragging the widgets is apallingly slow, especially when enlarged.

On the plus side, the applications GUIs, the new QT stuff, felt very snappy indeed. 

I had been thinking of switching to KDE from Gnome. I'll think again in a year or so.

---

### Post by Case_f on 2008-01-18
> **roderick said:**
> 
1) Both KDE 3.5 and 4.0 can CO-EXIST in the same install. So, you shouldn't remove 3.5.

Although in Kubuntu - not so much. At least in my experience. The 3.5 was still working, but sometimes it was giving weird errors and the desktop didn't really work (no wallpaper, superkaramba seemingly stuck etx). But yeah, it SHOULD be able to co-exist, maybe it was some problem in the packaging or something else.

---

### Post by mrgnash on 2008-01-29
Two words: bloody awful.

Aesthetic design is great, but the functional design is just garbage. 

That said, I think it is a huge step forward from KDE 3.5, and with some extensive reworking in certain areas, it could be a very solid DE.

---

### Post by AndrewTheArt on 2008-01-30
For anyone who can't connect to the Internet in KDE4 - 

Not sure if this syntax works in Ubuntu, but give this a shot - 

```
/etc/init.d/network start
```

Works in openSUSE 10.3 KDE 4.0

---

### Post by roderick on 2008-01-30
I just ran knetworkmanager from Run command. It can be added to the Autostart .kde4 directory for future boot-ups. 

I assume knetworkmanager will be updated to a Qt4/KDE4 version later, so unfortunately, you need this for now under Kubuntu with KDE4.

---

### Post by LuisAugusto on 2008-01-31
> **roderick said:**
> I just ran knetworkmanager from Run command. It can be added to the Autostart .kde4 directory for future boot-ups. 

I assume knetworkmanager will be updated to a Qt4/KDE4 version later, so unfortunately, you need this for now under Kubuntu with KDE4.

The port is work in progress :)

---

### Post by amrlima on 2008-02-12
In terms of performance, how is kde4 on gutsy? I have 3.5 on my Gutsy instalation and I am thinking on giving kde 4 a try now...

---

### Post by walkerk on 2008-02-12
> **AndrewTheArt said:**
> For anyone who can't connect to the Internet in KDE4 - 

Not sure if this syntax works in Ubuntu, but give this a shot - 

```
/etc/init.d/network start
```

Works in openSUSE 10.3 KDE 4.0

slightly different...
```
/etc/init.d/networking start
```
```
/etc/init.d/networking stop
```
```
/etc/init.d/networking restart
```

---

### Post by Tuxoid on 2008-02-12
I installed KDE4 last nite and tried it out this morning. I thought "this is so cool!" then I tested some stuff. I can't seem to get my volume control media-keys to work (or any volume control whatsoever) and the second time I logged into it my panel was gone (along with everything on it). I don't know how to get it all back.

---

### Post by Hieronymus on 2008-04-30
Ok, yesterday I decided to give Kubuntu KDE4 a try, it works pretty well for me. I still have the problem with the iwl wireless driver which I have to work around using ndiswrapper, but in general no big issues. 

Irritating is that after installing new packages there the menu entry will only appear after a reboot. 

Furthermore no really big issues. 

Jeroen

---

