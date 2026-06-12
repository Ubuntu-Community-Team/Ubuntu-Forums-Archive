---
title: "Compiz help."
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by phizikal on 2007-07-01
Okay, I am not a total newb. But I never tried to mess with compiz, yes I have direct rendering.

when i run compiz.

_____________

root@admin:/home/admin# compiz.real: No composite extension

---

### Post by phizikal on 2007-07-02
no help at all?

---

### Post by hyperair on 2007-07-02
Well it seems you haven't really addressed your issue correctly. For one thing, you haven't even stated what problem you're having! It's not a surprise really that nobody has replied your post.

---

### Post by pingpongboss on 2007-07-02
first of all, good luck with your problem. I don't know enough to help you

second, the other poster is right. You should include more info that would help others diagnose your problem.

---

### Post by dwebb86 on 2007-07-02
No composite extension?
I think I might know what's wrong....

run the command **sudo gedit /etc/X11/xorg.conf**

go down to the very bottom and add this:
[B]
Section "Extensions"
     Option           "Composite" "Enable"
EndSection
[/B]
Save the file and try compiz again, you might have to restart X (CTRL ALT Backspace)

That might do it for you, you didn't give much information, but I've been through hell the past week trying to install Compiz perfectly, and that seems like it might do the trick.
Give more info if it doesn't work out, and we'll answer again.

---

