---
title: "How do you change window backgrounds?"
date: 2010-05-25
forum: Desktop Environments
---

### Post by X-Windows on 2010-05-25
I know, absolute beginner stuff, but I can't figure this out...
 
I'm trying to install an emerald theme while maintaining the Compiz desktop effects. I'm running Ubuntu 10.04 Lynx and have installed Emerald Theme Manager and Compiz. I was looking for a good theme to go with my background/laptop and took a liking to this one, [http://compiz-themes.org/content/show.php/Darkness+emerald+theme?content=124315&PHPSESSID=aad7e8c800081d0fa328d060c9fe64fb](http://compiz-themes.org/content/show.php/Darkness+emerald+theme?content=124315&PHPSESSID=aad7e8c800081d0fa328d060c9fe64fb).
 
 I'm sure this is a stupid question but how do I install this? By following the link to the rgba true theme, there are "instructions" on how to install it, but I just cant figure it out. I have the window borders setup but I'm stumped on how to get the transparent black window backgrounds(by window backgrounds I mean everything inside the frame). The frame works fine but it looks terrible with the solid white window interior. Can someone tell me how to get this working? I have already tried Compiz opacity (terrible, makes everything unreadable). Every background setting I see is RGB, no transparent setting. If it helps, I'm trying to get everything ~75% transparent, no solid colors.
 
Thanks in advance!

---

### Post by isaacj87 on 2010-05-25
> **X-Windows said:**
> I know, absolute beginner stuff, but I can't figure this out...
 
I'm trying to install an emerald theme while maintaining the Compiz desktop effects. I'm running Ubuntu 10.04 Lynx and have installed Emerald Theme Manager and Compiz. I was looking for a good theme to go with my background/laptop and took a liking to this one, [http://compiz-themes.org/content/show.php/Darkness+emerald+theme?content=124315&PHPSESSID=aad7e8c800081d0fa328d060c9fe64fb](http://compiz-themes.org/content/show.php/Darkness+emerald+theme?content=124315&PHPSESSID=aad7e8c800081d0fa328d060c9fe64fb).
 
 I'm sure this is a stupid question but how do I install this? By following the link to the rgba true theme, there are "instructions" on how to install it, but I just cant figure it out. I have the window borders setup but I'm stumped on how to get the transparent black window backgrounds(by window backgrounds I mean everything inside the frame). The frame works fine but it looks terrible with the solid white window interior. Can someone tell me how to get this working? I have already tried Compiz opacity (terrible, makes everything unreadable). Every background setting I see is RGB, no transparent setting. If it helps, I'm trying to get everything ~75% transparent, no solid colors.
 
Thanks in advance!

Hey there,

I'm assuming that you want to get this: [http://gnome-look.org/content/show.php/Darkness+gtk2+%28rgba+true%29?content=124548]("http://gnome-look.org/content/show.php/Darkness+gtk2+%28rgba+true%29?content=124548") up and running correct? Then, at that point, you can get the window borders changed (Emerald). Before we continue, since you say you're new, I'll explain, in my own words what exactly we're going to do. 

Compiz - These are the desktop effects. It is a compositor. It gives you all the fancy effects people like so much

Emerald - Window borders. When enabled, this overtakes Metacity's window borders. People like Emerald because it totally configurable. When enabled, it also effects such things as drop-down shadows.

GTK2 - Widget toolset that draws the windows. I don't fully understand this, but the way I see it, it handles the overall design of the desktop. It effects the way buttons, scrollbars, comboboxes, colors, drop-down menus, etc. look. There are different engines (such as, Murrine, Aurora, etc.) that each provided their own individual looks.

So, what we are doing here, is changing an aspect to a GTK2 engine. This won't have direct effect on Compiz/Emerald/Metacity.

Let's get this bad boy installed, shall we?

(These directions are taking off from the link itself, but organized for your viewing pleasure)

Install the repo that contain the necessary files. Open up a terminal window (Applications -> Accessories -> Terminal):

Then copy and paste the following command(s):

```
sudo aptitude install dpkg-dev
```

We've now prepared our comp to build this thing, now add a repo:

```
sudo add-apt-repository ppa:erik-b-andersen/rgba-gtk
```

Great, we've added the repo, now let's update our sources:

```
sudo apt-get update && sudo aptitude upgrade
```

Done. Now, let's install the package we need to get this running.

```
sudo apt-get install gtk2-module-rgba
```

Ok. So, now we have the package installed necessary to **build** this thing. Now, let's build it.

Still in terminal, let's do this (the following command will install a program that will automagically build packages for you. Why? So it's easier to remove the package if you don't want it anymore):

```
sudo apt-get install checkinstall
```

Now let's get a deps necessary to build the thing:

```
sudo apt-get build-dep gtk2-engines-murrine
```

Now, we make temp folder to work in:

```
mkdir tempbuild
```

Enter it:

```
cd tempbuild
```

and lastly get the sources:

```
apt-get source gtk2-engines-murrine
```

Then list everything for some reason (I don't know either):

```
ls
```

Now we need to enter our source folder:

Type:

```
cd
```

and press tab. The folder will locate itself in Terminal and press enter.

Now, we edit the file so we can apply the transparency effects:

```
gedit src/support.h
```

In the window that appears, scroll down to the section called: /*Opacity Settings*/

This is where you're personal preferences comes in. If you want **more **transparency, use these settings:

```
/* Opacity settings */
#define GRADIENT_OPACITY 1.00
#define WINDOW_OPACITY 0.70
#define ENTRY_OPACITY 0.92
#define NOTEBOOK_OPACITY 0.85
#define MENUBAR_OPACITY 0.70
#define MENUBAR_GLOSSY_OPACITY 0.70
#define MENUBAR_STRIPED_OPACITY 0.70
#define TOOLBAR_OPACITY 0.70
#define TOOLBAR_GLOSSY_OPACITY 0.70
#define MENU_OPACITY 0.70
#define TOOLTIP_OPACITY 0.70
```

**OR** if you want **less** transparency, use these:

```
/* Opacity settings */
#define GRADIENT_OPACITY 1.00
#define WINDOW_OPACITY 0.85
#define ENTRY_OPACITY 0.92
#define NOTEBOOK_OPACITY 0.90
#define MENUBAR_OPACITY 0.85
#define MENUBAR_GLOSSY_OPACITY 0.85
#define MENUBAR_STRIPED_OPACITY 0.85
#define TOOLBAR_OPACITY 0.85
#define TOOLBAR_GLOSSY_OPACITY 0.85
#define MENU_OPACITY 0.85
#define TOOLTIP_OPACITY 0.85
```

Now, save, close, and go back into Terminal. From there do this:

```
./configure --prefix=/usr/ --enable-animation
```
```
make
```
```
sudo checkinstall
```

Congratulations, you successfully configured and built your own package. Check the original link you provided ([[http://gnome-look.org/content/show.php/Darkness+gtk2+%28rgba+true%29?content=124548](http://gnome-look.org/content/show.php/Darkness+gtk2+%28rgba+true%29?content=124548)) to tweak it just the way you like it.

---

### Post by X-Windows on 2010-05-25
Thanks for your explanation, I have finished the code without issue, but nothing has changed. I'm sure I still need to do some setup somewhere. Emerald still sets the window borders though. I looked through the Appearance > Install > /home/tempbuild folder and couldn't find any theme packages. I'm afraid I dont know what all the code did in the end, it seemed to install some debian patches and gnome-color-chooser but no theme? Sorry for all the questions, I see now why the theme creator said this is *not* a plug-and-play theme...

---

### Post by isaacj87 on 2010-05-25
> **X-Windows said:**
> Thanks for your explanation, I have finished the code without issue, but nothing has changed. I'm sure I still need to do some setup somewhere. Emerald still sets the window borders though. I looked through the Appearance > Install > /home/tempbuild folder and couldn't find any theme packages. I'm afraid I dont know what all the code did in the end, it seemed to install some debian patches and gnome-color-chooser but no theme? Sorry for all the questions, I see now why the theme creator said this is *not* a plug-and-play theme...

Sorry, I guess I forgot to mention you need to install the theme. This part is easy, however.

Just download the theme: [http://gnome-look.org/content/download.php?content=124548&id=1&tan=18719254&PHPSESSID=5b3db5584a04107159da3de265600fd7](http://gnome-look.org/content/download.php?content=124548&id=1&tan=18719254&PHPSESSID=5b3db5584a04107159da3de265600fd7)

It's best to save it to the desktop. Now, right click on the desktop and choose "Change Desktop Background."

From there, move over to the "Theme" tab and simply drag and drop the file you download into the window. Voila! You've now installed the theme. Select the theme to use it. If you see no difference (aka no transparency) try logging out and back in.

Basically, the instructions I wrote up there explained *how* to enable transparency, but you have to have a theme that *uses* transparency. Let me know how it works out for you :)

---

### Post by X-Windows on 2010-05-25
Ah thanks that fixed it. Is there a way to execute the **emerald --replace** command on startup instead of opening the terminal to fix window borders? I imagine it would need to be entered in a startup config file somewhere in the boot folder?

---

### Post by isaacj87 on 2010-05-25
Yeah definitely.

Just go to System -> Preferences -> Startup Applications

On the right, click "Add."

Where it says Name:

```
Emerald
```

Where it says Command:

```
emerald --replace
```

and you can leave "Comment" blank if you wish.

Commands are case-sensitive, so make sure you put the command correctly or it won't load. Post a pic in the screenshot thread in the Community Cafe to show off your work!

---

### Post by X-Windows on 2010-05-26
So that's what that was. Thanks for all your help isaac! I just have one more question, is it possible to make the marked areas transparent? I turned RGBA support on in the color-chooser but it still doesn't allow for transparent backgrounds. I've heard rumors that it is possible to have transparent window backgrounds.

[IMG]http://img696.imageshack.us/img696/8749/screenshot1eu.png[/IMG]

---

### Post by isaacj87 on 2010-05-26
Technically, yes. However, it'll effect the *entire* window. If done tastefully, it could look pretty cool.

You'll have to use Compiz in order to achieve this effect.

First, we need to make sure CompizConfig-Settings-Manager is installed.

1) Open up a Terminal window, copy and paste this:

```
sudo aptitude install compizconfig-settings-manager
```

Now, let's open it. Navigate to System -> Preferences -> CompizConfig Settings Manager

Within CCSM, look or search a plugin titled, "Opacity, Brightness, and Saturation."

In that plugin,  in the frame titled, "Window Specific Settings" click "New." Now, in the new window, go ahead and turn the "Window Value" up to 90. (**You need to do this first!** If you don't, your windows will be completely transparent and you won't be able to see anything). Now, in the "Windows" field, type "Normal" (without quotes, of course). Go ahead and click close and enable the plugin located on the left.

This will make the entire window slightly transparent. You can adjust the opacity to your tastes.

---

### Post by X-Windows on 2010-05-26
Wow, you really know your stuff! Turns out compiz opacity works much better with the pseudo-transparent window borders. Is it possible to edit either the panel.rc or the gtkrc files so that the theme does not affect the panels? The theme is missing some pixmaps.
[IMG]http://img168.imageshack.us/img168/7753/screenshot2xm.png[/IMG]

---

### Post by isaacj87 on 2010-05-26
> **X-Windows said:**
> Wow, you really know your stuff! Turns out compiz opacity works much better with the pseudo-transparent window borders. Is it possible to edit either the panel.rc or the gtkrc files so that the theme does not affect the panels? The theme is missing some pixmaps.
[IMG]http://img168.imageshack.us/img168/7753/screenshot2xm.png[/IMG]

Well, yes and no. I've done something like what you've asked, but it was a royal pain in the butt to tweak and check, tweak and check. You know what I mean? Technically, you can enter the panel.rc and gtkrc file and comment out all the sections calling to a specific pixmap for the theme. It isn't *too* difficult, but it does take time.

From the looks of it, I'm assuming you want to make the panel completely transparent. If you're not too concerned with having panel background you could just turn it off and go "naked."

Try this and see if you like it. Right click on an empty part of the panel. You'll see an option labeled "Properties." In the new window, move over to the "Background" tab. From there, choose "Solid Color" and adjust to your desired color/opacity preference. If that doesn't float your boat, I'd be willing to edit the theme. Just live me a download link so I can edit it and pass it back to you. :)

---

### Post by X-Windows on 2010-05-26
I'd hate for you to have to do all the hard work, is it just going in and commenting out all the panel related pixmaps? If so I should be able to do it. I imagine to check it the process is Save > Update > Switch themes > Switch back? Right now I have the messed up part moved to another auto-hide panel, but it would be nice to have one transparent panel.

---

### Post by isaacj87 on 2010-05-26
> **X-Windows said:**
> I'd hate for you to have to do all the hard work, is it just going in and commenting out all the panel related pixmaps? If so I should be able to do it. I imagine to check it the process is Save > Update > Switch themes > Switch back? Right now I have the messed up part moved to another auto-hide panel, but it would be nice to have one transparent panel.

Yup and yup. Did the suggestion about enabling a solid colored transparent panel not work? 

One thing you could do (it'd be easier, but you'll get some garbage messages in Terminal sometimes) is just delete the panel pixmap images from the theme folder.

(I'm on my OS X comp right now, so I can't tell you where everything is ATM)

---

### Post by X-Windows on 2010-05-26
The transparent solid panel just made the empty space transparent, the "main menu" clock and other doodads still have a funky semi trans effect I cant seem to get rid of. Below is a photo of what happened when i set the background to 0% opacity, the entire middle and all empty space is transparent, but anything that has a pixmap is solid. I remember doing a fix for this on one of my earlier installs of Ubuntu, by following these instructions. [http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm)

I tried it again, but it doesn't seem to work with the murrine engine.  

[IMG]http://img709.imageshack.us/img709/6832/screenshot3fp.png[/IMG]

---

### Post by isaacj87 on 2010-05-27
> **X-Windows said:**
> The transparent solid panel just made the empty space transparent, the "main menu" clock and other doodads still have a funky semi trans effect I cant seem to get rid of. Below is a photo of what happened when i set the background to 0% opacity, the entire middle and all empty space is transparent, but anything that has a pixmap is solid. I remember doing a fix for this on one of my earlier installs of Ubuntu, by following these instructions. [http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm](http://www.techsupportalert.com/content/ubuntu-tips-and-tricks.htm)

I tried it again, but it doesn't seem to work with the murrine engine.  


We can fix this and it's not hard. I just need to know the exact theme you're using.

---

