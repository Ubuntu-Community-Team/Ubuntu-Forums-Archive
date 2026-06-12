---
title: "Applications - simple question"
date: 2009-02-25
forum: General Help
---

### Post by DeadRobot on 2009-02-25
I know in Windows applications are .exe and in OSX applications are .app but what exactly are they in Ubuntu?

---

### Post by mb_webguy on 2009-02-25
They aren't anything.

Linux doesn't rely on file extensions to determine what the file is or does.  Any file can be executable, though of course only scripts or application binaries will actually do anything.  Generally, executables in Linux don't have a file extension, though you may occasionally encounter .sh (for shell scripts) and .bin (for binary exectuables).

Programs are located in one of several places, depending on how they were installed, which makes it easier to determine where the programs came from and how to remove or update them.

Programs installed using a package manager (which should be the vast majority of them) are located in the /usr directory, with the executables in /usr/bin and data in /usr/share.  

Programs compiled from source or installed from deb files or an installer are located in either /usr/local (with executables in the /usr/local/bin directory and data in the /usr/local/share directory) or less often the /opt directory.

Programs intended to be used only by a specific user are located in that user's ~/bin directory, though this is generally only for scripts created by the user.

---

### Post by Peter09 on 2009-02-25
There is no default executable extension in Linux. No file by default can be executed. To execute a file the 'execute' bit must be set using the command 'chmod'. Therefore any file name can be an executable file, with or without an extension.

This is considered a security strength of Linux in that before a file can be executed the user must be involved (or a secure task) in changing its permission.

---

### Post by mb_webguy on 2009-02-25
> **Peter09 said:**
> To execute a file the 'execute' bit must be set using the command 'chmod'.

... or by right-clicking on the file in your file manager, clicking Properties, then the Permissions tab, and changing the file permissions.

---

