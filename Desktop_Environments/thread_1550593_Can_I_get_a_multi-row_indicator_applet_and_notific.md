---
title: "Can I get a multi-row indicator applet and notification area?"
date: 2010-08-11
forum: Desktop Environments
---

### Post by The_Eddster on 2010-08-11
I have my gnome-panel set at 48 pixels, which is double the normal size. I was wondering if it would be possible to make it so that the icons in the indicator applet and notification area appear in more than one row? It would be more efficient use of the gnome-panel space and would look neater.

There is something called the [Quick lounge applet]("http://quick-lounge.sourceforge.net/") which does what I want but it only works for application launchers. In the attached screenshot I have quick lounge set up with 2 rows of application launchers, but if I could do the same thing for the indicator applet and notification area (which appear in one row) I'll be happy.

Thanks in advance

---

### Post by Vermind on 2010-12-20
Hi, [there is a patch for the notification area]("http://gnome-look.org/content/show.php/Multirow+notification+area?content=106858"). I made a [deb package of it for 64-bit machines]("http://dl.dropbox.com/u/971117/dev/gnome-panel_2.30.2-2table3_amd64.deb"). I am looking for a fix for the indicator applet.

---

### Post by Willy2 on 2010-12-30
> **Vermind said:**
> Hi, [there is a patch for the notification area]("http://gnome-look.org/content/show.php/Multirow+notification+area?content=106858"). I made a [deb package of it for 64-bit machines]("http://dl.dropbox.com/u/971117/dev/gnome-panel_2.30.2-2table3_amd64.deb"). I am looking for a fix for the indicator applet.I have tried to install that patch, but I didn't succeed. Is het possible you make a deb package for 32bit to?

> **The_Eddster said:**
> There is something called the [Quick lounge applet]("http://quick-lounge.sourceforge.net/") which does what I want but it only works for application launchers. In the attached screenshot I have quick lounge set up with 2 rows of application launchers, but if I could do the same thing for the indicator applet and notification area (which appear in one row) I'll be happy.

Thanks in advance
I'm a computernoob but in my opinion if it is possible to make something like a drawer, which is a panel in a panel with an push-up/pulldown menu layout, it should be possible to make a simular applet with a Quick-Launch-Applet lay-out.
If someone can figure it out how to make such a applet, it should be great because than you'll be able  to arrange everything in your panel just the way you want.

---

### Post by Vermind on 2010-12-30
This is already possible using [avant-window-navigator]("https://launchpad.net/~awn-testing/+archive/ppa") (awn). In awn, indicator applet and notification area both automatically change to 2 rows if you make your panel thick enough (see attached screenshot). Also, you can right click them and choose the number of rows from the preferences if you like. The only thing I miss from gnome-panel is the clock+calendar+weather+locations applet. However, it is also possible to use one avant-window-navigator with everything else, and then a small not expanded gnome-panel with only the clock thing in the corner of your screen.


Dockbarx is a great launcher/window icon applet for awn or gnome-panel.
MintMenu is a great main menu for either gnome-panel or awn.
[You can get both from the webupd8 ppa]("https://launchpad.net/~nilarimogard/+archive/webupd8"). for mintmenu for awn, you need to use [another ppa]("http://www.webupd8.org/2010/11/use-mintmenu-in-avant-window-navigator.html").

My problem with awn is that it uses noticeably more battery than gnome-panel, so I would like this to be possible with gnome-panel.

I noticed that I had modified the na-tray.c file after applying the patch, since the old patch didnt work properly for 2.30.2. Here is my patch: [http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch](http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch)
I have also attached it to this post for more permanent storage.

To patch gnome-panel with the patch do this in a terminal:
```
mkdir working-folder
cd working-folder
apt-get source gnome-panel # note sudo is not required
cd gnome-panel-*
wget http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch
patch -p1 < na-tray-multirow-2.30.2.patch

```
Now we need to edit the debian changelog to make sure that ubuntu updates will not screw this up:
```
gedit debian/changelog
```
Just add this at the top:
```
gnome-panel (1:2.30.2-2table3) maverick; urgency=low

  * Allow a multirow table of icons on thick panels

 -- Your Name <your@email.com>  Thu, 23 Sep 2010 18:13:14 +0200


```
The date and time should be current, and the version (1:2.30.2-2table3) must be later than the previous entry in the list. For me the previous entry was (1:2.30.2-1ubuntu3) so (1:2.30.2-2anything) is after it.

After this is done we can go on and compile a deb package:
```
sudo apt-get build-dep gnome-panel # make sure we have build dependencies installed
sudo apt-get install devscripts # If you have never built debian packages before
debuild # This should build the package for your machine. May take a while.
```
Note: the final command may report:
```
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1258:
running debsign failed
```
This is not dangerous, the packages are created but not signed. To install the packages, do:
```
cd ..
sudo dpkg -i gnome-panel_2.30.2-2table3_*deb
```
You only need to install the gnome-panel package. The libpanel-applet, data, dev, and doc packages are not needed.

---

### Post by Willy2 on 2011-01-01
Thanks.
I get this:```
@ ~ $ mkdir working-folder
@ ~ $ cd working-folder
@ ~/working-folder $ apt-get source gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for gnome-panel
```Maybe I can get the source from one of these pages, but I don't know which of the three packages I need or what to do with it.:
[http://packages.ubuntu.com/source/maverick/gnome-panel]("http://packages.ubuntu.com/source/maverick/gnome-panel")
[https://launchpad.net/ubuntu/+source/gnome-panel/1:2.30.2-1ubuntu3]("https://launchpad.net/ubuntu/+source/gnome-panel/1:2.30.2-1ubuntu3")

---

### Post by Vermind on 2011-01-01
Your apt/sources.list seems not to include source for regular Ubuntu repositories. You may need to start synaptic, go to Settings - Repositories, and make sure "source code" is ticked.

Alternatively you can go to [http://packages.ubuntu.com/maverick/gnome-panel](http://packages.ubuntu.com/maverick/gnome-panel)
and download the three files on the right side under "Download source package gnome-panel". The .dsc, .orig, and -ubuntu3.debian.tar.gz files should be put in working-folder, and only the ubuntu3.debian.tar.gz extracted.

---

### Post by Willy2 on 2011-01-01
> **Vermind said:**
> Your apt/sources.list seems not to include source for regular Ubuntu repositories. You may need to start synaptic, go to Settings - Repositories, and make sure "source code" is ticked.
With the source code on, I get exactly the same. Even after re-installing the panel and reboot.

> **Vermind said:**
> Alternatively you can go to [http://packages.ubuntu.com/maverick/gnome-panel](http://packages.ubuntu.com/maverick/gnome-panel)
and download the three files on the right side under "Download source package gnome-panel". The .dsc, .orig, and -ubuntu3.debian.tar.gz files should be put in working-folder, and only the ubuntu3.debian.tar.gz extracted.Doing this, I get:```
@ ~/working-folder $ cd debian
@ ~/working-folder/debian $ wget http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch
--2011-01-01 14:17:24--  http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch
Resolving dl.dropbox.com... 75.101.148.191, 174.129.33.164, 184.73.197.198, ...
Connecting to dl.dropbox.com|75.101.148.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8622 (8.4K) [text/x-diff]
Saving to: `na-tray-multirow-2.30.2.patch'

100%[======================================>] 8,622       36.5K/s   in 0.2s    

2011-01-01 14:17:25 (36.5 KB/s) - `na-tray-multirow-2.30.2.patch' saved [8622/8622]

@ ~/working-folder/debian $ patch -p1 < na-tray-multirow-2.30.2.patch
patching file applets/notification_area/na-tray.c
Hunk #1 FAILED at 33.
Hunk #2 FAILED at 48.
Hunk #3 FAILED at 194.
Hunk #4 FAILED at 216.
Hunk #5 FAILED at 223.
Hunk #6 FAILED at 235.
Hunk #7 FAILED at 248.
Hunk #8 FAILED at 498.
Hunk #9 FAILED at 515.
Hunk #10 FAILED at 543.
Hunk #11 FAILED at 570.
Hunk #12 FAILED at 736.
Hunk #13 FAILED at 813.
13 out of 13 hunks FAILED -- saving rejects to file applets/notification_area/na-tray.c.rej
```

---

### Post by Vermind on 2011-01-01
> **Willy2 said:**
> With the source code on, I get exactly the same. Even after re-installing the panel and reboot.

Sorry, I neglected to mention that you also need to click "reload" after enabling the source code part. Alternatively do sudo apt-get update.

> **Willy2 said:**
> 
Doing this, I get:```
@ ~/working-folder $ cd debian

```
Oh, it would appear that you need to first extract the orig.tar.gz, then cd there, then extract the .debian.tar.gz, then patch, like so:
```

cd  working-folder
tar xzf gnome-panel_2.30.2.orig.tar.gz
cd gnome-panel-2.30.2
tar xzf ../gnome-panel_*.debian.tar.gz
wget http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch
patch -p1 < na-tray-multirow-2.30.2.patch

```
The patch will only work in the gnome-panel-2.30.2 directory. 
Sorry for the confusion.

---

### Post by Willy2 on 2011-01-01
> **Vermind said:**
> Sorry, I neglected to mention that you also need to click "reload" after enabling the source code part. Alternatively do sudo apt-get update.I already did this myself, but it didn't make any difference.;)

> **Vermind said:**
> Oh, it would appear that you need to first extract the orig.tar.gz, then cd there, then extract the .debian.tar.gz, then patch, like so:
```

cd  working-folder
tar xzf gnome-panel_2.30.2.orig.tar.gz
cd gnome-panel-2.30.2
tar xzf ../gnome-panel_*.debian.tar.gz
wget http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch
patch -p1 < na-tray-multirow-2.30.2.patch

```
The patch will only work in the gnome-panel-2.30.2 directory. 
Sorry for the confusion.
Thanks for all the time and trouble you're puting into this.
However, my system still can't find the source. After doing exactly what you said, I got: ```
@ ~/working-folder $ sudo apt-get build-dep gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for gnome-panel
```
Than I copied the dsc file to every folder in the workspace folder and tried:```

@ ~/working-folder $ dpkg-source -x gnome-panel_2.30.2-1ubuntu3.dsc
gpgv: Signature made Fri 27 Aug 2010 10:42:35 CEST using DSA key ID A2D7D292
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./gnome-panel_2.30.2-1ubuntu3.dsc
dpkg-source: info: extracting gnome-panel in gnome-panel-2.30.2
dpkg-source: info: unpacking gnome-panel_2.30.2.orig.tar.gz
dpkg-source: info: unpacking gnome-panel_2.30.2-1ubuntu3.debian.tar.gz
dpkg-source: info: applying 01_layout.patch
dpkg-source: info: applying 03_dnd_places_link.patch
dpkg-source: info: applying 04_default_panel_config.patch
dpkg-source: info: applying 05_no_session_delay.patch
dpkg-source: info: applying 09_default_icons.patch
dpkg-source: info: applying 16_compiz_workspace_switcher.patch
dpkg-source: info: applying 17_about-ubuntu-translation.patch
dpkg-source: info: applying 18_lockdown_lock_editor.patch
dpkg-source: info: applying 25_dynamic_fusa_detection.patch
dpkg-source: info: applying 30_disable-initial-animation.patch
dpkg-source: info: applying 40_unset_menuproxy.patch
dpkg-source: info: applying 71_change_bookmark_submenu_limit_value.patch
dpkg-source: info: applying 85_disable_shutdown_on_ltsp.patch
dpkg-source: info: applying 99_ltmain_as-needed.patch
dpkg-source: info: applying 90_git_wnck_show_realize.patch
dpkg-source: info: applying 91_git_wnck_pager_update.patch
```
Than again:```

@ ~/working-folder $ sudo apt-get build-dep gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for gnome-panel
```:neutral:

---

### Post by Vermind on 2011-01-01
> **Willy2 said:**
> 
I copied the dsc file to every folder in the workspace folder and tried:```

@ ~/working-folder $ dpkg-source -x gnome-panel_2.30.2-1ubuntu3.dsc
gpgv: Signature made Fri 27 Aug 2010 10:42:35 CEST using DSA key ID A2D7D292
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./gnome-panel_2.30.2-1ubuntu3.dsc
dpkg-source: info: extracting gnome-panel in gnome-panel-2.30.2
dpkg-source: info: unpacking gnome-panel_2.30.2.orig.tar.gz
dpkg-source: info: unpacking gnome-panel_2.30.2-1ubuntu3.debian.tar.gz
dpkg-source: info: applying 01_layout.patch
dpkg-source: info: applying 03_dnd_places_link.patch
dpkg-source: info: applying 04_default_panel_config.patch
dpkg-source: info: applying 05_no_session_delay.patch
dpkg-source: info: applying 09_default_icons.patch
dpkg-source: info: applying 16_compiz_workspace_switcher.patch
dpkg-source: info: applying 17_about-ubuntu-translation.patch
dpkg-source: info: applying 18_lockdown_lock_editor.patch
dpkg-source: info: applying 25_dynamic_fusa_detection.patch
dpkg-source: info: applying 30_disable-initial-animation.patch
dpkg-source: info: applying 40_unset_menuproxy.patch
dpkg-source: info: applying 71_change_bookmark_submenu_limit_value.patch
dpkg-source: info: applying 85_disable_shutdown_on_ltsp.patch
dpkg-source: info: applying 99_ltmain_as-needed.patch
dpkg-source: info: applying 90_git_wnck_show_realize.patch
dpkg-source: info: applying 91_git_wnck_pager_update.patch
```

That looks exactly like what I get after apt-get source gnome-panel, so You could proceed with
```
cd gnome-panel-*
wget http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch
patch -p1 < na-tray-multirow-2.30.2.patch
debuild

```
Hope that works.

---

### Post by Willy2 on 2011-01-01
Thanks.
I'm almost there I guess
The first time I tried I got in the text:```
dpkg-checkbuilddeps: Unmet build dependencies: cdbs (>= 0.4.41) gnome-pkg-tools (>= 0.14) libgnome-desktop-dev (>= 2.26) libbonoboui2-dev (>= 2.1.1) liborbit2-dev (>= 1:2.12.1) libwnck-dev (>= 2.19.5) libgconf2-dev (>= 2.6.1) libecal1.2-dev (>= 1.6.0) libedataserverui1.2-dev (>= 1.11.2) gtk-doc-tools (>= 1.0) libgnome-menu-dev (>= 2.27.92) libedataserver1.2-dev (>= 1.2.0) evolution-data-server-dev libgweather-dev (>= 2.27.90) librsvg2-dev libdbus-glib-1-dev (>= 0.71) libdbus-1-dev (>= 1.1.2) network-manager-dev (>= 0.6) libnm-util-dev (>= 0.6) libpolkit-gobject-1-dev (>= 0.91) libcanberra-gtk-dev libgweather-dev
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting. 
dpkg-buildpackage: warning: (Use -d flag to override.) 
debuild: fatal error at line 1337: 
dpkg-buildpackage -rfakeroot -D -us -uc failed 
```After I installed the dependencies, I got a lot of text also:```
W: gnome-panel source: out-of-date-standards-version 3.9.0 (current is 3.9.1) 
W: gnome-panel source: configure-generated-file-in-source config.log 
W: libpanel-applet2-doc: copyright-without-copyright-notice 
W: gnome-panel-data: copyright-without-copyright-notice 
W: gnome-panel-data: desktop-command-not-in-package /usr/share/applications/gnome-panel.desktop gnome-panel 
W: gnome-panel-data: desktop-command-not-in-package /usr/share/applications/ubuntu-about.desktop yelp 
W: gnome-panel: copyright-without-copyright-notice 
W: libpanel-applet2-0: copyright-without-copyright-notice 
W: libpanel-applet2-0: package-name-doesnt-match-sonames libpanel-applet-2-0 
W: gnome-panel-dbg: copyright-without-copyright-notice 
W: libpanel-applet2-dev: copyright-without-copyright-notice 
Finished running lintian. 
Now signing changes and any dsc files... 
Could not find a signing program (pgp or gpg)! 
debuild: fatal error at line 1258: 
running debsign failed
```
Than I did: ```
 
@ ~/working-folder $ sudo dpkg -i gnome-panel_2.30.2-2table3_*deb 
[sudo] password for l: 
dpkg: error processing gnome-panel_2.30.2-2table3_*deb (--install): 
 cannot access archive: No such file or directory 
Errors were encountered while processing: 
 gnome-panel_2.30.2-2table3_*deb 
```When I look in my working-folder I see what is in the screenshot.
When I install the deb packages which are in the working-folder, and I kill and restart the panel, nothing changed.

---

### Post by Vermind on 2011-01-01
From your screenshot, I can see that the packages were indeed created. You don't have gpg, but that shouldn't matter. a simple sudo dpkg -i gnome-panel*deb in the working folder, and then killall gnome-panel should sort out notification area. This will not affect indicator applet.

If installing the packages does not work after this, then I am forced to believe that the patch did not apply correctly for some reason.

The other command with -table in it did not work, because You didn't change the version; I just gave you the commands to build it and see. The packages should be identical though. To change the version, do this:
```
cd gnome-panel-2.30.2
gedit debian/changelog

```
Please see what to put in the changelog from my original post.
After doing that, you can do
```
debuild
```
again, and should end up with some deb packages with incremented version.

---

### Post by Willy2 on 2011-01-01
Oke, I did that an than:```
@ ~/working-folder $ debuild
This package has a Debian revision number but there does not seem to be
an appropriate original tar file or .orig directory in the parent directory;
(expected one of gnome-panel_2.30.2.orig.tar.gz, gnome-panel_2.30.2.orig.tar.bz2,
gnome-panel_2.30.2.orig.tar.lzma,  gnome-panel_2.30.2.orig.tar.xz or working-folder.orig)
continue anyway? (y/n)
``` After I choose y, I get a lot of text ending with:```
dpkg-source -b working-folder
dpkg-source: error: can't build with source format '3.0 (quilt)': no orig.tar file found
dpkg-buildpackage: error: dpkg-source -b working-folder gave error exit status 255
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```No new deb packages in my working-folder but a tar.gz file called *gnome-panel_2.30.2-2table3.debian.tar.gz* I tried a few times to debuild but I got the same.

Edit: I finally managed to get the deb packages. Unfortunately, after installing them nothing changed about my notification area.
I give up for today. I'll try on another computer tomorrow or the day after. 
Thanks again for all the time and labor today.
Till later :)

Greets, Willy

---

### Post by Vermind on 2011-01-01
If your gnome-panel-2.30.2/applets/notification_area/na-tray.c
is not like the attached, then the patch has not been applied.
If the patch somehow fails, you can extract the attached file into
working-folder/gnome-panel-2.30.2/applets/notification_area.
Then run debuild again from the gnome-panel-2.30.2 directory.

Anyway, if you are willing to leave gnome-panel, the avant window navigator setup is nice too.

---

### Post by Willy2 on 2011-01-02
It worked! :p
I couldn't get it work on a tweaked Ubuntu desktop
I couldn't get it work on a Mind desktop (I've tried this on Julia)
But is does work on a sober, clean Ubuntu-desktop
Conclusion: Making this patch work, works best right after installing Ubuntu.

Thanks a lot for your patience.

> **Vermind said:**
> Anyway, if you are willing to leave gnome-panel, the avant window navigator setup is nice too.I've tried several alternatives. The reason why I still using the Gnome-panel is because I use the Gnome-panel applets. Thats why I find it quite annoying there isn't something like Quick-lounge-applet for organizing the applet icons in the Gnome-panel.

---

### Post by Vermind on 2011-01-02
> **Willy2 said:**
> It worked! :p
I couldn't get it work on a tweaked Ubuntu desktop
I couldn't get it work on a Mind desktop (I've tried this on Julia)
But is does work on a sober, clean Ubuntu-desktop
Conclusion: Making this patch work, works best right after installing Ubuntu.

Thanks a lot for your patience.

No problem. I actually have one Mint at home, if it comes with gnome-panel I may try to solve this for Mint as well and post the results. Don't hold your breath though.

---

### Post by Vermind on 2011-01-02
Hi,I tried this on Mint. Ticking the source code box in Synaptic really doesn't work, because it only enables source code for the Mint repository, not the upstream Ubuntu repositories where Mint's GNOME panel comes from. Therefore, I had to add 3 lines to /etc/apt/sources.list:
```
sudo gedit /etc/apt/sources.list
```
The lines are these:
```

deb-src http://archive.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse
```
So, basically the ones already there that mention ubuntu, but with <b>deb-src</b> in the beginning.
I never made any deb packages on the system, so the next thing I had to do was ```
sudo apt-get install devscripts
```
After ```
sudo apt-get update
mkdir working-folder
cd working-folder
apt-get source gnome-panel
```
reported this (shortened)
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'gnome-panel' packaging is maintained in the 'Bzr' version control system at:
...
dpkg-source: warning: failed to verify signature on ./gnome-panel_2.30.2-1ubuntu3.dsc
dpkg-source: info: unpacking gnome-panel_2.30.2-1ubuntu3.debian.tar.gz
...
dpkg-source: info: applying 01_layout.patch
...
dpkg-source: info: applying 91_git_wnck_pager_update.patch
```
So, all was good.
I then did
```

cd gnome-panel-2.30.2
wget http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch
patch -p1 < na-tray-multirow-2.30.2.patch

```
Which said
```

patching file applets/notification_area/na-tray.c

```
So all was good.
Then I went and changed the version:
```
gedit debian/changelog
```
I added this bit at the top of the file:
```

gnome-panel (1:2.30.2-2multirow3) maverick; urgency=low

  * Allow multiple rows of notification icons.

 -- User <user@email.com>  Sun, 2 Jan 2011 22:54:14 +0200


```
Remember the empty line before the following entry in the changelog.

Before running debuild, I remembered to get the dependencies sorted out:
```

sudo apt-get build-dep gnome-panel

```
This contained 117 new packages, which took maybe 2 minutes to download.
After that, I ran
```

debuild

```
It crunched the numbers for a while, perhaps another 2 minutes.
In the end I got
```

Now signing changes and any dsc files...
Could not find a signing program (pgp or gpg)!
debuild: fatal error at line 1258:
running debsign failed

```
This is not too fatal, and the packages were created. So I went back to working folder and installed only the gnome-panel_... package.
```

cd ..
sudo dpkg -i gnome-panel_2.30.2-2multirow3_amd64.deb

```
This was on a 64-bit system, as you can see. Finally, I restarted gnome-panel with
```

killall gnome-panel

```
And the result is visible in the attached screenshot.
Good luck for other Mint users!

---

### Post by Willy2 on 2011-01-03
Thanks for this. The mint desktop isn't at my home so I can't try it today.

I've a little question: Do you (or anybody else who read this) know by chance if it is possible to align the icons within the notification area to the right instead to the left of the area?

---

### Post by Vermind on 2011-01-03
> **Willy2 said:**
> Thanks for this. The mint desktop isn't at my home so I can't try it today.

I've a little question: Do you (or anybody else who read this) know by chance if it is possible to align the icons within the notification area to the right instead to the left of the area?

In na-tray.c, they place the icons using a call like this:
```
    gtk_container_child_set (GTK_CONTAINER (priv->table),
                             icon,
                             "left-attach", col,
                             "right-attach", col + 1,
                             "top-attach", row,
                             "bottom-attach", row + 1,
                             NULL);
```
Modifying that would cause them to be aligned differently. There is also this:
```
  gtk_table_attach_defaults (GTK_TABLE (priv->table),
                             icon,
                             cols - 1, cols,
                             rows - 1, rows);
```
I don't know which ones you would need to modify, but the first thing I would try is just flip the col values, so the first call would become:
```
    gtk_container_child_set (GTK_CONTAINER (priv->table),
                             icon,
                             "left-attach", col + 1,
                             "right-attach", col,
                             "top-attach", row,
                             "bottom-attach", row + 1,
                             NULL);
```
And the second:
```
  gtk_table_attach_defaults (GTK_TABLE (priv->table),
                             icon,
                             cols, cols -1,
                             rows - 1, rows);
```
This should in theory flip the icon arrangement to be from right to left, still laid from top to bottom in as many rows as you have.
After making the change, just run debuild again from the gnome-panel-2.30.2 directory.

---

### Post by Willy2 on 2011-01-03
Doing that, all the icons in the notification area disappeared
I tried```
if (left != col|| right != col +1 ||
``` to change in ```
if (left != col + 1 || right != col||
``` But the icons still are gone.

---

### Post by Vermind on 2011-01-03
Right,
upon closer inspection it seems that the na-tray.c adds new icons always to the last column, and when it fills up creates a new column. If we want to do the reverse, we would have to change multiple functions and it would not be fun. However, it may be possible to alter it so that when it adds an "orphan" icon on the right side, it would then also move the lowest icon(s) in the first column to the last column thus causing the first column to be the one with orphans. However, this also requires that you get your indexes and pointers straight...

---

### Post by Willy2 on 2011-01-04
Thank you for looking in to it.:)

---

### Post by akoutsoulelos on 2011-02-26
First of all thanks for this patch! Your effort is much appricated!!

I tried the steps but when running debuild I get this error:

/bin/bash ../libtool  --tag=CC   --mode=link gcc  -g -O2 -g -O2 -export-dynamic -Wl,-z,defs -Wl,-O1 -Wl,--as-needed -o gnome-panel GNOME_Panel-stubs.o GNOME_Panel-skels.o GNOME_Panel-common.o  panel-typebuiltins.o panel-marshal.o main.o panel-widget.o button-widget.o xstuff.o panel-session.o panel-compatibility.o panel.o applet.o drawer.o panel-config-global.o panel-util.o panel-gconf.o panel-properties-dialog.o panel-run-dialog.o menu.o panel-context-menu.o launcher.o panel-applet-frame.o panel-shell.o panel-background.o panel-background-monitor.o panel-stock-icons.o panel-action-button.o panel-menu-bar.o panel-menu-button.o panel-menu-items.o panel-separator.o panel-recent.o panel-action-protocol.o panel-toplevel.o panel-struts.o panel-frame.o panel-xutils.o panel-multiscreen.o panel-a11y.o panel-bindings.o panel-profile.o panel-force-quit.o panel-lockdown.o panel-addto.o panel-ditem-editor.o    ../gnome-panel/libegg/libegg.la ../gnome-panel/libpanel-util/libpanel-util.la -pthread -lbonoboui-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lbonobo-2 -lbonobo-activation -lORBit-2 -lgnome-desktop-2 -lstartup-notification-1 -lgconf-2 -lgnome-menu -ldbus-glib-1 -ldbus-1 -lpthread -lcanberra-gtk -lcanberra -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lcairo -lgio-2.0 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0   -lX11 -lXau   
libtool: link: gcc -g -O2 -g -O2 -Wl,-z -Wl,defs -Wl,-O1 -o gnome-panel GNOME_Panel-stubs.o GNOME_Panel-skels.o GNOME_Panel-common.o panel-typebuiltins.o panel-marshal.o main.o panel-widget.o button-widget.o xstuff.o panel-session.o panel-compatibility.o panel.o applet.o drawer.o panel-config-global.o panel-util.o panel-gconf.o panel-properties-dialog.o panel-run-dialog.o menu.o panel-context-menu.o launcher.o panel-applet-frame.o panel-shell.o panel-background.o panel-background-monitor.o panel-stock-icons.o panel-action-button.o panel-menu-bar.o panel-menu-button.o panel-menu-items.o panel-separator.o panel-recent.o panel-action-protocol.o panel-toplevel.o panel-struts.o panel-frame.o panel-xutils.o panel-multiscreen.o panel-a11y.o panel-bindings.o panel-profile.o panel-force-quit.o panel-lockdown.o panel-addto.o panel-ditem-editor.o -pthread -Wl,--export-dynamic  -Wl,--as-needed ../gnome-panel/libegg/.libs/libegg.a -lICE -lSM -lz ../gnome-panel/libpanel-util/.libs/libpanel-util.a /usr/lib/libbonoboui-2.so /usr/lib/libgnomecanvas-2.so /usr/lib/libgnome-2.so /usr/lib/libpopt.so /usr/lib/libart_lgpl_2.so /usr/lib/libbonobo-2.so /usr/lib/libbonobo-activation.so /usr/lib/libORBit-2.so -lgnome-desktop-2 -lstartup-notification-1 /usr/lib/libgconf-2.so -lgnome-menu -ldbus-glib-1 -ldbus-1 -lpthread -lcanberra-gtk -lcanberra /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libpangoft2-1.0.so /usr/lib/libgdk_pixbuf-2.0.so -lm /usr/lib/libpangocairo-1.0.so /usr/lib/libcairo.so /usr/lib/libgio-2.0.so /usr/lib/libpango-1.0.so /usr/lib/libfreetype.so -lfontconfig /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so /usr/lib/libgthread-2.0.so -lrt /usr/lib/libglib-2.0.so -lX11 -lXau -pthread
/usr/bin/ld: panel-multiscreen.o: undefined reference to symbol 'XRRFreeScreenResources'
/usr/bin/ld: note: 'XRRFreeScreenResources' is defined in DSO /usr/lib/libXrandr.so.2 so try adding it to the linker command line
/usr/lib/libXrandr.so.2: could not read symbols: Invalid operation
collect2: ld returned 1 exit status
make[5]: *** [gnome-panel] Error 1
make[5]: Leaving directory `/mnt/data/Development/gp-notify/gnome-panel-2.30.2/gnome-panel'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/mnt/data/Development/gp-notify/gnome-panel-2.30.2/gnome-panel'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/mnt/data/Development/gp-notify/gnome-panel-2.30.2/gnome-panel'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/mnt/data/Development/gp-notify/gnome-panel-2.30.2'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/mnt/data/Development/gp-notify/gnome-panel-2.30.2'
make: *** [debian/stamp-makefile-build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1325:
dpkg-buildpackage -rfakeroot -D -us -uc failed

Any idea?

---

### Post by rockorequin on 2011-03-26
I got the same link error and added -lXrandr to the PANEL_LIBS line in Makefile. This fixed the build problem. (But Makefile is generated by configure so if you run ./configure again it'll lose the setting so you'll have to add it to configure, probably somewhere around line 13126 where it is setting up PANEL_LIBS.)

ld seems to be trying to automatically link to the function in libXrandr.so.2 but failing on 64 bit systems. (It built fine without -lXrandr on a 32 bit system I tried.)

---

### Post by wast2006 on 2011-05-20
the patch for gnome-panel 2.32-1 (Ubuntu Natty)

---

### Post by msrinath80 on 2011-06-17
> **Vermind said:**
> This is already possible using [avant-window-navigator]("https://launchpad.net/~awn-testing/+archive/ppa") (awn). In awn, indicator applet and notification area both automatically change to 2 rows if you make your panel thick enough (see attached screenshot). Also, you can right click them and choose the number of rows from the preferences if you like. The only thing I miss from gnome-panel is the clock+calendar+weather+locations applet. However, it is also possible to use one avant-window-navigator with everything else, and then a small not expanded gnome-panel with only the clock thing in the corner of your screen.


Dockbarx is a great launcher/window icon applet for awn or gnome-panel.
MintMenu is a great main menu for either gnome-panel or awn.
[You can get both from the webupd8 ppa]("https://launchpad.net/~nilarimogard/+archive/webupd8"). for mintmenu for awn, you need to use [another ppa]("http://www.webupd8.org/2010/11/use-mintmenu-in-avant-window-navigator.html").

My problem with awn is that it uses noticeably more battery than gnome-panel, so I would like this to be possible with gnome-panel.

I noticed that I had modified the na-tray.c file after applying the patch, since the old patch didnt work properly for 2.30.2. Here is my patch: [http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch](http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch)
I have also attached it to this post for more permanent storage.

To patch gnome-panel with the patch do this in a terminal:
```
mkdir working-folder
cd working-folder
apt-get source gnome-panel # note sudo is not required
cd gnome-panel-*
wget http://dl.dropbox.com/u/971117/dev/na-tray-multirow-2.30.2.patch
patch -p1 < na-tray-multirow-2.30.2.patch

```
Now we need to edit the debian changelog to make sure that ubuntu updates will not screw this up:
```
gedit debian/changelog
```
Just add this at the top:
```
gnome-panel (1:2.30.2-2table3) maverick; urgency=low

  * Allow a multirow table of icons on thick panels

 -- Your Name <your@email.com>  Thu, 23 Sep 2010 18:13:14 +0200


```
The date and time should be current, and the version (1:2.30.2-2table3) must be later than the previous entry in the list. For me the previous entry was (1:2.30.2-1ubuntu3) so (1:2.30.2-2anything) is after it.

After this is done we can go on and compile a deb package:
```
sudo apt-get build-dep gnome-panel # make sure we have build dependencies installed
sudo apt-get install devscripts # If you have never built debian packages before
debuild # This should build the package for your machine. May take a while.
```
Note: the final command may report:
```
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1258:
running debsign failed
```
This is not dangerous, the packages are created but not signed. To install the packages, do:
```
cd ..
sudo dpkg -i gnome-panel_2.30.2-2table3_*deb
```
You only need to install the gnome-panel package. The libpanel-applet, data, dev, and doc packages are not needed.

Thank you so very much for posting the instructions for the 2.30.2 panel. It works wonderfully on my Debain Squeeze 32 bit installation. Many thanks!!!

---

