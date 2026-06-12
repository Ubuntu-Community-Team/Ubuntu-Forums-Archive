---
title: "XGL - Works but with no Effects"
date: 2006-06-03
forum: Desktop Environments
---

### Post by v8YKxgHe on 2006-06-03
Hey,

I THINK i've got XGL working. Although when set the session to XGL - and go to login, it goes to login - but then after 10 seconds it shows me an error message something like 'Cann't start Display' - then it goes back to the main login screen. 

So I select Gnome session, and I can login fine. Everything seems faster, but I am not seeing any effects. If I go the the terminal and type "compiz" I get this:

compiz.real: No composite extension

What does that mean? And how can I get effects? 

Regards,

---

### Post by PriceChild on 2006-06-03
Which howto have you been following?

The end of [http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267) suggests:

> 
Section "Extensions"
          Option  "Composite" "Enable"
EndSection

At the end of your xorg.conf

---

### Post by v8YKxgHe on 2006-06-04
I was following this guide: 

[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

But I shall follow the other guide now, if you think I should? EDIT: No I wont because that's nVidia - I have ATI.

---

