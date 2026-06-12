---
title: "Changing Rhythmbox icons"
date: 2007-04-28
forum: Desktop Effects &amp; Customization
---

### Post by B. W. on 2007-04-28
**[center][Here's](http://ubuntuforums.org/showpost.php?p=2592429&postcount=28) the actual guide. Thanks gamma.[/center]**

Is there anyway to change all of the icons in the source pane of Rhythmbox (specifically to a Tango style theme)? I could change some of them if I replaced the images the program uses, but there are certain ones that couldn't be changed last time I tried.

Here's what I'm talking about:

---

### Post by kpolice on 2007-04-28
A piece of cake, put in your icon theme the following icons:

rhythmbox-podcast
stock_channel
stock_music-library
stock_playlist
stock_smart-playlist

The size that rhythbox use is 24x24px.

---

### Post by B. W. on 2007-04-30
> **kpolice said:**
> A piece of cake, put in your icon theme the following icons:

rhythmbox-podcast
stock_channel
stock_music-library
stock_playlist
stock_smart-playlist

The size that rhythbox use is 24x24px.
I tried putting them in "/usr/share/icons/Tango/24x24" and "/usr/share/icons/Tango/24x24/actions". It doesn't work.

I did a search for those names, which brings me to the the Rhythmbox and Gnome directories (which is what I replaced last time, but there was one icon that couldn't change).

---

### Post by kpolice on 2007-04-30
It should work, it's working for me in GNOME 2.18 + rhythmbox 0.10 in ArchLinux.

Maybe you have a cache for your icon theme?

---

### Post by B. W. on 2007-04-30
> **kpolice said:**
> It should work, it's working for me in GNOME 2.18 + rhythmbox 0.10 in ArchLinux.

Maybe you have a cache for your icon theme?
Using this command fixed it.
```
sudo gtk-update-icon-cache -f /usr/share/icons/Tango
```
Thanks!

Just for giggles, here's my icons if anyone's interested.

---

### Post by gamma on 2007-05-01
I grabbed the icons from [http://bugzilla.gnome.org/show_bug.cgi?id=380896](http://bugzilla.gnome.org/show_bug.cgi?id=380896) and threw them into a zip. Put the extracted actions/ folder in ~/.icons/gnome/24x24/ and enjoy. You may need to put them in the icon theme directory for your specific theme, so replace gnome with Tango if they don't show up under tango.

Thanks to B.W. for figuring out how these icons are named. :D

---

### Post by gamma on 2007-05-02
Shot of the icons from my last post.

---

### Post by Bou on 2007-05-02
Love this. What about the actual application icon, can it be changed?

---

### Post by Bou on 2007-05-02
By the way, gamma, I resized your icons because the looked somewhat blurry. Now they look OK.

---

### Post by Bou on 2007-05-02
Replaced the incorrect "radio" icon (which was "radio-new") and added 16x16 icons for the right-click menu and the notification area icon, as well as the application icon. But the right-click menu still uses the big ones, and the NA still uses the old one, and the application icon looks blurry.

---

### Post by gamma on 2007-05-02
> **Bou said:**
> Replaced the incorrect "radio" icon (which was "radio-new") and added 16x16 icons for the right-click menu and the notification area icon, as well as the application icon. But the right-click menu still uses the big ones, and the NA still uses the old one, and the application icon looks blurry.

Cool thanks! If you want to take a look at rhythmbox-tray-icon.png that'd be cool too. I'm not exactly sure what size it should be. It's currently using a 16x16 music note and scaling it up, but using the 16x16 or 24x24 icon looks blurry.

It appears 18x18 pixels is the size needed so that things don't appear blurry in the tray.

---

### Post by kpolice on 2007-05-02
Usually tray icons are 22x22

---

### Post by gamma on 2007-05-02
> **kpolice said:**
> Usually tray icons are 22x22

Yea that's what I though, but doing a 22x22 pixel icon for the tray is distorts the icon. I decided to make a 22x22 black box and it only showed up as 18x18, so that's how I got that number.

---

### Post by Cheizzz on 2007-05-02
This works great, thanks!
now, i would like to take it one step further, how would I change the ugly "repeat" and "random" buttons?

---

### Post by kpolice on 2007-05-02
stock_repeat and stock_shuffle

---

### Post by Bou on 2007-05-02
> **kpolice said:**
> stock_repeat and stock_shuffle

I borrowed some icons from [here]("http://www.taimila.com/orange-look.php") and now it looks much better.

Plus, I opened a Gutsy suggestion about the issue [here]("http://ubuntuforums.org/showthread.php?p=2579817#post2579817").

---

### Post by gamma on 2007-05-02
I was using the attached image as a tray icon. Looks nice and crisp here.

---

### Post by gamma on 2007-05-02
Rhythmbox looks very pretty for me now :D.

Thanks guys!

---

### Post by Fylk on 2007-05-02
Hey guys, I tried that and for some reason it didn't work.

---

### Post by gamma on 2007-05-02
> **Fylk said:**
> Hey guys, I tried that and for some reason it didn't work.

Where are you putting these files and what icon theme are you using?

---

### Post by Fylk on 2007-05-03
I tried them in both the Tango set and the Gnome set, changing the icons setting for me theme both time, restarting X both time.

---

### Post by kpolice on 2007-05-03
Probably you have a cache for your icons, delete it.

---

### Post by gamma on 2007-05-03
> **Fylk said:**
> I tried them in both the Tango set and the Gnome set, changing the icons setting for me theme both time, restarting X both time.

I'd recommend putting the icons in your /home directory in .icons, but you can update your cache for Tango by issuing this command as said on the first page.

```
sudo gtk-update-icon-cache -f /usr/share/icons/Tango
```

---

### Post by Morbett on 2007-05-04
Bou, I downloaded your latest gnome icon set for rhythmbox.  Where do I put them, in the generic .icons folder?

---

### Post by LuisGMarine on 2007-05-04
Do any of the contributors to this thread mind making a nice to follow HOWTO.  I'm just asking since some people might find it hard and annoying to read a whole thread on how to do such a thing.

Just write down a simple list of steps, and the proper materials to get this working.  Just a thought, and if there is one up already, link it so I can use it for future references to people that might need help changing such things.

Greatly appriciate your guys, work, hope to hear from you soon!

---

### Post by Bou on 2007-05-04
> **Morbett said:**
> Bou, I downloaded your latest gnome icon set for rhythmbox.  Where do I put them, in the generic .icons folder?

You have to put them in ~/.icons/gnome.

Here's a new package which includes a 32px app icon that looks good in the switcher, and gamma's tray icon.

---

### Post by Morbett on 2007-05-04
So I put the icons in home/.icons/gnome ?  Do I need to do anything else?  Thanks!

---

### Post by gamma on 2007-05-04
PLEASE DON'T QUOTE THIS GUIDE, IT MAY BE UPDATED AND MULTIPLE VERSIONS COULD CONFUSE USERS. :P

**ICON INSTALLATION HOWTO**
Most icon themes inherit the gnome icon theme, meaning they use it as a fallback. Some themes inherit the Tango theme, which in then inherits gnome, so any theme based off Tango or gnome should work correctly with this guide.

NOTE: If you see ''s in this guide, ignore them, they're there to make it easier to read. :D

1) Getting the icons
Find the attached latest archive of icons in this thread to the desktop. Right click on the package icon on this desktop, right click and select 'Extract Here'. You're now going to have a ARCHIVENAME_FILES folder on your desktop. We'll need that later.

2) Determine if you have a custom 'gnome' icon theme
Open a nautilus window, hit CTRL+L and put '~/.icons' into the location bar. This will show all your custom icon themes. If you don't see a 'gnome' folder in skip to step 4.

3) Drag and drop fun!
If the 'gnome' folder exists then you're going to have to open up the ARCHIVENAME_FILES folder and drag and drop the icons in the appropriate places in the 'gnome' folder. For example if you open our ARCHIVENAME_FILES folder you'll see 16x16, 22x22, 24x24, etc. In these there are directories like actions, apps. You need to move the icons in 16x16/actions to '~/.icons/gnome/16x16/actions'. 22x22/actions would go in '~/.icons/gnome/22x22/actions' and so forth.
Skip to step 5.

4) Rename the ARCHIVENAME_FILES folder
Get your ARCHIVENAME_FILES folder from your desktop and rename it to 'gnome' and then drag and drop it into the '~/.icons' folder.

5) Things should be up and running, open rhythmbox and you should see the new icons.


**TROUBLESHOOTING**
-I'm not seeing these icons
If the icons aren't appearing make sure you've followed the guide correctly. Then try to change to another icon theme and then change back to the new one and see if that fixes things. Some of the application icons may require you to log out and log back into gnome. If things still aren't working determine what icon theme you're using in theme preferences. Find the theme in '~/.icons' and simply follow step 3, but instead of moving icons to the 'gnome' folder move them to this custom theme's folder.

-How do I get rid of these icons?
You'll have to go to '~/.icons' and remove all the custom icons you created. So if you followed this guide, things will be in the '~/.icons/gnome' folder.

---

### Post by Morbett on 2007-05-04
Thanks.  Great icon sets and howto guide.

---

### Post by B. W. on 2007-05-04
gamma, I put a link to your guide in my original post You might want to post it in the tutorials forum.

---

### Post by LuisGMarine on 2007-05-05
Outstanding guide guys!

It worked like a charm for me, I couldn't of have asked this to become anymore easier!  The difference in having these custom icons, really does show!  

Great thanks to everyone who got the running, specially Bou and Gamma, great job guys!

---

### Post by LuisGMarine on 2007-05-08
Since I'm teaching myself how to script using bash, I thought this would be a neat first little script to start with.

Here is what I have so far, The comments should explain themselves

```

 #!/bin/bash


#checks if ~/.icons/gnome folder already exists

if [ -d $HOME/.icons/gnome ]

then

echo "gnome folder already exists, copying custom icons"

##after this part I"m not sure what to do since I'm starting, 
maybe someone with more experience can fill this section in. 
 What needs to happen in the lines above is obviously the 
'drag and drop fun' as you call it your tutorial.  Where all the 
icons are copied over to the ~/.icons/gnome folder



#if not then its going to create the folder

else 

echo "Creating folder, and installing custom icons" && mkdir $HOME/.icons/gnome && cd $HOME/.icons/gnome

#extract the proper files in there

tar xjf $HOME/Desktop/gnome.tar.bz2

fi
```

So far this works if I were to install these custom icons for the first time, trust me I used it myself.  So if you guys want to help me out that would be great, of course you can make things a lot better, but this is a first step.  I just thought it would be a neat program, specially for lazy people like me that would love to make anything a one click sort of deal.

The way this script works right now if you take the package from Bou in the most recent post named gnome.tar.bz2  and placing the script in the Desktop directory, just ot keep things simple

Hope to hear from you guys soon.

---

### Post by idn on 2007-05-15
Thanks for this, there is a thread on bugzilla about the ugly RB icons i was reading the other day, the icons in this thread (gnome.tar.bz) make RB look so much better. 

However the shuffle and repeat icons still look pretty ugly for me (I am using the snowish icon set). Is there someone more talented than myself who could possibly make some better icons for repeat and shuffle?

---

### Post by njee on 2007-05-26
there's some made by Lauri Taimilia in this thread:

[http://ubuntuforums.org/showthread.php?t=451095](http://ubuntuforums.org/showthread.php?t=451095)

---

### Post by pt123 on 2007-07-07
I have changed the default icons using some from Qwertys minimal theme
[http://www.gnome-look.org/content/show.php?content=61792](http://www.gnome-look.org/content/show.php?content=61792)

, and personally edited a few of them. 

Attached is a screenshot of how the controls look like.

also anyone replacing their icons in the gnome icon library remember to build their icon cache using

sudo gtk-update-icon-cache -f /usr/share/icons/gnome

I hope the official gnome icons are changed to something similar to Qwerty's than these ugly engraved icons from the 90s.

---

