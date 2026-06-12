---
title: "gDesklets application is not working correctly."
date: 2007-08-10
forum: Desktop Effects &amp; Customization
---

### Post by JMowery on 2007-08-10
As you can see from the attached image, that is all that pretty much happens.
I go to run the application from the Applications menu and then the gDesklets Shell pops up, and immediately fails to function.  If I try closing it, it will make me force quit, and if I let it set for awhile it will close automatically.

I un-installed gDesklets afterwards and re-installed, still the same thing.  I disabled Compiz Fussion and Kiba-Dock as well, nothing happening.

I'm just clueless as to what to try now as I have tried all that I know, and it simply isn't working, which is a shame because I am writing an article on my experiences with Ubuntu and I'm hoping that will get a lot of views, and this is somewhat of a let down considering how many people have told me to install it to give it a shot.

So, maybe someone here can try to help me figure out how to resolve this issue.

Any help is appreciated.

Thanks very much.

---

### Post by renzokuken on 2007-08-10
i'm fairly sure you cant use gdesklets with Compiz / Beryl.

you should try Screenlets instead

---

### Post by moore.bryan on 2007-08-10
*this will sound silly, but are you sure you have desklets set to load?  have you checked the man page for gdesklets to make sure you're calling the program appropriately?  also, i prefer [adesklets]("http://adesklets.sourceforge.net/") to gdesklets... maybe you want to check it out.*

---

### Post by JMowery on 2007-08-10
> **moore.bryan said:**
> *this will sound silly, but are you sure you have desklets set to load?  have you checked the man page for gdesklets to make sure you're calling the program appropriately?  also, i prefer [adesklets]("http://adesklets.sourceforge.net/") to gdesklets... maybe you want to check it out.*

What do you mean by having them set to load?

I followed the guide here on Ubuntu:

sudo apt-get install gdesklets
Then I went to Applications > Accessories > gDesklets

Nothing happens


What exactly are man pages?  I hope you understand I'm new to this.

---

### Post by JMowery on 2007-08-10
james@james-desktop:~/Desktop$ ./Shell/__init__.py:153: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead gtk.threads_init()
/usr/lib/gdesklets/libdesklets/system/gtop.so: undefined symbol: Py_InitModule4 System in /usr/lib/gdesklets/Controls/System is NOT a valid plugin!

Those were some errors I got when trying to run the shell from the CLI.

I don't know if those are affecting the program, but I don't know what else to do.

---

### Post by JMowery on 2007-08-10
I tried installing Screenlets from here:
[http://compiz.org/Desktop_Screenlets](http://compiz.org/Desktop_Screenlets)

I did everything correctly then when I'm told to type this:
wget [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg) -O- | sudo apt-key add - && sudo apt-get update

I get this back:
--14:35:23--  [http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg](http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg)
           => `-'
Resolving hendrik.kaju.pri.ee... 195.222.13.21
Connecting to hendrik.kaju.pri.ee|195.222.13.21|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
14:35:24 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.


So, another installation that has failed :(

Very disappointing to be honest, after I had high expectations from Ubuntu finally.

---

### Post by JMowery on 2007-08-10
I now went to install screenlets by source.
 [http://hendrik.kaju.pri.ee/screenlets/failid/screenlets-0.0.7.tar.bz2](http://hendrik.kaju.pri.ee/screenlets/failid/screenlets-0.0.7.tar.bz2)

james@james-desktop:~$ screenletsd start
Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
james@james-desktop:~$ CachingBackend: Loading cache ...
Session-file /home/james/.config/Screenlets/screenletsd.ses not found (will be created automatically).

Okay, so then it says that, but nothing has happened.  I then continue on by running:
screenletsd add Notes

I get back:

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
add-screenlet-utility | (c) RYX (Rico Pfaus) 2007 | released under GPL
No handlers could be found for logger "dbus.proxies"
Error: Screenlets-Backend (screenletsd) not found.
james@james-desktop:~$ 


Yet another error.


Anyone have any idea about this?

Seems like no matter what I try, nothing is working.

---

### Post by moore.bryan on 2007-08-10
> **JMowery said:**
> What do you mean by having them set to load?

I followed the guide here on Ubuntu:

sudo apt-get install gdesklets
Then I went to Applications > Accessories > gDesklets

Nothing happens


What exactly are man pages?  I hope you understand I'm new to this.
*i mean, have you chosen desklets to load when you run gdesklets?  in a terminal (cli), type ```
man gdesklets
``` and you'll get the manual for gdesklets... same process for any other program you're trying to figure out.  ;-)  no worries about the newbie-ness... we were all there and some of us are perpetually there.*

---

### Post by JMowery on 2007-08-10
> **moore.bryan said:**
> *i mean, have you chosen desklets to load when you run gdesklets?  in a terminal (cli), type ```
man gdesklets
``` and you'll get the manual for gdesklets... same process for any other program you're trying to figure out.  ;-)  no worries about the newbie-ness... we were all there and some of us are perpetually there.*

Yes, I already read that.

I have an error, not a failure to RTFM.  Which is why I came on here.

There is an error preventing me from running gDesklets, aDesklets, and now as well AWN:

checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto dbus-glib-1 libglade-2.0 xdamage xcomposite xrender) were not met:

No package 'libwnck-1.0' found
No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found
No package 'dbus-glib-1' found
No package 'xdamage' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

The errors will not end.

Does anyone else have these problems.

I mean, calling me a newbie is fine and dandy, but, all I want to do is install some applications and it has been nothing but trouble.  These applications are also apparently popular.

---

### Post by JMowery on 2007-08-10
I'm almost about to uninstall Ubuntu and give up.  Nothing is worth this amount of trouble.  All I wanted to do was install gDesklets and install AWN, both of which won't run.  AWN doesn't support 64bit from what I read on the forums.

I just don't know what else to do and no one on the entire forums had an answer for similar posts of mine, they just kinda died off.

I assume this post is going to die off without being helped, so I'm going to let it do just that and move on.

---

### Post by moore.bryan on 2007-08-10
> **JMowery said:**
> Yes, I already read that.
I have an error, not a failure to RTFM. 
*easy, man... just trying to cover the basics so we don't have to go back over them later.*
> Which is why I came on here.*you're in the right place, then...*
> There is an error preventing me from running gDesklets, aDesklets, and now as well AWN:

checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto dbus-glib-1 libglade-2.0 xdamage xcomposite xrender) were not met:

No package 'libwnck-1.0' found
No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found
No package 'dbus-glib-1' found
No package 'xdamage' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.*let me look into some of the errors and get back to you...*
> I mean, calling me a newbie is fine and dandy, but, all I want to do is install some applications and it has been nothing but trouble.  These applications are also apparently popular.[I]i wasn't calling you a newbie as a derogatory name; you said you were new at this and i wanted to let you know we're all new in many respects.  i may have been doing this for a while, but i still run into a ton of things about which i need to post.

what errors do you get when you try to install adesklets?
[/I]

---

### Post by moore.bryan on 2007-08-10
> **JMowery said:**
> I'm almost about to uninstall Ubuntu and give up.  Nothing is worth this amount of trouble.  All I wanted to do was install gDesklets and install AWN, both of which won't run.  AWN doesn't support 64bit from what I read on the forums.

I just don't know what else to do and no one on the entire forums had an answer for similar posts of mine, they just kinda died off.

I assume this post is going to die off without being helped, so I'm going to let it do just that and move on.
*you've gotta give it a little more than 11 hours!  ;-)  hang in there and we'll try to solve this!*

---

### Post by JMowery on 2007-08-10
I'm just frustrated, so I apologize.  I had installed Gentoo before and I had that working great and never had a problem with it (after attempting to install it around 20 times at least, and i'm not even joking about that)

Yet I can't get Ubuntu to work for me.

So, let me list all my issues again:

I got Avant Window Navigator to install and run by using a debian package for the 64 bit version.

Problem is that the icons look weird sometimes.

Like the icon to firefox will appear when the window is minimized, but when I maximize the window, this kinda higlighted box will come up in place of where the firefox logo was, and it will be there instead.

Now I don't believe that is supposed to happen, I think the highlighted box is supposed to appear behind the firefox logo to show that it is currently active, but it just makes the application logo disappear.

This happens for every application btw, as long as it is in focus, the icon will disappear.

So I made progress with that, but it's just acting weird like that and just wondering if any of you have experienced that when changing focus on windows and having the icons disappear and then reappearing when they lose focus.



With gDesklets.  I have un-installed them through the Synaptic manager thing.  I was excited about the screenlets, but that isn't happening for some reason or another.  I'll give those a break.


Compiz Fussion runs fine though.


I just don't understand why none of these widget applications want to work for me.

---

### Post by JMowery on 2007-08-10
Here are some screenshots of Avant Window Navigator

Showing that when a window has focus, the icon disappears.

In all of the screenshots I have seen with AVN, I never seen that happen.

First shot is with Firefox active.
Second shot is with the terminal active.  Notice how the icons disappear when active, but appear when not active :|

---

### Post by moore.bryan on 2007-08-10
[I]to be honest with you, i don't use avant and don't know much about it...  knowing what i DO know, i wonder if there are icons missing; meaning, when a window is active, avant gives it a larger icon.  i don't know if avant simply magnifies the icon which exists or not; perhaps someone else can shed light on that.

do me a favor and try to COMPLETELY remove gdesklets in the terminal with ```
sudo aptitude remove --purge gdesklets
``` and then reinstall with ```
sudo aptitude install --with-recommends gdesklets
```
 and post any issues...
[/I]

---

### Post by JMowery on 2007-08-10
I'll be sure to give that a shot right now.  Just wanted to post some new errors I got by becoming super user with screenlets:

james@james-desktop:~$ sudo screenletsd stop

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
Screenlets-daemon stopped.

james@james-desktop:~$ sudo screenletsd start

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
james@james-desktop:~$ Traceback (most recent call last):
  File "/usr/local/share/screenlets/screenletsd.py", line 46, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 266, in <module>
    class Screenlet(gobject.GObject, EditableOptions):
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 288, in Screenlet
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 669, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 293, in __new__
    mainloop=mainloop)
dbus.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

So yeah, I guess that _dbus.py does not like my computer or something like that.

I'll try the gDesklets again.

---

### Post by JMowery on 2007-08-10
Going no where with gDesklets, same problem as before.  Launches the shell which is immediately broken.

---

### Post by moore.bryan on 2007-08-10
*what happens when you just try to run gdesklets?  (i.e. go to Applications --> Run Application and type "gdesklets" without the quotes)*

---

### Post by JMowery on 2007-08-10
Same result.

By terminal, by menu, and by the run application menu, it's all the same result.  The gDesklets Shell launches, and nothing happens and either a few moments later it closes on it's own or I am forced to quit it.

It was the same result when compiling it by source as well.

---

### Post by moore.bryan on 2007-08-10
*that's REALLY strange... i've never heard of this issue.  when you launch it from terminal, exactly what are the errors?  if you're feeling frisky, could you install adesklets and try to launch them?*

---

### Post by JMowery on 2007-08-10
I'm gonna fire up Ubuntu later on tonight, and see if I can get it working, and then I'm going to install Fedora 7 and Sabayon Linux and see if they both work better.  I guess I'm turning my article into a comparison now.

So, I'm going to go ahead and do that and I'll let you know if it works on any other distros, and then I'll reinstall Ubuntu again and see if it works out from a fresh install (even though I only installed this a day ago)

So, i'll be working on it and I'll let you know how things work out.

---

### Post by moore.bryan on 2007-08-11
*great... any progress?*

---

### Post by briggsy87 on 2007-10-05
I have all the same errors that were experienced by "JMowery" fortunately i want to continue using ubuntu and will try and figure this out.

First i installed through synaptic, loaded the shell using applications>gdesklets
  Here it starts the shell and hangs at a blank shell screen that seems to stop loading halfway through (See Screen shot).

Then i tried the steps that were recommended by "moore.brian" in which i completely removed gdesklets in the terminal and then installed them again (also using the terminal).

I AM a newbie and do not care if you call me one, but i need help. and if you think i may be missing something very basic...i probably am!

one thing i will say is that i have read the manual and there seems to be nothing of any substance to me in there in terms of my problem.

Any help would be much appreciated.

---

### Post by Faud on 2007-10-06
Are you running compiz-fusion or beryl while running gdesklets ?

---

### Post by CaptainInsaneO on 2007-10-06
Both of you, please post output of

```
gdesklets check
```

---

### Post by briggsy87 on 2007-10-06
No i am not using compiz or beryl, as a matter of fact i just reinstalled my Ubuntu OS and other then "apt-get update" and "apt-get upgrade" gdesklets is the first thing i have installed (or at least attempted).

Here is the output of gdesklets check:
[INDENT]Checking requirements:
 - sys ... found
 - xml.parsers.expat ... found
 - xml.sax ... found
 - gtk ... found
 - ORBit ... found
 - bonobo.ui ... found
Requirements checking done. Your system looks ok![/INDENT]

---

### Post by CaptainInsaneO on 2007-10-06
There is a known bug in gDesklets with AMD64, I'm assuming you both are running 64bit because this is the error that happens when you do. Try this alternate .deb file for your gDesklets install and let me know if it fixed it:

[http://launchpadlibrarian.net/7542161/gdesklets_0.35.4-1ubuntu1_amd64.deb](http://launchpadlibrarian.net/7542161/gdesklets_0.35.4-1ubuntu1_amd64.deb)

---

### Post by briggsy87 on 2007-10-06
Yes i am running AMD64, also with the 64bit version of Ubuntu.
Installing this package has fixed my problem, i appreciate the help captain insane0.

One question that i do have is, this version seems to not have any pre-listed desklets, does this mean that i am going to a site and doing them the manual way. (that is fine i was just wondering if there was a way to add them into the GUI list).

---

### Post by CaptainInsaneO on 2007-10-06
Oh, sorry about that. Didn't foresee that happening :(

Here's how to install that package without messing up the files (takes a bit of work)

Install gdesklets and gdesklets-data via Synaptic (just do search for gdesklets, they'll both come up).
Copy the gdesklets directory from the deb I gave you to your /usr/lib directory. How to do this is as follows:

Open the deb with Archive Manger, double click data.tar.gz. You'll find the gdesklets directory you need in that tarball under /./usr/lib/

Once you find it, do a ```
gksu nautilus
``` in a terminal and copy the gdesklets directory over.

Then type ```
gdesklets start
``` in terminal and you should be good. :)

---

### Post by dk5151 on 2007-10-13
Thanks for that fix, I was having the same problem. If you want all of the applets you can install gdesklets-data from synaptic after you install the fixed package.

---

### Post by CaptainInsaneO on 2007-10-13
> **dk5151 said:**
> Thanks for that fix, I was having the same problem. If you want all of the applets you can install gdesklets-data from synaptic after you install the fixed package.

That's a great tip! I wish I had thought of it. ](*,)

---

### Post by Yfrwlf on 2008-06-13
> **CaptainInsaneO said:**
> That's a great tip! I wish I had thought of it. ](*,)

Thanks for the answers in the thread and everyone's help, but I was just wondering, if this is a fixed 64-bit package that you have here then why not throw it into the repos so that this bug will get fixed for everyone else trying to install it from the repos?

Just a suggestion, though I've never done that before but I know you can help with "packaging" for Ubuntu if you want to. ^^

Though it'd be an even bigger help if Linux just used standard packages for all distros, then that fixed package could help anyone running any distro...

---

### Post by Enigma90825 on 2008-06-22
Hi,
I've been having this exact same problem on Ubuntu 8.04. Whenever I start gDesklets, the window goes gray and must be force closed. I have tried this fix as well as [http://www.righteoushack.net/?p=10](http://www.righteoushack.net/?p=10) with no avail. I'm pretty sure I am doing this one right (a bit fuzzy about the nautilus copying, just open up nautilus, navigate to the usr/lib and then drag and drop the new gdesklets folder, right?) and the same for the other one. Any help on getting this working would be GREATLY appreciated! :confused:

---

### Post by Yfrwlf on 2008-06-22
> **Enigma90825 said:**
> Hi,
I've been having this exact same problem on Ubuntu 8.04. Whenever I start gDesklets, the window goes gray and must be force closed. I have tried this fix as well as [http://www.righteoushack.net/?p=10](http://www.righteoushack.net/?p=10) with no avail. I'm pretty sure I am doing this one right (a bit fuzzy about the nautilus copying, just open up nautilus, navigate to the usr/lib and then drag and drop the new gdesklets folder, right?) and the same for the other one. Any help on getting this working would be GREATLY appreciated! :confused:

You don't need to do it that way.  Just install the package version mentioned here after uninstalling the one from the repos if you've installed it, and then install the gdesklets-data package from the repos afterward.

The package mentioned here will allow it to load, and the data package will give you all the desklets.

---

