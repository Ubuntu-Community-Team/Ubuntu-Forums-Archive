---
title: "Opening files with Wine from desktop"
date: 2010-09-10
forum: Desktop Environments
---

### Post by oinkl on 2010-09-10
I'm trying to get wine to open .pdf files with Foxit.

I have no problems running the following command in terminal
wine "C:\\Program Files\\Foxit Reader\\Foxit Reader.exe" file.pdf

The following is the desktop entry file for pdf files.
[Desktop Entry]
Type=Application
Name=Foxit Reader
Exec=wine "C:\\Program Files\\Foxit Reader\\Foxit Reader.exe" %F
NoDisplay=true

When I try to open pdf files from desktop, I get a dialog box about how to invoke the exe file. How do I get the exe to register the list of files properly?

Also, how would I pass command line parameters for Foxit in the desktop entry file?

---

