---
title: "HOWTO: Set Custom GTK theme for specific applications"
date: 2009-11-29
forum: Desktop Environments
---

### Post by X1R1 on 2009-11-29
If you are like me, you like to mess around with your system a lot a try new stuff. One of the things I hate is when I found a pretty good theme but then I open up and application and I dont like the colors used in that specific application, but everything else is fine so I want to change just that application look and feel.

I will do this with pidgin but you can use it with any GTK application.

First, get the theme you would like to install into your custom app and install it normally (system wide).

Left click the desktop and choose change desktop background, from there you can install a theme you have already downloaded or search for a theme you like.

I will asume you already have the theme installed, if you dont know how to do it just post here and I will add it to this howto.

All your installed GTK themes are on > /usr/share/themes/
so you need to choose one theme from here first (remember the folder name you would need it).

After that you need to edit the application launcher to set the specific theme, all the launchers are stored in > /usr/share/applications/

So, lets say you want to skin pidgin with a theme called "Clearlooks-DarkLime" then go and edit:

```
sudo gedit /usr/share/applications/pidgin.desktop
```

and on the Exec line paste the following:

```
bash -c 'GTK2_RC_FILES=/usr/share/themes/Clearlooks-DarkLime/gtk-2.0/gtkrc pidgin'
```

Save and close the file. Then go ahead and open your application, you will notice that its looks completely different from the system theme.

I used pidgin here as an example cause people tend to like to skin messengers, so I figured this would help.

But you can do this with any GTK application you want, you just need to edit the launcher.

And that wraps it up, if you need help just post here I will be around :popcorn:

Hope it helps!!!

Special thanks to reed9 for helpin me.

---

### Post by jrdnyquist on 2010-05-20
I can't seem to make this work for pidgin in Lucid. Is there anything else I could be missing? Even with the launcher modified pidgin seems to ignore any theme I try to force on it this way.

---

### Post by X1R1 on 2010-05-23
same happened to me, you have to carefully check syntax of the exec or it wont launch.

Try just pasting the line you want to add to the launcher in a terminal to see if pidgin opens up with your desired theme, eg:

> GTK2_RC_FILES=/usr/share/themes/Clearlooks-DarkLime/gtk-2.0/gtkrc pidgin

Will open up pidgin with the Clearlook-Darklime theme.

Try it out and let me know.

PS:Sorry for the delay in the response...hope you still need it.

---

### Post by jrdnyquist on 2010-05-24
I'm certain the syntax is correct. I also tried pasting your suggestion but Pidgin's GTK theme never changes from the default GTK theme for some odd reason. Still stumped.

---

### Post by Xavier Oddmon on 2010-08-31
I can't seem to get this to work completely. What i'm trying to do is change the size of the scrollbars in apps I intend to use a tablet for (specifically xournal.) What's bothering me is that I can change the theme this way, the colors and whatnot change, but the scrollbars remain the same size... I've got two gtkrc files which are almost identical except that one contains ```

	GtkRange::slider-width = 12
	GtkRange::stepper-size = 12
``` while another contains ```

	GtkRange::slider-width = 36
	GtkRange::stepper-size = 24
```
Changing the colors and other appearance options confirm that it is loading a different gtkrc file, but the scroll bars remain the same size. If I manually change theme, the scroll bars do increase in size...

---

### Post by mikerobinson on 2012-10-15
Sorry for resurrecting an old thread, but this no longer works in Kubuntu 12.04:

```
GTK2_RC_FILES=/usr/share/themes/Clearlooks-DarkLime/gtk-2.0/gtkrc program-name
```

Is there any other way to execute a program and choose a different GTK theme? I want to use Clearlooks for all by default and one specific program I want to use oxygen-gtk.

---

### Post by vasa1 on 2012-10-15
@mikerobinson,
The forum has a policy on old threads. I suspect that this one will be closed. Please open a new thread for your issue. I'm also interested in a solution.

---

### Post by Toz on 2012-10-16
And on that note, closing.

As vasa1 says, please create a new thread so that it contains more recent information.

---

