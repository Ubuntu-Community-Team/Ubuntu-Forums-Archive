---
title: "Several issues on a new Jaunty PC"
date: 2009-07-11
forum: Desktop Environments
---

### Post by coverup1128 on 2009-07-11
I would very appreciate help with several annoying issues on a newly installed Jaunty PC:

1. How do I make apps open on a specific desktop? Eg, I would like FireFox to always open on Desktop 4. 

2. I want the application windows to get focus when they open. Also, I want new Windows to open on an active desktop (I don't mind them stealing focus). For instance, some of my Matlab programs take some time to produce a figure. I usually switch to a different desktop during such long sessions to check mail or read the news. What I want is to have Matlab running on Desktop 1, but have the figures open on Desktop 3, if I am reading mail on Desktop 3, or on desktop XYZ if I am doing something on that desktop. 

3. I would like to rename desktops to something more intelligent than Desk 1. I tried renaming them using the config window, but it seems that the new names do not stick, After reboot some of the new names are always lost.

4. The keyboard repeat and delay settings have to be re-set after every logout/restart. The settings in the System -> Preference -> Keyboard are fine, but the keyboard's response is slow, until I move the sliders in the keyboard a little, and put them back.

5. I like navigating through documents and websites by pressing and holding PageUP, PageDown and arrow keys - while the key is pressed, the keyboard keeps sending the keystrokes to the application, until the key is released. This works fine in FireFox but in Adobe Reader, no matter how long I hold PageDown, the page moves only once, and them nothing happens until the key is released and pressed again. This behavior is different from what I used to have on Ubuntu 8.04 PCs and on other Linux distros

Any help please?

---

### Post by coverup1128 on 2009-07-19
C'mon, nobody have any ideas?

---

### Post by nmaster on 2009-07-19
> **coverup1128 said:**
> I would very appreciate help with several annoying issues on a newly installed Jaunty PC:

1. How do I make apps open on a specific desktop? Eg, I would like FireFox to always open on Desktop 4. 

2. I want the application windows to get focus when they open. Also, I want new Windows to open on an active desktop (I don't mind them stealing focus). For instance, some of my Matlab programs take some time to produce a figure. I usually switch to a different desktop during such long sessions to check mail or read the news. What I want is to have Matlab running on Desktop 1, but have the figures open on Desktop 3, if I am reading mail on Desktop 3, or on desktop XYZ if I am doing something on that desktop. 

3. I would like to rename desktops to something more intelligent than Desk 1. I tried renaming them using the config window, but it seems that the new names do not stick, After reboot some of the new names are always lost.



I would also like to hear some suggestions regarding these questions.  #1 would be especially useful.

---

### Post by nmaster on 2009-07-22
really, no one??

---

### Post by jocheem67 on 2009-07-22
I can only suggest that you check out gconf-editor for these kind of settings..

Otherwise these might be gnome-related issues , more than specifically ubuntu's...

---

### Post by Dullstar on 2009-07-22
1.  If you want it to open on Desktop 4, switch to desktop 4, works for me.  Otherwise, try the forum search function or Google it.

2.  You lost me there.

3.  I think only KDE uses desktop names as far as I can tell.  I mainly use GNOME and I so far have not found anything that uses the names of desktops.

4.  Hmm...  [_This is the best I have to offer._](http://tinyurl.com/kv35eg)

5.  Adobe reader, in my opinion, isn't the best reader out there.  These days I rarely need PDF viewers, but there are options.  I don't know if this exists on Linux, but when I used to use Windows as my main operating system, I had Foxit Reader.  Try this: [_Google Search._](http://tinyurl.com/m3jaq9)

I hope this helps.

---

### Post by mister_p_1998 on 2009-07-22
Im sure they only open on the ACTIVE desktop, if I click on a shortcut on desktop one, then quickly flip to number two, it opens on two. You can move them to another after they've loaded by right button over the program on the taskbar and select move to workspace (right or whatever)

Steve

---

### Post by coverup1128 on 2009-07-24
> **mister_p_1998 said:**
> Im sure they only open on the ACTIVE desktop, if I click on a shortcut on desktop one, then quickly flip to number two, it opens on two. You can move them to another after they've loaded by right button over the program on the taskbar and select move to workspace (right or whatever)

Steve
You're right... 

Nonetheless quite often windows open so that they are covered by other windows. When I use matlab, this is especially annoying, since I may have a dozen of windows open (editors, figures, simulink, etc.). In KDE, clicking a scope brings it up right away. I find this a lot more convenient then watching which little button on the panel starts flashing.

---

### Post by wojox on 2009-07-24
```
sudo apt-get install compizconfig-settings-manager
```

1. Then, go to System->Preferences->Advanced Desktop Effects->Place Windows (it will be towards the bottom). In the Fixed Window tab, click new and for the text area type, "class=Firefox" and then select the viewport you want the app to appear on.

3. Right click Workspace switcher select Prefrences Change Names.

---

### Post by coverup1128 on 2009-07-25
> **wojox said:**
> ```
sudo apt-get install compizconfig-settings-manager
```

1. Then, go to System->Preferences->Advanced Desktop Effects->Place Windows (it will be towards the bottom). In the Fixed Window tab, click new and for the text area type, "class=Firefox" and then select the viewport you want the app to appear on.

3. Right click Workspace switcher select Prefrences Change Names.

Thank you for the tip regarding 1. Will this work even though I don't use compiz? I will give it a shot anyway. 

Regarding 3, I did try renaming desktops the way you suggested, but the new names don't stick and are lost on logout. Only the first one has kept the new name.

---

