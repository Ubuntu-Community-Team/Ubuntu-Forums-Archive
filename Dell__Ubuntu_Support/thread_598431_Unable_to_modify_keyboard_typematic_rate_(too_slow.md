---
title: "Unable to modify keyboard typematic rate (too slow)"
date: 2007-10-31
forum: Dell  Ubuntu Support
---

### Post by Skure on 2007-10-31
Well, since I am using an Optiplex 745 I'll try here.

I use kubuntu /7.10 and I really only have one problem. The keyboard repeat rate is far  too slow and I am unable to increase it.

It is mot likely not an X thing as the rate is equally slow  in a console. If I use 
"xset r rate 500 20" then  "xset q" reports back "auto repeat:  on" and "auto repeat delay:  500    repeat rate:  20"  but the rate is far slower than indicated. Setting this form the UI control in KDE does not help either,

So is there a setting or command somewhere else I should check?

---

### Post by Skure on 2007-10-31
Ok, there was one thing I did not test before I made the initial question. I was using a keyboard with a PS/2 connector and thus a P2/2 to USB converter. That seems to be the reason. I have now tested with a "native" USB keyboard and the keyboard rate increased immediately and can be controlled as normal.

---

