---
title: "Using Patches?"
date: 2009-02-10
forum: General Help
---

### Post by AbsentHarvest on 2009-02-10
I am not able to click and drag (make my own applets for AWN)
Apparently this is a bug. After doing some more research I found that this bug has a patch. applet_addremove.patch

SO>>>>>> My question is... How can I install this patch? It appears as a text document as I open it. I know I need to type out a command of some sort in the terminal in a certain spot... I really have no idea where that is or what to do exactly... So I am here for guidance.

---

### Post by overlord.gaurav on 2009-02-11
Do the following in a terminal:

**0. Go to your home folder**
```
cd ~
```

**1. Download the svn.**
```
svn checkout http://avant-window-navigator.googlecode.com/svn/trunk/ avant-window-navigator
```

**2. Go to a-w-n directory.**
```
cd avant-window-navigator

```

**3. Copy downloaded file into the avant-window-naviagor dir, rename to patch.diff** (it can be anything, just use that name elsewhere in the code that follows).


**4. Apply patch:**
```

patch -p0 < patch.diff

```
[COLOR="Red"](Note: if that errors out (ignore hunk failed messages) use -p1, not -p0)[/COLOR]

**5. Delete the patch file, you don't need it anymore.**
```
rm patch.diff

```

**6. Go to step 3 if there are more patches you want to apply.**

**7. Prepare for Installation.**
```
./autogen.sh
```
[COLOR="Red"](NOTE: If that errors out and asks for some packages, install the packages with that name and also those of the same name with -dev on the end. So if it asks for xlib, you have to install xlib and xlib-dev (I don't know what packages it really needs, this one is made up))[/COLOR]

**8. Compile.**
```
make
```
[B]
9. Install.[/B]
```
sudo make install
```

**10. Restart AWN.**

---

### Post by moonbeam on 2009-02-11
Just a note... According to this 

[https://bugs.launchpad.net/awn/+bug/141159](https://bugs.launchpad.net/awn/+bug/141159)

The patch was applied to trunk over a year ago.

---

