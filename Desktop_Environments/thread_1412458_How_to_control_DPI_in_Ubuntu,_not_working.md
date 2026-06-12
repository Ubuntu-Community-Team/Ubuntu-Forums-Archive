---
title: "How to control DPI in Ubuntu, not working"
date: 2010-02-21
forum: Desktop Environments
---

### Post by richy2010 on 2010-02-21
Hi all

Searched the forum and google for a few days trying out various options, nothing working so far. Let's see if anyone here has a tip for me ;)

I'm running Ubuntu Netbook Remix 9.10 (latest) on Compaq Mini 702EA (1024x600). The text is very small in Firefox and the rest of the desktop due to the high DPI of the display panel (118dpi).

Therefore I would like to increase the DPI setting, so that text,icons, web pages are rendered larger.

I found this page covering a lot of ideas, none of which work for Ubuntu or firefox
[http://www.mozilla.org/unix/dpi.html](http://www.mozilla.org/unix/dpi.html)

In X the way to increase the DPI seems to be to configure a smaller display resolution in mm than is actually the case. However, this does not work either

Section "Monitor"
    Identifier    "Configured Monitor"
    DisplaySize    163 95 # 160dpi 
EndSection

I did find a control in Ubuntu to make the Remix desktop larger.. however, now writing this I cannot find where it was. Anyone remember?

The only other workaround is to configure Firefox's font size for each charset, Western etc to have a larger min size. This means text is larger, but images are still small, and so pages don't look quite right. Firefox does not allow configuration of the "zoom" at a fixed amount, 130% would probably be enough.

Firefox layout.css.dpi seems mostly broken, it only changes anything if going beyond 192, after which the text is then too large!

Any ideas?

---

### Post by mcduck on 2010-02-21
System/Preferences/Appearance, Fonts-tab, click the Details-button.

Seting the DPI in xorg.conf should work justa s well, but you really need to post the whole file here if you want help with that.

---

### Post by richy2010 on 2010-02-21
> **mcduck said:**
> System/Preferences/Appearance, Fonts-tab, click the Details-button.

Seting the DPI in xorg.conf should work justa s well, but you really need to post the whole file here if you want help with that.

Thanks for the tip.

OK, Xorg.0.log:  [http://www.pastebin.com/f61d2b406](http://www.pastebin.com/f61d2b406)

/etc/X11/xorg.conf:  [http://www.pastebin.com/m5dcc970c](http://www.pastebin.com/m5dcc970c)

Thanks for taking a look

---

### Post by mcduck on 2010-02-21
xorg.conf looks OK to me. Try adding the resolution there as well, that might dom the trick.

You could also set DPI directly, isnetad of setting the display dimensions, if you only plan to use one resolution. (not that using different than the display's native resolution woiuld make much sense with LCD screen anyway...)

```

Section "Monitor"
         Identifier      "Configured Monitor"
         Modes "1024x600"       
         Option   "DPI" "118 x 118"
EndSection
```


..also, the NoDDC line in the device section should be like this:
```
Option   "NoDDC" "true"
```
(you are now missing the "true" -part of the setting)

---

### Post by richy2010 on 2010-02-21
> **mcduck said:**
> xorg.conf looks OK to me. Try adding the resolution there as well, that might dom the trick.

You could also set DPI directly, isnetad of setting the display dimensions, if you only plan to use one resolution. (not that using different than the display's native resolution woiuld make much sense with LCD screen anyway...)

```

Section "Monitor"
         Identifier      "Configured Monitor"
         Modes "1024x600"       
         Option   "DPI" "118 x 118"
EndSection
```
..also, the NoDDC line in the device section should be like this:
```
Option   "NoDDC" "true"
```(you are now missing the "true" -part of the setting)

Hi, thanks for this tip.

I tried with all the changes including NoDDC correction, but I get a swiffy display (like TV with interference), commenting out the NoDDC change and restarting gets it working again, however xdpyinfo|grep res   still shows 117x117 dpi :(

is NoDDC needed to control DPI?

I've set System/Preferences/Appearance, Fonts-tab, Details to be 160dpi. Not sure why X is not using this for Firefox tho. Or why Firefox is not using the Appearance value directly like other Gnome apps.

I noticed this in the new Xorg.0.log file:

(==) intel(0): DPI set to (96, 96)
(WW) intel(0): Option "DPI" is not used

Cheers, richy

---

### Post by richy2010 on 2010-02-21
BTW, there is a big security issue in ubuntu.. i can just select "Recovery" -> "Root console" without it ever asking me for the root password!! Is this a known potential prob?

---

### Post by richy2010 on 2010-02-21
I realised that Modes "1024x600" should be in Section "Screen" 

Still not working tho.. :(

Could Option "IgnoreEDID" "true"  help?

maybe also:
Option "UseEDID" "False"

---

### Post by mcduck on 2010-02-21
The "noDDC" option isn't usually necessary, but some people are suffering from a bug that requires that entry to e able to set the DPI. Since adding that setting didn't help you you should be able to safely leave that option out. Actually things *should* work better without such option.

You could indeed try enabling/disabling EDID.

Firefox probably doesn't follow the Gnome setting because it's not actually a GTK application, even though Mozilla makes it look like one. It uses it's own toolkit (XUL) for the user interface, and that doesn't always work exactly as you'd expect it to...

..and no, the recovery mode thing is not a bug. It's a designed feature, since physical access to a computer should always be considered as root access. With physical access to a machine anybody will be able to access all your data in a way or other anyway (be it booting with a live-CD, or removing your hard drives to read them on another machine, or something else) so being able to use the recovery mode doesn't make much of a difference security-wise. On the other hand it makes recovering from many problems considerably easier. If you want to, you can set a Grub password to restrict access to recovery mode, but if anybody gets unrestricted access to your computer you have already lost the game... (the _only_ way to protect your data if your computer gets in wrong hands is to encrypt the data.)

---

### Post by richy2010 on 2010-02-21
> **mcduck said:**
> xorg.conf looks OK to me. Try adding the resolution there as well, that might dom the trick.


I tried two other ideas, not successful tho:

1)
/usr/bin/startx   defaultserverargs

Someone suggested changing ubuntu default from -dpi 75 to this:

defaultserverargs="-dpi 120 -ac -nolisten tcp"

2) 
/etc/X11/xinit/xserverrc contains this line

"exec /usr/bin/X11/X -dpi 78 -nolisten tcp"

i changed to 146, but no difference after reboot.

So I'm still stuck.. DPI is 117x117 according to xdpyinfo

---

### Post by mcduck on 2010-02-21
> **richy2010 said:**
> I tried two other ideas, not successful tho:

1)
/usr/bin/startx   defaultserverargs

Someone suggested changing ubuntu default from -dpi 75 to this:

defaultserverargs="-dpi 120 -ac -nolisten tcp"

2) 
/etc/X11/xinit/xserverrc contains this line

"exec /usr/bin/X11/X -dpi 78 -nolisten tcp"

i changed to 146, but no difference after reboot.

So I'm still stuck.. DPI is 117x117 according to xdpyinfo

You seem to be trying different DPI value for everything? Perhaps it would help to use the same value in every polace where you try to set it, since there really is only one correct DPI for certain screen size & resolution...

---

### Post by richy2010 on 2010-02-22
> **mcduck said:**
> You seem to be trying different DPI value for everything? Perhaps it would help to use the same value in every polace where you try to set it, since there really is only one correct DPI for certain screen size & resolution...

Ok, i'll try make them all the same 160... i used different values so I could test more than one change at a time.  it's still stuck on 117x117 tho.

any idea how I can boot to a shell login? then I could do a startx -dpi 160   and test that, cheers rich

---

### Post by richy2010 on 2010-02-22
Unfortunately those options dont seem to work with my intel GMA chipset :(

(WW) intel(0): Option "NoDCC" is not used
(WW) intel(0): Option "IgnoreEDID" is not used
(WW) intel(0): Option "UseEDID" is not used
(WW) intel(0): Option "DPI" is not used
(--) RandR disabled

---

### Post by richy2010 on 2010-02-22
ok, finished setting everything to the same DPI... but still it is stuck at 117x117

Any ideas?

Cheers, richy

---

### Post by richy2010 on 2010-02-23
> **mcduck said:**
> You seem to be trying different DPI value for everything? Perhaps it would help to use the same value in every polace where you try to set it, since there really is only one correct DPI for certain screen size & resolution...

No Squint Firefox Zoom remember addon seems to be what I am looking for, giving it a try now:
[https://addons.mozilla.org/en-US/firefox/addon/2592](https://addons.mozilla.org/en-US/firefox/addon/2592)

---

### Post by richy2010 on 2010-02-23
> **richy2010 said:**
> No Squint Firefox Zoom remember addon seems to be what I am looking for, giving it a try now:
[https://addons.mozilla.org/en-US/firefox/addon/2592](https://addons.mozilla.org/en-US/firefox/addon/2592)

Unfortunately it doesn't solve the DPI issue in Firefox, as it now means pages don't fit on pages. However, as text only zoom set to 170% it seems to have the desired effect.. I will run with this now

cheers, rich

---

