---
title: "problem opening .txt files"
date: 2010-01-07
forum: Desktop Environments
---

### Post by jcshane on 2010-01-07
First, let me apologize for starting a new thread when one exists that partially addresses my issue ([http://ubuntuforums.org/showthread.php?t=254921](http://ubuntuforums.org/showthread.php?t=254921)). However, my account privileges on these boards don't allow me to post replies (an issue I haven't figured out yet). I'm using 8.10.

When I attempt to open a .txt file I get a dialog box that says:[INDENT]Do you want to run "filename.txt", or display its contents?
"filename" is an executable text file.
<Run in Terminal> <Display> <Cancel> <Run>
[/INDENT]If I choose <Run>, nothing happens that I can see - the file does not open in Text Editor. But if I choose <Display> it does. Another way to open the file in Text Editor is to right-click, choose "Open with Other Application..." and then choose Text Editor from a list. On the other hand, if I choose a recently opened .txt file from my Places>Recent Documents drop-down menu, the file opens immediately in Text Editor.

In the Properties of the .txt files, Text Editor is chosen as the default application under the "Open With" tab. Under the "Permissions" tab, the checkbox next to "Allow executing file as program" is orange but not checked. If I attempt to check it, the checkmark appears for a moment and disappears.

Thanks for any suggestions!

---

### Post by mcduck on 2010-01-07
Is the file on your Ubuntu partition, or on some Windows file system?

The reason for the file manager asking if you want to execute the file is that the file has execute permission set, and any file with execute permission is treated as a program (no matter if it actually contains any executable code or not).

If the file is on Ubuntu partition, and you are the file's owner, you should be able to remove the execute permission and the file will automatically open in editor when clicked. If it's on a windows file system that's not an option, since those file systems don't actually support permissions as they are used in Linux/Unix systems.

You can also set the behavior for opening executable text files in the file manager's references, the default behavior is to as what you want to do, but you can set it to open the file every time instead.

(And no, choosing to run the file is not even supposed to open the file for viewing or editing. It tries to run the file as if it was a program.)

---

### Post by hariks0 on 2010-01-07
Nautilus > Edit > Preferences > Behaviour Tab

Please refer the screenshot.

---

### Post by jcshane on 2010-01-07
> **mcduck said:**
> Is the file on your Ubuntu partition, or on some Windows file system?

The reason for the file manager asking if you want to execute the file is that the file has execute permission set, and any file with execute permission is treated as a program (no matter if it actually contains any executable code or not).

If the file is on Ubuntu partition, and you are the file's owner, you should be able to remove the execute permission and the file will automatically open in editor when clicked. If it's on a windows file system that's not an option, since those file systems don't actually support permissions as they are used in Linux/Unix systems.

You can also set the behavior for opening executable text files in the file manager's references, the default behavior is to as what you want to do, but you can set it to open the file every time instead.

(And no, choosing to run the file is not even supposed to open the file for viewing or editing. It tries to run the file as if it was a program.)
Thanks mcduck, I think you pinpointed the issue. I used to have Windows, but am now using a new computer that never had Windows installed on it.

If I try to open a .txt file that was created on this new computer and is stored on the new computer, it opens just fine. I have the issue described if I try to open: a) a .txt file that was created in Windows or b) a .txt file that is stored on my usb thumbdrive, regardless of whether it was created in Windows or Ubuntu.

Is it possible/desirable to 'reformat' the thumbdrive so that I don't have this issue? Would it prevent me from using the thumbdrive on computers with other OSes?

---

### Post by jcshane on 2010-01-07
> **hariks0 said:**
> Nautilus > Edit > Preferences > Behaviour Tab

Please refer the screenshot.
Thanks hariks0, but I don't have anything called Nautilus that I'm aware of.

---

### Post by hariks0 on 2010-01-07
> **jcshane said:**
> Thanks hariks0, but I don't have anything called Nautilus that I'm aware of.

Nautilus is the default file browser of Gnome. Just open a folder and navigate to Edit menu...

---

### Post by mcduck on 2010-01-07
> **jcshane said:**
> Thanks mcduck, I think you pinpointed the issue. I used to have Windows, but am now using a new computer that never had Windows installed on it.

If I try to open a .txt file that was created on this new computer and is stored on the new computer, it opens just fine. I have the issue described if I try to open: a) a .txt file that was created in Windows or b) a .txt file that is stored on my usb thumbdrive, regardless of whether it was created in Windows or Ubuntu.

Is it possible/desirable to 'reformat' the thumbdrive so that I don't have this issue? Would it prevent me from using the thumbdrive on computers with other OSes?
You can format the drive into some Linux file system, but that would indeed prevent Windows and OSX from reading it since they pretty much only support their own file systems and nothing else.

For the files that are already on your computer you should be able to just change their ownership to your own user and then remove the execute permission. With files that are on the thumb drive this isn't an option, so you'll probably just want to change the file manager's settings to always open the file instead of asking what to do. Unless you do a lot of shell scripting it's unlikely that you'd want to execute any text files anyway. And if you *do* shell scripting you most likely just execute the files from command line instead of clicking them in the file manager..

---

### Post by jcshane on 2010-01-07
> **mcduck said:**
> For the files that are already on your computer you should be able to just change their ownership to your own user and then remove the execute permission. With files that are on the thumb drive this isn't an option, so you'll probably just want to change the file manager's settings to always open the file instead of asking what to do. Unless you do a lot of shell scripting it's unlikely that you'd want to execute any text files anyway. And if you *do* shell scripting you most likely just execute the files from command line instead of clicking them in the file manager..

I don't know how to do either of those things (change ownership or change file manager settings) but I can live with the current state of affairs.

Thanks again for your help!

---

### Post by mcduck on 2010-01-07
Harikso posted instructions for changing te file manager setting above.

For file permissions just right-click a file and select "Properties". You can set the permissions on the Permisssions-tab of the properties dialog. The execute permission is a check box near the bottom of the dialog.

---

### Post by jcshane on 2010-01-09
> **mcduck said:**
> For file permissions just right-click a file and select "Properties". You can set the permissions on the Permisssions-tab of the properties dialog. The execute permission is a check box near the bottom of the dialog.

As I mentioned in my first post, the files' properties dialog doesn't let me change the permissions. The checkbox is orange but not checked. If I check it, the checkmark appears for a moment then disappears.

---

### Post by mcduck on 2010-01-09
Yes, that will happen if the files are on a windows filesystem (FAT or NTFS). For files on those filesystems your only option is to use the Nautilus setting mentioned above in this thread.

---

