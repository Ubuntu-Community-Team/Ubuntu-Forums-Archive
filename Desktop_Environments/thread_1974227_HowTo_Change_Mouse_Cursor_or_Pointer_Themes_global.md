---
title: "HowTo: Change Mouse Cursor or Pointer Themes globally and persistently."
date: 2012-05-05
forum: Desktop Environments
---

### Post by ohnonot on 2012-05-05
[B][edit: this started off as a failproof how-to but turned out to have slings and traps. if this first post works for you, fine. otherwise you might want to start [here]("http://ubuntuforums.org/showpost.php?p=11928568&postcount=10").]

[/B]problem: changing mouse pointers (cursor themes) does not work under xubuntu/xfce.
usually changing the theme from xfce4-settings-manager takes effect in firefox and other apps, but when moving the pointer onto window decorations it reverts to the default theme.

searching on the net shows that this problem has been around for years, and still is, and there's dozens of fixes/half-solutions/requests around.

here's one that works on my regular xubuntu distro (11.10) with xfce 4.8 - and believe me, i've been trying all kinds of things, logging out and in after every change, rebooting many times... this one is 100% - at least on my setup - and i just feel that it's worth sharing.

here it comes:

You change the cursor theme from xfce4-settings-manager -> Mouse -> Theme.
then you find a file called .Xdefaults in your home folder. probably it will have an entry:```
Xcursor.theme: PolarCursorTheme # or whatever you have there
```if not, put it there.
change that name to your new cursor theme as named in the settings-manager.

Now you have to REBOOT (logging out and in is NOT enough!) and after that you should have your desired cursor theme everywhere. if not, try this:

- have your cursor themes in /usr/share/icons instead of ~/.icons
- make sure they have the proper permissions and ownership, and make sure all the files have them. if not apply them recursively (usually read and write for root, read only for all others) for the whole folder.
- make sure the theme name inside index.theme matches the name in your .Xdefaults (additionally, it's surely safest if the theme has exactly the same name as the folder it's in)
- if you made changes, reapply the theme from settings-manager (change to a different theme and back to the one you want) and REBOOT again.

:popcorn:enjoy!

PS: lots of cursor themes from gnome-look.org - or xfce-look.org. - section X11 mouse themes

PPS: I haven't updated for a couple of months; if this has been fixed, please let me know.

---

### Post by ohnonot on 2012-05-08
edit:
i just found out that i had login set to autologin while i did all this experimenting; 
i just proved empirically that when i unset the autologin (that's in /etc/lightdm/lightdm.conf for xubuntu, setting autologin-user= (meaning nil))
the greeter somehow changes the mouse pointer to the default pointer.
i tried adding the same line as in .Xdefaults to the lightdm-gtk-greeter.conf but it doesn't help.
there is still one option to set the "ancient" default cursor with this:```
sudo update-alternatives --config x-cursor-theme
```- but i don't know how to add themes to that list.
for me it's not a biggie because i use autologin if i'm not digging deep inside the bowels of my OS - for you it mayb is.

so  if someone knows how to add cursor themes to the list provided by this:```
sudo update-alternatives --config x-cursor-theme
```- i'd be happy to  know!

---

### Post by Toz on 2012-05-08
Try this:
```
sudo update-alternatives --install /etc/alternatives/x-cursor-theme x-cursor-theme /usr/share/icons/<Cursor> 51
```
...where <Cursor> is the name of the cursor directory _and_
...51 is the priority.

---

### Post by stinkeye on 2012-05-09
I found that editing 2 settings when changing the mouse cursor makes
the change consistent.
```
gsettings set org.gnome.desktop.interface cursor-theme "[COLOR="Magenta"]$CURSOR[/COLOR]" &
	sudo ln -fs /usr/share/icons/[COLOR="magenta"]$CURSOR[/COLOR]/cursor.theme /etc/alternatives/x-cursor-theme
```
...where [COLOR="magenta"]$CURSOR[/COLOR] is your cursor-theme name.

I wrote this which will list your cursor-themes in **/usr/share/icons**
allowing you to chose your theme and run the above commands with the option to restart lightdm.

Save as **change_cursor** and make executable.
```
#!/bin/bash

### Script to change cursors in /usr/share/icons ###

#
## create installed cursor list text file
ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt

# 
## show a numbered list of cursors to choose from
cat -b ~/.cursorlist.txt 
 
	echo -e "\033[36mEnter your theme selection number:\033[0m"
	read CHOICE

#
## match the theme selection number to the cursor name
CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p') 
	echo -e "\n\033[36mYou have selected ...$CURSOR\nContinue?(y/n):\033[0m"
	read Ans
if  [ "$Ans" != "y" ]; then
exit
else

#
## Change to selected  cursor ###
	gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" &
	sudo ln -fs /usr/share/icons/$CURSOR/cursor.theme /etc/alternatives/x-cursor-theme
	#sudo sh -c "echo '[Icon Theme]\nInherits=$CURSOR' > /usr/share/icons/DMZ-White/cursor.theme"
fi

#
## Restart session to complete cursor change ###
	read -p "Do you wish to restartx? Save any work as you will now be logged out.(y/n):"
if  [ "$REPLY" != "y" ]; then 
	echo -e "\033[36m\nYou need to log out to complete cursor change.\033[0m";
else 
	sudo service lightdm restart
fi 
```
To run click on **change_cursor** and choose to **Run in Terminal**.


***I have downloaded some themes which do not include a **cursor.theme** file.
You will need to create one for that theme for the script to work
Look in **/usr/share/icons/DMZ-White/cursor.theme** for the correct format.

---

### Post by ohnonot on 2012-05-11
i messed it up.
stinkeyes script gives this message:```
Enter your theme selection number:
3

You have selected ...ATER
Continue?(y/n):
y
[sudo] password for holy: 
ln: accessing `/etc/alternatives/x-cursor-theme': Too many levels of symbolic links
Do you wish to restartx? Save any work as you will now be logged out.(y/n):

```...and doesn't change anything.
my
```
sudo update-alternatives --config x-cursor-theme
```returns another error:```
update-alternatives: using /usr/share/icons/ATER to provide /etc/alternatives/x-cursor-theme (x-cursor-theme) in manual mode.
update-alternatives: error: unable to install /etc/alternatives/x-cursor-theme.dpkg-tmp as /etc/alternatives/x-cursor-theme: No such file or directory

```and toz's command - no error, but no effect either
:confused:

---

### Post by Enigmapond on 2012-05-11
You don't actually need the script to accomplish this although it is very handy. you can simply write the name of the cursor theme in /etc/alternatives/x-cursor-theme.

```
sudo gedit /etc/alternatives/x-cursor-theme
```

Next to Inherits=put the theme name here. Save log out/in and it will be changed....just another way.

---

### Post by Toz on 2012-05-11
> **ohnonot said:**
> and toz's command - no error, but no effect either
:confused:
After running that command, try running:
```
sudo update-alternatives --config x-cursor-theme
```
...to set the cursor theme.

---

### Post by Dennis N on 2012-05-11
> **ohnonot said:**
> and toz's command - no error, but no effect either
:confused:

A little analysis:

First of all, x-cursor-theme in the /etc/alternatives directory is a **symbolic link**.

Now, from the man page for update-alternatives, here is the syntax and definition of terms of the install option:

> update-alternatives --install _link_ _name_ _path_ _priority_

..._link_ is the  generic name for the master link, _name_ is the name of its symlink *in the alternatives directory*, and _path_ is the alternative being introduced for the master link.

the target of _link_ is _name_ (in the alternatives directory) and the target of _name_ is _path_. (Note: in an actual command, _path_ would be replaced by the complete path to the cursor.theme file in the new cursor's folder.)

if _link_ is set as /etc/alternatives/x-cursor-theme, and _name_ as x-cursor theme, realize that this makes _link_ = _name_ since the second argument of the command is by definition in /etc/alternatives.

The command will just be ignored and the new cursor is not installed into the alternatives, as a symlink cannot have two targets (x-cursor-theme pointing to both path and itself.) Obviously, also not a good practice to link a symbolic link to itself.

---

### Post by zombifier25 on 2012-05-12
> **Dennis N said:**
> A little analysis:

First of all, x-cursor-theme in the /etc/alternatives directory is a **symbolic link**.

Now, from the man page for update-alternatives, here is the syntax and definition of terms of the install option:

the target of _link_ is _name_ (in the alternatives directory) and the target of _name_ is _path_. (Note: in an actual command, _path_ would be replaced by the complete path to the cursor.theme file in the new cursor's folder.)

if _link_ is set as /etc/alternatives/x-cursor-theme, and _name_ as x-cursor theme, realize that this makes _link_ = _name_ since the second argument of the command is by definition in /etc/alternatives.

The command will just be ignored and the new cursor is not installed into the alternatives, as a symlink cannot have two targets (x-cursor-theme pointing to both path and itself.) Obviously, also not a good practice to link a symbolic link to itself.

This +1


I have tried various method to change the cursor theme and make it consistent; none works except for this: remove the "default" folder in /usr/share/icons, and make "default" a symlink to the folder of the cursor theme, log out and log in. Done. Simple. Fast. No tampering with /etc/alternatives/x-cursor-theme needed.
(it's 2012 and a dirty hack is still required to make the cursors on Firefox and the desktop and the window borders look similar. What The Chuck?)

---

### Post by ohnonot on 2012-05-12
wow, so many answers!
first of all:> **zombifier25 said:**
> I have tried various method to change the cursor theme and make it  consistent; none works except for this: remove the "default" folder in  /usr/share/icons, and make "default" a symlink to the folder of the  cursor theme, log out and log in. Done. Simple. Fast. No tampering with  /etc/alternatives/x-cursor-theme needed.
(it's 2012 and a dirty hack is still required to make the cursors on  Firefox and the desktop and the window borders look similar. What The  Chuck?)- i agree with your complaint!
apart from that, i *think* the setting in ~/.Xdefaults has priority over /usr/share/icons/default.
anyhow, it doesn't solve the problem to make the cursor theme persistent throughout major changes in the session. that's a foggy way of saying it, i know.
if i can influence the cursor theme as it looks *before* i log in, then it's pretty persistent i would say.
of course i then still have to set the right cursor theme for the desktop environment.

it *seems* that [the solution is found here]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647/comments/110").

a HUGE thanks to Dennis N who [set me off in the right direction]("http://ubuntuforums.org/showpost.php?p=11927663&postcount=8").
i think you not only took the time to read the whole thread but also to analyse all the half-truths and errors, including, of course, my own.

having said that, i am as thankful to everyone else.
:popcorn:

> **Toz said:**
> Try this:
```
sudo update-alternatives --install  /etc/alternatives/x-cursor-theme x-cursor-theme  /usr/share/icons/<Cursor> 51
```...where <Cursor> is the  name of the cursor directory _and_
...51 is the priority.- so this would be the WRONG version which is surprisingly wide spread on the internet. or maybe it works on some systems?!

next: how do i *remove* items from the list i get with```
sudo update-alternatives --config x-cursor-theme
```???

---

### Post by Toz on 2012-05-12
> **ohnonot said:**
> - so this would be the WRONG version which is surprisingly wide spread on the internet. or maybe it works on some systems?!

next: how do i *remove* items from the list i get with```
sudo update-alternatives --config x-cursor-theme
```???

Sorry for the confusion, but my post was simply in reply to the question on how to add an item to the alternatives list. To remove the item from the list, try this:
```
sudo update-alternatives --remove  x-cursor-theme  /usr/share/icons/<Cursor>
```

---

### Post by zombifier25 on 2012-05-12
> **zombifier25 said:**
> 
I have tried various method to change the cursor theme and make it consistent; none works except for this: remove the "default" folder in /usr/share/icons, and make "default" a symlink to the folder of the cursor theme, log out and log in. Done. Simple. Fast. No tampering with /etc/alternatives/x-cursor-theme needed.
(it's 2012 and a dirty hack is still required to make the cursors on Firefox and the desktop and the window borders look similar. What The Chuck?)

Forgot the extra step of choosing the desired theme in Ubuntu Tweak (or MyUnity, etc.) Now that should work.
BTW, I don't have a .Xdefault in my home.

---

### Post by Dennis N on 2012-05-12
> **ohnonot said:**
> 
- so this would be the WRONG version which is surprisingly wide spread on the internet. or maybe it works on some systems?!
[/CODE]???

The install command from Toz works fine provided you change the first link to the one that is outside /etc/alternatives and points to x-cursor-theme.

What should it be? If you check /usr/share/icons/default/index.theme (properties, or use ls -l) you will see it is a link to x-cursor-theme. This is the link we want to use.

The correct command would be:

```
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/NewCursor/cursor.theme 20

```

where NewCursor is the name on the folder of the one you want to install. As mentioned in post #4, you may need to create a cursor.theme file for it.


The priority number is not really important, since by setting this manually, this new cursor is used regardless of priority.

I know this works. I have installed two extra cursors I downloaded from gnome-look.org, and they show up after the [COLOR="Red"]sudo update-alternatives --config x-cursor-theme[/COLOR] command is given.

**Don't forget:** For Unity, you also need to change the gnome cursor (if that's the proper term) to the same theme by using the 'advanced settings' tool.

---

### Post by ohnonot on 2012-05-12
> **Dennis N said:**
> The correct command would be:```
sudo update-alternatives --install  /usr/share/icons/default/index.theme x-cursor-theme  /usr/share/icons/NewCursor/cursor.theme 20

```where NewCursor is the name on the folder of the one you want to  install. As mentioned in post #4, you may need to create a cursor.theme  file for it.
- this is exactly what i did.
in my last post, the sentence "the solution is found here" had the wrong link; corrected it now; _[This]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/459647/comments/110")_ is the right one.

> **zombifier25 said:**
> BTW, I don't have a .Xdefault in my home.- make it! one entry is enough.

---

### Post by Dennis N on 2012-05-12
There is another easy way that doesn't use update-alternatives. Described in this post:

[http://ubuntuforums.org/showpost.php?p=11650342&postcount=22](http://ubuntuforums.org/showpost.php?p=11650342&postcount=22)

It uses instructions (linked in post) given by one of the cursor makers at gnome-look.org. It uses the ln command to make a new symlink from x-cursor-theme to the desired cursor. One liner.

The new cursor won't show up in the alternatives list since it was not 'installed'.

Again, you have to change the gnome cursor too.

---

### Post by stinkeye on 2012-05-12
If instead of adding downloaded cursor themes with update-alternatives,
would overwriting the **/usr/share/icons/default/index.theme** work.


eg The setting changed when using gnome-tweak-tool
```
gsettings set org.gnome.desktop.interface cursor-theme "[COLOR="magenta"]$CURSOR[/COLOR]"
```


and then...
```
sudo sh -c "echo '[Icon Theme]\nInherits=[COLOR="magenta"]$CURSOR[/COLOR]' > /usr/share/icons/default/index.theme"
```
[COLOR="Magenta"]$CURSOR=new theme[/COLOR]

Update-alternatives is probably the best way, this is just so I can use a script.

---

### Post by Dennis N on 2012-05-12
Everybody loves the command line, but there is a utility program with GUI that can do this also:

Install the program **Alternatives Configurator** which is in the Ubuntu repository under the package name **galternatives**.


[B]USING THE GUI PROGRAM ALTERNATIVES CONFIGURATOR (search for this name in the Dash)
[/B]
Preliminary:

Put new cursor folder in /usr/share/icons. Create cursor.theme file if needed.

Start the program: 

You are asked for your password.
Select **x-cursor-theme** from the list in the left.
To add a new cursor, click 'Add' button and browse in the popup window to the new cursor's directory in /usr/share/icons.
Click Open, and select the file cursor.theme
Click ok.
Click ok.
New cursor becomes available in the main window. Select it and close. It will become active after log out.

For Unity: in addition to the above, use 'advanced settings' to complete the job and change the gnome cursor.

---

### Post by stinkeye on 2012-05-12
> **Dennis N said:**
> Everybody loves the command line, but there is a utility program with GUI that can do this also:

Install the program **Alternatives Configurator** which is in the Ubuntu repository under the package name **galternatives**.


[B]USING THE GUI PROGRAM ALTERNATIVES CONFIGURATOR (search for this name in the Dash)
[/B]
Preliminary:

Put new cursor folder in /usr/share/icons. Create cursor.theme file if needed.

Start the program: 

You are asked for your password.
Select **x-cursor-theme** from the list in the left.
To add a new cursor, click 'Add' button and browse in the popup window to the new cursor's directory in /usr/share/icons.
Click Open, and select the file cursor.theme
Click ok.
Click ok.
New cursor becomes available in the main window. Select it and close. It will become active after log out.

As with the manual method, use 'advanced settings' to complete the job and change the gnome cursor.

Thanks, didn't know about galternatives.
Just used it to add and select a new theme and it worked after logout.
...and thanks for the clear instructions.

---

### Post by Dennis N on 2012-05-12
> **stinkeye said:**
> If instead of adding downloaded cursor themes with update-alternatives, would overwriting the **/usr/share/icons/default/index.theme** work.
[/COLOR]


My thought on that:

Lots of people give this method as the way to change the cursor. It 'works', but could have unforseen consequences, since you are actually **directly editing and changing** the cursor.theme file of the active cursor to some other cursor's name after Inherits=.

Especially true if you then change the cursor again with update-alternatives, since that changes the x-cursor-theme link's target to the new cursor instead (and never writes anything to a cursor's file), leaving the previous cursor with the wrong information written in it's cursor.theme file.

---

### Post by ohnonot on 2012-05-13
galternatives is a good one.

---

### Post by vasa1 on 2012-05-13
> **ohnonot said:**
> galternatives is a good one.
Yes, Dennis' suggestion helped me get all aspects, pointer, insertion bar, hourglass in order. Even though every thing worked fine Unity 2D/3D, the Xfce session needed a fix with respect to the cursor/pointer.

Just one comment: Dennis mentioned using Advanced Settings (gnome-tweak-tool) to complete the Gnome side of things. I have it installed but couldn't find it easily in 4.10. I ended up running ```
gnome-tweak-tool
``` from the terminal.

---

### Post by Dennis N on 2012-05-13
> **ohnonot said:**
> galternatives is a good one.

I agree. Faster. Uses the same commands behind the GUI, and avoid making a mistake in typing in the commands yourself.

However, knowing the use of the underlying commands does give you a better understanding on what is going on.

---

### Post by ohnonot on 2012-05-21
i've changed my cursor theme with the methods described here. since then i changed window managers and display managers and start building my own session from scratch - the mouse cursor stays the same. great!
:lolflag::lolflag::lolflag:

---

### Post by ridgeland on 2013-04-07
Thanks.
I'm using Debian Wheezy RC1 Xfce
After changing the mouse theme in the settings menu I got the double standard.
I created ~/.Xdefaults with just the two lines
#
Xcursor.theme: Chameleon-Pearl-Large
Xcursor.size: 36
#
Look in /etc/X11/cursors for the cursors you have installed (just drop the .theme)
After reboot the system is all the same mouse theme.

---

### Post by numberofthebeast92 on 2013-10-10
I figured it out, and thought i would share my methods.

First open a terminal, do these
sudo add-apt-repository ppa:rebuntu16/other-stuff 
sudo apt-get update
sudo apt-get install xfce-theme-manager

And then, before you open up xfce theme manager, go to your home folder, click view, show hidden folders, click .icons, put your cursor theme in there. Then open xfce theme manager, go to cursors, and it should show up. Reboot and voila.

---

### Post by Dennis N on 2013-10-10
> **numberofthebeast92 said:**
> I figured it out, and thought i would share my methods.

First open a terminal, do these
sudo add-apt-repository ppa:rebuntu16/other-stuff 
sudo apt-get update
sudo apt-get install xfce-theme-manager

And then, before you open up xfce theme manager, go to your home folder, click view, show hidden folders, click .icons, put your cursor theme in there. Then open xfce theme manager, go to cursors, and it should show up. Reboot and voila.

Hi numberofthebeast92,

I Installed this to check it out. It seems convenient because settings are within one window, you can save your collection of settings (didn't test), and there are theme previews. 

But it gave me the same bad result when choosing the mouse cursor as using just the "Mouse and Touchpad" dialog under Settings. 

That is, I was left with two different cursor themes depending on what the cursor is over. In Firefox or Libre Office windows, and even over my desktop the new one appears. Over the panels or window borders or in the file manager window, the old default cursor appears. Logged out and back in as well.

You would also still need to change the default cursor to your new one with "Alternatives Configurator" (galternatives) to get the same cursor everywhere.

Tested in Xubuntu 12.10

---

### Post by numberofthebeast92 on 2013-10-10
The reboot part was important, but ill say im on Linux Lite 1.0.6. May make a difference idk. Not saying its gonna work for everyone.

---

### Post by Dennis N on 2013-10-10
Hi, I did reboot too, and it didn't make any difference. Your Linux Lite system is behaving differently than Xubuntu if you don't see this problem. It may have some changes made by its developer to fix the issue. I think when I get some time I will download it and give it a test run.

---

### Post by numberofthebeast92 on 2013-10-10
Yea i mean i went through, Ubuntu 13.04, Fedora, Linux Mint 15, Debian, etc. and this one runs the best in my opinion. Very little resource usage.

---

