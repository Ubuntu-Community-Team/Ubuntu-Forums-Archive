---
title: "File Comparison script"
date: 2009-02-05
forum: General Help
---

### Post by ChimpofDOOM on 2009-02-05
Hey guys,

Ok, need some help because I'm kind of stumped.  
Basically what I want to do is compare the contents of 2 files and spit out the differences.

Using the diff command this can be done, however my problem is that diff checks line by line and if a new line appears, it throws all the results off.  

What I'm looking for is a way that it can check the contents of a file and identify what's different, not what was there before (regardless if something may of changed line)

Any idea's on how this can be done appreciated? :D

---

### Post by ajgreeny on 2009-02-05
> Using the diff command this can be done, however my problem is that diff checks line by line and if a new line appears, it throws all the results off. 
I'm not quite sure what you mean by this as any extra lines added to a file still appear as the difference between the two, as far as I can see.

---

### Post by Simian Man on 2009-02-05
Use sdiff.  This will provide much better for comparison.  If you are a vimmer, there's also vimdiff.  I think emacs has something too if that is your thing.

---

### Post by ChimpofDOOM on 2009-02-05
> **ajgreeny said:**
> I'm not quite sure what you mean by this as any extra lines added to a file still appear as the difference between the two, as far as I can see.

Yeah sorry, badly worded :)

Here's an example:

File 1:
Howdy
Hello
Bonjour
Guten Tag

File 2:
Howdy
Bonjour
Guten Tag
Hello
Goed Middag

Now if diffs was to run that it would see the line differences, what I need it to be able to do, is effectively, see "Hello" and then scan the entire document until it can see it, then move on.  In this example it would report "Goed Middag" as a difference between the 2 files.

I think this script might do it, but any suggestions or alterations, welcome.

```
#!/bin/bash
 
compareFile = "/path/to/file/to/compare.txt"
outputFile = "/path/to/outputFile.txt"
 
for filename in /some/dir/of/text/files/*.txt; do 
        
        numlines=`cat $filename | wc -l`
                
        for i in `seq 1 $numlines`; do 
                current=`cat $filename | head -$i | tail -1` 
 
                grep -q "${current}" ${compareFile} 
 
                if [ $? != 0 ]; then
                         #doesn't exist, append to $outputFile
                        echo "${filename}:${current}" >> ${outputFile} 
                fi
        done 
done
```

---

### Post by mixmaster on 2009-02-05
sort both files then compare the results?

---

### Post by Simian Man on 2009-02-05
```

# cmpr
#!/bin/bash

sort $1 > t1
sort $2 > t2

sdiff t1 t2 | less

```

cmpr f1 f2

```

Bonjour                                                         Bonjour
                                                              > Goed Middag
Guten Tag                                                       Guten Tag
Hello                                                           Hello
Howdy                                                           Howdy
(END) 

```

Seems to be what you want.

---

