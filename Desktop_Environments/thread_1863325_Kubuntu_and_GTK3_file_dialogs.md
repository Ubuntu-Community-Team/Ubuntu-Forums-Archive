---
title: "Kubuntu and GTK3 file dialogs"
date: 2011-10-17
forum: Desktop Environments
---

### Post by LostAndFound on 2011-10-17
I've upgraded to Ubuntu 11.10 Oneiric. I normally use Kubuntu - with kdm - but typically run several Gnome / GTK applications. Since upgrade, I have a problem with several GTK applications including Gedit, Update-Manager, and Nautilus.

The problem is that the file open dialogs are not responsive to the mouse, (so impossible to select files, buttons with the mouse, although the key short cuts such as Tab, Alt-W etc do work. I tried changing the Appearance settings (GTK+ appearance e.g. with various options such as qt-curve and Oxygen-Molecule - but the problem does not seem to be related to any of these. I also set-up a new user and the problem exists when the new user is logged-in.

Running Nautilus, and looking at .xsession-errors I get messages such as:
(nautilus:17324): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
[31mvoid DBusMenuImporterPrivate::slotItemsPropertiesUpdated(const DBusMenuItemList&, const DBusMenuItemKeysList&)[0m: No action for id 1385

I think the issue may be due to something with the X server, or the move to GTK3 (e.g. Synaptic seems OK). Or perhaps due to some package or setting.

---

### Post by elnur on 2011-10-22
I doubt I can help you with this problem, but the reason is definitely not the move to GTK3, because I'm using GTK3 applications without problems. Well, they look much uglier than GTK2 applications, but they're fully working.

---

### Post by LostAndFound on 2011-10-24
Thanks for your reply. 

The issue seems to only occur with Gnome 3 applications (So the problem occurs in Gedit, Nautilus), but not, for example, in Bluefish, and Rhythmbox which are not Gnome 3 as far as I can tell.

I also tried using GDM display manager (made no difference)
Disabled desktop effects (made no difference)
Disabled the nvidia driver (used vesa - again, made no difference)

The following bug report may be related:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/856354](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/856354)

I had earlier encountered the following issue (related to: migration away from /var/run, /var/lock):
[http://ubuntuforums.org/showthread.php?t=1859432](http://ubuntuforums.org/showthread.php?t=1859432)

---

### Post by LostAndFound on 2011-10-26
Additional information:

I installed Kubuntu on a separate partition on the same computer. 
I then installed nautilus and gedit
The same problem occurred.
(Also with and without nvidia driver, with/without desktop effects)

-- So perhaps there is a bug/ or I have a hardware issue. Any ideas for further debugging/investigation would be welcome, thanks

---

### Post by schnelle on 2011-10-26
Maybe oxygen-gtk3 will help: [http://kubuntuforums.net/forums/index.php?topic=3118994.0](http://kubuntuforums.net/forums/index.php?topic=3118994.0)

---

### Post by LostAndFound on 2011-10-26
Thanks schnelle, I installed gtk3-engines-oxygen following the instructions.

Gedit does look better now, but the file select dialog does not respond to the mouse. I can navigate via the keyboard - just not with the mouse.

Also when I dismiss the 'Open->File' dialog, I cannot access the menues File, Edit, View menus with the mouse, though I can with the keyboard shortcuts Alt-F etc. 

It's very inconsistent and buggy.

---

### Post by auz090 on 2011-11-12
I am still trying to find a solution for this too.

I may be wrong but the "Gtk3-widgets-display" issue can be separated from the "mouse-events-not-firing" issue.  Can confirm that both issues have been happening on my Kubuntu 11.10 KDE 4.7.2 (with nvidia driver) since upgrade.  And they affect GTK3 apps like Glade-3 (glade-gtk2 is ok), software-properties-gtk.  At least the Gtk2 apps are ok.

Also, both issues do not happen when log in as Gnome3 session.

---

### Post by LostAndFound on 2011-12-01
Thanks auz090,

I still have this problem. I test from time to-time after updates, (usually with gedit). I think that it is a mouse-pointer issue with X. (And indeed can be separated from the visual appearance of the windows).

---

### Post by auz090 on 2011-12-27
Hi,

Found out yesterday the problem has something to do with the left-button mouse click in KDE.

In KDE, I use left-handed mouse.  And this "left-button-click" signal doesn't get passed on to any Gtk+3 apps running in KDE.  If I changed back to "right-handed" mouse (default) in KDE->SystemSettings, Gtk+ apps worked fine.

Now I am not sure where the bug lies. KDE or Gtk+ or somewhere in between ;)?
Still looking for a solution. 

Kubuntu 11.10 Oneiric, KDE 4.7.2

---

### Post by inobe on 2011-12-27
> **auz090 said:**
> Hi,

Still looking for a solution. 

Kubuntu 11.10 Oneiric, KDE 4.7.2

upgrade to kde 4.7.4


[http://www.kubuntu.org/kde-sc-474](http://www.kubuntu.org/kde-sc-474)

4.7.2 is, well... old, many bugs have been fixed, see if it helps.

---

### Post by LostAndFound on 2012-01-06
Hello auz090,

Great - you have identified the problem. I use the mouse left-handed. 
If I switch to right-handed mouse, the file dialogs/buttons work correctly.
(This also explains why not so many other users came across the problem).

I tried inobe's solution of upgrading KDE to 4.7.4, but the issue remains. 

Perhaps the bug needs to be registered at [https://bugs.launchpad.net/](https://bugs.launchpad.net/)
?

---

### Post by auz090 on 2012-06-08
Hi,

For the record, with KDE 4.8.3, the issue with Gtk3 apps and left mouse button is gone. 
Beautiful  work to all KDE n app developers.
:)

---

