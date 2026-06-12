---
title: "Using mv in a script"
date: 2009-04-15
forum: General Help
---

### Post by silentrebel on 2009-04-15
Hello I'm trying to write a bash script but I'm not having too much success.
Here is the code for the script I named *tr*:
```
#!/bin/bash
path=$1
path=${path//' '/'\ '}
echo $path
sudo mv $path ~/.local/share/Trash/files
```
Here is the command I used to execute the script:
> tr es\ se
Here is the output:
> es\ se
mv: cannot evaluate `es\\': No file or folder of this type
mv: cannot evaluate `se': No file or folder of this type

Please note that if I remove the 3rd line from the code, the output is as follows:
> es\ se
mv: cannot evaluate `es': No file or folder of this type
mv: cannot evaluate `se': No file or folder of this type

The first line of the output is exactly right; however when I give this to the mv command it doesn't use it properly.  I am sure this file exists in the current directory.
Thank for the help.

EDIT: I just realized I stuck this in a very random place.  If anyone could delete this, it would be greatly appreciated.

---

### Post by cariboo on 2009-04-15
I moved the post to a place where more people can see your question. In the future just report the post using the icon on the lower left below your username.

Jim

---

### Post by mb_webguy on 2009-04-15
I'm assuming you're trying to accommodate files and directories with spaces in the name.  Why can't you just do the following?```
#! /bin/sh
sudo mv "$@" ~/.local/share/Trash/files

```

---

