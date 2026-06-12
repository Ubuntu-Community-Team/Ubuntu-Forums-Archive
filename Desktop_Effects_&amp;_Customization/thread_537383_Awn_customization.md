---
title: "Awn customization"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by i-am-me on 2007-08-28
I have three things:

1. How do I make the Awn Main Menu use a KDE style menu instead of a gnome style menu?

2. How do I rename a stack? I want to make more than one, but they all have the same name.

3. Is there a way to download an icon theme for Awn that includes programs, stacks, and widgets? or do I have to do it myself (If I do, how do I do it for stacks?)? or is it part of the overall themes?

---

### Post by isaacj87 on 2007-08-28
> **i-am-me said:**
> I have three things:

1. How do I make the Awn Main Menu use a KDE style menu instead of a gnome style menu?

2. How do I rename a stack? I want to make more than one, but they all have the same name.

3. Is there a way to download an icon theme for Awn that includes programs, stacks, and widgets? or do I have to do it myself (If I do, how do I do it for stacks?)? or is it part of the overall themes?

1. As far as I know, there's only a gnome style menu so far. I don't think there is anyone developing one for KDE.

2. I'm not sure what you're talking about because stacks get it's name from the folder assigned to it. For example if the folder is "Stacks" located in /home/yourname/Stacks, then the title above the stacks applet will display:
"/home/yourname/Stacks" and inside the actual dialog, it will display "Stacks"

What I do, because I have multiple stacks on my dock, is use a folder called "Pictures" for my pictures stacks and use a folder name "Music" for my music.

3. AWN gets the icon theme from the one that is being currently used. If you using the Human theme ,which uses the Human theme icon set, then AWN will display the Human theme icon set. I created my own stacks icon to use when the composite is unavailable. So, if you want to achieve a certain look, it might require some extra time.

---

### Post by i-am-me on 2007-08-29
By icon theme I'm guessing it doesn't detect KDE icon themes....

I've also discovered that Open filemanager doesn't work. I'm guessing this is also because of the GNOME and KDE thing. Any way to set it to use Konqueror?

The stacks problem is okay now. It just needed a restart.

---

### Post by isaacj87 on 2007-08-29
> **i-am-me said:**
> By icon theme I'm guessing it doesn't detect KDE icon themes....

I've also discovered that Open filemanager doesn't work. I'm guessing this is also because of the GNOME and KDE thing. Any way to set it to use Konqueror?

The stacks problem is okay now. It just needed a restart.

You know that's an interesting question. Because, even on the AWN forum site, I don't think anyone's ever mentioned any theme related problems with KDE. But then again, I wasn't really looking! What icon theme is it currently using for you? The default I'm assuming?

 I'm guessing stacks is probably geared towards GNOME users. You might want to ask the developer over at the AWN forum. His name is Timon.

[AWN Forum]("http://www.planetblur.org/hosted/awnforum/index.php")

In any case, this is the best place to get up-to-date info on AWN, its applets and the like. The devs are usually on and can provide direct assistance and if enough people want something, they'll code it in! It's really cool.

---

### Post by jsully1 on 2007-08-29
Adding to this, is there any way to customize the speed of the animations?  It seems fairly slow on my laptop.

---

### Post by isaacj87 on 2007-08-29
> **jsully1 said:**
> Adding to this, is there any way to customize the speed of the animations?  It seems fairly slow on my laptop.

Never tried it, but there seems to be a setting for the auto_hide_delay (its default is 1000). 
Open up gconf and go to apps->avant-window-navigator

In the right panel there is the setting "auto_hide_delay." Play around with it and see if that helps.

If you don't know how to open gconf, do this:

press alt+f2
type in: gconf-editor

---

### Post by jsully1 on 2007-08-29
I'm looking to set the actual length of time that it takes for the hide animation to complete.

---

### Post by wireddad on 2007-08-29
Can y'all post some pictures of your awn?  I would like to see what I "could" do with this program.

---

### Post by isaacj87 on 2007-08-29
Sorry...had to remove my pics...I'm clearing stuff out of my flickr.com account.

---

### Post by Inxsible on 2007-08-29
Don't mean to hijack the thread, but since its on the same topic.

How does AWN compare to KibaDock? I find Kiba to be extremely slow, partly because of the Akamaru physics engine. How responsive is AWN ?

Also, Kiba sucks when it comes to maintaining a separation between launchers and window list. Weird things happen. The launcher and the open window will have the same icon and move around, making it harder to recognize which is the open window and which is the launcher. I end up opening multiple instances of Firefox or any other app, like that. I am ready to get rid of Kiba already. :(

---

### Post by isaacj87 on 2007-08-29
> **jsully1 said:**
> I'm looking to set the actual length of time that it takes for the hide animation to complete.

Ah, I see..I'm afraid not at this point. There was a patch that could be applied that eliminates the autohide animation completely...but it's outdated and is no longer functional. You might want to suggest your idea  at the AWN launchpad site.

---

### Post by Inxsible on 2007-08-29
Oh and Isaac, can I get a copy of your wallpaper in 1400x900 or bigger if you have one. It would go nicely with my theme :)

---

### Post by isaacj87 on 2007-08-29
> **Inxsible said:**
> Don't mean to hijack the thread, but since its on the same topic.

How does AWN compare to KibaDock? I find Kiba to be extremely slow, partly because of the Akamaru physics engine. How responsive is AWN ?

Also, Kiba sucks when it comes to maintaining a separation between launchers and window list. Weird things happen. The launcher and the open window will have the same icon and move around, making it harder to recognize which is the open window and which is the launcher. I end up opening multiple instances of Firefox or any other app, like that. I am ready to get rid of Kiba already. :(

AWN is soooo much better than kiba. Kiba-dock is CPU hungry as well has a complete memory hog. AWN looks great, has a lively development team that is constantly working on it (i.e. improving it). AWN, on my laptop, uses only 3.5 megs of ram!! And while you hover over the dock, it uses about 20% CPU. Which is phenomenal. What about in terms of look? I'll admit kiba is better looking in some ways, but AWN isn't by any means ugly (the reflections are great). AWN as a task manager is much better as well, and compiz fusion window previews work with it as well.

---

### Post by isaacj87 on 2007-08-29
No I personally don't...sorry! I've only got a 1280x800.

This guy has it but I'm not sure if it's a widescreen or not...If it is you could easily GIMP it down to 1440x900

[Leopard Wallpaper]("http://www.flickr.com/photos/dominoes/544155098")

---

### Post by Inxsible on 2007-08-29
> **isaacj87 said:**
> No I personally don't...sorry! I've only got a 1280x800.

This guy has it but I'm not sure if it's a widescreen or not...If it is you could easily GIMP it down to 1440x900

[Leopard Wallpaper]("http://www.flickr.com/photos/dominoes/544155098")

Sweet !!! thanks a bunch. I shall use the original size of 2560x1600. I have a lot of space on my hard drive ;)

---

### Post by isaacj87 on 2007-08-29
About your Kiba-Dock troubles...just get rid of it. It's really not it's cracked up to be. Even with it's akamaru physics engine, AWN's up and coming libawn-effects development has simpler but just as nice effects.

---

### Post by jsully1 on 2007-08-30
AWN is significantly more usable, and had defined separation points for launchers, open apps, and widgets.
Screenshots:
[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=18&page=1](http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=18&page=1)

---

### Post by i-am-me on 2007-08-30
> **Inxsible said:**
> Don't mean to hijack the thread, but since its on the same topic.

How does AWN compare to KibaDock? I find Kiba to be extremely slow, partly because of the Akamaru physics engine. How responsive is AWN ?

Also, Kiba sucks when it comes to maintaining a separation between launchers and window list. Weird things happen. The launcher and the open window will have the same icon and move around, making it harder to recognize which is the open window and which is the launcher. I end up opening multiple instances of Firefox or any other app, like that. I am ready to get rid of Kiba already. :(

Well, I can't really tell the difference between awn and kiba, but they're both pretty responsive on my sytem. But looking at ksysguard, awn tends to stay somewhere around the middle with CPU usage while kiba goes from top to bottom and back to the top (still doesn't use much, im just not really running much right now. And I do prefer awn for normal use. Kiba is just for fun.

---

### Post by [Alsharifi] on 2007-09-01
X2 AWN > Kiba.....kiba is a pain in the ***.


quick question,how can i get a ubuntu main menu launcher on the dock,i dunno the command
also other system stuff like volume and stuff like that

---

### Post by Inxsible on 2007-09-01
> **'[Alsharifi] said:**
> X2 AWN > Kiba.....kiba is a pain in the ***.


quick question,how can i get a ubuntu main menu launcher on the dock,i dunno the command
also other system stuff like volume and stuff like that
The command for ubuntu mainmenu is ```
alacarte
```

---

### Post by i-am-me on 2007-09-01
> **'[Alsharifi] said:**
> X2 AWN > Kiba.....kiba is a pain in the ***.


quick question,how can i get a ubuntu main menu launcher on the dock,i dunno the command
also other system stuff like volume and stuff like that
I dont know about "other system stuff", but you can get the Main Menu as a widget in awn bzr and enable from the prefs.

---

### Post by phoochka on 2007-09-01
Another thread hijack! o-0

I´m not a big fan of the mac setup and was wondering if there was a way to set AWN on TOP of the desktop rather than on the bottom where I keep my Gnome pannel?
I´ll probably switch to kiba anyways, but was just wondering.

---

### Post by coldstatue on 2007-09-02
> **i-am-me said:**
> I dont know about "other system stuff", but you can get the Main Menu as a widget in awn bzr and enable from the prefs.

I recently wiped all traces of awn from my feisty box. (I think)... I uninstalled, then searched and deleted any remaining files/folders. Even if I compile, I have no stacks, clock, or menu option in the prefs, even thoguh I have the new prefs, where just the first section contains everything from the old prefs. My AWN folder even contains a subfolder named, "clock". No new gconf options are available. I can't even get the white line. \ I tried a tutorial by reacocard on another site, which I cannot find now, regarding the compiling of the bzr with no patches. I also downloaded some debs of reacocard's, and went the automatic rout from the repos. No luck. Are we supposed to have stacks if we install from the repos/tutorial on the main AWN thread now? I can see the tutorial was edited for bzr, rather than svn.

Any suggestions? The AWN thread is so long, I admit I skipped some pages in my search. I'm not sure where to ask this.

Thanks for any help.

P.S. - In trying a few things to see if I had stacks available, (and without knowing how the backend folder works) i dragged a folder onto AWN, and now have a desktop icon with "none" for the name that cannot be removed. This happened on an earlier version, but I can't remember how to get rid of it. I tried in the prefs.
Thanks

---

### Post by isaacj87 on 2007-09-02
> **coldstatue said:**
> 
P.S. - In trying a few things to see if I had stacks available, (and without knowing how the backend folder works) i dragged a folder onto AWN, and now have a desktop icon with "none" for the name that cannot be removed. This happened on an earlier version, but I can't remember how to get rid of it. I tried in the prefs.
Thanks

Well, stacks is defaulted to linking items. So create another folder on the desktop called "none" and deleted both. It can't be deleted because it's looking for the original it links to.

After I get something done  I'll try and help you get AWN+Stacks running. :)

---

### Post by coldstatue on 2007-09-03
Got the bad launcher, but I had to do it through gconf-editor, which does have some new number entries under the applets folder, but nothing I can find relating to stacks, the clock, or gnome menu. I didn't used to be able to get rid of launchers in there (I don't think), so I have changed something successfully.

Thank you

---

### Post by i-am-me on 2007-09-05
Hmm, well, instead of compiling try installing it from its repos. They are:

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

then install avant-window-navigator-bzr

---

### Post by coldstatue on 2007-09-06
Well, that did something, but not all good. I got rid of the old install completely - removed all traces. (I think) .. I already had those repos, but deleted them and used your links to be sure they were exact. I installed, and wound up with a new bar. There is a launcher section, a separator, and then 4 white lines, all divided by separators. I restarted, as I have read about the white line problem. Unfortunately, my prefs no longer work. Whether I go System>Preferences>AWN-Manager, or right-click on the bar, I cannot bring up the prefs. The white lines remain.

After all I've done, it's hard to remember, but I think this is why I compiled from source. Guess I'll go back to that, because I no longer have a desktop switcher, which I use quite a bit.

If you can think of any other possible sources of this problem, please let me know. Otherwise, I guess I'll wait for the next version to come out.

Thanks for your time.

---

### Post by Inxsible on 2007-09-06
> **coldstatue said:**
> Well, that did something, but not all good. I got rid of the old install completely - removed all traces. (I think) .. I already had those repos, but deleted them and used your links to be sure they were exact. I installed, and wound up with a new bar. There is a launcher section, a separator, and then 4 white lines, all divided by separators. I restarted, as I have read about the white line problem. Unfortunately, my prefs no longer work. Whether I go System>Preferences>AWN-Manager, or right-click on the bar, I cannot bring up the prefs. The white lines remain.

After all I've done, it's hard to remember, but I think this is why I compiled from source. Guess I'll go back to that, because I no longer have a desktop switcher, which I use quite a bit.

If you can think of any other possible sources of this problem, please let me know. Otherwise, I guess I'll wait for the next version to come out.

Thanks for your time.
you must have created a launcher without an icon. There is a bug wherein if you do that, you can no longer pull up the Awn Manager. Go to your home folder and then remove the launchers that you created from /home/user/.awn/launchers (i think)

---

### Post by svtfmook on 2007-09-06
is there a way to use just the launcher portion and not the window list?

---

### Post by Inxsible on 2007-09-06
> **svtfmook said:**
> is there a way to use just the launcher portion and not the window list?

I don't think so. The applet that you add adds a Launcher/Task Manager both :(

---

### Post by coldstatue on 2007-09-06
The bad launcher was not the culprit. Turns out you must delete usr/local/bin/awn-manager before installing a new version. Works great, though I didn't have stacks, notification area (though added as an applet) or a clock. EDIT: UNTIL i installed awn-core-applets-bzr (I think it's called) I did a search for awn and avant in synaptic. All is well except a clock that is invisible unless I hover over it, and a grey line for a notification area. Still, it's progress! Stacks is working. Thank you

---

### Post by seamus7 on 2007-10-27
Many Avant Window Navigator themes can be found at....
[http://www.queervisions.com/arch/2007/10/awn_avantwindow.html](http://www.queervisions.com/arch/2007/10/awn_avantwindow.html)

---

