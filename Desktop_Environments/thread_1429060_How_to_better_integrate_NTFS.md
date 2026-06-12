---
title: "How to better integrate NTFS?"
date: 2010-03-13
forum: Desktop Environments
---

### Post by Vostrocity on 2010-03-13
I have 3 partitions on my HDD. One ext3 for Ubuntu, one NTFS for Windows, and another NTFS for all of my files. This way I can keep my files in one place and be able to access them on both OS. I have three small issues with this configuration.
1. Files on NTFS can't be moved to Trash, only deleted outright.
2. Dragging files between my Home Folder or Desktop to the NTFS partition defaults to copy rather than move.
3. Opening any plain text file on the NTFS partition gives me a pop up that asks me whether I want to run it or display its contents.

---

### Post by mcduck on 2010-03-13
> **Vostrocity said:**
> I have 3 partitions on my HDD. One ext3 for Ubuntu, one NTFS for Windows, and another NTFS for all of my files. This way I can keep my files in one place and be able to access them on both OS. I have three small issues with this configuration.
1. Files on NTFS can't be moved to Trash, only deleted outright.
2. Dragging files between my Home Folder or Desktop to the NTFS partition defaults to copy rather than move.
3. Opening any plain text file on the NTFS partition gives me a pop up that asks me whether I want to run it or display its contents.

1. NTFS has it's own way of managing file deletion, so I'm not sure if you can do anything about this one.

2. That's normal, and happens every time you are dragging something from one partition to another (regardless of the file system used). I don't remember ever seeing an option to change this behavior, but if you drag the file using the middle mouse button you'll get a popup dialog that asks if you want to copy, move or link the file...

3. You could either change the NTFS partition's mount options so that the files aren't mounted with execute permission, or you can just set your file manager to view executable files by default instead of asking what to do (In Nautilus you'll find that option if you go to Edit/Preferences and then to the Behavior-tab).

---

### Post by Vostrocity on 2010-03-13
> **mcduck said:**
> 1. NTFS has it's own way of managing file deletion, so I'm not sure if you can do anything about this one.

2. That's normal, and happens every time you are dragging something from one partition to another (regardless of the file system used). I don't remember ever seeing an option to change this behavior, but if you drag the file using the middle mouse button you'll get a popup dialog that asks if you want to copy, move or link the file...

3. You could either change the NTFS partition's mount options so that the files aren't mounted with execute permission, or you can just set your file manager to view executable files by default instead of asking what to do (In Nautilus you'll find that option if you go to Edit/Preferences and then to the Behavior-tab).

I'm still hoping someone will be able to suggest a solution for 1 and 2. But thanks for your tip on 3. I'm also wondering what an executable text file really is. I don't recall ever encountering one.

---

### Post by mcduck on 2010-03-13
> **Vostrocity said:**
> I'm still hoping someone will be able to suggest a solution for 1 and 2. But thanks for your tip on 3. I'm also wondering what an executable text file really is. I don't recall ever encountering one.

Every text file that has executable permission set. (basically every shell script, python program etc. that are text files but can be ran as programs.)

But if your drive is mounted with options that set then *every* text file will be executable text file. (just like every ohter file is executable file). The system doesn't know if the files are actual programs until it tries to run them since it doesn't read through the complete files when you just view them in the file manage.

---

