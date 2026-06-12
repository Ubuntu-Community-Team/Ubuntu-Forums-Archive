---
title: "setting keyboard accel maps for GTK apps"
date: 2014-05-28
forum: Desktop Environments
---

### Post by cybernetic12 on 2014-05-28
I am using a GTK app (zim to be exact), and I want to change its keyboard shortcuts.

~/.config/zim/accelmap   is a file that begins like this:
```
; zim GtkAccelMap rc-file         -*- scheme -*-
; this file is an automated accelerator map dump
;
; (gtk_accel_path "<Actions>/MainWindow/set_pathbar_path" "")
; .... ....

```

The file is generated from I-don't-know-where.  All the lines are commented out.  If I change it and re-start the app, the file will be over-written.

I tried adding:
```

    gtk-can-change-accels = 1

```
to ~/.gtkrc-2.0  but the result is the same -- accelmap file is over-written.

I also added this:
```
@binding-set unbind-ctrl-d {
    unbind "<alt>e";
}
GtkTreeView { gtk-key-bindings: unbind-ctrl-d; }
GtkTextView { gtk-key-bindings: unbind-ctrl-d; }

```
to ~/.config/gtk-3.0/gtk.css   -- same result, accelmap file is over-written.

I have upgraded to Ubuntu 14.04 and am using LXDE/Lubuntu.

I think I have Unity and Gnome installed but I don't log into those desktops.  But I have heard that Unity disabled those keyboard shortcut functions.

Call me old-fashioned but I found that some very simple maneuvers no longer work in the newer "upgrades" and I feel that I'm using a dumb and inflexible operating system :(


I searched online for answers but a similar question (for another GTK app) still remains unanswered.

Also, Ubuntu forums such as this one does not allow me (a new user) to add comments to questions unless I have gained 50 reputation or so.  This makes it impossible for me to even discuss questions that are disrupting my usage, with other users who have the same disease.  *sigh*

---

### Post by Toz on 2014-05-29
To change the keyboard accelerator, first you need to have the option turned on:
1. Settings Manager >> Appearance >> Settings >> "Enable editable accelerators"
...or...
2. Adding  "gtk-can-change-accels = 1" to your ~/.gtkrc-2.0 file. (this will require that you log out and in again or change the GTK theme away and back again for it to take effect)

Then, hover your mouse over the menu entry and either press Backspace to delete it or enter the shortcut that you want to use. (Source: [http://docs.xfce.org/faq]("http://docs.xfce.org/faq")).

You can try to edit accelmap file directly, but you need to know the proper setting for it to work. The above method works for me and the file doesn't get overwritten.

> Also, Ubuntu forums such as this one does not allow me (a new user) to add comments to questions unless I have gained 50 reputation or so. This makes it impossible for me to even discuss questions that are disrupting my usage, with other users who have the same disease. *sigh* 
You should be able to comment on any post you see providing the thread is not closed. Your number of posts shouldn't matter. Which thread were you trying to post to that wasn't working?

---

### Post by laurent7 on 2014-12-30
Hello,

I have currently the version 14.04 of ubuntu (a friend installed it 5 days ago so i am not really familiar with linux). I tried to enable equatin editor in Zim (i sucessed by installing latex ) but now i would like to add a shortkey "Ctrl+e" and i have exactly the same problem: accelmap file is over-written each time i re-open the app Zim.
On version 14.04 Ubuntu i didn't find : "1. Settings Manager >> Appearance >> Settings >> "Enable editable accelerators"
...or..."

---

### Post by Toz on 2014-12-30
> **laurent7 said:**
> On version 14.04 Ubuntu i didn't find : "1. Settings Manager >> Appearance >> Settings >> "Enable editable accelerators"
This is a feature specific to Xfce or the **X**ubuntu flavour of the Ubuntu distros.

It may be best to create a new thread specific to your issue on Ubuntu (Unity).

---

