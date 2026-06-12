---
title: "Unity - howto un-maximise windows"
date: 2011-05-28
forum: Desktop Environments
---

### Post by nicolasdiogo on 2011-05-28
hello,

just upgraded from maverick to natty

and i am now using Unity 2D, although i have Nvidia drivers installed.

my question (please excuse my stupidity); how can i un-maximise my windows?

i mean i have openned Eclipse IDE into full window (maximised) but do i make it back as a floating window?

thanks a lot,


Nicolas

---

### Post by wildmanne39 on 2011-05-28
> **nicolasdiogo said:**
> hello,

just upgraded from maverick to natty

and i am now using Unity 2D, although i have Nvidia drivers installed.

my question (please excuse my stupidity); how can i un-maximise my windows?

i mean i have openned Eclipse IDE into full window (maximised) but do i make it back as a floating window?

thanks a lot,


NicolasHi, click the square shape icon in the panel at the top of the screen next to the minus and x.

---

### Post by nicolasdiogo on 2011-05-29
thanks but there was no icons

i have followed your on link how to reset unity and run the commands

```

unity --reset
unity --reset-icons

```


and it fixed the icons problem for the windows when maximised

but i got these errors - are these serious (CRITICAL - it says)

> 
unity-panel-service: no process found
** (<unknown>:5312): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:5312): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
** (<unknown>:5312): DEBUG: PlaceEntry: Applications
** (<unknown>:5312): DEBUG: PlaceEntry: Commands
** (<unknown>:5312): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:5312): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:5312): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:5312): DEBUG: Setting to primary screen rect: x=0 y=0 w=1440 h=900
** (<unknown>:5312): DEBUG: Lost the name com.canonical.Unity.Launcher on the session bus


** (<unknown>:5312): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window65013716: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:5312): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x751680: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:5312): WARNING **: Failed to fetch view type at /org/ayatana/bamf/window65013716: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:5312): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x751680: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


** (<unknown>:5312): WARNING **: Failed to fetch view type at /org/ayatana/bamf/application0x751680: Method "ViewType" with signature "" on interface "org.ayatana.bamf.view" doesn't exist


(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed

(<unknown>:5312): GLib-GObject-WARNING **: invalid cast from `BamfWindow' to `BamfApplication'

** (<unknown>:5312): CRITICAL **: bamf_application_get_desktop_file: assertion `BAMF_IS_APPLICATION (application)' failed


---

### Post by wildmanne39 on 2011-05-29
> **nicolasdiogo said:**
> thanks but there was no icons

i have followed your on link how to reset unity and run the commands

```

unity --reset
unity --reset-icons

```


and it fixed the icons problem for the windows when maximised

but i got these errors - are these serious (CRITICAL - it says)
Hi, no, not if that was during the reset, if it was after then you might need to worry about it.

---

### Post by nicolasdiogo on 2011-05-30
it was after.


i have uninstalled gnome and unity, and then installed unity again.

still not working with the login option of 'ubuntu' for the desktop.

i have to use option 'unity 2d', on the drop-down when login in.


so all in all the upgrade when fine except for the massive point of having a working desktop.  bit of a shame since Ubuntu's team put so much effort into Unity.

but i will keep on trying to fix it, and post back

thanks a lot for your suggestions.


Nicolas

---

### Post by Copper Bezel on 2011-05-30
Okay, you didn't actually need to uninstall "gnome," which is a meta-package and doesn't remove the environment anyway, which is good, because Unity depends on it.

When you run unity --reset, that refers to the Compiz plugin that Unity-2D isn't. As I understand it, you're actually switching to vanilla Unity by doing so. However, the odd missing window control applet in Unity 2D is probably something that can be solved with a little more information, as is why you can't log into the normal Unity desktop directly but can run it anyway.

I'm assuming that the controls are still missing when you first log in in Unity 2D?

---

### Post by Oxwivi on 2011-05-31
The messages you get after Unity has been successfully reset is just the process showing it's working.

Just move the Terminal to some unused workspace.

---

### Post by nicolasdiogo on 2011-05-31
the controls are now present on Unity 2D - it is working fine as expected.

let me try the regular version.

by the way, i am using Nvidia driver.


thanks guys

---

### Post by HookedOnLinux on 2011-05-31
> **nicolasdiogo said:**
> the controls are now present on Unity 2D - it is working fine as expected.

let me try the regular version.

by the way, i am using Nvidia driver.


thanks guys


If I'm correct, you can also double click the title bar on top of the window you want to un-maximize/maximize.

---

### Post by nicolasdiogo on 2011-06-01
in my case there was something wrong with my gnome configuration

as soon as i moved/deleted my previous gnome folders from my $HOME everything started working properly.

it seems that 
```
unity --reset
```

does not actually reset the desktop environment fully.

will that be an improvement needed? a bug? or plainly just me asking too much of an upgrade?

thanks guys

---

