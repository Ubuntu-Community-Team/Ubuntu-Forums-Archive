---
title: "xfig hand pointer problem!"
date: 2008-02-29
forum: Desktop Environments
---

### Post by ravikumar on 2008-02-29
How do i change hand pointer xfig.So that it should show index finger. Currently it shows all the finger. I was using it in older version of red hat. Now i moved to Ubuntu Gusy Gibbon.Its urgent please help me. 

Thanks

---

### Post by kerry_s on 2008-02-29
i don't see nothing for that in the man pages->
[http://www.cs.duke.edu/csl/docs/xfig-man.html](http://www.cs.duke.edu/csl/docs/xfig-man.html)

you have a look maybe i missed, my eye's are tired. :)

---

### Post by ravikumar on 2008-02-29
thanks kerry_s  kerry_s,

If we couln'd change pointers in applicaton, then is there any way around to make it happen.

---

### Post by PaulFr on 2008-02-29
In w_cursor.c in xfig source code, I see

```
    arrow_cursor    = XCreateFontCursor(d, XC_left_ptr);
      bull_cursor     = XCreateFontCursor(d, XC_circle);
      buster_cursor   = XCreateFontCursor(d, XC_pirate);
      crosshair_cursor    = XCreateFontCursor(d, XC_crosshair);
      null_cursor     = XCreateFontCursor(d, XC_tcross);
      text_cursor     = XCreateFontCursor(d, XC_xterm);
      pick15_cursor   = XCreateFontCursor(d, XC_dotbox);
      pick9_cursor    = XCreateFontCursor(d, XC_hand1);
      wait_cursor     = XCreateFontCursor(d, XC_watch);
      panel_cursor    = XCreateFontCursor(d, XC_icon);
      lr_arrow_cursor = XCreateFontCursor(d, XC_sb_h_double_arrow);
      l_arrow_cursor  = XCreateFontCursor(d, XC_sb_left_arrow);
      r_arrow_cursor  = XCreateFontCursor(d, XC_sb_right_arrow);
      ud_arrow_cursor = XCreateFontCursor(d, XC_sb_v_double_arrow);
      u_arrow_cursor  = XCreateFontCursor(d, XC_sb_up_arrow);
      d_arrow_cursor  = XCreateFontCursor(d, XC_sb_down_arrow);
``` and I see in e_edit.c, the call to set pick9_cursor which by the above is XC_hand1. I do not see any app resources for this readily. So I think you may need to recompile xfig for your requirements.

---

### Post by kerry_s on 2008-02-29
hmm, i didn't get no hand, it was just my regular cursor. unfortunately it segfaulted as soon as opened the menu at the top and didn't work after that, so i just uninstalled it.

i don't know what to tell ya, i'm running a custom cursor theme(aero-extra-large) i didn't have any change at all.

the hand your describing sounds like the core theme, have you tried changing cursor themes?

my core theme is set to the aero, see pic

---

### Post by ravikumar on 2008-03-04
how to install xfig with patch level 4? And is that solves my hand pointer problem. i tried installing xfig 3.2.4, but getting errors while xmkmf. Thanks

---

