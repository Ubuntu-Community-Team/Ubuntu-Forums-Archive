---
title: "Quicksilver/Launchy for ubuntu"
date: 2006-11-23
forum: Desktop Environments
---

### Post by klarre on 2006-11-23
Hi!
I have been looking for a replacer for my windows application Launchy (similar mac application is called Quicksilver), do you know any? It is a program launcher that shows up when pressing some buttons and has a textfield to type application names in (the one you want to start).

Thank you.

---

### Post by mexlinux on 2006-11-23
You should try katapult, it's in the repos
See:
[http://kde-apps.org/content/show.php?content=33985]("http://kde-apps.org/content/show.php?content=33985")

---

### Post by klarre on 2006-11-24
> **mexlinux said:**
> You should try katapult, it's in the repos
See:
[http://kde-apps.org/content/show.php?content=33985]("http://kde-apps.org/content/show.php?content=33985")

Thanks!
May I ask you if you know a GNOME alternative please?

---

### Post by Bruegger on 2006-11-24
Not sure wht u referring to..try pressing alt+F2 in Gnome..to use the run launcher...is tht the one u lookin for?

---

### Post by keithpeter on 2006-12-19
> **Bruegger said:**
> Not sure wht u referring to..try pressing alt+F2 in Gnome..to use the run launcher...is tht the one u lookin for?

Close but not quite. I use quicksilver on my iBook under Mac OS X. The app makes a list of all the files and applications on the computer in the background. 

When you invoke it by pressing a key chord - the default is ctrl-space you get a small window over any apps you are running with a small text box.

The crucial difference from alt+f2 is that when you type a few characters into the box it runs an interactive search and filters a list of files and apps. You keep typing until the thing you are trying to find appears, then you hit return. If the thing is an app it runs. If the thing is a file it does the double-click action for that file. The nice part is that the app remembers the search terms, so after a few invocations, swiftfox would start on ctrl-space-s. The app rescans the catalogue at a period you set, or you can manually re-catalogue so new stuff is indexed.

In this way, I can run my iBook almost entirely from the keyboard. I'm thinking an Ubuntu/Linux version of this would be seriously super-ungulate in the sense that I could move to a new desktop using the scroll wheel and invoke stuff.

I'm dreaming of a minimal fluxbox desktop where you type something to start an app or load a file - sort of Jef Raskin Humane interface.

I'll try the K app mentioned but if anyone knows of anything that will work with fluxbox, I'd appreciate knowing.

---

### Post by 23meg on 2006-12-19
Deskbar is where it's at. It comes preinstalled in Edgy.

---

### Post by dlai on 2006-12-29
I have read about gnome launch box... have not tried it out though

---

### Post by davidsiegel on 2007-09-20
You might want to take a look at [GNOME Do]("https://launchpad.net/gc")

---

### Post by wersdaluv on 2007-09-21
The Deskbar is the best alternative for GNOME that I have found.

Just set a shortcut to focus on the deskbar. In my case, I use alt+J because it is easy to press.

---

### Post by tylerjames on 2007-09-27
Hmm... Looks like it's deskbar for now.

I used to use Katapult, but it doesn't seem to work that well now that I have Compiz Fusion installed.

I hope someone makes one for Gnome that as good as (or better than) Launchy and Quicksilver.

How is the development for GNOME Do coming along David?

---

### Post by davidsiegel on 2007-09-27
Just peachy! Try it out: [http://launchpad.net/gc](http://launchpad.net/gc) - there's now a tarball that doesn't require monodevelop to build.

---

### Post by davidsiegel on 2007-11-10
If you're interested in giving GNOME Do a try, I've attached a package. You press <Super>space to bring GNOME Do to the front.

Also, see [http://davebsd.com/do/addins](http://davebsd.com/do/addins) for some awesome addins. Try the Rhythmbox one, it will blow your mind. Place addins in ~/.do/addins and resatrt GNOME Do to load them

David

---

### Post by davidsiegel on 2007-11-10
Ok, now I've attached it :)

---

### Post by hasbean on 2007-11-10
Wow, Gnome Do is pretty impressive right now.

I hope it makes it to the repos, as it's the closest to Quicksilver I've seen so far.

---

### Post by davidsiegel on 2007-11-12
Hey, we have a repo now:

> Packages
=========
Do packages are currently available through a Launchpad PPA. These packages are from the still-in-development codebase and, like the project, are potentially unstable. Please make sure to provide feedback on packages to the mailing list.
 To use the packages from the PPA, add the following lines to your /etc/apt/sources.list file:
 deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
 and install GNOME Do with the command: sudo apt-get update && sudo apt-get install gnome-do.


---

### Post by airtonix on 2007-11-12
open a terminal, then type : 

> gksudo gedit /etc/apt/sources.listpaste following into that file at the bottom

>   deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy mainsave and exit

Then again in the terminal, type : 

> sudo apt-get update && sudo apt-get install gnome-do

To grab plugins: (still in terminal)

>  cd ~/.do/addins && wget [http://davebsd.com/do/addins/](http://davebsd.com/do/addins/) -l 1 -r -A .dll
It changes to your gnomeDo plugin folder in your hme folder and then begins to download all the DLL files at 
[http://davebsd.com/do/addins/](http://davebsd.com/do/addins/)

---

### Post by context45 on 2008-01-05
gnome-do is really exciting..but
I could not get it to auto launch whenever I press super+space.
every time I need to go to applications->GNOME do. to launch it.

I had checked my keyboard settings, my super(WIN) key is enabled & set to default.

 could some one lead me to auto launch the gnome-do..??

thanks

BTW.. I am using gusty gibbon(the best linux I had ever tried..so simple yet powerful..)

---

### Post by context45 on 2008-01-06
> **context45 said:**
> gnome-do is really exciting..but
I could not get it to auto launch whenever I press super+space.
every time I need to go to applications->GNOME do. to launch it.

I had checked my keyboard settings, my super(WIN) key is enabled & set to default.

 could some one lead me to auto launch the gnome-do..??

thanks

BTW.. I am using gusty gibbon(the best linux I had ever tried..so simple yet powerful..)

1/5/2008 6:58:16 PM [Info]: Successfully loaded "Applications" Item Source.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Define" Command.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Directory Scanner" Item Source.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Firefox Bookmarks" Item Source.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "GNOME Special Locations" Item Source.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Email" Command.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Open" Command.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Open Terminal Here" Command.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Open URL" Command.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Recent Files" Item Source.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Run" Command.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Run in Shell" Command.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "Internal GNOME Do Items" Item Source.
1/5/2008 6:58:16 PM [Info]: Successfully loaded "GNOME Do Item Sources" Item Source.
1/5/2008 6:58:16 PM [Error]: Could not read addins directory /home/USER/.do/addins: Directory '/home/USER/.do/addins' not found.
1/5/2008 6:58:16 PM [Error]: libtomboy not found - keybindings will not work.
1/5/2008 6:58:16 PM [Info]: Binding key '<Super>space' for '/apps/gnome-do/preferences/key_binding'. You may change this keybinding with Configuration Editor (gconf-editor).
1/5/2008 6:58:16 PM [Error]: Could not add global keybinding: libtomboy

the terminal log shows that "libtomboy" is missing for key-binding.
is it another library..? 
tried to search in syaptic package manager, but does not exists.

---

### Post by davidsiegel on 2008-01-06
Sorry, we're having problems with libtomboy all of a sudden for an unknown reason. You'll need a sufficiently new version of Tomboy notes and it will include libtomboy. Alternatively, you can use compiz or something else to bind a key combo to the command gnome-do which will have the same effect.

---

### Post by context45 on 2008-01-07
installed tomboy & the super+space key-binding works.
 installing is easy the usual way. (apt-get install tomboy),
 but make sure to (apt-get update)

 Thanks david

---

