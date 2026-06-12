---
title: "wine problems :("
date: 2006-09-27
forum: Gaming &amp; Leisure
---

### Post by haxer on 2006-09-27
Hello i have problem with wine i have installed toribashi on "c" in wine but when i open up terminal and types in wine toribash then it says wine: could not load L"c:\\windows\\system32\\toribash.exe": Module not foun

---

### Post by Shay Stephens on 2006-09-27
You need to specify the whole path:

wine "c:\path\to\app"

Use the quotes, especially if the path has any spaces in it.

---

### Post by haxer on 2006-09-27
Ok so C:/Programfiles/terobashi?

---

### Post by Shay Stephens on 2006-09-27
> **haxer said:**
> Ok so C:/Programfiles/terobashi?

Well more like this:
```
wine "c:\Program Files\terobashi\filename.exe"
```

You have to use wine, then the quotes to contain the full path.  And with windows, you have to use the backslash.  And you need to specify the program file to run.  I just used the generic filename.exe, use whatever real program name you need.

---

### Post by haxer on 2006-09-27
Thanks :) but i get this 


oem@haxer:~$ wine c:\Program Files\terobashi\terobashi.exe
wine: cannot find 'c:Program'
oem@haxer:~$

---

### Post by Shay Stephens on 2006-09-27
That's because you are not putting the path in quotes like I have mentioned and shown twice now.

---

### Post by delta99 on 2006-09-27
Shouldn't it be more like:
```

wine "/home/haxer/.wine/c/Program Files/terobashi\terobashi.exe"
```

---

### Post by CAUSTICROUTER on 2006-09-27
I couldn't figure out how to CD to a directory with spaces in it at first, so I just renamed Program Files program_files. I also noticed that it is cap sensitive.

---

### Post by Shay Stephens on 2006-09-27
Yes, you are right.  Here is the properties for the icon I have to load Photoshop 7.

```
wine '/home/shay/.wine/drive_c/Program Files/Adobe/Photoshop 7.0/Photoshop.exe'
```

Stupid me, I forgot the whole path includes the home directory, and I borked the slashes by thinking they were back slashes ;-)

That's what I get for posting without verifying ](*,)

---

### Post by DeVelaine on 2006-09-27
Another nice tactic for running a program through Wine is to create a launcher for it. That way you can make the launcher put the correct path in using whichever of the four correct path options is needed to run the file.

---

