---
title: "What are the caveats of changing DE's?"
date: 2024-04-28
forum: Desktop Environments
---

### Post by cbiweb on 2024-04-28
I'm on Gnome currently.

If I want to try KDE or something else, what kind of damage (if any) will I do to my current setup?

---

### Post by deadflowr on 2024-04-28
It adds bloat?

---

### Post by TheFu on 2024-04-28
KDE and Gnome are special situations because they are built using completely different toolkits.  That makes it generally safer to switch between them, as settings are unlikely to conflict between GTK+ and Qt toolkits.

Where using multiple DEs under the same userid tends to break things is when multiple versions of Gnome have collisions.  So there are older GTK+ versions used in XFCE, Mate, Cinnamon, and a few other DEs.  These occasionally use the same configuration setting keys, but they mean different things, which can screw up between different DEs.

The best practice for trying out different DEs is to create a new userid/username for each DE you want to try.  Run only that userid with one specific DE and see how you like it.  After you choose the one you want too keep, copy (retain permissions) all the files from the original username/userid into the same location under the new username/userid and chown all the files to the new username.  Run with that new username for a few weeks and figure out if there are any issues or not.  For the most part, the files of concern will be in ~/.local/ and ~/.config/, but there will be others for programs like Firefox, thunderbird, and other programs that keep data in other areas.  The data usually isn't really an issue, just the settings/configurations.

Linux is always multi-user, so why not use multiple users to reduce risks for different tasks?

---

### Post by ajgreeny on 2024-04-28
In the far distant memory I have of my start in the Ubuntu OS 4.10 or 5.04 I always installed the default gnome 2 system but then often added kubuntu-desktop package to that.

Yes, I ended up with two of each of the main application types in my system, ie two file-managers, two text-editors, two terminals, etc etc.
In those days 20 years ago I never had any major problems having those two DEs together in my system, and I generally used the KDE desktop most when logging in.
I have no idea how well those two now work together as they are so very different from the 2010 versions.

When gnome-2 disappeared and turned into gnome-3 and unity-desktop, which was not to my taste (just like the gnome version currently used) so I moved very quickly to Xfce and Xubuntu and immediately found it to be just the best that I had tried.

I have now been with Xubuntu since that time in 2010 (I think) and I use Xfce on all the various other distros that I use.

To try them all out I suggest you download the versions of the different DEs you want to try and simply run them in VMs such as KVM/QEMU or, if you find it easier, Virtualbox.

---

### Post by MAFoElffen on 2024-04-29
+1 with ajgreeny --

Once upon a time I wondered what would happen if I installed Gnome, Unity, Kubuntu, Xubuntu, and Lubuntu... It ended up with lots of multiple versions of applications that did the same thing (like ajgreeny mentioned), but different flavors of those.

That evolved into approaching it a bit differently: installing Ubuntu, then installing gnome-session, xfce4, lxde-core, i3, cinnamon, & kde-plasma-desktop. Much more minimal.  

Think of multiple Windows Managers, then pick and choose what else you want to keep there with it as applications. There will still be multiples of some things, but less of them.

It was just a test.

I live mostly in Gnome and i3, depending what I am doing.

---

### Post by oui on 2024-04-29
> **cbiweb said:**
> I'm on Gnome currently.

If I want to try KDE or something else, what kind of damage (if any) will I do to my current setup?

As I will use more than one or two big member of the typical KDE app's, espec. rosegarden, marble, kdenlive etc (also I find the KDE office with calligra words a lot better as all the derivates of star office) I use mainly KDE app's in about all situations.

but I did install then on xubuntu minimal and it seems to go perfectly! I did never have so light to rebuild completely my system this week after the publication of xubuntu stable.

with the KDE tools, following ones, it is a great installation:

```
sudo apt install aptitude calligra didiwiki gimagereader jwm kdenlive kmplayer konqueror krita kwave kwrite l3afpad librecad marble menu mplayer mtpaint nted okular osmo rosegarden synaptic tesseract-ocr xsane
```

l3afpad is only for some manipulations being not allowed with other graphic editors. gimagereader has no equivalent in KDE. mtpaint is somewhat ideal for screenshots and her manipulation. tesseract-ocr and xsane are needing for high performance ocr. a great power of xfce4 consists in manipulation of keyboard maps for Asiatic languages (I use it for Tamil and Hindi). JWM as well as aptitude are preventive there: If the system froze I have a minimal chance starting JWM or without some graphic environment (I will not use then at all daily!).

---

