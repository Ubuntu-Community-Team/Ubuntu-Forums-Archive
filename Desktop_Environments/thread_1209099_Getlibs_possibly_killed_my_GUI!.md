---
title: "Getlibs possibly killed my GUI!"
date: 2009-07-09
forum: Desktop Environments
---

### Post by martini1179 on 2009-07-09
Getlibs possibly killed my GUI!

I'm not exactly sure what happened, but my GUI has become almost completely unusable. 

Most of the time, when I try to click on almost anything, buttons, panels, the main menus, the application's menu etc, the click doesn't register. I can sometimes regain temporary functionality (read: for the next left-click only) with a combination of repeated clicking and right-clicking. Most of the time, the keyboard commands will work. 

This problem has quickly devolved to the point where most of the time, I need to press the power or reset buttons to leave Ubuntu, and even the keyboard commands often don't work anymore. 

Furthermore, the update manager is not functioning properly. The update manager will load, but when I press the "Check" button, the update manager window will gray out for a fraction of a second and then comes back, without asking for a password. This must be related to the GUI issue since it happened at the same time. 

The mouse moves fine, and it works flawlessly in Vista. 

The strange thing is, **I'm having the same GUI problems on the Jaunty Live CD!!!!** WTF? 

So what was I doing when this started happening? I was browsing the web, checking out the OpenTorrent project's page. NoScript was enabled, and I wanted to allow temporary access to that domain, when I noticed that I couldn't click on the NoScrpit icon. 

I'm an Ubuntu noob, but I *think* I know how this could have happened. Earlier, I was trying to get the Chromium alpha to work, but I kept getting the following error: 

"Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64"

I searched for a solution, until I found this thread: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/190227](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/190227)

Towards the bottom of the page, a suggestion was made to use getlibs to install additional packages for libgail.so and a testimonial that it "fixed" someone's "chromium-browser problem." 

So that's what I did. Maybe two hours later, I started having all of these problems. If memory serves, libgail.so is a file in the libgail-common package and apparently is a component of GTK/GTK+, which according to Wikipedia is "a cross-platform widget toolkit for creating graphical user interfaces. It is one of the most popular toolkits for the X Window System, along with Qt." 

I've tried to fix this by trying to fix broken packages via the recovery console, as well as the "fix  your graphical problems" option, also in the recovery console.

I'd rather not have to reinstall Ubuntu just to fix this, so if someone knows how to undo this damage, any help would be greatly appreciated.

---

### Post by martini1179 on 2009-07-09
I should also add the last time I tried to check for updated packages in Update Manager, I got the following error message: 

"Could not grab your mouse 

A malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus. 

Try again" 

I had just started another painful Ubuntu session and no other windows were open. I never got this error message before I started having these GUI problems.

---

### Post by martini1179 on 2009-07-10
/bump

---

### Post by Clorow on 2009-07-11
I'm not sure why it's happening on a live CD also, that's strange.

You can drop to a shell on another virtual terminal by pressing Ctrl+Alt+F1 at any time. Try doing:
```
sudo apt-get purge chromium-browser
```

---

### Post by martini1179 on 2009-10-18
I'm an idiot. 

Simple noob mistake. I've figured out a workaround, and I'm relatively certain that my mouse is the problem. 

I have a wireless Logitech Mediaplay mouse. Unplugging it from the USB port and plugging a different (wired, in my case) mouse worked perfectly. I then unplugged the wired mouse and plugged the Logitech back in and it worked. Presumably, just unplugging/plugging the mouse will work. 

But why is the mouse messing up to such a degree? I have a theory: According to Logitech's own knowledgebase, the wireless receivers are faulty and require Logitech's Windows-only drivers. If you don't install the drivers, the cursor will occasionally jump to the edge of the screen, something to which I've become accustom. I'm thinking that this faulty receiver can also be responsible for the mouse occasionally not registering mouse clicks. 

And if you want to fix the Mediaplay's jumping cursor (and possibly fix the unresponsive mouse buttons), here's how: According to Logitech's site, the company makes other wireless keyboards/mice whose receivers are compatible with the Mediaplay mouse. I don't remember them off hand, but check the Logitech knowledgebase for the Mediaplay wireless mouse. You can also use the included USB to PS/2 adapter, but you'll lose the ability to use a few of the extra buttons. 

I'm writing this for anyone else who may encounter/has encountered this problem. I hope someone finds it useful.

---

