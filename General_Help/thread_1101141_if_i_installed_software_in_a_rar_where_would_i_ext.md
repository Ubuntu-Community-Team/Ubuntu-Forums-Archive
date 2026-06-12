---
title: "if i installed software in a rar where would i extract it?"
date: 2009-03-20
forum: General Help
---

### Post by bilmas on 2009-03-20
i am used to using .deb files to install things i download but this is in a rar archive and it's a folder. i tried extracting the folder to my home folder and then adding both what i thought to be the main file and the .bin file to my application menu but that didn't work.  is there somewhere special this has to be?

---

### Post by hansdown on 2009-03-20
Hi bilmas.

This should help.

[http://www.google.ca/search?q=install+software+in+a+rar++file+in+ubuntu+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=install+software+in+a+rar++file+in+ubuntu+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by mb_webguy on 2009-03-20
If you get a .bin file, it's usually an installer.  If this is the case, right-click on the file and select Properties.  Go to the Permissions tab and make the file executable, then close the Properties window.  Now double-click on the .bin file to execute it.  Depending on the application, you may need to run the installer with superuser privileges.  If this is the case, then open the terminal and type "sudo /path/to/installer.bin", substituting the actual path and filename as appropriate.

If the .bin file isn't an installer, then you just need to put the file somewhere in your PATH.  A good place for programs only your user account needs to run is in a directory called "bin" in your user's home directory.  Open your home directory in the file manager.  Right-click and create a new folder named "bin".  Copy the .bin file to this folder, then right-click on it and make it executable as described above.  You can remove the .bin extension if you want, since Linux doesn't care about file extensions.  You should now be able to run the application by opening the terminal or Run Application dialog (Alt+F2) and entering the name of the file.  You can make a launcher for it in the Applications menu if you want by right-clicking on the menubar and selecting "Edit Menus".

---

