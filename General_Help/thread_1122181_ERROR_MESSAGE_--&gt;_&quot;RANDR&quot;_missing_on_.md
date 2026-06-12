---
title: "ERROR MESSAGE: --&gt; &quot;RANDR&quot; missing on display &quot;:0.0&quot;"
date: 2009-04-10
forum: General Help
---

### Post by riwa on 2009-04-10
I'm trying to run a mapmaking program which I downloaded as a .rpm and converted with alien to a .deb file. Then I installed the .db file with dpkg. When I start the program it goes to a menu to what game you want to create a map for but when the actual working tool starts it spams this message: 

--> Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated


When I checked the console I found this

```
Xlib:  extension "RANDR" missing on display ":0.0".
Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
//[Gtk-WARNING ** Keeps spamming over the console]
```

I know I've seen this message (Xlib: ext..) many times before but I have never noticed a problem before. The program crashed and returned a run-time error.

---

