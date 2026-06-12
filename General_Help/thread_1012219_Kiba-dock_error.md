---
title: "Kiba-dock error"
date: 2008-12-15
forum: General Help
---

### Post by Proteusiq on 2008-12-15
Exclamation  Errors in Kiba-dock
Hej Guys,
my Kiba dock rans perfectly(almost) but it aborts itself when I do the setting giving me this error

(kiba-settings:7919): Gtk-CRITICAL **: gtk_window_set_default_size_internal: assertion `change_height == FALSE || height >= -1' failed

and also when I do other things I get this error and then it aborts

(kiba-settings:7800): Gtk-CRITICAL **: gtk_window_set_default_size_internal: assertion `change_height == FALSE || height >= -1' failed

(kiba-settings:7800): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(kiba-settings:7800): Gtk-CRITICAL **: gtk_window_get_position: assertion `GTK_IS_WINDOW (window)' failed

(kiba-settings:7800): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkWindow'

(kiba-settings:7800): Gtk-CRITICAL **: gtk_window_get_size: assertion `GTK_IS_WINDOW (window)' failed

Can someone tell me what is this and how to make it not do that!

Thank you
Proteusiq is online now Report Post   	Edit/Delete Message

---

### Post by Proteusiq on 2009-03-23
I am using Cairo-dock now! It is working Brilliantly and I have to say it is more STABLE than Kiba-dock. Plus is has more features and just sweet!

You Can Do It this way(From Cairo-Dock Forum)

Add Cairo-Dock repository to your sources open the sources.list file:

sudo gedit /etc/apt/sources.list

and add the appropriate repository to the end of the file:

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) hardy cairo-dock

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) gutsy cairo-dock

The signed GPG key for identification of the repository is:

wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -

Then, to install Cairo-Dock, issue these two commands in the terminal:

sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins

Note: if you get the error "E: Couldn't find package cairo-dock-plug-ins" try the code below as it seems there has been a name change and the package is now called cairo-dock-plugins in intrepid.

sudo apt-get install cairo-dock-plugins

Then Add it to you Sessions for it to start on log on


Quote:
If You Can Not Fight Them Join Them

---

