---
title: "Original (Windows) DLLs in Wine - How much can it do?"
date: 2007-05-12
forum: Gaming &amp; Leisure
---

### Post by botulismo on 2007-05-12
So, this is just a question I'm fielding out there... I know Wine allows you to use original MS DLLs and I have used a couple here and there to get a program to work, but how far can it go? If I replaced all the Wine DLLs with ones from an original Windows installation would it be that much more compatible? I doubt that it would be that easy, but I'm just curious to see if anyone knows.

---

### Post by AndrewRiedi on 2007-05-12
> **botulismo said:**
> So, this is just a question I'm fielding out there... I know Wine allows you to use original MS DLLs and I have used a couple here and there to get a program to work, but how far can it go? If I replaced all the Wine DLLs with ones from an original Windows installation would it be that much more compatible? I doubt that it would be that easy, but I'm just curious to see if anyone knows.

It would damage compatibility in a huge and major way.  Not a single application would run at all.  There are a few core dlls such as ntoskrnl, gdi, most of the direct3d ones, etc. that you cannot replace.  The reason is simple, those dlls which are implemented over drivers Wine cannot run because Wine does not have access and cannot run Windows drivers (except for maybe printer drivers).  The other dlls are implemented over the core dlls.  These are the ones you can replace and still have a running system.  These will usually give more compatibility, although you will usually also lose cleaver features that the Wine developers have added for you.  These include drag and drop, copy/paste, etc.

---

### Post by lakersforce on 2007-05-12
Short answer: you would be better off using windows!

---

### Post by Enverex on 2007-05-12
> **botulismo said:**
> So, this is just a question I'm fielding out there... I know Wine allows you to use original MS DLLs and I have used a couple here and there to get a program to work, but how far can it go? If I replaced all the Wine DLLs with ones from an original Windows installation would it be that much more compatible? I doubt that it would be that easy, but I'm just curious to see if anyone knows.

ONLY use Windows/third party DLL files if a program explicitly asks for them. There are a few other rare occasions where you MAY need to use native DLLs rather than Wine's own (msxml3, Direct Play, etc) but those are rare. Using native DLLs for no reason will just break Wine.

---

### Post by botulismo on 2007-05-12
That's what I kind of imagined or else others would end do it more often... Really I have no need for Windows programs other than a game or two, but mostly I use the Wii and PS2 for that. Thanks for the answer guys.

---

