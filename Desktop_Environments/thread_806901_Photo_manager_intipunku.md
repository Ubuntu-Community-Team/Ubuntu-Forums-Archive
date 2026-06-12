---
title: "Photo manager intipunku"
date: 2008-05-25
forum: Desktop Environments
---

### Post by irielion on 2008-05-25
Hi,
People who are interested in a new photo manager, with functionalities beyond any other photo manager, windows and linux. Please read my blog. This is my lastest post. Screenshot will be submitted very soon. Experts can try the svn.
Please note that i am desperate for translators and art designers.

[I][SIZE="2"]The newest version of Intipunku is almost ready. I can almost say the program has changed completely. It has gotten more mature. It is more user friendly, more stable and more feature rich. I have added various filters than can enhance you photos significantly.
The project is up2date translated in English, Catalan, Spanish and Dutch, since nobody is helping me in the project i can only translate to the languages that i know sufficiently.
After 0.3 I will add more features and bugfixes, however i must say with the release of 0.3 the project base has been set.
Before the project was intended to be a clone of Picasa, however i feel that project has gone beyond the funcionality of any photo manager. Therefore i also work on port for windows, it is a pain it the ***, since Intipunku depends on various unix only programs. I did manage to create ports of all of them fortunately, including gphoto2!!![/SIZE][/I]

---

### Post by irielion on 2008-05-25
-

---

### Post by irielion on 2008-05-25
Yet here are screenshots and a list of features.

- Tagger and folder support
- Enhancements
 * Brightness
 * Contrast
 * Temperature
 * Color
 * Sharpness
- Auto-tools
 * Auto-contrast
 * Equalize
 * Sepia
- Tools
 * Red eye
 * Crop
 * Blue sky gradient
 * Rotating
- Export function
 * To picasa album
 * to facebook album (todo)
 * to folder (todo)
 * to local html album
- Import functions
 * from picasaweb
 * from facebook
 * from camera
 * from folder
- Misc function
 * Panorama creation
 * Collage creation (next version)
 * Slideshow (half done)
 * Manually adjust time/date exif tags
 * Set as background (win32, gnome, kde)
- Translations:
 * English (full)
 * Catalan (full)
 * Spanish (full)
 * Dutch (full)
 * Italian (very incomplete)
 * German (very incomplete)

---

### Post by irielion on 2008-05-25
If anyone wants to try it you have add these lines to your /etc/apt/sources.list; I have uploaded the pre2 release.
```

deb http://ppa.launchpad.net/intipunku/ubuntu hardy main
deb-src http://ppa.launchpad.net/intipunku/ubuntu hardy main
```

---

### Post by kaboodle_fish on 2008-05-26
Has anyone else tried this?

---

### Post by lanzen on 2008-05-26
I tried to install it, but there's a missing dependancy I can't find:
python-gtkimageview (>=1.1.0.99+svn20080525)

---

### Post by irielion on 2008-05-26
Hey! Did you use the repositery?? The python-gtkimageview build for i386 should be there, the amd64 failed, but i will fix that soon. In the final release i will make a generic system that install the dependencies. Dependencies is such a pain in the ***.

---

### Post by lanzen on 2008-05-26
Yes, I did. And I'm on AMD 64 right now. I'll try 386 later on when I'll be on that system.

---

### Post by irielion on 2008-05-26
I'm doing a new build right now. I'm sorry for the problem.

---

### Post by lanzen on 2008-05-26
It's ok. Take your time.  :)

---

### Post by irielion on 2008-05-26
It is stuff preparing releases. I spend more time packaging and porting (win32) than actually programming. Taking in account that programmers of dependencies have done a bad job in portability of code and autoconf/automake scripts.

Here you can see the progress of the builds: [https://launchpad.net/~intipunku/+archive](https://launchpad.net/~intipunku/+archive), it should be done in 10 minutes i hope.

---

### Post by irielion on 2008-05-26
amd64 build is done

---

### Post by georgeogoodman on 2008-05-26
When I launch the app, I get the following errors:
Traceback (most recent call last):
  File "/usr/share/intipunku/intipunku.py", line 42, in <module>
    from inti.web import *
  File "/usr/lib/python2.5/site-packages/inti/web.py", line 27, in <module>
    import gtkmozembed, gobject, gtk
ImportError: No module named gtkmozembed

Thanks for working on this. :)

---

### Post by irielion on 2008-05-26
install python-gnome2-extras

Next package, will have that has required.

---

### Post by georgeogoodman on 2008-05-26
I got it to load :)

One note: I take virtually all my photos in the raw format for my camera.  There are open source libraries for dealing with raw formats for Canon, Nikon, etc. and if you supported that I might well switch from F-Spot to your tool.

Thanks for a very fast tool!

---

### Post by irielion on 2008-05-27
Hey, could you maybe send me one of those files. The canon raw have .crw extension right? Try editing (in root) /usr/share/pyshared/inti/constants.py. There is a line EXT=".jpg".split(), change that to EXT=".jpg .crw".split() then intipunku will allow the extension. run intipunku from commandline and see if any errors turn up concerning the specific raw files. If it says add youfile and not later "del" yourfile. It should be loaded. Anyhow if you give me the example files i can work on easily supporting it.
Cheers.

---

### Post by irielion on 2008-05-27
It is very difficult to implement this, however i can implement it that they are autoconverted to another format (tiff, pnm tell me what is the best). It will store the original in the "Original" folder of the album.

---

### Post by lanzen on 2008-05-27
Ok, downloaded and install, but it doesn't run

$ intipunku
location: /usr/lib/xulrunner-1.9b5/libxpcom.so 
before 3
database saved
Traceback (most recent call last):
  File "/usr/share/intipunku/intipunku.py", line 641, in <module>
    app  = IntiPunku()
  File "/usr/share/intipunku/intipunku.py", line 116, in __init__
    self.imbrowser = SunBrowser(self.imbrowser_cb, self.imindex, self.dindex, self.tagindex, self.win)
  File "/usr/lib/python2.5/site-packages/inti/browser.py", line 102, in __init__
    i = self.tm.get_iter((0,0))
ValueError: invalid tree path

---

### Post by irielion on 2008-05-27
Did you put in a valid album directory? If not go to console: rm -rf ~/.config/intipunku and try again. I was already working on a first start wizard that will take care of that stuff.

---

### Post by lanzen on 2008-05-28
Oh yeah, I misunderstood the message in the starting window. I thought it meant it needed some dirs for storage purpose and, of course, I made it point to empty directories.

Now I'm starting to understand how it works. It has a sqlite db, and stores that and thumbnails in ~/.config/intipunku/cache.

---

### Post by geoken on 2008-05-28
I have two questions.

I noticed in the change list it says something about folders. Does that mean it's possible to browse your folder structure from the side pane?

Also, I noticed on your blog you mentioned needing help with artwork (among other things). What exactly do you need?

---

### Post by irielion on 2008-05-28
Hi,
The next pre release wil be clearer. Currently you have the folder structure. The albums you see are folders. You can change that to Tags. 

I need mostly icons, currently i develop icons myself, however some of them are a bit weird. The icons should like the Tango-like icons, developed in svg and then exported to a 128x128 png. However many icons are coming directly from the ubuntu theme, in Windows this is not the case. So i fact i need a complete new icon theme that fits with windows.
Also I could use a nice impressive splash screen. 

If you are interested you can send me a private message.

---

### Post by radagast1155 on 2008-05-28
Bro, hate to rain on your parade like this because on my 32-bit platform your script did this:


aramil@ubuntu-hanesher-desk:~$ intipunku
Traceback (most recent call last):
  File "/usr/share/intipunku/intipunku.py", line 42, in <module>
    from inti.web import *
  File "/usr/lib/python2.5/site-packages/inti/web.py", line 27, in <module>
    import gtkmozembed, gobject, gtk
ImportError: No module named gtkmozembed



good news is that i know how to fix this!
in your deb file take any modules you created and install them in this dir:
usr/lib/python2.5/site-packages/

this will also make your package independent from foreign packages

---

### Post by irielion on 2008-05-28
Soon i release a new pre version, which will not use gtkmozembed. Gtkmozembed was needed for login to facebook. But it funcioned to slow to complete it, so i put it for another release. 

Thank you for advicing me about the folder, i am quite aware of that. the setup.py installs it in that dir. However in this way also python2.4 users can make use of it and it is python independent (although you do make me wonder why it has to be). So possible i change this.

---

### Post by geoken on 2008-05-29
Can someone go into a little more detail about fixing the Gtkmozembed issue?

The app will currently not start up for me and I receive the exact error message that radagast1155 posted above.

---

### Post by irielion on 2008-05-29
Wait a little, it is fixed upstream. If you really cannot wait you have to edit the inti/web.py file, and remove gtkmozembed. But better just wait, tomorrow i will put an update.

---

### Post by geoken on 2008-05-30
Cool, thanks.

I really liked your app when I first tried it I few months ago. I can't wait to try it again with all the new features you added.

---

### Post by irielion on 2008-05-30
Thanx for the compliment. Few months ago the app was a baby, now it is a bit more mature. It runs faster, it has more features and i hope it is more stable. Before it used to crash if it couldnt understand a jpeg. Now i just ignores it. I hope today i can update the release.

---

### Post by irielion on 2008-05-30
Pre3 is out. The only things need to be done is win32 port and a function to move/copy photos between albums. I suppose you guys dont care about win32 port :)

---

### Post by q1u2i3z on 2008-05-30
I am interested in the photo manager. I am running amd 64 are the bugs worked out? I would like to in stall asap

---

### Post by irielion on 2008-05-30
Yes that is supposed to work now. On the blogsite, there is now a link to the APT page where you can see the status of all packages.

---

### Post by kaboodle_fish on 2008-05-31
I think you deserve thanks for making this.

p.s. Is there anyway you could add a printing option?

---

### Post by irielion on 2008-05-31
In which sense do you mean printing, you mean like multiple photos on one page or some special functionality? If it is just multiple photos on one page for sure i can implement this before end of the release. Any special funcionality will go in other release.

---

### Post by kaboodle_fish on 2008-06-01
> **irielion said:**
> In which sense do you mean printing, you mean like multiple photos on one page or some special functionality? If it is just multiple photos on one page for sure i can implement this before end of the release. Any special funcionality will go in other release.

The option to print multiple photos on one page would just be super.

---

### Post by irielion on 2008-06-01
I will implement it.

---

### Post by irielion on 2008-06-18
Alright it took some time, but the print function is almost implemented. It is in svn now. I continue to test it and port the stuff to windows.

---

