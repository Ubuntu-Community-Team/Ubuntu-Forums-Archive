---
title: "Changing the default application launcher"
date: 2009-06-20
forum: General Help
---

### Post by dizwell on 2009-06-20
When I inserted a DVD, a dialog appeared saying 'which application do you want to launch' to play the thing. I chose to enter a custom command and selected the 'always do this' option.

Unfortunately, the command I typed in was wrong.

How do I now change what the default application to be launched when a DVD is inserted should be? Or, how do I make the system prompt me again so I can type the right command in?

This is 9.04 x64

---

### Post by divague on 2009-06-20
Go to System->Preferences->Preferred Applications

---

### Post by mc4man on 2009-06-20
It's in file management -> media which is an option in system -> preferences that's not enabled by default. (enable in edit menus

Or go in terminal    ```
nautilus-file-management-properties

```
Or nautilus -> edit -> prefereces

Or insert a dvd and hold down the shift button, the pop up will return

When you used the custom command it created a userapp.desktop in ~/.local/share/applications with a blue diamond icon and a display name of the app in the command

The real file name would be userapp-<appname>-xxxxxx.desktop, at this point you could find the real name in ~/.local/share/applications/mimeapps.list.
It would be the first listed (default) on this line

x-content/video-dvd=

If you wanted to you could right click on the .desktop in ~/.local/share/applications -> properties and change the command, icon and display name or leave it or delete it.
If you delete it then you may want to delete the entry in the line in mimeapps.list

If so do carefully, ex. below (a custom command for mplayer
```
x-content/video-dvd=[COLOR="Blue"]userapp-mplayer-2V6RVU.desktop;[/COLOR]vlc.desktop;totem.desktop;
```
```
x-content/video-dvd=vlc.desktop;totem.desktop;
```

to make clear removed this (note that includes the ;

userapp-mplayer-2V6RVU.desktop;


If you edit it or create a new custom definition it's usually good to go into ~/.local/share/applications, find the .desktop and give it a distinctive name, you can easily end up with multiple ones with the same display name even though the commands are different.

The actual file name will always be unique and **cannot be changed** (the actual filename is what's used and displayed in mimeapps.list

---

### Post by dizwell on 2009-06-20
Perfect answer! Thankyou so much.

1) the stuff about .local/share/applications is the real nitty-gritty stuff and being able to clear out the long list of silly experiments I'd created was very nice!

2) the tip about holding down the shift key as a DVD was inserted counts, perhaps, as the true answer here, in the sense that that one tip alone allowed me a second chance to type in a new command.

Wonderful stuff. Thankyou so very much: greatly appreciated.

---

### Post by mc4man on 2009-06-20
there are alot of advantages to getting familar and comfortable with ~/.local/share/applications and mimeapps.list.

sometimes it's more useful to edit a .desktop directly in a text editor, though for that you'd need to know the 'real name'

While for appname.desktops it's simple, for userapp.desktops not so, you need to track it down in mimeapps.list, then use the path/name in the terminal. 

 What's very useful instead is to install nautilus-actions and make yourself a 'open in text editor' action. 
(then you can r. click on a .desktop -> open with your nautilus action

(command of gedit, parameters of %M

While most of this was for hardy, which because of the lack of a 'use custom command' in file man. -> media made things a bit more difficult, the ides and methods still hold true.

Sometimes it's nicer to use a 'normal' .desktop, either creating your own or coping an existing one with a name change on the way in. (I used to 'borrow one from unused apps like gxine and cd audio extrator, no longer do so, either use an existing with name change, create a new one or an userapp (custom comm.

Among other things, editing in the .desktop allows you to add your copied, created or userapp.desktops to your Applications menu 

Somewhat scattered thread on subject and Ex.s

[http://ubuntuforums.org/showthread.php?p=5633803#post5633803](http://ubuntuforums.org/showthread.php?p=5633803#post5633803)

---

