---
title: "sed Help to remove line breaks from files"
date: 2009-04-12
forum: General Help
---

### Post by BenAshton24 on 2009-04-12
Hello, I have lots of plain text files, all in the format:

```
 NUMBER:NUMBER
    textexttextexttextexttextexttextexttextexttextext
    textexttextexttextexttextexttextexttextexttextext
    textexttextexttextexttextexttextexttextexttextext

 NUMBER:NUMBER
    textexttextexttextexttextexttextexttextexttextext
    textexttextexttextexttextexttextexttextexttextext

```


with the length of text, number value, and number of paragraphs varying with each file. Can someone help me to write a nice "sed" command that will remove the line breaks and spaces in order to leave the text files formatted like so:

```
NUMBER:NUMBER
textexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextext

NUMBER:NUMBER
textexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextexttextext
```

etc. etc. currently all I have is this which would remove the four spaces before each line of each paragraph

```
sed 's/    //g' file.txt > file2.txt
```

Any help would be much appreciated. Thanx

---

### Post by unutbu on 2009-04-12
I know you asked for sed, but would you be interested in a python script?

---

### Post by BenAshton24 on 2009-04-13
> **unutbu said:**
> I know you asked for sed, but would you be interested in a python script?

Yes please, anything that will get the job done :P

---

### Post by unutbu on 2009-04-13
Save this as ~/bin/reformat.py

[PHP]#!/usr/bin/env python
import sys
import re
numpat=re.compile('\s*[0-9]+:[0-9]+')
first=True
for line in open(sys.argv[1],'r'):
    match=numpat.match(line)
    if match:
        if not first:
            print '\n'
        print line.strip()
        first=False
    else:
        print line.strip(),
[/PHP]
Make it executable:
```
chmod 755 ~/bin/reformat.py
```

Run it like this:
```
reformat.py file.txt > file2.txt
```

---

### Post by BenAshton24 on 2009-04-13
Thank you! Your script worked brilliantly, However, I just noticed that although the general format is as I previously specified, the first two lines at the top of the files contain text that doesn't need reformatting. Is there any way to tweak the script slightly so that it skips the first two lines. If not then that's fine because at least the task of changing 1000+ files isn't as big as it was before :P 

Thanks again,
Ben

---

### Post by unutbu on 2009-04-13
How's this?
[PHP]#!/usr/bin/env python
import sys
import re
numpat=re.compile('\s*[0-9]+:[0-9]+\s*')
first=True
for lineno,line in enumerate(open(sys.argv[1],'r')):
    if lineno<2:
        print line,
    else:
        match=numpat.match(line)
        if match:
            if not first:
                print '\n'
            print line.strip()
            first=False
        else:
            print line.strip(),  
[/PHP]

---

### Post by BenAshton24 on 2009-04-13
That is perfect! :D Thank you so much! :) you have saved me lots of time :D

---

