---
title: "Manage, group, tile and resize multiple (OpenOffice) windows"
date: 2010-08-31
forum: Desktop Environments
---

### Post by balta on 2010-08-31
Hi there,
 I've been having this "issue" for a while but only now I really need to get it "solved".
Formerly I used to use Windows, and under it Word to work.
Now I switched to Ubuntu and OpenOffice but there is a very useful feature I miss:

I liked how Word was able to display any number of opened files dividing equally the space between each window, horizontally or vertically. (Which was very useful when working comparatively on a couple or more text files).

I'm currently unable to do this in an automated way (ie: without resizing manually all the windows).

Is there some tool or trick I am missing?
Is there a program that can quickly and easily help me achieve this result?
Maybe the solution is an OpenOffice add on?

Thanks for your help!

PS: If this is not the right section of the forum please fix it (if you can) or PM me so I can have it fixed ;)

---

### Post by hariks0 on 2010-08-31
Install Compiz and there are plenty of ways to manage/tile/group windows under Window Management. :)

---

### Post by balta on 2010-08-31
Thanks for your response but you see, I'm not really in a good relationship whit compiz-config, let me say that
1) I don't really understand what those things do
2) every time I go there I do something wrong (I just tried to make this work and as a result I lost my rotating-two-faced-desktop-cube and Alt+Tab #-o)

So if you are able to configure compiz to achieve what I was looking for would you please be so kind to post me a, let me call it, tutorial on how to get things done?

Thanks however for your attention (I promise I'll be trying to surpass my hate for compiz-config :P)

Hope to read from you soon ;)

---

### Post by hariks0 on 2010-08-31
OK. BTW, you have to change the number of desktops to a minimum of 4 to have the Desktop cube and 2 for the Desktop wall. It is under General > Desktop size. Regarding the Alt+Tab, you may try activating the Application switcher under Window Management. If it asks for resolving conflicts, disable the module that uses the same key binding already.
:)

---

### Post by balta on 2010-08-31
Really thanks man for your help!
I just fixed the alt+tab and the desktop cube (which can actually be made with only two desktops ;))!
I'll now keep on trying with compiz!
Hope to find a solution and post it here.

If anyone has already struggled over this and has the right configuration to achieve automatic window resizing please share it!

Thanks!

---

### Post by hariks0 on 2010-08-31
1. You can use the grid or tile plugin of Compiz.
2. A simple program to tile windows horizontally and vertically can be found at [http://tile-windows.googlecode.com/](http://tile-windows.googlecode.com/) .Download source archive extract and make.
Use "path/to/executable/tiler -v" to tile windows vertically or "path/to/executable/tiler -h" to tile windows horizontally in commands of compiz. [Refer the first link in my signature]

3. Gnome-Do has a plugin which enables you to perform the Tiling and Cascading of windows. Just check in Gnome-Do's Preferences if the Window Manager plugin is ticked. It allows you to control windows for each workspace.

The following links may be of use to you in the meantime.

[xTile]("http://www.giuspen.com/x-tile/")
[Arrange]("http://manpages.ubuntu.com/manpages/jaunty/man1/Arrange.1x.html")
[ctrlwm]("http://ubuntuforums.org/showthread.php?t=1288385"):popcorn:

---

### Post by balta on 2010-08-31
xTile totally did the trick!
Perfectly what I was looking for!
I think it should be available from the Ubuntu-software-center!
Thanks man

---

