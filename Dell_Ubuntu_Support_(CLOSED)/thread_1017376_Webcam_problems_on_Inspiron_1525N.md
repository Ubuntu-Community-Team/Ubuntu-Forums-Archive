---
title: "Webcam problems on Inspiron 1525N"
date: 2008-12-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Madwand on 2008-12-21
I have a Dell Inspiron 1525N with Ubuntu Hardy and integrated webcam. Until recently, the webcam worked with Cheese. I have been searching (in vain, so far) for a way to use the webcam more usefully with programs such as Ekiga and GYachE. My latest effort involved adding the medibuntu repository and installing Skype. Sometime during this effort, even Cheese stopped recognizing my webcam: it tells me, "No camera found." Somehow I've disabled my webcam!

During the process of adding the medibuntu repository, I got this message:

```
The following packages were automatically installed and are no longer required:
  linux-backports-modules-2.6.24-16-generic oem-config-gtk libxalan110
  localechooser-data oem-config libqt3-mt libxerces27
Use 'apt-get autoremove' to remove them
```

I don't know what this means, but I found it suspicious because the "linux-backports-modules" I think has something to do with getting laptop-specific drivers working.

Can anyone tell me what I might be able to do (or undo) to get my webcam working again? What does the strange message above mean, and does it have anything to do with this problem?

---

### Post by llamakc on 2008-12-21
That message is helpful in that it lets you know which packages are no longer needed. The 'backports' package referenced in that message refers to an earlier kernel version. You are most likely using a newer kernel. Make sure you have the linux-backports-module package for your current kernel.

You're using 8.04, correct? I'm on 8.10 and the updated kernel is 2.6.27-9.

I'd update my package list 

```

sudo aptitude update

```

And upgrade any packages

```

sudo aptitude safe-upgrade

```

If it grabs a new kernel, you'll want the backports-module that matches the kernel version.

```

sudo aptitude install linux-backports-modules-`uname -r`

```

[http://packages.ubuntu.com](http://packages.ubuntu.com) has 2.6.24-19 as the most recent kernel for Hardy. 

After that is all upgraded, see if it helps. FWIW I can't get Cheese working for me at all, but Skype & aMSN both have no problems with the webcam on my 1525.

HTH

---

### Post by Madwand on 2008-12-21
Thanks for the explanation. "safe-upgrade" got my webcam working again, in both Cheese and Skype.

---

### Post by digitizemd on 2009-01-04
This is quite interesting.  I have a inspiron 1525, and cheese does not work either (ubuntu 8.10).  I randomly tried out opensuse 11.1 yesterday (gnome install) and cheese worked fine with the webcam; kubuntu 8.10 was also able to utilize the webcam.  The one issue I noticed was that in opensuse cheese only listed up to a resolution of 640x480... which I imagine is the max for the webcam.  On ubuntu, cheese has 1600x1200 as the default; unfortunately lowering the resolution to 640x480 doesn't solve the issue.  Considering ubuntu 8.10 and opensuse 11.1 have very similar specs (kernel, gnome, etc.), I'd think cheese would work out fine.

edit:  also, cheese freezes when changing the resolution.

---

### Post by llamakc on 2009-01-13
Yep, I still can't get Cheese to work. aMSN and Skype work fine though.

---

