---
title: "Weird Gnome Problem"
date: 2007-01-26
forum: Desktop Environments
---

### Post by suziequzie on 2007-01-26
I have a weird Gnome problem. I am currently running Kubuntu 6.06. I tried installing ubunutu-dekstop so I can play around with Gnome, see how I like it, and compare the two. 

I can't log into Gnome. If I try, I get a black screen with white empty panels top and bottom. All I can do is press CTRL-ALT-BACKSPACE to return to the kdm manager.

Now, the weird part: My boyfriend's account can log into it no problem. If I log in under his name (I'm the tech support, so I know his password, etc), Gnome will load with no problems. 

I really don't want to have to try a second user account for myself to get Gnome running, but if I have to I will. Any suggestions? Has anyone noticed anything like this before? 

(ps, I chose KDM when asked which option cuz I really like my KDM themes... but if I need to re-install and choose GDM then I will.)

---

### Post by sloggerkhan on 2007-01-26
There's probably something in you one of the hidden files on your home folder that gnome really doesn't like.

---

### Post by suziequzie on 2007-01-26
Well, right now I am writing this response in gnome in my boyfriend's account, just giving it a look-see. I'll have to remember to make sure it loads kde for him when he gets home.  He doesn't handle change all that well... I'm just happy he is using linux...

---

### Post by ComplexNumber on 2007-01-26
yeah, i think its to do with the config files too. if you login **using kde **and delete the following (hidden) directories then logout and login immediately, it should recreate them:
.gconf
.gconfd
.gnome2
.nautilus

you see. kde is a monster...and it tries to ruthlessly take over the desktop, killing and corrupting everything belonging to anything non-kde. its part of the 'do everything the kde way rather than the freedesktop.org way' doctrine of kde :p. thats been my experience anyway.

---

### Post by suziequzie on 2007-01-26
> **ComplexNumber said:**
> yeah, i think its to do with the config files too. if you login **using kde **and delete the following (hidden) directories then logout and login immediately, it should recreate them:
.gconf
.gconfd
.gnome2
.nautilus

you see. kde is a monster...and it tries to ruthlessly take over the desktop, killing and corrupting everything belonging to anything non-kde. its part of the 'do everything the kde way rather than the freedesktop.org way' doctrine of kde :p. thats been my experience anyway.

Thanks. I'll give it a try and see how it works.

---

### Post by suziequzie on 2007-01-26
[B]VICTORY!!!!!

[/B]Thank you! That worked!  I'm now in Gnome!  Now, to tweak the preferences to my liking...

(had to run kdesu konqueror to delete the directories... I guess there were some root-protected files in there)

---

### Post by ComplexNumber on 2007-01-26
> **suziequzie said:**
> [B]VICTORY!!!!!

[/B]Thank you! That worked!  I'm now in Gnome!  Now, to tweak the preferences to my liking...

(had to run kdesu konqueror to delete the directories... I guess there were some root-protected files in there)
glad it worked.

btw for more detailed tweaking of your preferences if you can't find it mentioned in the application that you're trying to tweak, use a program called gconf-editor. you should find it in system tools in the menu. if its not there, just run 'gconf-editor' in the terminal. you'll find it a very useful tool now and again.

---

### Post by sloggerkhan on 2007-01-26
I'd also say add for fun the following:
Gnome Art Manager (in repos)
and
Gnome Color Chooser
[http://ubuntuforums.org/showthread.php?t=293342](http://ubuntuforums.org/showthread.php?t=293342)

---

### Post by suziequzie on 2007-01-26
Thanks for the tips and link to tweaking my desktop. One of the things that excited me about the prospect of linux was changing the way the desktop looks in more robust ways than windows could do. 

Whereas my boyfriend is happy to just slap his favorite wallpaper on and leave the defaults...

---

### Post by ComplexNumber on 2007-01-26
> **suziequzie said:**
> Thanks for the tips and link to tweaking my desktop. One of the things that excited me about the prospect of linux was changing the way the desktop looks in more robust ways than windows could do. 

Whereas my boyfriend is happy to just slap his favorite wallpaper on and leave the defaults...
thats part of the reason why i like gnome - its so incredibly easy to theme. 
i recommend that you head straight to gnome-look.org and grab yourself a few themes and icon sets. you can either install them systemwide in /usr/share/themes(for themes) and /usr/share/icons(for icons), or you can install them in the .themes and .icons directories in your home directory.
i also recommend gnome-color-chooser, as recommended above.

---

### Post by suziequzie on 2007-01-26
I've got [IMG]http://www.gnome-look.org/content/m1/m52195-1.png[/IMG] for a background...  [http://www.gnome-look.org/content/show.php?content=52195](http://www.gnome-look.org/content/show.php?content=52195)

Very easy on the eyes. 

Also downloaded the sky metacity theme from there... [http://www.gnome-look.org/content/show.php?content=36860](http://www.gnome-look.org/content/show.php?content=36860) and have blue loaded up. 

How do you change how the panels look?  I like the way they loook in the sky theme's preview.

---

### Post by suziequzie on 2007-01-26
Oooohhhh.... installed gdesklets...  Love 'em. Got calendar running with artwork for various months installed from the repos...

---

### Post by ComplexNumber on 2007-01-26
for the panel to use the settings in the theme, right click on the panel, select 'properties' then 'background' tab, then select 'use system theme'.

make sure that you have the appropriate gtk2 theming engines installed. fire up synaptic, then do a search on Name only for "engine". you will see a lot of them, but most of the gtk2 engines are installed in the gtk-engines package anyway. however, not all of them are, though. install any gtk**2**(ignore the gtk ones) engines that are not in the following list:

[I]* Clearlooks, the default GNOME theme, based on Bluecurve;
 * Crux, formerly known as the Eazel engine;
 * High contrast, which is used by some accessibility themes;
 * Industrial, the famous engine from Novell (formerly Ximian);
 * LighthouseBlue, another engine based on Bluecurve;
 * Metal, which gives a metallic look;
 * Mist, a flat and high performance engine;
 * Redmond95, which provides a look similar to that of Windows;
 * Smooth, which is used by many themes as being nice, fast and
   configurable;
 * ThinIce.
[/I]

this ensures that all themes will look as they should do. you will defintely need to install gtk2-engines-pixbuf.

now put "theme" in the synaptic search engine. you will see lots of gnome-icon themes and various gtk2 themes to install.

i think the human and clearlooks themes are rather nice. mist themes look awful, rezlooks doesn't look that good either (IMO). candido themes are nice.
although there aren't any in the repos, my favourites are perhaps murrine using the murrine theme engine. they're the most tweakable too (if you download and install [this]("http://gnome-look.org/content/show.php?content=45917") from source, you can configure your installed murrine themes however you want). you can get the murrine themes from gnome-look.org.  oh, you have to have the murrine engine installed - get it from [here]("http://gnome-look.org/content/show.php?content=42755").

---

### Post by suziequzie on 2007-01-26
Right now I'm running gnome art manager.  Sweet.  So far, I do like gnome.  

And I still like KDE too...

"I love them both for different reasons..."

---

### Post by sloggerkhan on 2007-01-28
Gnome has stuff to love. Never really been big on the gdesklet thing, though.

---

