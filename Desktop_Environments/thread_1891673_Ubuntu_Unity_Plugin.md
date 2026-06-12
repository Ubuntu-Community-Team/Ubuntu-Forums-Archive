---
title: "Ubuntu Unity Plugin"
date: 2011-12-06
forum: Desktop Environments
---

### Post by Gael33 on 2011-12-06
After giving Gnome 3 desktop environment a try, I decided to revert back to Unity. I completely purged Gnome 3, logged in as Ubuntu 2D and found that the Ubuntu Unity Plugin wasn't functioning correctly. I wanted to shrink the icons in the side bar but nothing happens. Any ideas?
PS. Yes, the plugin is ticked in Compiz :)

---

### Post by vasa1 on 2011-12-06
But the plug-in is for Unity 3D, not for Unity 2D. Unity 2D doesn't use compiz, AFAIK.

---

### Post by Gael33 on 2011-12-06
> **vasa1 said:**
> But the plug-in is for Unity 3D, not for Unity 2D. Unity 2D doesn't use compiz, AFAIK.


Okay, I now understand :)

Checking my login menu, I don't have a way of getting back to Ubuntu Unity 3D ... there is probably a solution to fix this that I don't know of ... perhaps you or someone else could point me in the right direction, thanks.

---

### Post by ingeva on 2011-12-06
> **vasa1 said:**
> But the plug-in is for Unity 3D, not for Unity 2D. Unity 2D doesn't use compiz, AFAIK.
Evidently not. I hate the Unity interface, so I tried Ubuntu 2D. The Compiz configuration did not work for anything, and after experimenting with it I returned to "3d". Now whenever I start a program it's in full screen mode. This gives me real stomach pain, and I have no idea how to fix it. Can anyone give me a tip?

Also, is there a way to put icons into the top panel (moving the menu bar back where it belongs) , or to make the launch icons smaller than 32? I would prefer 24 or even 16, to eliminate the need for scrolling.

Oh, and how can I add shortcuts to the launch panel except by installing?
(After a month or so I discovered how to move them. Canonical has sure gone out of their way to make things complicated! :( )

(BTW, I hate the "dash" too. Gives me the impression that I have changed to a Mac computer or something, with a learning curve starting from scratch), and disturbing whatever else on my screen).

---

### Post by grahammechanical on 2011-12-06
@Gael33

Try opening the Ubuntu Software Centre and searching for Unity 3D. Is Core Library of the Unity interface (Libunity-core-4.0-4) installed? If not install it. You may have removed the Unity 3D libraries when installing Gnome 3 Shell. It will take a restart to get the Ubuntu option at the login screen.

@ingeva

If you have CompizConfigurationSettingsManager (CCSM) installed you can find it in the Dash by searching Compiz. Open the utility and put a tick mark against the Unity Plugin and the click the label Ubuntu Unity Plugin and you will get options to modify Unity including Launcher icon size. It is under the Experimental tab and you use a slider to reduce the size of the icons.

Oh, I have just noticed that you want the icons smaller than that modification allows. Sorry, for getting it wrong. Please ignore the above.

Regards.

---

### Post by ingeva on 2011-12-06
> **grahammechanical said:**
> @Gael33

Try opening the Ubuntu Software Centre and searching for Unity 3D. Is Core Library of the Unity interface (Libunity-core-4.0-4) installed? If not install it. You may have removed the Unity 3D libraries when installing Gnome 3 Shell. It will take a restart to get the Ubuntu option at the login screen.

Thanks, but now the dash won't open, and I can't find the software centre.... :(

---

### Post by wildmanne39 on 2011-12-06
Hi, try hitting ctrl+alt+t then type software-center.
Thank you

---

### Post by ingeva on 2011-12-06
> **wildmanne39 said:**
> Hi, try hitting ctrl+alt+t then type software-center.
Well, I found myself running 11.10 after a software update (I was running 11.04) and since a big software assignment was finished I decided to spend some time investigating the Unity interface. It has many surprises, and most of them are not very good.
I wonder, can some help me with the following problems:

1. Programs always start in full screen mode. Full screen gives me stomach pain, and every time I start a program I have to use several mouse and keyboard clicks to bring it in order.
Only the startup manager start programs normally.
2. Sometimes, window borders disappear, making it impossible to move or resize windows (Alt-F7/8 doesn't work either).
3. Sometimes windows have a fixed height from top to bottom of screen, and they are impossible to resize.
4. Launcher icons can't be smaller than 32. That is much too big, making it necessary to scroll the launcher. It should be possible to reduce the size to about 16.
5. How can I open an additional panel, making room for more program icons?
6. How can I get the menu bar to appear below the title bar where it belongs?
7. How can I change the icon associated with a program in the launcher?
8. There's no "Restart" option in the shutdown menu. How do I add one?
9. Launcher won't start 2.nd instance of a program already running.

This is very frustrating. I didn't ask for a GUI change. The Gnome panels were ideal, unobtrusive, and fast. I do not understand why they should invent something as gruesome as Unity, but so far I have not been able to find anything better than Ubuntu so I'll make an effort and try to live with it. I tried Fedora and have never had a more negative experience with an OS, being even worse than Windows or Mac. I sure lost the wish to try Mandriva, Suse, or even Debian.

Ubuntu 2D is barely acceptable, Ubuntu 3D - far from it.

Help - if there is any?

---

### Post by wildmanne39 on 2011-12-06
Hi, you can use this link to get the new gnome classic for 11.10 it is not exactly as gnome2 but it is as close as you can get for now.

You can add things to the top panel by hitting atl+right click on the panel.
[http://ubuntuforums.org/showthread.php?t=1859960](http://ubuntuforums.org/showthread.php?t=1859960)

It is also possible that some of your problems are from doing an upgrade it is better to do a fresh install, I know you did not intend to upgrade but the result may be the same.
Thank you

---

### Post by ingeva on 2011-12-07
> **wildmanne39 said:**
> Hi, you can use this link to get the new gnome classic for 11.10 it is not exactly as gnome2 but it is as close as you can get for now.

You can add things to the top panel by hitting atl+right click on the panel.
[http://ubuntuforums.org/showthread.php?t=1859960](http://ubuntuforums.org/showthread.php?t=1859960)

It is also possible that some of your problems are from doing an upgrade it is better to do a fresh install, I know you did not intend to upgrade but the result may be the same.
Thank you
OK, thanks!
I actually did a fresh install and the list of problems were the ones remaining after that.
I have just re-installed 11.04 but I still have a 11.10 install in another partition, so I can continue experimenting when time allows.
I tried the "gnome-session-fallback" earlier and it didn't work. However, I'll try again. I may have done something wrong. It's a while ago, since I've been working on a software project.

I appreciate all help. I might have found out more by reading more in the forum, but the last couple of months I've just been too busy. However, I can see that I'm not the only one having problems with Unity. It's a premature a alfa version.

Hmmm.... Alt+right-click .... Clumsy for a left-hander! :)

---

### Post by Gael33 on 2011-12-07
Hi, I reset the Unity 3D desktop with this command; Ctrl + Alt + T, and in the terminal run command  unity --reset
It takes a little while to complete, so go have a coffee and come back in 20 minutes ... if completed, reboot and be amazed :)
It worked for me ...

---

### Post by vasa1 on 2011-12-07
> **Gael33 said:**
> Hi, I reset the Unity 3D desktop with this command; Ctrl + Alt + T, and in the terminal run command  unity --reset
It takes a little while to complete, so go have a coffee and come back in 20 minutes ... if completed, reboot and be amazed :)
It worked for me ...

Good to know things worked for you! :)

---

### Post by ingeva on 2011-12-07
> **vasa1 said:**
> Good to know things worked for you! :)
It is still working ... after nearly 3 hours.
Lots of error messages; files that do not exist.

LAST: I let it go for about 5 hours, and aborted because I was
going out and wanted to shut down the computer.
When I came back and rebooted, nothing was changed, except
now I get an annoying pop-up box that asks for my password
every time FireFox wants to use one of my saved ones.

I think I'll stick to 11.04 for another while, until the unity program works a little (NO, MUCH) better. I don't see much point in upgrading this time anyway - even if I could use the old Panel.

---

### Post by Ghouli on 2011-12-08
> **ingeva said:**
> It is still working ... after nearly 3 hours.
Lots of error messages; files that do not exist.

LAST: I let it go for about 5 hours, and aborted because I was
going out and wanted to shut down the computer.
When I came back and rebooted, nothing was changed, except
now I get an annoying pop-up box that asks for my password
every time FireFox wants to use one of my saved ones.

I think I'll stick to 11.04 for another while, until the unity program works a little (NO, MUCH) better. I don't see much point in upgrading this time anyway - even if I could use the old Panel.

Did you remove old settings from your home before you did fresh install? I have home on different partition, and had a number of problems with 11.10 when I did my install. Removed bunch of crap from home, did clean install and everything worked just fine. In 11.10 Unity seems much faster and more stable. Worth the upgrade in my opinion.

---

### Post by Stray Wolf on 2011-12-20
> **ingeva said:**
> 
1. Now whenever I start a program it's in full screen mode. This gives me real stomach pain, and I have no idea how to fix it. Can anyone give me a tip?

2. Also, is there a way to put icons into the top panel (moving the menu bar back where it belongs) , 

3. or to make the launch icons smaller than 32? I would prefer 24 or even 16, to eliminate the need for scrolling.

4. Oh, and how can I add shortcuts to the launch panel except by installing?
(After a month or so I discovered how to move them. Canonical has sure gone out of their way to make things complicated! :( )

5. (BTW, I hate the "dash" too. Gives me the impression that I have changed to a Mac computer or something, with a learning curve starting from scratch), and disturbing whatever else on my screen).

1. On my system the app opens in the same sized window as when it was last closed. I recommend you do a fresh install if you want to see how 11.10 works without all the hiccups that get carried over in an upgrade. I've never had an upgrade go smoothly. If you're not too short on patience you should try it.

2. You can add a classic gnome menu to your panel: 
***sudo add-apt-repository ppa:diesch/testing***
***sudo apt-get update***
[B][I]sudo apt-get install classicmenu-indicator
[/I][/B]You can also add indicators to you panel through the software center. Though the options are limited. There's also a way to move the Unity Launcher to the bottom. I just "Googled" it.

3. I've only used the Compiz Configuration Settings Manager (CCSM) to adjust the icons size in the launcher. I've never gone smaller than 35 so I checked and no, CCSM doesn't go smaller. Have you tried "MyUnity"? - [https://launchpad.net/~myunity/+archive/ppa]("https://launchpad.net/%7Emyunity/+archive/ppa")

4. You can use "alacarte" from the software center to create launchers and then move them to Unity.

5. I don't know if trying scopes would help give you an idea of where the dash seems to be going and how it could be useful. You can do a search for Unity Scopes or you can add the ppa - [http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu](http://ppa.launchpad.net/scopes-packagers/ppa/ubuntu).

I'm still waiting for 12.04 to make my final decision on the direction Ubuntu is going. Since Unity is new I think it deserves some time to develop. Personally, if Unity in 12.04 doesn't add some functionality to the launcher I'll be looking around for alternatives as well. The home launcher (and others) need sub-launchers for specific files and folders (Like sub-docks in cairo-dock). Each launcher should have right-click "contextual" menus with options specific to that launchers program. Being able to drag and drop launchers, files and folders and web page shortcuts from the Dash to the Desktop - from the Desktop to the Launcher and everything in between would be intuitive. Right now I can't put a link to this page on my desktop or launcher without a tedious workaround. Also, right-clicking a mounted drive used to give an option to format, not just dismount or remove safely. I'd like the format option back.

I figure the longer Unity is out the more ways there will be to customize it, and the more apps there will be to make that customization easy.

---

### Post by ingeva on 2011-12-20
> **Stray Wolf said:**
> 1. On my system the app opens in the same sized window as when it was last closed.
Thank you for a comprehensive response!
I have now re-ordered my partitions and made a separate home partition for testing other distributions. I just tried openSUSE 12.1 yesterday, but it also had Unity as the default, and if you go "classic" there's virtually nothing. Also, it installed virtually everything, so it took a lot of time.

The classic Gnome menu is fine, but not alone. I've used panels since Windows 2000 (I think) introduced them more than 10 years ago, and I can imagine nothing else. Gnome 2 allows you at least 3 panels, and the icons can be made real small so there's plenty of room for them. You can have spaces between them so they can be grouped nicely. Not like Unity which has only one panel (Launcher). The icons are way too big and they can't be grouped with any kind of separator.

I realize that things have to develop, and so far whatever I have tried has not been up to my requirements - except Ubuntu 11.04, which I run in classic mode, no effects - which means fewer annoyances.

I try to use my computer efficiently.  I never play games. It's all games, colors, flash, rounded corners and blinkenlichts nowadays. I think the default should always be the simplest (KISS). Those who want a lot of bling can add it for themselves. The desktop installation should have an option list so users could decide what to install, to reduce time and space. Only the "must have" should be installed automatically.

Right now I'm too busy for more experimenting for a while. I can't wait till 12.04 comes out, but I'm not too optimistic about it. If Canonical has some sense they'll rewrite Panels for Gnome 3 - or what about the simpler GUIs, XFCE and whatever? I think most serious users will be happier with a solution like that.

---

### Post by Stray Wolf on 2011-12-23
Right now, Unity doesn't seem too far off from cairo-dock which I've always used. So, anytime I installed before 11.10 (I skipped 11.04) I'd always have to immediately install and configure the dock. I kept the gnome-panel on auto-hide and auto-width in the upper-right hand corner as a sys-tray/notification area so my desktop for years has already behaved much like on Unity. Except I kept a cairo-dock bottom-center and a dock top-center on auto-hide. I think Unity's Dash (as more scope and lenses are developed) adds some functionality that cairo didn't have. But the gap of customization of behavior and appearance in Unity compared to cairo-dock is still pretty huge right now.  I like how the terminal on cairo-dock opened in a sub-dock. And it had a drop-down style main menu with all the categories you'd expect (office, internet, graphics, preference, administration, places, etc...). I thought the whole point of Ubuntu was to have enough control over your UI to individualize it to your taste and work-flow. I'm not convinced that it's lost that. But I do think it's diminished for the time being.

---

