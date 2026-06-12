---
title: "Broken links created"
date: 2009-04-29
forum: General Help
---

### Post by jesterthejedi on 2009-04-29
When I run this:

$ ln -s Mashup-1/actions/*png M2/actions/

The links are created in the actions folder, but every one of them (343) is broken. I know how to make simple links in the same folder, but in a new folder I am not having any luck. I can do this with right click on nautilus, but those links break if you move the folder path. What I'm looking for is the proper arguements or wildcards to create identical symbolic links in a different parallel folder.

---

### Post by cariboo on 2009-04-30
If you want to link all the files in a directory, you need to use the full path. eg:

```
ln -s /media/tunes /home/user/tunes
```

---

### Post by jesterthejedi on 2009-05-03
Got that working, however when I move the folder, such as into an archive the links break. Is there a way to edit the links target to point to a sourced directory and that would be static?

For example: Both folder A and B are in an archive
folder A has PNG files
folder B has links to the PNG files in Folder A and unique files

when the archive is moved, the links drop. however links in the same folder are safe, their target is specific to the original file name. 

Thus I need the links in folder B to always look at folder A no matter the parent location, both would be located in the same parent folder.

---

