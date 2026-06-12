---
title: "Dropbox icon and XFCE indicator plugin"
date: 2014-05-24
forum: Desktop Environments
---

### Post by winecurmudgeon2 on 2014-05-24
My Dropbox icon in the indicator plugin was there this morning and then disappeared. I'm running Xubuntu 12.04 with XFCE 4.10, and have never had this problem. It always showed up in the indicator plugin. Dropbox had been installed via the nautilus dropbox in synaptic, with the thunar addition.

As near as I can tell, Dropbox is still running, because I get the notification bubble when something happens with Dropbox. I have tried almost everying I can find to restore the icon:

-- Removing the plugin from the panel and putting it back. Nothing.
-- killall indicator-application-service and killall xfce4-indicator-plugin. The plugin blinked, but didn't quit either time.
-- Removing and reinstalling Dropbox and the indicator plugin. No change.
-- killall xfc4-panel. It went away, but when I restarted it, Dropbox was still missing.
-- Changing the icons. Nope.

Any thoughts would be much appreciated

---

### Post by dannyboy79 on 2014-05-24
i have dropbox for xubuntu 14.04 and when I view my panel preferences i see "notification area (external)" and "indicator plugin (external)", do you have both of those in your panel?

---

### Post by winecurmudgeon2 on 2014-05-24
I do have a notification area, but I don't use it. I have Docky instead. So the only items in the top panel are the menu, lots of separators, the indicator plugin, weather plugin, date, and log out.

---

### Post by dannyboy79 on 2014-05-24
what i was driving at was that is it possible that the dropbox tray icon is only visible in the notifications area addon? have you tried to launch the dropbox configuration again to see if maybe you don't ahve the sys tray icon enabled?

---

### Post by winecurmudgeon2 on 2014-05-25
The only two configuration options are start on startup and show desktop notifications, both of which are checked. Dropbox does show up in the notifications area plugin, so I guess I will use that. I can't figure out, for the life of me, why it is acting so squirrely -- one minute fine, the next minute gone. It has never done this before in the six years I've been running Linux. And I didn't do anything to 12.04 before this happened.

Thanks for your help.

---

### Post by n.hinton on 2014-07-05
in a terminal ```
dropbox stop
dropbox start
``` poor workaround but it works for me (just for the dropbox icon that is)

---

### Post by el_garicimo on 2014-12-17
Did you ever find a fix for this? Dropbox indicator has flickered on and off as well, but I don't know why. I was trying to futz with it today, and noticed the Chrome indicator was working...even when I had closed chrome! That's because I guess chrome had "allow chrome to run in the background" enabled. But turning that off, now even the Chrome icon doesn't show up in the Notification area (external).

I honestly think there's some bug in the Notification area (external). I'm using xubuntu 14.04

---

### Post by jean-marie2 on 2014-12-19
I've exactly the same problem with icon of Dropbox in notification area : it's simply disappear but synchronisation seems to be ok
I've uninstalled and reinstalled Dropbox but do nothing more. 
I'm using xfce 4.10 and ubuntu 14.10

---

### Post by petros-mikos on 2014-12-19
Same problem here. Dropbox icon appears on one boot, disappears on another. Tried installing, uninstalling but to no avail.

---

### Post by Kurt_Alan on 2014-12-20
Moderators,

Why is this thread marked "solved"?  There is no solution stated.  If there is, please point it out to me. Thus far, I can't find any solution for this problem on the Internet.  Many Linux users of various distros and flavors are having the same problem.

It doesn't matter whether I install from a .deb from dropbox.com via CLI or via synaptic nautilus-dropbox, the result is the same:

Dropbox itself functions (You can check via ```
 dropbox status 
```

but without an indicator there is no access to dropbox's powerful features, such as "selective sync," which, for me, is the only reason I am paying $450.00 per year for two accounts, 3 TB.  Now dropbox is no better than Google Drive.

I have started a trouble ticket at dropbox.com and I am waiting for a reply.  I have also posted to that forum.  Others are having the same problem, with no solution.  A quick google search will show that lots of Linux users are having this problem and that there is no solution at this time.

I'm going to raise hell with dropbox if this is not fixed.  Any recommendations?

---

### Post by Kurt_Alan on 2014-12-20
This is not a work-around for the no indicator problem.  My Dropbox works fine but is no better than Google Drive if I can't access preferences and selective sync, for which I must have an indicator.

---

### Post by el_garicimo on 2014-12-20
I've been hammering on this all day...not solved but made some interesting discoveries... i'm using 64 bit xubuntu 14.04 on a dell xps 12 9q33

I don't know if it's related, but there was also an indicator issue with Copy, which this post from webupd8 addresses: [http://www.webupd8.org/2014/06/fix-copycom-indicator-menu-for-ubuntu.html](http://www.webupd8.org/2014/06/fix-copycom-indicator-menu-for-ubuntu.html)
I've been trying to figure out if I could apply this solution analogously to my dropbox installation, but it's not been obvious / haven't been able to figure it out.

in this article, the link to this bug report: [https://bugs.launchpad.net/libdbusmenu/+bug/1086563](https://bugs.launchpad.net/libdbusmenu/+bug/1086563)

and in that bug report, there is a test case python script:
[http://pastebin.ubuntu.com/7604811/](http://pastebin.ubuntu.com/7604811/)

downloading that python script as python_test.py and running that python script in my terminal:
$ python python_test.py

I get a firefox indicator popping up...however, if I change the "firefox" in line 18 of the python script to "dropbox" , a dropbox indicator shows up!

ctrl- z stops the python script, and closing that terminal windows makes the icons disappear again.

Perhaps this info will help people who actually know what they're doing get a fix!

---

### Post by el_garicimo on 2014-12-20
Wow, I think I inadvertantly figured it out! For me at least :-p

I have a netbook that I'm running a 32 bit installation of lubuntu on, and the dropbox icon works fine there...I figured I'd try to install another desktop environment to see if that would help. Apparently it's pretty easy, and this article does a good job of explaining it:

[http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/)

Basically, it's super easy to install another desktop environment and switch which one you want to load upon login. I decided i'd try lubuntu here's what I did

1.) install the desktop environment via terminal (you could use the software center too though)

$ sudo apt-get install lubuntu-desktop

2.) after it was done, shut down the computer

3.) boot into xubuntu. At the login screen, in the upper right next to the batter icon, there's a little xubuntu icon...click that, and it gives you a choice of what session to log in as. I didn't even know this, but apparently there's an 'xfce session' option and a 'xubuntu' session option....being curious, i clicked on the 'xfce session' option, and logged in....and voila! dropbox icon was back.

4.) Now that the icon was back, I tried it for the regular 'xubuntu' login session and it works for that too. And of course it woks for the lubuntu sessions as well.

So that seemed to do it! hopefully it works for you guys too!

---

### Post by markodd on 2014-12-21
[B]BE CAREFUL. DON'T DO WHAT THE POSTER ABOVE ME DID! IT BROKE MY SETUP!
[/B][COLOR=#000000]
Actually, there's no need to install a diferent desktop environment. All you need to do is change to XFCE and then when going back to Xubuntu, the icon is there. However, how do I make Xubuntu my default environment?! It always boots me to xfce and it's pissing me off![/COLOR]

[COLOR=#000000]
EDIT: Apparently I'm on Xubuntu, but everything looks different. For example, my "docky" doesn't let me choose "Intellihide" now. A warning pops-up saying that docky requires compositing and because of that docky will not function properly and the windows will look different. So ya, does anyone know how to fix this or will I have to format my PC again?[/COLOR]

[COLOR=#000000]God damn it algaricimo, I hate you! [/COLOR]

[COLOR=#000000]Though really, why does switching to XFCE and then going back to Xubuntu break things up?![/COLOR]

---

### Post by el_garicimo on 2014-12-21
uh-oh, looks like I may have opened a pandora's box of sorts... I don't use docky, so I don't know why that may have messed things up...I have spent my fair share of frustrated hours futzing with my setup though, so I feel you pain!

This did indeed fix the problem for me and a couple others though, so for those of you wanting to try but hesitant to take the risk, you can just take a full backup of your system on an external hardrive using something like clonezilla before making the plunge.

---

### Post by markodd on 2014-12-22
> **el_garicimo said:**
> uh-oh, looks like I may have opened a pandora's box of sorts... I don't use docky, so I don't know why that may have messed things up...I have spent my fair share of frustrated hours futzing with my setup though, so I feel you pain!

This did indeed fix the problem for me and a couple others though, so for those of you wanting to try but hesitant to take the risk, you can just take a full backup of your system on an external hardrive using something like clonezilla before making the plunge.

You don't have to do all that stuff you did. All you have to do is disable compositing and then reboot.

---

