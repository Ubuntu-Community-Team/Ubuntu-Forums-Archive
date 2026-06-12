---
title: "shell script help"
date: 2009-03-11
forum: General Help
---

### Post by MountainX on 2009-03-11
I have about 100 folders that I need to delete. I want to script this, but I haven't written scripts before. I just read a [tutorial]("http://www.justlinux.com/nhf/Programming/Introduction_to_bash_Shell_Scripting.html") on it and now I want to give it a try. 

I can find all the folders to be deleted like this:
```
find / -path *SBV$ > /home/myuser/SBV-list
```

I can remove them like this:
```
rm -rfv '/path1/path2/path3/$SBV$'

```

I know how to write a for-loop in a shell script now. I just don't know how to put all these elements together.

Here is my initial outline /pseudo code:
```
#!/bin/bash
# script - test 1

echo "starting..."

for folder in $SBV-list; do
    rm -rf $folder
    echo "removed " $folder
done

exit 0
```

Can anyone help me turn this into a working script? Thanks

---

### Post by gersongarcia on 2009-03-11
Dear MountainX,

You don't need a script for this task. In fact it is a common task for Unix System administrator. You can use find command as follow:

# mkdir -p /path1/path2/path3/SBV1
# mkdir -p /path1/path2/path3/SBV2
# mkdir -p /path1/path2/path3/SBV3
# mkdir -p /path1/path2/path3/SBV4
# find /path1 -name "SBV*"
/path1/path2/path3/SBV2
/path1/path2/path3/SBV3
/path1/path2/path3/SBV1
/path1/path2/path3/SBV4
# find /path1 -name "SBV*" -exec rm -rf {} \;
# ls -al /path1/path2/path3
total 8
drwxr-xr-x 2 root root 4096 2009-03-11 20:08 .
drwxr-xr-x 3 root root 4096 2009-03-11 20:07 ..

---

