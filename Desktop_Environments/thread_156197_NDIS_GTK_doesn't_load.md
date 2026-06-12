---
title: "NDIS GTK doesn't load"
date: 2006-04-06
forum: Desktop Environments
---

### Post by Geffers on 2006-04-06
I originally loaded Kubuntu but have installed the GNOME desktop having had problems running NDIS Wrapper.

Now in the GNOME desktop if I open a terminal window and type sudo ndisgtk after being prompted for the password I get the following error message;

Failed to load GTK bindings. Please check your Gnome installation

I tried an uninstal then reinstal of NDIS GTK

How do I check the gnome installation as it all appears to be working fine, I am posting this via the gnome desktop.

I have also viewed the Gnome Desktop properties via synaptic and can see no obvious error, all the dependencies appear to be loaded.

Geffers

---

### Post by Retrix on 2006-04-11
This is a bug in the packaging, which I apologize for. It has been fixed in the dapper version.

To run ndisgtk, you'll need to install the python-glade2 and python-gtk2 packages installed.

---

### Post by Geffers on 2006-04-12
[QUOTE=Retrix]This is a bug in the packaging, which I apologize for. It has been fixed in the dapper version.

To run ndisgtk, you'll need to install the python-glade2 and python-gtk2 packages installed.[/QUOTE]

Thanks for reply, fortunately I have en ethernet adsl connection which is working fine but I'd like to get the wifi working and the command line is a wee bit awkward as I'm unsure which files to load as drivers for my Linksys card.

I think the experimentation will be easier with ndis gtk.

Geffers

---

