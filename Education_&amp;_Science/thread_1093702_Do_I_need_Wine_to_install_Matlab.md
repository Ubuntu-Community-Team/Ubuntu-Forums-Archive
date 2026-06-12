---
title: "Do I need Wine to install Matlab?"
date: 2009-03-11
forum: Education &amp; Science
---

### Post by irockonguitar on 2009-03-11
Hey I've got Matlab2007b, and I'd like to install it on my laptop, which runs Ubuntu 8.10. I've noticed that most people on the forums here have installed it using Wine, but is this necessary? I noticed that there is a "setup.exe" file, which of course, won't run by simply clicking on it, but will it work in Wine? I don't have Wine (yet) but if I need to, I will download it, so if there's any advice I should take into account first, please let me know!

Thanks in advance.

---

### Post by epitaph on 2009-03-11
MATLAB itself supports Linux. Whether or not you have an installer CD that does is another story.

For me, the one provided had an extremely old version of the student edition of MATLAB and there was no installation support for Linux.

I obtained a copy of MATLAB R2008a from the Mathematics department and installed it without a hitch on 8.04. It still works fine after an upgrade to 8.10.

---

### Post by irockonguitar on 2009-03-11
Hmm, I got my copy from a friend via a usb flash drive, so I'm not even entirely certain that it isn't pirated. What can/should I do to go about installing it? Alternatively, I do have Octave installed on my laptop, but I can't seem to start an editing session, so if anybody has any advice on that, I could perhaps avoid installing Matlab altogether, if that's a better idea.

Thanks!

---

### Post by epitaph on 2009-03-11
I'm not experienced with Octave. If I recall correctly, I think that octave doesn't come with an IDE. You could probably use something like Scite to create your m-files and then run them using octave.

Scilab has similar functionality but probably does not have the same level of compatibility with m-files.

I think a lot of this depends on what your problem is and what you want to accomplish.

Oh, and not to confuse you too much but Scipy, Numpy, and matplotlib are worth looking into.

There might just be no install files for Linux on the USB drive he gave you.

---

### Post by irockonguitar on 2009-03-11
> **epitaph said:**
> I'm not experienced with Octave. If I recall correctly, I think that octave doesn't come with an IDE. You could probably use something like Scite to create your m-files and then run them using octave.

Scilab has similar functionality but probably does not have the same level of compatibility with m-files.

I think a lot of this depends on what your problem is and what you want to accomplish.

Oh, and not to confuse you too much but Scipy, Numpy, and matplotlib are worth looking into.

There might just be no install files for Linux on the USB drive he gave you.

Yeah, I don't know exactly what I'm looking for, but I imagine that setup.exe file isn't it, and I don't see anything else that looks like it will run in Ubuntu.

Basically, all I need Matlab for is matrix algebra, and occasionally mapping. I'm taking Geomatics Engineering, and most of our programming is in C++ or Visual Basic, but once in awhile we're asked to do a bunch of matrix manipulations, and sometimes draw a map. Of course, I can do all of this using the school's computers, but I'd just like to have the capability on my laptop as well.

Thanks for the alternative suggestions. I might check them out this weekend if I have time.

---

### Post by epitaph on 2009-03-12
Look for an INSTALL file or a bash script (.sh) I suppose. I'd have to see it to be sure.

---

### Post by ahmatti on 2009-03-12
Matlab linux version comes in a separate CD/DVD from the Windows version. So probably your friend only has the Win-version, you could of course try asking him/her. Octave doesn't have an editor, but you can use e.g gedit to write your m-files, it has syntax highlighting as well. 

There is also an IDE for Octave called QtOctave, but I haven't used it. Check out this thread: [http://ubuntuforums.org/showthread.php?t=713880&highlight=qtoctave](http://ubuntuforums.org/showthread.php?t=713880&highlight=qtoctave).

---

### Post by irockonguitar on 2009-03-12
> **ahmatti said:**
> Matlab linux version comes in a separate CD/DVD from the Windows version. So probably your friend only has the Win-version, you could of course try asking him/her. Octave doesn't have an editor, but you can use e.g gedit to write your m-files, it has syntax highlighting as well. 

There is also an IDE for Octave called QtOctave, but I haven't used it. Check out this thread: [http://ubuntuforums.org/showthread.php?t=713880&highlight=qtoctave](http://ubuntuforums.org/showthread.php?t=713880&highlight=qtoctave).

Ok, I'll try that, thanks!

---

### Post by bryonak on 2009-03-12
```
sudo aptitude install octave qtoctave
```

Then simply launch it from the menu.
I've been using QtOctave for more than a year now, and it's almost fully compatible to MatLab.
I say almost because Octave can do anything MatLab does, except for a different way of handling graph styles. On the other hand, Octave can do a bunch of terminal related things MatLab can not.

Two other differences I'm aware of (Octave 3 vs MatLab 7):
1. MatLab only supports single quote strings, Octave supports both single and double. For MatLab compatibility, you should use only single quotes.
2. MatLab does wrong integer arithmetic when rounding, QtOctave does it right. Since both are numerical programs, the errors introduced by this are usually irrelevant.

EDIT: forgot to add that with QtOctave in GNOME, you have to fiddle around with the Qt settings to make it remember window positions. This is the main drawback, since it can be quite a hassle.

---

### Post by irockonguitar on 2009-03-12
> **bryonak said:**
> ```
sudo aptitude install octave qtoctave
```

Then simply launch it from the menu.
I've been using QtOctave for more than a year now, and it's almost fully compatible to MatLab.
I say almost because Octave can do anything MatLab does, except for a different way of handling graph styles. On the other hand, Octave can do a bunch of terminal related things MatLab can not.

Two other differences I'm aware of (Octave 3 vs MatLab 7):
1. MatLab only supports single quote strings, Octave supports both single and double. For MatLab compatibility, you should use only single quotes.
2. MatLab does wrong integer arithmetic when rounding, QtOctave does it right. Since both are numerical programs, the errors introduced by this are usually irrelevant.

Awesome, that sounds like it'll work. I'll give it a try.

Thanks!

---

