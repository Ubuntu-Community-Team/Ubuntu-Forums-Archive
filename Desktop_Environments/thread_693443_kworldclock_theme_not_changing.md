---
title: "kworldclock theme not changing"
date: 2008-02-11
forum: Desktop Environments
---

### Post by sfabel on 2008-02-11
Hi Forum,

little question: does anyone else experience the same thing? I have the kworldclock desktop background running, and would like it to display a different theme.

So I changed the command under "Configure Desktop - Backgrounds - Advanced Options" to the following:

```

kworldclock --theme flatworld --dump --size %xx%y -o %f

```

This does not work. It shows the correct preview, but does not adjust the desktop background accordingly. I only added the '--theme flatworld' parameter to the already existing commands (both preview cmd and Command).

Any idea? I couldn't find anything about that on the 'net, maybe you can help?

Thanks,
Stephan

---

### Post by BryanFRitt on 2008-06-13
I posted workaround, etc... here
[http://bugs.kde.org/show_bug.cgi?id=65894](http://bugs.kde.org/show_bug.cgi?id=65894)
for what I think your problem might be.

---

### Post by BryanFRitt on 2008-06-13
bug fix:
in
maploader.cpp

replace:

uint size=0;
for (uint i=0; i<sizes.count(); ++i)
  if (sizes[i] >= width)
    {
      size = sizes[i];
      break;
    }

with:

uint size=0;
for (uint i=0; i<sizes.count(); ++i)
{
size = sizes[i];
if(sizes[i] >= width)
break;
}

worked for my test!
The old one would fail if largest map < resize to width

---

