---
title: "How do I get Blender to appear in Dash / Launcher?"
date: 2011-06-02
forum: Desktop Environments
---

### Post by CleverCoder on 2011-06-02
Good afternoon! I just recently took the dive to learn Ubuntu and become more proficient with Unix. One of the applications I'm trying to setup is Blender.

I chose to extract the latest beta to the /opt/ folder. This seemed like a good place (any other suggestions?). I can run Blender from there with no serious issues, but it's inconvenient to have to browse to that path anytime I want to run Blender.

Two questions:
- I read that when an application is running, I should have the option to "Keep in Launcher" on the icon. For Blender, it seems that the option doesn't exist. Is this a bug? Is there another way to create this shortcut?
- Using Dash, I type "Blender" expecting to locate the Blender application. It doesn't show up. The only thing that appears is the downloaded package. I figured that if the Dash UI can locate the application, I could add the shortcut. I thought I read somewhere that there is a command that would force Dash to rebuild or update it's database ... is that what I need to do?

Any tips appreciated! 

Cheers!
-Sean

---

### Post by Copper Bezel on 2011-06-02
Well, since you didn't install it normally, the command blender might not even work from the run dialog or terminal, and you certainly don't have it in the menu so that it would appear in Dash. 

Try the command first - whatever the executable is called without the path - by hitting Alt+F2 for the Run Dialog and then typing the command. If it doesn't, you can just use the full path you've been using as the command. 

Hit Alt+F2 again and run alacarte . It's the menu editor. You can create a new entry and use the command for Blender that's working. 

If it doesn't appear in the Dash after that, you can try creating a .desktop file instead. Navigate to /usr/share/applications, open one of the launchers in gedit, and make a new text file using the format from the one you opened. Save it as blender.desktop, right-click it in the file manager, select Properties, and change its Permissions to Allow Running as an Application.

Now, drag and drop it onto the Launcher.

I promise Linux isn't usually this difficult - installing applications manually instead of from the repositories can be a **** - but it is a learning experience. = )

Edited. Missed a step.

---

### Post by CleverCoder on 2011-06-05
Thanks for the insight! I develop software and have used unix off and on for many years, so the process of configuring and building via. makefile isn't too exotic. Launching applications from a terminal session is also pretty standard to me :)

So it looks like the real trick here was the menu editor. "Edit Menus"... I'm not sure why I never saw this before. Maybe a slight gap in documentation? Would be nice to add it here:
[https://help.ubuntu.com/11.04/ubuntu-help/unity-launcher-intro.html](https://help.ubuntu.com/11.04/ubuntu-help/unity-launcher-intro.html)

Nonetheless, running the "Main Menu" editor allowed me to add Blender to the launcher... and it worked.

Thanks again for the tip!
-Sean

---

### Post by Copper Bezel on 2011-06-05
Hey, I'm glad that worked out - go ahead and mark the thread as Solved, from Thread Tools in the upper right.

Yeah, Ubuntu seems to be documented around the assumption that packages are installed from repositories (including PPAs) or occasionally from .debs. Unity gets its menu information from the Gnome desktop that runs underneath it, and in vanilla Gnome that's handled from Alacarte, but *most* of what Alacarte does isn't needed or used in Unity. 

I really wish Ubuntu just used a folder of .desktop files for Unity's menus, rather like the Windows Start Menu. I have the same issue with the third-party shell I'm using (lots of bits that depend on settings from Gnome parts that aren't used, and specifically entries from Alacarte used in a search-based menu as well.)

---

### Post by mc4man on 2011-06-05
> I read that when an application is running, I should have the option to "Keep in Launcher" on the icon. For Blender, it seems that the option doesn't exist.
You should keep in mind that the dash - apps lens will only find .desktops, not binaries. Any .desktop installed to or placed in  a  /share/applications/ folder in your path should show
For /opt I think if you create a /share/applications then a .desktop should show if placed there

As far as the unity launcher basically the same thing - while if running a binary it will show up, either with a generic, terminal, or the app's icon, only it's .desktop can be added to the launcher successfully.
Favourites icons in the launcher are just shortcuts to a .desktop, not the actual .desktop or  binary itself.

So in the case of the blender beta it doesn't contain a .desktop (blender.desktop), so there is nothing to add to the unity launcher till one is created and then added in any one of the various ways.

---

