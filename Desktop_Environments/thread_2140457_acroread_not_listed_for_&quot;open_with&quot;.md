---
title: "acroread not listed for &quot;open with&quot;"
date: 2013-04-29
forum: Desktop Environments
---

### Post by shochatd on 2013-04-29
This is 13.04 with the standard (Unity) desktop.
I have Adobe Reader 9 installed and can use it from the command line as acroread. But I'd like to be able to select it via "open with" in Nautilus from the context menu for a PDF. I have the impression that this requires a desktop file. I found AdobeReader.desktop in /opt/Adobe/Reader9/Resource/Support and tried putting a symlink in /usr/local/share/applications to this file. Contents of AdobeReader.desktop:
[Desktop Entry]
Name=Adobe Reader 9
MimeType=application/pdf;application/vnd.fdf;application/vnd.adobe.pdx;application/vnd.adobe.xdp+xml;application/vnd.adobe.xfdf;
Exec=acroread 
Type=Application
GenericName=PDF Viewer
Terminal=false
Icon=AdobeReader9
Caption=PDF Viewer
X-KDE-StartupNotify=false
Categories=Application;Office;Viewer;X-Red-Hat-Base;
InitialPreference=9

But that doesn't seem to work. I still don't see it under "open with" even if I do "Show other applications". What do I need to do? I'm not trying to set it to be the default application for PDFs (I want to keep evince as the default). 
-- David

---

### Post by mc4man on 2013-04-30
Add a %U to the end of Exec= line in the AdobeReader.desktop, like - 
```
Exec=acroread %U
```

---

### Post by shochatd on 2013-04-30
> **mc4man said:**
> Add a %U to the end of Exec= line in the AdobeReader.desktop, like - 
```
Exec=acroread %U
```

Thank you. That fixed it immediately. To set the record straight, after posting, I discovered that a symbolic link to /opt/Adobe/Reader9/Resource/Support/AdobeReader.desktop already existed in /usr/share/applications, named acroread.desktop. It had been installed as part of the package. So I replaced the symlink with a copy and edited it as you suggested.

---

### Post by sambody on 2013-11-08
It worked for me too. I had a desktop file in /home/myusername/.local/share/applications/ called adobe reader.desktop (or acroread), but it didn't appear in the "open with" context menu. By adding " %U", it was solved. Thank you.

---

### Post by SheamusPatt on 2013-11-16
Another solution, especially if you haven't already installed the version on the Adobe website, is to install the Canonical Partners version as described here [[COLOR=Red]**Ask Ubuntu: Adobe Reader Installation**[/COLOR]]("http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader") . This goes through the regular package manager, and seems to get the desktop settings right.

---

### Post by sacha3 on 2014-08-22
Where do I find the location of the installed Adobe reader?

---

### Post by Ksiencha on 2014-08-22
I guess in **/usr/bin**

---

### Post by shochatd on 2014-08-22
On my system, it is /opt/Adobe/Reader9/bin/acroread. If all else fails, you could just do a brute force search:
find / -name acroread 2>/dev/null
It looks like (again, on my system) there is also a symbolic link to this:
/usr/bin/acroread -> /opt/Adobe/Reader9/bin/acroread. 
-- David

---

### Post by mc4man on 2014-08-22
> **sacha3 said:**
> Where do I find the location of the installed Adobe reader?
Says where the .desktop is located in the original post..

---

