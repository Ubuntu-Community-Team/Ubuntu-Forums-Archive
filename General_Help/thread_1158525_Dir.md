---
title: "Dir"
date: 2009-05-13
forum: General Help
---

### Post by m_2009 on 2009-05-13
What is the ubuntu equivalent or dir /s in terminal as used in windows in order to list all files and subfolders etc.

Ive tried dir -r and dir -d and neither work, they only give the files inside the folder, not subfolders too.

---

### Post by m_2009 on 2009-05-13
Have sorted it now.

I realised that the -R is case sensitive :-\"

now I am stuck with how to change how the directories are listed with the files contained within.

Is there a switch that can be used to make the output such as the following

/test/
/test/file1
/test/file2
/test/folder1/
/test/folder1/file3

etc...

---

### Post by sailthesea on 2009-05-13
A few helpful guides on commands, file structure and hierarchy are available at these links 
 Much care is needed when using the CLI to file manage particularly when using sudo or logging into root, with normal privileges you can only total your home directory 

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
 
 All good reading before you start ;)

---

