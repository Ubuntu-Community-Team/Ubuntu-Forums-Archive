---
title: "Change splash screen background color."
date: 2007-12-27
forum: Desktop Environments
---

### Post by X40nick on 2007-12-27
Hi,

I have gone for the Blue look with Ubuntu, everything is now blue! Except the splash screen background.

I have changed the color in Login Window properties, but I still have the default brown/orange? Yet before the log-in theme comes up, I have my desired blue color?

This is confusing and really annoying me!!!

Thank you so much.

Nick.

---

### Post by AlexOK on 2007-12-27
Read this

[http://ubuntuforums.org/showthread.php?t=477704&highlight=brown&page=2](http://ubuntuforums.org/showthread.php?t=477704&highlight=brown&page=2)

> Based on what I've read, it seems like commenting the following lines out in "/etc/gdm/PreSession/Default" seems to solve the problem and the color then the color should be left at whatever color is set as the login screen background until the desktop loads.

Quote:
# Default value
#if [ "x$BACKCOLOR" = "x" ]; then
# BACKCOLOR="#dab082"
#fi

#"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
Jake

---

### Post by X40nick on 2007-12-27
Thank you so much! I really am grateful for your help! 

THANK YOU!

Nick.

---

### Post by Girindor on 2008-01-12
that really helped me too, thanks! :-)

---

### Post by Dark Hornet on 2008-01-15
--Yes..this helped me a ton as well...that was really annoying me.

---

### Post by Nythain on 2008-02-12
amazing, thanks a million... orange just didnt fit well with neutronium black :P

---

### Post by theZoid on 2008-06-28
> **AlexOK said:**
> Read this

[http://ubuntuforums.org/showthread.php?t=477704&highlight=brown&page=2](http://ubuntuforums.org/showthread.php?t=477704&highlight=brown&page=2)

This hosed my X in Ubuntu Hardy...beware :D

---

