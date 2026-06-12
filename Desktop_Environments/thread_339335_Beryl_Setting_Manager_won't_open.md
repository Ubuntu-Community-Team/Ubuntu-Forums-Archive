---
title: "Beryl Setting Manager won't open"
date: 2007-01-15
forum: Desktop Environments
---

### Post by Guillaumeb on 2007-01-15
Hello,

I have upgraded Beryl on Ubuntu Edgy from V 0.1.1 to the latest version today

It works fine except that I cannot open the beryl Setting manager from the drop down menu (though I can open the theme manager)

Is this a known issu? Can it be solved? What command would you use to open it from the terminal?

---

### Post by ComplexNumber on 2007-01-15
> **Guillaumeb said:**
> Hello,

I have upgraded Beryl on Ubuntu Edgy from V 0.1.1 to the latest version today

It works fine except that I cannot open the beryl Setting manager from the drop down menu (though I can open the theme manager)

Is this a known issu? Can it be solved? What command would you use to open it from the terminal?
does anything happen when you do so? do you have all those listed in the screenshot installed? to open from the terminal, type in 'beryl-manager'.

---

### Post by Random20230808 on 2007-01-15
To open beryl manager from terminal just type```
beryl-manager
```
I've read about the problem from other users and I think that it's a known issue in the latest release.
Check out the beryl site [http://wiki.beryl-project.org/index.php/Main_Page]("http://wiki.beryl-project.org/index.php/Main_Page") to see some more infos.

---

### Post by ComplexNumber on 2007-01-15
i have edgy and mine works fine. i did have to add 'beryl-manager' to the menu myself, though.

btw you do know that once you've selected beryl-manager, this will often merely add the beryl icon to your notification area on your panel. this show that beryl is active should you wish to use it.  from there, you may still need to select 'beryl' after right clicking on the icon and selecting 'select window manager'.

---

### Post by Guillaumeb on 2007-01-15
Thanks for your replies

Beryl actually works fine and loads on start up and all

What i'm trying to open is the beryl Manager Settings to customize mouse clicks, hot areas, cube rotations  and all. This is the only thing that would not open from the drop down menu  from the beryl icon in the notification task bar. When clicking on beryl setting manager nothing happens

Going to the terminal and typing beryl Manager simply shows me this drop down menu

I just went to the add/remove software place and as it was updating an error message showed up:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

Maybe i should mention that I do not have this public key everyone is talking about.

I simply added
 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

to my sources.list and did sudo apt-get update

I encounter one error but as I reupdated it and everything seemed to be alright I got the new version of beryl but did not have to enter any Key and cannot access the Setting manager


Does that sound clear to you ? Do you want me to detail something?

Thanks for your replies, I really appreciate

---

### Post by Guillaumeb on 2007-01-15
BTW, typing beryl-settings in the terminal I get this message:

guillaumeb@laptop:~$ beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in ?
    import berylsettings
ImportError: No module named berylsettings

---

### Post by ComplexNumber on 2007-01-15
> **Guillaumeb said:**
> BTW, typing beryl-settings in the terminal I get this message:

guillaumeb@laptop:~$ beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in ?
    import berylsettings
ImportError: No module named berylsettings
see my screenshot above. which packages don't you have installed?

---

### Post by mexlinux on 2007-01-15
I had the same problem, yesterday.
tooday's update fixed the problem.
I noticed that python was also updated today (don't know if thats related)

---

### Post by Guillaumeb on 2007-01-15
OK this is what i have

It seems that 

beryl-dbus and beryl-dev do not show the same way on my Synaptic here

---

### Post by ComplexNumber on 2007-01-15
you seem to have everything. so is this the only problem now?:
> I encounter one error but as I reupdated it and everything seemed to be alright I got the new version of beryl but did not have to enter any Key and** cannot access the Setting manager**

---

### Post by Guillaumeb on 2007-01-15
yeh  right clicking on the beryl icon in the task bar and selecting Beryl Setting Manager does not produce anything.

And as I said, typing beryl-settings in the terminal to try to open it in a different way, gets me this message:

guillaumeb@laptop:~$ beryl-settings
Traceback (most recent call last):
File "/usr/bin/beryl-settings", line 2, in ?
import berylsettings
ImportError: No module named berylsettings

---

### Post by ComplexNumber on 2007-01-15
install libberylsettings-dev. the dev package contain a file called berylsettings.pc which goes in /usr/lib/pkconfig. the system looks for this file to see where the beryl settings are located.
in fact, install **all** the beryl-settings packages.

---

### Post by Guillaumeb on 2007-01-15
Thanks. I followed your advice and now it works great. I have a brand new setting manager. Thanks a lot

---

### Post by ComplexNumber on 2007-01-15
> **Guillaumeb said:**
> Thanks. I followed your advice and now it works great. I have a brand new setting manager. Thanks a lot
glad to help :). it suddenly clicked with me after i re-read:
>  Traceback (most recent call last):
File "/usr/bin/beryl-settings", line 2, in ?
import berylsettings
ImportError: **No module named berylsettings**that can only be that some element of the beryl-setting packages aren't installed. from the repo where i got my beryl packages, there is only beryl-settings, libberylsettings, and libberylsettings-dev. usually if a package can't be found its because the dev package hasn't been installed. so i looked at the screenshot that you gave and noticed that you had lots of other beryl-settings packages available, but you only had 'beryl-settings' installed. so it must have been because beryl settings(located at /usr/bin/beryl-settings) was looking for and expecting to find another component which wasn't installed (or which couldn't be found because a dev package was missing)

---

### Post by Deelight on 2007-01-18
> **Guillaumeb said:**
> BTW, typing beryl-settings in the terminal I get this message:

guillaumeb@laptop:~$ beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in ?
    import berylsettings
ImportError: No module named berylsettings

Installing the package "beryl-settings-bindings" should solve the problem.

---

### Post by ronmarley1 on 2007-01-18
I had this same issue and installed beryl-settings-bindings and libberylsettings-dev and now I can get to the "much redesigned" Beryl Settings Manager.  I'm not sure which installation fixed the problem, but I'd guess it was beryl-settings-bindings.

---

### Post by JohnnyGalaxy on 2007-01-18
> **Deelight said:**
> Installing the package "beryl-settings-bindings" should solve the problem.

Thanks, worked just fine for me.

---

### Post by neymac on 2007-01-18
> Originally Posted by Deelight View Post
Installing the package "beryl-settings-bindings" should solve the problem.


It works now.

---

### Post by gotgenes on 2007-01-18
> **Deelight said:**
> Installing the package "beryl-settings-bindings" should solve the problem.
That's it, indeed. Guess somebody forgot to update the package dependencies.

---

### Post by dabl on 2007-01-18
I was going to post a complimentary note about how well the new Beryl upgrade is working, until I saw this and checked Beryl-settings.  :( 

Actually, it really does seem much more stable on Kubuntu Edgy, especially with my Aquamarine windows decorator.  It seems to auto-start better -- I had to run the previous version manually about half the time.

Oh well, 2 steps forward and 1 step back, I suppose ....

:roll:

---

### Post by mexlinux on 2007-01-18
I'm still getting this problem in kubuntu edgy, even installing the proposed files....
Any Idea??

---

### Post by bobbyrj3d on 2007-01-18
My install broke after upgrading from the official repositories too. However, after I installed 2.0 from the svn repository and forced beryl-settings-bindings to 1.5 the settings manager worked flawlessly.

---

### Post by computerwolf on 2007-01-19
I registered for the forum just because I can't get this to work. I am a complete noob at this as well, so bear with me. I started out installing the 1.99 files, and the settings manager didn't open, i had installed all parts of it, trying to fix it, and the settings manager still wouldn't open. I then saw that I could get the svn 2.0.. whatever files, so I updated all the beryl files. Still nothing. Then I noticed that bobbyrj3d forced the beryl-setting-bindings to 1.5, so I gave it a try, and still nothing happens. I just want this to work, that's all.

---

### Post by mexlinux on 2007-01-19
It's a Bug in Beryl related with python versions:
[http://bugs.beryl-project.org/ticket/815]("http://bugs.beryl-project.org/ticket/815")

---

### Post by computerwolf on 2007-01-19
However it seems like when they try: python2.5 /usr/bin/beryl-settings, it either works or gives them this error:

Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 1421, in <module>
    makeCategoryArea(Category)
  File "/usr/bin/beryl-settings", line 1268, in makeCategoryArea
    CatBasePixbuf = gdk.pixbuf_new_from_file_at_size("%s/%s"%(BaseDir,CatImages[Category.Name]),IconSize,IconSize)
gobject.GError: Unrecognized image file format

However, mine still says this:
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 2, in <module>
    import berylsettings
ImportError: No module named berylsettings

---

### Post by mexlinux on 2007-01-19
These errors runing with python 2.5 are related to the 2.5 installation, some libraries are installed for 2.4 but not for 2.5 .....
I don't know how to fix that, yet.

---

### Post by mexlinux on 2007-01-19
Beryl forums provided the solution for the Python version:

Install these packages:
```

librsvg2-2, librsvg2-bin, librsvg2-common

```
And there your can start the setting manager with this command:
```

python2.5 /usr/bin/beryl-settings

```

---

### Post by bwhite82 on 2007-01-20
Type the command:

> $sudo gedit /usr/bin/beryl-settings

The very first line in the file should be:

> #!/usr/bin/env python

Append 2.5 to the end, like so:

> #!/usr/bin/env python2.5

Save the file. Should work now.

---

### Post by mid_night gypsy on 2007-01-20
soldierboy101st,
 Thank you, for solving the BSM mystery.It work like a charm!!!!
                                                                                   Gypsy

---

### Post by Naegling23 on 2007-01-20
I was following this thread, but couldnt get it to work.  A quick google search led to this result from the beryl forums:

Install librsvg2-common

This fixed the problem for me, it seems to be a fix for kubuntu/kde users.

Just wanted to pass this along.

---

### Post by computerwolf on 2007-01-21
I have performed both things that mexlinux and soldierboy101st suggested, and I still have the same error :(

---

### Post by drew_t on 2007-01-22
> **mid_night gypsy said:**
> soldierboy101st,
 Thank you, for solving the BSM mystery.It work like a charm!!!!
                                                                                   Gypsy

That did the trick for me too.  Thanks.

---

### Post by darkmediator on 2007-01-29
I also appreciate the help given here. Thankyou all.

---

### Post by baobab68 on 2007-01-31
I have the settings manager problem too. The messages I see when I run beryl-settings from a terminal are:

```

Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 1797, in <module>
    makeCategoryArea(Category)
  File "/usr/bin/beryl-settings", line 1637, in makeCategoryArea
    PlugInfo=makePluginArea(Plugin)
  File "/usr/bin/beryl-settings", line 1540, in makePluginArea
    makeGroupArea(Group,NoteBook)
  File "/usr/bin/beryl-settings", line 1480, in makeGroupArea
    if (makeSubGroupArea(SubGroup,VBox)):
  File "/usr/bin/beryl-settings", line 1425, in makeSubGroupArea
    GroupVBox.pack_start(MakeBackendWidgets(),True,True)
  File "/usr/bin/beryl-settings", line 1363, in MakeBackendWidgets
    for backend in berylsettings.Backends():
AttributeError: 'module' object has no attribute 'Backends'

```
 
I have updated /usr/bin/beryl-settings so that it refers to python2.5, which I do have installed.

I uninstalled and resintalled everything beryl-related in order to try to get the tile plugin working again, but now, although Beryl itself is working, the settings manager is not.


Anyone have any suggestions?

---

### Post by baobab68 on 2007-01-31
I finally fixed it by completely removing Beryl, rebooting, and reinstalling the latest SVN compiled by Trevino. I was *sure* I had already done that but apparently not.

---

### Post by penguinchrissy on 2007-01-31
I have tried everything suggested in here so far. I did the lib-dev, the librsvg2 files then the editing the beryl-settings file. I have even uninstalled and rebooted then reinstalled from the SVN compiled by Trevino which is where I was getting mine from orginally but didn't hurt to try. I've tried sudo apt-get upgrade/dist-upate. I'm all out of ideas. This is really upsetting because I'm reading all but these new plug-ins and I can't try them :confused:. Please help 

Here some info I hope will help

after editing beryl-setting with python2.5 I get this error 
```
dj@dj-laptop:~$ beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 1797, in <module>
    makeCategoryArea(Category)
  File "/usr/bin/beryl-settings", line 1637, in makeCategoryArea
    PlugInfo=makePluginArea(Plugin)
  File "/usr/bin/beryl-settings", line 1540, in makePluginArea
    makeGroupArea(Group,NoteBook)
  File "/usr/bin/beryl-settings", line 1480, in makeGroupArea
    if (makeSubGroupArea(SubGroup,VBox)):
  File "/usr/bin/beryl-settings", line 1425, in makeSubGroupArea
    GroupVBox.pack_start(MakeBackendWidgets(),True,True)
  File "/usr/bin/beryl-settings", line 1363, in MakeBackendWidgets
    for backend in berylsettings.Backends():
AttributeError: 'module' object has no attribute 'Backends'

```

Before editing 
```
dj@dj-laptop:~$ beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 1797, in <module>
    makeCategoryArea(Category)
  File "/usr/bin/beryl-settings", line 1637, in makeCategoryArea
    PlugInfo=makePluginArea(Plugin)
  File "/usr/bin/beryl-settings", line 1540, in makePluginArea
    makeGroupArea(Group,NoteBook)
  File "/usr/bin/beryl-settings", line 1480, in makeGroupArea
    if (makeSubGroupArea(SubGroup,VBox)):
  File "/usr/bin/beryl-settings", line 1425, in makeSubGroupArea
    GroupVBox.pack_start(MakeBackendWidgets(),True,True)
  File "/usr/bin/beryl-settings", line 1363, in MakeBackendWidgets
    for backend in berylsettings.Backends():
AttributeError: 'module' object has no attribute 'Backends'

```

I don't know how to insert screen shots but I do have them. So if those will help let me know how to get them up.

---

### Post by sixfoottallrabbit on 2007-01-31
Just downgrade the settings bindings to to the earlier SVN version. That worked for me.

---

### Post by ffxr on 2007-01-31
i had a similar problem.. u can try to remove everything beryl related.
with something like this:

```
sudo apt-get --purge remove beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings beryl-settings-bindings beryl-vidcap emerald libberyldecoration0 libberylsettings0 libemeraldengine0

sudo apt-get remove beryl* emerald* libberyl* libemerald*
sudo apt-get autoremove
sudo apt-get autoclean
rm -r ~/.beryl

rm -r ~/.emerald
rm -r ~/.beryl-managerrc
```

then reinstall beryl normally & from the standard repos'.
There is also plenty of help over @ [http://www.beryl-project.org/](http://www.beryl-project.org/)

---

### Post by penguinchrissy on 2007-01-31
Downgrading the berly setting binding work just to a pack --> force version in synaptic and works like a charm!

---

### Post by MarkoGT3 on 2007-09-27
Hi guys! New to the forums...

Anyway, I have had this problem too, I can't open The Beryl settings manager!
I think that installing beryl-settings-bindings could help but I have no idea how to do that. Is there something I type into the terminal to install beryl-settings-bindings?

Thanks!

---

### Post by ronmarley1 on 2007-09-28
> **MarkoGT3 said:**
> Hi guys! New to the forums...

Anyway, I have had this problem too, I can't open The Beryl settings manager!
I think that installing beryl-settings-bindings could help but I have no idea how to do that. Is there something I type into the terminal to install beryl-settings-bindings?

Thanks!

Welcome to the forums!  Before you go any further, you may want to stop working with Beryl and just go right to Compiz Fusion.  Beryl remerged with Compiz a few months ago, and is now known as Compiz Fusion.  Beryl is no longer under development.  There are many threads and many posts related to the re-merged project  If you see the posts above, the last one before yours is from January.
Good luck!

---

