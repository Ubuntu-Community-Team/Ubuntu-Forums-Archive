---
title: "how do I find the path to firefox?"
date: 2009-03-04
forum: General Help
---

### Post by phatjonny on 2009-03-04
Dear forum

A very noob question,  Can anyone help me locate the path to firefox.  I really can't fnd it.

Thanks, as always

---

### Post by mb_webguy on 2009-03-04
Type "whereis firefox" in the terminal.  This will show you the installation directories for Firefox.  The executable will be in the /usr/bin directory.

If you're ever not sure of the actual command used to run an application, and therefore don't know what to use with the "whereis" command, if there's a launcher in your Applications menu you can right-click on the menu, select Edit Menus, and look at the properties of the launcher.

---

### Post by mcduck on 2009-03-04
You can use "which", it gives path to program's executable. In his case running "which firefox" would return "/usr/bin/firefox".

Anyway, almost every program intended for normal users put their executables in /usr/bin.

---

### Post by yther on 2009-03-04
Also, typing "which firefox" in a terminal will give you the complete path to the executable.  (In the case of multiple versions floating around, it returns the first one it finds, which it gets by searching your PATH from first to last.)

So, **whereis** will show you various directories that contain "firefox stuff" and **which** shows you the exact file that the system will run for you.

*Edit: [waves to mcduck]*

---

### Post by phatjonny on 2009-03-04
Thanks to all above, I have found the path, and yes it is indeed 
/usr/bin/firefox  But when I add it to writer's tools for OpenOffice 3.0 it still is not connecting OO to the web, any ideas?

	' Unix
	Case 4
		ReadBrowserPath()
		/usr/bin/firefox

---

### Post by ryan.nabinger on 2009-03-04
and the ultimate:
slocate firefox

and the super ultimate:
find / -name "firefox" 2>/dev/null

("2>/dev/null" will redirect the annoying errors (for dirs you don't have permissions))

---

