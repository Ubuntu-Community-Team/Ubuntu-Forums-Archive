---
title: "How to change 'line width' for window edge resizing"
date: 2010-12-02
forum: Desktop Environments
---

### Post by spaceboy909 on 2010-12-02
This has bugged me forever.....and I mean really bugged me. The 'pixel width' is too low, such that trying to get my mouse to line up just perfectly on the window edge to get the resize icon, is very difficult.

After a bit of searching, I discovered Alt F8, which, for those that don't know, is a resize shortcut and works very well, however, I will still use the 'edge resizing' option quite a bit, and would like to widen the 'line' a few pixels.

Is this possible in a user settings file, or is this hardcoded?  I am learning to develop, so I wouldn't mind looking into this one as a beginning project.  If that's the case, could someone point me to the appropriate package?

---

### Post by bvc on 2010-12-03
What window manager and what theme? In metacity you have to edit the themes metacity-theme-1.xml file. Look for something like
```
      <distance name="left_width" value="4"/>
      <distance name="right_width" value="4"/>
      <distance name="bottom_height" value="4"/>
```Change the value=.

This is from my Clear-Alternative and Clear-Alternative-wide metacity themes. Clear-Alternative appears to have a thin border but does not. Some of the border is the same color as the gtk engine background color.

Oh, and that's for```
frame_geometry name="normal"
```There will be other 'frame_geometry's' but that's what you are looking for.

---

### Post by spaceboy909 on 2010-12-03
> **bvc said:**
> What window manager and what theme? 
Thanks for the response.  I'm using the Mist theme, and it's just a default Ubuntu/Gnome install, so I assume it's using X-Windows.  I'll take a look around and see if I can find the related files.

---

### Post by bvc on 2010-12-03
/usr/share/themes/theme_name/metacity-1/metacity-theme-1.xml

---

### Post by spaceboy909 on 2010-12-18
Ok, finally got myself setup good; thanks for the help!

I have mine set at '7'.  For those interested in seeing a more permanent 'fix' for this issue, here's the bug report page for it:  [https://bugzilla.gnome.org/show_bug.cgi?id=496536](https://bugzilla.gnome.org/show_bug.cgi?id=496536)

---

### Post by rmcd on 2011-08-15
@bvc: Thank you, thank you, thank you, thank you!

---

