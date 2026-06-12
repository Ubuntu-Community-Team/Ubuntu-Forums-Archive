---
title: "Need help with a bash script to process multiple lines"
date: 2009-03-06
forum: General Help
---

### Post by Huufarted on 2009-03-06
I'm looking for a way to automate a download procedure that I'll be doing infrequently.  At work, there's a cron script on another server that includes a URL on each line followed by a few other details about the file.  I don't care about anything but the first column.

I know how to extract each item I'm looking for from the line:

If the file contents are
```

http://10.11.12.13/file.txt abcd 1234
http://10.11.12.14/file.txt efgh 5678

```
then the below command
```

cat filename.txt | cut -d " " -f1

```
will leave me with 
```

http://10.11.12.13/file.txt
http://10.11.12.14/file.txt

```

As each line is processed by cut, I'd like wget to grab that file and that's the part that I'm unsure of.  When this script runs, the file can contain anywhere from 0 to an unlimited number of lines.  Regardless of how many lines there are, I need to use wget on the URL portion of each line.

Anybody know how to do this?  I'm fairly new to shell scripts, so I'm still finding my way around.

---

### Post by lloyd_b on 2009-03-06
```
#!/bin/bash

while read LINE; do
    URL=${LINE%% *}
    wget $URL 
done
```

Then invoke it as "script < file", where "file" is the data file containing the lines with the URLs.  The script will then take the contents of the file, and "read" them a line at a time.  

The "URL=..." line is a bash internal version of your "cut" command.

Lloyd B.

---

### Post by cybergalvez on 2009-03-06
give this a try

```

#!/usr/bin/env python

import subprocess
import sys

__doc__ = '''
usage processfiles.py <filename.txt>
'''

def main(f):
    for line in file(f).readlines():
        url = line.split()[0]
        subprocess.call('wget %s' % url, shell=True)
        

if __name__ == '__main__':
    File = sys.argv[1]
    main(File)

```

to use it just do process.py filename.txt or what ever you name the file

---

### Post by geirha on 2009-03-06
Just tell wget to read the urls to download from a file (-i); in this case the file is stdin (-).
```
cut -d " " -f1 filename.txt | wget -i -
```

---

### Post by Huufarted on 2009-03-06
geirha, so by your syntax it would let me type

cat filename | wget -i -

and that would process each line in the file?

---

### Post by geirha on 2009-03-06
If you have a file with one url per line, then ```
wget -i filename
``` will download each url. You'll need to cut away everything that is not an url or part of an url.

---

### Post by cybergalvez on 2009-03-06
> **geirha said:**
> If you have a file with one url per line, then ```
wget -i filename
``` will download each url. You'll need to cut away everything that is not an url or part of an url.

thats essentially what the python program above does, it reads in the file one line at a time, cuts the url out based on the "space" and sends that to wget.  it doesn't get any easier then that

---

