---
title: "set a custom Icon for an application"
date: 2008-04-25
forum: Desktop Environments
---

### Post by ivotron on 2008-04-25
Hi,

When I run gvim, the window doesn't show its icon (the one shown in the menu), it shows the default 'application' icon (the cube in the window and the 'ninja star' in the taskbar).

I've tried everything, I installed gnome-icon-theme but nothing happens. Does the binary has the icon embeded in it? How can I modify it

Thanks

---

### Post by spupy on 2008-04-25
> **ivotron said:**
> Hi,

When I run gvim, the window doesn't show its icon (the one shown in the menu), it shows the default 'application' icon (the cube in the window and the 'ninja star' in the taskbar).

I've tried everything, I installed gnome-icon-theme but nothing happens. Does the binary has the icon embeded in it? How can I modify it

Thanks

Open a terminal and type:
```
locate gvim*png
```
It will list all gvim directories containing PNG's. Presumably, you will find there the icons that gvim uses and that are bothering you. With sudo you can replace these icons with something you like.

---

### Post by Bubba64 on 2008-04-25
You can also right click on properties of the icon you want to change then click on the icon and then look at the icons that come up and look through others by clicking on drop down and you can also put in the search bar blah.png for whatever your looking for to bring up another icon menu.

---

### Post by ivotron on 2008-05-24
> **spupy said:**
> Open a terminal and type:
```
locate gvim*png
```
It will list all gvim directories containing PNG's. Presumably, you will find there the icons that gvim uses and that are bothering you. With sudo you can replace these icons with something you like.

I already did this and it isn't working. It looks like the binary has the icon embedded. It's really frustrating because I have two other applications that doesn't get its icon assigned to it and when I switch task by pressing alt-tab its hard to get to vim.

The funny thing is that I have in another computer Xubuntu Hardy with the same packages installed and when I open gvim it actually displays the icon.

Thanks for you reply.

---

### Post by spupy on 2008-05-24
> **ivotron said:**
> I already did this and it isn't working. It looks like the binary has the icon embedded. It's really frustrating because I have two other applications that doesn't get its icon assigned to it and when I switch task by pressing alt-tab its hard to get to vim.

The funny thing is that I have in another computer Xubuntu Hardy with the same packages installed and when I open gvim it actually displays the icon.

Thanks for you reply.

So you mean gvim gets the icon that is for apps that don't have their own icon? If the other computer has an icon for gvim, is it possible that you are just missing this icon? Search the other computer with locate to find what icon gvim uses. It sounds to me very un-linux-ish for an app to have an embedded icon.

---

### Post by ivotron on 2008-06-19
> **spupy said:**
> So you mean gvim gets the icon that is for apps that don't have their own icon? If the other computer has an icon for gvim, is it possible that you are just missing this icon? Search the other computer with locate to find what icon gvim uses. It sounds to me very un-linux-ish for an app to have an embedded icon.

Hi spupy, thanks for taking the time and replying.


The command I invoke in order to run gvim is gvim. When I look for what gvim is, I get the following:

```
$ ll /usr/bin/gvim*
lrwxrwxrwx 1 root root 22 2008-05-28 14:22 /usr/bin/gvim -> /etc/alternatives/gvim*
```

Then, gvim in alternatives:
```

$ ll /etc/alternatives/gvim
lrwxrwxrwx 1 root root 18 2008-05-28 14:22 /etc/alternatives/gvim -> /usr/bin/vim.gnome*
```

And vim.gnome is a binary file.

Then, in theory, if I put a file in /usr/share/pixmaps/ called vim.gnome.[png | svg | xpm] the icon should appear, right?

The problem I'm having is that I don't get any icon for the window. I have ubuntu on my desktop pc and when I open the gvim app, the icon is there. I have tried putting a 48x48 icon png file for vim.png, gtk-vim.png, gnome-vim.png, gvim.png, gnomevim.png and gvim.png. None have worked.

Thanks for your help.

---

### Post by denham2010 on 2008-06-20
Hiya,

Programs operate differently when it comes to the icon displayed on the titlebar.

Firstly, the program needs to have been written to look for an icon to place in the titlebar. Not all programs do.

If a program is going to look for an icon for the title bar, the first place it will most likely be is in the program's root folder (for most linux distros /usr/share/<progname>). Reason being this folder will be the same for every installation of the program (remembering, a lot of apps are cross platform, and different distros may install programs in different paths).

The next alternatives are /usr/share/pixmaps, /usr/share/icons and also ~/.icons (remembering you may not be using the default system theme!)

The icons in /usr/share/pixmaps, /usr/share/icons and ~/.icons are generally just used for program launchers (*.desktop files). These being what are displayed in your menus.

To get a program to display it's icon in the title bar, I would suggest checking it's root folder, and (if there is not an icon in there) placing an icon in there (you will more than likely need to be root to do this). Remembering, the name of the icon will need to be correct for it to be used, and it may not be as simple as just using the program name. Also bear in mind, they type of image may make a difference as well (.png, .jpg, .xpm etc) as it all comes down to how the application was programmed.

Having a look at the source code of the app may shed some light on:

1 - If it looks
2 - Where it looks
3 - What it looks for.

Cheers.

---

### Post by ivotron on 2008-06-20
Hi denham2010, thanks a lot for your reply.

I've looked in vim's installation folder (/usr/share/vim/) and there's no image inside it. I'm now at my desktop PC, where I'm running Ubuntu and where the icon is properly shown and after doing a locate *vim*png I can see that the icon that the vim-gnome package installs is in /usr/share/pixmaps/ and its called gtkvim.png. In my laptop (running Xubuntu and where the problem is appearing) I placed the same image with the same name at the same place and it doesn't display it.

I'm using the Tango icon theme and I've also tried placing the .png and .svg images in each subfolder of it, as well as in every other theme folder. No luck.


So, I don't know what else to do. I've posted the question to the xubuntu-users mailing list. Hope they can help.

---

### Post by denham2010 on 2008-06-20
Hi Ivotron,

Just a quick question, are you using the same window manager on both machines?

Eg. compiz-fusion with emerald on both machines, or emerald on one and xfwm4 or metacity on the other etc...

If they are using different window managers, it may be in the way metacity (gnome default window manager), xfwm4 (xfce default window manager) and emerald (default compiz-fusion window manager) handle icons in title bars that could be causing the issue.

Thoughts?

---

### Post by ivotron on 2008-06-22
Hi denham2010,

Both are using emerald :???:

---

### Post by ivotron on 2008-07-02
Finally!!!!!

So I copied my .gvimrc file from my Laptop (Xubuntu; no GVim icon in window) to my desktop(Ubuntu; GVim icon in window) and it the icon disappeared! Hence, the source of the problem is this configuration file by itself.

The problem was that I had the following option inside my .gvimrc file:

```
set guioptions=

```
I set this variable to nothing since I don't use the toolbar (T) neither the menubar (m) but it turns out that there are also other things you can modify for the GUI interface, one of this being the icon!!!

From the :help 'guioptions' command:

	  ```
'i'	Use a Vim icon.  For GTK with KDE it is used in the left-upper
		corner of the window.  It's black&white on non-GTK, because of
		limitations of X11.  For a color icon, see |X11-icon|.

```

I modified to

```
set guioptions=i

```

So now I have GVim's window icon back :) 

One question arises though. Where is this image physically located? I deleted all the files from the /usr/share/pixmaps/ folder that are related to Vim and the icon is still there, so my guess is that it's really embedded in the binary file.

Thanks!

---

