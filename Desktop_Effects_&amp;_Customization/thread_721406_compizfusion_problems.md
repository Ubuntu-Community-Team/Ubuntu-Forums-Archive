---
title: "compizfusion problems"
date: 2008-03-11
forum: Desktop Effects &amp; Customization
---

### Post by gawdin on 2008-03-11
ok I have compizfusion installed, and I have followed all the instructions from this document

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

I did the subversion install and svn for the emerald themes but no themes show up

also when i go into the system>preferences>appearance>visual effects and I click custom it says desktop effects could not be enabled

if you need system information tell me how to get a summary and I will post it

I am running Ubuntu 7.10 (Gutsy Gibbon)

---

### Post by wblancqu on 2008-03-11
What video card and driver are you using. Please post /etc/X11/xorg.conf. Also post output of glxinfo.

Grtz

---

### Post by kdarkentity on 2008-03-11
what happens after you compiz --replace? Does compiz start but you have no emerald theme being displayed?

---

### Post by gawdin on 2008-03-11
wont let me post xorg.conf says invalid file... by the way I am a complete newbie to this so I may appear completely ignorant and one should assume unless I say otherwise also how do i output glxinfo? thanks for any help

---

### Post by gawdin on 2008-03-11
> **kdarkentity said:**
> what happens after you compiz --replace? Does compiz start but you have no emerald theme being displayed?

the screen flashes like it refreshed but I notice no difference

---

### Post by wblancqu on 2008-03-11
```
cat /etc/X11/corg.conf >> ~/Desktop/xorg.txt
```

A file should appear on your desktop, post the contents of it. Also perform

```
glxinfo >> ~/Desktop/glxinfo.txt
```

And post the contents of the other created file.

Grtz

PS.: Don't worry about being a newbie ;), everybody has to begin somewhere. Good luck in your ubuntu experience.

---

### Post by gawdin on 2008-03-11
thought i should point out the typo for the code (in case anyone uses this as a reference)

cat /etc/X11/corg.conf should be xorg.conf


thanks for how to do that

also out of curiosity what is the glxinfo used for? I understand the xorg.conf is like dxdiag in Windows.

---

### Post by wblancqu on 2008-03-11
Can you also please post the output of:
```
compiz --replace
```

Grtz

---

### Post by gawdin on 2008-03-11
um, it doesn't output it... just sits there

this is what I entered
```
compiz --replace >> ~/Desktop/compizreplace.txt
```

it refreshes then does nothing, doesn't even give me back the command line just a black blinking box

---

### Post by gawdin on 2008-03-11
nevermind it created the text

---

### Post by wblancqu on 2008-03-11
Try:
```
compiz --replace 2> ~/Desktop/compiz.txt
```

Otherwise, just perform compiz --replace in a terminal, and copy/paste the output here.

PS.: The 2> means: write "error" output to given file, while >> means: write "normal" output to given file, > means: write output to file, while first clearing the given file.

Grtz

---

### Post by gawdin on 2008-03-11
hmm more stuff I didn't know, it did output with the >> though it just took a little bit here it is again if you didn't see it from my last post

---

### Post by wblancqu on 2008-03-11
Try:

```
sudo apt-get install xserver-xgl
```

and reboot. Then try running compiz again.

Grtz

---

### Post by wblancqu on 2008-03-11
If that doesn't work, remove xserver-xgl:

```
sudo apt-get remove xserver-xgl
```

Try following this guide:

[http://ubuntuforums.org/showthread.php?t=253856](http://ubuntuforums.org/showthread.php?t=253856)

---

### Post by gawdin on 2008-03-11
ok the first one when going into visual effects and clicking custom it still said it couldn't load them

the tutorial didn't work at all the part where you add in the compiz to the source list then update, the update gives errors for those links

---

### Post by wblancqu on 2008-03-11
could you reinstall the xserver-xgl package, reboot, and post the output again of compiz --replace.

grtz

---

### Post by gawdin on 2008-03-11
sorry it took so long

---

