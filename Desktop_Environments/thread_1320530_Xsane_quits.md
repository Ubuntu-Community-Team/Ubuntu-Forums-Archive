---
title: "Xsane quits"
date: 2009-11-09
forum: Desktop Environments
---

### Post by cscj01 on 2009-11-09
I upgraded to Ubuntu 9.10 from 9.04 about two weeks ago.  To date, I have had no issues.  Today, I tried to scan a document with my HP Scanjet 3570c.  This worked perfectly with Ubuntu 9.04.  Now, XSane opens, I select the preview window, and select Acquire preview.  The preview scan appears, and then XSane quits with no message.

I started the System Monitor, and then XSane.  I saw the xsane process with a Waiting Channel of poll_schedule_timeout.  When I chose Acquire preview, the Waiting Channel changed to pipe_wait.  The staus was sleeping in both cases.  Then the process disappears.

I tried scanning without a preview and got the same result.

Does anyone have any ideas?  I am just learning my way around Linux, so I am unsure of how to get any additional information.

---

### Post by Marly on 2009-11-11
I've got the same problem with the same scanner, karmic from a fresh install.
This is the output:
```
:~$ xsane
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:7979): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated


```

first line is the more interesting, have you got the same line?

It seems sameway related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/446373](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/446373)
No solution at this time...

---

### Post by ADBrown85 on 2009-11-11
I was having a similar problem with XSane yesterday. According to Oliver Rauch, the author of XSane, the SANE team has changed some things in the latest release of the backends that breaks compatibility. This was posted on the XSane web site in February...

 "If you experience any problems with XSane and sane-backends with a version number greater than 1.0.19 then this may be caused by an incompatible development of sane-backends. In this case it may be worth to try sane-backends-1.0.19 or earlier. XSane is and will keep compatible to the original SANE-1.0 standard. I will not spend any time for incompatible things that will mess up everything."

 Indeed if you look at the version numbers in Jaunty libsane is 1.0.19, whereas the one in Karmic is 1.0.20, so I suppose this kind of makes sense.

 I went into Synaptic and removed xsane and its dependencies, then installed older versions from source. Now things are working again with my Canon scanner!

 Download from:
  [http://www.sane-project.org/source.html](http://www.sane-project.org/source.html)
  [http://www.xsane.org/xsane-download.html](http://www.xsane.org/xsane-download.html)

 Hope that helps you guys too!

Similar threads and bug reports:
  [http://ubuntuforums.org/showthread.php?t=1320141](http://ubuntuforums.org/showthread.php?t=1320141)
  [https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/455889](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/455889)
  [https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/478761](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/478761)

---

### Post by cscj01 on 2009-11-12
Okay, I understand what you did.  However, I am not sure how to do it, as I have not installed anything from source as yet.  Can you give me a little more guidance here?  Could you just install libsane 1.0.19 rather than remove all of XSane since Oliver says he is maintaining compatibility with the 1.0 standard.  If so, how do you just replace that?  If not, how do you compile a version from source?  Thanks.

---

### Post by cscj01 on 2009-11-12
Marly, I do not get the first line you received.  My result is:

```
:~$ xsane

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xsane:20342): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
```

---

### Post by ADBrown85 on 2009-11-12
cscj01,

No problem.  Here are the steps in detail.  A lot of this could be done just as easily, or maybe even more easily through the terminal but the GUI is good too.

To remove xsane:

[LIST=1]
[*]System | Administration | Synaptic Package Manager
[*]Search for libsane
[*]Click the box beside libsane and choose Mark For Removal.
[*]It will ask if you want to remove packages that depend on libsane.  Click Mark.
[*]Click the Apply button and then confirm by clicking Apply again.
[/LIST]
Install dependencies for xsane:

[LIST=1]
[*]Still in Synaptic, search for and install *libgimp2.0-dev*.
[*]A bunch of dependencies will be needed.  Click Mark.
[*]Click the Apply button and confirm by clicking Apply again.
[/LIST]
Download and install libsane:

[LIST=1]
[*][http://www.sane-project.org/source.html](http://www.sane-project.org/source.html)
[*]Download *sane-backend-1.0.19.tar.gz *from one of the mirrors.  I had problems with the USA sites, but the Germany one worked well.  It is in the *old-versions* directory.  I'll assume you downloaded it to your Desktop.
[*]Right-click the file and select *Extract Here*.
[*]Open a terminal and enter **cd ~/Desktop/sane-backends-1.0.19/**.
[*]Enter **./configure**.  This makes sure you have everything you need.
[*]Enter **make**.  This compiles the library inside the current directory.
[*]Enter **sudo make install**.  This copies the library to where it needs to be.
[/LIST]
Download and install xsane:

[LIST=1]
[*][http://xsane.org/xsane-download.html](http://xsane.org/xsane-download.html)
[*]Download *xsane-0.996.tar.gz* from one of the mirrors.
[*]Repeat the previous steps from the libsane install, substituting the xsane file or directory where appropriate.
[/LIST]
As for only changing libsane, actually both of these will be installed in the */usr/local* directory instead of */usr*.  When a program needs a library the */usr/local* directory is always checked first, so I think you could get away with only doing libsane.  (*/usr* is for programs from your distribution, whereas */usr/local *is for programs you install yourself.)  Actually you probably wouldn't even need to remove libsane in Synaptic, but if you did then you could be sure XSane would be using the 1.0.19 version.

Hope that takes care of everything!

Andy

---

### Post by cscj01 on 2009-11-12
Andy,

I downloaded the sane backends per your instructions.  Then after extracting the archive, I ran ./configure.  I received a warning that sane would be complied without USB support.  Since my scanner (HP 3570c) is a USB device, and the message said the C++ compiler would be used, I decided to install the libusb C++ libraries.  Then I ran ./compile again and got no warnings.  So far so good.

I have a few more questions.  I have a Nikon Coolscan V ED.  The message about what backends would be built did not mention any Nikon Coolscan film scanners.  Do I also need to download, compile, and install sane-extras?  If so, do I do that after installing the sane backends and before installing XSane?  Also, where are the extra backends?  I did not see them at the German web site.

Thanks again for your help.

---

### Post by ADBrown85 on 2009-11-12
Nice pickup on the libusb libraries!  I had upgraded instead of doing a fresh install so I didn't notice that.

As for the Nikon scanner, check out [http://www.sane-project.org/sane-mfgs.html#Z-NIKON](http://www.sane-project.org/sane-mfgs.html#Z-NIKON).  It looks like all you need for the CoolScan V ED is *coolscan2*.  When I run configure it says it is going to build that so I'd say you don't need the extras.  If your configure says it isn't going to build coolscan2 look through all the status messages to see if it mentions it.  For example mine said it disabled the CANON_PP backend because it couldn't find the libieee1284 library.

Also, it sounds like you're getting close, but a poster on another thread just pointed out you can get the old Jaunty packages from [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/).  Assuming you have an Intel processor it looks like you'd want packages like *libsane-extras_1.0.19.11_ubuntu2_i386.deb*.

---

### Post by Marly on 2009-11-13
ADBrown85
thank you for suggestions, installing version 1.0.19 of libsane solved the problem. I've downloaded Jaunty packages from launchpad.

I still don't understand the warning I get from the terminal, but at least now I'm able to scan again :D

---

### Post by cscj01 on 2009-11-13
Well, things are strange here.  My scanner now works, but I'm not sure why.  Here's the scoop.

1. I installed libsane-1.0.19 using the following commands:

./config
make
sudo checkinstall -D

This installed libsane-1.0.19 in /usr/local.  I had assumed it would make a .deb package as well, but there does not seem to be one.  I suppose this is why the libsane-1.0.19 package does not show when I do a dpkg -l.

2. I followed the same procedure for xsane-0.93.  However, the install failed with a permissions failure on a usr/bin directory (I don't have the message because my terminal cache was too small, and I did a dpkg -l to see what packages were installed).

3.  I launched XSane from the Applications/Graphics/XSane menu entry and XSane came up, but the Preview menu was blank.

4.  I decided to look through usr/local directories to see if I could figure out what was happening.  I found an xsane icon in /usr/local/share/applications labeled "XSane - Scanning" which launched XSane and worked; I can scan.

5.  I found an xsane executable in usr/local/bin that also works as in 4 above.

6.  The xsane executable in usr/bin does the same as the one on the Applications menu.

7.  The dpkg -l command does not list either libsane-1.0.19 or xsane-0.93 as being installed.  That makes sense for xsane-0.93 because of the message I received when trying to install it.  However, I do not know why the libsane-1.0.19 package does not show up.

So, I am wondering about a few things.

1.  Since the xsane-0.93 package installation failed, do I have any XSane 0.93 files lying around other than in the xsane-0.93 folder on my Desktop?

2.  When a fix comes out for the XSane/Sane bug, how do I remove libsane-1.0.19 since dpkg does not show it as installed?

3.  Can I safely delete the xsane-0.93, xsane-0.93.tar.gz, and sane-backends-1.0.19 folders from my Desktop?

4.  I also have an xsane-0.996 folder on my Desktop from (I think) an extraction of the xsane-0.996.tar.gx folder (which is now in my Trash) that I must have done while I was attemptimg to install xsane-0.93.  Do I assume corecctly that I do not need to try to install xsane-0.996?

All in all, this has been educational.  I'm just not sure whether I know enough to be useful or just enough to be dangerous at this point.

---

### Post by ADBrown85 on 2009-11-13
[SIZE=2][COLOR=Red][COLOR=Black]Hmm, sounds like things are definitely a bit weird...

[/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Red][COLOR=Black]First, I should say [/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Red][COLOR=Black]that I don't have any experience with checkinstall.  Maybe someone else will come along that will know how it keeps track of everything.[/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Black]  (I understand that it calls sudo make install at some point.)

[/COLOR][/SIZE][SIZE=2]So, I'll try to comment on the other stuff...

It seems like the sticking point for all of this is finding out if XSane actually installed correctly.  Since you do have stuff in */usr/local *and since you can scan again, it seems like the needed parts did get installed correctly.  I don't know what the message during the install could have been, but it seems like you might want to increase your terminal buffer and try again.  (Or redirect the output to a file as in ***sudo make install > file.txt***.)  One thing that is really weird though is you shouldn't have a */usr/bin/xsane* file anymore.  I'm assuming you removed everything in Synaptic first?

It may help to confirm where XSane is really coming from.  [/SIZE][SIZE=2][COLOR=Red][COLOR=Black]The icon in */usr/local/share/applications* should just be calling *xsane* as if you typed it in the terminal.  ([/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Red][COLOR=Black]Actually, those .desktop files are just text files.  If you drag one into gedit, one of the lines will give you the executable.  Mine says *exec=xsane*.[/COLOR][/COLOR][/SIZE][SIZE=2])  [/SIZE][SIZE=2][COLOR=Red][COLOR=Black]You can find out which file is really being used in those cases by entering **which xsane **in a terminal.  It will print out the full path of the first xsane executable it finds in one of the directories in the PATH environment variable.  Of course, if the versions are different *Help | About* inside the application will let you know too.

Other than that, [/COLOR][COLOR=Black]when a fix comes out (which considering Oliver's message I'm not sure if that will be anytime soon), running **sudo make uninstall** will get rid of everything that install copied over.  And y[/COLOR][COLOR=Black]es you can get rid of the tar balls and their corresponding folders on your Desktop.  When you need to uninstall later you can just download them again.  If 0.93 is working and you don't want anything in 0.996 I guess you don't need that either.  (It might be worth looking through the release notes...)

[/COLOR][/COLOR][/SIZE][SIZE=2][COLOR=Red][COLOR=Black]I might have had the same problem with the preview menu with the later versions.  Installing version 0.93 did work though.  Interestingly enough, after that I tried 0.996 again and it magically still worked.  I should note that  I did uninstall from the old version's directory before I tried[/COLOR][/COLOR] a new version each time though.
[/SIZE] [SIZE=2][COLOR=Red]
[COLOR=Black]Basically I think it's good that you tried the source code route though!  It will probably come in handy someday because sometimes you need something that isn't in the repositories and doesn't have a package available.  That being said, if you get to the point where you don't want to deal with this anymore remember you can just try the Jaunty packages from Launchpad.  Apparently it worked for Marly.

Good luck,
Andy
[/COLOR][/COLOR][/SIZE]

---

### Post by cscj01 on 2009-11-14
Andy,

Let me see if I understand correctly.

In order to clear up some of this confusion, I can:

1.  un-install libsane-1.0.19;
2.  un-install XSane;
3.  Use the Jaunty packages to re-install XSane and libsane.

If I do this, should I add the Jaunty Launchpad repository to sources and install with Synaptic or download the packages from Launchpad and install them from the .debs?

Thanks.

Cecil

---

### Post by TeutonJon78 on 2009-11-15
Well, I'm having the same problem.  XSANE worked perfectly fine with 9.04 but now crashes after scanning in 9.10.  Bah.

---

### Post by cscj01 on 2009-11-18
Okay, I uninstalled XSane and libsane, then re-installed them using the Jaunty .deb packages.  Now everything works except whenever I try to quit XSane.  It will not quit.  I have to force it.  Any ideas anyone?

---

### Post by cscj01 on 2009-11-20
I just found some interesting things in /usr/lib/sane.  Although I un-installed libsane (current Karmic version 1,0,20) before installing 1.0.19, I have some files that seem to be backends for 1.0.20.

For example, I have libsane-coolscan.la, libsane-coolscan.so.1, and libsane-coolscan.so.1.0.19.  I have this same trio (la, so.1, and so.1.0.19) for every backend represented in the directory.

(1) Why would I have the ones with 1.0.19 at the end of the file names?
(2) Doesn't the install for any version of libsane just put in the la's and the so.1's?
(3) Should I just remove libane, clear the directory, and reinstall?

The reason I ask these questions is because XSane and VueScan no longer recognize my Nikon scanner, though they both did before.  I entered the result of some commands in the Hardware & Laptops forum ([http://ubuntuforums.org/showthread.php?t=1331668](http://ubuntuforums.org/showthread.php?t=1331668)).  I am in dire need of repairing this as I need to get a significant number of negatives scanned soon for a job I am doing.

Hopefully someone can shed some light on this.  I am now at the stage of knowing just enough to be really confused about a lot of things>

---

### Post by cscj01 on 2009-11-20
A little more information (I am new at this).  I can launch XSane and Vuescan from a terminal using sudo and (lo and behold), the Nikon scanner is there.  Could this be a rules issue?  Help!

---

### Post by ADBrown85 on 2009-11-24
Sorry to disappear for awhile--I had a deadline and wasn't really checking email.  I'm glad to see you got things at least halfway working though.

I'm not sure what you mean by why you're seeing the 1.0.19 versions of the backends.  Isn't that the version you have installed?

I'm afraid I don't have any familiarity with the rules things, but the other thread I was monitoring seems to have something similar.  Check out this post:

[http://ubuntuforums.org/showthread.php?p=8308683](http://ubuntuforums.org/showthread.php?p=8308683)

---

### Post by cscj01 on 2009-11-25
Andy,

See the thread below I started in Hardware & Laptops.  It is an interesting side note to this problem. I solved that one as indicated, and now everything works except having to force quit XSane each time.

[http://ubuntuforums.org/showthread.php?t=1331668](http://ubuntuforums.org/showthread.php?t=1331668)

Cecil

---

### Post by 73ckn797 on 2010-10-15
I cannot get my HP J4580 scanner to work and followed the recommendations from this thread. That did not work. Could I use the packages from Jaunty? I see here: [http://packages.ubuntu.com/jaunty/libsane](http://packages.ubuntu.com/jaunty/libsane) that I can download the packages relevant to 
**[B][SIZE=2]libsane (1.0.19-23ubuntu7)[/SIZE]** [/B]

Do you think this will work?

I have just performed a fresh install of 9.10. I began losing scanner functionality after 10.04 and completely lost it with 10.10. Will this work with 10.1o?

This is a Ubuntu/Xsane issue. The scanner works perfectly when I boot into Win XP.

---

### Post by cscj01 on 2010-10-26
> I cannot get my HP J4580 scanner to work and followed the recommendations from this thread. That did not work. Could I use the packages from Jaunty? I see here: [http://packages.ubuntu.com/jaunty/libsane](http://packages.ubuntu.com/jaunty/libsane) that I can download the packages relevant to
libsane (1.0.19-23ubuntu7)

I have Ubuntu 10.04.  This problem is maddening.  First Simple Scan worked and Xsane did not when I upgraded to 10.04 from 9.10.  I had installed libsane 1.0.19 in 9.10 to get Xsane working.  Then Simple Scan stopped working.  So, I un-installed libsane 1.0.20 and installed 1.0.19 in 10.04.  Both Simple Scan and Xsane worked for a while.  Then they quit working, and Vuescan did not even recognize my Coolsacn V ED.  So I added the Robert Ancell PPA for Simple Scan and installed his latest build.  Simple Scan and Xsane starting working again and my Nikon scanner re-appeared. Now both Xsane and Simple Scan have quit working again.

I have an open issue with Xsane that has been there since 9.10.  I don't believe anyone cares about scanning at Ubuntu.  If so, this problem would have been resolved long ago.

I still have an XP instance on my PC in a dual boot configuration.  My scanner works perfectly in XP.  Since that is the case, I can only assume the folks who work on these type of issues do not feel this is important enough to fix.

I plan to re-install libsane 1.0.19 again to see if I can scan using something.  If not, I suppose I'll have to boot XP just to scan.  Sad.

But to answer your question, yes you can use the jaunty debs to install 1.0.19.  It may or may not fix your problem, and it may or may not quit working after a bit.

---

### Post by Objekt on 2010-10-26
You're not alone.  I, too, have noticed that Xsane didn't work in Ubuntu 9.10, and is still broken in Ubuntu 10.04.  Or, if I understand the first page of this thread correctly, Ubuntu 10.04 has again done something that breaks compatibility with Xsane.

Either way, Xsane doesn't work.

I've been using an alternative scanner app, Skanlite, installed through the Ubuntu Software Center.  It works perfectly with my Brother MFC-7440N.

I can't say how Skanlite compares to Xsane.  I can't get Xsane to run, so I can't explore its features.  But I have yet to find anything I need that Skanlite doesn't do.

Because I do have Skanlite to use, I probably won't bother manually downgrading sanelib, or doing the other things necessary to make Xsane work.

Just for giggles, here's what I get when I try to run Xsane in a terminal:
```
user4@user4-desktop:~$ xsane
Xlib:  extension "RANDR" missing on display ":0.0".
The program 'xsane' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 18240 error_code 8 request_code 151 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by dangmc on 2010-10-29
> **Objekt said:**
> You're not alone.  I, too, have noticed that Xsane didn't work in Ubuntu 9.10, and is still broken in Ubuntu 10.04.  Or, if I understand the first page of this thread correctly, Ubuntu 10.04 has again done something that breaks compatibility with Xsane.

Either way, Xsane doesn't work.

I've been using an alternative scanner app, Skanlite, installed through the Ubuntu Software Center.  It works perfectly with my Brother MFC-7440N.

I can't say how Skanlite compares to Xsane.  I can't get Xsane to run, so I can't explore its features.  But I have yet to find anything I need that Skanlite doesn't do.

Because I do have Skanlite to use, I probably won't bother manually downgrading sanelib, or doing the other things necessary to make Xsane work.

Just for giggles, here's what I get when I try to run Xsane in a terminal:
```
user4@user4-desktop:~$ xsane
Xlib:  extension "RANDR" missing on display ":0.0".
The program 'xsane' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 18240 error_code 8 request_code 151 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```



Scanlite works for me: Ubuntu 10.10_x64, I'm using a Canon 8800f and I'm giving up on Xsane for a while until some of these problems get fixed. Xsane has a lot more features but not much good if it won't work!

---

### Post by 73ckn797 on 2010-10-29
> **dangmc said:**
> Scanlite works for me: Ubuntu 10.10_x64, I'm using a Canon 8800f and I'm giving up on Xsane for a while until some of these problems get fixed. Xsane has a lot more features but not much good if it won't work!

Will Scanlite do multiple pages and save in PDF? Maybe it will work for my HP All-in-One scanner. I have reverted back to 9.10 to be able to use Xsane.

---

### Post by Objekt on 2010-10-29
> **73ckn797 said:**
> Will Scanlite do multiple pages and save in PDF? Maybe it will work for my HP All-in-One scanner. I have reverted back to 9.10 to be able to use Xsane.

No, Skanlite won't output a .pdf, not to my knowledge.

However, there is another app that WILL scan multi-page docs to a multi-page .pdf: gscan2pdf.  Nifty little app.  You can even change the page order after scanning, then save the result as a .pdf.

Also, I occasionally use ScanSoft PaperPort SE 11, a Windows-only application.  I run it on a virtualized Windows XP machine through Virtualbox.  However, since I discovered gscan2pdf and skanlite, I use PaperPort infrequently.

---

### Post by dangmc on 2010-10-29
> **Objekt said:**
> No, Skanlite won't output a .pdf, not to my knowledge.

However, there is another app that WILL scan multi-page docs to a multi-page .pdf: gscan2pdf.  Nifty little app.  You can even change the page order after scanning, then save the result as a .pdf.

Also, I occasionally use ScanSoft PaperPort SE 11, a Windows-only application.  I run it on a virtualized Windows XP machine through Virtualbox.  However, since I discovered gscan2pdf and skanlite, I use PaperPort infrequently.

Objekt:
    I just tried 'gscan2pdf' It works fine except OCR function not very accurate. Anything else available for photo work except xsane?
         Thank you
Update: increasing resolution from 75 to 150 or 300 dpi increases accuracy in ocr mode

---

