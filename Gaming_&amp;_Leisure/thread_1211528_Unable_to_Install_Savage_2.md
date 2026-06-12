---
title: "Unable to Install Savage 2"
date: 2009-07-12
forum: Gaming &amp; Leisure
---

### Post by MasterNetra on 2009-07-12
Hey all tryin to install Savage 2 from .bin and thus far is a no go. And yes the "Allow executing file as program" is selected. Tried to sh it in term, no go, tried double clicking, no go. 
When double clicking a error box pops up saying file is of a unknown type.
and in term..
```

Me@Mycomputer:~$ sudo sh ~/Savage2Install-2.1.0-i686.bin
/home/Me/Savage2Install-2.1.0-i686.bin: 1: Syntax error: "(" unexpected

```

thoughts?

---

### Post by Vakman on 2009-07-12
All right. So save Savage 2 installer to the desktop. Then open up a terminal. ```
cd ./Desktop
```
Next ```
chmod +x Savage2Install-1.3.99-i686.bin
``` or the x64 version if that is the one you have. Lastly run ```
sudo ./Savage2Install-1.3.99-i686.bin
``` 
Then the installer will pop up. Post back :)

---

### Post by MasterNetra on 2009-07-12
> **Thisislaw said:**
> All right. So save Savage 2 installer to the desktop. Then open up a terminal. ```
cd ./Desktop
```
Next ```
chmod +x Savage2Install-1.3.99-i686.bin
``` or the x64 version if that is the one you have. Lastly run ```
sudo ./Savage2Install-1.3.99-i686.bin
``` 
Then the installer will pop up. Post back :)

Well Its in my home directory so that I don't have to cd to it..I did mention that it is essentially +x in my first post but, I see now what I did wrong...sh instead of ./ >.<

---

### Post by MasterNetra on 2009-07-12
Lovely its installed...now it CTDs every time I try to run it. >.<

---

### Post by Vakman on 2009-07-12
> **MasterNetra said:**
> Well Its in my home directory so that I don't have to cd to it..I did mention that it is essentially +x in my first post but, I see know what I did wrong...sh instead of ./ >.<

Of course I read your post and it was not automated :P. I am glad you edited. I sent this because you were doing sh. Now then, CTD means...?
Crash to desktop?

---

### Post by MasterNetra on 2009-07-12
> **Thisislaw said:**
> Of course I read your post and it was not automated :P. I am glad you edited. I sent this because you were doing sh. Now then, CTD means...?
Crash to desktop?

Yeap.

---

### Post by Vakman on 2009-07-12
By the way, what graphics card do you have?

---

### Post by MasterNetra on 2009-07-12
> **Thisislaw said:**
> By the way, what graphics card do you have?

*points to his signature*

---

### Post by Vakman on 2009-07-12
> **MasterNetra said:**
> *points to his signature*

xD Didn't even notice. And we may have a problem here. As far as I know you can't run this with Intel since (last I checked) the driver does not support OpenGL 2.0 or later. But that was in April not sure of now. Try opening .savage2\startup.cfg and turn "xrand" from "true" to "false" at the video section, this fixed someone else's issue in the forums but he had an  card. Can't hurt to try. Your problem is likely the Intel driver.

---

### Post by Vakman on 2009-07-12
> **Artificial Intelligence said:**
> Any chance you're using a intel card? If so you can't run savage 2 at the moment, as the intel driver doesn't support OpenGL 2.0 or later.
Is from the thread I found this post. He is right, just not sure if they are supported now.

---

### Post by MasterNetra on 2009-07-12
Made the attempted and it ended in failure so I'll take it as a no. :/

---

### Post by Vakman on 2009-07-12
Check out this thread [http://ubuntuforums.org/showthread.php?t=1189557](http://ubuntuforums.org/showthread.php?t=1189557)
New installers or something at the end, one day ago. Worth a shot.

---

### Post by MasterNetra on 2009-08-30
> **Thisislaw said:**
> Check out this thread [http://ubuntuforums.org/showthread.php?t=1189557](http://ubuntuforums.org/showthread.php?t=1189557)
New installers or something at the end, one day ago. Worth a shot.

Thanks. (lol sorry for the lengthy delay.)

---

### Post by Vakman on 2009-09-01
> **MasterNetra said:**
> Thanks. (lol sorry for the lengthy delay.)

:lolflag: That is okay, glad it worked :)

---

### Post by MasterNetra on 2009-09-02
> **Thisislaw said:**
> :lolflag: That is okay, glad it worked :)

It didn't tryed the one that is supposed to be for 32bit and it claims its wrong architecture. And I am running Ubuntu 9.04 (32bit). So nope didn't work. :p

---

