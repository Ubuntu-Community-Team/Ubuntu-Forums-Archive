---
title: "Permissions"
date: 2006-01-03
forum: General Help
---

### Post by Y-town on 2006-01-03
When i try to add a file in this directory

Places>Computer>Filesystem>opt>lammp>htdocs>index.html

i get an error saying "You do not have permissions to write to this folder." How can i fix this?

---

### Post by rjwood on 2006-01-03
What are you trying to do? What kind of file?

---

### Post by Omnios on 2006-01-03
This is because rout is the owner of this file, basicly root is the owner of the files in the file system other than /home. In terminal you can use sudo mv filenane directory or another option is copy it Sudo cp /dir/filename /dir/filename.
the sudo command allows you to do things as root.

 This is a links thread to termainal commands
[http://ubuntuforums.org/showthread.php?t=45651&highlight=commands]("http://ubuntuforums.org/showthread.php?t=45651&highlight=commands")

 ANother option is to set up a open as root script that allows you to open a directory or text file as root if thats what you want to set up

[http://ubuntuforums.org/showthread.php?t=75610&highlight=open+root]("http://ubuntuforums.org/showthread.php?t=75610&highlight=open+root")

[http://www.ubuntuguide.org/#openfilesasrootviarightclick]("http://www.ubuntuguide.org/#openfilesasrootviarightclick")

 Edit: I have to learn to type faster lol you beat me to it rjwood lol

---

### Post by cbudden on 2006-01-03
I have had some trouble with changing the permissions of the lampp directory, so I use the root nautilus script to move things in and out of the folder.

---

