---
title: "I miss Beryl :("
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by CSMatt on 2007-10-23
I was eagerly looking forward to Gutsy because if its inclusion of Compiz Fusion.  Beryl was great,but I always found its manager to be too complex for me compared to the old compiz-settings program.  Well, after an upgrade and some tweaking of other components, I have found Compiz Fusion to be a real pain.  For one, I no longer have a window manager that will handle Metacity themes, only Emerald.  The desktop switcher in the taskbar doesn't work at all with the workspaces in Compiz Fusion.  GNOME Compiz Manager doesn't work anymore.  Enabling something in Compiz Fusion sometimes has no effect, Emerald and the Compiz effects sometimes stop working by themselves, and I accidentally gave something a key combination and now I can't disable the combination.

I realize that all of these complaints are vague, but there isn't much more that I can elaborate on.  The Beryl and Compiz Core versions in Feisty worked perfectly, and even when I was using the bleeding edge builds of Beryl back when I was using Edgy I didn't have near as much of a problem as I do now.  To make matters worse, I have to take my laptop to class in the morning, and I was hoping to show off the eye candy.

I miss Compiz/Beryl.

---

### Post by weblordpepe on 2007-10-23
I just wish that the window-switcher and expose` thing showed minimized windows. Considering people always alt-tab to minimized windows.

---

### Post by NawaMan on 2007-10-24
I too miss Beryl. There are many thing wrong or not working the way it was or even the way it supposed to be. But I think we should help shaping Compiz to be the better on as now the resources are now focus one project.

Most of the problem I encounter at first, I found the work around so may be if you can post what is the problem you are experiencing. We can take a look, case by case.

As You mentioned that pager(switcher on the taskbar) does not work, I guest you config it with GNOME Desktop Effect (As I had done). If that is the case, stop using GNOME DE because that is for Compiz not for Compiz Fusion. Install CompizConfig Setting Manager (CCSM) (or the new name Advance Desktop Effect Setting) and use this instead.

About the theme, I don't know what did you do but for mine Metacity work as default. 
If you don't like it, use CCSM to disable Window Decoration plugin or uninstall Emerald.

There is some problem with some setting not to take effect such as triggering show desktop with corner but there is a workaround involving GConf (Let me know if you want to know more).

Hope this help.

---

### Post by CSMatt on 2007-10-25
Desktop Effects was removed by the upgrade, so I can't do that.  I'm not sure what Compiz used for a compatible window manager that used Metacity themes in 7.04, but from what I remember it was compatible with Beryl and it wasn't Helidor.  I believe that Beryl called it "GTK+ Window Manager" or something similar.

I *did* actually install CCSM and removed GNOME Compiz Manager.  One of my complaints in the first post was that a lot of the times it did not even really do anything to Compiz Fusion.  I would enable plugins and/or other features and it seemed that Compiz pretty much ignored them.

I heard that Compiz just came out with their stable version of Fusion, so I'm guessing that most of the problems are due to the version that Ubuntu used from Debian unstable when 7.10 was made.  From what I heard Ubuntu releases are made by freezing the Debain unstable at the time and stabilizing it, slipping the GNOME release in at the last minute.  Hopefully the backports team is working on getting it into the repositories.

---

### Post by NawaMan on 2007-10-25
It's true in many cases that setting things in CCSM has no effect. I believe it may be because some setting has changed its name since the last time CCSM was updated so when you set something it has no effect. My workaround is to go directly to GConf and set it there and it usually works. Because of this I think the problem you are having is the fault of CCSM not the compiz it self.

Just a thought.

---

### Post by CSMatt on 2007-10-25
It would be great if you could post that GConf workaround you were talking about earlier.

---

### Post by NawaMan on 2007-10-25
You can run GConf using gconf-editor (type that in terminal) or enable its menu item (right click you main menu icon and select "Edit Menu", GConf is called "Configuration Manager" in "System Tools" menu. You can simply enable it and it will now be on your menu).

Once you run, navigate to /apps/compiz/general/allscreens/options for general setting and /apps/compiz/plugins/ for setting of each plugin.

Editing with GConf is not as intuitive and descriptive as on CCSM but it always takes effect (as I've never experience otherwise). I usually try to set in CCSM first before I go GConf.

In case of your emerald/metacity problem, try running "metacity --replace &". If this success, uninstall emerald and restart (I try that and it work here). 

:D

---

### Post by CSMatt on 2007-10-26
Reminds me of the Windows registry.

---

### Post by new2*buntu on 2007-10-28
> **CSMatt said:**
> Reminds me of the Windows registry.
:lolflag: Me too, and I miss Beryl also. 
BTW, what are the benefits of using Compiz Fusion instead of Beryl? I don' t see any new features except for the cube reflection thing I can't get working.

---

### Post by AvengingAngel718 on 2007-10-28
i miss some stuff  about beryl and i'm pleased with some stuff in compiz. i was looking around earlier today though, and they are developing a bunch of new really cool plugins that just werent ready when it shipped. there definitely is a learning curve for compiz, but now that i'm used to it i think the settings manager is a lot easier to use. 

on a completely different note, props to weblordpepe for having the fish from goodbye galaxy as your icon. gotta love old DOS games....

---

### Post by CSMatt on 2007-10-29
I tried compiling the last Beryl version in Gutsy but ran into errors in make despite eventually satisfying the configure script.  I also tried pulling the Beryl packages out of the Feisty repositories and using them on Gutsy, only to find out that one of the libraries that Beryl needs has been upgraded to the point that it is incompatible now.  I believe I also ran into recursive dependencies at some point as well.  Thankfully I was using the LiveCD so I didn't mess up my system.

I'm thinking of just purging all Compiz-related packages, deleting any leftover configuration files, and reinstalling Compiz again.  I remember having problems with my Beryl settings after removing the official version from Edgy and installing the Feisty version after upgrading and fixing it by deleting the .beryl folder.  I suppose the same logic could fix Compiz Fusion as well.  Compiz Fusion worked perfectly on the LiveCD, so this is definitely an upgrade problem and not something to do with my hardware or incompatible drivers.

---

### Post by CSMatt on 2007-10-29
Purging all traces of compiz in the hidden files did it.  Compiz Fusion now works. :)

---

### Post by sloggerkhan on 2007-10-29
agree that some things about beryl are much nicer. I particularly like beryl's theme manager and control panel lots and lots more than the compiz one....

---

### Post by CSMatt on 2007-10-29
Even though I got Compiz Fusion working, is it possible at all to "port" Beryl to Gutsy using the current libraries?  Like I said I already tried compiling and I got make errors.

---

### Post by DouglasAWh on 2007-10-29
I miss Beryl too!!!!!

---

### Post by weblordpepe on 2007-10-31
> **AvengingAngel718 said:**
> 
on a completely different note, props to weblordpepe for having the fish from goodbye galaxy as your icon. gotta love old DOS games....
:wink::guitar:

---

