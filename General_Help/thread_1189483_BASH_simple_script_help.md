---
title: "BASH: simple script help"
date: 2009-06-16
forum: General Help
---

### Post by ianneilson on 2009-06-16
Hi there,

I have a simple bash script I've made that compares two numbers (in this case they are actually hashes of files). The first has ($ORIGCOUNT) gets extracted from a log file, the second ($MYCOUNT) at the moment is hard coded into the file.

Here is the script:

```
#!/bin/bash

MYCOUNT=`echo "23551"`

ORIGCOUT=`grep "string" ./include/hash.txt |grep -v "tar" |cut -d " " -f2`

echo "hash from the file is $ORIGCOUT"
echo "my hash is $MYCOUNT"

if [ "$MYCOUNT" = "$ORIGCOUNT" ]; then
        echo "Hashes match, continuing."
else    echo "Hashes don't match!"
        exit
        fi

echo "Test completed."

```However, I get the following output:

[ian@SERVER automation]$ ./test_hash.sh
hash from the file is 23551
my hash is 23551
Hashes don't match!

########################

As you can see though.. They actually do match, but it is coming back as them not matching..

Any help?..



##########################


Sorry, just realised this is kinda in the wrong catagory, if someone could move this thread to somewhere more aproperate for me that would be great...

---

### Post by swisstone198 on 2009-06-16
run 

bash -x <script>

this will show you what it is doing

---

### Post by swisstone198 on 2009-06-16
spelling mistake on origcount

---

### Post by ianneilson on 2009-06-16
> **swisstone198 said:**
> spelling mistake on origcount


AAAAAAAAAAAAAAAAAAAAAAAAAAAAHHHHHHHHHHHHHHHHHH!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I'm a moron, thanks for your help.

---

### Post by swisstone198 on 2009-06-16
No worries, we all do it.

---

