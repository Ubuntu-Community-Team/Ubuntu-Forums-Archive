---
title: "sudo + gedit = Broken text editor"
date: 2006-02-18
forum: Desktop Environments
---

### Post by cheuschober on 2006-02-18
Don't quite know when exactly this happened (seems it happened right around when I was downloading -- not installing -- the new kernel updates as recommended by the update manager) but gedit is half-busted. It's just fine until I need to run it with a sudo (which as you know is quite often). When I attempt to sudo it with any file I get the following:

```
 sudo gedit /etc/network/interfaces

** (gedit:14558): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi)' failed

(gedit:14558): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BonoboMDI'

** (gedit:14558): CRITICAL **: bonobo_mdi_get_active_child: assertion `BONOBO_IS_MDI (mdi)' failed

(gedit:14558): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `BonoboMDI'

** (gedit:14558): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:14558): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDOW (win)' failed

** (gedit:14558): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:14558): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:14558): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:14558): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:14558): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(gedit:14558): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(gedit:14558): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

Any help would be appreciated. Already tried a 'reinstallation' of gedit to no avail.

Best,
~Chad

---

### Post by houstonpatrick on 2006-03-02
I am having the same problem with my computer as well and I've discovered a way to fix it. Keep in mind I never really use ubuntu forums, I hope the format is clear enough to understand.

[COLOR="Blue"]THE PROBLEM[/COLOR]
I am unable to execute gedit, for example the command  "sudo gedit /etc/fstab" returns the message :
             [COLOR="Red"]command is not found[/COLOR]
It seems when I try to install with "sudo apt-get install gedit" I get the message:
             [COLOR="Red"]gedit is already the newest version.
             0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded[/COLOR].
Additionally "Text Editor" remains on the Applications menu and is checked in the Synaptic Package Manager but when I try to execute it from the Applicaitons menu  it reutuns with the message :
[COLOR="Red"]            Cannot launch entry
            Details: Failed to execute child process "gedit" (File too large)[/COLOR]
This problem just started happening today, March 2 following the installation of the following package:
         [COLOR="Red"]  irssi-text (0.8.9+0.8.10rc5-0ubuntu4) to 0.8.9+0.8.10rc5-0ubuntu4.1 . [/COLOR]

[COLOR="Blue"]THE SOLUTION[/COLOR]
Well first of all you can use the nano text editor to bypass gedit (I also discovered by doing this that I like nano more than gedit.) Use the following command to do so:
[COLOR="Red"]           sudo nano /filepath[/COLOR]
To fix the problem you need the orginal ubuntu disc, (I don't know why, it seems there is probably a way to just get it from the internet but I used the disc.) Type the following commands to reinstall gedit:
[COLOR="Red"]         sudo apt-get remove gedit
          sudo apt-get install gedit[/COLOR]
Now gedit should work!

---

### Post by kijun on 2006-03-02
I am sure of that it wouldn't be a solution that you waiting for... but why don't you just use "vi" or "nano" which are text based text editor unlike gedit.  Then, you wouldn't have that problem.

---

### Post by houstonpatrick on 2006-03-02
I was assuming some people actually prefer to use gedit. If they don't then they wouldn't have the problem and they have no reason to be reading this post.

---

### Post by taurus on 2006-03-02
[QUOTE=houstonpatrick]I was assuming some people actually prefer to use gedit. If they don't then they wouldn't have the problem and they have no reason to be reading this post.[/QUOTE]
Or perhaps they didn't know there are some other options besides gedit!!!

---

### Post by quonsar on 2006-03-02
it's not broken. when running a graphical app which requires sudo you must use 'gksudo'

```
gksudo gedit
```

---

### Post by Mustard on 2006-03-03
[QUOTE=quonsar]it's not broken. when running a graphical app which requires sudo you must use 'gksudo'

```
gksudo gedit
```[/QUOTE]

That has its own pitfalls as well from my experience.  Try typing in this..

```
gksudo gedit /etc/fstab
```

You will soon see the problem. :)
A file with open with the name "  fstab'   ", so it's adding a single quote to the end of the filename.

What you would need to do to is..

```
gksudo 'gedit /etc/fstab'
```

The problem with that method is that as soon as you put the first single quote in, you no longer have autocompletion working to autocomplet pathnames and long filenames.

Personally I still use sudo gedit, because I haven't had any issues with it (so far).

---

### Post by akiro.yamamoto on 2006-03-03
Actually gksudo is normally to be used in desktop entries or when using the Run Dialog. For example if you want a destop entry for Root File Browser, the Command Entry would be 'gksudo nautilus'. 'gksudo' is the graphical equivelant of terminal 'sudo'. 
Hope this helps clarify.

---

### Post by IAmAI on 2006-03-05
[QUOTE=Mustard]
Personally I still use sudo gedit, because I haven't had any issues with it (so far).[/QUOTE] Using *sudo* can break things. As described in the Unbunti Wiki page *[RootSudo](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29#head-0c932eb3f1619126fc8307ee7690f462552d34ec)*, certain files' ownership can become set to *root* thus causing login to fail. This happened to me when I used *sudo* with *kate* (from within Gnome). Next time I logged in I was suprised by an error message stating login had failed. I had to delete *~/.ICEauthority* to fix this.

---

### Post by Mustard on 2006-03-05
[QUOTE=IAmAI]Using *sudo* can break things. As described in the Unbunti Wiki page *[RootSudo](https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29#head-0c932eb3f1619126fc8307ee7690f462552d34ec)*, certain files' ownership can become set to *root* thus causing login to fail. This happened to me when I used *sudo* with *kate* (from within Gnome). Next time I logged in I was suprised by an error message stating login had failed. I had to delete *~/.ICEauthority* to fix this.[/QUOTE]

Well this is true.  The knowledge of the solution to the ICEauthority problem though, makes me prefer to  continue to use sudo, as I prefer to keep the ability to use autocompletion when typing in the command line. :)

If it breaks I know how to fix it. ;)

---

### Post by dralaroc on 2006-05-11
[QUOTE=taurus]Or perhaps they didn't know there are some other options besides gedit!!![/QUOTE]


That would be me!  I am having some gedit issues currently, trying to figure out how to fix it.  But, this nano thing is kinda cool, never heard of it. 

Thanks Guys

---

