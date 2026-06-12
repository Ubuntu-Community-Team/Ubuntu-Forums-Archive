---
title: "file dialogs not working with Compiz"
date: 2010-02-08
forum: Desktop Environments
---

### Post by jwatne on 2010-02-08
Greetings, all.

I have had a weird issue with file dialogs when running Compiz as the window manager on Karmic Koala for the last couple days.  Sometimes, when attempting to use a file open dialog, the dialog does not display anything, or the buttons do not accept any input.  The image below is an example from this morning, when attempting to use Music > Import Folder... in Rhythmbox.

[IMG]http://home.comcast.net/~jwatne/NoDialog.png[/IMG]

I have encountered similar problems when trying to open a local HTML file within Firefox.  I use the Compiz Fusion Icon to toggle between Compiz and Metacity as needed, using Metacity when viewing video or playing Nexuiz on my 8-year-old machine.

The problems started after attempting to install TORCS, The Open Racing Car Simulator, per the instructions posted in a reply in [http://kiloandtorcs.blogspot.com/2009/09/install-torcs-on-ubuntu.html]("http://kiloandtorcs.blogspot.com/2009/09/install-torcs-on-ubuntu.html"):

```
sudo apt-get build-dep torcs
```

After doing so, I wound up getting a black screen.  I went back and re-downgraded and locked the versions of the libgl1-mesa-dri and libgl1-mesa-drx libraries, per the "[How to fix black wallpaper...]("http://www.ode2.com/?p=44")" posting.  Upon doing so, the Synaptic Package Manager reported the libgl1-mesa-dev library as being broken, and I wound up removing it.

The easy solution, of course, would be always to run Metacity, which doesn't have these problems.  However, I do like the eye candy and cube rotation for quick desktop switching with Compiz.  I have found that sometimes using the Compiz Fusion Icon to switch from Compiz to Metacity, then back to Compiz, seems to re-enable the file dialogs when using Compiz.  Then again, sometimes it doesn't.

Has anyone run into a similar problem?  If you have found the "magic" keywords that I didn't come up with while attempting to search for the right solution, I would be happy to be directed to an already-posted solution.  Is there any additional information that I may give you, such as portions of the .xsession-errors file, which may help track this down?

Thanks in advance!

---

### Post by jwatne on 2010-02-25
Well, I wound up taking the MS Windows approach to dealing with this: reinstalling the OS.  Before that, I had some other weird things start happening after trying out an alpha version of a tool adding a CoverFlow-like view to the default Gnome file manager.

Any suggestions for a more elegant way to handle this should something similar occur, or should it happen to some other poor soul?

Thanks much!

---

