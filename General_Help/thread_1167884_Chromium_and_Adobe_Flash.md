---
title: "Chromium and Adobe Flash?"
date: 2009-05-23
forum: General Help
---

### Post by nortexoid on 2009-05-23
I just installed Chromium from the daily builds PPA, and I can't find any info on how to install the flash plugin for it. Help?

---

### Post by lovinglinux on 2009-05-23
You can't. It is still an alpha release and doesn't support plugins yet.

---

### Post by nortexoid on 2009-05-23
Weird. I could've sworn that I saw others running Chromium with flash enabled.

---

### Post by lovinglinux on 2009-05-23
> **nortexoid said:**
> Weird. I could've sworn that I saw others running Chromium with flash enabled.

Maybe you saw them running Google Chrome under Wine.

---

### Post by lovinglinux on 2009-05-23
[http://ubuntuforums.org/attachment.php?attachmentid=114757&d=1243064861](http://ubuntuforums.org/attachment.php?attachmentid=114757&d=1243064861)

---

### Post by nortexoid on 2009-05-23
Bah! I was hoping for a decent webkit alternative to Firefox. Thanks for pointing that out.

---

### Post by hyperdude111 on 2009-05-23
> **lovinglinux said:**
> [http://ubuntuforums.org/attachment.php?attachmentid=114757&d=1243064861](http://ubuntuforums.org/attachment.php?attachmentid=114757&d=1243064861)

Just checking that screeny and i realized it is the one i posted on a different thread earlier, from my system. Didn't expect that.

---

### Post by lovinglinux on 2009-05-23
> **hyperdude111 said:**
> Just checking that screeny and i realized it is the one i posted on a different thread earlier, from my system. Didn't expect that.

I'm sorry. I thought would be better than upload another image and waste resources. I can remove the link if you want.

---

### Post by hyperdude111 on 2009-05-23
> **lovinglinux said:**
> I'm sorry. I thought would be better than upload another image and waste resources. I can remove the link if you want.

Oh no, i don't mind it was just surprising.

Its quite cool.

---

### Post by sdowney717 on 2009-05-23
arora 0.5 compiled with QT webkit works with the plugins like flash

---

### Post by nortexoid on 2009-05-23
> **sdowney717 said:**
> arora 0.5 compiled with QT webkit works with the plugins like flash

I should have emphasized *GTK*. I've tried Midori and Epiphany (webkit) but didn't them find them viable alternatives to Firefox. Looks like I'll have to hang on.

---

### Post by zjagannatha on 2009-08-09
There is, now, an implementation of Chromium that supports extensions like Flash.

Directions can be found [[COLOR="Blue"]_here_[/COLOR]]("http://webupd8.blogspot.com/2009/07/how-to-enable-flash-support-for.html") but I've also paraphrased them below.

Find your libflashplayer.so file.
Mine's at /usr/lib/libflashplayer.so, but yours might be someplace else.
Once you've found the file, you need to copy that folder into your chromium plugins folder.
```
sudo cp /usr/lib/libflashplayer.so /usr/lib/chromium-browser/plugins/
```
Replacing /usr/lib/libflashplayer.so with the location of your flash library.

Once that's been done, you should be able to run Flash apps through Chromium by starting it with this:
```
chromium-browser --enable-plugins
```

If you want you can change the shortcut in your menu:
Right click on the Ubuntu logo on your main menu (By default, on the top left of the screen)
Click Edit Menus
Find your Chromium link
Edit the command to be the above command

[SIZE="5"][COLOR="Red"]NOTE:[/COLOR][/SIZE] Chromium is still in **Development**. As a result, plugins don't work very well, so you might have trouble with it.

---

### Post by oboedad55 on 2009-08-18
> **zjagannatha said:**
> There is, now, an implementation of Chromium that supports extensions like Flash.

Directions can be found [[COLOR="Blue"]_here_[/COLOR]]("http://webupd8.blogspot.com/2009/07/how-to-enable-flash-support-for.html") but I've also paraphrased them below.

Find your libflashplayer.so file.
Mine's at /usr/lib/libflashplayer.so, but yours might be someplace else.
Once you've found the file, you need to copy that folder into your chromium plugins folder.
```
sudo cp /usr/lib/libflashplayer.so /usr/lib/chromium-browser/plugins/
```
Replacing /usr/lib/libflashplayer.so with the location of your flash library.

Once that's been done, you should be able to run Flash apps through Chromium by starting it with this:
```
chromium-browser --enable-plugins
```

If you want you can change the shortcut in your menu:
Right click on the Ubuntu logo on your main menu (By default, on the top left of the screen)
Click Edit Menus
Find your Chromium link
Edit the command to be the above command

[SIZE="5"][COLOR="Red"]NOTE:[/COLOR][/SIZE] Chromium is still in **Development**. As a result, plugins don't work very well, so you might have trouble with it.

chromium-browser --enable-plugins, fixed it for me. On one of my systems it installed it in the menus correctly and in not. I just changed the menu entry. Thanks for the fix!

---

### Post by PGScooter on 2009-08-22
> **zjagannatha said:**
> There is, now, an implementation of Chromium that supports extensions like Flash.

Directions can be found [[COLOR="Blue"]_here_[/COLOR]]("http://webupd8.blogspot.com/2009/07/how-to-enable-flash-support-for.html") but I've also paraphrased them below.

Find your libflashplayer.so file.
Mine's at /usr/lib/libflashplayer.so, but yours might be someplace else.
Once you've found the file, you need to copy that folder into your chromium plugins folder.
```
sudo cp /usr/lib/libflashplayer.so /usr/lib/chromium-browser/plugins/
```
Replacing /usr/lib/libflashplayer.so with the location of your flash library.

Once that's been done, you should be able to run Flash apps through Chromium by starting it with this:
```
chromium-browser --enable-plugins
```

If you want you can change the shortcut in your menu:
Right click on the Ubuntu logo on your main menu (By default, on the top left of the screen)
Click Edit Menus
Find your Chromium link
Edit the command to be the above command

[SIZE="5"][COLOR="Red"]NOTE:[/COLOR][/SIZE] Chromium is still in **Development**. As a result, plugins don't work very well, so you might have trouble with it.

That fix worked for me as well (I just followed the paraphrase, I didn't even go to the link). Thanks.

---

### Post by Wiebelhaus on 2009-08-22
> **nortexoid said:**
> I just installed Chromium from the daily builds PPA, and I can't find any info on how to install the flash plugin for it. Help?

[Here buddy:]("http://ubuntuforums.org/showthread.php?t=1236093")

---

### Post by harry2006 on 2009-08-22
hey folks...i've been thinking of putting chromium on Ubuntu for some time but need some feedback from those who are using it now. is this really worth installing? though i've used it in xp and dont find it that amazing. any thoughts?

---

### Post by PGScooter on 2009-08-22
> **harry2006 said:**
> hey folks...i've been thinking of putting chromium on Ubuntu for some time but need some feedback from those who are using it now. is this really worth installing? though i've used it in xp and dont find it that amazing. any thoughts?

just been using it for a few days now, but I find it to be worth it. It is extremely easy to install (just add the ppa and then do the two steps for the flash plugin), and I find it to be very fast.

---

### Post by nortexoid on 2009-08-22
> **harry2006 said:**
> hey folks...i've been thinking of putting chromium on Ubuntu for some time but need some feedback from those who are using it now. is this really worth installing? though i've used it in xp and dont find it that amazing. any thoughts?

I no longer use firefox (though I do miss adblock).

---

### Post by oboedad55 on 2009-08-22
> **nortexoid said:**
> I no longer use firefox (though I do miss adblock).

It's still under development of course, but it is very fast!

Jon

---

### Post by Malcy on 2009-08-22
Chromium has just updated and --enable-extensions is broken. Hmm.... Gmail notification and the ad blocker are of course now not working. I hope that they fix it soon.

---

### Post by darco on 2009-08-22
I use adsweep and it works fine here...running the latest chromium...

darco

---

### Post by PGScooter on 2009-08-22
did anyone else have problems with the update? i am going to hold off for a bit.

---

### Post by fooman on 2009-08-22
i have the latest updates and flash works fine here.
[IMG]http://file:///home/jackel2/Pictures/Link%20to%20Screenshot-61.resized.png[/IMG]

---

### Post by darco on 2009-08-22
there're not taking about flash....

darco

---

### Post by nortexoid on 2009-08-22
> **oboedad55 said:**
> It's still under development of course, but it is very fast!

Jon

It may be under development but I've experienced only the rare crash. (The "Aww Snap" errors are only slightly more frequent.) I only keep Firefox around for Java.

---

### Post by Malcy on 2009-08-23
> **fooman said:**
> i have the latest updates and flash works fine here.
[IMG]http://file:///home/jackel2/Pictures/Link%20to%20Screenshot-61.resized.png[/IMG]

Flash isn't the problem (well, it's another problem on 64bit atm), it is the extensions. If you set the --enable-extensions switch on the start up command, chromium just refuses to start. Remove this switch and chromium starts fine, without extensions of course. This happened precisely when update manager updated chromium to the latest build last night.

---

### Post by darco on 2009-08-23
> **Malcy said:**
> Flash isn't the problem (well, it's another problem on 64bit atm), it is the extensions. If you set the --enable-extensions switch on the start up command, chromium just refuses to start. Remove this switch and chromium starts fine, without extensions of course. This happened precisely when update manager updated chromium to the latest build last night.

Whether I run chromium from the command line or the shortcut on my desktop, both have  --enable-extensions set and I have no issues at all. Extensions are enabled, chrome://extensions confirms it.
What issues are you having w/ x64 bit flash? Its running perfect here..Originally I had to utilize an x32 bit flash player by installing it in the usr/lib/chromium/plugins but now since chromium is an x64 build, it auto detects the x64 plugins (about:plugins)

darco

---

### Post by Malcy on 2009-08-23
> **darco said:**
> Whether I run chromium from the command line or the shortcut on my desktop, both have  --enable-extensions set and I have no issues at all. Extensions are enabled, chrome://extensions confirms it.
What issues are you having w/ x64 bit flash? Its running perfect here..Originally I had to utilize an x32 bit flash player by installing it in the usr/lib/chromium/plugins but now since chromium is an x64 build, it auto detects the x64 plugins (about:plugins)

darco

Well, that's what happened. Since a chromium update last night, it refuses to run if --enable extensions is set.

The flash problems are more with Firefox but sometimes with chromium. I have been getting a lot of crashes so severe that the system just reboots if it's Firefox or the tab is killed if it is Chromium and there is more than one tab open. There are no logs for Firefox as the reboot is instant. I have installed 32 bit Ubuntu today as I was getting sick of the crashes and couldn't pinpoint the cause other than it's not faulty hardware.

---

### Post by Geomas on 2009-08-24
I just installed Chromium today (24 Aug. 2009). The following terminal command enabled Flash:

> chromium-browser --enable-plugins

and now I can watch YouTube videos or listen to Google Voice messages in Chromium.

---

### Post by magicmax0 on 2009-10-01
This fix worked for me also, i had to download flash player 10 for linux first from adobe. I choose the tar.gz file and fished through it to find that libflashplayer.so file. Pasted it into that plugins directory for chromuim, restarted and BAM youtube works! I didnt have to put the "--enable plugins" line in, using version 4.0.219 of chromium, it just worked. Now if only i could get java working with chromium.. i would have no need for firefox anymore :)

---

### Post by areskz on 2009-12-08
Flash works good for me (Chromium 4.0.246.0 + Adobe Flash 10 plugin), but there is no sound.

Did anyone encounter problems with sound in flash applications in Chromium?

---

### Post by victor9098 on 2009-12-08
I have the same problem. Flash works fine but I get no sound. Running the latest version of chromium (daily build) 4.0.267.0 (Ubuntu build 34059). When I go into the sound settings (System -> Preferences -> Sound) while trying to play a video on You Tube (for example) I can see chromium 'flickering' on/off in the applications tab but no sound.

Any thoughts?

---

### Post by dnovotny on 2009-12-17
I am not sure if you are still having problems or not, but I figured out how to fix my sound issue.  I opened the launcher, and edited the command to add --enable-plugins on the end, so now its chromium-browser %U --enable-sync --enable-plugins

I am running the developer build for it on 9.10 x64 so that may make or may not make a difference.

---

### Post by j_baer on 2009-12-17
I installed Chrome from the PPA and the plugins. Everything just worked!

I've been getting update nearly everyday which caused "quick time" to break for a brief period.

Development must really be fast paced.

I shared my thoughts on Chrome [ **here**]("http://www.projblog.com/?page_id=206").

:)

---

### Post by mister_playboy on 2009-12-26
If you already have 64bit Flash for Firefox, you can get it working in Chromium with a symbolic link.

Go to Chromium's plugin directory:

```
cd /usr/lib/chromium-browser/plugins
```

Create the link to FF's libflashplayer.so:

```
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so
```

---

### Post by Amathist on 2011-02-06
i use chromium on 64 bit lucid I have been having trouble finding a fix ](*,) but browsing the forums taught me a few nifty tricks.  this is what worked for me:

1: download adobe flash plugin (square) here: [http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)

2: open chromium and type the following into the address bar: about:plugins (the annoying smiley here represents a : followed by a p....)

3: hit the detail button and scroll down to the shockwave flash plugin to find the location of the plugin file:

Shockwave Flash
Shockwave Flash 10.3 d162
Name:	Shockwave Flash
Description:	Shockwave Flash 10.3 d162
Version:	
Priority:	1
[COLOR="Red"]**Location:	/var/lib/flashplugin-installer/npwrapper.libflashplayer.so**[/COLOR]
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl

4: open the tarball you downloaded from adobe labs and extract the libflashplayer.so file to your desktop

5: type the following command into the terminal window:
gksudo "gnome-open %u"
this will open a file browser with SU privileges

6: navagate to the plugin directory (/var/lib/flashplugin-installer/)

7: make a backup of the old plugin by renaming it (npwrapper.bak.libflashplayer.so)

8: copy libflashplayer.so from your desktop and rename it npwrapper.libflashplayer.so

9: close all the windows you just opened and restart your browser

this worked for me, it smoothed out flash video :popcorn:(youtube) and allowed me to play the apps on facebook with less lag.:lolflag:

---

### Post by Yasho on 2011-02-12
> **harry2006 said:**
> hey folks...i've been thinking of putting chromium on Ubuntu for some time but need some feedback from those who are using it now. is this really worth installing? though i've used it in xp and dont find it that amazing. any thoughts?
Hi,
It is definitely worth adding to Ubuntu, this is because Chromium lets you view pages (at least some) that can only be properly viewed in IE for windows. For eg, there are some sites that take you all the way even in Firefox, but at the last stage, when you want to pay, there is no "Pay" button visible. This is visible only in IE for windows. [www.airtel.in](www.airtel.in) is one such site.

---

### Post by luigi_mb on 2011-02-12
I don't know much about Chromium, but Google-Chrome (I use the dev version) has Flash built in.

/luigi

---

