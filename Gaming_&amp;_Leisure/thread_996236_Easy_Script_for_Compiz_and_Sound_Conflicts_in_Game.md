---
title: "Easy Script for Compiz and Sound Conflicts in Games"
date: 2008-11-28
forum: Gaming &amp; Leisure
---

### Post by drelyn86 on 2008-11-28
Covering a couple basic nuisances in Ubuntu...

It is commonly known that OpenGL windows flicker annoyingly while running Compiz. 

Also - some people (such as myself) like to have their sound settings set to play a sound when buttons and menu items are clicked. You may notice that this disables the sound in your games when opening them from the menu. 

Today we are going to write a very basic script that addresses both of these issues, and it should take less than one minute after you do it enough times. I will be using the game Neverball as an example.

Note: Neverball is a fun game, IMO. If you don't have it already...

```
sudo aptitude install neverball neverputt
``` 
-----------------------------

First, you'll want to know the command to open the game you're running. This step is unnecessary if you already know the command. 
The way I do is by going into the main menu settings...

```
alacarte
```

Or you can just right-click your main menu and select "Edit Menus". 

Find the game (or application) and go into its Properties...

[IMG]http://i486.photobucket.com/albums/rr229/drelyn86/mainmenu1.png[/IMG]

You should see the command used to launch the game. You might as well leave this open, as we will be changing this later. 

[IMG]http://i486.photobucket.com/albums/rr229/drelyn86/Screenshot-LauncherProperties.png[/IMG]

Now it's time to write the script. 
I usually keep all of my scripts in a folder called "Scripts" in my home folder. 

```
mkdir ~/Scripts
gedit ~/Scripts/Neverball
```

Enter the following:

```
#!/bin/sh
metacity --replace & sleep 2 && neverball && compiz --replace
```

(notice where I inserted the command that we retrieved from the main menu settings)
Save and exit. 

Now make the script executable. 

```
chmod 755 ~/Scripts/Neverball
```

Now, go back into the launcher properties for Neverball in the Main Menu settings...

Assuming your username is "ubuntu"...
Change the command to the following:

```
sh /home/ubuntu/Scripts/Neverball
```

Close out of the properties and the main menu settings

You should now be able to launch your game via the main menu... it will disable Compiz, wait 2 seconds, and then open the game, and the "click" sound from clicking on the menu item will not disable the game's access to your sound. Also, once your game is closed, it will automatically re-enable Compiz.

-----------------

Note: If you're trying to do something like this that does not require sound, or if you don't have the sound settings enabled to play a sound when clicking on a menu item, you can remove the "sleep 2 &&" portion of the script. 

One example of an OpenGL app that does not require sound would be Google Earth...

```
#!/bin/sh
metacity --replace & googleearth && compiz --replace
```

---

