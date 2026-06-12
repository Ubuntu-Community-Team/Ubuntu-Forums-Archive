---
title: "Mono?"
date: 2006-01-10
forum: General Help
---

### Post by BinaryGod on 2006-01-10
Not sure if this is the right place or not.

I switched over to Apple from Windows about 8 months ago and have since been developing my .NET apps with Mono.  I decided to partition off my HDD and install Ubuntu, been hearing many good things about it and so far I love it.

I wanted a linux install so that I could successfully run MonoDevelop/GTK# stuff as this won't work on the OS X.  Cocoa# is so young that it's extremely difficult to use.

I'm new to this type of installation, the last linux I used was Suse 9.0, and I used Ximian Desktop to get all my stuff installed.  So I'm not real familiar with the procedures involved.

Is there any guide to installing Mono on Ubuntu, I've tried some and no matter what I do I get dependency errors for packages that are there, or have higher version numbers.  Is there an easier way?

---

### Post by lysis on 2006-01-10
have you tried searching the repositories for mono?  

```

mono-apache-server - backend for mod_mono Apache module
mono-classlib-2.0 - Mono class library (2.0)
mono-classlib-2.0-dbg - Mono class library (2.0) - debug symbols
mono-gmcs - Mono C# 2.0 compiler
mono-xsp - simple web server to run ASP.NET applications
monodevelop - C#/Boo/Java/Nemerle/ILasm Development Environment
monodevelop-boo - Boo plugin for MonoDevelop
monodoc-gecko-manual - compiled XML documentation for Gecko#
monodoc-gecko2.0-manual - compiled XML documentation for Gecko#2
monodoc-gtk-manual - compiled XML documentation for Gtk#
monodoc-gtk2.0-manual - compiled XML documentation for Gtk#2
monodoc-gtksourceview-manual - compiled XML documentation for GtkSourceView#
monodoc-gtksourceview2.0-manual - compiled XML documentation for GtkSourceView#2
monodoc-http - MonoDoc http based viewer
monodoc-nunit-manual - compiled XML documentation for Nunit

```

when i apt-cache search mono i get those results.  enable all the additional repositories for ubuntu ( sudo gedit /etc/apt/sources.list and un-comment the additional sources already in the file)

then you'll be able to sudo apt-get install [filename]  if you see the prog you need above just use that.

thanks.

---

### Post by az on 2006-01-10
[QUOTE=BinaryGod]
I'm new to this type of installation, the last linux I used was Suse 9.0, and I used Ximian Desktop to get all my stuff installed.  So I'm not real familiar with the procedures involved.

Is there any guide to installing Mono on Ubuntu, I've tried some and no matter what I do I get dependency errors for packages that are there, or have higher version numbers.  Is there an easier way?[/QUOTE]
Aren't you using synaptic?

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mono&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mono&searchon=names&subword=1&version=breezy&release=all)

All of the mono stuff is in the repositories.  If you use synaptic (or any other apt frontend) you will not have dependancy problems.

If you still have problems, perhaps you need to add the universe or other repositories?
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by BinaryGod on 2006-01-10
Thanks for the info guys.

After I made that post I decided that since I had been trying to many different ways of getting stuff working that I would wipe out the partition and start over.

I did this, and Mono installed perfectly from the Snyaptic thingy, then I got brave and enabled the Universe repositorys and tried MonoDevelop and blam, it's working fine!!

I don't know how I screwed that up last time, but it works now....

---

### Post by Rajan Varadarajan on 2006-01-11
Binary
I got interested in MONO recently and would like to develop .NET applications on my ubuntu system. Are there good tutorials available (other than the ones on the mono project web site itself)? Thanks in advance for your help.

---

