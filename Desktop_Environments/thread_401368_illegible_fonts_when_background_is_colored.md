---
title: "illegible fonts when background is colored?"
date: 2007-04-04
forum: Desktop Environments
---

### Post by bcrowell on 2007-04-04
I have a fresh install of Edgy, on a system with an LCD monitor. In the initial install, all the sans serif fonts were extremely ugly and hard to read. Turning on sub-pixel smoothing improved the situation quite a bit. However, the fonts still look really bad and hard to read when the background is not white. For example, on the ubuntuforms site, there are some headers in which text is displayed on a brown or blue background, and it's extremely hard to read. Also, the firefox menus have a gray background, and suffer from the same problem. Here is an example of what I'm talking about:

[IMG]http://www.lightandmatter.com/font_problem.png[/IMG]

I don't know if it will look the same to other people on their monitors, but on mine, I get a white halo surrounding every letter. In the sample image I gave, I see the halo around the letters in the brown box that says "Welcome, Bcrowell," and also in the blue box that says "No tags were found." Strangely, I do *not* see the problem in the dark brown box, presumably because it's white text on a darker background.

Can anyone suggest how to fix this?

As a band-aid fix, it would probably help if I could figure out how to make the background color of firefox's menus white rather than gray. However, it still wouldn't help me in other situations where text is displayed on a colored background, e.g., on the ubuntuforums pages. This doesn't appear to be just a firefox issue. It also happens, for example, in the menus displayed by my window manager.

TIA!

-Ben

---

### Post by bcrowell on 2007-04-04
OK, I at least managed to do the bandaid fix of making the background menu color be white in firefox. Maybe this will be helpful to other people. Here [http://www.mozilla.org/unix/customizing.html](http://www.mozilla.org/unix/customizing.html) is information about customizing firefox. To get white backgrounds in firefox's menus, I went into the directory ~/.mozilla/firefox/default.1fy/chrome , did a "cp userChrome-example.css userChrome.css" , and added the following lines to the userChrome.css file:

```
menubar, menubutton, menulist, menu, menuitem {
    background            : white !important;
}

menupopup > * {
    background            : white !important;
}


```

I would still be grateful to anyone who could enlighten me about how to fix the underlying problem, which seems to be new in Edgy -- I never experienced it in Breezy.

---

### Post by timken240 on 2008-05-01
Thanks for the help !
I couldn t read my firefox 3 menus, now I can 
:guitar:

---

