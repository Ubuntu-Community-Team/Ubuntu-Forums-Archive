---
title: "Very basic WINE question"
date: 2005-10-09
forum: Desktop Environments
---

### Post by blair on 2005-10-09
I have the most basic questions regarding WINE. I have searched all the forums for WINE tips (as well as Frank's WINE corner) and the answer to these complete beginner questions are still not clear:

1. If I have a single Linux partition (plus swap of course) can I install Win32 apps on this partition using WINE?

2. If so, is this easier or harder than having a second Windows partition where I install my Win32 apps and than just access them from Linux?

3. If I have a dual boot Win/Linux system, can I access my Win apps from Linux or do I need to reinstall Win apps separately from within Linus? 

4. If WINE allows me to access Win apps on my Windows partition from within Linux, is it easier or harder to get this config working rather than reinstall the Windows apps directly to the Linux partition from within Linux and by using WINE?


thanks for your assistance.

---

### Post by Leif on 2005-10-09
I'm not a big wine user, but I'll try :

1. yes, wine creates a virtual drive for its windows

2-3-4. depends on the application. for complex ones, I don't think wine can make them work from outside

---

### Post by Zwack on 2005-10-09
You can run windows applications under wine with no windows pieces at all...
depending on the application.

If you have a windows partition you can use that instead of a virtual drive.  Wine can also use the Microsoft DLLs to provide (in some cases) better compatibility.

Not all applications work under wine.  It's worth trying them though.  I have one application that has a font issue under Wine, but it works well enough that I don't worry about it.  I am using a non MS set up...

I hope that this helps.

Z.

---

### Post by agger on 2005-10-10
If I have a Windows partition, then how do I tell wine to use the Windows installation there to run Windows apps instead of using its .wine directory?

---

### Post by Zwack on 2005-10-10
[QUOTE=agger]If I have a Windows partition, then how do I tell wine to use the Windows installation there to run Windows apps instead of using its .wine directory?[/QUOTE]

Modify .wine/config 
It's pretty well documented, and you may want to edit some of the settings from different sections.

Copy it first though... you can't be too careful.

Z.

---

### Post by Snocrash on 2005-10-11
[QUOTE=agger]If I have a Windows partition, then how do I tell wine to use the Windows installation there to run Windows apps instead of using its .wine directory?[/QUOTE]

Or....apt-get install winesetuptk. Then run winesetup. If there is a Windoze partition, it should be found. After configing wine with winesetup, it will write a new config file for you.

 -Sno

---

