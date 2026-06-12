---
title: "sudo code to remove files from ur computer"
date: 2009-05-14
forum: General Help
---

### Post by cowboyup8606 on 2009-05-14
i am trying to remove this one file from my computer and it wont let me my friend told me a sudo code that will delete it but i cant remember it i know it was  " sudo -r something and the path could someone plz help me out ?

---

### Post by KhurramM on 2009-05-14
On terminal:

man rm

to see different options

use:

 sudo rm path~to~file/your~file

---

### Post by cowboyup8606 on 2009-05-14
im sorry i dont quiet understand what u meen :( im kinda new to this and i thought the code i was told was sudo -r ( some number ) / (path)

---

### Post by elysianfields44 on 2009-05-14
In terminal:

rm [path/to/filename]     to delete individual files; 

rmdir [path/to/directory] to delete empty directories;

rm -r [path/to/directory] to delete non-empty directories (use this with caution, the -r option makes this recursive!)

---

### Post by jocko on 2009-05-15
> **cowboyup8606 said:**
> im sorry i dont quiet understand what u meen :( im kinda new to this and i thought the code i was told was sudo -r ( some number ) / (path)

To remove a file:
```
rm /path/to/filename
```To remove a folder (together with the files it contains):
```
rm -r /path/to/foldername
```To remove all files or folders within a folder, but leave the folder:
```
rm -r /path/to/foldername/*
```"sudo" is a prefix that you need to put in front of a command if you need administrative rights to run the command.
If the files you want to remove are somewhere outside your home directory you may need to type "sudo" in fron of "rm" to be able to remove the files, so:
```
sudo rm /path/to/filename
```will remove files outside your home directory, even if they are very important system files. So:
[SIZE=4][COLOR=Red]**NEVER**[/COLOR][/SIZE] use sudo unless you really need it, and know what will happen. A "sudo rm" command has the power to wipe your entire filesystem.
Even if I know this I have managed to destroy my ubuntu install more than once by not checking for typos in the path in "sudo rm" commands. Something as simple as an extra space in the path or filename can lead to removal of much more than you aim for.
Examples:
```
rm -r /home/username/file
```Will only remove the file "file" in the folder "/home/username".
```
rm -r /home /username/file
```Will remove the entire /home folder (at least if you put sudo in front of the command).
```
rm -r / home/username/file
```Will remove the entire filesystem (/) (if you put sudo in front of the command).

---

### Post by MysticalRiotCandy on 2009-05-15
To be safe, I find it a lot better to just open up Nautilus with root priveliges.  Then you can just point and click and delete.  A little bit safer, unless you're the type that habitually hits the Delete key.

---

