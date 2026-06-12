---
title: "New Universal Launcher/Menu : Revolve"
date: 2007-10-08
forum: Desktop Environments
---

### Post by booljayj on 2007-10-08
Note- I am incapable of programming this myself, but could easily manage a project like this if called upon to do so.

I propose a new universal launcher/menu for the gnome desktop. It is called "Revolve". Slogan: Life should revolve around you.

I have seen and used many beautiful menus and launchers, but I always find them lacking. gDesklet launchers like gnomedock work well at what they do, but are stiff and ugly. Window managers like AWN look wonderful, but could never fulfill the task of being a complete system menu. Many people have their own agendas on how a menu/launcher should look and feel, and often make something so specific that only people like themselves can use it. I'm sick of it, and it's not the way things should be. Why not change it up a bit.

Quicksilver's (Mac) Costellation plugin is the perfect example of how a menu can be set up in both an easy to use and powerful manner. Quite frankly, though, it's just way too cluttered. We need something powerful yet simple for the gnome desktop, something that follows recognizable laws of interface design, something that we can all use easily and cleanly regardless of skill level or application.

First: the user presses the activation key. Everything on the screen dims out, and a circular menu with 4 cardinal directions fades in.

Second: the user reaches for the directional arrows. The user should need nothing but these four buttons to navigate the entire menu. He presses the right button corresponding to the right part of the circle, which happens to open a programs menu.

Third: The circle fades and moves slightly to the left and a list of categories emerges from behind it on the right. This list has five visible options which fade out in either direction. The categories are named for each of the categories of programs in the Gnome menu. The user scrolls the list by pressing up or down, focusing on the category they want to view.

Fourth: The circle and smaller menu move yet again to the left to make room for a list of actually programs to emerge on the right. This list can be navigated by pressing up and down. When the user selects the program they want, they simply press right once more to activate it, causing the whole menu structure to fade away while the application opens.

Fifth: Say the user did not want to open that program, or any at all. They simply need to press left once to move back to the categories list, and left again to focus on the main circle.

Sixth: Now they press up, which leads them to a system menu. The circle fades and moves down while a hyperbolic list structure appears above (subject to change. I need to find something pretty, unique, and easy to use). Preferences form a list arcing to the top and bottom left corners, fading as they get further, and administrative utilities form a similar structure on the right. In the middle is a loqout/power menu.

Seventh: Pressing left will focus on the preferences menu, allowing the user to scroll through the list in a similar method as before. The same occurs when the user presses right. Pressing up will invoke a new method that goes over all the others and contains all logout and power options. Pressing down will, once again, move the user back to the circle.

Eight: The user has not done anything, but still wishes to close Revolve. All they must do is press any key other than an arrow key to exit.

This method will allow a user to access a program in 5 button presses. Yes, it's true that the same can be done with 3 clicks of the mouse on the Gnome Menu (if one clicks on each category to open it), but that does not factor in the time it takes to move the mouse, focus on the correct option, or wait for the menu to open while hovering. This method will be fast, especially if the user can define the order of the programs/categories in the menus. They could keep their most used programs closer to the center and their least used further.

This could easily be implemented in Python, which would allow numerous plugins to easily be written and would give the whole program a very liquid feel. The Cairo libraries seem to be the place to go for vector art animations and the like, so those could be used. Overall I would like to see something as easily modified as Quicksilver, without becoming as bloated as it is. For instance, Amarok users could find a plugin that would allow them to scroll through their albums/artists and set them to play. Compiz users could enable true transparency and accelerated effects. The possibilities are endless.

So... who's with me?

---

### Post by booljayj on 2007-10-23
Bump*

Anyone interested? Have any questions, comments, observations?

---

### Post by booljayj on 2007-10-30
Attached are some pictures of what the design might look like. I just used inkscape to throw these out. The second one is of the main wheel, and the first is the programs view with the accessories folder open. Note- these should have icons, but I didn't want to take the time to grab them all from their respective folders.

---

### Post by trash on 2007-11-05
I'd for one would like to see this go further, hope you get some interested programers soon:)

---

### Post by davidsiegel on 2007-11-10
To me, this seems like the same old menus in a circular arrangement. Searching for what you want to do is extremely effective. Check out GNOME Do: [http://launchpad.net/gc](http://launchpad.net/gc)

GNOME Do allows you to quickly search for many objects present in your GNOME desktop environment (applications, Evolution contacts, Firefox bookmarks, files, artists and albums in Rhythmbox, Pidgin buddies) and perform commonly used commands on those objects (Run, Open, Email, Chat, Play, etc.).

Attached is a preliminary package.

---

### Post by trash on 2007-11-10
> **davidsiegel said:**
> To me, this seems like the same old menus in a circular arrangement. Searching for what you want to do is extremely effective. Check out GNOME Do: [http://launchpad.net/gc](http://launchpad.net/gc)

GNOME Do allows you to quickly search for many objects present in your GNOME desktop environment (applications, Evolution contacts, Firefox bookmarks, files, artists and albums in Rhythmbox, Pidgin buddies) and perform commonly used commands on those objects (Run, Open, Email, Chat, Play, etc.).

Attached is a preliminary package.

It's nice and works well but you do have to know exactly what you are looking for. I think it still needs a menu or shortcuts to menu catagories.

---

### Post by davidsiegel on 2007-11-10
I'm the lead developer on the project, so if you can tell me more about what you think GNOME Do needs, I can work on adding those things. What do you mean by shortcuts to menu categories? It has a menu (although it doesn't do much) - click the white triangle.

---

### Post by trash on 2007-11-10
> **davidsiegel said:**
> I'm the lead developer on the project, so if you can tell me more about what you think GNOME Do needs, I can work on adding those things. What do you mean by shortcuts to menu categories? It has a menu (although it doesn't do much) - click the white triangle.

Nice job so far:).
let's say I wanted to see a list of all the games I have installed, they are all listed in the gnome games submenu but there is no means to open it

---

### Post by davidsiegel on 2007-11-10
Thanks. Okay, I understand. Did you know you can press the down arrow to see a list of search results? I take it that what you want is to type "game" and have all games show up in that list? I guess in this situation you should just use the GNOME main menu. I am operating under the assumption that people know the names of what they are looking for, and that they are looking for particular things: "chess" rather than "game." This helps us optimize search so that you get results as soon as you press a key. If I get more suggestions like yours, I will reconsider this approach.

---

### Post by trash on 2007-11-10
I didn't know about the down arrow, i like!
Don't get me wrong I like the search, and combined with the down arrow it's perfect.
Your program can easily replace the gnome main menu with just 4 buttons on it that open submenus, without losing any of it's current functionality.

Oh btw, your icon looks great in AWN:)

---

### Post by davidsiegel on 2007-11-10
Okay, you've stumbled upon a great idea - how about I have searchable items for each category in the GNOME main menu. This way, you can search "games" and you'll get a result called Games. Then, you can press the right arrow to get a list of all games. Thanks, trash!

Can you post a screen shot of AWN? I thought my window isn't detected by awn.

---

### Post by trash on 2007-11-10
It wasn't detected but dragging it from the menu to AWN work perfectly:).

I am so happy you could see a way to make it work!! THANKS!:D

---

### Post by davidsiegel on 2007-11-10
Awesome.

---

### Post by davidsiegel on 2007-11-10
Also, you know there's a keybinding, right? <Super>space. Or you can just use another keybinding method (Compiz shortcuts) to bind any old key combo to the command gnome-do

---

### Post by davidsiegel on 2007-11-10
Also, make sure you try the addins: [http://davebsd.com/do/addins](http://davebsd.com/do/addins)

They're the best part.

---

### Post by trash on 2007-11-10
K i think we need to start a Gnome-do thread hehe.

I can't get the addins working and there is some strange behaviour with Opera and Gnome-do icons in AWN... for example the opera icon will disappear and gnome-do will minimize and refocus opera.. it's bizar!

here's the new thread [http://ubuntuforums.org/showthread.php?p=3747598#post3747598](http://ubuntuforums.org/showthread.php?p=3747598#post3747598)

---

### Post by trash on 2007-11-10
> **booljayj said:**
> Bump*

Anyone interested? Have any questions, comments, observations?

What do you think of the potential of Gnome-do?

---

### Post by Depressed Man on 2007-11-10
Not an evolution user, thunderbird support would be awesome! (for contacts)

---

### Post by davidsiegel on 2007-11-12
> **Depressed Man said:**
> Not an evolution user, thunderbird support would be awesome! (for contacts)

We have a Thunderbird contacts plugin. It's our do-addins launchpad branch. If you send me an email or something, I will build it and send it to you so you can drop it in your addins directory. Thunderbird uses this weird format for storing its contact info, so the Thunderbird addin may not work perfectly, although it certainly should work.

---

