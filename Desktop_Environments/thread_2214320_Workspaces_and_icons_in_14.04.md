---
title: "Workspaces and icons in 14.04?"
date: 2014-03-31
forum: Desktop Environments
---

### Post by Odyssey1942 on 2014-03-31
I think that the Gnome 2 desktop in 10.04 is the most productive I have ever had the pleasure to use. I now run 12.04 but in fallback mode and for the most part have recreated the experience.

I have used Unity enough to basically conclude that I can do at least some of what I could do in Gnome 2, but at the expense of at least one more mouse click, and in some cases multiple additional clicks, and all for the apparent objective of a clean desktop (which to me is a loss of productive space.)

The most important features of the old desktop to me are:

1) multiple workspaces (I run 8 each with multiple browser and other windows, and each for a different "topic/interest")

2) desktop icons

3) user managed icons on the upper title bar

Will I be able to either:

-run fallback in 14.04, or

-accomplish all of the above in Unity? If not all, which and which not?

TIA

---

### Post by grahammechanical on 2014-03-31
Why don't you install 14.04 and test all this out for yourself? I can tell you this, we do not install Fallback in 14.04. It is gone. Instead we install gnome-session-flashback. Then we get two additional options at login; Gnome Flashback (Compiz) and Gnome Flashback (Metacity). We use CCSM to modify the Compiz Flashback but with Metacity Flashback we get only one workspace until we right click on the workspace icon then we get a dialog that allows us to set any number of workspaces. I hate desktop icons. Ugly. Ugly.

Do not install Gnome classic as that is actually gnome 3 shell with a classic like extension.

---

### Post by Odyssey1942 on 2014-04-01
Graham, thanks. I wish I had extra hours to "test" but I am stretched very thin and mostly use my computer just to get things done. So if I can get simple questions like the above answered without downloading, making a DVD, and spending time figuring out how things work, it helps me a lot.

Failing some "simple" answers to my hopefully simple questions, will certainly do as you suggest and have a play. (I didn't follow all of what you wrote and if you answered some or all of my questions, please forgive.)

Will heed your guidance regarding Gnome Classic. BTW, I am not very knowledgeable, in fact confused, about all the Gnome 2, Gnome 3, Classic, "forks", etc., terminology. I just want a desktop like I had in 10.04 and now have in fallback 12.04. 

I take no issue with your comment on appearance. It simply isn't something that I think about. What I do think about is convenient, fast, and fewest steps.

---

### Post by frank18 on 2014-04-01
I use  Gnome Flashback (Metacity) on Ubuntu 14.04 and i am very happy with it, it does exact same thing for me as the Fallback since i never use more than one desktop

---

### Post by Odyssey1942 on 2014-04-01
If I understood Graham, Gnome Flashback (Metacity) allows multiple workspaces. (Just to ensure that we are on the same page, 10.04 and 12.04 fallback both use the same desktop and upper panel, but provide different workspaces [which in my view is simply a different bottom panel allowing segregation of work by type or interest in the different workspaces.]) This is 1/3 of my objective if my understanding is correct.

Under Gnome Flashback (Metacity):

Can the upper panel be user customized?

Are desktop icons possible?

---

### Post by deadflowr on 2014-04-01
Don't use gnome classic/flashback myself, but kansasnoob's got a nice thread going on all of this here
[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

That should clear up of few of the ins and outs of what you might expect from the old gnome-like layouts.

Enjoy

---

### Post by Odyssey1942 on 2014-04-01
DF, I have been following links and reading continuously since seeing your post, but am no closer to the answers to my three very simple (I thought) questions, other than what Graham indicated with respect to workspaces.

Maybe I should just ask, "Can the old Gnome 2 Classic interface (from 10.04) be duplicated in 14.04?" If not, which of the three objectives that I have outlined cannot be achieved?

---

### Post by deadflowr on 2014-04-02
Well, objectives 1 and 2 should work as they already do.
(There may or may not need to be a tweak to get desktop icons)

But I have no clue about objective 3.

This of course would be the gnome-flashback (metacity /or compiz) version.
And not the new gnome classic, which is quite confusing, even to me.

---

### Post by grumblebum2 on 2014-04-02
Once 14.04 is installed it's just a matter of running ...
```
sudo apt-get install gnome-panel
```

This will give you 2 flashback session  choices..... compiz or metacity.
It mimmicks the old gnome2 enviroment with a top and bottom panel.
To interact with the panels use Super+alt+MouseRclick.

You can drag applications from the Applications menu onto the desktop or into the panel
and customize your workspaces from the workspaces switcher applet when in the flashback metacity session.
Very similar to before.

If you prefer to use the  flashback compiz session, leave the workspaces applet configured to show 1 workspace and
and configure your desktops in **compizconfig-settings-manager(ccsm) >  general options > desktop size**
You only need to set your horizontal and vertical numbers.
The panel applet will pick up the change and display accordingly.


**[COLOR="#FF0000"]***[/COLOR]** one thing to note...if you open ccsm to the desktop size tab again it will reset your workspaces to 1 
and you will need to configure again.

---

### Post by buzzingrobot on 2014-04-02
Multiple workspaces *are* supported in Unity by default. A switcher can be added to the Launcher via System Settings. Install Unity Tweak Tool to adjust the numbers, as well as other useful settings (desktop icons, too, I believe.)

User-managed icons in the panel happen to a much reduced extent. 

To stay with the Gnome 2 interface, I recommend installing the Mate desktop ([http://mate-desktop.org/](http://mate-desktop.org/)) following the install instructions at their site. (No 14.04 instructions are there, but I'd imagine we will see them after 14.04 is released. Installing as for 13.10 on 14.04  worked for me, but it is still a moving target for now. The official version available in the Mate repos is 1.6.  A recent bump to 1.8 is available unofficially, but I found a few annoyances with those packages. Also, Mate packages are currently making their way into Ubuntu's Universe repo when someone builds them for Debian.)

---

### Post by Odyssey1942 on 2014-04-02
Thanks for all the helpful replies. I can see that I failed to mention that I understand that Unity already supports multiple workspaces. 

What I do not want is to have to click on something to get to see those workspaces. I want them in the lower panel in the bottom right (a la 10.04) where I can see them all the time and move from one to another with a single click. (BTW, that is why I want icons on the desktop.)

I am unsure from the recent posts whether this is possible. If so, which of the alternatives makes this possible?

And if so, is there one shell that makes all three possible. Thanks.

---

### Post by buzzingrobot on 2014-04-02
Mate will get you what you want. It's the Gnome 2 code rebuilt, patched, fixed, etc.  Same interface. A LiveCD is available, so you could check it out.

Cinnamon, KDE, and XFCE will, as well, in their own ways.

Gnome 3 enables an approximation of the old interface via extensions.

Note that in Unity you do not need to click on a switcher/pager to move to an open app in another workspace. Clicking the app's icon in the Launcher will take you there. You do need the switcher to get to unused workspaces. Keyboard equivalents exist. Momentarily hold the Windows key to see a list.

---

### Post by Odyssey1942 on 2014-04-02
BR, Thanks for all the good information. Since you appear to be in the know on these things, or from anyone really, will Mate simply be an interface to 14.04, or does it utilize an earlier version of Ubuntu?

---

### Post by deadflowr on 2014-04-02
> **Odyssey1942 said:**
>  will Mate simply be an interface to 14.04, or does it utilize an earlier version of Ubuntu?

I'm somewhat confused by that, but for whatever it's worth, mate is a fork of the old gnome2 desktop environment, and has been built to run on the most current systems.

Mate is not just an interface.
It is a fully functional desktop environment, which include file managers and other common apps.
It designed to run mostly the same as the old gnome2 desktop, with a few minor changes, and a few app name changes.

If that helps.

---

### Post by buzzingrobot on 2014-04-02
> **Odyssey1942 said:**
> ...will Mate simply be an interface to 14.04, or does it utilize an earlier version of Ubuntu?

Mate is a desktop environment like KDE, Unity, XFCE, etc. that can be added to Ubuntu; it's not a full-fledged distribution, earlier or otherwise.  When you add it to an Ubuntu Unity system, it's offered as an alternative by the display manager when you log in. (The default is to stay with the last interface used, so a user needs to manually choose Mate at the log in, and it will stay the default until the user makes another change.)

When the Gnome project stopped working on Gnome 2 about three years ago, Canonical chose to develop Unity to replace it.  Some other developers decided to maintain the Gnome 2 approach and rebuilt the Gnome 2 codebase into Mate (They can't use the Gnome name).  It's been tweaked and adjusted to keep pace, of course, but it looks and works like old Gnome 2 because, in essence, it is.

I found it worked fine on 13.10.  I'd wait for the dust to settle after the 14.04 release. Mate hasn't created an offical 14.04 repo yet and there are a number of Mate packages in the 14.04 repos coming over from Debian, so when I installed on 14.04 packages were pulled from both places. So far, so good, but when Mate opens its official repo for 14.04, I'll move to that.

Mate is also available from Linux Mint.  It's a very polished implementation and, since it's Mint, uses the Ubuntu repos. Current version is Mint 16, based on 13.10. By default, it ships with one panel at the bottom and Mint's own Mint Menu.  More panels can be easily added and the traditional menus can replace the Mint Menu via a right click on the panel, as in Gnome 2.

---

### Post by Odyssey1942 on 2014-04-02
DF & BR, Thanks for yours which I believe answered my question, which though badly worded, was to confirm that Mate (and others) can be utilized on (in? with?) 14.04.

The ideal circumstance (for me)  is to enjoy the advances of each LTS Ubuntu, but maintain the productivity (for me) of Gnome 2. Unless someone disabuses me of this opinion, I am comfortable that this can be done.

I will definitely wait a couple (four? more?) weeks after release before installing 14.04 so to avoid early release issues.

---

### Post by anaconda on 2014-04-02
> **Odyssey1942 said:**
> DF & BR, Thanks for yours which I believe answered my question, which though badly worded, was to confirm that Mate (and others) can be utilized on (in? with?) 14.04.

The ideal circumstance (for me)  is to enjoy the advances of each LTS Ubuntu, but maintain the productivity (for me) of Gnome 2. Unless someone disabuses me of this opinion, I am comfortable that this can be done.

I also prefer the gnome2 interface, but I went a different route. 
Now I use xfce. (Xfce is the windowmanager in xubuntu.) 
It took some tweaking and getting used to, but now I have gnome2-like desktop, and am happy with it.

---

### Post by Odyssey1942 on 2014-04-02
Anaconda, are you limited to 2 workspaces or can you have more, and if so, how many?

Thanks.

---

### Post by monkeybrain20122 on 2014-04-04
> **Odyssey1942 said:**
> 

What I do not want is to have to click on something to get to see those workspaces. I want them in the lower panel in the bottom right (a la 10.04) where I can see them all the time and move from one to another with a single click. (BTW, that is why I want icons on the desktop.)
.

For Unity, you just install ccsm (compizconfig-settings-manager from the repo), enable expo and make the bottom right corner a hot corner. that way you don't have to click to get to them, you don't even have to get to the panel, just put the mouse at the corner(which is what I do) 

This works with any DE if you install compiz. I did this in 10.04 as well as I absolutely hated the panel. It is inefficient IMO.

Edit: See screenshot Expo Corner/Edge
P.S You can have as many work places as you want. I always use 4 but I have seen people with 9 or even 16 (it is a square number if you want vertical and horizontal number to be the same, but they don't have to be. The setting is in ccsm > General > desktop size , maybe in Unity-tweak as well, but I don't use u-t so can't say for sure)

---

### Post by frank18 on 2014-04-04
If you install Ubuntu14.04 and install  mate desktop you are asking for trouble, just my opinion

---

### Post by Odyssey1942 on 2014-04-05
Frank, interesting comment.

What would be the nature of the trouble?

---

### Post by oldrocker99 on 2014-04-06
I started using MATE with Mint, found Mint annoying (the system, not MATE), and, now, I install Kubuntu and install MATE over it; KDE for the apps, and MATE for the desktop. The only bugs I've found with MATE are the crash with Compiz, and the disappearing panels (which can be fixed when it happens by locating Syetem/Preferences/Appearance and changing the theme).

Aside from that, MATE (running 1.8 on my 14.04) works very well for me, and I recommend it to anyone who misses the old GNOME 2.3.

---

### Post by buzzingrobot on 2014-04-06
> **oldrocker99 said:**
> I started using MATE with Mint, found Mint annoying (the system, not MATE), and, now, I install Kubuntu and install MATE over it; KDE for the apps, and MATE for the desktop. The only bugs I've found with MATE are the crash with Compiz, and the disappearing panels (which can be fixed when it happens by locating Syetem/Preferences/Appearance and changing the theme).

Aside from that, MATE (running 1.8 on my 14.04) works very well for me, and I recommend it to anyone who misses the old GNOME 2.3.

Does Mozo (the menu editor) work for you on 1.8?  Wouldn't for me when I installed 1.8 on 14.04 from the "archive" at Mate's repo. The "user and group" gizmo didn't work, either. (There's a patch to Mozo on Github that, I suspect, addresses that problem, but the achive doesn't appear to have been updated.  I'm guessing we won't see 1.8 for Ubuntu in the official Mate repo until after 14.04 is released.)

Compiz and Mate 1.6 often don't get along well (although Fedora's 1.6 spin uses Compiz, so there's a way to do make it happy).  I don't know about 1.8.

---

### Post by monkeybrain20122 on 2014-04-06
> **oldrocker99 said:**
> I started using MATE with Mint, found Mint annoying (the system, not MATE), and, now, I install Kubuntu and install MATE over it; KDE for the apps, and MATE for the desktop. The only bugs I've found with MATE are the crash with Compiz, and the disappearing panels (which can be fixed when it happens by locating Syetem/Preferences/Appearance and changing the theme).

Aside from that, MATE (running 1.8 on my 14.04) works very well for me, and I recommend it to anyone who misses the old GNOME 2.3.

This is just horrendous. :) KDE+ MATE + Compiz??!! This has the be the most unnecessarily bloated and mixed up installation ever. :) First KDE has panel and what not and it can be customized to look like gnome 2 so you don't need MATE at all since you are using KDE applications anyway. Secondly kde has its own compositor (kwin) which has most of Compiz's functions and eye candies so you don't need Compiz.

---

### Post by Allen.McIntosh on 2014-05-16
I am was also a fan of 10.04.  To get close with 14.04 I installed gnome-session-flashback and gnome-tweak-tool.  I signed on with flashback/metacity, and everything was almost OK.  I can get multiple workspaces by right clicking on the workspace switcher, and add to the top menu bar with alt-right-click (or just ctrl+drag-and-drop from a menu).  The only problem is that I seem to have set autoraise and can't get it turned off again. :( It's a small price to pay.

---

### Post by josepato on 2014-08-08
Nice, thanks :)

---

