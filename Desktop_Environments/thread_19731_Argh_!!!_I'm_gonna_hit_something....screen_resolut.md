---
title: "Argh !!! I'm gonna hit something....screen resolution."
date: 2005-03-13
forum: Desktop Environments
---

### Post by Metz on 2005-03-13
Myself and X/Gnome/Ubuntu don't seem to agree on the resolution 
I should be running on my laptop.

nVidia GForce 4 440 64mb...natural res 1280x854

....x only allows me 1152x768. I've researched this...and can't find the problem !!!

Help ? Please :(

---

### Post by dickinsd on 2005-03-13
[QUOTE=Metz]Myself and X/Gnome/Ubuntu don't seem to agree on the resolution 
I should be running on my laptop.

nVidia GForce 4 440 64mb...natural res 1280x854

....x only allows me 1152x768. I've researched this...and can't find the problem !!!

Help ? Please :([/QUOTE]
 Hi.

What steps have you taken to try and correct this your self?

I would hate to tell you to try something that you had already tried.

Just in case, try this:
```
sudo emacs  /etc/X11/XF86Config-4
```
You should see a screen section that will include something like this:
```
Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	**DefaultDepth     24**
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes    "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
The part I 'high lighted' :: **DefaultDepth     24** is the depth that will be loaded at boot, you should try to add the desired resolution under this depth :: e.g.
```
Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	**DefaultDepth     24**
	...
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    **"1280x854"** "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```
You need to **add** your desired resolution to the first position in the *array* of options if you want this resolution to be the default resolution.

If you then save the file and exit, and then restart X

In FC3 I can restart X by pressing the keys:
```
CTRL+ALT+BackSpace
```
I can't remember if this owrks in Ubuntu, if not, then just shut down and restart your computer.

Hopefully that should fix your prob.

Dave

---

### Post by Metz on 2005-03-15
Thanks Dickinsd...

I tried this, but it's not working.

If I run the System->Admin->Display Manager, the higest entry in the list is 1152x768, which is what I'm currently running.  There are 4 others, of decreasing resolution available in the list.

I've modified the /etc/X11/XF86Config-4 file, and basically removed all by the Depth 24 entries, and added the of modes that I want....

```

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	Modes    "1280x854" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

I've had to remove the 'viewport' option, as the system objects to this.

However, still no luck in the 1280x854 departement :( It's really starting to get to me. I know it can work, just can't get it to happen. All the graphics stuff I run is cr*p to use at the moment.

---

### Post by smtanner on 2005-03-15
Could you post your entire XF86config file.

---

### Post by theChauvinist on 2005-03-15
Hi, I had the same problem, and for me it worked when I did exactly what's mentioned above, but to the /etc/X11/xorg.conf file instead, as mentioned in a different thread.

Hope that helps.

---

### Post by LordCantenberry on 2005-03-15
I have a similiar problem in that my screen resolution always resets when I reboot gnome or my computer.  I tried the above steps but it still didnt work.  I was wondering if it would hurt anything if i simply removed all display resolutions and depths except the one that I currently want.

Also my monitor refresh resets everytime I restart can I specify a default one in this config file.

Thanks

---

### Post by bored2k on 2005-03-15
sudo dpkg-reconfigure xserver-xorg

---

### Post by pirate_yarrr on 2005-03-15
I used to have this problem with my 64 meg 3dfx card. There is a workaround though...lie to xfree/xorg. Tell it the card has 128 megs of video memory, and it will most likely allow you to run it at 1280x1024. I don't remember the exact syntax though, but usually it's in the sample file, but commented out.

Nathan

---

