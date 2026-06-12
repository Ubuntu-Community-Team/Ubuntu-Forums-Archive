---
title: "mouse window focus behavior GNOME3 - layers,transparency,etc."
date: 2012-04-06
forum: Desktop Environments
---

### Post by miatawnt2b on 2012-04-06
I used the Advanced Settings applet to set my window focus to automatically activate teh window when the mouse is over the window.  However, one thing I don't like is that the behavior will actually bring the window to the front as well.  I really liked how I had things set up in Gnome2 with compiz where the mouse pointer would grab window focus, but the window would remain on the same 'layer' In addition, I had compiz set up to make background windows varying degrees of transparency so I could see layered windows.

Is there any way to regain this functionality in Gnome3?

---

### Post by miatawnt2b on 2012-04-24
anyone?

---

### Post by kevinmchapman on 2012-04-24
The option is hidden away in Dconf-Editor in the path:

org/gnome/desktop/wm/preferences

Change focus-mode to "sloppy" or "mouse". They both seem to work the same as far as I can see

---

### Post by miatawnt2b on 2012-04-25
The issue isn't that I can't make mouse focus work at all, it is working, though I do admit sloppy and mouse work exactly the same. 

My issue is that when mouse grabs focus, it will bring teh window to the front. I do not want this to happen. I want the window to remain in the background. Additionally I would like layered trancparency for my windows.

-J

---

### Post by kevinmchapman on 2012-04-25
OK, I see what you mean. Yes, if you click on a window "under" another, it raises it, but if you simply scroll the lower window it does not raise it.

This is different from E17, which I mainly use. I have that set up to raise only on clicking the title bar. Clicking elsewhere (to cut and paste, for example) just gives focus, which is far more efficient for me. I don't think Gome allows this, yet at least.

---

### Post by zph7 on 2012-09-14
- install gconf-editor:
sudo apt-get install gconf-editor

- open gconf-editor

- under apps->metacity->general
  there is an auto_raise option; turn this off

---

### Post by kevinmchapman on 2012-09-15
I have no auto-raise option anywhere in gconf-editor.

There is an option in dconf, but it is already unchecked.

---

### Post by ykanello on 2012-10-14
@zph7
Thanks that worked for me!
Y

---

