---
title: "Will Ksnapshot work in Gnome?"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Ben Logan on 2006-06-16
Hi everyone,

I'm a recent Ubuntu convert.  Love it!  Kudos to everyone involved.  

One thing I'm missing is a good screen-cropper tool.  The screen capture is convenient for grabbing a whole-screen-image (and I love the little analog camera icon), but I want to be able to grab just a bit of a web-image e.g. like I can with CaptureMe on a Mac.  

My question: when I try to install Ksnapshot (which I understand is built for the KDE environment), the installer prompts me to insert my Ubuntu Dapper install disk. I'm afraid it's going to convert my entire OS to KDE.  I like Gnome and want to stick with it.  

If I complete the install, will Ksnapshot function properly within Dapper's Gnome environment? 

Thanks, 
Ben
:?:

---

### Post by bluevoodoo1 on 2006-06-16
I have ksnapshot working in GNOME with no problems at all. 

GNOME has its own screen capture program though, and you might have it already if you don't want to mess around with ksnapshot and are afraid it will convert your system (which it shouldn't).

Accessories > Take screenshot
or
```
gnome-screenshot
```

---

### Post by Ben Logan on 2006-06-16
Thanks blue.  Cool that you have ksnapshot rolling in gnome.  Do you perhaps remember whether you were prompted to insert your install disc upon adding through "add/remove" programs?  That's what's giving me the creeps!

---

### Post by bluevoodoo1 on 2006-06-16
It's probably asking for your CD because it's probably listed in your /etc/apt/sources.list as a source to get packages from.

Are you connected to the internet? Since you're posting here I'll assume yes, so I would try the following. 

From the terminal (we're making a backup first)
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Then from the terminal:
```
sudo gedit /etc/apt/sources.list
```

Place a # in front of the line that refers to a CD-rom, it will probably be at the top. Save the file. 

Then from the terminal
```
sudo apt-get update
```

By commenting out the CD in your sources.list you won't be prompted to insert the CD for upgrades, you will simply download the packages.

But either way, you could try using Synaptic Package Manager, and search for ksnapshot. Even if it asks for the CD it's easier to tell what is really being installed. Add/Remove seems a bit cloudy to me in that wayl.

---

### Post by Ben Logan on 2006-06-16
Awesome Blue.  I'll give that a shot.  My wife has the Ubuntu computer at a cafe currently.  I'm on the Windows machine.  Thanks so much for your helo. 

:)

---

### Post by reclusivemonkey on 2006-06-17
[QUOTE=Ben Logan]
One thing I'm missing is a good screen-cropper tool.  The screen capture is convenient for grabbing a whole-screen-image (and I love the little analog camera icon), but I want to be able to grab just a bit of a web-image e.g. like I can with CaptureMe on a Mac.  
[/QUOTE]

You could used the Gnome Screenshot tool, and then just use gThumb Viewer to crop the image after. It seems overkill to install a KDE application and all the QT libs just to crop an image. You could also use the Gimp, but gThumb will load a lot quicker to do a simple crop.

---

