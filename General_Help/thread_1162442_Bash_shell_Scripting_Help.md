---
title: "Bash shell Scripting Help"
date: 2009-05-17
forum: General Help
---

### Post by yma981 on 2009-05-17
Hey Guys

I need some help in programming a bash scrip:

I need to write all the files in a folder/subfolders to a file:  (See script)

#!/bin/bash
path="http://www.xxx.com/yyy/zzz/"
ls -A * > /home/yma/Test/output-$(date +%Y%m%d).txt


But the Issue is that I can't concatenate a web path to the each file: 

ls -A * (on folder folder1)
test1.txt test2.txt folder2/

folder2: 
test3.txt 


1- Suppose the web path is [http://www.xxx.com/yyy/zzz/](http://www.xxx.com/yyy/zzz/)
2- I need the script to write the output file as follow: 
         a- return [http://www.xxx.com/yyy/zzz/folder1/test1.txt](http://www.xxx.com/yyy/zzz/folder1/test1.txt)
                      [http://www.xxx.com/yyy/zzz/folder1/test2.txt](http://www.xxx.com/yyy/zzz/folder1/test2.txt)
                      [http://www.xxx.com/yyy/zzz/folder1/folder2/test3.txt](http://www.xxx.com/yyy/zzz/folder1/folder2/test3.txt)

**Note:** New to bash scripting

---

### Post by geirha on 2009-05-17
```
find * -type f -printf 'http://www.xxx.com/yyy/zzz/%p\n'
```

---

### Post by yma981 on 2009-05-17
Geirha, I really appreciate your hasty response 

It worked like a charm 

Thank You

---

### Post by yma981 on 2009-05-17
I am evolving the script to Add an  additional functionality, after writing the files to a txt, i am appending those files to a global txt file in order to keep track of the files already processed in order to prevent additional processing in the future (file duplication). 

1- I wish the script to read the global file Line by Line and compare it to the line to be written on the /home/yma/Test/output-$(date +%Y%m%d).txt    

2- using an if statement the script should make SURE the File isn't written before in the global filde in order to write it to the output-$(date +%Y%m%d).txt


```
#!/bin/bash

while read line  # this while loop read output.txt (global file) LINE BY LINE
    do
    find * -type f -printf 'http://www.xxx.com/yyy/zzz/%p\n' > /home/yma/Test/output-$(date +%Y%m%d).txt
    done < "/home/yma/Test/output.txt"

cat output-$(date +%Y%m%d).txt >> /home/yma/Test/output.txt   
```     



Any help Please I am confused how the if statement should process the 

```
find * -type f -printf 'http://www.xxx.com/yyy/zzz/%p\n'
```

---

### Post by geirha on 2009-05-17
Probably better to do it the other way around. Loop through the output of the find command, then use grep to check if it is listed in the global file.
```

outfile=/home/yma/Test/output-$(date +%Y%m%d).txt
find * -type f -printf 'http://www.xxx.com/yyy/zzz/%p\n' | 
while read line; do
  grep -q "^$line$" "/home/yma/Test/output.txt" || echo "$line" 
done >> "$outfile"

```

---

### Post by yma981 on 2009-05-17
> **geirha said:**
> Probably better to do it the other way around. Loop through the output of the find command, then use grep to check if it is listed in the global file.
```

outfile=/home/yma/Test/output-$(date +%Y%m%d).txt
find * -type f -printf 'http://www.xxx.com/yyy/zzz/%p\n' | 
while read line; do
  grep -q "^$line$" "/home/yma/Test/output.txt" || echo "$line" 
done >> "$outfile"

```

Dear Geirha,thankx for your help 

I tested the code above, it simply creates the output-$(date +%Y%m%d).txt with the same content as the Global output.txt file -> I am trying to achieve the contrary... I am trying to prevent any file written in output.txt to be written to  output-$(date +%Y%m%d).txt since it would have previously been written in a prior  output-$(date +%Y%m%d).txt

---

### Post by geirha on 2009-05-17
Hm, that's odd. It really shouldn't. The output-$(date) file does not get truncated though. Did it perhaps already exist? Try changing «done >> "$outfile"» to «done > "$outfile"» to make sure it gets overwritten if it exists.

If that still doesn't work, check that the grep does what we expect by doing the following tests in a terminal:

```

line="<an url that exists in output.txt>"
grep -q "^$line$" "/home/yma/Test/output.txt" || echo "$line"   # It should not print anything

line="<an url that does not exist in output.txt>"
grep -q "^$line$" "/home/yma/Test/output.txt" || echo "$line"   # Should print that line since it is not in output.txt

```

---

### Post by yma981 on 2009-05-17
> **geirha said:**
> Hm, that's odd. It really shouldn't. The output-$(date) file does not get truncated though. Did it perhaps already exist? Try changing «done >> "$outfile"» to «done > "$outfile"» to make sure it gets overwritten if it exists.

If that still doesn't work, check that the grep does what we expect by doing the following tests in a terminal:

```

line="<an url that exists in output.txt>"
grep -q "^$line$" "/home/yma/Test/output.txt" || echo "$line"   # It should not print anything

line="<an url that does not exist in output.txt>"
grep -q "^$line$" "/home/yma/Test/output.txt" || echo "$line"   # Should print that line since it is not in output.txt

```

1- I deleted the output-(date).txt and retried, same result the file is recreated and populated with links available in output.txt  («done >> "$outfile"» to «done > "$outfile"» was changed)

2- Both tests with/without URL from output.txt returned values as expected.

---

### Post by geirha on 2009-05-18
Hm. I can't spot any errors, so I don't understand why the script does the complete opposite of what it's supposed to :/

---

### Post by yma981 on 2009-05-18
Why don't you test it yourself Geirha ?

Anyway, I really  appreciate your help and your time. Thanks 

Maybe if we change the algorithm? What if we try the diff command and output.txt and a temp file that output the difference between the 2 file ?? Do u think it will work ?

---

### Post by geirha on 2009-05-18
I have tested it like this.
```
# Start off with an empty global output.txt
> /tmp/output.txt

# Create some folders
mkdir -p /tmp/test/folder{1..4}

# Randomly add ten files in the folders
cd /tmp/test
for ((i=0; i < 10; i++)); do mktemp -p folder$((RANDOM%4+1)); done

# All ten files should now be added to $outfile
outfile=/tmp/output-$(date +%s).txt
find * -type f -printf 'http://www.xxx.com/yyy/zzz/%p\n' |
while read line; do
  grep -q "^$line$" "/tmp/output.txt" || echo "$line"
done >> "$outfile"

# $outfile now contains 10 lines.
$ wc -l "$outfile"
10 /tmp/output-1242651538.txt

# Append it to the global
cat "$outfile" >> /tmp/output.txt

# Create 5 more random files
for ((i=0; i < 5; i++)); do mktemp -p folder$((RANDOM%4+1)); done

# Only the 5 new files should be added this time.
outfile=/tmp/output-$(date +%s).txt
find * -type f -printf 'http://www.xxx.com/yyy/zzz/%p\n' |
while read line; do
  grep -q "^$line$" "/tmp/output.txt" || echo "$line"
done >> "$outfile"

# As expected, only the five new files are added ...
$ wc -l /tmp/output*.txt
  10 /tmp/output-1242651538.txt
   5 /tmp/output-1242651705.txt
  10 /tmp/output.txt
  25 total

```

---

### Post by yma981 on 2009-05-18
I tested the following script (As you suggested) to a remote server with a 61 line output.txt file 

But unfortunately when i scanned manually the output between output.txt and output-(date).txt, I spotted some redundancy between the 2 files in the output-(date).txt which I think contradicts the primary goal, eventhough it worked on my local machine?!!!  

BTW I was writting a second script that worked correctly on my local machine but didn't work properly on the remote server and resulted in some errors. (I checked the pathes and everything should work). Might be resulting from the different environment issues??

note: I tried your test and it worked correctly 

Extract of your code that i used:
```

#!/bin/bash
outfile=/xxx/yyy/zzz/output-$(date +%Y%m%d).txt
find * -type f -printf 'http://www.X.com/Y/Z/%p\n' |
while read line; do
  grep -q "^$line$" "/xxx/yyy/zzz/output.txt" || echo "$line"
done >> "$outfile"
cat "$outfile" >> /xxx/yyy/zzz/output.txt

```

---

### Post by geirha on 2009-05-18
Is the remote machine running something other than linux perhaps? The implementation of the grep and find commands may be different on other UNIX variants. In particualar, the -q option to grep is not widely supported. You could try changing the grep to 
```
grep "^$line$" "/xxx/yyy/zzz/output.txt" >/dev/null 2>/dev/null || echo "$line"
```

What system is the remote machine running?
```
lsb_release -a
uname -a
```

EDIT: Oh, and what version of bash?
```
bash --version
```

---

### Post by yma981 on 2009-05-18
System info:
Linux  2.6.28-9.11.intel.BHsmp #1 SMP Mon Apr 13 10:31:03 MDT 2009 x86_64 x86_64 x86_64 GNU/Linux

Bash version

GNU bash, version 3.2.48(1)-release (x86_64-unknown-linux-gnu)
Copyright (C) 2007 Free Software Foundation, Inc.

---

