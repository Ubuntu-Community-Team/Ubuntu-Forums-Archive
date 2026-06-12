---
title: "Compiz Fusion stopped working after today's update (28th June)"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by paul.maddox on 2007-06-28
Hi everyone,

I installed compiz fusion recently on my ATI x1400 laptop using XGL and everything has been working brilliantly until today's updates.

Normally I have to start compiz using the following command:
```
compiz --replace -c emerald
```
and it worked fine but now, nothing happens. No error messages, no window decoration/borders. Absolutly nothing.

It's like compiz isn't even trying to replace the existing window manager at all, it just sits there seemingly running but not effecting anything.


Anyone else having problems like this today?

---

### Post by Mr Greencastle on 2007-06-28
I second this, have switched to Beryl SVN (from trevino) until it gets fixed.

Its a shame, was liking Fusions new effects... oh well I'm sure it'll get fixed soon enough!

---

### Post by paul.maddox on 2007-06-28
Are you using fglrx too? I have found a temporary fix for mine that seems to get it working for now...


Open up /usr/bin/compiz in an editor and comment out all of the following lines:

```

# if vesa or vga are in use, do not even try glxinfo (LP#119341)
if running_under_bad_driver; then
    abort_with_fallback_wm
fi

# check if we have the required bits to run compiz and if not,  fallback
if ! check_tfp || ! check_npot_texture || ! check_composite; then
    abort_with_fallback_wm
fi

```

Save it and then run the following commands:

```

$ compiz
$ emerald --replace

```


This works for me but it's a bit of a bodge until they fix the actual problem!

---

### Post by Mr Greencastle on 2007-06-28
Yes, I can confirm that that works for now.
I wonder why that fixes it or, moreover, why its causing that problem in the first place?

For anyone else who is having this problem:

Open a terminal then type: sudo gedit /usr/bin/compiz
Then uncomment the lines (by adding a number sign in front) stated in the previous post.

Thanks for pointing this out!

And yes, I do hope 'they' get the real problem fixed...

---

### Post by burgerboy06 on 2007-06-28
it did work, thanks

Did not kick in until i ctrl alt backspaced out of my session and did my compiz --replace command.

---

### Post by Mr Greencastle on 2007-06-29
Thats good to hear, it seems as though the Fusion team has fixed this in a recent update, at least I think so because looking at the same file, those lines don't appear...

I may be wrong though, regards.

Mr Green.

---

### Post by burgerboy06 on 2007-06-29
you are right.  i just commented out the code, got it to work, and then the update popup showed its ugly face.  Good times.

---

