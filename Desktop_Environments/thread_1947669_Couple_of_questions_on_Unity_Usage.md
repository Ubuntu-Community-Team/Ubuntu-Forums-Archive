---
title: "Couple of questions on Unity Usage"
date: 2012-03-27
forum: Desktop Environments
---

### Post by Ifaistos on 2012-03-27
Hello everyone :-)

I decided to start using Unity, only a couple of days ago.
I must say that now that I have read a little bit about it, saw some videos on its usage, I kinda like it!

Problem is that I am still using 2D version... haven't been able to  run the regular Unity version... I guess gfx problem...  But that's on another thread...

Anyway.. I wanted to ask a couple of questions regarding the use of Unity...

1. On the Dash, I type "Movies".  I have a folder called movies.  Although it finds some files (but not all) from inside the folder and subfolders of movies, it doesn't find the folder itself?  My filters are all set to "all".  Is this a bug, or am I doing smt wrong?

2.  Is there a way to go to the folder of a file that you find in dash?  I tried to right click, but no result :(

3. How do I move a launcher icon up or down the launcher?  I tried to click and drag, but all it does, is to move the launcher list up or down... (I imagine that I will not be able to do it, because I am using 2D).

4. Is there a quick way to "show the desktop".  I downloaded My Unity, and although it does have an option for an active Show the Desktop button, it is not implemented yet... btw.. The italians have done a great job with my Unity!

5. How do you move a window to another workspace??  I tried by showing the desktops and click and drag, but it doesn't work.  I found a way, which is really cumbersome, by right clicking on the menu bar of the application, then checking the option : Use system Title Bar and Borders, then unmaximizing the application and then right clicking to get the option of moving to another workspace... Is there another faster and less cumbersome way?

That's it for now.... but I am sure that as I continue to play around with Unity, and learn more about it.. I will have more questions..

Thank you all in advance.

---

### Post by d.atanasov on 2012-03-27
> **Ifaistos said:**
> 

3. How do I move a launcher icon up or down the launcher?  I tried to click and drag, but all it does, is to move the launcher list up or down... (I imagine that I will not be able to do it, because I am using 2D).


There is a way to move a launcher icons (never worked for me I hope for you to work). There is gconf-tools or dconf-tools 
[http://askubuntu.com/questions/75479/arrange-icons-on-unity-2d-bar](http://askubuntu.com/questions/75479/arrange-icons-on-unity-2d-bar)

> 
4. Is there a quick way to "show the desktop".  I downloaded My Unity, and although it does have an option for an active Show the Desktop button, it is not implemented yet... btw.. The italians have done a great job with my Unity!
 You can do something very useful for me like turning your edges of the screen to do it. You can find it in Ubuntu Tweak Tool under Compiz Configuration. If you don`t have it here is a link to install it or you can search through the software center 
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

> 
5. How do you move a window to another workspace??  I tried by showing the desktops and click and drag, but it doesn't work.  I found a way, which is really cumbersome, by right clicking on the menu bar of the application, then checking the option : Use system Title Bar and Borders, then unmaximizing the application and then right clicking to get the option of moving to another workspace... Is there another faster and less cumbersome way?
I do it by pressing **Ctrl + Alt + Shift + Arrow** Arrow is just the direction of the workspace where you want to move your window :)

best regards

---

### Post by Ifaistos on 2012-03-27
Thanks for your answers..

Regarding No 3, I was looking for smt faster and more direct.  I wanted to be able to change the launcher "on the fly" and not go through some configurations... it's no big deal.. I guess they'll fix this in the upcoming version.

The answer to No5 is awesome!! I tried it and it works.  However I would appreciate it, if Unity had some kind of visual confirmation that the window has changed since I have to use ctrl-alt-arrow to check if the window was actually moved or not...


Thank you again....
Anyone have answers to the other questions?

---

### Post by d.atanasov on 2012-03-27
Well in previous distros there was indication from the window switcher, but I don`t see it in Unity... There was a discussion in the ubuntu forums (as far as I can remember)that there should be an direct why to change the order of the icons in the launcher, but the Unity is still in progress. For the moment this is the way to change the order in the next 12.04 there will be great changes I think :)

best regards

---

### Post by Ifaistos on 2012-03-27
Hello everyone :)

I just managed to run Ubuntu option.. that is Unity 3D.

I can change the order of launcher items within the launcher just by dragging out and dragging in...

I can also show the desktop by alt-tabing, because one of the options is "show desktop".

What I found a problem with was with CCSM.  I tried to opt for rotating cube and I broke Unity completely... I had to : 
Unity -- reset and reboot to get it back on again.
Does anyone know if we can have rotating cube, without breaking Unity?


One more question... Unity has 2x2 workspace switcher by default.  Is there a way I can edit this setting and add or subtract columns and rows?

Thank you all :-)

---

### Post by Ifaistos on 2012-03-28
Instead of doing a bump, I decided to do a recap on the questions still pending...

1. On the Dash, I type "Movies". I have a folder called movies. Although it finds some files (but not all) from inside the folder and subfolders of movies, it doesn't find the folder itself? My filters are all set to "all". Is this a bug, or am I doing smt wrong?

2. Is there a way to go to the folder of a file that you find in dash? I tried to right click, but no result :(

3. What I found a problem with was with CCSM. I tried to opt for rotating cube and I broke Unity completely... I had to : 
Unity -- reset and reboot to get it back on again.
Does anyone know if we can have rotating cube, without breaking Unity?

4. One more question... Unity has 2x2 workspace switcher by default. Is there a way I can edit this setting and add or subtract columns and rows?

Thanks.

---

### Post by stinkeye on 2012-03-28
> 1. On the Dash, I type "Movies". I have a folder called movies. Although it finds some files (but not all) from inside the folder and subfolders of movies, it doesn't find the folder itself? My filters are all set to "all". Is this a bug, or am I doing smt wrong?
The dash isn't really a search. It is more of an activity logger.

 > 2. Is there a way to go to the folder of a file that you find in dash? I tried to right click, but no result
No.

> 3. What I found a problem with was with CCSM. I tried to opt for rotating cube and I broke Unity completely... I had to : 
 Unity -- reset and reboot to get it back on again.
 Does anyone know if we can have rotating cube, without breaking Unity?
The cube works.
Try this in order in ccsm. Before you start open a terminal and if needed run
**compiz --replace & disown** if after a reasonable amount of time 
compiz fails to load properly.
Choose to disable or resolve conflicts when prompted.
[LIST]
[*]Uncheck unity
[*]Uncheck desktop wall
[*]Enable desktop cube
[*]Enable Rotate cube 
[*]Enable unity
[/LIST]

If the session becomes unresponsive try ctr+alt+del or ctr+alt+print+k
to logout and set compiz back to defaults within the unity 2d session.

> 4. One more question... Unity has 2x2 workspace switcher by default. Is there a way I can edit this setting and add or subtract columns and rows?
ccsm > General Options > Desktop Size
and adjust the horizontal and vertical virtual size.

---

### Post by bogan on 2012-03-28
Hi!, **Ifaistos,**

You Posted: >  Regarding No 3, I was looking for smt faster and more direct.  I wanted  to be able to change the launcher "on the fly" and not go through some  configurations... it's no big deal.. I guess they'll fix this in the  upcoming version. If you press and hold the Mouse Left-Click with the cursor on the Launcher item you want to move, after a pause of a fraction of a second, the Icon will shift slightly, and you can then move it up or down to where ever you wish - release and it stays there, without having to drag it off the launcher and back elsewhere.

This works in both 2D Unity and 3D, whereas [ 4 ] changing the array of workspaces can be done in MyUnity, but only in 3D. ( I am sure I have seen the same option elsewhere, but can not lay my hands on it.)

[ 2 ] To do a 'Right-Click' on a file in Dash you have to use 'Alt+Right-Click' but there is not a 'Show Folder' option in my setup.

Chao!, **bogan.**

---

### Post by Ifaistos on 2012-03-29
Thank you all :)

I have been working with Unity the last few days, and it looks just great!

---

