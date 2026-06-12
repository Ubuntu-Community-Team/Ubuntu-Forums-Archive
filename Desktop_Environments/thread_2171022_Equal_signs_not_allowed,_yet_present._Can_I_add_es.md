---
title: "Equal signs not allowed, yet present. Can I add escape characters?"
date: 2013-08-28
forum: Desktop Environments
---

### Post by user_of_gnomes on 2013-08-28
> Launching desktop application with an environment variable

You can add an environment variable to an application by editing its .desktop file. For example, to run "digiKam" with the environment variable APPMENU_DISPLAY_BOTH=1, find the corresponding digikam.desktop file and add the setting of the variable, via the env command, to the entry "Exec":

Exec=env APPMENU_DISPLAY_BOTH=1 digikam -caption "%c" %i

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

> 
The Exec key must contain a command line. A command line consists of an executable program optionally followed by one or more arguments. The executable program can either be specified with its full path or with the name of the executable only. If no full path is provided the executable is looked up in the $PATH environment variable used by the desktop environment. **The name or path of the executable program may not contain the equal sign ("="). Arguments are separated by a space**. 

[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

Do I have to add escape characters (and if so, how?) or am I misinterpreting the freedesktop standard?

---

### Post by mc4man on 2013-08-29
> **user_of_gnomes said:**
> 
Do I have to add escape characters (and if so, how?) or am I misinterpreting the freedesktop standard?
"The **name or path **of the executable program may not contain the equal sign ("=")"
The = sign(s) in your ex. aren't in the name or path
(I use an Exec= with an env that has = in it quite often with no issue

---

### Post by user_of_gnomes on 2013-08-29
> **mc4man said:**
> "The **name or path **of the executable program may not contain the equal sign ("=")"
The = sign(s) in your ex. aren't in the name or path
(I use an Exec= with an env that has = in it quite often with no issue

Thanks for the clarification! It seems that Wine also generates shortcuts with an equal sign present in the environment variables.

---

