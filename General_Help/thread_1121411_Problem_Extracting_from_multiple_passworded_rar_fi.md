---
title: "Problem Extracting from multiple passworded rar files"
date: 2009-04-10
forum: General Help
---

### Post by gspat on 2009-04-10
Hi!

Here is the situation:

I have three sets of files I want to extract, they all have the same password - "Evil" (sans the quotes).

The files look like this:

1.part1.rar
1.part2.rar
1.part3.rar
2.part1.rar
2.part2.rar
2.part3.rar
3.part1.rar
3.part2.rar
3.part3.rar

I tried using unrar to extract the files using:

unrar x -p *.part1.rar

but it tells me that there is nothing to extract after I type in the password but typing:

unrar x -p 1.part1.rar

and typing the password in works fine... why is this? 

Also, is there a wildcard command where I could just use to extract them all in one shot, with a one time typing of the password?

Also, the help for unrar is confusing... 

does this:

p[password]   Set password

mean -pEvil, -p[Evil] or something else? 

Thank you in advance!

---

### Post by mb_webguy on 2009-04-10
In describing command syntax, anything in brackets ([]) is optional.  So in this case you could use the "-p" option without providing a password, and unrar will then prompt you for the password.  If you wanted to provide the password in the command, it would go after the "-p" option, separated from it by a space (e.g. "unrar x -p password something.rar").

In your case, try the command "unrar x -p *.rar", or if these are the only rar archives in the current directory, "unrar x -p ./*".

---

### Post by gspat on 2009-04-10
I had tried that, but it gave me the "no files to extract" response

I also tried the space after the -p, but the program assumed the text after the switch was the file to be extracted.

Also, I can't go *.rar, as then I will have 3 copies of the file in the directory (assuming it works).

---

### Post by gspat on 2009-04-10
Well, after searching, it seems that rar and unrar do not like wildcards in their command lines...

so I made a script to do it for me...

Enjoy!

```

#!/bin/bash

ls *.part1.rar > output.file
while read -r LINE ; do unrar x -pEvil "$LINE" ; done < output.file
rm output.file

```

The code could be modified to take variables from the command line to modify the password if need be... If someone does, please post it here for a more complete solution for others!!

---

### Post by poing on 2009-04-10
Here is how to unrar multiple files: [http://ralphunden.net/?q=unrar-multiple-files](http://ralphunden.net/?q=unrar-multiple-files)
That way you can just ls *.part1.rar | munrar x -pEvil

---

### Post by mb_webguy on 2009-04-10
Try this:```
find ./ -name *.part1.rar -exec unrar x -p*Password* '{}' \;
```

---

### Post by gspat on 2009-04-10
Nice!!

Thank you!!!

---

