---
title: "Can't make .exe file executable for wine"
date: 2011-05-02
forum: Desktop Environments
---

### Post by shaquille on 2011-05-02
Hello friends, I am using Ubuntu 10.10. I installed wine but till now I didn't use it. Now when I am trying to use it, it ask executable file. So, I tried to make the .exe file executable. I went to the "Properties" of the file --> went to the "Permission" tab. Then when I try to put Tick mark on "Allow executing file as program" I failed. It seems the box don't want to be black!!!! I just cannot put tick mark. So, wine cannot execute any .exe file. 
Please help me.

---

### Post by Morbius1 on 2011-05-02
As it turns out you don't have to mark it executable to run on Wine. It's not Wine that's throwing the error it's something called cautious-launcher.

I'll give you 3 ways to circumvent the problem:
**[1] Run it from the terminal:**
```
wine "/path/to/exe/file"
```**[2] Fix the file association:**
Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as  the default ( from the Wine that's already selected) and every time you run an exe it should select the wine without the cautious  launcher script.

**[3] Fix it at it's source:**
Open up as root "Properties" on /usr/share/applications/wine. 

What you will see is this:
> cautious-launcher %f wine start /unixChange it to this:
> wine start /unixI would go with option [2] myself. I don't like messing with system files unless I really have to.

---

### Post by shaquille on 2011-05-02
> **Morbius1 said:**
> As it turns out you don't have to mark it executable to run on Wine. It's not Wine that's throwing the error it's something called cautious-launcher.

I'll give you 3 ways to circumvent the problem:
**[1] Run it from the terminal:**
```
wine "/path/to/exe/file"
```**[2] Fix the file association:**
Right click an *.exe file and select Properties  -> Open With -> Add -> Use a custom command > type in:  wine

In the "Open With" tab mark the "wine"[COLOR=Black] [COLOR=Blue]**you added**[/COLOR] [/COLOR]as  the default ( from the Wine that's already selected) and every time you run an exe it should select the wine without the cautious  launcher script.

**[3] Fix it at it's source:**
Open up as root "Properties" on /usr/share/applications/wine. 

What you will see is this:
Change it to this:
I would go with option [2] myself. I don't like messing with system files unless I really have to.

Thanks a lot!!! It worked!!!!!!!

---

### Post by MossMethod on 2011-07-23
I can not figure how to do step number 2 with Gnome 3. custom command box does not come up and when I click wine it does not change the file to be able to run as exe this is frustrating.

With Gnome 3 is it impossible to get command line box bacK?

---

