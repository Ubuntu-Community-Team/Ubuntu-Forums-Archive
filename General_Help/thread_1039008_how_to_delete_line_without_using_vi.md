---
title: "how to delete line without using vi?"
date: 2009-01-14
forum: General Help
---

### Post by siuchi on 2009-01-14
It is a bad title i know. What i wanna ask is how can a delete a line in file without using vi , or i should say the quickest way.

Let me make an example.

I want to delete line 16 in .ssh/known_hosts. I need to open vi , go to line 16 then delete.

Is there any quicker way?

Thanks

---

### Post by eentonig on 2009-01-14
Using vi

> vi *filename*   # open the file
16G    # Go to the 16th line
dd     # delete the line under your cursor
:wq!   # save and exit

Or you could use sed if you now how to match the 16th line

[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

---

### Post by kivuyo on 2009-01-14
i want to edit a file using vi .im using gedit ,in case of edit server file when im my local machine its hard ,
kivuyo

---

### Post by hyper_ch on 2009-01-14
in nano you delete lines with ctrl+k

---

### Post by eentonig on 2009-01-14
Can you rephrase that sentence? I'm having a hard time understanding what exactly you're trying to say.

If I understand you correctly:
- You want to use vi?
- You currently use gedit?
- You need to modify a file on another machine? I guess you access the server via ssh?

---

### Post by sdennie on 2009-01-14
Try:

```

sed -n '16!p' some_file

```

If that gives you the desired output, use:

```

sed -n -i '16!p' some_file

```

---

### Post by mixmaster on 2009-01-14
The following script will delete line N (counting from 0) from a file:

#!/bin/bash
file=$1
rm /tmp/__lineremover__ 2>/dev/null
cat $file | awk '
BEGIN { i=0; }
{
line = $0;
if (i != '$2') {
print line;
}
i++;
}
' >> /tmp/__lineremover__
mv /tmp/__lineremover__ $file

(invocation is <executablename> file-to-remove-line-from line-to-remove)
it can easily be modified to always work on your known_hosts file if that is what you want

---

