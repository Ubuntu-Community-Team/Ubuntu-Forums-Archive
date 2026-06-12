---
title: "Extracting files from folders"
date: 2006-09-23
forum: Desktop Environments
---

### Post by geetarista on 2006-09-23
I'm not sure if this was possible, but I have a bunch of folders that have only 1 file each in them.  Is there any way that I can pull each of those files out of each folder and throw it into either the main directory or another specific directory?

---

### Post by fstab on 2006-09-23
Oh its possible:

1.Run the following in your terminal, it creates a folder in your home directory.
```
mkdir ~/folders_with_one_file
```

2. Move all the folders with one file into that new folder.

3. Run the following command, it will list of all the files inside the folder ~/folders_with_one_file folder.
```
find ~/folders_with_one_file -type f
```

4. Read the output of the previous command.  If you want all the files listed by the previous command to be inside a single folder, run the following two commands.  After executing them, you should be left with a bunch of empty directories in ~/folders_with_one_file and all the files that were in them will have been moved to ~/files_from_those_folders.

```
mkdir ~/files_from_those_folders
find ~/folders_with_one_file -type f -exec mv {} ~/files_from_those_folders \;
```

---

### Post by geetarista on 2006-09-23
That worked perfectly--thank you!!

Noe I'm assuming that if I wanted only PDF files within the directories, I would do this:

```
find ~/folders_with_one_file -type .pdf .PDF -exec mv {} ~/files_from_those_folders \;
```

Is that right?

---

### Post by fstab on 2006-09-23
No, type only works with "f" for files and "d" for directories.  You can find the files that end with .pdf or .PDF with the -iname option.  -iname matches parts of the filename in a case-insensitive way.

List all your pdf's with this:
```

find ~/folders_with_one_file -iname *.pdf
```

If the output is the files you want to move, then run
```

find ~/folders_with_one_file -iname *.pdf -exec mv {} ~/files_from_those_folders \;
```

---

### Post by geetarista on 2006-09-23
Ohhhh...that makes sense now.  I'm still trying to learn all of these commands.

Thanks so much for your help!!!

---

