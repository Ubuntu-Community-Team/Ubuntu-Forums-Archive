---
title: "Noob - How to Run a Program From a Menu?"
date: 2009-04-26
forum: General Help
---

### Post by rich1939 on 2009-04-26
I'm a relatively new programmer for Ubuntu (Gnome) and I created a program using Gtk+ and PostgreSQL that I'd like to run from the "Applications" menu. I tried to create a Launcher for it, but when in the Command box I enter the path to my program (e.g., ~rich/programs/myProgram) it won't execute, but when I browse to that same directory from the "Places" menu and double-click the program entry, it runs fine.

How do I put my program into the Applications Menu so that it will run when I choose it (just like other programs there)?

---

### Post by mb_webguy on 2009-04-26
If what you posted is the path you're giving it, it will never work.

The tilda ("~") stands for "/home/*your_user_name*".  So "~rich/programs/myProgram" actually means "/home/richrich/programs/myProgram", which I'm pretty sure isn't the right path.

Use either "~/programs/myProgram" or "/home/rich/programs/myProgram".  Better yet, use the Browse button in the launcher dialog to locate the program.

---

### Post by rich1939 on 2009-04-27
> **mb_webguy said:**
> If what you posted is the path you're giving it, it will never work.


I'm sorry that I was trying to simplify the path I was using. It's actually the following:

```

/home/richard/Documents/Development/CBsolotime/solotime/bin/Release/

```

So...when I open a Terminal window to that directory and type ./solotime, it runs fine, but when I put the path and the program-name into the Launcher, it doesn't run.

If I navigate to that same directory and double-click the "solotime" executable, it runs fine.

So what I need is some way to get "solotime" to run from a menu. Sorry for misinforming you about the actual path...but I need some help to meke this program run like any other that appears in the Applications menu. It needs access to files in the target directory also, so if I need to move it somewhere else, I also need to move those files.

Hope that makes everything clearer.

---

### Post by mb_webguy on 2009-04-27
In that case....  That's weird.  A launcher for a command should be no different from entering the command itself.  What happens when you try to add a launcher for the program to the panel rather than to the Applications menu?

EDIT:  And I'm assuming the *actual* actual path you're using is "/home/richard/Documents/Development/CBsolotime/solotime/bin/Release/solotime", rather than "/home/richard/Documents/Development/CBsolotime/solotime/bin/Release/", which simply points to the directory, and not the program...

---

### Post by rich1939 on 2009-04-27
> **mb_webguy said:**
> In that case....  That's weird.  A launcher for a command should be no different from entering the command itself.  What happens when you try to add a launcher for the program to the panel rather than to the Applications menu?

EDIT:  And I'm assuming the *actual* actual path you're using is "/home/richard/Documents/Development/CBsolotime/solotime/bin/Release/solotime", rather than "/home/richard/Documents/Development/CBsolotime/solotime/bin/Release/", which simply points to the directory, and not the program...

Yes. I did include the program in the Launcher's path. One question: Does the Launcher change to the target path before executing the program? If not, then maybe that's my problem. If that's the case, then how do I change to that directory before launching the program....using the Launcher.

I'll try putting in in the Panel, although I'll have to learn how to do that too. This is really weird because I've been programming for over 40 years and now I feel like a complete NOOB when switching to Linux. :)

---

### Post by Brucevdk on 2009-04-27
> **rich1939 said:**
> Does the Launcher change to the target path before executing the program?

It does not, also I'm not sure if it's a good idea to make your application depend on being launched from the installation directory (or at least the directory in which the executable can be found). 

Also here's my understanding of how the applications menu works. Applications provide .desktop files or launchers and install these into /usr/share/applications (globally) or possibly ~/.local/share/applications (locally). These directories are defined in the [XDG Base Directory Specification](http://standards.freedesktop.org/basedir-spec/basedir-spec-latest.html). Here's an example of a .desktop file:

```

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=true
Name=Test Menu Item
Exec=/home/bruce/bin/test-menu-item
Categories=Utility;

```

The categories define under which category the item is sorted. The menu itself is build by including all the .desktop files from the earlier mentioned directories, the configuration file for this is /etc/xdg/menus/applications.menu. The relevant snippet is:

```

<!-- Read standard .directory and .desktop file locations -->
<DefaultAppDirs/>
<DefaultDirectoryDirs/>

```

For more information see the [Desktop Menu Specification](http://standards.freedesktop.org/menu-spec/latest/).

Hope this information is of any use to you.

---

### Post by rich1939 on 2009-04-27
> **Brucevdk said:**
> It does not, also I'm not sure if it's a good idea to make your application depend on being launched from the installation directory (or at least the directory in which the executable can be found). 


Okay, thanks. It seemed as though that was what was happening. I guess I'll have to modify my program to take that into account.

Thanks again.

---

