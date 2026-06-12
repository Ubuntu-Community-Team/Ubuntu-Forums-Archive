---
title: "**problems with synaptic**?"
date: 2006-02-04
forum: Desktop Environments
---

### Post by tension on 2006-02-04
Ubuntu's installed and has been running smoothly....until now.

  I loaded several applications using synaptic, and am [COLOR="Red"]not[/COLOR] finding start icons on my Gnome desktop to launch those programs.

  I can find the executable files installed in my /urs/bin folder by synaptic, so I'm  guessing its just the interface that's dead?

  I don't seem to have to the same problem using the "add application" route.

  ?Anyone have thoughts on this problem?

---

### Post by amohanty on 2006-02-04
Its _not_ a problem with synaptic. Not all applications will have icons in the applications menu. Only those that install ....desktop files in /usr/share/applications and some other folders in /usr/share will show up for all users. However just do a :> find -iname filename and you will know where they are. Optionally if you have already installed them via synaptic, you can select the package and view the installed files. Then you can add those to the menu via the menu editor.

HTH
AM

---

### Post by TomAnthony on 2006-02-04
I actually ahd a similar issue, and maybe with the same thing. To start I installed Ubuntu for the first time yesterday, and I'm a noob. I was playing around with synaptic to add python libraries, and after a reboot I could use the desktop (right click), but there were no icons, and the panels were bare, and I couldn't left or right click on them. My sollution was to reinstall the OS. I wonder if our issues are linked. Keep in mind I really don't know what I'm doing yet.

---

### Post by amohanty on 2006-02-04
If you did an default install, you probably had gnome. gnome uses a lot pf python libs, so theres a possibility that when you install the python libs, you might have broken something (unlikely - but possible, synaptic should have warned you). In such a scenario, you dont need to reinstall the os, just drop into recovery mode and do a:
> sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

This reinstall all the desktop components.

HTH
AM

---

### Post by tension on 2006-02-04
Well, reinstalling the system smacks of microsoft.  I'd like to leave that as a last resort.  

  I was able to work around some of my problems by following the advise above.  I manually configured the application menu to show the missing applications. (select <new> in the application menu editor and then find the appropriate files through search-n-pick) . (Another minor problem though, I can't get the " find -iname filename" code to work.)
  This doesn't necessary take synaptic off the hook. After poking around I found Clamav, the application, has had some problems loading through synaptic.  I'm guessing that this is the problem here, I found the files loaded, I can still can't access the program.  Maybe its something I'm overlooking.
  Anyway, thanks for the help 

e

---

### Post by tension on 2006-02-04
Oh, and one more thing, synaptic did give me an error message the first time around.

e

---

### Post by amohanty on 2006-02-04
> (Another minor problem though, I can't get the " find -iname filename" code to work.)

so in the terminal if you do:
> find -iname replace_with_filename

what happens?

for e.g. 

> aseem@kandinsky:/usr$ find -iname *.py
./share/doc/python2.4/examples/Demo/cgi/cgi1.py
./share/doc/python2.4/examples/Demo/cgi/cgi2.py
./share/doc/python2.4/examples/Demo/cgi/cgi3.py
./share/doc/python2.4/examples/Demo/cgi/wiki.py
./share/doc/python2.4/examples/Demo/comparisons/regextest.py
./share/doc/python2.4/examples/Demo/comparisons/sortingtest.py
./share/doc/python2.4/examples/Demo/comparisons/systemtest.py
./share/doc/python2.4/examples/Demo/classes/Complex.py


You either have to do it from the top level dir / or from the dir where you suspect the file to be.

For clamav follow instructions at:
[https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29](https://wiki.ubuntu.com/ClamAV?highlight=%28clamav%29)

HTH
AM

---

### Post by Madpilot on 2006-02-04
[QUOTE=tension]Well, reinstalling the system smacks of microsoft.  I'd like to leave that as a last resort.[/QUOTE]

The package ubuntu-desktop isn't your whole system, not by a long shot. Adding/removing it won't actually affect that much.

I've got it removed right now, because I don't need all the international fonts that Ubuntu ships with and removing them causes the ubuntu-desktop package to be removed as well.

Ubuntu-desktop is basically just a way to install a whole pile of packages all at once, it's not really a package in it's own right.

---

### Post by tension on 2006-02-05
*amohanty*:
  Ok,ok I got <find -iname> to work.  Seems as though I had a little problem with syntax.  I'm still working on command-in sentences fro this OS.

  I did a [COLOR="Red"]complete[/COLOR] removal of ClamAV and componants and installed the whole thing again through Synaptic.  I then ran it from the terminal successfully.  One problem:  running <freshclam> gave me an update error for my version.  I remember reading somewhere on this forum that Ubuntu will update automatically.  Is this true?

*madpilot*:
  Yeah, I pick that up from reading other posts.  My concern is that I'll lose some data/configurations if I should ever have to go that route.  The original install did require erasing of the disk.

e

---

### Post by amohanty on 2006-02-05
> I remember reading somewhere on this forum that Ubuntu will update automatically. Is this true?

Yes. I am not sure but I think it checks about once per hour by default. Look up the docs, or in the link above look at the very last section.

> My concern is that I'll lose some data/configurations if I should ever have to go that route. The original install did require erasing of the disk.

Most user settings, ie settings and configs created by you are in your home dir in a bunch of .dirs. To view these 'hidden' folders do a :

> ls -a

SO a reinstall of _ANY_ software you have setup previously will not affect your settings.

HTH
AM

---

