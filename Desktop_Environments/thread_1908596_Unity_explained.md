---
title: "Unity explained"
date: 2012-01-13
forum: Desktop Environments
---

### Post by jorpoveda on 2012-01-13
I have used Ubuntu before back when it used GNOME 2 and I really like it a lot. Now I have start using it again and I find out that now it includes Unity. If it is not too much problem, can someone explain me the advantages of Unity. How can I add or remove apps, position? Is it possible? 

I also remember that I use to have "Home Folder" icon in the desktop. Can I visualise it again? 

Thank you.

---

### Post by trikster_x on 2012-01-13
> How can I add or remove apps, position?

You can add apps by dragging them from the app search menu, accessed through the dash home button. Simply drag them to the bar and drop them in place. You can remove an icon by right clicking on it and unchecking "Keep In Launcher".

>  "Home Folder" icon in the desktop.

Not sure how to do this, but there should be an icon in the unity dock bar for the home folder.

>  can someone explain me the advantages of Unity.

The only real advantage I have noticed to using Unity over Gnome is it is much less intimidating to new users. This is mainly because their is very little actual utility. You can drag new icons in, delete unnecessary ones, and do a quick search for apps. Beyond that there are very few things that can be customized. If you want to make a custom launcher, good luck messing with the icon files. 

IMHO Unity is still absolutely not ready for use as Canonical's main desktop environment. The dash is completely unpolished(why so many clicks to get a full view of my system apps?) and cluttered. Using options that were once working perfectly now causes major problems(still trying to figure out why "always on top" = "always focus window"). While Canonical has done some great things with the DE, I can't help but wonder if they could have done them without using Unity.

---

### Post by StewartM on 2012-01-13
What trikster_x said.

I would add one thing that I think helps tame Unity. It's un-auto-hiding the launcher. You can do that *without installing CompizConfig Settings Manager (ccsm)*, which most tutorials recommend. I would not install ccsm, especially not a relative newbie, as if some people have reported wrecking their systems using that.

Instead, use gconf-editor.

Open it and go to apps | compiz1 | plugins | unityshell | screen0 | options 
 
and set the launcher_hide_mode to '0' (Never hide).

That means at least switching between active windows can be done with a single click (i.e., as they appear in the launcher when opened).

I found the above bit of advice in a web forum, but I can't find it again via google. But it worked for me.

> **trikster_x said:**
> 
IMHO Unity is still absolutely not ready for use as Canonical's main desktop environment. The dash is completely unpolished(why so many clicks to get a full view of my system apps?) and cluttered. Using options that were once working perfectly now causes major problems(still trying to figure out why "always on top" = "always focus window"). While Canonical has done some great things with the DE, I can't help but wonder if they could have done them without using Unity.

Unity has driven me to trying out KDE and Lubuntu. 

Unity only makes sense for small screens, tablets and smartphones. That's why the oversized icons and top-panel menus. It would be much improved if desktop/laptop users had at least the option of moving the dock, of putting menus back on the top of windows, of shrinking the icons and launchers. I can use it, and it's an OK desktop for those who don't do much with their system but surf the web, check email, and the like, but it's not good for anyone approaching a power user. It's the least customizeable Linux desktop around (though GNOME 3 comes close, I have hope that GNOME will add back elements of GNOME 2).

-StewartM

---

### Post by bryanl on 2012-01-13
interesting how change influences people.

The 'home' folder is usually the second icon down on the launchpad.

System utilities are a selection in the icon at the top right (along with shutdown) and you can always hit the 'super' (windows) key and type in a few search letters. 

The applications center is also in the launchpad and it allows finding new apps, removing ones you don't want on your system, and seeing what others think of them.

cluttered is an interesting judgment as Unity tends to inhibit clutter  --- one of the main complaints is that it is difficult to fill the desktop with icons and other such truck.

Just because it's different doesn't mean it's bad -- and sometimes learning something a bit different can be profitable. (but it is easier, often, to just gripe ...)

Used to be just looking at UI upgrades was interesting -- Windows has done it several times. With Unity, watching the behavior on these forums is sometimes more interesting.

---

### Post by trikster_x on 2012-01-13
> **bryanl said:**
> 
cluttered is an interesting judgment as Unity tends to inhibit clutter  --- one of the main complaints is that it is difficult to fill the desktop with icons and other such truck.

Just because it's different doesn't mean it's bad -- and sometimes learning something a bit different can be profitable. (but it is easier, often, to just gripe ...)

I typed that from the viewpoint of some one who used launchers with custom shell scripts to make my desktop run the way that is most efficient for me. It used to be a matter of clicking on the main menu, hover over a category and open desired program. Now I have to click the dashboard button, click on find apps, click on filter, and click on installed apps just to see a list of apps in that category. Sure, I can use the search feature, **IF** I know what the specific name of the app I need is. While I like the frequently used apps feature, that should be on the initial dash window. Otherwise its only purpose is to clutter my search for the app I need. And the "Apps Available for Download"? That would be fine if it would disappear when I filter my app selection. If I want to search for an app to download, I will open the Software Center.

God forbid I want to make my own launcher. Then I have to create a .desktop file just to describe its function and give it an icon. Used to be able to right click on it, drag an icon image and type a quick shell command. And if I accidentally leave the text editor while I create it, then I have to understand how to use a terminal to finish it.

It's not the fact that it is different that makes it bad, it's the fact that it is bad that makes it bad. I see tons of potential in Unity, and I hope one day it lives up to its full potential. But as it stands I wish I still had my Ubuntu 10.04 live CD.

---

### Post by mcduck on 2012-01-14
> **trikster_x said:**
> I typed that from the viewpoint of some one who used launchers with custom shell scripts to make my desktop run the way that is most efficient for me. It used to be a matter of clicking on the main menu, hover over a category and open desired program. Now I have to click the dashboard button, click on find apps, click on filter, and click on installed apps just to see a list of apps in that category. Sure, I can use the search feature, **IF** I know what the specific name of the app I need is. While I like the frequently used apps feature, that should be on the initial dash window. Otherwise its only purpose is to clutter my search for the app I need. And the "Apps Available for Download"? That would be fine if it would disappear when I filter my app selection. If I want to search for an app to download, I will open the Software Center.

God forbid I want to make my own launcher. Then I have to create a .desktop file just to describe its function and give it an icon. Used to be able to right click on it, drag an icon image and type a quick shell command. And if I accidentally leave the text editor while I create it, then I have to understand how to use a terminal to finish it.

It's not the fact that it is different that makes it bad, it's the fact that it is bad that makes it bad. I see tons of potential in Unity, and I hope one day it lives up to its full potential. But as it stands I wish I still had my Ubuntu 10.04 live CD.
Actually you can still create Launchers usign graphical tool, and the tools used are exactly the same as before (the oly difference is that you don't get the option for new launcher in right-click menu, most likely because Gnome 3 doesn't use desktop icons (including launchers) by default.

Still, Alacarte works just like before, and if you want to create a launcher from right-click menu you can create an empty one in your Templates directory. Taht allows you to right-click, select Templates->new launcher, and then just right-click the newly created launcher to access it properties and configure the icon, command etc. there.

What comes to finding apps with the search, keep in mind that it's not only searching the application name but also the description. So as long as your programs and scripts have proper descriptions in their launchers, finding whhat you want shouldn't be hard at all even if you don't know the exact name. (For example searching for "photo" will display both "Shotwell Photo Editor" and "Gimp Image Editor", even though Gimp doesn't have "photo" in it's name.)

I'm actually finding Unity quite usable, and defintiely a quick interface to use compared to most others. But I can sure see how annoying it would be if one tried to use it with the mouse. I suppose the idea behind the design is that power users would quickly learn the few simple keyboard shortcuts it takes (and would most likely prefer shortcuts over mouse navigation anyway), while the mouse navigation and interface is designed more towards less technically oriented people.

---

### Post by MG&amp;TL on 2012-01-14
I feel duty-bound to point out that a) some people like Unity

b) gnome 2 was dead anyways

c) Feel free to use any other desktop environment.

d) Looking back, I see every other DE being criticised at a new release. Even GNOME2, from whatever GNOME1 was. So...give it time, and then there will be uproar at Unity being ditched.

---

### Post by jorpoveda on 2012-01-14
Well I must say it was really good to read all these varied opinions. I think that Unity is not bad at overall, I have been using it and giving it the chance and it is not bad at all. It was really helpful to know about the "super" key shortcut, are there any others?

Thank you all for your impressions about Unity, they were really helpful for me.

---

### Post by MG&amp;TL on 2012-01-14
[http://www.webscopia.com/2011/10/unity-basics-and-keyboard-shortcuts-in-ubuntu-11-10-oneiric-ocelot/]("http://www.webscopia.com/2011/10/unity-basics-and-keyboard-shortcuts-in-ubuntu-11-10-oneiric-ocelot/")

---

### Post by matza55 on 2012-01-14
> **StewartM said:**
> What trikster_x said.

I would add one thing that I think helps tame Unity. It's un-auto-hiding the launcher. You can do that *without installing CompizConfig Settings Manager (ccsm)*, which most tutorials recommend. I would not install ccsm, especially not a relative newbie, as if some people have reported wrecking their systems using that.

Instead, use gconf-editor.

Open it and go to apps | compiz1 | plugins | unityshell | screen0 | options 
 
and set the launcher_hide_mode to '0' (Never hide).

That means at least switching between active windows can be done with a single click (i.e., as they appear in the launcher when opened).

I found the above bit of advice in a web forum, but I can't find it again via google. But it worked for me.



Unity has driven me to trying out KDE and Lubuntu. 

Unity only makes sense for small screens, tablets and smartphones. That's why the oversized icons and top-panel menus. It would be much improved if desktop/laptop users had at least the option of moving the dock, of putting menus back on the top of windows, of shrinking the icons and launchers. I can use it, and it's an OK desktop for those who don't do much with their system but surf the web, check email, and the like, but it's not good for anyone approaching a power user. It's the least customizeable Linux desktop around (though GNOME 3 comes close, I have hope that GNOME will add back elements of GNOME 2).

-StewartM

Thanks for the tip!

---

### Post by matza55 on 2012-01-14
> **bryanl said:**
> interesting how change influences people.

The 'home' folder is usually the second icon down on the launchpad.

System utilities are a selection in the icon at the top right (along with shutdown) and you can always hit the 'super' (windows) key and type in a few search letters. 

The applications center is also in the launchpad and it allows finding new apps, removing ones you don't want on your system, and seeing what others think of them.

cluttered is an interesting judgment as Unity tends to inhibit clutter  --- one of the main complaints is that it is difficult to fill the desktop with icons and other such truck.

Just because it's different doesn't mean it's bad -- and sometimes learning something a bit different can be profitable. (but it is easier, often, to just gripe ...)

Used to be just looking at UI upgrades was interesting -- Windows has done it several times. With Unity, watching the behavior on these forums is sometimes more interesting.

Many icons on desktop - someone said that it slows down the pc? Is it true?

---

### Post by bogan on 2012-01-14
Hi!,** mcduck**,

You Posted:>  Actually you can still create Launchers usign graphical tool, and the  tools used are exactly the same as before (the oly difference is that  you don't get the option for new launcher in right-click menu, most  likely because Gnome 3 doesn't use desktop icons (including launchers)  by default.

Still, Alacarte works just like before, and if you want to create a  launcher from right-click menu you can create an empty one in your  Templates directory. Taht allows you to right-click, select  Templates->new launcher, and then just right-click the newly created  launcher to access it properties and configure the icon, command etc.  there. Could you please explain in detail how to create a Launcher in 11.10.
With previous versions of ubuntu I found the right-click method of creating a custom Launcher quite straight forward and easy.
I am running logged in to Gnome Classic (Gnome3 ) with Unity 2D Launcher. But your description is meaningless to me.
Are Alacarte and Taht programs I need to load ? ( neither bring any response from Software Center). 
Or is there something in gconf or ccsm that I need to initiate.??

I find it surprising that the opinions about Unity in this Thread make no mention of the effective absence of Panels in Unity. Though they are still fully available when logged in to Gnome Classic.

Chao!, **bogan**

---

### Post by mcduck on 2012-01-14
Sorry about the typos, it's just "that", not "Taht, the lancher creating tool". ;)

Anyway, you don't need any additional tools for creating a launcher, the necessary stuff is already there. But using Alacarte has the benefit that the launchers you create will also be available in all the various menus on different desktop environments, including Unity's Dash menu & searches. (and you can of course drag it from the menus to your desktop if you like having desktop icons for your apps)

[apt:alacarte]("apt:alacarte")

One installed it wll appear with the name "Main Menu", just like in Gnome 2 desktop. (Also it's the same tool you got in Gnome 2 if you clicked the Applications-menu and selected "Edit Menus")

...and using it is simple, just browse into the category where you want to add a new launcher and click the "New Item"-button.

What comes to the other method I suggested, all you need is an basic .desktop file (the file type used for launchers). Put it into ~/Templates and rename it something like "New Application Launcher" or whatever you like. After that to create a new launcher you right-click and select Create New Document-> New Application Launcher and you get a new empty launcher. Right-click and go to Properties, and you'll be able to set the icon, name, command and comments there.

In case you want to try the template way, here are the contents of a basic launcher .desktop file. Just paste it into a new text file and save as "New Application Launcher.desktop or something like that):
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=
Exec=
Name[en_US]=Application launcher
Comment[en_US]=
Name=
Comment=
Icon=
```

---

### Post by jorpoveda on 2012-01-14
Thanks for the template to create the basic launcher.

---

### Post by bogan on 2012-01-15
[SIZE=2]Hi!, **mcduck**,

Thanks for your explanation and the template.

I was puzzled why entering "alacarte" in the Ubuntu Software Search box produced "Main Menu" as the only item found; evidently "alacarte" is a Alias well known to the system.

I was aware of the "+ New Item" option in Edit Menu, but assumed it meant a new Menu entry, and had not tried it until now.

As far as the Template method is concerned, I followed your instructions to the limit of my my understanding, but a Right Click on the Desktop screen gives "No templates installed", when I select 'Create new document.'
I assumed that "~/.Template" meant a Hidden Folder in the Root directory, ie the one in which /etc and /Home are to be found.
 As I could not find anything of that name with 'Show Hidden Files' activated, I entered:[/SIZE]```
root@alan-MS-7318:/home/alan# cd
root@alan-MS-7318:~# mk[SIZE=2]dir .Templates
root@alan-MS-7318:~#[/SIZE]
```[SIZE=2]as that did not produce any visible results, I entered:[/SIZE]```
root@alan-MS-7318:~# mkdir ~/.Templates
mkdir: cannot create directory `/root/.Templates': File exists
root@alan-MS-7318:~#
```[SIZE=2]
I then copy pasted your template to Gedit but the system would not allow me to save it to ~/.Templates, or to /root/.Templates, so I saved it to Desktop.[/SIZE]```
root@alan-MS-7318:~# gksu nautilus
```[SIZE=2] then allowed me to copy it from there to /root/.Templates

But presumably that is not the same as ~/.Templates;
 so I copied the .Templates folder to the previous folder level, ie where Home is.

I also tried with the NewLauncher file renamed as: ".NewLauncher", as in ".desktop", and re-booting, logging in both to Gnome Classic and to Ubuntu, but none of these succeeded. It still produced the "No templates installed" message.

In my ignorance of the niceties of Root addressing what am I[/SIZE] doing wrong?

Chao!,** bogan**

---

### Post by MG&amp;TL on 2012-01-15
Nope, "~/" is a bash alias for $HOME, whatever that may be. If you're root, it's probably /root/, if you're normal, it's probably /home/bogan/ or whatever.

---

### Post by bogan on 2012-01-15
Hi!, **mcduck** &** MG&TL**,  Now I am even more confused  than I was before:
 
MG&TL Posted> :..."~/" is a bash alias for $HOME, whatever that may be. If you're root, it's probably /root/, if you're normal, it's probably /home/bogan/ or whatever.Which I take to mean that "$HOME" is not neccessarily the same as "/home" and ~/home is yet something else.
When I open a normal Terminal the prompt does not show the CD,```
  alan@alan-MS-7318:~$ dir
BackUp     Documents  examples.desktop  Music    Public       vbeinfo
Desktop  Downloads  grub          Pictures    Templates  Videos
alan@alan-MS-7318:~$ 
```Wheras a ROOT Terminal shows it as /home/alan#.
 If I then enter 'cd' it goes to /root, though it does not show it except with "~#". ```
 root@alan-MS-7318:/home/alan# dir
BackUp     Documents  examples.desktop  Music    Public       vbeinfo
Desktop  Downloads  grub          Pictures    Templates  Videos
root@alan-MS-7318:/home/alan# cd
root@alan-MS-7318:~# dir
Desktop  more  xorg.conf
root@alan-MS-7318:~# 
```So it seems "/root" to be root folder inside the folder I thought was Root, and a home directory inside /home, or maybe it is vica versa ??.

Anyway, I copied the "NewLauncher" (without the dot) file to an empty "Templates"(also minus the '.') folder I found in /home, and Eureaka! 

Right-Click>Create New Document> now gives me a "NewLauncher" option as well as "Empty Document".

Chao!, **and many thanks, bogan**.

---

### Post by mcduck on 2012-01-15
> **bogan said:**
> [SIZE=2]
As far as the Template method is concerned, I followed your instructions to the limit of my my understanding, but a Right Click on the Desktop screen gives "No templates installed", when I select 'Create new document.'
I assumed that "~/.Template" meant a Hidden Folder in the Root directory, ie the one in which /etc and /Home are to be found.

Sorry, that's my bad. :)

It's *~/Templates*, not *~/.Templates*. I always rember it as a hidden directory as I've actually hidden it on my desktop using the .hidden file trick... :D (if you create a text file called ".hidden" you can add any file and directory names from the same directory where the .hidden file is, one per each line, to hide them in Nautilus without renaming the files.)

And like MG&TL said, ~ is an alias for your home directory. So just create a directory called Templates in your home and you can then add any template files you want there and they'll the appear in Right-click->Create New Document.

(you might have to log out and back again after creating the template directory before Nautilus recognizes it.)

---

### Post by mcduck on 2012-01-15
> **bogan said:**
> Hi!, **mcduck** &** MG&TL**,  Now I am even more confused  than I was before:
 
MG&TL PostedWhich I take to mean that "$HOME" is not neccessarily the same as "/home" and ~/home is yet something else.
When I open a normal Terminal the prompt does not show the CD,```
  alan@alan-MS-7318:~$ dir
BackUp     Documents  examples.desktop  Music    Public       vbeinfo
Desktop  Downloads  grub          Pictures    Templates  Videos
alan@alan-MS-7318:~$ 
```Wheras a ROOT Terminal shows it as /home/alan#.
 If I then enter 'cd' it goes to /root, though it does not show it except with "~#". ```
 root@alan-MS-7318:/home/alan# dir
BackUp     Documents  examples.desktop  Music    Public       vbeinfo
Desktop  Downloads  grub          Pictures    Templates  Videos
root@alan-MS-7318:/home/alan# cd
root@alan-MS-7318:~# dir
Desktop  more  xorg.conf
root@alan-MS-7318:~# 
```So it seems "/root" to be root folder inside the folder I thought was Root, and a home directory inside /home, or maybe it is vica versa ??.

Anyway, I copied the "NewLauncher" (without the dot) file to an empty "Templates"(also minus the '.') folder I found in /home, and Eureaka! 

Right-Click>Create New Document> now gives me a "NewLauncher" option as well as "Empty Document".

Chao!, **and many thanks, bogan**.

Ok, I'll try to explain these directories and shortcuts...

/ is the root of the filesystem, also known as the root directory.

There's also a user account called "root", and /root is that user's home directory.

/home contains the home directories of all normal user accounts.

...and both ~ and $HOME are aliases for the current user's home directory, /home/*username*.

---

### Post by Grez on 2012-01-15
Hi guys.

Here's my four pennorth on Unity...

Initially I found it clunky and unfamiliar as most of us did. however, after using it for a few weeks and looking up some tips and tricks, I actually like using it... and in some cases better then GNOME 3.

One of the things I did was to install Avant Dock (awn) from the Software Centre, and I put on a main menu app, which now gives rather old-fashioned acces to the apps similar to the drop-down lists in GNOME 2. So if I'm in a hurry, I look in there.

I've got my favourite programs pinned into the unity launcher for quick access, and I also have, at the moment, a list of the keyboard shortcuts in front of me, showing the Super-key (Windows-key) shortcuts for all manner of stuff. I like the idea of expo mode so I can look at all my open apps at once; also using Super+S to look at all my desktops at once, which I find as useful, if not more so than the old way of using the bottom bar with the buttons on it.

I suppose it's a question of how you wlike to work and whatever floats your boat. I know it's still a work in progress, but I reckon, as with GNOME 2, once I'm used to it, I'll find a lot of useful ways of using it.

So shoot me down......

:)

---

