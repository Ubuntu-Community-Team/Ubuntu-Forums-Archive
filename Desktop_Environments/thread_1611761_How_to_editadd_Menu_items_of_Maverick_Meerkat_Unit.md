---
title: "How to edit/add Menu items of Maverick Meerkat Unity Desktop??"
date: 2010-11-02
forum: Desktop Environments
---

### Post by fslurrehman on 2010-11-02
Hi
Few days ago, I installed ubuntu notebook **Maverick Meerkat** with **Unity Desktop **on my Fujitsu A530 Laptop.
My question is that:

**Q. How can I edit/add Main Menu items for this Unity Desktop? I would highly appreciate your help.**

Additional Details:

I edited the Menu Item from *'System>Preference>Main Menu'* but change is not reflected in Unity Desktop Item and Default Menu List of Application is displayed. :(

---

### Post by r_mano on 2010-11-06
I have the same problem. Moreover, my CrossOver Office installation add new top-level menu with applications, that are invisible in Unity (I have to start them form terminal-command line). I was not able to find a single "configure" option for Unity interface.

¿Any help?

---

### Post by slidingClouds on 2010-11-06
When you say "Main Menu" - do you mean: (1) the items that are displayed when you press the Ubuntu icon on the top-left of the screen; or, (2) the items in the pane on the left of the screen?

I can help you with (2) (- find and run the application you need, then right-click the icon in the left-pane and select "Keep in Launcher"). Still looking for (1).

Eli

---

### Post by r_mano on 2010-11-06
It was (2). I did discover the existance of (1) with your post :-).
Thanks, great. 

The other problem I think is a bug/feature, see [https://bugs.launchpad.net/unity/+bug/635223](https://bugs.launchpad.net/unity/+bug/635223)

---

### Post by fslurrehman on 2010-11-06
Thanks r_mano and slidingClouds 

About    (2): When I right click matlab software icon on launcher, it shows 'com-mathworks-util-PostVMlnit' and does not shows 'Keep in Launcher'.  

Except matlab program I have successfully docked Terminal and System Monitor programs to the launcher.

About   (1): I can not edit predefined main page with 6 icons of Web, Music, Photos & Videos, Games, Email & Chat, Office, File & Folders, Get New Apps. 

Also when I click from '*Applications (from Launcher)>System>Main Men', *I find my installed program of scilab under *Science Menu* whereas scilab program is there in *All Applications* list (when checked from launcher).

I have done extensive search  but only intro of unity desktop is given every where. I haven't found any help/documentation, or customization guide.

The bottom line is that [B]I cannot find any way to re organize or customize the grouping of my apps in launcher and main page of Unity Desktop of Maverick Meerkat. I need some help in this. 

[/B]

---

### Post by r_mano on 2010-11-06
Yep, I have the same problem with some application. For example, digiKam does not show the "keep in launcher" entry in launcher. 

Puzzled.

---

### Post by duanedesign on 2010-11-18
[There is a bug]("https://bugs.launchpad.net/bugs/657771") about the inconsistent appearance of the 'keep in launcher' option.

---

### Post by LinkMJB on 2010-12-04
Alright boys and girls, I spent some time tinkering with this tonight and found a solution using user preferences. I am considering writing a zenity front-end/(python/bash) backend to automate user input, bridging or to replacing "alacarte/Main Menu" functionalities to make this easier for the average user.

Here is what I have found so far ->
1) User customization is based in ~/.gconf/desktop/unity/launcher/favorites
2) Each application in your favorites has a directory within the favorites folder, and is indexed/referenced using the %gconf.xml
3) If you have already created a custom folder/application using alacarte/Main Menu, you should already have a file created under /usr/share/applications you can reference in the next step. Otherwise, make one using alacarte/Main Menu
4) cp -pr ~/.gconf/desktop/unity/launcher/favorites/app-firefox.desktop ~/.gconf/desktop/unity/launcher/favorites/app-[custom_name].desktop
6) vi ~/.gconf/desktop/unity/launcher/favorites/app-[custom_name].desktop/%gconf.xml
7) insert a line like so (inside the <gconf></gconf>):
[INDENT]<entry name="desktop_file" type="string">[/INDENT]
[INDENT][INDENT]<stringvalue>/usr/share/applications/[custom_name].desktop</stringvalue>[/INDENT][/INDENT]
[INDENT]</entry>[/INDENT]
8) Logout and log back in, or restart gdm ('sudo restart gdm')

NOTE: I assume similar things can be done to add programs into "Applications", but I expect it will live under /usr/share and effect ALL users...

Have fun! I will post back here when/if I create the GUI front-end to handle these steps, and provide a method to retrieve the .deb package

---

### Post by LinkMJB on 2010-12-08
I finished the frontend to handle menu creation, I named the tool "prixfixe" as a pun on "alacarte." This is meant only as a TEMPORARY solution for this problem until freedesktop.org gets their act together and provides a solution that works with Ubuntu + Unity.

While writing it I discovered a lot of broken functionality in gksudo (multiple command parsing, and random X display disconnects), and zenity (--question returns 0 ALWAYS, and does not return y/n).

Here is the URL for what I built if you are interested:
[prixfixe]("https://m4s73rz.ath.cx/matt/software/prixfixe.deb")

Install it using 'sudo dpkg -i prixfixe.deb'

Enjoy!

---

### Post by Rocket J Squirrel on 2010-12-09
Hey LinkMJB, thanks for working on this! Couple questions: after installing prixfixe, how do we launch it and how do we use it? Can you give an example of adding a menu item to Unity's launcher thingy?

---

### Post by LinkMJB on 2010-12-10
Hey Rocket,

Once you install the package, you should be able to logout and log back in and see it available in your favorites on the left side of the screen (this is assuming you are using Maverick Meerkat, with Unity as your display manager). 

To run the program, simply click the PrixFixe icon in the favorites dock or run prixfixe from command line (as user, not root), and follow the on-screen gui prompts.

After this, logout/login and you should have a menu item created based on the information the gui received from you. At this time prixfixe menu items require the logout/login since I didn't spend enough time figuring out what tickles Unity to reload the menu bar. The most I started to pick up on were /usr/share/applications/bamf.conf, bamfdaemon, dbus, and gdm.

It ended up being easier just to have the user logout/login ;)

---

### Post by Rocket J Squirrel on 2010-12-10
Thanks, LinkMJB. One final question: what information about the application I want to put on the launcher thingy do I need to gather before starting prixfixe?

---

### Post by LinkMJB on 2010-12-10
Hey Rocket,

Approach using PrixFixe the same way you would Alacarte... the gui will walk you through everything you need to know, and if it needs a file path (for the program you want to run, and the icon you want to use) it will popup a file navigation window for you to pick the program/icon.

The following are each question PrixFixe will ask:
1) Program name
[INDENT]This will end up being what the program is called in the favorites menu. It is also important you choose something UNIQUE here. i.e. -> If you have "firefox" as an application you are making the menu for, don't name it "firefox" in fear you may overwrite the official menu item for it in "applications". Something like "firefox-launch" or "firefox-fav" would be better[/INDENT]
2) Program Description
[INDENT]Enter whatever you like here, to describe the program you are making a menu entry for[/INDENT]
3) Program Icon
[INDENT]Choose any icon you would like to use for the menu item. If you are making one for a program that already exists, you can choose the same one if you want. You can figure out what other programs are using their icon as by looking at '/usr/share/applications/[program_name].desktop'[/INDENT]
4) Program Path
[INDENT]This will be what the menu item executes when you click it. You can figure out what other programs call by looking at the same file I listed above, or by trying this command: 'which [program_name]'[/INDENT]
5) Program Type
[INDENT]These are the different sections that exist under "Applications", choose whatever category you think it belongs in[/INDENT]
6) Arguments for the program
[INDENT]Now that you chose what the program path is, do you want any arguments for it? i.e. -> (for 'ls', something like '-al' may be wanted here)[/INDENT]
7) Terminal usage
[INDENT]If this program does not have a GUI that will run (a command versus a GUI application), you will want to choose this option so you can see the output in the terminal window[/INDENT]

Give it a try, PrixFixe should be pretty hard to "screw up", unless you choose an application name that exists already ;)
Let me know if you have any other questions.

---

### Post by cvmostert on 2011-05-03
Thanks for the post.

I installed Blender 2.5 (not yet in the repositories) and made a launcher on the Desktop.

I could pin the shortcut but could not delete it afterwards from the desktop, if I did delete from the Desktop, the Pin-on also went. so what I needed to do is to copy the Launcher I made to /usr/share/applications
and i could search for the application in Unity to pin it.

Thanks for leading me into the right direction.

Cheers:D

> **LinkMJB said:**
> Alright boys and girls, I spent some time tinkering with this tonight and found a solution using user preferences. I am considering writing a zenity front-end/(python/bash) backend to automate user input, bridging or to replacing "alacarte/Main Menu" functionalities to make this easier for the average user.

Here is what I have found so far ->
1) User customization is based in ~/.gconf/desktop/unity/launcher/favorites
2) Each application in your favorites has a directory within the favorites folder, and is indexed/referenced using the %gconf.xml
3) If you have already created a custom folder/application using alacarte/Main Menu, you should already have a file created under /usr/share/applications you can reference in the next step. Otherwise, make one using alacarte/Main Menu
4) cp -pr ~/.gconf/desktop/unity/launcher/favorites/app-firefox.desktop ~/.gconf/desktop/unity/launcher/favorites/app-[custom_name].desktop
6) vi ~/.gconf/desktop/unity/launcher/favorites/app-[custom_name].desktop/%gconf.xml
7) insert a line like so (inside the <gconf></gconf>):
[INDENT]<entry name="desktop_file" type="string">[/INDENT]
[INDENT][INDENT]<stringvalue>/usr/share/applications/[custom_name].desktop</stringvalue>[/INDENT][/INDENT]
[INDENT]</entry>[/INDENT]
8) Logout and log back in, or restart gdm ('sudo restart gdm')

NOTE: I assume similar things can be done to add programs into "Applications", but I expect it will live under /usr/share and effect ALL users...

Have fun! I will post back here when/if I create the GUI front-end to handle these steps, and provide a method to retrieve the .deb package

---

