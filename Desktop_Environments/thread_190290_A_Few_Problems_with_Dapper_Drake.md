---
title: "A Few Problems with Dapper Drake"
date: 2006-06-06
forum: Desktop Environments
---

### Post by srunni on 2006-06-06
I have used Breezy Badger a little in the past, and I just upgraded to Dapper Drake. I'm running it through an XP VMWare installation. I've run into two problems so far:

1. The highest resolution that my 19" LCD monitor supports and looks the best in is 1280x1024. I went to System -> Preferences -> Screen Resolution, but the highest available resolution is 1024x768. Is there anyway to change this, because I can't use Ubuntu in full screen mode until then?

2. This is a problem I ran into with Breezy Badger as well; the version of Firefox that comes with the CD is 1.5.0.3, while the newest version of Firefox is 1.5.0.4. The "Check for Updates" feature in Firefox is grayed out, so that won't work. Is there any other way that I can easily upgrade to Firefox 1.5.0.4, or do I have use the terminal again? If so, could someone who has figured this out post exactly what commands they entered?

Thanks a lot in advance!

---

### Post by oyvindaa on 2006-06-06
For your Firefox question, check this one:

[http://ubuntuforums.org/showthread.php?t=186337&highlight=firefox+1.5.0.4](http://ubuntuforums.org/showthread.php?t=186337&highlight=firefox+1.5.0.4)

---

### Post by srunni on 2006-06-06
Thank you SO much. I always like to have the newest version of open source stuff like Firefox. Does anyone know the answer to my screen resolution question?

---

### Post by oyvindaa on 2006-06-06
There's a program in Synaptic called '915resolution'.

Try that.

---

### Post by srunni on 2006-06-06
I did, and it gave me an error message about not properly detecting the Intel chipset; maybe this is because I'm running Ubuntu as a guest OS.

---

### Post by oyvindaa on 2006-06-06
Oh, right. I didn't notice the VMWare part of your post. I'm sorry, I'm unable to help you then. 

I'm sure someone else can though.

---

### Post by srunni on 2006-06-06
Well, thanks a lot anyway, I emailed the guy that made 915resolution and I'll see what he says.

---

### Post by Melvil on 2006-06-06
You might try to edit the /etc/X11/xorg.conf and add 1280x1024 as a resolution there

---

