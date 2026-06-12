---
title: "Inspiron 1420, 7.10 problem."
date: 2007-11-06
forum: Dell  Ubuntu Support
---

### Post by HanShot1st on 2007-11-06
I bought the Inspiron 1410 with feisty preloaded and I just recently upgraded to Gutsy 7.10.  Everything is working great, except I cannot get it to recognize my graphics card the 'Intel Graphics Media Accelerator X3100.'  Whenever I start my computer up I get a message saying that my graphics card cannot be detected and that it is running in safe mode. So if anyone can please help me shed some light on the issue it would be much appreciated. Thank you.

---

### Post by perryrt on 2007-11-10
Have you looked at the Dell wiki?

[[COLOR="blue"]http://linux.dell.com/wiki/index.php/Main_Page[/COLOR]]("http://linux.dell.com/wiki/index.php/Main_Page")

I'm not a computer guy, but...I have a sneaky suspicion that your problem might be with the way Ubuntu turned on the new 3d desktop by default in the new version.

You might want to see if this fix helps:

[[COLOR="Blue"]http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/No_Gnome_Display_Manager[/COLOR]]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/No_Gnome_Display_Manager")

It's really designed for a complete failure of the display manager (i.e. you start up in text mode only), but it might do you some good if the problem is a driver issue.

However, for the record, I'm not a programmer, you are on your own, your milage may vary, and if this idea gives you a running nose and toe fungus it's Not My Fault [-( 

Seriously, it sounds like your video driver, and that may help. Good luck!

---

