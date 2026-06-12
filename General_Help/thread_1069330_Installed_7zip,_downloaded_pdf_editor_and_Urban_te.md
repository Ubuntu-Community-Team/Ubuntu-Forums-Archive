---
title: "Installed 7zip, downloaded pdf editor and Urban terror"
date: 2009-02-13
forum: General Help
---

### Post by SVEN1 on 2009-02-13
Can't find where they went to. Any ideas?

---

### Post by mb_webguy on 2009-02-14
Apps installed from the repositories are found in the /usr directory, with the executables in the /usr/bin directory.  Apps installed from other sources may be found in either the /usr/local directory (with executables in the /usr/local/bin directory) or the /opt directory.

If you know the name of the application, you can find out where it is located with the command "whereis *application*" in the terminal.

As to your specific applications...  

Unlike the Windows version, the Linux version of 7-zip doesn't have a GUI of its own.  Instead, it acts as a module for other graphical archive managers, like File Roller (Ubuntu's default Archive Manager).  You can also use 7-zip from the command-line using the command "p7zip" or "7z" (depending on whether you installed the p7zip or p7zip-full package) from the terminal.

PDF Editor should be in your Applications menu under Graphics.  You can run it from the terminal using the command "pdfedit".

As for Urban Terror, assuming you downloaded it from [this site]("http://www.urbanterror.net/page.php?6"), the executable is in the directory where you extracted the zip file, as described on that page.  Depending on whether you're running 32- or 64-bit Linux, you need to use either the ioUrbanTerror.i386 file or the ioUrbanTerror.x86_64 file.  Make the appropriate file executable by either right-clicking on the file in Nautilus and going to Properties->Permissions, or use the command "chmod a+x */path/to/file*" in the terminal.  Then you can either run that command from the terminal by typing "/path/to/ioUrbanTerror.*version*", or you can make a launcher in the Applications menu, using the same command.

---

### Post by SVEN1 on 2009-02-15
Thought I installed the pdf editor. Managed to install it and it shows up in Graphics now.

I re-downloaded UT to my docs. where I made a folder for it. The reason the game did not install right the first time is I only installed one of 2 packages. Game runs good, spent 3 1/2 hours playing.

Still a rank newbie with Ubuntu, still learning the basics.
I'm finding I like Ubuntu more than XP, just miss my Paintshop Pro, I have PsP7 and X2 Ultimate. Still learning Gimp.
:popcorn:

---

