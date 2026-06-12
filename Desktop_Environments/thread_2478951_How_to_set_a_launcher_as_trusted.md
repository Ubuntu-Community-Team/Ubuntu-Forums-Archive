---
title: "How to set a launcher as trusted?"
date: 2022-09-09
forum: Desktop Environments
---

### Post by artist-wavenet on 2022-09-09
When I double left click this file in Dolphin:
/home/stephen/Desktop/Flameshot.desktop
Flameshot opens as expected.

In spite of this, the icon for this file in my desktop display does not open the file. When I double left click this icon I get the error
 > [INDENT] **Untrusted Desktop File** This desktop file is not trusted, it cannot be launched. To enable launching right-click, then: **Enable "Allow Launching"**
 [/INDENT]

I do not get this "Allow Launching" menu item when:
 
[LIST=1]
[*]I right click on the icon in the desktop 
[*]I right click on its file in Dolphin 
[*]I right click on this file in the "File Manager" 
[/LIST]
 So I attempted to do it from the command line by using the instructions on this webpage: [How to mark a .desktop file as trusted from command line on Ubuntu 18.04?]("https://askubuntu.com/questions/1202488/how-to-mark-a-desktop-file-as-trusted-from-command-line-on-ubuntu-18-04") . Since I all desktop icons in /home/stephen/Desktop/ are untrusted launcher links I used this command sequence below, and also shown is the response:
```

$ chmod u+xrw /home/stephen/Desktop/*.desktop
$ chmod g+xrw /home/stephen/Desktop/*.desktop
$ chmod o+xr /home/stephen/Desktop/*.desktop
$ chmod o-w /home/stephen/Desktop/*.desktop
$ gio set "/home/stephen/Desktop/*.desktop" "metadata::trusted" yes
gio: Setting attribute metadata::trusted not supported
```
I got the same error when I gave gio a specific file instead of the *  wildcard character, and also when I attempted to execute gio as root.

 What is the correct attribute to give the gio command? In which file managers should the "Allow Launching" menu item appear?
 My OS is Ubuntu 22.04 jammy
 Here is one of the .desktop files I have this trouble with:

```
[Desktop Entry]
Comment=Powerful yet simple to use screenshot software.
Comment[en_US]=Powerful yet simple to use screenshot software.
Exec=flameshot launcher
GenericName=
GenericName[en_US]=
Icon=flameshot
Name=Flameshot (Snappy Edition)
Path=
StartupNotify=false
Terminal=false
Type=Application
Version=1.0
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-Desktop-File-Install-Version=0.26
X-KDE-SubstituteUID=false
X-KDE-Username=
```

Here is my attempt to validate the icon:
```
stephen@stephen:~$ desktop-file-validate /home/stephen/Desktop/Flameshot.desktop
/home/stephen/Desktop/Flameshot.desktop: warning: value "" for key "Path" in group "Desktop Entry" does not look like an absolute path
stephen@stephen:~$ sudo desktop-file-install /home/stephen/Desktop/Flameshot.desktop
/usr/share/applications/Flameshot.desktop: warning: value "" for key "Path" in group "Desktop Entry" does not look like an absolute path
stephen@stephen:~$ sudo desktop-file-edit /home/stephen/Desktop/Flameshot.desktop
/home/stephen/Desktop/Flameshot.desktop: warning: value "" for key "Path" in group "Desktop Entry" does not look like an absolute path
```

Still the "Allow Launching" menu item does not appear when this desktop icon is right clicked.

My OS is Ubuntu Desktop 22.04.1

I have an an encrypted, and RAIDed, ZFS file system.

The home directory partition is in a pair of RAID 1 mirrored HDD drives. This one partition covers the entire capacity of the 10TB Raided pair.

The root directory, boot directory, swap, read, and write, partitions are in a pair of RAID 1 mirrored SDD drives.

The details of the installation is in a document I wrote, the current version of which can always be be downloaded from:
[https://www.mediafire.com/file/2w8mdb96tbzslub/Ubuntu_22.04_Root_on_ZFS_Encryption.odt/file](https://www.mediafire.com/file/2w8mdb96tbzslub/Ubuntu_22.04_Root_on_ZFS_Encryption.odt/file)

 I created a spreadsheet to compare the results of the " strace gio  set" command done in the test account, which is new temporary account  created for testing in which I am able to create working desktop icons,  and the stephen account, which is the main account, and the one created  during Ubuntu installation, where I am not able to. This is attached as file:

giosetenablecomparison.ods

Column A is the result of the command in the main account, and Column  B is the result in the test account. The results are closely comparable  until row 59. In the test account this shows "close(3)" for the main  account, and "close(3) = 0" in the test account.

 In the stephen account the output ends at row 59. In the test account the output continues all the way to row 516.

 I do not know what all this output means. It appears to me that some  error is ending the process prematurely in the stephen account. Someone  here can see what has gone wrong, and suggest a solution.

The old computer I migrated from has a Pop!_OS 21.04. The new  computer I migrated to, and have this icon trouble with, has Ubuntu  22.04. When I did the migration I copied all the binaries in /opt, and  all files in /home. By copying all files in /opt I hoped to spare myself  the time, and effort, to do all the software installations again. I  know there are binaries elsewhere such as in /user/bin, and /snap. I did  not copy these, and intended to install these in the new computer using  installation files. I knew there would be broken links in the /Desktop  directory until the apps these are linked to are installed. I think now  this may have been a mistake, and that all should have been installed  from installation files in the new computer.

Any comments on why my desktop icons are not working in the stephen account would be much appreciated.

---

### Post by artist-wavenet on 2023-05-30
The "Allow Launching" menu item did not appear because the directory:  "~/Desktop" was writable by others. I had to find, and analyze, gnu  source code to find this out. The key to it was line 200 in file:
 ```
/usr/share/gnome-shell/extensions/ding(at)rastersoft.com/fileItemMenu.js"
``` .
 (substitute (at) for @)
 This is:
 ```
if (fileItem.isValidDesktopFile &&  !this._desktopManager.writableByOthers &&  !fileItem.writableByOthers && (selectedItemsNum == 1 )) {
```
Because the directory "~/Desktop" was writable by others, the term  "!this._desktopManager.writableByOthers" was false, and so the menu item  did not appear.
 he requirement that the "~/Desktop" directory not have writable by  others permission is not documented, and it needs to be. It would have  saved me a lot of time had it been.

---

