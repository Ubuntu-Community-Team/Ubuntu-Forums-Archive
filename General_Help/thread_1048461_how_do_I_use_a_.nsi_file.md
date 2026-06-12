---
title: "how do I use a .nsi file?"
date: 2009-01-23
forum: General Help
---

### Post by Pacopag on 2009-01-23
Hi.
I downloaded a program called pdfsam, but only the source code is available for download.  There is a folder called "install" which contains a file called "install-enhanced.nsi".  I'm guessing that I have to run this file in order to install the program.  Can someone please tell me what to do?

Thanks.

---

### Post by kellemes on 2009-01-23
> **Pacopag said:**
> Hi.
I downloaded a program called pdfsam, but only the source code is available for download.  There is a folder called "install" which contains a file called "install-enhanced.nsi".  I'm guessing that I have to run this file in order to install the program.  Can someone please tell me what to do?

Thanks.

Isn't this just a Nullsoft Installer File Project?
Are you sure you downloaded the correct sourcecode tarball?
Are there any more files in there?

But anyway, just to be sure..
Unpack this file to some directory..
Open a terminal window and enter this directory you unpacked it to.
```
cd /path/to/directory
```

make the file executable..
```
chmod +x install-enhanced.nsi
```

run it..
```
./install-enhanced.nsi
```

Edit: I haven't looked into "pdfsam". But maybe there are alternative software packages for what you're looking for? What is it that "pdfsam" does?

---

### Post by Pacopag on 2009-01-23
Ya.  There's a bunch of folders.  

paco@magnetboxtogo:~/Desktop/pdfsam$ ls
emp4j                                pdfsam-encrypt
emp4j-1.0.1-build-src.zip            pdfsam-encrypt-0.2.4e-build-src.zip
install                              pdfsam-jcmdline-1.0.3-build-src.zip
jcmdline                             pdfsam-langpack
launcher-src.zip                     pdfsam-langpack-build-src.zip
libraries-1                          pdfsam-launcher
nsi.zip                              pdfsam-maine-br1
pdfsam-1.4.1e-build-src.zip          pdfsam-merge
pdfsam-1.4.1e-libraries.zip          pdfsam-merge-0.6.5-build-src.zip
pdfsam-1.4.1e-template.zip           pdfsam-mix
pdfsam-console-1.1.5e-build-src.zip  pdfsam-mix-0.1.4e-build-src.zip
pdfsam-console-br1                   pdfsam-split
pdfsam-cover                         pdfsam-split-0.4.6-build-src.zip
pdfsam-cover-0.2.4e-build-src.zip    template-enhanced-1

Ignore the .zip files, which just contain the folders listed here.

---

### Post by Pacopag on 2009-01-23
paco@magnetboxtogo:~/Desktop/pdfsam/install$ ./install-enhanced.nsi 
./install-enhanced.nsi: line 1: Name: command not found
: command not foundnsi: line 2: 
./install-enhanced.nsi: line 3: SetCompressor: command not found
: command not foundnsi: line 4: 
./install-enhanced.nsi: line 6: !define: command not found
./install-enhanced.nsi: line 7: !define: command not found
./install-enhanced.nsi: line 8: !define: command not found
./install-enhanced.nsi: line 9: !define: command not found
: command not foundnsi: line 10: 
./install-enhanced.nsi: line 12: !define: command not found
./install-enhanced.nsi: line 13: !define: command not found
./install-enhanced.nsi: line 14: !define: command not found
./install-enhanced.nsi: line 15: !define: command not found
./install-enhanced.nsi: line 16: syntax error near unexpected token `;'
./install-enhanced.nsi: line 16: `;!define MUI_STARTMENUPAGE_REGISTRY_VALUENAME 'tartMenuGroup

---

