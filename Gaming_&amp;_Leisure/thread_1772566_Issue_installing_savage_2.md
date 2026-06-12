---
title: "Issue installing savage 2"
date: 2011-05-31
forum: Gaming &amp; Leisure
---

### Post by -gabe-noob- on 2011-05-31
Hi when installing savage 2, after marking it as an executable and typing the following code in terminal: 


gabriel@gabriel-GA-MA790X-UD4P:~/Downloads$ ./Savage2Install-2.1.0.1-x86_64.bin

(<unknown>:7646): Gtk-CRITICAL **: IA__gtk_text_attributes_ref: assertion `values != NULL' failed

(<unknown>:7646): Gtk-CRITICAL **: IA__gtk_text_attributes_ref: assertion `values != NULL' failed
Segmentation fault
gabriel@gabriel-GA-MA790X-UD4P:~/Downloads$ 

I get that seg fault, is there something I'm doing wrong?

---

### Post by Soulcage on 2011-06-02
Did you remember to ```
chmod +x Savage2Install-2.1.0.1-x86_64.bin
```?
Only thing I can think of... Though it probably would of said as much.

---

### Post by -gabe-noob- on 2011-06-02
yeah thats just the code that makes it executable isn't it?

---

### Post by lengau on 2011-07-30
What Gtk theme are you using? I believe this is an issue with certain Gtk themes.

You can try the following command as a workaround to get it working:

GTK2_RC_FILES=/usr/share/themes/Default/gtk-2.0-key/gtkrc ./Savage2Install-2.1.0.1-x86_64.bin

That will run the installer with the default Gtk theme, which seems to work.

If you're a KDE (Kubuntu) user, the bug has been reported [on the KDE bug tracker]("https://bugs.kde.org/show_bug.cgi?id=278874").

---

### Post by -gabe-noob- on 2011-07-31
> **lengau said:**
> What Gtk theme are you using? I believe this is an issue with certain Gtk themes.

You can try the following command as a workaround to get it working:

GTK2_RC_FILES=/usr/share/themes/Default/gtk-2.0-key/gtkrc ./Savage2Install-2.1.0.1-x86_64.bin

That will run the installer with the default Gtk theme, which seems to work.

If you're a KDE (Kubuntu) user, the bug has been reported [on the KDE bug tracker]("https://bugs.kde.org/show_bug.cgi?id=278874").

I swap between DE's, WM. To play games and install games I use openbox, so I think it might be the GTK theme issue because I have Kubuntu-Desktop installed and thats usually my work environment. Thanks for the tips.

---

### Post by -gabe-noob- on 2011-07-31
Found it, and its working. THANK YOU SO MUCH SIR <3

---

