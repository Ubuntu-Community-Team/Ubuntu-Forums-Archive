---
title: "Compiz Updated earlier today"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by Tristam Green on 2007-11-09
I received an update for Compiz and CCSM earlier today, and now I cannot open CCSM.  In fact, if I go to System>Preferences>Appearance>Visual Settings I can select "Custom" but the setting doesn't stick.  If I close Appearance, it just shows back up as "Extra".

The icon for CCSM appears under System>Preferences, but if I click it, it never opens.

I have checked System Monitor to see if ccsm even opens, and it appears it does, but then it quits unexpectedly.

No error messages, no warnings.  It's really irritating, and I was just getting used to setting Compiz up.

Help?

---

### Post by Shrynn on 2007-11-09
> **Tristam Green said:**
> I received an update for Compiz and CCSM earlier today, and now I cannot open CCSM.  In fact, if I go to System>Preferences>Appearance>Visual Settings I can select "Custom" but the setting doesn't stick.  If I close Appearance, it just shows back up as "Extra".

The icon for CCSM appears under System>Preferences, but if I click it, it never opens.

I have checked System Monitor to see if ccsm even opens, and it appears it does, but then it quits unexpectedly.

No error messages, no warnings.  It's really irritating, and I was just getting used to setting Compiz up.

Help?

Pretty much the same issue here.... Updated to the newest release and now Compiz won't work. The process is running but all my effects are no longer working. CCSM won't open either.

Running Compiz in Terminal gives me:
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Still poking around. Any help would be appreciated.

---

### Post by Tristam Green on 2007-11-09
my compiz readout:
> 
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

btw, if i close the terminal session after the last line appears, all the window borders disappear.  what's going on here?

is there any additional info I could post that would assist with this?

---

### Post by Shrynn on 2007-11-09
Windows borders disappear because when you run a program from a Terminal that program is dependent on that terminal. If you close the Terminal you kill the process. So your window boarders disappear because Compiz is no longer running.

Anyone know what the CCSM launcher command is?

---

### Post by Tristam Green on 2007-11-09
it's just ccsm.  it shows up for about 5 seconds in system monitor then disappears.

---

### Post by ayoli on 2007-11-09
I'm not sure but if you come to gusty with an upgrade you may need to delete all your previous compiz settings
move them to make a backup
```
mv ~/.config/compiz ~.config/compiz.save
mv ~./.gconf/apps/compiz/ ./gonf.compiz.save
```
login/out and see if it is better, if not and you want to have your old settings back:
```
mv ~.config/compiz.save ~.config/compiz
mv ./gonf.compiz.save ~./.gconf/apps/compiz/
```

---

### Post by Zorael on 2007-11-09
Tip: Add an ampersand (**&**) to the end of any command to have it run in the background, allowing you to retain control of your terminal.

```
$ compiz &
```

---

### Post by ayoli on 2007-11-09
> **Tristam Green said:**
> it's just ccsm.  it shows up for about 5 seconds in system monitor then disappears.

run cssm from the terminal will give you more infos

---

### Post by Shrynn on 2007-11-09
Hrmm, dunno why that didn't work before...

Anyway here is the CCSM crash message:
> Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by Zorael on 2007-11-09
Hmm. Try completely removing - either in Synaptic, or by typing the following in a terminal:
```
sudo apt-get **purge** compiz* libcompiz* libdeco*
```

Then reinstall. It solves "most" issues when ccsm won't start.

Your mileage may vary. :>


edit: You will still retain your ccsm profile, not to worry.

---

### Post by Tristam Green on 2007-11-09
placing the ampersand after the command did not fix the window borders disappearing.

here is my ccsm output from the terminal

```
 Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

```

---

### Post by Shrynn on 2007-11-09
I tracked down the lines pointed out in the error message:
> class IdleSettingsParser:
    def __init__(self, context):
        def FilterPlugin (p):
            return not p.Initialized and p.Enabled

        self.Context = context
        self.PluginList = filter (lambda p: FilterPlugin (p[1]),
                                  self.Context.Plugins.items ())

        gobject.timeout_add (200, self.Wait)

    def Wait(self):
        if len (self.PluginList) == 0:
            return False

        gobject.idle_add (self.ParseSettings)

        return False


I'm not good at reading this stuff but maybe someone else is. I'll attempt reinstalling. I'll let you know.

---

### Post by Zorael on 2007-11-09
> **Tristam Green said:**
> placing the ampersand after the command did not fix the window borders disappearing.

It would only help if the window borders appeared and then promptly disappeared when you closed the terminal. Is that the case? I'm not sure I follow.

---

### Post by Tristam Green on 2007-11-09
after pressing enter when typing 

```
$ compiz &
```

the window borders flicker then reappear.

after i close the terminal, they disappear globally.

i did the purge command you listed and reinstalled compiz and ccsm via synaptic, still nothing.

---

### Post by Shrynn on 2007-11-09
I also reinstalled with no luck.... More errors:
> shrynn@shrynn-Linux:/usr/lib/python2.5/site-packages/ccm$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
OSError: [Errno 2] No such file or directory

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


---

### Post by Tristam Green on 2007-11-09
Weird.

The only other thing I could think of was that I'd added Treviño's repos so I could try kibo-dock.

On a whim I removed those repos and reinstalled the entirety of compiz/ccsm.

Ctrl+Alt+Bksp, and ccsm was able to come right back.

Just out of curiosity:

My ccsm shows up as "Advanced Desktop Effects Settings" in the System>Preferences menu.

After it "updated" earlier today, it showed up as "CompizConfig Settings Manager" in the menu.

Which *should* it read, or does it matter at this point, as long as it is working?


-Trist

---

### Post by Zorael on 2007-11-09
And you haven't added any weird repositories, I hope?

Treviños eyecandy repository (which provided fresh Beryl and Compiz-Fusion packages for Feisty) cause similar problems for updaters from 7.04 (or fresh Gutsy installers who've added the repository anyway). To get ccsm to work, you'd need to remove that depository from your software sources (/etc/apt/sources.list, or in Synaptic), *then* purge, update from sources, and reinstall.

edit: If you're completely removing Compiz via Synaptic (instead of doing the terminal way), you probably need to remove *everything* mentioning compiz. compiz*, libcompiz* and libdecoration0. Likely not all of them are culprits, but it's better to be safe.

The adress to the mentioned repository should contain something like '3v1n0', and it should mention eyecandy. If it's there, remove/comment it.

If you haven't touched your list of software sources and you're still getting this error, I'm not sure I can help. Mind you though, it's frighteningly similar to the issues people who use/have used that repository experience.

---

### Post by Shrynn on 2007-11-09
Ahhhh the plot thickens..... I ALSO installed Kiba just before this update. Seems there is a conflict.

I wouldn't worry about the name in the menu, it was probably part of the Update we installed.

---

### Post by Tristam Green on 2007-11-09
> **Zorael said:**
> And you haven't added any weird repositories, I hope?

Treviños eyecandy repository (which provided fresh Beryl and Compiz-Fusion packages for Feisty) cause similar problems for updaters from 7.04 (or fresh Gutsy installers who've added the repository anyway). To get ccsm to work, you'd need to remove that depository from your software sources (/etc/apt/sources.list, or in Synaptic), *then* purge, update from sources, and reinstall.

The adress to the mentioned repository should contain something like '3v1n0', and it should mention eyecandy. If it's there, remove/comment it.

If you haven't touched your list of software sources and you're still getting this error, I'm not sure I can help. Mind you though, it's frighteningly similar to the issues people who use/have used that repository experience.

Yeah, that's exactly what I ended up doing :)  Thank you very much for your help ^^

---

### Post by Tristam Green on 2007-11-09
Well, crap.  Now while compiz and ccsm are both working, my workspace switcher is acting odd.

When appearance settings are set to "None" I get four full workspaces.  If I change it back to "Custom", it appears that I only get one workspace, but four "virtual" workspaces, much like Windows' Virtual Desktop Manager Powertoy.

Any ideas?

---

### Post by Zorael on 2007-11-09
KDE? Gnome?

Try adding --ignore-desktop-hints as an argument to Compiz.

---

### Post by Tristam Green on 2007-11-09
gnome.

will that argument keep after i restart the machine? will i have to restart x afterwards?

apologies for all the slight ignorance, i'm quite new to compiz.

---

### Post by Zorael on 2007-11-09
Okay.

I don't run Ubuntu (and Gnome) myself, but it likely only starts Compiz with little or no arguments.

When you pass arguments to it yourself (in a terminal, or in a run box), they will only count for that session of Compiz; if you terminate the compiz process (by rebooting, restarting X, killall compiz, etc), you will be left without a window manager - and you'd once again need to pass the arguments if you want them reestablished.

I run Kubuntu, where Compiz isn't as integrated as in vanilla Ubuntu. I made a script to start it with the arguments I want, and then I set it up to autostart. Similar to adding it into Settings -> Sessions, I imagine.

Also, I'm struck by another feeling that I might not be completely following you. What is the difference between four "full workspaces" and four "virtual workspaces"?

---

### Post by Tristam Green on 2007-11-09
> **Zorael said:**
> 
Also, I'm struck by another feeling that I might not be completely following you. What is the difference between four "full workspaces" and four "virtual workspaces"?
After I reinstalled Compiz and ccsm, I noticed that only two workspaces showed up on my switcher, even though the properties for it indicated that I have four.

I went into the Compiz settings under General>Desktop Size and the defaults are:

> Horizontal Virtual Size: 2
Vertical Virtual Size: 1
Number of Desktops: 1

I set them to 4, 1, 4, respectively and the behavior is now as follows:

I do have four separate workspaces, and I can switch between them if I click on each workspace on the switcher.

However, as I rotate the cube, while it appears at first glance to be switching between four desktops (meaning, there are four sides to the cube), Each side of the cube shows a virtual instance of Desktop #1, as opposed to each side showing a separate Desktop.

When I drag a window from one "Desktop" to another, it does cross to the next side of the cube, but the Switcher indicates that the window is not going from Desktop #1 to Desktop #2.


**EDIT** What the Hell.  I set it to 4,1,1 and it now works perfectly.  This is so weird, and it's making me paranoid :-)

---

### Post by Zorael on 2007-11-09
Leave Number of Desktops at 1. You'll only want to tinker with Horizontal Virtual Size when you're dealing with the cube.

That could be the source of your issues with the pager/switcher applet - to be honest, I'm not sure what Number of Desktops *does*.

KDE has some massive issues with this - if you set it to 4 Horizontal, you often end up with 4x4 desktops. Adding that --ignore-desktop-hints argument helps a bit; you could try that.

---

### Post by Tristam Green on 2007-11-09
Zorael, you're my personal savior on Compiz :-)  Thanks again for all the assistance; it helped to keep me from pulling my hair out.

=D>=D>

Cheers,
Trist

---

