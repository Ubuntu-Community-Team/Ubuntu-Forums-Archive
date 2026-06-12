---
title: "Change File Nmes to be Windows Compliant?"
date: 2008-12-23
forum: General Help
---

### Post by iampriteshdesai on 2008-12-23
I tend to save web pages in Opera but the file names have charachters like | / which aren't accepted in Vista, how do I bulk remove those file characters? Also anything to stop this happening in Ubuntu?

---

### Post by ajgreeny on 2008-12-23
You can bulk rename, replacing or deleting characters using gprename from the repos.

---

### Post by kaibob on 2008-12-23
You can also use the rename command. For example, to remove the characters ; and ? and | and \ from the names of files in a directory, enter the following in a terminal window:

```
rename -n 's/[;?|\\]//g' *
```

If you want to replace the characters with say an underscore, enter:

```
rename -n 's/[;?|\\]/_/g' *
```

The -n option does a dry run and reports what it proposes to change. To actually change the file names, substitute -v for -n. 

I don't know how to alter the behavior of Opera.

---

### Post by iampriteshdesai on 2008-12-24
But how can I select which folder and file to change name wityh that command?

---

### Post by kaibob on 2008-12-24
> **iampriteshdesai said:**
> But how can I select which folder and file to change name wityh that command?

You open a terminal window, change to the directory that contains the file, and enter the rename command. The command as presently written acts on all files contained in the directory. You can limit this by changing the * at the end of the command to something else. If you only want it to act on html files, you would change * to *.html. If you want it to work on one specific file, change * to the file name.

You can make the command into a Nautilus script. This would allow you to right click on a specific file in Nautilus, and the script would then work only on that file. To do this, first create the following shell script:

```
#!/bin/bash

# Get file and directory names.
FILE="$1"
DIR=$(dirname "$1")

# Change to target directory.
cd "$DIR"

# Remove characters from file name. 
rename -v 's/[:;?|\\]//g' "$FILE"
```

Then place the script in the following directory:

/home/username/.gnome2/nautilus-scripts

To actually change a file, right click on the file in Nautilus, go down to "Scripts", and then select the name you have given the script.

---

