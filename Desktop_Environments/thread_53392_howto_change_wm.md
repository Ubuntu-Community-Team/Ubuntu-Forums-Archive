---
title: "howto change wm"
date: 2005-07-31
forum: Desktop Environments
---

### Post by Lambert on 2005-07-31
I'm running hoary 5.0.4. I wanted to try a few different window managers but searching google and this forum has given me very little. I tried a CLI "killall metacity && sleep 1 && [wm]" but that did nothing. I found in configuration editor (desktop>gnome>applications>window manager but couldn't find a way to edit these. 

 Could you point me towards a howto or give some decent instructions on how to change the default windows manager so I can try others?

---

### Post by Lord Illidan on 2005-07-31
You could install kubuntu-deskop via Synaptic to get KDE!

---

### Post by varunus on 2005-07-31
Some window managers can be started from the CLI with "wmname --replace" to remove metacity.  You should also be able to edit the gconf key you were talking about to point at a different window manager.  That should let you set your WM...

Another, much less cleaner way, if the above doesn't work, would be to rename the original metacity file in /usr/bin and make a new symbolic link to another window manager:

sudo mv /usr/bin/metacity /usr/bin/metacity_old
sudo ln -s /usr/bin/new_wm_name /usr/bin/metacity

Then log out and back in.

I'm sure there's a better way though...

---

### Post by miscz on 2005-07-31
You should be able to select other window managers by selecting them in GDM. If you want to add some gnomeness to them run gnome-settings-deamon, gnome-panel etc. It would be more helpful if you told us what window managers you want to run because not all of them work well with Gnome (desktop switching is often an issue).

---

### Post by Lambert on 2005-07-31
currently I want to try enlightenment. When downloading via synaptic the description said something along the lines of easily integrating with gnome desktop.

---

### Post by ghostintheshell on 2005-07-31
yes, me too. I would like to easily try enlightment but when installing the requiered packages nothing new appears in the GDM menu (only Gnome).

any idea to add this WM in the gdm menu?

tx.

---

### Post by ghostintheshell on 2005-07-31
[QUOTE=ghostintheshell]yes, me too. I would like to easily try enlightment but when installing the requiered packages nothing new appears in the GDM menu (only Gnome).

any idea to add this WM in the gdm menu?

tx.[/QUOTE]

Ok, I'm under Enlightenment.

      To add the Enlightenment entry in GDM:  

Create the file* /usr/share/xsessions/enlightenment.desktop* and paste these lines in this file:   

```

[Desktop Entry] 
Encoding=UTF-8 
Name=E17 
Exec=/usr/bin/enlightenment 
Icon= 
Type=Application

``` 

Log out. Enlightenment should be available in GDM ;)

---

### Post by Lambert on 2005-08-01
That gave me the option to choose enlightenment on login but not what I'm looking for. I want to use the gnome desktop with enlightenment as the window manager, (plus try others such as icewm).

Someone can correct me if I'm wrong but my understanding is we can use the gnome desktop with other window managers. Currently metacity is default (it used to be sawfish before that). I want to use gnome desktop and change the window manager from metacity to something else. Can this be done and how?

---

### Post by Lambert on 2005-08-02
I figured out what I was trying to do. 

Open system>preferences>sessions

Go to the current sessions tab and find metacity in the list. 

Highlight it and click remove (notice the order value though before doing this). This shuts down the window manager so you won't have title bars on your window or control over your windows.

Go to the tab - Startup Programs and add enlightenment with the same order value as metacity had. Mine was 20

Open a termianl and type <sudo enlightenment --replace> [you can use any WM in place of  enlightenment that you have installed-openbox, icewm...]

This will start the windowmanager you picked. 

Now, if I'm wrong on the next part somebody please correct me. On the tab session options, if you leave the auto save change to session un checked, when you log back in it will revert back to metacity , if you check this then next time you log in it should keep enlightenment as the default WM.

---

