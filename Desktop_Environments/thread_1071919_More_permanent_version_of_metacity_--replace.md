---
title: "More permanent version of metacity --replace"
date: 2009-02-16
forum: Desktop Environments
---

### Post by xonpathos on 2009-02-16
Ok, so I don't like Compiz.  It's pretty and all, but it causes way more problems than I'm willing to put up with.

I do like Metacity.  One "metacity --replace" fixes all the annoying problems I have with Compiz.  The only problem is I have to do it every time I restart.

I've seen a zillion things to make this happen:  

go to System -> Preferences -> Appearance -> Visual Effects and choose none; 

gconf-config and make the desktop -> applications -> window_manager and set the default to /usr/bin/metacity; 

set the WINDOW_MANAGER environment variable to /usr/bin/metacity; 

add "metacity --replace" to .gnomerc

I've tried all of these things, one at a time and all together.  None of them work.  Most of them don't seem to do anything, and the last one makes it so that Gnome never comes up.

So, my question:  How can I give Compiz the boot and get Metacity to stick around permanently?

---

### Post by abn91c on 2009-02-16
you can always do ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

---

### Post by UbuntuNerd on 2009-02-16
you can go to synaptic package manager and search for "fusion icon" installed it, and you should be able to switch between compiz and metacity with one click.
if you really want to uninstall compiz just look for it in synaptic and mark it for removal you also have to uninstall "compiz settings manager, compiz core".

---

### Post by xonpathos on 2009-02-18
> **abn91c said:**
> you can always do ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
```

I've been afraid to do that... I've heard horror stories of it going very badly.

> **UbuntuNerd said:**
> you can go to synaptic package manager and search for "fusion icon" installed it, and you should be able to switch between compiz and metacity with one click.

I downloaded this and am using it.  It's strange that it doesn't load the icon automatically when I start the computer, but since I've installed this Metacity starts up by default instead of Compiz.  Not sure that was the intended behavior of the app, but it got me what I wanted, so I'll take it.  :)

---

### Post by UbuntuNerd on 2009-02-18
to add it to the start up just hit "alt + F2" and type this

```
ln -s /usr/bin/fusion-icon /home/YOUR_USERNAME_HERE/.config/autostart/fusion-icon/fusion-icon
```
replace "your user name" with your own, you can also launch "fusion Icon" from Applications > System tools > Fusion Icon
then you should see the icon on the top right corner of your screen.

---

### Post by xonpathos on 2009-02-20
Is it just me, or is it particularly difficult to tell when one window manager is running vs the other?  It's really annoying.

It seems the icon was *saying* that Metacity was running, but it was mistaken.  If I tell it to run Metacity, the screen flickers and then Metacity is (presumably) actually running.

I'd still be curious to know how to have Metacity and Compiz on the same machine but use Metacity as the default.

---

### Post by Armor Nick on 2009-02-21
Maybe adding metacity --replace to your autostart menu (under preferences->sessions) will help.

---

### Post by adult swim on 2009-02-21
have you tried pressing alt+f2 entering in ```
gconf-editor
``` and then browsing to desktop>gnome>applications>window_manager and changing the default from /usr/bin/compiz to /usr/bin/metacity
EDIT: somehow i missed where you explicitly stated you have tried this in your OP, sorry about that!

---

### Post by theozzlives on 2009-02-21
do they have a metacity settings manager?

---

### Post by mcduck on 2009-02-21
> **theozzlives said:**
> do they have a metacity settings manager?

Nope, most of it's settings are handled in another parts of Gnome (for example number of desktops is set in the Workspace Switcher-applet although it's actually Metacity's setting, keyboard shortcuts are set in System/Preferences/Keyboard Shortcuts and so on).

For the few extra settings that are not available in menus you'll just have to use gconf-editor.

---

### Post by theozzlives on 2009-02-21
> **mcduck said:**
> Nope, most of it's settings are handled in another parts of Gnome (for example number of desktops is set in the Workspace Switcher-applet although it's actually Metacity's setting, keyboard shortcuts are set in System/Preferences/Keyboard Shortcuts and so on).

For the few extra settings that are not available in menus you'll just have to use gconf-editor.

so no fancy effects, bummer.

---

### Post by islandis on 2010-02-26
I realize this message comes almost a year later to the day, BUT. I was just having a similar problem on Arch Linux, where I replaced metacity with compiz and then ended up in a World of Pain upon deciding to go back.

What worked for me was something I found in an Arch guide to getting Compiz to autoload on login.  The answer is in GConf, but NOT in changing the "/desktop/gnome/applications/window_manager/" settings back to metacity.  Apparently those fields ("current" and "default") have been deprecated in Gnome since 2.12 (that is--late 2005 or so).

The value you want to change in GConf is this one:

> /desktop/gnome/session/required_components/windowmanager compiz

Just change the "compiz" to "metacity" and you should be good to go!

---

### Post by drreed on 2010-04-20
> **xonpathos said:**
> I've been afraid to do that... I've heard horror stories of it going very badly.



I downloaded this and am using it.  It's strange that it doesn't load the icon automatically when I start the computer, but since I've installed this Metacity starts up by default instead of Compiz.  Not sure that was the intended behavior of the app, but it got me what I wanted, so I'll take it.  :)


The command you use to run your compiz after changes "compiz --replace" is the same command you have to run to get your Xfwm4 back (in Xubuntu) after you remove compiz, "xfwm4 --replace", otherwise, your windows won't be drawn completly. I added to some of those horror stories recently until I figured that out. Notice you see "metacity --replace" too. Whatever you used before you used compiz, you have to tell it to --replace to get it back after you remove the other (compiz) you'd been using.

I suspect I can now install/uninstall compiz with little concern, and can try it again with guidance from more experienced users. Just trying to get the cube thing going your first dance (like every other dweeb that installs it) may not be the best approach to evaluating compiz "smartly".  :)

Now I'm more receptive to trying alternate window managers and decorators. I wonder if you have to use Emerald, or whether you can use something else as a decorator? Being able to fix it when you break it is important for manglers like me.:guitar:

---

### Post by Hammerwell on 2010-04-27
> **islandis said:**
> I realize this message comes almost a year later to the day, BUT. I was just having a similar problem on Arch Linux, where I replaced metacity with compiz and then ended up in a World of Pain upon deciding to go back.

What worked for me was something I found in an Arch guide to getting Compiz to autoload on login.  The answer is in GConf, but NOT in changing the &quot;/desktop/gnome/applications/window_manager/&quot; settings back to metacity.  Apparently those fields (&quot;current&quot; and &quot;default&quot;) have been deprecated in Gnome since 2.12 (that is--late 2005 or so).

The value you want to change in GConf is this one:



Just change the &quot;compiz&quot; to &quot;metacity&quot; and you should be good to go!

Yea, this did the trick. Nearly everything is fine now. Now running: metacity. =D>

---

