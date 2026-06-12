---
title: "Fluxbox questions"
date: 2005-06-14
forum: Desktop Environments
---

### Post by mattack on 2005-06-14
I've been playing around with Fluxbox, and I like it . I have a few questions though.

1. I'm having trouble with the slit. I don't really understand it. How can I get Gkrellm to run in the slit "automagically" when I log in?

2. The system tray... It only holds one icon. For instance if I have two applications running that are minimized to the system tray, only one of them is accessible. Is there a way to make it expand if more than one application is there?

---

### Post by byen on 2005-06-14
same here... i installed fluxbox to check it out and i like the way it looks..but its complicated and takes a lot of my time. I wish there was a walkthrough where these things were explained.. Im having the same trouble with slit as well...lets see if someone who knows flux shares some info.
PS- sorry this wasnt a solution for your problem.

---

### Post by Equanimity on 2005-06-14
[QUOTE=mattack]1. I'm having trouble with the slit. I don't really understand it. How can I get Gkrellm to run in the slit "automagically" when I log in?[/QUOTE]
To start gkrellm as a docked application:
[INDENT][FONT=Courier New]gkrellm -w &[/FONT][/INDENT]
Fluxbox doesn't come with a session manager, so having applications start automatically upon login requires you to create an .xsession file in your home folder. The contents of ~/.xsession in your case would be:
[INDENT][FONT=Courier New]/usr/bin/gkrellm -w &
/usr/bin/fluxbox[/FONT][/INDENT]
I believe the .xsession file needs to be executable:
[INDENT][FONT=Courier New]chmod u+x ~/.xsession[/FONT][/INDENT]
Then change your GDM session type from "Fluxbox" to "Default". This will cause GDM to launch the contents of your .xsession file upon login (in this case launch gkrellm and fluxbox). I havn't tested this myself (I use openbox), but this should launch fluxbox with gkrellm in the slit.

---

### Post by mattack on 2005-06-15
[QUOTE=Equanimity]To start gkrellm as a docked application:
[INDENT][FONT=Courier New]gkrellm -w &[/FONT][/INDENT]
Fluxbox doesn't come with a session manager, so having applications start automatically upon login requires you to create an .xsession file in your home folder. The contents of ~/.xsession in your case would be:
[INDENT][FONT=Courier New]/usr/bin/gkrellm -w &
/usr/bin/fluxbox[/FONT][/INDENT]
I believe the .xsession file needs to be executable:
[INDENT][FONT=Courier New]chmod u+x ~/.xsession[/FONT][/INDENT]
Then change your GDM session type from "Fluxbox" to "Default". This will cause GDM to launch the contents of your .xsession file upon login (in this case launch gkrellm and fluxbox). I havn't tested this myself (I use openbox), but this should launch fluxbox with gkrellm in the slit.[/QUOTE]

This worked like a charm. Thanks.  :) 

Now I have another question...
Is there a way to lock the screen when I walk away, like in Gnome with xscreensaver? Could I just start the xscreensaver daemon by putting it in my .xsessions file?
This is a necessary function of any window manager I use as I have a 2 year old who likes to "pay on da poo-yo" and I don't want him messing things up.

---

### Post by beefsprocket on 2005-06-15
You should be able to edit your .fluxbox/keys file to include a line like the following:

Insert Keys here :ExecCommand xscreensaver-command -lock

i.e.

Control Shift X :ExecCommand xscreensaver-command -lock

An alternate gui method is running fluxkeys. Add an entry. Muddle around a little to choose your keys and ExecCommand, then paste xscreensaver-command -lock into the rightmost box (make sure you have xscreensaver running as a process when fluxbox starts up).

Good luck.

---

### Post by mattack on 2005-06-15
[QUOTE=beefsprocket]You should be able to edit your .fluxbox/keys file to include a line like the following:

Insert Keys here :ExecCommand xscreensaver-command -lock

i.e.

Control Shift X :ExecCommand xscreensaver-command -lock

An alternate gui method is running fluxkeys. Add an entry. Muddle around a little to choose your keys and ExecCommand, then paste xscreensaver-command -lock into the rightmost box (make sure you have xscreensaver running as a process when fluxbox starts up).

Good luck.[/QUOTE]

I tried adding the following to my ~/.xsession file
```
/usr/bin/xscreensaver -no-splash
```
in every possible place (first, second, and third)
but it borks everything up. No menu when I right-click and no toolbar either, so I guess that Fluxbox isn't running correctly when I do this. First is the worst because Gkrellm doesn't even load.
My ~/.xsession file:
```
/usr/bin/gkrellm -w &
/usr/bin/fluxbox

```

how can I get xscreensaver running so it doesn't bork everything when I start Fluxbox? DoI need to make it 
```
/usr/bin/xscreensaver -no-splash -W &
```

---

### Post by jonrkc on 2005-06-15
Those of you new to Fluxbox and experimenting with it--be sure to try out the tabbed-application feature.  (Middle-click on the titlebar of an app, move it to overlap an existing titlebar, and then the two apps are joined. You can change their positions at will in a similar way.)  I generally have seven or eight applications going at once, all day long, that I use frequently, and it's easy to join them ALL together and have just one "window" showing, whose contents change as I simply mouseover the name of the app I want next.  The best word I can find for the feeling is "graceful."  It is really a pleasant way to work, especially when you have favorite apps you use daily.

You can, of course, group them by category, and/or on different workspaces.  Increasingly I find I like to use just one workspace, especially with this space-saving tabbed method.

Fluxbox may just be the easiest window manager there is to use.  I've tried literally at least a dozen different ones, and generally use IceWM, but Fluxbox has become my second-favorite.  Sometimes it depends on what I'll be doing for a while, which window manager I will choose to use. I'm glad that, thanks to Open Source, we have such a variety to choose from, and to suit all kinds of tastes.

And yes, the Slit can be very useful.  There are dozens of little apps you can put in there, conveniently out of the way till you want them.  You can find them all over the place--using Google is one way.

---

### Post by darkaudit on 2005-06-15
The new versions of Fluxbox don't need the .xsession file. There is now the file ~/.fluxbox/apps which will take care of that for you.

Here's part of mine. It makes GTK apps look right, 2 aterms and gdesklets.

[startup] {gnome-settings-daemon &}
[startup] {aterm}
[startup] {aterm}
[startup] {gdesklets start}

You can also use the apps file to set apps to open in certain desktops and certain positions. Like this for Firefox:

[app] (Gecko)
  [Workspace]   {1}
  [Position]    {0 0}
[end]

(I know it says Gecko, but it works for firefox.) :)

---

### Post by jonrkc on 2005-06-15
[QUOTE=darkaudit]
You can also use the apps file to set apps to open in certain desktops and certain positions. Like this for Firefox:

[app] (Gecko)
  [Workspace]   {1}
  [Position]    {0 0}
[end]

(I know it says Gecko, but it works for firefox.) :)[/QUOTE]
And if you need to find out what name to use for this purpose, issue "xprop" on a command line and it will tell you to place the "+" cursor in the window you want information about.  Look for the line that says "WM_CLASS(STRING)" and use the first word in quotes after that
(try it on a Firefox window and you'll see "Gecko" there).  Many programs have window class names that you can only easily find out this way.

---

### Post by mattack on 2005-06-15
Wow..  forget the ~/.xsessions file.
My ~/.fluxbox/apps file is as follows:

```
[startup] {gnome-settings-daemon}
[startup] {gnome-volume-manager}
[startup] {/usr/bin/gkrellm -w &}
[startup] {/usr/bin/fbpager -w &}
```

and everything works just the way I want it to. Sweet!
Even hotkey I set up in Gnome to lock the screen. This is nice.

Now if I could get my second question answered from way back at the beginning of the thread...

What's up with the system tray? Why does it only hold one icon? How can I get it to expand when neeeded to hold more than one icon?

---

