---
title: "I want minimized-window icons back!!"
date: 2011-12-07
forum: Desktop Environments
---

### Post by matteosistisette on 2011-12-07
Hi,

I recently upgraded from 10.10 to 11.04 and hence Gnome has been replaced by Unity (is it how it is called?).

I guess I will learn to love it, but there is one thing that I find demential: icons of minimized applications (i.e. those you minimize by clicking on the "_" button on the window's title bar) are mixed with icons of applications in launcher that are not open at all. While having icons on the left or bottom or wherever is just a matter of tastes and habits, mixing minimized window icons with launcher application icons is simply insane (that Apple invented it doesn't mean it's a good idea)....

The question is, **is there a way (there MUST be a way) to separate them and have the minimized window icons on a bar on the bottom of the screen** (which I will make non-auto-hidable) **isolated** from the icons of not-open applications?

I often pick a file in Nautilus and then drag it into the filezilla icon (which is minimized) to bring filezilla's window up and then drag the file into it, all in one single drag-n-drop. I know I can do exactly the same now with the launcher icons, but when you have only a couple of open applications it's much more handy to have them isolated than to have to "discern" them in the middle of other not-currently-open applications........

Also, i find clicking on minimized icon to switch between apps much handier than using alt-tab, and then again, having only the relevant icons helps a lot...


Thanks in advance
m.

---

### Post by Jay Car on 2011-12-07
On Natty (11.04) you can just log out, and at the log-in look for the little gear (or wheel, as some describe it) icon to the right, click it and select Gnome and it will give you the old Gnome back. Then you can set it up like you want.

It's what I did to get by until I could get acclimated to the newer desktops on another computer. Just be patient, things are a bit bumpy nowadays, but will probably smooth out over time. 

:)

---

### Post by westdale on 2011-12-07
thank goodness for that 
I learned how to make the launcher smaller but even so I hate the clutter.
Thanks for the advice

---

### Post by Mr. Shannon on 2011-12-07
If you upgrade to 11.10 switching to gnome classic will no longer work as it drops support for gnome 2.  The other gnome option (besides Unity) in 11.10 is gnome shell (which I think has to be installed) which also operates in this very Mac OSX way.  Gnome shell even goes further by removing the minimize button all together, though it can be added back in.

One possibility for when you upgrade is to try out Linux Mint.  It is a derivative of Ubuntu but uses gnome shell and has a custom made bar at the bottom similar to the old gnome bar.  It also re-enables the minimize button by default.

---

### Post by matteosistisette on 2011-12-07
Thank you, but I don't want to switch to gnome (at least unless unity really proves to be inferior but I'm confident it was chosen for a reason).

I would like to configure Unity so that I have the minimized icons separated from launcher icons, preverrably on the bottom of the screen.

I guess that can be done, can't it? (otherwise yes, I will seriously consider switching to gnome)

---

### Post by matteosistisette on 2011-12-07
OH MY GOD I hadn't noticed this horrible new scroll bar thing. Now THAT's insane. Is it possible to have normal scroll bars in Unity?

---

### Post by Mr. Shannon on 2011-12-07
Below is a link to some instructions for adding a taskbar to Unity.  Though it may partially cover the bottom of Unity's sidebar.

[http://www.liberiangeek.net/2011/10/add-taskbar-in-ubuntu-11-0411-10-with-panel-tint2/]("http://www.liberiangeek.net/2011/10/add-taskbar-in-ubuntu-11-0411-10-with-panel-tint2/")

NOTE: I have not tried this.

**EDIT:** To return to the old scroll bar enter the folowing command in a terminal

```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.1-0

```

This was taken from [http://mikebeach.org/2011/05/20/disable-the-overlay-scrollbars-in-ubuntu-natty/]("http://mikebeach.org/2011/05/20/disable-the-overlay-scrollbars-in-ubuntu-natty/") which tells you how to add them back if you decide to.

---

### Post by mcduck on 2011-12-07
While there's no way to alter the grouping of icons in Unity's launcher bar, there's a simple and easy way to make the difference between a running application and a launcher for non-running app more clear. Just set Unity to only highlight running app icons instead of all icons.

You can do that with CompizConfig Settings Manager, the option for highlighting mode is in the Unity-plugin's options under the Experimental-tab.

(what comes to sorting, runnign apps that aren't pinned to the launcher should already appear underneath pinned ones by default.)

---

### Post by mcduck on 2011-12-07
If you don't feel Unity to be clean looking you are just as able to switch to a more lightweight and clutter-free desktop environment/window manager as you were before. The _only_ DE you can't have any more is Gnome2, which definitely isn't a decision anybody could claim Unity's (or even Ubuntu developers') fault. (besides, the Classic mode of Gnome3 is as close to old Gnome desktop as one could relistically hope to get considering how new Gnome 3 is and that pretty much everyhting in the background has changed)

---

### Post by Jay Car on 2011-12-07
> **matteosistisette said:**
> Thank you, but I don't want to switch to gnome (at least unless unity really proves to be inferior but I'm confident it was chosen for a reason).

I would like to configure Unity so that I have the minimized icons separated from launcher icons, preverrably on the bottom of the screen.

I guess that can be done, can't it? (otherwise yes, I will seriously consider switching to gnome)

Ok, I understand your feelings. Many of us have gone through that same sense of disbelief and puzzlement.  However, once we began to understand the types of changes that have happened, we've learned to start working with what is at hand. 

If you really want to learn how to use Unity, I would suggest starting [here]("http://fridge.ubuntu.com/2011/04/21/the-power-user%E2%80%99s-guide-to-unity/"). 

It's true that the old Gnome is no longer available after Natty, but since Natty is what you are using now, there's no reason NOT to use it as a temporary "fix" while you familiarize yourself with Unity.  

I still have Natty and Gnome2 on my work computer.  It's familiar and stable and I can concentrate on work projects instead of fussing with Unity.  However, I also have Oneiric installed on another computer, and I spend some hours each weekend learning more about it all, I wouldn't say I truly like Unity, but I can use it now, and not feel like I'm fighting with it.  Progress comes in small steps sometimes.  :)

Just stay calm, be patient and think things through.  

:)

---

### Post by mystika1 on 2011-12-07
Lubuntu would be a better choice if you want lightweight, fast, and fully customizable. I love it. I used Unity and really learned to deal with it for a while but when I decided to try Lubuntu I was amazed at the speed of my machine. I also realized how restrictive Unity really is...unless you have hacks you just can't change any settings except for the icon size and wallpaper. Sorry..I don't hate Unity at all, but I like to make my desktop my own. 

Penny

---

### Post by mcduck on 2011-12-07
> **mystika1 said:**
> Lubuntu would be a better choice if you want lightweight, fast, and fully customizable. I love it. I used Unity and really learned to deal with it for a while but when I decided to try Lubuntu I was amazed at the speed of my machine. I also realized how restrictive Unity really is...unless you have hacks you just can't change any settings except for the icon size and wallpaper. Sorry..I don't hate Unity at all, but I like to make my desktop my own. 

Penny

"hacks"? ;)

Gnome-tweak-tool and dconf-editor are all you need, and both are official parts of the Gnome project. (although both these aren't really even related to Unity, but Gnome instead. Stuff like wallpaper, theme or colors have nothing to do with Unity so if it's that kind of customization you are after then blaming Unity for lack of them is barking at the wrong tree...

Of course if you are looking for settigns for that *really* are related to Unity, the tools would be CompizConfig Settings MAnager (as official tool as it gets for editing Compiz settings, including Unity plugin) and dconf-editor. :)

---

### Post by nothingspecial on 2011-12-07
This is a support thread. If you have some advice please offer it. If you want to moan, do it elsewhere.

---

### Post by mystika1 on 2011-12-07
Pardon me if I have offended anyone, but when I installed ubuntu 11.04 the only thing that you could change on the desktop appearance out of the box was the wallpaper and a unity plugin had to be installed in compiz to change icon size in the side bar. There were other settings in that plugin but when I changed anything else things went south and I would have to revert to the original settings. There are lots of threads here discussing this. I used it for six months and had to install outside apps to do basic changes. For example, when I say it was not configurable it was because I could not move the unity side panel to any other side and had to keep it on the left. If this has changed then please correct me. 

I suggested Lubuntu because the features that the OP is asking about are default and would require no effort to attain.(without having to install outside apps** and extra panels**) the OP was concerned about clutter...
 That is my point. :) 

My suggestion was not made to offend and not to bash Unity... The OP seems to want to configure the desktop(and asked about it) and I gave my honest opinion based on what I experienced.

Sincerely,

Penny

---

### Post by Tim1361 on 2012-01-22
No need to apologize. You are right. 

I too am frustrated beyond words with Unity.. I know they want one interface for phone to tablet to computer but I work on a 20" monitor. Making icons small is fine for me because I have a mouse but no we have to use the smallest a human finger would use on tablet or phone is silly. 

I really hope Ubuntu doesn't die on this one because it is one hell of a good system but Ubuntu, "you are not apple, get over it" keeps going through my mind. You are great in your own right so don't try to be something you are not and definitely don't try to be all things to all people on all platforms as that is a sure road to ruin.

thanks for the idea mcduck but compiz manager doesn't have highlight under experimental or anywhere else I can find.

My wish list of things that should be simple:

changing an icon in the launcher easily
changing the size of an icon in the launcher below "32"
displaying running icons differently or putting running programs in a  different location
grouping icons in a cascading fashion (ie games, internet, work, home etc)

Not trying to rant here but I've been using Ubuntu for more than 5 years and this is not impressive. If anything it is a step towards the "do it the way we tell you" of Apple and Microsoft that I left those platforms because of.

---

