---
title: "Wallpaper-tray issue"
date: 2009-05-21
forum: General Help
---

### Post by SpitfireSMS on 2009-05-21
I have wallpaper tray installed, its working fine with 1 small issue.
The default ubuntu wallpapers are somehow still being used, and it kinda sucks that every 5th wallpaper it switches to is an ugly old blank beige image.
My preferences specify 1 folder, and the default wallpapers are not in it.

I also went and deleted the wallpapers from their original location, so they are not on my hard drive anywhere I can find them, yet they still get displayed.

They dont work with my conky settings, and they just look ugly lol.

How can stop them from getting displayed

---

### Post by danwood76 on 2009-05-21
I had to make a patch to the source code to make this function correctly.
My patch basically forces it to only look in the specififed folder and is more of a hack.

If you fancy recompiling it I can post up a patch file?

---

### Post by SpitfireSMS on 2009-05-21
Im newish to ubuntu, but that should be fine with a quick how-to.
Thanks!):P

---

### Post by danwood76 on 2009-05-21
I will post it up later, I have an exam in 3 hours :)

---

### Post by SpitfireSMS on 2009-05-21
No problem man, I know what its like ;)

---

### Post by danwood76 on 2009-05-21
What version of wallpaper tray does jaunty come with?
(I already upgraded to karmic so I'm unsure)

---

### Post by danwood76 on 2009-05-21
Attached is a .tar.gz of the patch.
It simply removes the applets ability to use the themes backgrounds, it is a proper hack but it gets the job done.

First make sure the wallpaper-tray applet isn't running (right click remove). Then open a terminal (Applications->Accesories->Terminal) and run the following commands (copy and paste each line and press enter):
```

mkdir source
cd source
apt-get source wallpaper-tray
sudo apt-get build-dep wallpaper-tray

```
The last command will ask for your sudo password as its installing new packages.
These commands setup a new directory to keep source code in, download the wallpaper-tray source from the ubuntu repositories and install all the dependencies required to build it.

Then open up the archive attached to this post with the archive manager and untar the two files within it to ~/source/wallpaper-tray-0.5.5/debian/patches
(the ~/ means your home dir so its the same as the directory the source code has gone to)

Then the next part is to build it:
```

cd ~/source/wallpaper-tray-0.5.5
dpkg-buildpackage

```
Then in the ~/source directory a .deb file will be created which when opened will allow you to reinstall the package. This will overwrite the current version with the patched version and it should work.

Re add the wallpaper-tray to the panel and add a wallpaper directory to it and you should be there.
Congratulations you just compiled and installed your first software package on Ubunut ;)

Any problems post here!

---

### Post by SpitfireSMS on 2009-05-21
Worked perfectly, thanks so much.

---

### Post by coeus82 on 2009-10-08
Hello, 

I tried the above code, but when doing dpkg-buildpackage I get the following output:

```
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1

```

Any idea why it's now asking for a changelog?

** note: I've also tried to work with Desktop Drapes but for some reason it doesn't want to read the folder I'm selecting.

---

### Post by DJ_Peng on 2009-10-17
I took the dist-upgrade to 9.10 yesterday and was disappointed when my beloved wp-tray didn't want to work. I tried your steps and ended up with this when I ran dpkg-buildpackage:
>  signfile wallpaper-tray_0.5.5-0ubuntu3.dsc
gpg: skipped "Joao Pinto <joao.pinto@getdeb.net>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-genchanges  >../wallpaper-tray_0.5.5-0ubuntu3_i386.changes
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
dpkg-buildpackage: warning: Failed to sign .dsc and .changes file
When I tried to add the newly installed applet I got the same error message as I did before, "The panel encountered a problem while loading 'OAFIID:wp_tray'."
I did notice a number of dbus errors during the upgrade. Could the two errors be related? I really don't want to have to run yet another clean install since I just did that for 9.04 and I would like to avoid having to reinstall everything again.

---

### Post by iaggrey on 2009-11-10
Thanks, @[danwood76]("http://www.uluga.ubuntuforums.org/member.php?u=381686")! This method still works as of now (at least on my HP dv5t running Ubuntu 9.10 64-bit).

---

### Post by Lessss on 2009-11-13
If the error you are getting is *The panel encountered a problem while loading "OAFIID:wp_tray"* Then first make sure the pictures are not on an unmounted drive.  This was my issue. Soon as I mounted the external drive it started working.

---

### Post by DJ_Peng on 2009-11-13
That's the error I'm getting (just trying to add WT back to my panel), but none of my image files are on an unmounted drive. In fact the folder I had it set to use before I upgraded to karmic is /media/UbuntuData/Files/SFW. What do I edit to let me start from scratch?

---

### Post by Lessss on 2009-11-19
Wallpaper tray:  Right click on panel, preferences, directory list.

---

### Post by DJ_Peng on 2009-11-19
I would try that if I could get the tray on my panel. Just adding the item brings up the closed applet dialog.

---

### Post by Paresh on 2009-12-01
> **coeus82 said:**
> 
```
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1

```

Any idea why it's now asking for a changelog?


I got this error because I compiled from the wrong directory.  make sure you're in the 'wallpaper-tray-0.5.5' directory before building the package.

---

