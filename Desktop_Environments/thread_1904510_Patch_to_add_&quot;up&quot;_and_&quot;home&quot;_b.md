---
title: "Patch to add &quot;up&quot; and &quot;home&quot; buttons to Nautilus toolbar"
date: 2012-01-04
forum: Desktop Environments
---

### Post by flar on 2012-01-04
When I upgraded to Oneiric, I was disappointed with the changes to Nautilus. Specifically, I didn't like the removal of the up button (up to parent folder) from the toolbar.  I was also annoyed that the reload button and the home button were removed from the toolbar.  In addition, I wanted to move the buttons to the left of the location entry.


So I made a patch to make Nautilus look like this:
[IMG]http://i84.photobucket.com/albums/k28/segaert/oddstuff2/nautilus-mod3.png[/IMG]



Instead of this:
[IMG]http://i84.photobucket.com/albums/k28/segaert/oddstuff2/nautilus-orig.png[/IMG]



It works for me, but I'm not much of a coder, so no guarantees.
Of course, others are free to modify this for their own needs.
I should note, this patch is intended for 11.10 Oneiric.  Previous versions do no need this patch because they already have this functionality.


I've made three versions of the patch that do different things. The first only adds the up button. The second adds the up and home buttons.  The third adds up, reload and home buttons. Only one is needed.  Choose the patch to download here: 

[ATTACH]210735[/ATTACH] (Up button only)
[ATTACH]210272[/ATTACH] (Up and Home buttons)
[ATTACH]210882[/ATTACH] (Up, Reload and Home buttons)



**INSTRUCTIONS:**

Make a new directory to work in, then download the nautilus source code and dependencies:

```
 mkdir nautilus-mod
cd nautilus-mod
apt-get source nautilus
sudo apt-get build-dep nautilus
```

Then go to the nautilus source directory:

```
cd nautilus-3.2.1
```

and move the nautilus-toolbar-patch.txt file to the source directory

```
mv [location of patch] .
```

Patch the source code:

```
patch -p1 < nautilus-toolbar-patch.txt 
```

If the patch is successful, build nautilus

```
./configure --prefix=/usr
make
```

Kill any running nautilus process, then install system-wide:

```
killall -KILL nautilus
sudo make install
```

---

### Post by bluexrider on 2012-01-04
Will have to give it a shot. Nice, Thanks

---

### Post by flar on 2012-01-08
So far so good.  I've been using the patched version of nautilus heavily for a week and no problems at all.

---

### Post by flar on 2012-01-12
Here is another patch the only adds the up button to the nautilus toolbar:

[ATTACH]210735[/ATTACH]


Here is the result:

[IMG]http://i84.photobucket.com/albums/k28/segaert/oddstuff2/nautilus-up.png[/IMG]

---

### Post by wojtalik on 2012-01-14
Wow! It works. It is awesome! I've been waiting for this patch for so long. Many thanks!

Question: will I have to patch nautilus again when my ubuntu will update itself to next version?

Greetings,

W.

---

### Post by flar on 2012-01-14
A new patch, this one adds the up button, the reload button, and the home button, like this:

[IMG]http://i84.photobucket.com/albums/k28/segaert/oddstuff2/nautilus-mod3.png[/IMG]

Download here:  [ATTACH]210882[/ATTACH]

---

### Post by flar on 2012-01-14
> **wojtalik said:**
> Wow! It works. It is awesome! I've been waiting for this patch for so long. Many thanks!

Question: will I have to patch nautilus again when my ubuntu will update itself to next version?

Greetings,

W.


If nautilus is updated, it will overwrite the patched version.

There are numerous ways to handle this:

You could just go into the previously patched nautilus folder and run sudo make install again.  


Or, you could pin the current version of nautilus so it never gets updated


Or, you could use checkinstall instead of sudo make install.  Make your  package have a high version number so it never gets updated.

---

### Post by cmcanulty on 2012-01-15
I followed up to the mv command then you lost me. I saved the patch to my desktop but don't know how to move it to the proper place because I don't know what the place is. I found all the nautilus files from synaptic but there are a ton of them and I don't want to screw up nautilus, thanks. It seems so weird to me that at every turn ubuntu 11.10 removes functions rather than adding or improving them. I really miss that up button.

---

### Post by flar on 2012-01-15
> **cmcanulty said:**
> I followed up to the mv command then you lost me. I saved the patch to my desktop but don't know how to move it to the proper place because I don't know what the place is. I found all the nautilus files from synaptic but there are a ton of them and I don't want to screw up nautilus, thanks. It seems so weird to me that at every turn ubuntu 11.10 removes functions rather than adding or improving them. I really miss that up button.

When you "apt-get source nautilus" it will create a new folder called nautilus-3.2.1 containing the source code for nautilus.  You have to move the patch file into that folder and apply the patch to the source code.  Then build and install.  Nothing affects your current nautilus files until you type "sudo make install"

If you want nautilus back to its original state, do "sudo make uninstall" and reinstall nautilus with this command:

```
sudo apt-get install --reinstall nautilus
```

---

### Post by |{urse on 2012-01-15
flar, this is magnificent. I really missed that up arrow lol.

---

### Post by cmcanulty on 2012-01-16
OK great I got it working, thanks

---

### Post by flar on 2012-01-18
I noticed today that there is an update for nautilus.  If you apply the update, it will overwrite your patched nautilus and you will have the crappy default toolbar again.  

If you happen update nautilus, it's easy to fix:

Method 1:  go back to the patched nautilus source folder and run "sudo make install"

Method 2: download the updated nautilus source, patch it, build it and reinstall it.  The patch works perfectly fine on the updated nautilus source code.



There are several ways to avoid this althogether, which I mentioned in a previous post.

---

### Post by kendon on 2012-01-20
this is great, i really missed those buttons. would it be hard to integrate move to trash, cut, copy and paste buttons?

---

### Post by flar on 2012-01-22
> **kendon said:**
> this is great, i really missed those buttons. would it be hard to integrate move to trash, cut, copy and paste buttons?

They should be pretty simple because all those functions are already in Nautilus.  I don't know if I'll have time to do it myself, but if I ever get around to it, I'll post a patch.

---

### Post by MeduZa on 2012-01-25
I really don't understand why the up to parent folder button has been removed .... :confused: I only use that button :(

---

### Post by sammiev on 2012-01-25
Very nice job! :)

---

### Post by flar on 2012-01-26
> **MeduZa said:**
> I really don't understand why the up to parent folder button has been removed .... :confused: I only use that button :(

Me too, that's why I sat down to make this patch.  I rarely use the back and forward buttons.  

Lately I feel like we've returned to the old days of linux, where you had to spend hours fixing little things just to make your computer usable.

---

### Post by cmcanulty on 2012-01-26
Yes at every step they either removed functions and options or made them so hard to find they might as well have been removed, the point was? Easier I think not especially for inexperienced users.

---

### Post by kendon on 2012-01-27
> **flar said:**
> They should be pretty simple because all those functions are already in Nautilus.  I don't know if I'll have time to do it myself, but if I ever get around to it, I'll post a patch.

that would be great. i basically understand how this stuff works, so maybe you could point me in the right directions (i.e. where would i look for the lines to insert etc.). would be much appreciated :D

---

### Post by flar on 2012-01-29
> **kendon said:**
> that would be great. i basically understand how this stuff works, so maybe you could point me in the right directions (i.e. where would i look for the lines to insert etc.). would be much appreciated :D

Unfortunately I have no time to work on this right now, but take a look at the patches.  The patch files have headings that identify the files that I had to change.  Below the headings it shows the lines that I added or modified.  Compare the patch files and you can probably figure out how to add more buttons.  Not sure about a Trash button though, that might take some effort.

---

### Post by Rundll on 2012-01-30
Thanks flar, gnome and ubuntu seem to be on a mission to remove functionallity and configurability when it conflicts with their interface ideas, they've changed from the free software ethos of 'extend and configure' to 'cut and restrict'.

The plus side is it creates developers out of users.

---

### Post by kendon on 2012-02-01
> **flar said:**
> Unfortunately I have no time to work on this right now, but take a look at the patches.  The patch files have headings that identify the files that I had to change.  Below the headings it shows the lines that I added or modified.  Compare the patch files and you can probably figure out how to add more buttons.  Not sure about a Trash button though, that might take some effort.

alright, i'll try some time, if i ever get something out of it i shall post it here. thanks nevertheless :D

---

### Post by SilverDeath on 2012-02-08
great work, thanks alot! :)

---

### Post by bluexrider on 2012-02-08
OOOOPS!

Ended up loosing F4 and F7 functions
That would be clutterflow and terminal

guess I need to reinstall

---

### Post by flar on 2012-02-09
> **bluexrider said:**
> OOOOPS!

Ended up loosing F4 and F7 functions
That would be clutterflow and terminal

guess I need to reinstall

You lost those functions after the patch?  I've never used F4 and F7 -- what do they do exactly?  They don't seem to do anything on my installation even without the patch.

---

### Post by bluexrider on 2012-02-10
> **flar said:**
> You lost those functions after the patch?  I've never used F4 and F7 -- what do they do exactly?  They don't seem to do anything on my installation even without the patch.
I had nautilus elementary installed.
F4 would enable clutterflow and F7 would enable a terminal within nautilus

screenshot attached after fixing


```
sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by wojtalik on 2012-02-17
This patch works fine with Ubuntu 11.10 oneiric too. Just checked.

---

### Post by Copper Bezel on 2012-02-17
Oh yes, much better. = ) Thanks flar!

---

### Post by flar on 2012-02-23
^^You're welcome !

---

### Post by barabashechka on 2012-03-15
thanks for your work!

---

### Post by timeout2k2 on 2012-03-16
GREAT WORK !!

really, productivity is back where it was during good'ol 'buntu times :p

btw. i really don't know who had the idea of putting the nav arrows in the upper right, as this is really against every other implementation of arrow keys (every browser i know of) - back in the '90s you could have set a standard doing this - now its far too late !

---

### Post by sticmou on 2012-05-02
I agree with all the previous comments.
Removing such navigation features is a pretty bad ergonomic idea.
Anyway, this is a GREAT patch.
Thank you again and again!

---

### Post by wojtalik on 2012-05-05
The patch works also with Ubuntu 12.04 LTS precise pangolin.

---

### Post by cmcanulty on 2012-05-05
Sorry I am stuck again at the move file here is what I get. The last few lines show the errors. I have 2 folders in my Home one is nautilus-3.2.1 and one nautilus-mod which has the Patch file in it. I can't figure out what I am doing wrong or follow the rest of the steps
Sorry to be so dumb
```

cmcanulty@Darcy25:~$  mkdir nautilus-mod
mkdir: cannot create directory `nautilus-mod': File exists
cmcanulty@Darcy25:~$ cd nautilus-mod
cmcanulty@Darcy25:~/nautilus-mod$ apt-get source nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'nautilus' packaging is maintained in the 'Bzr' version control system at:
https://code.launchpad.net/~ubuntu-desktop/nautilus/ubuntu
Please use:
bzr branch https://code.launchpad.net/~ubuntu-desktop/nautilus/ubuntu
to retrieve the latest (possibly unreleased) updates to the package.
Need to get 4,638 kB of source archives.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main nautilus 1:3.4.1-0ubuntu1 (dsc) [2,257 B]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main nautilus 1:3.4.1-0ubuntu1 (tar) [4,583 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main nautilus 1:3.4.1-0ubuntu1 (diff) [52.3 kB]
Fetched 4,638 kB in 4s (1,046 kB/s)
gpgv: Signature made Mon 16 Apr 2012 12:51:07 PM EDT using DSA key ID A2D7D292
gpgv: Can't check signature: public key not found
dpkg-source: warning: failed to verify signature on ./nautilus_3.4.1-0ubuntu1.dsc
dpkg-source: info: extracting nautilus in nautilus-3.4.1
dpkg-source: info: unpacking nautilus_3.4.1.orig.tar.xz
dpkg-source: info: unpacking nautilus_3.4.1-0ubuntu1.debian.tar.gz
dpkg-source: info: applying 01_lpi.patch
dpkg-source: info: applying 03_translations_list_update.patch
dpkg-source: info: applying 04_suppress_umount_in_ltsp.patch
dpkg-source: info: applying 05_desktop_menu_export.patch
dpkg-source: info: applying 06_never_exec_nonexec_launchers.patch
dpkg-source: info: applying 08_clean_session_capplet.patch
dpkg-source: info: applying 09_no-initial-fade.patch
dpkg-source: info: applying 11_copy_skipping_pager.patch
dpkg-source: info: applying 12_unity_launcher_support.patch
dpkg-source: info: applying 13_translate_unity_launcher.patch
dpkg-source: info: applying 14_bring_del_instead_ctrl_del.patch
dpkg-source: info: applying 15_use-ubuntu-help.patch
dpkg-source: info: applying 20_static_unity_quicklist.patch
dpkg-source: info: applying git-0001-Workaround-focus-issues-on-typeahead.patch
dpkg-source: info: applying zg_activity_logging.patch
dpkg-source: info: applying dont_wrap_labels_after_dots.patch
cmcanulty@Darcy25:~/nautilus-mod$ sudo apt-get build-dep nautilus
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  autoconf automake autopoint autotools-dev cdbs dh-autoreconf dh-translations
  docbook docbook-dsssl docbook-to-man gir1.2-gnomedesktop-3.0 gir1.2-gtk-2.0
  git git-man gnome-common gnome-pkg-tools gobject-introspection
  gsettings-desktop-schemas-dev gtk-doc-tools intltool jade libatk1.0-dev
  libcairo-script-interpreter2 libcairo2-dev libdbus-1-dev libdbus-glib-1-dev
  libdbusmenu-glib-dev libdee-dev liberror-perl libexempi-dev libexif-dev
  libexpat1-dev libffi-dev libfontconfig1-dev libfreetype6-dev libgail-3-dev
  libgdk-pixbuf2.0-dev libgee-dev libgirepository1.0-dev libglib2.0-dev
  libglib2.0-doc libgnome-desktop-3-dev libgtk-3-dev libgtk-3-doc
  libgtk2.0-dev libice-dev liblaunchpad-integration-3.0-dev libnotify-dev
  libpango1.0-dev libpcre3-dev libpixman-1-dev libpng12-dev libpthread-stubs0
  libpthread-stubs0-dev libsm-dev libsp1c2 libtool libunity-dev libx11-dev
  libxau-dev libxcb-render0-dev libxcb-shm0-dev libxcb1-dev libxcomposite-dev
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev
  libxft-dev libxi-dev libxinerama-dev libxml2-dev libxrandr-dev
  libxrender-dev libxt-dev libzeitgeist-dev python-scour sp
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev
  xorg-sgml-doctools xsltproc xtrans-dev zlib1g-dev
0 upgraded, 93 newly installed, 0 to remove and 1 not upgraded.
Need to get 36.4 MB of archives.
After this operation, 167 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libcairo-script-interpreter2 amd64 1.10.2-6.1ubuntu2 [62.4 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main autoconf all 2.68-1ubuntu2 [560 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main autotools-dev all 20120210.1ubuntu1 [42.4 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/main automake all 1:1.11.3-1ubuntu2 [571 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise/main liberror-perl all 0.17-1 [23.8 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise/main git-man all 1:1.7.9.5-1 [630 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise/main git amd64 1:1.7.9.5-1 [6,087 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise/main autopoint all 0.18.1.1-5ubuntu3 [604 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise/main intltool all 0.50.2-2 [52.0 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise/main dh-translations all 116 [21.6 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise/main python-scour all 0.26-3 [46.5 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise/main cdbs all 0.4.100ubuntu2 [47.6 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ precise/main libtool amd64 2.4.2-1ubuntu1 [302 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ precise/main dh-autoreconf all 5ubuntu1 [14.7 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ precise/main docbook all 4.5-4ubuntu1 [441 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ precise/main libsp1c2 amd64 1.3.4-1.2.1-47.1 [1,391 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ precise/main jade amd64 1.2.1-47.1 [297 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ precise/main docbook-dsssl all 1.79-6ubuntu1 [327 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ precise/main sp amd64 1.3.4-1.2.1-47.1 [161 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ precise/main docbook-to-man amd64 1:2.0.0-28ubuntu1 [77.6 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ precise/main gir1.2-gnomedesktop-3.0 amd64 3.4.1-0ubuntu1 [8,004 B]
Get:22 http://us.archive.ubuntu.com/ubuntu/ precise/main gir1.2-gtk-2.0 amd64 2.24.10-0ubuntu6 [243 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ precise/main gnome-common all 3.1.0-0ubuntu1 [14.6 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ precise/main gnome-pkg-tools all 0.19.1ubuntu2 [25.8 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ precise/main gobject-introspection amd64 1.32.0-1 [266 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ precise/main gsettings-desktop-schemas-dev amd64 3.4.1-0ubuntu1 [4,230 B]
Get:27 http://us.archive.ubuntu.com/ubuntu/ precise/main xsltproc amd64 1.1.26-8ubuntu1 [15.1 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ precise/main gtk-doc-tools all 1.18-2ubuntu1 [178 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ precise/main libpcre3-dev amd64 8.12-4 [232 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ precise/main zlib1g-dev amd64 1:1.2.3.4.dfsg-3ubuntu4 [165 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ precise/main libglib2.0-dev amd64 2.32.1-0ubuntu2 [1,801 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ precise/main libatk1.0-dev amd64 2.4.0-0ubuntu1 [71.4 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ precise/main libexpat1-dev amd64 2.0.1-7.2ubuntu1 [216 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ precise/main libfreetype6-dev amd64 2.4.8-1ubuntu2 [794 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ precise/main libfontconfig1-dev amd64 2.8.0-3ubuntu9 [659 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu/ precise/main xorg-sgml-doctools all 1:1.10-1 [12.0 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-core-dev all 7.0.22-1 [299 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ precise/main libxau-dev amd64 1:1.0.6-4 [10.5 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ precise/main libxdmcp-dev amd64 1:1.1.0-4 [26.9 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-input-dev all 2.1.99.6-1 [133 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-kb-dev all 1.0.5-2 [27.6 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu/ precise/main xtrans-dev all 1.2.6-2 [82.9 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ precise/main libpthread-stubs0 amd64 0.3-3 [3,258 B]
Get:44 http://us.archive.ubuntu.com/ubuntu/ precise/main libpthread-stubs0-dev amd64 0.3-3 [2,866 B]
Get:45 http://us.archive.ubuntu.com/ubuntu/ precise/main libxcb1-dev amd64 1.8.1-1 [81.6 kB]
Get:46 http://us.archive.ubuntu.com/ubuntu/ precise/main libx11-dev amd64 2:1.4.99.1-0ubuntu2 [908 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-render-dev all 2:0.11.1-2 [20.1 kB]
Get:48 http://us.archive.ubuntu.com/ubuntu/ precise/main libxrender-dev amd64 1:0.9.6-2build1 [27.5 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu/ precise/main libpng12-dev amd64 1.2.46-3ubuntu4 [207 kB]
Get:50 http://us.archive.ubuntu.com/ubuntu/ precise/main libice-dev amd64 2:1.0.7-2build1 [133 kB]
Get:51 http://us.archive.ubuntu.com/ubuntu/ precise/main libsm-dev amd64 2:1.2.0-2build1 [89.5 kB]
Get:52 http://us.archive.ubuntu.com/ubuntu/ precise/main libpixman-1-dev amd64 0.24.4-1 [257 kB]
Get:53 http://us.archive.ubuntu.com/ubuntu/ precise/main libxcb-render0-dev amd64 1.8.1-1 [20.9 kB]
Get:54 http://us.archive.ubuntu.com/ubuntu/ precise/main libxcb-shm0-dev amd64 1.8.1-1 [6,900 B]
Get:55 http://us.archive.ubuntu.com/ubuntu/ precise/main libcairo2-dev amd64 1.10.2-6.1ubuntu2 [585 kB]
Get:56 http://us.archive.ubuntu.com/ubuntu/ precise/main libdbus-1-dev amd64 1.4.18-1ubuntu1 [211 kB]
Get:57 http://us.archive.ubuntu.com/ubuntu/ precise/main libdbus-glib-1-dev amd64 0.98-1ubuntu1 [127 kB]
Get:58 http://us.archive.ubuntu.com/ubuntu/ precise/main libgdk-pixbuf2.0-dev amd64 2.26.1-1 [51.1 kB]
Get:59 http://us.archive.ubuntu.com/ubuntu/ precise/main libxft-dev amd64 2.2.0-3ubuntu2 [55.0 kB]
Get:60 http://us.archive.ubuntu.com/ubuntu/ precise/main libpango1.0-dev amd64 1.30.0-0ubuntu2 [493 kB]
Get:61 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-xext-dev all 7.2.0-3 [253 kB]
Get:62 http://us.archive.ubuntu.com/ubuntu/ precise/main libxext-dev amd64 2:1.3.0-3build1 [159 kB]
Get:63 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-xinerama-dev all 1.2.1-2 [4,966 B]
Get:64 http://us.archive.ubuntu.com/ubuntu/ precise/main libxinerama-dev amd64 2:1.1.1-3build1 [8,358 B]
Get:65 http://us.archive.ubuntu.com/ubuntu/ precise/main libxi-dev amd64 2:1.6.0-0ubuntu2 [203 kB]
Get:66 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-randr-dev all 1.4.0+git20101207.0d32bb07-0ubuntu2 [32.0 kB]
Get:67 http://us.archive.ubuntu.com/ubuntu/ precise/main libxrandr-dev amd64 2:1.3.2-2 [24.9 kB]
Get:68 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-fixes-dev all 1:5.0-2ubuntu1 [15.5 kB]
Get:69 http://us.archive.ubuntu.com/ubuntu/ precise/main libxfixes-dev amd64 1:5.0-4ubuntu4 [13.0 kB]
Get:70 http://us.archive.ubuntu.com/ubuntu/ precise/main libxcursor-dev amd64 1:1.1.12-1 [29.9 kB]
Get:71 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-composite-dev all 1:0.4.2-2 [10.5 kB]
Get:72 http://us.archive.ubuntu.com/ubuntu/ precise/main libxcomposite-dev amd64 1:0.4.3-2build1 [9,578 B]
Get:73 http://us.archive.ubuntu.com/ubuntu/ precise/main x11proto-damage-dev all 1:1.2.1-2 [8,286 B]
Get:74 http://us.archive.ubuntu.com/ubuntu/ precise/main libxdamage-dev amd64 1:1.1.3-2build1 [5,514 B]
Get:75 http://us.archive.ubuntu.com/ubuntu/ precise/main libgtk2.0-dev amd64 2.24.10-0ubuntu6 [3,858 kB]
Get:76 http://us.archive.ubuntu.com/ubuntu/ precise/main libdbusmenu-glib-dev amd64 0.6.1-0ubuntu3 [78.7 kB]
Get:77 http://us.archive.ubuntu.com/ubuntu/ precise/main libdee-dev amd64 1.0.10-0ubuntu1 [51.5 kB]
Get:78 http://us.archive.ubuntu.com/ubuntu/ precise/main libexempi-dev amd64 2.2.0-1 [659 kB]
Get:79 http://us.archive.ubuntu.com/ubuntu/ precise/main libexif-dev amd64 0.6.20-2 [349 kB]
Get:80 http://us.archive.ubuntu.com/ubuntu/ precise/main libgtk-3-dev amd64 3.4.1-0ubuntu1 [4,062 kB]
Get:81 http://us.archive.ubuntu.com/ubuntu/ precise/main libgail-3-dev amd64 3.4.1-0ubuntu1 [24.1 kB]
Get:82 http://us.archive.ubuntu.com/ubuntu/ precise/main libgee-dev amd64 0.6.4-1 [21.1 kB]
Get:83 http://us.archive.ubuntu.com/ubuntu/ precise/main libffi-dev amd64 3.0.11~rc1-5 [96.1 kB]
Get:84 http://us.archive.ubuntu.com/ubuntu/ precise/main libgirepository1.0-dev amd64 1.32.0-1 [763 kB]
Get:85 http://us.archive.ubuntu.com/ubuntu/ precise/main libglib2.0-doc all 2.32.1-0ubuntu2 [1,932 kB]
Get:86 http://us.archive.ubuntu.com/ubuntu/ precise/main libgnome-desktop-3-dev amd64 3.4.1-0ubuntu1 [41.6 kB]
Get:87 http://us.archive.ubuntu.com/ubuntu/ precise/main libgtk-3-doc all 3.4.1-0ubuntu1 [1,818 kB]
Get:88 http://us.archive.ubuntu.com/ubuntu/ precise/main liblaunchpad-integration-3.0-dev amd64 0.1.56 [8,156 B]
Get:89 http://us.archive.ubuntu.com/ubuntu/ precise/main libnotify-dev amd64 0.7.5-1 [19.6 kB]
Get:90 http://us.archive.ubuntu.com/ubuntu/ precise/main libunity-dev amd64 5.10.0-0ubuntu1 [236 kB]
Get:91 http://us.archive.ubuntu.com/ubuntu/ precise/main libxml2-dev amd64 2.7.8.dfsg-5.1ubuntu4 [804 kB]
Get:92 http://us.archive.ubuntu.com/ubuntu/ precise/main libxt-dev amd64 1:1.1.1-2build1 [490 kB]
Get:93 http://us.archive.ubuntu.com/ubuntu/ precise/main libzeitgeist-dev amd64 0.3.18-1 [21.3 kB]
Fetched 36.4 MB in 37s (975 kB/s)                                              
Extracting templates from packages: 100%
Selecting previously unselected package libcairo-script-interpreter2.
(Reading database ... 288149 files and directories currently installed.)
Unpacking libcairo-script-interpreter2 (from .../libcairo-script-interpreter2_1.10.2-6.1ubuntu2_amd64.deb) ...
Selecting previously unselected package autoconf.
Unpacking autoconf (from .../autoconf_2.68-1ubuntu2_all.deb) ...
Selecting previously unselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20120210.1ubuntu1_all.deb) ...
Selecting previously unselected package automake.
Unpacking automake (from .../automake_1%3a1.11.3-1ubuntu2_all.deb) ...
Selecting previously unselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously unselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.7.9.5-1_all.deb) ...
Selecting previously unselected package git.
Unpacking git (from .../git_1%3a1.7.9.5-1_amd64.deb) ...
Selecting previously unselected package autopoint.
Unpacking autopoint (from .../autopoint_0.18.1.1-5ubuntu3_all.deb) ...
Selecting previously unselected package intltool.
Unpacking intltool (from .../intltool_0.50.2-2_all.deb) ...
Selecting previously unselected package dh-translations.
Unpacking dh-translations (from .../dh-translations_116_all.deb) ...
Selecting previously unselected package python-scour.
Unpacking python-scour (from .../python-scour_0.26-3_all.deb) ...
Selecting previously unselected package cdbs.
Unpacking cdbs (from .../cdbs_0.4.100ubuntu2_all.deb) ...
Selecting previously unselected package libtool.
Unpacking libtool (from .../libtool_2.4.2-1ubuntu1_amd64.deb) ...
Selecting previously unselected package dh-autoreconf.
Unpacking dh-autoreconf (from .../dh-autoreconf_5ubuntu1_all.deb) ...
Selecting previously unselected package docbook.
Unpacking docbook (from .../docbook_4.5-4ubuntu1_all.deb) ...
Selecting previously unselected package libsp1c2.
Unpacking libsp1c2 (from .../libsp1c2_1.3.4-1.2.1-47.1_amd64.deb) ...
Selecting previously unselected package jade.
Unpacking jade (from .../jade_1.2.1-47.1_amd64.deb) ...
Selecting previously unselected package docbook-dsssl.
Unpacking docbook-dsssl (from .../docbook-dsssl_1.79-6ubuntu1_all.deb) ...
Selecting previously unselected package sp.
Unpacking sp (from .../sp_1.3.4-1.2.1-47.1_amd64.deb) ...
Selecting previously unselected package docbook-to-man.
Unpacking docbook-to-man (from .../docbook-to-man_1%3a2.0.0-28ubuntu1_amd64.deb) ...
Selecting previously unselected package gir1.2-gnomedesktop-3.0.
Unpacking gir1.2-gnomedesktop-3.0 (from .../gir1.2-gnomedesktop-3.0_3.4.1-0ubuntu1_amd64.deb) ...
Selecting previously unselected package gir1.2-gtk-2.0.
Unpacking gir1.2-gtk-2.0 (from .../gir1.2-gtk-2.0_2.24.10-0ubuntu6_amd64.deb) ...
Selecting previously unselected package gnome-common.
Unpacking gnome-common (from .../gnome-common_3.1.0-0ubuntu1_all.deb) ...
Selecting previously unselected package gnome-pkg-tools.
Unpacking gnome-pkg-tools (from .../gnome-pkg-tools_0.19.1ubuntu2_all.deb) ...
Selecting previously unselected package gobject-introspection.
Unpacking gobject-introspection (from .../gobject-introspection_1.32.0-1_amd64.deb) ...
Selecting previously unselected package gsettings-desktop-schemas-dev.
Unpacking gsettings-desktop-schemas-dev (from .../gsettings-desktop-schemas-dev_3.4.1-0ubuntu1_amd64.deb) ...
Selecting previously unselected package xsltproc.
Unpacking xsltproc (from .../xsltproc_1.1.26-8ubuntu1_amd64.deb) ...
Selecting previously unselected package gtk-doc-tools.
Unpacking gtk-doc-tools (from .../gtk-doc-tools_1.18-2ubuntu1_all.deb) ...
Selecting previously unselected package libpcre3-dev.
Unpacking libpcre3-dev (from .../libpcre3-dev_8.12-4_amd64.deb) ...
Selecting previously unselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.4.dfsg-3ubuntu4_amd64.deb) ...
Selecting previously unselected package libglib2.0-dev.
Unpacking libglib2.0-dev (from .../libglib2.0-dev_2.32.1-0ubuntu2_amd64.deb) ...
Selecting previously unselected package libatk1.0-dev.
Unpacking libatk1.0-dev (from .../libatk1.0-dev_2.4.0-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libexpat1-dev.
Unpacking libexpat1-dev (from .../libexpat1-dev_2.0.1-7.2ubuntu1_amd64.deb) ...
Selecting previously unselected package libfreetype6-dev.
Unpacking libfreetype6-dev (from .../libfreetype6-dev_2.4.8-1ubuntu2_amd64.deb) ...
Selecting previously unselected package libfontconfig1-dev.
Unpacking libfontconfig1-dev (from .../libfontconfig1-dev_2.8.0-3ubuntu9_amd64.deb) ...
Selecting previously unselected package xorg-sgml-doctools.
Unpacking xorg-sgml-doctools (from .../xorg-sgml-doctools_1%3a1.10-1_all.deb) ...
Selecting previously unselected package x11proto-core-dev.
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.22-1_all.deb) ...
Selecting previously unselected package libxau-dev.
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.6-4_amd64.deb) ...
Selecting previously unselected package libxdmcp-dev.
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.1.0-4_amd64.deb) ...
Selecting previously unselected package x11proto-input-dev.
Unpacking x11proto-input-dev (from .../x11proto-input-dev_2.1.99.6-1_all.deb) ...
Selecting previously unselected package x11proto-kb-dev.
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.5-2_all.deb) ...
Selecting previously unselected package xtrans-dev.
Unpacking xtrans-dev (from .../xtrans-dev_1.2.6-2_all.deb) ...
Selecting previously unselected package libpthread-stubs0.
Unpacking libpthread-stubs0 (from .../libpthread-stubs0_0.3-3_amd64.deb) ...
Selecting previously unselected package libpthread-stubs0-dev.
Unpacking libpthread-stubs0-dev (from .../libpthread-stubs0-dev_0.3-3_amd64.deb) ...
Selecting previously unselected package libxcb1-dev.
Unpacking libxcb1-dev (from .../libxcb1-dev_1.8.1-1_amd64.deb) ...
Selecting previously unselected package libx11-dev.
Unpacking libx11-dev (from .../libx11-dev_2%3a1.4.99.1-0ubuntu2_amd64.deb) ...
Selecting previously unselected package x11proto-render-dev.
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.11.1-2_all.deb) ...
Selecting previously unselected package libxrender-dev.
Unpacking libxrender-dev (from .../libxrender-dev_1%3a0.9.6-2build1_amd64.deb) ...
Selecting previously unselected package libpng12-dev.
Unpacking libpng12-dev (from .../libpng12-dev_1.2.46-3ubuntu4_amd64.deb) ...
Selecting previously unselected package libice-dev.
Unpacking libice-dev (from .../libice-dev_2%3a1.0.7-2build1_amd64.deb) ...
Selecting previously unselected package libsm-dev.
Unpacking libsm-dev (from .../libsm-dev_2%3a1.2.0-2build1_amd64.deb) ...
Selecting previously unselected package libpixman-1-dev.
Unpacking libpixman-1-dev (from .../libpixman-1-dev_0.24.4-1_amd64.deb) ...
Selecting previously unselected package libxcb-render0-dev.
Unpacking libxcb-render0-dev (from .../libxcb-render0-dev_1.8.1-1_amd64.deb) ...
Selecting previously unselected package libxcb-shm0-dev.
Unpacking libxcb-shm0-dev (from .../libxcb-shm0-dev_1.8.1-1_amd64.deb) ...
Selecting previously unselected package libcairo2-dev.
Unpacking libcairo2-dev (from .../libcairo2-dev_1.10.2-6.1ubuntu2_amd64.deb) ...
Selecting previously unselected package libdbus-1-dev.
Unpacking libdbus-1-dev (from .../libdbus-1-dev_1.4.18-1ubuntu1_amd64.deb) ...
Selecting previously unselected package libdbus-glib-1-dev.
Unpacking libdbus-glib-1-dev (from .../libdbus-glib-1-dev_0.98-1ubuntu1_amd64.deb) ...
Selecting previously unselected package libgdk-pixbuf2.0-dev.
Unpacking libgdk-pixbuf2.0-dev (from .../libgdk-pixbuf2.0-dev_2.26.1-1_amd64.deb) ...
Selecting previously unselected package libxft-dev.
Unpacking libxft-dev (from .../libxft-dev_2.2.0-3ubuntu2_amd64.deb) ...
Selecting previously unselected package libpango1.0-dev.
Unpacking libpango1.0-dev (from .../libpango1.0-dev_1.30.0-0ubuntu2_amd64.deb) ...
Selecting previously unselected package x11proto-xext-dev.
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.2.0-3_all.deb) ...
Selecting previously unselected package libxext-dev.
Unpacking libxext-dev (from .../libxext-dev_2%3a1.3.0-3build1_amd64.deb) ...
Selecting previously unselected package x11proto-xinerama-dev.
Unpacking x11proto-xinerama-dev (from .../x11proto-xinerama-dev_1.2.1-2_all.deb) ...
Selecting previously unselected package libxinerama-dev.
Unpacking libxinerama-dev (from .../libxinerama-dev_2%3a1.1.1-3build1_amd64.deb) ...
Selecting previously unselected package libxi-dev.
Unpacking libxi-dev (from .../libxi-dev_2%3a1.6.0-0ubuntu2_amd64.deb) ...
Selecting previously unselected package x11proto-randr-dev.
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.4.0+git20101207.0d32bb07-0ubuntu2_all.deb) ...
Selecting previously unselected package libxrandr-dev.
Unpacking libxrandr-dev (from .../libxrandr-dev_2%3a1.3.2-2_amd64.deb) ...
Selecting previously unselected package x11proto-fixes-dev.
Unpacking x11proto-fixes-dev (from .../x11proto-fixes-dev_1%3a5.0-2ubuntu1_all.deb) ...
Selecting previously unselected package libxfixes-dev.
Unpacking libxfixes-dev (from .../libxfixes-dev_1%3a5.0-4ubuntu4_amd64.deb) ...
Selecting previously unselected package libxcursor-dev.
Unpacking libxcursor-dev (from .../libxcursor-dev_1%3a1.1.12-1_amd64.deb) ...
Selecting previously unselected package x11proto-composite-dev.
Unpacking x11proto-composite-dev (from .../x11proto-composite-dev_1%3a0.4.2-2_all.deb) ...
Selecting previously unselected package libxcomposite-dev.
Unpacking libxcomposite-dev (from .../libxcomposite-dev_1%3a0.4.3-2build1_amd64.deb) ...
Selecting previously unselected package x11proto-damage-dev.
Unpacking x11proto-damage-dev (from .../x11proto-damage-dev_1%3a1.2.1-2_all.deb) ...
Selecting previously unselected package libxdamage-dev.
Unpacking libxdamage-dev (from .../libxdamage-dev_1%3a1.1.3-2build1_amd64.deb) ...
Selecting previously unselected package libgtk2.0-dev.
Unpacking libgtk2.0-dev (from .../libgtk2.0-dev_2.24.10-0ubuntu6_amd64.deb) ...
Selecting previously unselected package libdbusmenu-glib-dev.
Unpacking libdbusmenu-glib-dev (from .../libdbusmenu-glib-dev_0.6.1-0ubuntu3_amd64.deb) ...
Selecting previously unselected package libdee-dev.
Unpacking libdee-dev (from .../libdee-dev_1.0.10-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libexempi-dev.
Unpacking libexempi-dev (from .../libexempi-dev_2.2.0-1_amd64.deb) ...
Selecting previously unselected package libexif-dev.
Unpacking libexif-dev (from .../libexif-dev_0.6.20-2_amd64.deb) ...
Selecting previously unselected package libgtk-3-dev.
Unpacking libgtk-3-dev (from .../libgtk-3-dev_3.4.1-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libgail-3-dev.
Unpacking libgail-3-dev (from .../libgail-3-dev_3.4.1-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libgee-dev.
Unpacking libgee-dev (from .../libgee-dev_0.6.4-1_amd64.deb) ...
Selecting previously unselected package libffi-dev.
Unpacking libffi-dev (from .../libffi-dev_3.0.11~rc1-5_amd64.deb) ...
Selecting previously unselected package libgirepository1.0-dev.
Unpacking libgirepository1.0-dev (from .../libgirepository1.0-dev_1.32.0-1_amd64.deb) ...
Selecting previously unselected package libglib2.0-doc.
Unpacking libglib2.0-doc (from .../libglib2.0-doc_2.32.1-0ubuntu2_all.deb) ...
Selecting previously unselected package libgnome-desktop-3-dev.
Unpacking libgnome-desktop-3-dev (from .../libgnome-desktop-3-dev_3.4.1-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libgtk-3-doc.
Unpacking libgtk-3-doc (from .../libgtk-3-doc_3.4.1-0ubuntu1_all.deb) ...
Selecting previously unselected package liblaunchpad-integration-3.0-dev.
Unpacking liblaunchpad-integration-3.0-dev (from .../liblaunchpad-integration-3.0-dev_0.1.56_amd64.deb) ...
Selecting previously unselected package libnotify-dev.
Unpacking libnotify-dev (from .../libnotify-dev_0.7.5-1_amd64.deb) ...
Selecting previously unselected package libunity-dev.
Unpacking libunity-dev (from .../libunity-dev_5.10.0-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libxml2-dev.
Unpacking libxml2-dev (from .../libxml2-dev_2.7.8.dfsg-5.1ubuntu4_amd64.deb) ...
Selecting previously unselected package libxt-dev.
Unpacking libxt-dev (from .../libxt-dev_1%3a1.1.1-2build1_amd64.deb) ...
Selecting previously unselected package libzeitgeist-dev.
Unpacking libzeitgeist-dev (from .../libzeitgeist-dev_0.3.18-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 14 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/lilypond-changes.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-snippets.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-extending.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-learning.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-usage.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-notation.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-essay.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/music-glossary.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-contributor.info.gz'
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for libglib2.0-0 ...
Setting up libcairo-script-interpreter2 (1.10.2-6.1ubuntu2) ...
Setting up autoconf (2.68-1ubuntu2) ...
Setting up autotools-dev (20120210.1ubuntu1) ...
Setting up automake (1:1.11.3-1ubuntu2) ...
update-alternatives: using /usr/bin/automake-1.11 to provide /usr/bin/automake (automake) in auto mode.
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.9.5-1) ...
Setting up git (1:1.7.9.5-1) ...
Setting up autopoint (0.18.1.1-5ubuntu3) ...
Setting up intltool (0.50.2-2) ...
Setting up dh-translations (116) ...
Setting up python-scour (0.26-3) ...
Setting up cdbs (0.4.100ubuntu2) ...
Setting up libtool (2.4.2-1ubuntu1) ...
Setting up dh-autoreconf (5ubuntu1) ...
Setting up docbook (4.5-4ubuntu1) ...
Setting up libsp1c2 (1.3.4-1.2.1-47.1) ...
Setting up jade (1.2.1-47.1) ...
Setting up docbook-dsssl (1.79-6ubuntu1) ...
Setting up sp (1.3.4-1.2.1-47.1) ...
Setting up docbook-to-man (1:2.0.0-28ubuntu1) ...
Setting up gir1.2-gnomedesktop-3.0 (3.4.1-0ubuntu1) ...
Setting up gir1.2-gtk-2.0 (2.24.10-0ubuntu6) ...
Setting up gnome-common (3.1.0-0ubuntu1) ...
Setting up gnome-pkg-tools (0.19.1ubuntu2) ...
Setting up gobject-introspection (1.32.0-1) ...
Setting up gsettings-desktop-schemas-dev (3.4.1-0ubuntu1) ...
Setting up xsltproc (1.1.26-8ubuntu1) ...
Setting up gtk-doc-tools (1.18-2ubuntu1) ...
Setting up libpcre3-dev (8.12-4) ...
Setting up zlib1g-dev (1:1.2.3.4.dfsg-3ubuntu4) ...
Setting up libglib2.0-dev (2.32.1-0ubuntu2) ...
Setting up libatk1.0-dev (2.4.0-0ubuntu1) ...
Setting up libexpat1-dev (2.0.1-7.2ubuntu1) ...
Setting up libfreetype6-dev (2.4.8-1ubuntu2) ...
Setting up libfontconfig1-dev (2.8.0-3ubuntu9) ...
Setting up xorg-sgml-doctools (1:1.10-1) ...
Setting up x11proto-core-dev (7.0.22-1) ...
Setting up libxau-dev (1:1.0.6-4) ...
Setting up libxdmcp-dev (1:1.1.0-4) ...
Setting up x11proto-input-dev (2.1.99.6-1) ...
Setting up x11proto-kb-dev (1.0.5-2) ...
Setting up xtrans-dev (1.2.6-2) ...
Setting up libpthread-stubs0 (0.3-3) ...
Setting up libpthread-stubs0-dev (0.3-3) ...
Setting up libxcb1-dev (1.8.1-1) ...
Setting up libx11-dev (2:1.4.99.1-0ubuntu2) ...
Setting up x11proto-render-dev (2:0.11.1-2) ...
Setting up libxrender-dev (1:0.9.6-2build1) ...
Setting up libpng12-dev (1.2.46-3ubuntu4) ...
Setting up libice-dev (2:1.0.7-2build1) ...
Setting up libsm-dev (2:1.2.0-2build1) ...
Setting up libpixman-1-dev (0.24.4-1) ...
Setting up libxcb-render0-dev (1.8.1-1) ...
Setting up libxcb-shm0-dev (1.8.1-1) ...
Setting up libcairo2-dev (1.10.2-6.1ubuntu2) ...
Setting up libdbus-1-dev (1.4.18-1ubuntu1) ...
Setting up libdbus-glib-1-dev (0.98-1ubuntu1) ...
Setting up libgdk-pixbuf2.0-dev (2.26.1-1) ...
Setting up libxft-dev (2.2.0-3ubuntu2) ...
Setting up libpango1.0-dev (1.30.0-0ubuntu2) ...
Setting up x11proto-xext-dev (7.2.0-3) ...
Setting up libxext-dev (2:1.3.0-3build1) ...
Setting up x11proto-xinerama-dev (1.2.1-2) ...
Setting up libxinerama-dev (2:1.1.1-3build1) ...
Setting up libxi-dev (2:1.6.0-0ubuntu2) ...
Setting up x11proto-randr-dev (1.4.0+git20101207.0d32bb07-0ubuntu2) ...
Setting up libxrandr-dev (2:1.3.2-2) ...
Setting up x11proto-fixes-dev (1:5.0-2ubuntu1) ...
Setting up libxfixes-dev (1:5.0-4ubuntu4) ...
Setting up libxcursor-dev (1:1.1.12-1) ...
Setting up x11proto-composite-dev (1:0.4.2-2) ...
Setting up libxcomposite-dev (1:0.4.3-2build1) ...
Setting up x11proto-damage-dev (1:1.2.1-2) ...
Setting up libxdamage-dev (1:1.1.3-2build1) ...
Setting up libgtk2.0-dev (2.24.10-0ubuntu6) ...
Setting up libdbusmenu-glib-dev (0.6.1-0ubuntu3) ...
Setting up libdee-dev (1.0.10-0ubuntu1) ...
Setting up libexempi-dev (2.2.0-1) ...
Setting up libexif-dev (0.6.20-2) ...
Setting up libgtk-3-dev (3.4.1-0ubuntu1) ...
Setting up libgail-3-dev (3.4.1-0ubuntu1) ...
Setting up libgee-dev (0.6.4-1) ...
Setting up libffi-dev (3.0.11~rc1-5) ...
Setting up libgirepository1.0-dev (1.32.0-1) ...
Setting up libglib2.0-doc (2.32.1-0ubuntu2) ...
Setting up libgnome-desktop-3-dev (3.4.1-0ubuntu1) ...
Setting up libgtk-3-doc (3.4.1-0ubuntu1) ...
Setting up liblaunchpad-integration-3.0-dev (0.1.56) ...
Setting up libnotify-dev (0.7.5-1) ...
Setting up libunity-dev (5.10.0-0ubuntu1) ...
Setting up libxml2-dev (2.7.8.dfsg-5.1ubuntu4) ...
Setting up libxt-dev (1:1.1.1-2build1) ...
Setting up libzeitgeist-dev (0.3.18-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
cmcanulty@Darcy25:~/nautilus-mod$ cd nautilus-3.2.1
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.2.1$ mv ~/Home/nautilus-mod
mv: missing destination file operand after `/home/cmcanulty/Home/nautilus-mod'
Try `mv --help' for more information.
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.2.1$ mv ~/Home/nautilus-mod/
mv: missing destination file operand after `/home/cmcanulty/Home/nautilus-mod/'
Try `mv --help' for more information.
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.2.1$ /home/cmcanulty/Home/nautilus-mod/Patch
bash: /home/cmcanulty/Home/nautilus-mod/Patch: No such file or directory
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.2.1$ 

```

---

### Post by flar on 2012-05-06
^^not sure what's going on, but I think you should make a new empty directory  and try again with a fresh download of the nautilus source. 

It's always best to start nice and clean when you're applying patches and compiling from source.

---

### Post by mc4man on 2012-05-06
> **cmcanulty said:**
> Sorry I am stuck again at the move file 

cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.2.1$ [COLOR="Blue"]mv ~/Home/nautilus-mod[/COLOR]
mv: missing destination file operand after `/home/cmcanulty/Home/nautilus-mod'



The blue isn't going to do much

---

### Post by SonicSteve on 2012-05-08
thanks for this, it really bugs me having the nav buttons on the right and not having the up/parent button is nearly unbearable.

---

### Post by cmcanulty on 2012-05-08
what is the point of removing functionality just to have more empty space on toolbar?

---

### Post by wojtalik on 2012-05-12
A tip for less experienced linux users:

For current release of Ubuntu (Ubuntu 12.04) change

```
cd nautilus-3.2.1
```

to:

```
cd nautilus-3.4.1
```

---

### Post by traditionalist on 2012-05-12
Brilliant! Worked perfectly, thanks very much.

---

### Post by flar on 2012-05-15
> **wojtalik said:**
> A tip for less experienced linux users:

For current release of Ubuntu (Ubuntu 12.04) change

```
cd nautilus-3.2.1
```

to:

```
cd nautilus-3.4.1
```

Thanks for that wojtalik.  

Anyone can feel free to update the patches or instructions as needed.  I haven't updated my system in a while and I may not upgrade to 12.04 at all.

---

### Post by jat255 on 2012-05-16
Hello, I've been trying to build this patch on 11.10 so I can get the up button back, but I'm running into a problem with the patch.

When I run `patch - patch -pl <nautilus-toolbar-patch.txt pl <nautilus-toolbar-patch.txt`, I get the error:

patch: **** strip count l is not a number


Unfortunately, I don't know much about patching, so I don't know what this error means. Any suggestions?

---

### Post by cmcanulty on 2012-05-16
OK I thought I had it by changing command to 3.4.1 but now I get this error see end of code section. This really seems difficult.
```
cmcanulty@Darcy25:~$ mkdir nautilus-mod
mkdir: cannot create directory `nautilus-mod': File exists
cmcanulty@Darcy25:~$ cd nautilus-mod
cmcanulty@Darcy25:~/nautilus-mod$ apt-get source nautilus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
NOTICE: 'nautilus' packaging is maintained in the 'Bzr' version control system at:
https://code.launchpad.net/~ubuntu-desktop/nautilus/ubuntu
Please use:
bzr branch https://code.launchpad.net/~ubuntu-desktop/nautilus/ubuntu
to retrieve the latest (possibly unreleased) updates to the package.
Skipping already downloaded file 'nautilus_3.4.1-0ubuntu1.dsc'
Skipping already downloaded file 'nautilus_3.4.1.orig.tar.xz'
Skipping already downloaded file 'nautilus_3.4.1-0ubuntu1.debian.tar.gz'
Need to get 0 B of source archives.
Skipping unpack of already unpacked source in nautilus-3.4.1
cmcanulty@Darcy25:~/nautilus-mod$ sudo apt-get build-dep nautilus
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
cmcanulty@Darcy25:~/nautilus-mod$ cd nautilus-3.4.1
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.4.1$ mv /Home/cmcanulty/nautilus-modmv: missing destination file operand after `/Home/cmcanulty/nautilus-mod'
Try `mv --help' for more information.
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.4.1$ mv /Home/cmcanulty/nautilus-mod/mv: missing destination file operand after `/Home/cmcanulty/nautilus-mod/'
Try `mv --help' for more information.
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.4.1$ mv /Home/cmcanulty/nautilus-mod/Patch
mv: missing destination file operand after `/Home/cmcanulty/nautilus-mod/Patch'
Try `mv --help' for more information.
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.4.1$ 

```

here is another try this is making me feel really stupid. I don't understand the directions in this part

"Patch the source code:

Code:

patch -p1 < nautilus-toolbar-patch.txt

If the patch is successful, build nautilus

Code:

./configure --prefix=/usr
make"

 here is my next try and the patch is in that folder I can see it and open it.


```
cmcanulty@Darcy25:~$ mv /Home/cmcanulty/nautilus-mod/nautilus-3.4.1/
mv: missing destination file operand after `/Home/cmcanulty/nautilus-mod/nautilus-3.4.1/'
Try `mv --help' for more information.
cmcanulty@Darcy25:~$  mv /Home/cmcanulty/nautilus-mod/nautilus-3.4.1/Patch
mv: missing destination file operand after `/Home/cmcanulty/nautilus-mod/nautilus-3.4.1/Patch'
Try `mv --help' for more information.
cmcanulty@Darcy25:~$ ^C
cmcanulty@Darcy25:~$
```

---

### Post by satish_j on 2012-05-17
I have installed precise recently and was really disappointed to find the Reload & Up buttons missing from toolbar.
@wojtalik, i saw your post confirming that the patch is working in precise..are you using the default Unity Desktop in Precise pangolin?
@flar: Can you share the programming skill/s required to make such patches in Open-source community?
This is no less than a major contribution to the community.Hats off to you :)

---

### Post by rlcastrobh on 2012-05-18
Works on nautilus-3.4.2 thank you very much.

---

### Post by mc4man on 2012-05-18
> **cmcanulty said:**
> 

 here is my next try and the patch is in that folder I can see it and open it.


```
cmcanulty@Darcy25:~$ mv /Home/cmcanulty/nautilus-mod/nautilus-3.4.1/
mv: missing destination file operand after `/Home/cmcanulty/nautilus-mod/nautilus-3.4.1/'
Try `mv --help' for more information.
cmcanulty@Darcy25:~$  mv /Home/cmcanulty/nautilus-mod/nautilus-3.4.1/Patch
mv: missing destination file operand after `/Home/cmcanulty/nautilus-mod/nautilus-3.4.1/Patch'
Try `mv --help' for more information.
cmcanulty@Darcy25:~$ ^C
cmcanulty@Darcy25:~$
```

That mv command is truncated & is just assuming you know what to do, so forget it

Take the _nautilus-toolbar-patch.txt_ file & place it directly in ~/nautilus-mod/nautilus-3.4.1
(just drop it right in the nautilus-3.4.1 folder

Then open a terminal & go 
 ```
cd ~/nautilus-mod/nautilus-3.4.1 && patch -p1 < nautilus-toolbar-patch.txt
```

(I do this a a nautilus package build so can't give you a screen, hopefully you get what I mean...

---

### Post by cmcanulty on 2012-05-18
I still get this error

```
cmcanulty@Darcy25:~$ cd ~/nautilus-mod/nautilus-3.4.1 && patch -p1 < nautilus-toolbar-patch.txt
bash: nautilus-toolbar-patch.txt: No such file or directory
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.4.1$ 
```
I am attaching a screenshot of the nautilus folder so you can see the patch is there

---

### Post by mc4man on 2012-05-18
> **cmcanulty said:**
> I still get this error

```
cmcanulty@Darcy25:~$ cd ~/nautilus-mod/nautilus-3.4.1 && patch -p1 < nautilus-toolbar-patch.txt
bash: nautilus-toolbar-patch.txt: No such file or directory
cmcanulty@Darcy25:~/nautilus-mod/nautilus-3.4.1$ 
```
I am attaching a screenshot of the nautilus folder so you can see the patch is there

What that file "Patch" is don't know, doesn't matter, get rid of it.

Go back to post 1, download nautilus-toolbar-patch.txt, (right click > save link as in Firefox), place IT in the nautilus folder, then open a terminal & run above command

See screens - note the patch name & size - 5.5kB

Note- i'm getting crap performance on this forum tonight so won't be back - good luck

---

### Post by satish_j on 2012-05-24
well,i just applied the patch on Ubuntu 12.04,but i noticed that if i start nautilus from command using 'sudo nautilus',it shows the reload & up buttons,but if i click the Home folder from unity launcher,it shows the old styled nautilus window.
Any ideas how to intergrate this into unity launcher?

Got it..A simple restart did the remaining work..

---

### Post by flar on 2012-05-29
If someone wants to package this and create a repo, please feel free.  It would make things easier for a lot of people.  I just don't have the time right now (in fact, I haven't even had access to my main computer for two months now).

---

### Post by cmcanulty on 2012-05-29
Boy making a deb file would be great for dummies like me, thanks

---

### Post by traditionalist on 2012-05-29
Well, this worked fine the first time I did it, but I had to do it again because of an update, and I have tried twenty times in a row and I can't get it to work again!

---

### Post by kirby33 on 2012-05-31
Hello everybody!

I have write a new patch for nautilus 3.4.2 (similar to the patch of flar).
This patch adds the Up button and a toogle button for the location bar.
The shortcut <control>L is replaced by F12 and works in toggle mode.
The "Search" label icon has been removed.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=219009&stc=1&d=1338475048[/IMG]

You can download this patch here:
[ATTACH]219008[/ATTACH] (Up and Toogle Edit location buttons)

**INSTRUCTIONS:**

Make a new directory to work in, then download the nautilus source code and dependencies:

```
mkdir nautilus-mod
cd nautilus-mod
apt-get source nautilus
sudo apt-get build-dep nautilus
```Then go to the nautilus source directory:

```
cd nautilus-3.4.2
```and move the nautilus-toolbar-patch.txt file to the source directory

```
mv [location of patch] .
```Patch the source code:

```
patch -p1 < nautilus-toolbar-patch.txt 
```If the patch is successful, build nautilus

```
./configure --prefix=/usr
make
```Kill any running nautilus process, then install system-wide:

```
sudo killall -KILL nautilus
sudo make install
nautilus -q
```If you want nautilus back to its original state, do "sudo make uninstall" and reinstall nautilus with this command:
```
sudo apt-get install --reinstall nautilus
```Thanks to flar for the original patch ;)

---

### Post by satish_j on 2012-06-01
Iam looking for a patch which would let me see Devices in the side-bar.
When the side-bar is configured as tree-view,we are not able to see Devices in it for Windows partitions.Switching it to 'Places' view enables Devices view in it.

---

### Post by kirby33 on 2012-06-02
Hello
I have found a small bug with my patch on the nautilus version which not use the english language...

Therefore i have fix this issue with this patch:

[ATTACH]219093[/ATTACH]

Reinstall first the original nautilus and apply the patch again

---

### Post by sasagundul on 2012-06-07
hi, please make a deb version of the patched nautilus :D
i'm hardly able to complete all the development package dependencies :(

---

### Post by SpeedyGonsales on 2012-06-09
Last patch posted to this topic missed moving buttons to the left, and I only needed up button so I made my own patch: 	nautilus-left-up-patch-3.4.2.txt 

Its name says it all:

Buttons back, forward and up are positioned **left** of location bar. Search button is positioned right of location bar.

Only one new button is added: UP (only one button I really missed).

My thanks goes to **flar** who made original patch, **kirby33** who updated it for nautilus 3.4.2 and **nyteryder79** from topic: [[How-To] Move Nautilus 3+ Back & Forward Buttons to the Left of the Location Bar]("http://ubuntuforums.org/showthread.php?p=11501676")

Procedure is same, but if somebody is lazy:

```
mkdir nautilus-mod
cd nautilus-mod
apt-get source nautilus
sudo apt-get build-dep nautilus
cd nautilus-3.4.2

```
Download patch from forum to current directory.
```

patch -p1 < nautilus-left-up-patch-3.4.2.txt
./configure --prefix=/usr
make
sudo killall -KILL nautilus
sudo make install
nautilus -q
```

Then Alt+F2 nautilus or better, logout & login.
There is slight possibility that I'll do deb file in distant future (if guys from GNOME would be so unreasonable to not heed their most loyal and loving users :D),
but it would be smart move for somebody who have enough time to try ```
man checkinstall
``` and do it for all of us. :wink:

---

### Post by cmcanulty on 2012-06-10
I followed all the steps successfully but no change in nautilus , see screenshot.

---

### Post by SpeedyGonsales on 2012-06-10
cmcanulty, you are using breadcrumbs Path bar instead of plain location bar.

Try in menu Go->Toggle Location bar / Path bar

(F12 or Ctrl+L, depending if nautilus is patched or not).

---

### Post by cmcanulty on 2012-06-11
That gives me the path but still no up arrow

---

### Post by traditionalist on 2012-06-11
Doesn't work for me either. I get errors regardless of what I do. Very odd because the first patch published worked fine, but after the last nautilus update I could not get it to work again, and this one does not work for me either.

---

### Post by SpeedyGonsales on 2012-06-11
I once had similar problem, to everybody else app worked perfectly but I had problems.

I have not found the cause till some guy who had enough patience asked me to run something like:

```
which app_name
```

And that showed that I compiled myself that app (make; sudo make install) before (a year or more before) and installed it in /usr/local/bin, which is in my path before /usr/bin, and so it couldn't work. Then I did ```
sudo make uninstall
``` and finally all went well.

If you (successfully) compile new binary, try to start it using full path, that could eliminate part of problems.

Problems with compilation depend on packets installed and Ubuntu version, too many variables to help if no precise info what went wrong is given.

---

### Post by kirby33 on 2012-06-12
:confused:  :confused:  :confused:  :confused:  :confused:  :confused: 

It seems to be difficult to install the nautilus patch for some people...
So I have make a deb file... :( but i can not to upload the file... 

firstly the deb filetype is not supported (ok i can zip the file...) and secondly the maximum file size is 976.6KB!!! 

 :oops: my deb file needs 2.3MB

---

### Post by kirby33 on 2012-06-13
:D Hello I am back!!!

You can found here the deb file patch for nautilus 3.4.2 (Ubuntu 12.04) 32bits:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v1.0.0_i386.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v1.0.0_i386.deb)

You can found here the deb file patch for nautilus 3.4.2 (Ubuntu 12.04) 64bits:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v1.0.0_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v1.0.0_amd64.deb)

\\:D/ Thanks to Canonical Launchpad!!!

The package name is nautiluspatch

[IMG]https://launchpadlibrarian.net/107500307/nautilus.png[/IMG]

---

### Post by cmcanulty on 2012-06-13
the deb 64bit-the up button is back but no home button, thanks

---

### Post by kirby33 on 2012-06-14
:lolflag: It is not a bug, i don't have added the home button :p

My patch adds just the UP and the EDIT location bar buttons...
The keyboard shortcut Ctrl+L is replaced by F12 and works in toggle mode.
(Add yes i know... The buttons are on the right side...) 

The HOME is already in the bookmark...
Do you really needs this HOME button???

---

### Post by kirby33 on 2012-06-14
:? Today the nautilus version has changed (Ubuntu update), it is now the release 1:3.4.2-0ubuntu2

:!: My previous patch was for the nautilus release 1:3.4.2-0ubuntu1 

Therefore I have write a new version of the nautilus patch based on the latest release 1:3.4.2-0ubuntu2

Sorry, I need more time to create a deb file for the 32bits version, however the 64bits deb file is available. (the text patch is available here: [https://launchpad.net/nautiluspatchtogglelocationbar](https://launchpad.net/nautiluspatchtogglelocationbar))

To only add the UP and EDIT buttons (Ubuntu 12.04 64bits):
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatchupedit_v1.0.1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatchupedit_v1.0.1_amd64.deb)
The package name is nautiluspatchupedit

To add the UP, EDIT and HOME buttons (Ubuntu 12.04 64bits):
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatchupedithome_v1.0.1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatchupedithome_v1.0.1_amd64.deb)
The package name is nautiluspatchupedithome


Please remove the previous patch before install the new one, (and of course install only one of the two patches)...

Bye ):P

---

### Post by cmcanulty on 2012-06-14
Great now everything is there, couldn't they just make theses options? They keep removing functionality to what purpose? Thanks so much for the deb file.

---

### Post by kirby33 on 2012-06-14
Always only for the 64bits nautilus release 1:3.4.2-0ubuntu2 :

To add the UP/RELOAD/EDIT/HOME buttons (Ubuntu 12.04 64bits):
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatchupreloadedithome_v1.0.1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatchupreloadedithome_v1.0.1_amd64.deb)
The package name is nautiluspatchupreloadedithome


To add the UP/RELOAD/EDIT buttons (Ubuntu 12.04 64bits):
 [https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatchupreloadedit_v1.0.1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatchupreloadedit_v1.0.1_amd64.deb)
The package name is nautiluspatchupreloadedit

Of course... it should be better to just makes theses options... but I don't know how do that.... (I am not programmer...)

---

### Post by kirby33 on 2012-06-25
Hello I have write a new patch for the 64bits  nautilus  1:3.4.2-0ubuntu3 (precise-proposed repository)

All the toolbar buttons are now options!!! You just need to go to the nautilus preference gui (menu Edit>Preferences>Toolbar)

[IMG]https://launchpadlibrarian.net/108567742/nautiluspatch_preferences.png[/IMG]

The 64bits deb file is available here:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu3-2_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu3-2_amd64.deb)

The  text file patch is also available:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu3-2.txt](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu3-2.txt)

---

### Post by cmcanulty on 2012-06-25
wow, very cool thanks!

---

### Post by basily on 2012-06-25
Is there any solution for those of us running 32bit?

---

### Post by kirby33 on 2012-06-25
Hello basily!

you can use the same text patch file and compile it yourself
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu3-2.txt](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu3-2.txt)

I will try to compile the 32bits deb file before this weekend...
I am sorry but i use a 64bits computer to my office... :oops:

---

### Post by basily on 2012-06-25
I'm keen to try and compile, but I'm not sure how to do that. Any tips would be appreciated...

---

### Post by kirby33 on 2012-06-26
I think the 32bits deb file will be available friday... However, you can read this:

Read Me!!! How install manually the nautilus patch:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/ReadMe_src.txt](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/ReadMe_src.txt)

Of course replace[FONT=monospace] "[/FONT]nautilus-toolbar-patch.txt" by the name of the text file (nautiluspatch_3.4.2-0ubuntu3-2.txt)...

---

### Post by basily on 2012-06-27
Thanks for the tip. I almost got there, but got stuck with the dependencies:

configure: error: Package requirements (
	gail-3.0
	gnome-desktop-3.0 >= 3.0.0
	libxml-2.0 >= 2.7.8
	x11
) were not met:

No package 'gnome-desktop-3.0' found

Weird because as far as I can tell those are all installed. Anyway, I guess I'll wait till Friday or whenever you have the 32bit .deb file.

EDIT: nevermind - I must have somehow skipped the step "sudo apt-get build-dep nautilus". Compiling now...

---

### Post by mwclark4453 on 2012-06-27
Works great.

---

### Post by kirby33 on 2012-06-27
I am back!!! :cool:

The deb file for Ubuntu 12.04 32bits (with nautilus 3.4.2-0ubuntu3) is available here:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu3-2_i386.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu3-2_i386.deb)

):P

---

### Post by Sciesch on 2012-07-02
> **kirby33 said:**
> I am back!!! :cool:

The deb file for Ubuntu 12.04 32bits (with nautilus 3.4.2-0ubuntu3) is available here:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu3-2_i386.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu3-2_i386.deb)

):P

Thanks kirby33!

Just, I wish i had the buttons aligned to the left side, anyway, good work :)

&#8364;: After reboot, nautilus won't start again for me with this patch :(

&#8364;: Ony trying to build flar's patch i get this error:

```


configure: error: Package requirements (
	gail-3.0
	gnome-desktop-3.0 >= 3.0.0
	libxml-2.0 >= 2.7.8
	x11
) were not met:

No package 'gnome-desktop-3.0' found

```

---

### Post by kirby33 on 2012-07-02
Hello Sciesch
I don't have well understand... The deb file does not work on your computer, or you are just not able to compile the patch?

If the deb file does not work: check if the executable files /usr/bin/glib-compile-schemas and /usr/lib/dconf/dconf-service exist...

I think the flar patch does not work on the source code of nautilus 3.4.2-0ubuntu3...
The flar patch was for the older nautilus release!!

My patch is based on the original nautilus 3.4.2-0ubuntu3 release... Therefore try in a first time to compile my release...

if you want move the icon to the left side, you just need to change one line of the source code.

About your dependencies issues: check if you have all these repositories in your file /etc/apt/sources.list:
```
deb http://archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ precise universe
deb-src http://archive.ubuntu.com/ubuntu/ precise universe
deb http://archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates universe
deb http://archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

Good luck ;)

---

### Post by kirby33 on 2012-07-02
You can check which nautilus release you use with this command:
```
apt-get changelog nautilus | grep ^nautilus | head -1
```My patch is for the release: 1:3.4.2-0ubuntu3

---

### Post by kirby33 on 2012-07-02
Hello Sciesch,

I think you probably need to install the following package:

libgail-3-dev
libxml2-dev
libgnome-desktop-3-dev
libx11-dev

```
sudo apt-get install libgail-3-dev libxml2-dev libgnome-desktop-3-dev libx11-dev
```;)

---

### Post by Sciesch on 2012-07-04
> **kirby33 said:**
> Hello Sciesch
I don't have well understand... The deb file does not work on your computer, or you are just not able to compile the patch?

If the deb file does not work: check if the executable files /usr/bin/glib-compile-schemas and /usr/lib/dconf/dconf-service exist...

I think the flar patch does not work on the source code of nautilus 3.4.2-0ubuntu3...
The flar patch was for the older nautilus release!!

My patch is based on the original nautilus 3.4.2-0ubuntu3 release... Therefore try in a first time to compile my release...

if you want move the icon to the left side, you just need to change one line of the source code.

About your dependencies issues: check if you have all these repositories in your file /etc/apt/sources.list:
```
deb http://archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise main restricted
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ precise universe
deb-src http://archive.ubuntu.com/ubuntu/ precise universe
deb http://archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates universe
deb http://archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

Good luck ;)

Hey kirby33, 
didn't know that about flar's patch. 

I'm trying your .deb again now, it worked for a while the last time and then suddenly nautilus would not start at all. 

If I encounter the mistake again, i'll check the error message and post it here :)

---

### Post by fenario on 2012-07-05
Hi

It looks like to me that you added the word Home to the path;
if you use ~ then there is no need for /home/cmcanulty, it replaces that

so from wherever you are you can use ~
and the . (dot) means "here in this folder"

so once you are inside the nautilus-3.2.1 directory your command would be like so:
mv ~/nautilus-mod/nautilus-toolbar-patch.txt .

if you just copy and paste this, she'll be apples
hope that does it
i was not as lucky as non of the dependencies are satisfiable
anyway good luck to you
Fenario

---

### Post by fenario on 2012-07-05
hi cmcanulty

from within nautilus-3blahblah source folder issue this command:
**mv ~/nautilus-mod/nautilus-toolbar-patch.txt .**

good luck

fen

---

### Post by fenario on 2012-07-05
Sorry cmcanulty the thread has changed, I should have read the whole lot before answering.....anyway

I'm in Oneiric and all my dependencies are impossible
is there a deb patch for nautilus 3.2.1 ?
Would anyone care to do one for this version, the highest in oneiric

Thanks

---

### Post by fenario on 2012-07-13
> **fenario said:**
> Sorry cmcanulty the thread has changed, I should have read the whole lot before answering.....anyway

I'm in Oneiric and all my dependencies are impossible
is there a deb patch for nautilus 3.2.1 ?
Would anyone care to do one for this version, the highest in oneiric

Thanks

Well on the strength of your patch I reinstalled to Ubuntu 12
and guess what, the patch doesn't do a thing; there is no difference at all. 
The files are in the local share folder. 
I have the proper version of both the patch and nautilus.

Any ideas what's gone amiss here? Any dependencies that are not mentioned?
Any special procedures after install?

It's a big flop after all night working;
but hoping for some answers
thanks 
fen

---

### Post by kirby33 on 2012-07-16
Hello fenario!
If you have properly install the nautilus patch, now you can toggle between the button bar path and the text bar path using only the F12 button (instead of Ctrl+L)

With the patch, F12 works in toggle mode... Each time you press the F12 button, the path bar toggle between the button and text mode...

If you want to add some buttons in the toolbar, from the nautilus window go to Edit>Preferences...  And go to the Toolbar tab. In this new tab you can to select the icon that you want to use.

;)

---

### Post by kirby33 on 2012-07-16
If you use the deb file, the only one dependence that you need is the nautilus package 1:3.4.2-0ubuntu3...

The others dependencies are needed only if you try to compile the patch yourself ;)

This is a snapshot of the preference menu:

[IMG]https://launchpadlibrarian.net/108567742/nautiluspatch_preferences.png[/IMG]

---

### Post by cmcanulty on 2012-07-16
Just a suggestion to make the computer icon look like a computer rather than a hard drive.Nice work, I hope they make these part of the main nautilus, it is so obvious these should be available on every nautilus install.

---

### Post by kirby33 on 2012-07-17
I know for the computer icon.... :( But i don't found it in the available GTK toolbar object...

Maybe there is a GTK expert here? 
In the function  g_object_new () , the GTK_STOCK_HARDDISK value gives the hard drive icon... But what is the keyword for the computer icon?

I have searched without success... :sad:

---

### Post by cmcanulty on 2012-07-17
In my /user/share/pixmaps there are 2;
gnome-computer
gnome-laptop
and in /user/share/pixmaps/other several more. If you want I can email them to you
My favorite is in /user/share/icons/gnome/48x48/devices/computer.png
see screenshot for that one

---

### Post by kirby33 on 2012-07-17
Thank you but i know where are these icons... It is not the issue...

GTK use some predefine object for the toolbar...
All these objects are defined here:
[http://developer.gnome.org/gtk/2.24/gtk-Stock-Items.html](http://developer.gnome.org/gtk/2.24/gtk-Stock-Items.html)

But there is no object with a computer in this list...

---

### Post by cmcanulty on 2012-07-17
OK sorry I didn't know that. They really keep removing stuff and making everything worse.

---

### Post by kirby33 on 2012-07-17
We can probably to add the computer icon but i don't know how to do that....

When I replace GTK_STOCK_HARDDISK by "computer" there is no icon :-k

However, I am able to add the computer icon in the side bar with this keyword but no in the toolbar...

Maybe somebody has an idea?

---

### Post by fenario on 2012-07-20
> **kirby33 said:**
> Hello fenario!
If you have properly install the nautilus patch, now you can toggle between the button bar path and the text bar path using only the F12 button (instead of Ctrl+L)

With the patch, F12 works in toggle mode... Each time you press the F12 button, the path bar toggle between the button and text mode...

If you want to add some buttons in the toolbar, from the nautilus window go to Edit>Preferences...  And go to the Toolbar tab. In this new tab you can to select the icon that you want to use.

;)

Thanks mate

i only just got it working and i'm extremely happy about it.
the deb file did not install properly, all it did is deposit the patched nautilus and it's xml file
it ought to have replaced the originals but it did not !

does anyone know what went wrong here?

I found out by nosing through the deb file and then check that it was in the path like inside the deb file; yes it was.
so i did this:

made a folder /usr/orig
moved the original nautilus from /urs/bin to  /usr/orig
moved patched nautilus into /usr/bin/
moved /usr/share/glib-2.0/schemas/org.gnome.nautilus.gschema.xml to  /usr/orig
moved patched xml to /usr/share/glib-2.0/schemas/

and presto...it worked
quite amazing to have that menu entry as well

thanks guys for your effort; well done
and well appreciated

fenario

---

### Post by cmcanulty on 2012-07-20
This may interest everyone. Apparently the new gnome release will have even less for nautilus. What is the point of continually removing functionality  in order to have more empty space?!
[http://www.omgubuntu.co.uk/2011/11/latest-gnome-3-nautilus-mock-ups-point-to-refined-look]("http://www.omgubuntu.co.uk/2011/11/latest-gnome-3-nautilus-mock-ups-point-to-refined-look")

---

### Post by fenario on 2012-07-20
> **cmcanulty said:**
> This may interest everyone. Apparently the new gnome release will have even less for nautilus. What is the point of continually removing functionality  in order to have more empty space?!
[http://www.omgubuntu.co.uk/2011/11/latest-gnome-3-nautilus-mock-ups-point-to-refined-look]("http://www.omgubuntu.co.uk/2011/11/latest-gnome-3-nautilus-mock-ups-point-to-refined-look")

Well said cmcanulty

It looks like there's a need for a granny version and one for us enthusiasts.

For now PINNING is the go. Nautilus is now pinned (locked version in synaptic) and kmix pinned to v.4.4.5 because you loose the true mixer window,:D and the list may go on; I might even revert firefox to v.3.24, it's already down to v.10. 

Some applets in gnome panel I pinched from Lucid and they work: netspeed, knetload, kkbswitch (with flags); that is good news, and! my favourite (because it has 3 accessible speeds) downloader from lucid d4x works again in 12.04. 

But the notification nor system tray have a battery applet and the complete indicator takes too much space; it never warns me anyway if I forget the mains plug. So I use gkrellm tweaked to warn me with a serious Brittish voice when activated.

And just for the sake of keeping our beloved gnome panel and nautilus
I keep Lucid going and I'll pack it with software before it expires and keep the whole 32 GB repository of Lucid with me at home.

For folks with older computers: I found out that xorg functions soooo much better with the 2.6.32-*-generic kernels, it works under 12.04 and gets glxgears from 50 to 500 fps. 
All the 3.*** kernels are now beyond my 2004 laptop.

12.04 needs a lot of attention and changes
so wishing you all successful tweaking
greets
fenario [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by kirby33 on 2012-07-23
Hello fenario

I am interesting by your feedback... How do you intall the nautiluspatch? Do you use the Ubuntu Software Center? 

If theory the patch (deb file) copy the new files "nautilus" and "org.gnome.nautilus.gshema.xml" in /usr/local/nautiluspatch_3.4.2-0ubuntu3-2/

After the postinst scipt creates a backup of the original files "nautilus" and "org.gnome.nautilus.gshema.xml" and replaces these files...

Finally /usr/bin/glib-compile-schemas is executed... This command updates the gnome registry (dconf variables)

From your description, i understand the postinst debian script is never executed...

If something does not work, i am interesting to solve the issue... But on my computer everything is ok :confused: 

Maybe there is an error message somewhere?

---

### Post by flar on 2012-07-25
> **cmcanulty said:**
> This may interest everyone. Apparently the new gnome release will have even less for nautilus. What is the point of continually removing functionality  in order to have more empty space?!
[http://www.omgubuntu.co.uk/2011/11/latest-gnome-3-nautilus-mock-ups-point-to-refined-look]("http://www.omgubuntu.co.uk/2011/11/latest-gnome-3-nautilus-mock-ups-point-to-refined-look")

This is why I've moved on to Linux Mint and the Mate desktop.  I can't believe what's happened to Gnome and Ubuntu lately. I've been on Ubuntu since the days of Warty Warthog, over 7 years!

You guys will have to depend on Kirby for any updates.

---

### Post by fenario on 2012-07-26
> **kirby33 said:**
> Hello fenario

I am interesting by your feedback... How do you intall the nautiluspatch? Do you use the Ubuntu Software Center? 

If theory the patch (deb file) copy the new files "nautilus" and "org.gnome.nautilus.gshema.xml" in /usr/local/nautiluspatch_3.4.2-0ubuntu3-2/

After the postinst scipt creates a backup of the original files "nautilus" and "org.gnome.nautilus.gshema.xml" and replaces these files...

Finally /usr/bin/glib-compile-schemas is executed... This command updates the gnome registry (dconf variables)

From your description, i understand the postinst debian script is never executed...

If something does not work, i am interesting to solve the issue... But on my computer everything is ok :confused: 

Maybe there is an error message somewhere?

Hi Kirby

Thanks for replying.

here is what I did:
before installing I shut down nautilus
the package was downloaded from launchpad
double clicked to install
gdebi gtk asked for password and I gave it
so you would not expect permission issues
no complaints when installing
but no entry in var/log/apt/history
it made folder /usr/local/nautiluspatch****/
it put the new nautilus and xml in there
it created backup folder in there
in the backup there are the two original files
so it did all that
but it did not replace the originals with the patched ones

so then i rebooted and it was still the old nautilus
next 
reinstalled nautilus patch
moved nautilus from /urs/bin to  /usr/orig
moved patched nautilus into /usr/bin/
moved /usr/share/glib-2.0/schemas/org.gnome.nautilus.gschema.xml to  /usr/orig
moved patched xml to /usr/share/glib-2.0/schemas/

and.....it worked; eureka!

was the dconf update necessary?
it worked without.
I just did that today anyway
is dconf-editor needed to do this registry updating?
because I did not have that installed at the time

by the way, unrelated to this,
I had a lot of bugs with compiz 9.7.8
tried previous versions
found out that 9.4 was buggy too
but 9.6 seems to work best

again.....downgrading and pinning
have to ask father Christmas for an upgraded laptop
though I like the older tougher cases better.

greetings 
fen

---

### Post by flar on 2012-08-01
I take back what I said earlier.  Not about moving away from Ubuntu (still doing that) but I will create a new patch just like the old ones for 12.04.

It turns out that the caja file manager from the Mate desktop does not make previews of NEF (nikon raw format) files, which I can't live without.  Rather than figure out how to make caja show thumbnails, I'll use the more modern nautilus (patched to have an up button, of course).  I won't get around to this until I'm back from vacation in a couple weeks.

---

### Post by kirby33 on 2012-08-02
Hello fenario,
I don't know where is the issue on your computer... However yes the dconf update is necessary... I think this step is automatically performed when you logout your gnome session (after coying the org.gnome.nautilus.gshema.xml file).
The command /usr/bin/glib-compile-schemas is used to force the update without logout the session. So maybe this can explain why your workaround works.
But i don't know why the patch does not work properly on your computer :confused:
I have test the patch on 5 computers and everything is ok for me...

Do you have try on another computer? Or maybe somebody has the same issue?

---

### Post by tessem11 on 2012-08-03
you could also use Ubuntu tweak. I believe that will work.:popcorn:

---

### Post by cmcanulty on 2012-08-05
today my nautilus patch is gone and when I try to install it I get the error on screenshot. 2nd screenshot is of synaptic showing I do have that version of nautilus installed. What gives? Ok I figured out I need to revert to the old nautilus but I can't install the old one as it says newer version already installed. Is there a way to keep the deb files current so this doesn't constantly happen or maybe I just just try another file manager but I do like nautilus and am used to it. Now I also read even more functions are due to be removed, see links below.
[http://ubuntuforums.org/showthread.php?p=12151780#post12151780]("http://ubuntuforums.org/showthread.php?p=12151780#post12151780")
[http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll]("http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll")

---

### Post by rCXer on 2012-08-07
Thanks flar.  Patch works perfectly in percise.

---

### Post by cmcanulty on 2012-08-11
I am not knowledgeable enough to understand all this but would the link below make it easier to keep the patch current with each new nautilus?

[http://raphaelhertzog.com/2012/08/08/how-to-use-quilt-to-manage-patches-in-debian-packages/]("http://raphaelhertzog.com/2012/08/08/how-to-use-quilt-to-manage-patches-in-debian-packages/")

---

### Post by kirby33 on 2012-08-13
Hello everybody!
I have updated the patch for nautilus 3.4.2-0ubuntu4

The 32bits deb file is already available here:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu4-1_i386.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu4-1_i386.deb)

The text patch file is available here:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu4-1.txt](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu4-1.txt)

The 64bits deb patch file is not yet available, sorry. I will make it after my holidays...
Regards,
kirby

---

### Post by kirby33 on 2012-08-16
The 64bits nautiluspatch deb file (for nautilus 3.4.2-0ubuntu4) is available here:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu4-1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu4-1_amd64.deb)

;)

---

### Post by cmcanulty on 2012-08-16
thanks new patch for 64 bit works great!

---

### Post by mnrl on 2012-08-20
how to add zoom in/out button to nautilus toolbar? Does anyone know?

---

### Post by cmcanulty on 2012-08-20
+1 would be very useful

---

### Post by DarkDead on 2012-08-22
> **kirby33 said:**
> 
The 32bits deb file is already available here:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu4-1_i386.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu4-1_i386.deb)


The 32bits patch is working good here. Thanks a lot kirby, this is just what I was looking for (damn Nautilus developers :mad:).

---

### Post by maursund on 2012-08-22
> **cmcanulty said:**
> +1 would be very useful

yes, please

---

### Post by kirby33 on 2012-08-23
I think I am able to add the zoom in/out buttons...
I will think about it for a future release... But I am too busy now.
;-)

---

### Post by N0rbert on 2012-09-22
Hello, I use 12.04, Nautilus (and its dependencies) was updated today to version 3.4.2-0ubuntu4.

I think we can create a PPA with patched version of Nautilus. 
I tried to create a package with checkinstall, but it conflicts with other Nautilus packages. Without checkinstall we can't Lock/Pin nautilus package version.

I use TortoiseHg with Nautilus. As far I know TortoiseHg can't work with Nemo and Athena forks of Nautilus.

---

### Post by gattanegra on 2012-09-22
My friend, this just made my day. I m so happy to have that home/up button patch!

:KS:KS:KS:KS:KS

---

### Post by Peneus on 2012-09-27
I really would like to add the following buttons: Copy, Paste, and New Tab. 
Is that possible?

> **kirby33 said:**
> I think I am able to add the zoom in/out buttons...
I will think about it for a future release... But I am too busy now.
;-)

---

### Post by N0rbert on 2012-09-28
> **kirby33 said:**
> The 64bits nautiluspatch deb file (for nautilus 3.4.2-0ubuntu4) is available here:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu4-1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu4-1_amd64.deb)

;)
Thank you, **kirby33**.
I think it's time to create a ppa for auto-updating.
I pinned both nautilus and nautiluspatch in Synaptic on my system.

---

### Post by kirby33 on 2012-11-06
Hello...

Sorry, I am really too busy for add new features in the nautiluspatch... :(

In fact, a ppa is a  good idea... But I don't have understand how to create a ppa... :confused:
If somebody can to explain me how to do that, that could be nice...

Moreover, my nautiluspatch package works fine but when you install it, It is specified the package is not authenticated :(  Somebody knows how to solve this issue?

(I have added the 64bits nautiluspatch release for nautilus v3.4.2-0ubuntu5)

[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu5-1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu5-1_amd64.deb)

---

### Post by cmcanulty on 2012-11-06
thanks! I inadvertently updated Nautilus yesterday and was bumbed these were gone

---

### Post by cmcanulty on 2012-11-06
you have to go to preferences in nautilus and click the toolbar tab

---

### Post by kirby33 on 2012-11-06
Exact! you have to go to the preferences in nautilus and click the toolbar tab.

Thank you cmcanulty! You do the hot line :mrgreen: :wink:

[IMG]https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_preferences.png[/IMG]

---

### Post by parazythum on 2012-11-09
No joy with the latest amd64 version of the patch :(

Here is what I get :
```
nautilus &
[1] 5845
Initializing nautilus-gdu extension
(nautilus:5845): GLib-GIO-ERROR **: Settings schema 'org.gnome.nautilus.preferences' does not contain a key named 'show-label-search-icon-toolbar'

[1]+  Trappe pour point d'arrêt et de trace              nautilus

```

I used the dconf editor and the key show-label-search-icon-toolbar is already there...

In my Precise the nautilus version is 1:3.4.2-0ubuntu5

---

### Post by t.h.w. on 2012-11-16
Hi flar,
Downloaded you patch and followed your instructions as in post #1 and everything is fine, as far I can see :) 
Thanks!

---

### Post by t.h.w. on 2012-11-16
> **kirby33 said:**
> Exact! you have to go to the preferences in nautilus and click the toolbar tab.

Thank you cmcanulty! You do the hot line :mrgreen: :wink:

[IMG]https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_preferences.png[/IMG]

Hi Kirby33,
After the initial txt-patch from flar I used your txt-patch (12.04) but do not have a tab 'toolbar' in preferences. Any sugestions?

---

### Post by t.h.w. on 2013-01-06
SOLVED

I did not use the right patch and/or right version of Nautilus when using the patch... ;)

> **t.h.w. said:**
> Hi Kirby33,
After the initial txt-patch from flar I used your txt-patch (12.04) but do not have a tab 'toolbar' in preferences. Any sugestions?


Ok, now it is learning-time to get the buttons first and than the location bar, instead of the other way around... will try to figure this out myself :lolflag:

[ATTACH]229661[/ATTACH]

---

### Post by Dopameen on 2013-02-06
Why does downloading the text attachements requires you to log on?!?  ](*,)

Also, the necessity of having to redo your tweaks all over again every time a new (security) patch comes out (which is happening as I'm writing) for an application that is remotely dependent forces people not to keep their system up to date. Way to go Ubuntu! ](*,)

("The message you have entered is too short. Please lengthen your message to at least 1 characters." because yahooapis.com is blocked by my Adblock. Another thumbs down for Ubuntu! ](*,))

---

### Post by DaOg75 on 2013-02-15
Many thanks to flar and kirby55 for the patch. I am able to run flars with no problems. Using 12.04.1 x64, GNOME nautilus 3.4.2. Great job.

---

### Post by jarodd on 2013-02-16
Great thanks to you. I am a noob but I follow the first post, and I finally find again parent button. You rocks bro !!! \\:D/

---

### Post by wim.glenn on 2013-02-19
I loved this patch, but it looks like it's not working anymore:

```
wim@wim-zenbook:~/Dropbox$ sudo dpkg -i nautiluspatch_v3.4.2-0ubuntu5-1_amd64.deb 
dpkg: regarding nautiluspatch_v3.4.2-0ubuntu5-1_amd64.deb containing nautiluspatch, pre-dependency problem:
 nautiluspatch pre-depends on nautilus (<< 1:3.4.2-0ubuntu6)
  nautilus is installed, but is version 1:3.5.90.really.3.4.2-0ubuntu4.1.

dpkg: error processing nautiluspatch_v3.4.2-0ubuntu5-1_amd64.deb (--install):
 pre-dependency problem - not installing nautiluspatch
Errors were encountered while processing:
 nautiluspatch_v3.4.2-0ubuntu5-1_amd64.deb

```

Anyone know how to fix it?

---

### Post by mattywix on 2013-03-14
@wim just manually apply the changes by reading the patch file in a text editor and then fixing each file.  Theres very few lines of code involved.

---

### Post by cmcanulty on 2013-03-15
Can you explain how to do that in more detail for dummies?

---

### Post by kirby33 on 2013-04-02
Sorry, but I am too busy... A new version of the patch is available:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu7-1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu7-1_amd64.deb)

The text patch file is also available:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu7-1.txt](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu7-1.txt)

---

### Post by kirby33 on 2013-04-10
The text patch file for nautilus v1:3.4.2-0ubuntu8 is available:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu8-1.txt](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_3.4.2-0ubuntu8-1.txt)

---

### Post by kirby33 on 2013-04-11
The 32 bits deb file for nautilus v1:3.4.2-0ubuntu8 is available:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu8-1_i386.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu8-1_i386.deb)
The 64 bits deb file for nautilus v1:3.4.2-0ubuntu8 is available:
[https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu8-1_amd64.deb](https://launchpad.net/nautiluspatchtogglelocationbar/trunk/nautiluspatchtogglelocationbar/+download/nautiluspatch_v3.4.2-0ubuntu8-1_amd64.deb)

---

### Post by flygin on 2013-06-07
awesome! digestive problems are past ...

---

### Post by mc4man on 2013-09-28
I set up a ppa for builds for someone so thought a link here for anyone else.
Basically the kirby33 mods with the nav buttons on the left.

If using I'd make sure to upgrade nautilus, nautilus-data & libnautilus-extension1a packages

[https://launchpad.net/~mc3man/+archive/naut-mods](https://launchpad.net/~mc3man/+archive/naut-mods)

---

### Post by toumanidislazaros on 2013-10-15
I just followed the instructions in the first post for the latest patch "nautiluspatch_3.4.2-0ubuntu8-1.txt" in quantal (nautilus 1:3.5.90.really3.4.2-0ubuntu4.2) and it works great!! Nice work!

---

### Post by pajus on 2014-09-12
Work as charm!! Thank you. 
Good to mention if you want to do "[COLOR=#000000][FONT=Ubuntu Mono]apt-get source nautilus"
[/FONT][/COLOR]first is required to allow "deb-src" packages in your "/etc/apt/sources.list" and then "sudo apt-get update"

---

### Post by phanhan on 2014-09-15
Thanks flar, gnome and ubuntu seem to be on a mission to remove functionallity and configurability when it conflicts with their interface ideas, they've changed from the free software ethos of 'extend and configure' to 'cut and restrict'.
ads: VinaHost là công ty cung c&#7845;p d&#7883;ch v&#7909; [thuê máy ch&#7911;]("http://vinahost.vn/may-chu-rieng.html") và cho thuê máy ch&#7911; và [thuê pvs]("http://vinahost.vn/gioi-thieu-cong-nghe-cloud.html")  và [Hosting doanh nghi&#7879;p]("http://vinahost.vn/business_hosting.php") và [d&#7883;ch v&#7909; email hosting]("http://vinahost.vn/email-hosting.html") 
và [ki&#7875;m tra tên mi&#7873;n]("http://vinahost.vn/ho-tro-ten-mien.html") và [&#273;&#259;ng ký tên mi&#7873;n]("http://vinahost.vn/vndomain.php") và tên mi&#7873;n vi&#7879;t nam và l&#432;u tr&#7919; website chuyên nghi&#7879;p v&#7899;i h&#417;n 8 n&#259;m kinh nghi&#7879;m trên th&#7883; tr&#432;&#7901;ng Vi&#7879;t Nam và B&#7855;c M&#7929;.
website technology: [tech new online]("http://www.technewonline.com")

---

