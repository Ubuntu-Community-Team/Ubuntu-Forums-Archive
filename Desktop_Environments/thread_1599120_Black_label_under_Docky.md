---
title: "Black label under Docky"
date: 2010-10-17
forum: Desktop Environments
---

### Post by Dsky on 2010-10-17
i see a big black label under the docky dock... i tried to activate maincity compositing but it's still there...

what can i do?

Thanks

---

### Post by Dsky on 2010-10-18
up

---

### Post by ankspo71 on 2010-10-18
Hi,
I am using my Ubuntu 10.10 Live CD right now (not Xubuntu), and I just installed docky to see if I can help. When I tried to run docky, I got docky with a big black area under docky. This is typical behavior for docks that require compositing. However, I was able to make the black area go away by using Metacity's compositing. 

Do you see any shadows on your screen after you enabled Metacity compositing? 
Try using these commands in the terminal to see if you see any errors: 
```
metacity --composite
metacity --no-composite
```
They turn metacity compositing on and off, but these might only be temporary changes.

Metacity is more designed for use with the Gnome desktop though. Actually, XFCE has its own compositing manager. Have you already  tried using that for compositing?
> 
xfwm4 includes its own compositing manager, which takes advantage of the new X.org's server extensions. The compositor is like a WM on its own, it manages a stack of all windows, monitor all kinds on X event and reacts accordingly. Having the compositing manager embedded in the window manager also helps keeping the various visual effects in sync with window events. If you want to use the compositor, you have to build xfwm4 using the --enable-compositor configure option. In any case, you can disable the compositor on xfwm4 startup using the '--compositor=off' argument.
[http://www.xfce.org/documentation/4.2/manuals/xfwm4](http://www.xfce.org/documentation/4.2/manuals/xfwm4)

Hope this helps.

---

### Post by ankspo71 on 2010-10-18
Hi,
Here are some links that talk about Docky in XFCE with XFCE's own compositing:

> 
Chris S.  said on 2009-12-11:
As long as the window manager supports compositing (which xfwm4 does) and can install the dependencies, docky will work just fine.
[https://answers.launchpad.net/docky/+question/93581](https://answers.launchpad.net/docky/+question/93581)

> 
Chris S.  said on 2010-06-19
Docky will work fine with xf4wm (xfce's window manager). You just need to
enable compositing. I don't use xfce, but try this post on ubuntuforums to
enable compositing in xfce:
[http://ubuntuforums.org/showpost.php?p=9423525&postcount=7](http://ubuntuforums.org/showpost.php?p=9423525&postcount=7)
Also, docky doesn't strictly need compiz. Metacity (default gnome window
manager) with compositing enabled works fine as well.
[https://answers.launchpad.net/docky/+question/114921](https://answers.launchpad.net/docky/+question/114921)

To enable compositing using Xubuntu's compositing manager:

> 
vor0nwe   said on June 7th, 2010 
In Xubuntu 10.04 (Lucid Lynx), in Settings / Settings Editor, select 'wfwm4' and 'General / use_compositing', click the 'edit' button, check the 'Enabled' button and click 'Save'.
Works perfectly for me!
[http://ubuntuforums.org/showpost.php?p=9423525&postcount=7](http://ubuntuforums.org/showpost.php?p=9423525&postcount=7)

---

### Post by Dsky on 2010-10-19
thanks so much ;)  now i look at them

---

