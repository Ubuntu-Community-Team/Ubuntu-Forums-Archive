---
title: "Renaming multiple files within directories. (SSH)"
date: 2009-05-02
forum: General Help
---

### Post by Gimenez on 2009-05-02
Hi guys I recently obtained a large amount of files on my server. I want to be able to execute a command whether in regex or w/e in order to rename multiple files. I know it sounds simple but I want the script to rename ALL files within all folders. For example...

I got :

Folder1/ File Blah Blah.zip 
Folder2/ File Blah Blah.zip 
Folder3/ File Blah Blah.zip 
Folder4/ File Blah Blah.zip 

I want the script or command to rename all files within a specified directory to replace spaces with underscores and include my site's name before the .zip. (Folder1/ File_Blah_Blah([www.sitename.com).zip](www.sitename.com).zip) 

Right now I am using UltraFXP to do it manually but I have to go folder by folder. If I can find a way to rename everything that way without me going manually into folders, I would appreciate it alot!

If anybody knows a way please help. Either an FTP program or anything that would do this automatically.

My OS is CentOS

---

### Post by clcollins on 2009-05-02
I needed to do something similar recently and found this to be helpful:

[http://www.thingy-ma-jig.co.uk/blog/19-04-2008/how-batch-rename-files](http://www.thingy-ma-jig.co.uk/blog/19-04-2008/how-batch-rename-files)

---

### Post by mobilediesel on 2009-05-02
> **Gimenez said:**
> Hi guys I recently obtained a large amount of files on my server. I want to be able to execute a command whether in regex or w/e in order to rename multiple files. I know it sounds simple but I want the script to rename ALL files within all folders. For example...

I got :

Folder1/ File Blah Blah.zip 
Folder2/ File Blah Blah.zip 
Folder3/ File Blah Blah.zip 
Folder4/ File Blah Blah.zip 

I want the script or command to rename all files within a specified directory to replace spaces with underscores and include my site's name before the .zip. (Folder1/ File_Blah_Blah([www.sitename.com).zip](www.sitename.com).zip) 

Right now I am using UltraFXP to do it manually but I have to go folder by folder. If I can find a way to rename everything that way without me going manually into folders, I would appreciate it alot!

If anybody knows a way please help. Either an FTP program or anything that would do this automatically.

My OS is CentOS

It took some testing but this works in BASH:```
for dir in $(ls -d */); do cd "$dir"; for file in $(ls|sed 's/ /_/g'); do mv "$(echo "$file"|sed 's/_/ /g')" "$(echo "$file"|sed 's/\(.*\)\(\.[^\.]*$\)/\1(www.website.com)\2/')"; done; cd ..; done
```
It lists directories only, then goes into each directory and renames all files adding "(www.website.com)" between the filename and extension and converting spaces to underscores, then goes to parent directory and into the next.

---

### Post by geirha on 2009-05-02
I'd use the find and rename commands.

```
find -name "*.zip" -print0 | xargs -0 -- rename [COLOR="Blue"]-n[/COLOR] 'y/ /_/; s/\.zip$/(www.sitename.com).zip/'
```

find -name "*.zip" will recursively find all zip-files from the current directory. It pipes that list of names to xargs, which adds each file as an argument to the next command (rename). 

The -n option to rename (marked in blue), will make rename only output what it would've done, it will not actually rename. If it looks right, replace -n with -v to have it do the actual rename.

---

### Post by mobilediesel on 2009-05-02
> **geirha said:**
> I'd use the find and rename commands.

```
find -name "*.zip" -print0 | xargs -0 -- rename [COLOR="Blue"]-n[/COLOR] 'y/ /_/; s/\.zip$/(www.sitename.com).zip/'
```

find -name "*.zip" will recursively find all zip-files from the current directory. It pipes that list of names to xargs, which adds each file as an argument to the next command (rename). 

The -n option to rename (marked in blue), will make rename only output what it would've done, it will not actually rename. If it looks right, replace -n with -v to have it do the actual rename.

Damn, that makes mine look like overkill! Yeah find and xargs look more like the way to go. I didn't know you could do the find-and-replace for the spaces like that.

---

