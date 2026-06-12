---
title: "Help with Compiz-fusion"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by Yes on 2007-08-12
I just switched from Beryl, and I need some help.

First question:  In Beryl, when setting the window opacity, you would chose between labeling the  window class, window title, etc.  What do I put down for the window type in Compiz?  I tried dialog, and that works for dialog boxes, but then I tried gnome-panel, but that doesn't seem to work.

Second question:  In Beryl, moving my mouse to the top-right corner of the screen displayed all of the windows so I could select one of the windows.  Is there any way to do this in Compiz?

Third question:  In Beryl, if I was at the desktop, I could hold my mouse wheel down, and move around the cube.  Is there any way to do that in Compiz?

Fourth question:  When I start Compiz using the command 'compiz --replace -c emerald &', the terminal doesn't work.  IE, where you would normally type the commands is just a white box.  The menu bar does work, though.

Fifth question:  When I start Compiz using the above command, I thought that that command is also supposed to start Emerald.  But it doesn't.  Emerald is installed, it just doesn't work.  The command 'emerald --replace' also work.

Sixth question:  Someone mentioned that I can get a plugin that allows me to set my screen saver as my rotating cube.  What plugin is this/where do I get it?

Seventh question:  How do I get fish to float in my cube?  Edit:  Apparently, I need the plugin "Cube Atlantis", which is in the "compiz-fusion-plugins-extra" package.  I have that installed, but I can't figure out how to use the plugins.

That's all for now, thanks!

---

### Post by Brezeck on 2007-08-12
It seems that all your problems can be solved on "compiz config setting manager"(i think it's the name, find it on system=>preferences)

for the first three ones, you can easily enable the settings, effects on  "compiz config setting manager", you should spend some time on it to solve your problems. 
when you get the settings correct, the first two ones will work fine, and "ctrl+alt+hold your mouse around" can move the cube.

for the fourth question, i think when u type those commands, your emerald have already started, but you didn't download any themes i think. go to [http://www.gnome-look.org](http://www.gnome-look.org) to download some beryl emerald themes to change the window border, and some gtk2.x themes to change the panel, terminal.

for the fifth, i always type "compiz --replace" then "emerald --replace", if you dont want to type them every time you log in, you can just put them in sessions.

for the sixth, i dont exactly know the plugin, sorry!

for the last one, you can also enable "Cube Atlantis" plugin on "compiz config setting manager", it has been installed with compiz fusion. but i don't think "Cube Atlantis" is a good plugin, the fishes look so unreal...

AT LAST, i wish you could forgive my terrible english...:)

---

### Post by Yes on 2007-08-12
Ok, I'm trying to figure out my first three questions in the manager.  For the fourth, I do already have quite a few themes downloaded, so it's not that.  Those other commands don't work, sorry.  For the time being, I'll stick to what I already have, so would you happen to know how to use the Cube Atlantis plugin?

Thanks.

---

### Post by Brezeck on 2007-08-12
also go to "compiz config setting managers", enable the "Cube Atlants" setting, then move your cube around, you'll find some fishes in you tube.

---

### Post by Brezeck on 2007-08-12
for the fourth question, have you imported the themes on emerald themes manager?

---

### Post by Yes on 2007-08-12
Yes, I did.  This is not only limited to the terminal.  My GAIM buddy list also does this.

Using emerald --replace did start Emerald successfully, though.

There isn't a "Cube Atlantis" setting in "compiz config setting managers".

I'm still having trouble with my first three questions.

Thanks.

Edit:  When I change the opacity of the cube, and exit out of the Compiz Manager, it resets all the opacity values that I had set back to 100.  Why is this?

---

### Post by Brezeck on 2007-08-13
I really wonder if you have installed compiz fusion correctly, maybe you haven't removed your beryl yet? this may cause some problems

---

### Post by Yes on 2007-08-13
No, Beryl is definitely gone, and I am almost 100% sure that compiz is installed correctly.

---

### Post by Brezeck on 2007-08-13
So, give me a minute, i'm going to switch to ubuntu now to help you!

---

### Post by Brezeck on 2007-08-13
Now have you see this picture? This is my compizconfig setting manager.(some Chinese characters on it but it's not important)
[IMG]http://xs218.xs.to/xs218/07331/Compizfusion.png[/IMG]
See the "Cube Atlantis" in "Effects"? If not, i'm sure you have something wrong with the installation! :(

---

### Post by petit.padavoine on 2007-08-13
1. The type for the gnome-panel is not gnome-panel, it's DOCK.
To find the type or any info on any window / app you have, follow this guide from the official compiz fusion blog: [http://smspillaz.wordpress.com/2007/06/04/soon-to-be-named-community-news-edition-5-for-june-2-2007-names-fanfare-and-zoom/](http://smspillaz.wordpress.com/2007/06/04/soon-to-be-named-community-news-edition-5-for-june-2-2007-names-fanfare-and-zoom/) (scroll down a bit to get to the part about finding types)

2. This is the Scale plugin. You should find it in the compiz config settings manager at the bottom. Click on it. In the actions tab, set the keyboard/mouse bindings that you want for it.

3. Same as above, but click on Rotate Cube instead of Scale.

4. Use Alt+F2 to enter "compiz --replace" instead of a terminal. Also add compiz --replace to your startup programs in System, Preferences, Sessions.

5. The same happens for me, so I added "emerald --replace" to my startup programs.

6/7. For Cube Atlantis and the Screensaver plugin, make sure you have installed every single plugin you can:
```
sudo apt-get install compiz-fusion-plugins-*
```
If that doesn't do the trick, post which repositories you installed compiz fusion from.
I used the tuxfamily.org repository and I have all those plugins.
To install from tuxfamily.org, first remove all your compiz stuff: ```
sudo apt-get --purge remove compiz* libcompizconfig*
```.
Then ```
sudo gedit /etc/apt/sources.list
``` and remove the repositories you used for compiz fusion. 
Then follow the guide at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Compiz-Fusion_.28a_Compiz-Beryl_fusion.29) to install from the tuxfamily.org repositories.
Finally run ```
sudo apt-get install compiz-fusion-plugins-*
``` to install all those great plugins :D.

---

### Post by Brezeck on 2007-08-13
This should be a good response!

---

### Post by Yes on 2007-08-13
Ok, I got the cube to scroll with the mouse, and I got the window scaler and opacity working.  

I'll try what you said about the plugins in a moment, but now, I have two more questions:

When use Emerald, some parts of programs don't work.  For example, images or text might appear as gray or white blocks.  This doesn't happen when I just use Comiz, so it's definitely Emerald.  Is there any way to fix this?

Is there any way to set up the window scaler to be triggered by a mouse moving to a screen edge?  I see that option under the actions tab, but I can't figure out how to enable it.

Thanks!

Edit:  The first command to install the plugins said that they were already installed.  Isn't there a way to get them without reinstalling compiz?

---

### Post by petit.padavoine on 2007-08-13
> **Yes said:**
> Ok, I got the cube to scroll with the mouse, and I got the window scaler and opacity working.  

I'll try what you said about the plugins in a moment, but now, I have two more questions:

When use Emerald, some parts of programs don't work.  For example, images or text might appear as gray or white blocks.  This doesn't happen when I just use Comiz, so it's definitely Emerald.  Is there any way to fix this?

Is there any way to set up the window scaler to be triggered by a mouse moving to a screen edge?  I see that option under the actions tab, but I can't figure out how to enable it.

Thanks!

Edit:  The first command to install the plugins said that they were already installed.  Isn't there a way to get them without reinstalling compiz?

Emerald problem, no idea.
Plugins: you'll have to reinstall.
I suppose you followed the how-to stickied at the top of this forum.
I really don't understand that how-to, it's kinda weird.
The repository is missing compiz-fusion-plugins-unofficial and compiz-fusion-plugins-unsupported, AND it's buggy: it keeps trying to update compiz-core but there's no update for it :D.
So yeah I guess you'll have to reinstall to cut a long story short.

EDIT: I forgot to answer about how to get the mouse in top right corner to activate Scale. If you go the Scale preferences and to the actions Tab, one of the options should be "ScreenEdge". Just set that to TopRight.

---

### Post by Yes on 2007-08-13
And I can't install the plugins separately, I have to reinstall compiz to install them?

I'm still having problems with Emerald, but I got the Scale to activate when move my mouse to the top right, thanks for that info.

---

### Post by modestmelody on 2007-08-13
> **Yes said:**
> Ok, I got the cube to scroll with the mouse, and I got the window scaler and opacity working.  

I'll try what you said about the plugins in a moment, but now, I have two more questions:

When use Emerald, some parts of programs don't work.  For example, images or text might appear as gray or white blocks.  This doesn't happen when I just use Comiz, so it's definitely Emerald.  Is there any way to fix this?

Is there any way to set up the window scaler to be triggered by a mouse moving to a screen edge?  I see that option under the actions tab, but I can't figure out how to enable it.

Thanks!

Edit:  The first command to install the plugins said that they were already installed.  Isn't there a way to get them without reinstalling compiz?
How'd you get the cube to rotate with the mouse?  Also, have you figured out how to get the Ctrl+Alt+Left Mouse click action to work with Left+Right click on the desktop like in Beryl?

---

### Post by petit.padavoine on 2007-08-14
You could try keeping your current compiz install and installing the plugins separately but I don't know if it would work and anyway I would recommend reinstalling everything because
1. You wouldn't lose any config data.
2. You would get almost hourly updates with the new repositories (Trevino keeps updating them)
3. The repositories from the how-to are buggy.

I guess you don't wanna do that but have you considered dropping Emerald?
I don't really like any of the Emerald themes so to me, the only major drawback in not using Emerald is that the Reflection plugin (I don't mean Cube Reflection, I mean window borders Reflection) doesn't look as good with gtk-window-decorator.

---

### Post by Yes on 2007-08-14
Right, I followed all the instructions for reinstallation, except I ran into some trouble:

The command 'gksudo apt-get -y upgrade' gave me an error, and the command for installing compiz also gave be an error.  I took out the -y in both, and I didn't get the error.  My other problem is that when I ran the installation command (without the -y), it told my how much disk space would be used, and asked if I wanted to continue.  I said yes, but then the cursor moved to the next line and didn't do anything.  What did I do wrong?

modestmelody, I don&#8217;t know about your second question.  The first, I&#8217;m pretty sure I went to &#8220;Rotate cube&#8221;, and then to the actions tab.  When I was there I played around with a few settings and eventually got it to work.

Thanks.

Edit:  I ran the install command as sudo instead of gksudo and it worked.

Edit2:  I'm having some trouble with the screensaver plugin.  When I set it to start after .1 minutes, it works, but if I set it to start after five minutes, it never starts.  Anyone know why this might be?

Thanks.

---

### Post by petit.padavoine on 2007-08-14
> **Yes said:**
> 

Edit:  I ran the install command as sudo instead of gksudo and it worked.

Edit2:  I'm having some trouble with the screensaver plugin.  When I set it to start after .1 minutes, it workes, but if I set it to start after five minutes, it never starts.  Anyone know why this might be?

Thanks.

Glad to see it worked out for you :D.

As far as the screensaver plugin goes, I have no idea.

---

### Post by Yes on 2007-08-14
Edit:  Nevermind, it's not working.  The times that work seem to be random.

---

