---
title: "Right Click on Task Bar Does Nothing"
date: 2011-11-28
forum: Desktop Environments
---

### Post by billmcn on 2011-11-28
I just upgraded from 9.* to 11.10. I want to add an application shortcut to the taskbar, but when I right-click on it nothing happens.

Is this expected behavior. If it is, how do I add shortcuts to the taskbar?

---

### Post by Copper Bezel on 2011-11-28
Which shell (interface) are you using? If it's the classic (two horizontal panels by default) interface, hold Alt while right-clicking. If you're using Unity (top and left panels) or Gnome Shell (top panel only,) you can't; you'll want to read up a bit on the customization options you have. Gnome 3 is very different from Gnome 2, no matter which shell you're using.

---

### Post by BC59 on 2011-11-28
There are 2 options

First. You open the application and when appears to the "bar" right click on the bar icon and choose "Keep in launcher" (Launcher is the official name of the bar)

Second. You open the "dash" (click on the upper part of the launcher) and on the search box write the name of the app. When it's icon appears drag and drop the icon to the desktop. Then from the desktop drag and drop again the icon to a folder you like to keep it (e.g. documents) From there drag and drop again to the launcher.


p.s. deleting the icon-link from the folder, deletes the link from the launcher.

---

### Post by billmcn on 2011-11-28
The "Keep in Launcher" option adds the appropriate Icon to the Launcher. (Thanks for the "Launcher" nomenclature too, I didn't know that.)

However, I have a further problem. The application I'm trying to add is the [IntelliJ]("http://www.jetbrains.com/idea/") IDE. From the command line, you launch it by running an idea.sh shell script. IntelliJ is a Java application, so the idea.sh script does some environment setup and calls Java with the appropriate arguments.

IntelliJ gets added to the launcher with the appropriate icon, but when I double-click on it nothing happens. I also notice that when I hover over the icon on the Launcher, no name comes up. It looks like the problem is adding a terminal application to the Launcher.

Now that I think about it, on the earlier version of Ubuntu I had to do some special trick to get the Launcher to work with a shell script. As I recall, I was able to do this by right-clicking on the launcher icon and setting some custom properties, but I can't figure out how to do this now.

[This blog post]("http://blog.jeroenreijn.com/2010/01/creating-intellij-launcher-on-ubuntu.html") gives an example command line for IntelliJ that appears to distill the work done by idea.sh, but it still presumes that you know how to add a shell command to the Launcher.

---

### Post by BC59 on 2011-11-28
Well, you are going to far....
Unity is not so flexible.

I just read that using the app alacarte you can create custom launchers

You can install it from a terminal 

```
sudo apt-get install alacarte 
```

Then you have to ask where is from the dash.

---

### Post by Copper Bezel on 2011-11-28
Sorry, I misunderstood (a lot of people refer to the top "panel" as a "taskbar", which leads to confusion.)

BC59, Alacarte is installed by default on Ubuntu, isn't it? You can just run "alacarte". Once it's up, you can select any of the categories and use "New Item" to create a new entry, with the command line pointing to the shell script. Then search by the name in the Dash, as you said, and when it comes up, drag-and-drop or right-click, whichever it is, to add the item to the Launcher.

Alacarte is the same "Main Menu" editor that was in Gnome 2. For that matter, it hasn't even been updated for GTK3, because it's not used in default Gnome 3, but it's the easiest way to create a custom application launcher in Unity. (Or Gnome Shell, for that matter, but that's a separate issue.)

---

### Post by BC59 on 2011-11-28
> **Copper Bezel said:**
>  Alacarte is installed by default on Ubuntu, isn't it? 

Good point!

---

### Post by efflandt on 2011-11-28
Once you add a launcher to **alacarte**, how do you find that launcher from the Unity dashboard?  When I try to search for the launcher I added to alacarte, dashboard only finds the script by that name and opens it as a text file (even though it has execute permission and is in my ~/bin which is in my $PATH).  **man alacarte** has no info.

I am just trying to launch a script in terminal.  I found a post earlier that explained how to add a desktop launcher with whatever gnome used to use, and that worked.  But it was a long command line that I cannot remember and have not found it again in a search yet after having to reinstall 11.10 due to video driver issues.

Seems strange that somebody overlooked some way to easily add customized desktop or panel launchers to Unity like there was for gnome by just right clicking.

PS: I just figured out how to do it after looking through the results of **apropos desktop**, at least to make a launcher icon on the Desktop:

```
gnome-desktop-item-edit --create-new ~/Desktop
```So I made another launcher called "Make Launcher" that runs: **sh -c 'gnome-desktop-item-edit --create-new ~/Desktop'** (since that did not seem to run without quoting it as a command to sh).

---

### Post by BC59 on 2011-11-29
We had a discussion with **beew** and he comments

> alarcarte works in Unity as well for creating .desktop files, but the launchers thus created doesn't sort properly in the Unity dash (but it appear to in Gnome Shell). To make the icon appear in the proper catagory in the dash you have to edit the desktop file with gedit and add the line "Catagory=whatever category desired;"

---

### Post by Copper Bezel on 2011-11-29
Yeah, although in this case, you only need to find it once to add it to the Launcher, right? Just type a bit of the name you gave it in the Dash and it should show.

---

### Post by mcduck on 2011-11-29
> **Copper Bezel said:**
> Yeah, although in this case, you only need to find it once to add it to the Launcher, right? Just type a bit of the name you gave it in the Dash and it should show.

+1 to this, and in case a recently created launcher doesn't show up in a Dash search, log out and back again (or relaod Unity) and it should start working.

---

### Post by billmcn on 2011-11-29
I clicked the "Dash Home" button in the launcher and searched for "alacarte". This brought up the "Main Menu" application. Is "Main Menu" synonymous with "alacarte". (There doesn't appear to be any "alacarte" on my system.)

There are "New Menu" and "New Items" in the "Main Menu" application, but when I click them nothing happens.

---

### Post by Copper Bezel on 2011-11-29
Yes, alacarte is Main Menu, in the same sense that gedit is Text Editor and totem is Movie Player and so on. 

Clicking "New Item" should bring up a dialog box to allow your to create your launcher. I don't honestly know what's going on if that's not the case.

---

### Post by BC59 on 2011-11-29
Ok we found a new way to create launchers on Unity. Alacarte--New item and when it appears on Unity launcher you right click and choose Keep on Launcher.

Then you edit the name, command and comment.

Looks it's working

---

### Post by billmcn on 2011-11-29
Looks like Main Menu aka AlarCarte is broken for me.

Is there a workaround? A command-line tool, or a text file I can edit?

---

### Post by BC59 on 2011-11-29
> **billmcn said:**
> Looks like Main Menu aka AlarCarte is broken for me.

Is there a workaround? A command-line tool, or a text file I can edit?

Try to reinstall it

```
sudo apt-get install --reinstall alacarte
```

You can open it executing alacarte on a terminal

---

### Post by mcduck on 2011-11-29
> **billmcn said:**
> Looks like Main Menu aka AlarCarte is broken for me.

Is there a workaround? A command-line tool, or a text file I can edit?

Make sure you are actually inside one of the existing menus before you try to create a new item. I don't think you can create an item directly in the root of the menu structure.

---

### Post by Copper Bezel on 2011-11-29
You can, actually - I just tried. That's not the problem.

---

### Post by efflandt on 2011-11-29
I hadn't noticed until someone mentioned it that the launcher I added to alacarte did show up in Dash Applications during a later login. So apparently you do have to log out of X and back in to refresh Dash.

alacarte was not on my 11.10 system until I installed it.

---

### Post by typhoon_tip on 2011-11-29
> **efflandt said:**
> alacarte was not on my 11.10 system until I installed it.

Correct. A lot of people get it because they install gnome-tweak-tools, which in turns installs gnome-shell and gnome-session-fallback, with another bunch of apps.

---

