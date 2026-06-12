---
title: "OpenOffice and SAMBA"
date: 2009-04-04
forum: General Help
---

### Post by Paul41 on 2009-04-04
I am having a problem with OpenOffice saving documents to SAMBA from my Ubuntu computer. When I create a document and save it for the first time it saves fine but every time after that I get the following error:

> Error saving the document mydocument:
Error creating object.
Could not create backup copy.


I only get this error when working on Ubuntu. I can open the same document in OpenOffice on Windows and it saves fine. I added nobrl to my fstab file but that did not fix the problem. If it matters SAMBA is running on a server (Ubuntu Server Edition).

Here is the portion of my fstab file where the share is mounted:
```
//192.168.1.100/sanders_share /home/paul/sanders_share cifs credentials=/root/.smbcredentials,nobrl,rw,iocharset=utf8,uid=paul,gid=paul,file_mode=0770,directory_mode=0770 0 0
```

---

### Post by Paul41 on 2009-04-08
bump

---

### Post by Paul41 on 2009-04-11
bump

---

### Post by Berserker v7 on 2009-04-11
Have you tried this under the conventional way of mounting? open the file browser and in the address bar give "smb://192.168.1.100". Access the required share... this share gets mounted in the ~/.gvfs folder. So, now you can open and save them at this location.

---

### Post by Paul41 on 2009-04-11
> **Berserker v7 said:**
> Have you tried this under the conventional way of mounting? open the file browser and in the address bar give "smb://192.168.1.100". Access the required share... this share gets mounted in the ~/.gvfs folder. So, now you can open and save them at this location.

OK, that works. So is there a way I make it work with my mounting in fstab?

---

### Post by Berserker v7 on 2009-04-11
Seems like an issue with cifs... Can you try automounting the share using smbfs?

---

### Post by Paul41 on 2009-04-11
I switched it to smbfs but get the same error. Here is what the fstab entry looks like now.

```
//192.168.1.100/sanders_share /home/paul/sanders_share smbfs credentials=/root/.smbcredentials,nobrl,rw,iocharset=utf8,uid=paul,gid=paul,file_mode=0770,directory_mode=0770 0 0
```

---

### Post by Paul41 on 2009-04-17
bump

---

### Post by Paul41 on 2009-04-20
bump

---

### Post by Paul41 on 2009-04-25
bump

---

### Post by Paul41 on 2009-04-28
bump

---

### Post by Paul41 on 2009-04-30
bump

---

### Post by Paul41 on 2009-05-02
bump

---

### Post by Paul41 on 2009-05-06
bump

---

### Post by Paul41 on 2009-05-08
bump

---

### Post by Paul41 on 2009-05-10
bump

---

### Post by Paul41 on 2009-05-12
bump

---

### Post by Paul41 on 2009-05-16
bump

---

### Post by Paul41 on 2009-05-19
bump

---

### Post by Paul41 on 2009-05-21
bump

---

### Post by Paul41 on 2009-05-23
bump

---

### Post by Paul41 on 2009-05-26
bump

---

### Post by Paul41 on 2009-05-29
bump

---

### Post by Paul41 on 2009-06-02
bump

---

### Post by Paul41 on 2009-06-04
bump

---

### Post by andyprough on 2009-06-04
try "auto,credentials", as in this post:

[http://ubuntuforums.org/showthread.php?t=287061](http://ubuntuforums.org/showthread.php?t=287061)

Also, in that thread there is a script to run to automount upon login. Give it a try.

---

### Post by Paul41 on 2009-06-04
I have one problem solved now and several new ones. I changed my fstab as follows: 

```
//192.168.1.100/sanders_share /home/paul/sanders_share cifs credentials=/root/.smbcredentials,iocharset=utf8,nobrl,file_mode=0777,dir_mode=0777 0 0
```

Now I can save a OpenOffice document when I open it but I can't do a save as or save a new document. When I try I get the following error.

> Error saving the document Untitled1:
General Error.
General input/output error.

It actually does save the document but when I try to open it I get a "ASCII filter Options" box and the file is empty after I click OK on the box.

In addition to that there are some files and folders that I have access to and some that I don't now. I should be able to access all of the files and folders, and have permission to do so.  Even on files or folders with the exact same permissions set, some I can open and some I can't.

---

### Post by Detonate on 2009-06-04
Do you have the option to automatically create a backup turned on in OpenOffice?  You can turn this feature on and off in the Tools>Options>Load/Save>General box.  If it is on, that might be causing the problem.

---

### Post by Paul41 on 2009-06-04
> **Detonate said:**
> Do you have the option to automatically create a backup turned on in OpenOffice?  You can turn this feature on and off in the Tools>Options>Load/Save>General box.  If it is on, that might be causing the problem.

I just tried turning it off but still get the same error.

---

### Post by Paul41 on 2009-06-08
bump

---

### Post by Crugster on 2009-08-30
I have the same problem, and mounting with the "auto" option did not work for me.
I have searched the web and it seems to be a common problem but I did not find a solution so far.

So, I was hoping for someone knowing a solution/workaround by now.
Hence: a new *BUMB*

---

### Post by Paul41 on 2009-08-30
> **Crugster said:**
> I have the same problem, and mounting with the "auto" option did not work for me.
I have searched the web and it seems to be a common problem but I did not find a solution so far.

So, I was hoping for someone knowing a solution/workaround by now.
Hence: a new *BUMB*

I still don't have a solution but I would still love one if someone has any ideas :)

---

### Post by Paul41 on 2009-09-28
Bump

---

### Post by Paul41 on 2009-10-19
bump

---

### Post by Paul41 on 2009-10-20
bump

---

### Post by Paul41 on 2009-10-21
bump

---

### Post by Paul41 on 2009-10-22
bump

---

### Post by Paul41 on 2009-10-23
bump

---

### Post by Paul41 on 2009-10-24
bump

---

### Post by Paul41 on 2009-10-25
bump

---

### Post by Paul41 on 2009-10-26
bump

---

### Post by jhb1608 on 2009-10-26
Stop constantly bumping. Thank you.

---

### Post by Paul41 on 2009-10-26
> **jhb1608 said:**
> Stop constantly bumping. Thank you.

I need a answer since it makes OpenOffice next to impossible to use for me. If a admin or forum staff member asks me to stop I will, other wise I bump it once a day.

---

### Post by Paul41 on 2009-10-29
bump

---

### Post by chivinou on 2009-11-18
I have the same type of issue.  But here is what I have noticed.  With this line I get the error:
//files/share        /smb/H  cifs    forcedirectio,iocharset=utf8,credentials=/home/me/.smbcredentials,uid=1000

with this one I don't:
//files/share        /smb/H  cifs    iocharset=utf8,credentials=/home/me/.smbcredentials,uid=1000

However without the "forcedirectio" large files sometimes get corrupted on transfer.
The "nobrl" did not seem to make a difference.

Also, accessing the share directly via smb://files/share does not work - for some reason when I do that in KDE and launches the file from Dolphin OpenOffice edits a copy under /tmp instead (it does work fine from Gnome, though)

---

### Post by natxoo on 2010-02-26
I've solved it installing gvfs-fuse package. This make openoffice use fuse an automagically 'copy' in /home/user/.gvfs

---

### Post by bobpaul on 2010-12-08
It doesn't make a copy in ~/.gvfs, the samba share is mounted in ~/.gvfs and nautilus gives Open Office "~/.gvfs/sharename on fileserver/path/file.odt" as the path.

This no longer works on Ubuntu 10.10, unfortunately. gvfs seems to work magically without a transparent mount operation, nautilus thinks ODS and ODT files on the samba share are zip files and opens them with file-roller (Archive Manager) and using File: Open to open the files directly in Open Office doesn't work either (no error dialog, but no file opens either.)

---

### Post by configt on 2011-08-11
So what is the solution?  I am having the same problem and have yet to see a solution that doesn't introduce new problems.

---

