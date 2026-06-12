---
title: "desktop icons disappear &amp; compiz fusion wont start at startup?!?"
date: 2008-03-31
forum: Desktop Effects &amp; Customization
---

### Post by azanoncello on 2008-03-31
Every time I restart my computer all my desktop icons disappear and my compiz fusion wont start properly.

The reason why I think they are related is because sometimes once compiz fusion is running my icons come back.

When I go to the Appearance Preferences I try and select "custom" but it does some thinking and flashing and then comes back and just goes back to "none" again.
The only way I am able to get compiz fusion running again is to select "normal" or "Extra" and then go to the CompizConfig Settings Manager and re enable everything that I want on.

I searched all the forums and couldn't find a solution and I've tried removing compiz fusion and then reinstalling it. 

Compiz Fusion used to run fine and then one time when i started my computer I noticed all my icons gone as well as compiz fusion wasn't running anymore.

My system:
P4 2.2ghz
512mb DDR
nvidia geforce2 mx400

When i run
```
compiz --replace
```

I get
```
andre@andre-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (autumn) - Info: Loaded Texture /usr/share/ccsm/images/leaf1.png
/usr/bin/compiz.real (autumn) - Info: Loaded Texture /usr/share/ccsm/images/leaf2.png
/usr/bin/compiz.real (autumn) - Info: Loaded Texture /usr/share/ccsm/images/leaf3.png
/usr/bin/compiz.real (autumn) - Info: Loaded Texture /usr/share/ccsm/images/leaf4.png
/usr/bin/compiz.real (autumn) - Info: Loaded Texture /usr/share/ccsm/images/leaf5.png
/usr/bin/compiz.real (autumn) - Info: Loaded Texture /usr/share/ccsm/images/leaf6.png
Segmentation fault (core dumped)

```

I tried to look for "Xgl" in the synaptic package manager but there seemed to be a lot with those letters in it.

I hope this hasn't been covered before. I have read over a lot of other forums first to see if it had to do with my compiz fusion install but I can't seem to find anything talking about this.
I tried to find "show desktop" in "gconf-editor" but I couldn't find it anywhere. I read in another forum that it might be the problem.

---

### Post by tommyhakinen on 2008-03-31
to enable compiz fusion to work on start up, go to system > prefences > sessions
under the startup programs, add new item and enter and save this code as the command:

compiz --replace

it will automatically start compiz fusion.

hope this can help.

good luck.

---

### Post by azanoncello on 2008-03-31
Yeah I actually did that already. It doesn't seem to help since compiz --replace isn't starting it properly right now.

---

### Post by CLomax on 2008-03-31
In that case, its best to reinstall it.
[PHP]sudo apt-get remove compiz[/PHP]
[PHP]sudo apt-get install compiz[/PHP]
**EDIT: Just realised that you had already reinstalled, can't delete this message.**

---

### Post by azanoncello on 2008-04-01
I removed it by going into the Synaptic package manager and searching for "compiz" I then removed everything that showed up. I then went back and installed from the terminal following one of the many guides posted here in the forms.

Will that make a difference?

---

