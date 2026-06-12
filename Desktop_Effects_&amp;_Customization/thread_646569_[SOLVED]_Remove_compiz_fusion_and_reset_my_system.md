---
title: "[SOLVED] Remove compiz fusion and reset my system"
date: 2007-12-21
forum: Desktop Effects &amp; Customization
---

### Post by IanB2 on 2007-12-21
I seem to have screwed up my system by trying to set up the cube in compiz fusion. I seem to have it working with GL desktop and then installed the advanced desktop settings. The desktop is now not behaving. :confused:

Now I'm unable to see any of the icons on my workspace thumb nails when I have any visual effects enabled. I'm also unable to set the number of workspaces.

Is there a way of going back to the original system setting without having to do a complete system re-install?

---

### Post by adityakavoor on 2007-12-21
```

metacity --replace

```

---

### Post by anyo409 on 2007-12-21
you might want to go to synaptics and remove Compiz fusion and see if that fixes the problem. Try a different user also and see if the problem persists. I am pretty sure you have messed up your settings that's all. What graphics card are you using ?

---

### Post by adityakavoor on 2007-12-21
to remove compiz u can try
```

sudo apt-get autoremove compiz*

```

---

### Post by IanB2 on 2007-12-25
Thanks for your help ..... I've removed and re-installed compiz fusion and all is now working fine again.

I've found a bug trying to use f-spot in slide show mode .... but it is already well documented. Compiz fusion is really good but not yet 'bomb proof'.

---

