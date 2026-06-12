---
title: "Funkty Firefox Fonts With .Fonts Folder"
date: 2006-07-06
forum: Desktop Environments
---

### Post by atoponce on 2006-07-06
Why is this?  When I create a .fonts folder with new fonts, and I relaunch Firefox, it picks an odd one, and uses that for rendering ALL pages.  This is very annoying.  Changing 'Edit --> Preferences --> Content --> Fonts & Colors' does absolutely nothing.

In my case, I have 6,760 fonts in my ~/.fonts folder.  I would like to use these fonts in OpenOffice.org, etc.  However, Firefox picks a specific font everytime it is launched.  The font Firefox chooses to use when that folder is available is 'illusion.ttf'.  This makes reading the text on the sites very difficult.  I would much rather just use my 'Bitstream Vera Sans.ttf' font.

If I rename the ~/.fonts folder, say to ~/.fonts2, then I no longer have any issues, and everything is fine in Firefox when rendering pages.

Has anyone else experienced this problem?  If so, how do you fix it?  Your help is appreciated.

Thanks.

---

### Post by atoponce on 2006-07-06
Here are some screenshots of what I am going through.  The funky screenshot is when the ~/.fonts folder exists, and the normal screenshot is when it doesn't.  Hope this helps.

---

### Post by atoponce on 2006-07-08
I have figured it out if anyone else stumbles across this, at least partially anyway.

The Microsoft True Type Core Fonts need to be installed, in order to render Verdana, Comic Sans Serif and other commonly used web page fonts.  You will need multiverse enabled for these fonts.

```
sudo aptitude install msttcorefonts
```

I still don't know, however, why I can't override the site design font in Firefox with a specified font.  Seems silly, if you ask me.

---

