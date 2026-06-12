---
title: "how to determine my video card in Jaunty"
date: 2009-06-17
forum: General Help
---

### Post by raymondvillain on 2009-06-17
32 bit Jaunty on 5 year old desktop, Pentium 4.  Intel graphics integrated into motherboard.  82865G or something like that.

There is a command, which I have forgotten, to be entered in a terminal session.  It lists the details of the graphics card, and perhaps the sound card also.

Does anyone else recall this very useful command?

If I should decide to install a separate video card, is there a list of video hardware compatible with 9.04?  Might as well pick one that is known to work.  I've searched the forums and several threads are enlisting users to add their working or non-working hardware to the list, but those threads are tedious to search.

Thanks,

---

### Post by Legace on 2009-06-17
If you're gonna get a new card, take one of nVidia. They got better drivers currently.

To check your video card:
[http://ubuntuforums.org/showthread.php?t=742716](http://ubuntuforums.org/showthread.php?t=742716)

(Try Google. You'll get answers faster ;))
[http://www.google.fi/search?q=what+video+card+check+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:fi:official&client=firefox-a](http://www.google.fi/search?q=what+video+card+check+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:fi:official&client=firefox-a)

---

### Post by Therion on 2009-06-17
Install **Gnome Device Manager**.

Select System/Administration/Synaptic Package Manager and then click the Search button. Type in *gnome-device-manager* and install the package.

One of my "Must Have" apps.

And here's the Ubuntu Hardware Compatibility List website:  [http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by Kevbert on 2009-06-17
Command for audio
```
lspci | grep audio
```
video
```
lspci | grep VGA
```
Go for a Nvidia display adapter.

---

### Post by martin_legion on 2009-06-17
Try this command:
```
sudo lshw -C display
```

Good luck

---

