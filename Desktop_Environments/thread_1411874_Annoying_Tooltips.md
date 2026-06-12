---
title: "Annoying Tooltips"
date: 2010-02-20
forum: Desktop Environments
---

### Post by Cygnia on 2010-02-20
Is there any way to get rid of the yellow box tooltips in Gnome? There's one in particular that pops up whenever clicking on the workspace switcher and that won't go away until mousing over it again. Screenshot is (hopefully) attached. Any ideas would be appreciated. Thanks.

---

### Post by hariks0 on 2010-02-20
Short Version: At command line type:

gconf-editor

Navigate to "tooltips_enabled" under apps, panel, global, and uncheck it.

(Tip: use Ctl-F and check both option boxes, search for "tooltips.)

Long version:

The long version is fun because you may discover myriad ways to mess up, I mean tweak, your computer along the way. Disclaimer: Usual disclaimer.

Essentially, you want to find the line in a particular GUI that says "tooltips_enabled" and the uncheck the box next to that. To get to that point, I did the following:

System -> Preferences -> Main Menu

That only works in some versions of Gnome on Linux. "Main Menu" may be somewhere else and you can spend some time looking around for it. Or, just open a terminal and type in "alacarte" which is the name of this "Main Menu" GUI thingie. The GUI application alacarte is the freeedesktop.org menu editor. Menus can and should comply with freedesktop.org specifications, and if they do, you can edit them from this application. As far as I can tell, alacarte does not have options that allow you to send it instructions to change the configuration, so you have to use alacarte as a gui. Which is fine.

Once alacarte is open, you will probably want to maximize it because the options and stuff are very wordy.

What you need to do at this point is to trick the computer into showing you another menu item that it normally does not display. See how the left side of Main Menu (alacarte) is basically your panel menu layout, and the right side is menu items and sub menus? Find the item called "Configuration Editor." On my system is is under Applications -> System Tools. Why is it here instead of System -> Administration or System -> Preference? The answer is obvious. The people who develop Gnome are brilliant, but stoned.

Anyway, check the box next to "Configuration Editor" and close Main Menu/alacarte. Now, "Configuration Editor" is available as an option to you.

Now, go to Applications -> System Tools -> Configuration Editor

Or, you can just skip all that messing around and open a terminal and type in:

gconf-editor

and that will open the Configuration Editor.

Maximize it.

Now, at this point you would think you'd click GNOME, but you don't. Remember, the Gnome designers are stoned. Why would you put a Gnome configuration thingie under "GNOME"??

Where you DO go does make sense in some ways. Go to applications->panel->global.

Then find tooltips_enabled and uncheck it. Now the tooltips are turned off in the panel.

There is probably a way to do the above on the command line but I don't recommend it. Nor am I exactly sure how to do it.

Tooltips will still exist in other applications. You may be able to disable them using a similar approach, and if you manage that, please let us know. Note that the Configuration Editor has a "find" function. Use it carefully!:D

---

### Post by doublewitt on 2010-08-14
I appreciate the effort in the explanation - but - after doing what is written there, tooltips still appear for the workspaces... there is no need for those tooltips...

Is there a "workspace-switcher" file that can be edited?

---

### Post by doublewitt on 2010-08-14
I found the solution (for me),

"The way to get rid of ALL tool tips is open your Compiz Config Settings Manager, enable "Opacity, Brightness and Saturation" under "Accessibility". Click on the button to go into the settings.

Under the "Opacity" tab go down to "Window Specific Settings" and click "Add". Type "Tooltip" and slide the opacity down to zero. Click "Close".

You're done."

[NB: It is possible you already have "Tooltip" included under another entry, for example if you've made your menus, popups, dropdowns etc transparent. If so just edit that entry and remove "Tooltip" form it so you don't have two conflicting opacity settings.]

from:  [http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html]("http://geekybits.blogspot.com/2007/07/ubuntu-tip-turning-off-tooltips.html")

**[SIZE="6"]*[/SIZE]**there are other alternatives on this page...

---

### Post by Dreamer Fithp Apprentice on 2012-04-15
> **doublewitt said:**
>  . . . open your Compiz Config Settings Manager,  . . . 
Is this feature still there in Oneiric? Or the same functionality somewhere? I hope so. I reinstalled Compiz just for this. Can somebody point me to where it is now, please?

---

### Post by overdrank on 2012-04-15
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

