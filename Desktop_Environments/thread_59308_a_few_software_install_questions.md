---
title: "a few software install questions"
date: 2005-08-23
forum: Desktop Environments
---

### Post by junior aspirin on 2005-08-23
hi i have a few questions about installing software in ubuntu (well linux in general) im relativly new to windows, but am loving it so far, and will be even more once i get cvscedera working...

1. where is the software installed to when installed from synaptic and when compiled/installed from source. ie in windows it *normaly* goes in 'program files'.

2. how can i uninstall programs i have installed from source. i read somewere you can just do a 'make uninstall' from the original source - but i have deleted that!

3. is it posible for a program compiled and installed from source to have an entry added to synaptic for easy uninstalation?

thanks i know these are not standard newbie questions, but im trying to learn  :grin:

---

### Post by tonysathre on 2005-08-23
when compiled from source they are put in whatever directory you were in when you compiled them, to uninstall packages open a terminal type rpm -e packagename, or just delete the directory, you can also use apt-get or dpkg, about the synaptic thing, i think if you just add extra repos the package should show up under synaptic, in sources.list file uncomment the commented repos, also search these forums for extra repos to add

---

### Post by nad on 2005-08-23
The binary executables are usually installed to one of your _bin_ directories ( /bin, /sbin, /usr/bin, /usr/sbin ) depending on the use of the application. Any libraries ( MS equivalent = dll's ) are typically installed in /lib ( /usr/lib, etc ). A customised system can have these files virtually anywhere the computer can connect to.

Not all applications have an uninstall feature. Uninstalling through a package manager is the safest method as libraries needed for other apps will not be uninstalled. Simply removing the binary and its' source will usually suffice for uninstallation but may leave orphaned libraries. These can be handled by several utilities. In your case, you may wish to install your application again, then uninstall it.

In order for an application to be recognized by your package manager, ... it needs to be in a format recognized by your package manager. Any project may be converted to a .deb file which is the format recognized by ubuntu's package manager. Please search here for instructions to do so (I imagine someone has posted a howto). It is not difficult.

---

### Post by junior aspirin on 2005-08-23
thanks for the quick reply
i realise that the compiled ones go in that directory. i asking when they are installed where do they go.

but i think i have the answer using the whereis command, they seem to go in /usr/bin and usr/share :s

one more question:
most programs can be started by just typing their name into a teminal etc, eg 'gaim' how can i set this up for a program that i just extracted to the location i wanted. ie i use the firefox and thunderbird nightly so just use download the precompiled binaries and put them in usr/local. and i have uninstalled the official tb and ff releases. i hope that makes sence.

---

### Post by tonysathre on 2005-08-23
make a launcher with the command something like this:

/usr/local/firefox, or whatever the binary name is

---

### Post by junior aspirin on 2005-08-23
thanks nad, cleared things up, u must have posed just before i did and missed your post.

i dont think my last post was too clear.

i want to iradicate the need to type the whole path into 'run application' or terminal, i just want to be able to type a word, ie gaim or firefox and the program will open. a similar thing can be done in windows too like for explorer and regedit etc, im sure its easy like putting a simlink somewhere or something.

---

### Post by nad on 2005-08-23
Creating an alias in your ~/.bashrc file is easy. Just add a line: alias gaim='/usr/bin/gaim' , but if your PATH includes the location of the "gaim" executable, this should not be necessary.

Perhaps you need to add directories to your user PATH. Add this line to your ~/.bashrc file: PATH=/new/path1:/new/path2:"${PATH}" , where /new/path1, etc are replaced by the absolute names of the directories that you wish to add.

As far as using the Run Applications applet. Only those items with launchers created for your desktop environment (other users ?) will show up here. Perhaps you may wish to look at the menu editor project listed in the forums homepage.

---

### Post by junior aspirin on 2005-08-23
btw i sorted it. even easyer than you sed :D

i just symlinked the location of firefox to the /usr/bin/ directory

oh and i never realised the run app was linked to the menu.

thanks problem solved :D

---

