---
title: "Compiz-Fusion settings wont &quot;stick&quot;"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by Shinobi326 on 2007-10-21
I upgraded to Gutsy yesterday and was able to get through reinstalling Nvidia drivers again.  I downloaded the Compiz Settings Manager yesterday to adjust some of the Compiz-Fusion settings BUT no matter what I do the settings never seem to take.

Is there some magic trick, button, restartX that I need to do in order to get the settings to "stick"?

Right now the most annoying thing is that I cannot move any windows.  I go into the settings manager and select "Move Window" and close the settings manager but I'm still not able to move any of my windows.

Any and all help would be appreciated!

---

### Post by Shinobi326 on 2007-10-22
Anyone?

---

### Post by HydroDiOxide on 2007-10-22
Had the same problem. The only to get things working for me, was to uninstall anything a search for compiz in sysnaptic came up with (including emerald), do a metacity --replace, reboot and install the plugins and ccsm again.

Then make sure the move and decorations plugin are on.

Good luck!

---

### Post by WinterWeaver on 2007-10-22
I didn't have this problem with a fresh install of 7.10.... However, long ago, with Feisty, I had this problem because I was changing the compiz settings in the configuration editor, and also installed the Compiz Settings Manager.... Whenever I changed settings in the Settings Manager, they would revert to whatever was in my Configuration Editor.

I was Extremely Happy with Gutsy's enabling of desktop effects. NO need for extra repos. just a simple 2 click to enable. then I added the Compiz Settings manager to customize my settings, and now everything is set up perfect.

Are you using Ubuntu's Compiz? Or are you using someone else's repos? If you are using someone else's repos, it could be where you are having problems.

lol... or maybe I will be corrected by someone else :P


WW

---

### Post by Monstroxus on 2007-10-22
same problem here...

---

### Post by Fabioamd87 on 2007-10-22
same problem, and i'm not using any external repos

---

### Post by Shinobi326 on 2007-10-22
Well when I first installed Fiesty I did have the old configuration manager(configuration editor?) for Compiz.  I don't remember uninstalling it unless Gutsty already did that for me during the upgrade.  I did install the newer Compiz Settings Manager and that's what I've been trying to use to change the settings.

I guess you're recommending me to go through synaptic, and try to uninstall this old configuration manager and I should be ok?

Does anyone else have any more suggestions?

---

### Post by 127.0.0.1 on 2007-10-22
reload compiz, go into terminal, run command "compiz". your windows might dissapear for a moment, than your new settings will be enabled.

---

### Post by Shinobi326 on 2007-10-23
That "Compiz" tip in that last post did the trick.... I hope that bug is patched someday though....strange. 

Thanks! :guitar:

---

### Post by Shinobi326 on 2007-10-29
Well much to my dismay, I'm still having problems with this.

I'm able to get around the issue by typing "compiz" in terminal after each reboot.  My configured settings in CCSM are still not "sticking" so everytime I reboot I have to go into CCSM, click on "move windows", type "compiz" in terminal and it works.  This is kinda lame to do this on every reboot.  

I'm still in need to get my CCSM settings to last.

I've tried the trick from this thread with no success either:  [http://ubuntuforums.org/showthread.php?t=595270](http://ubuntuforums.org/showthread.php?t=595270)

here is my output for 'dpkg -l | grep compiz' which might be a problem (I am running gutsy)?
```

ii  compiz                                 1:0.6.0+git20071008-0ubuntu1              OpenGL window and compositing manager
ii  compiz-core                            1:0.6.0+git20071008-0ubuntu1              OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra            0.5.2+git20070928-0ubuntu1                Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main             0.5.2+git20070928-0ubuntu2                Collection of plugins from OpenCompositing f
ii  compiz-gnome                           1:0.6.0+git20071008-0ubuntu1              OpenGL window and compositing manager - GNOM
rc  compiz-gtk                             1:0.3.6-1ubuntu13                         OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                         1:0.6.0+git20071008-0ubuntu1              OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager          0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
rc  gnome-compiz-manager                   0.10.3-0ubuntu1                           Compiz Gnome Manager
ii  libcompizconfig-backend-gconf          0.5.2+git20071010-0ubuntu1                Settings library for plugins - OpenCompositi
ii  libcompizconfig0                       0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
rc  libgnome-compiz-manager0               0.10.3-0ubuntu1                           Compiz Gnome Manager
ii  python-compizconfig                    0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings

```

Here is my output when I run 'compiz' in terminal (this is when it stops and waits for something.  I have to close terminal before it finishes the script which is not included below):
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA])
06:00.0 0300: 10de:0193 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1600) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

---

### Post by janhurst on 2007-10-29
I too am bitten by this bug. Ive tried to lodge a bug in launchpad but ill be damned if its not the most annoying system in the world.

Anyone figured out whats going on?

My system was upgraded from feisty if that helps?

---

### Post by ralexand on 2007-10-29
I had this same issue...particularly with the non-moveable windows.

Here's what I did to make sure compiz "stuck"

Go into your sessions and make a new startup file...something to the effect of "Compiz Startup"
make the path "compiz --replace gconf"

That should make compiz load for you consistently.

To allow the windows to move I simply went in and turned off all the plugins that I was unsure of their use.  I believe Regex was the problem, but I turned off a couple others in the process.  

Then rebooted.

Let me know if this helps.

---

### Post by Shinobi326 on 2007-11-02
Well....i've tried everything in this thread and nothing seemed to have worked after I would reboot.  However, I finally was able to at least piece together a solution that appears to have worked for me now even after I reboot.

[LIST]
[*]First, I uninstalled all "compiz" items using synaptic.
[*]rebooted
[*]Installed all gutsy related "compiz" items using synaptic including emerald and of course the compiz configuration manager
[*]sudo gedit /etc/X11/xorg.conf and ensured the following was included in the screen section(obviously adapt to your own type of video card):
[/LIST]

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8800 GTS]"
	Monitor		"Generic Monitor"
	Option          "NoLogo" "true"
	Option          "RenderAccel" "True"
	Option          "DamageEvents" "True"
#	Option		"AddARGBVisuals" "True"
	Option		"AddARGBGLXVisuals" "True"
	Option		"AllowGLXWithComposite" "True"
	Option         "DisableGLXRootClipping" "True"
	DefaultDepth	24
	SubSection	"Display"
		Depth	1
		Modes	"2560x1600"
```
[LIST]
[*]Made sure I added in a new sessions module for "Compiz restart" with command line code "compiz --replace ccp --sm-disable"
[*]Made sure I added in a new sessions module for "Emerald restart" with command line code "emerald --replace"
[*]opened up Compiz Configuration Manager and made all of the adjustments I needed (i.e. Move Windows, Resize Windows, Cube, etc.)
[*]rebooted
[/LIST]

Again, I claim no originality in any of the procedures.  They are all taken from a hodge podge of posts that I went through in the forums.  I'm hoping the sequence helps anyone who is experiencing the same ongoing issue.  Thanks again for the people who originated the information.  I wish I took better notes to state my sources!

---

### Post by jombeewoof on 2008-07-22
I know this is an old thread, but I fixed it by just removing the simple ccsm.

---

