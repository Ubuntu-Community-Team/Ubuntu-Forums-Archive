---
title: "Xmacro????"
date: 2005-12-25
forum: Desktop Environments
---

### Post by tane_stelzer on 2005-12-25
Okay since no one has really answered my other threads, I have sat down and tried to figure out what Xmacro is all about, now i know what this -s option is and how to use it. Just one last question. at the end of the command in my case xmacro -d 3000 -s 1.0 -k 54 remote_display. Well i know remote_display is not right and i know i have to substitute it for sth like bar:0.0 where bar is the computer name or? in my case ubuntu. Well now the only thing i dont understand is the 0.0 what no is that supposed to be, it is not my ip adderess cos i tried it and got error. am i right up until now? Please someone reply me this time, i am sure someones know sth in this forum, i am already frustrated enough with this!!!!
Tane
P.S I have already asked this question and related in onces in The Absolute Beginners Forum but no one can help me hopefully someone can help me here!!!!

---

### Post by Ocxic on 2005-12-25
i think 0.0 means screen 0 desktop 0, as you have multiple desktops you can switch too, but that is only a guess, so don't be suprised if i'm wrong.

---

### Post by tane_stelzer on 2005-12-25
and bar is the computer name or? I am really dont know, so should i put in 1.1 instead of 0.0??? Is that right I just really am confused with this and no ones seems to know.

---

### Post by neko18 on 2008-06-19
Sorry to revive a really old thread, but I was having the same problem. I figured it out though. To get the name of your display, type this into a terminal:
```
echo $DISPLAY
```

So, to use an XMacro script, you would run:
```
xmacroplay "$DISPLAY" < script_file.txt
```

To record an XMacro script, run:
```
xmacrorec2 > script_file.txt
```

---

