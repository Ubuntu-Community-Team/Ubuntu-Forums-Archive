---
title: "Search odt files"
date: 2009-05-05
forum: General Help
---

### Post by triplemaya on 2009-05-05
I often need to search a directory for a string in a file. The gnome-search-tool works ok for most file types, though the interface is a bit clunky, but it doesn't seem to search odt files, certainly it doesn't find files which have the word I'm searching for which I know are there!
Google desktop search is a fantastic tool, but as far as I can see there's no way to limit the search to a specific directory, and there's often such a blizzard of results it's quicker to go look in half a dozen files by hand.
Beagle doesn't seem to have a directory filter either.
Can anyone recommend a good search tool that will search just one directory?

---

### Post by spacesamurai on 2009-05-05
Call me old fashion, but how about the good ol' "find" command? Something akong the lines as: 

#find /[your]/[directory] -name *.odt

---

### Post by triplemaya on 2009-05-05
Thanks, but that just gets me all the odt files, I'm looking for odt files which contain a specific word, "hologram" for instance.

---

### Post by spacesamurai on 2009-05-05
If that is the case, you can just edit the name of the file you are searching for so that it matches that which you are searching for. 

The wildcards (i.e [*]) will check for any characters that may be in the file name. 

#find /[your]/[directory] -name *hologram*.odt

Hope this helps.

---

### Post by triplemaya on 2009-05-05
I'm looking for a string *inside* the file, not a string in the filename! I need to search through all the files one by one and get a list of all of the files which contain a string in the text of the file. And I need to search all text files, not just odt files, but I do need to search the odt files as well as all the others.

---

### Post by NoReflex on 2009-05-05
Hello!

I think you will find this thread useful : 
[http://ubuntuforums.org/showthread.php?t=899179](http://ubuntuforums.org/showthread.php?t=899179)

Best wishes,
NoReflex

---

### Post by triplemaya on 2009-05-05
Thanks for posting the thread link. The thread is highly informative, but not a complete solution. 

The bash script posted there works, but there is a problem with it.

It does not handle whitespace, so since most of my file names are long, descriptive, and contain whitespace, I get a huge list of lines like this
unzip:  cannot find or open of, of.zip or of.ZIP.
and, of course, the files which have whitespace in the name are not opened and searched.

The script is

 	```

#!/bin/bash

if [ $# -ne 1 ]; then
	echo "Usage: searchodt searchterm"
	exit 1
fi

for file in $(ls *.odt); do
	unzip -ca "$file" content.xml | zgrep -ql "$1"
	if [ $? -eq 0 ]; then
		echo "$file"
	fi
done

```

If someone could show me how to get the whole filename in one, with whitespace, this should be a winner.

---

### Post by NoReflex on 2009-05-05
On the second page of that thread there is a new version of the script posted by MelIrizarry that should work.
```
#!/bin/bash

if [ $# -ne 2 ]; then
        echo "Usage: searchodt searchpath searchterm"
        exit 1
fi

find $1 -name "*.odt" | while read file
do
        unzip -ca "$file" content.xml | grep -qli "$2"
        if [ $? -eq 0 ]; then
                echo "Found keyword in: " $file
        fi
done
```

I haven't tested it but I'm guessing it's OK.

Good luck!

Best wishes,
NoReflex

---

### Post by triplemaya on 2009-05-05
Thank you. It works a treat. Deep red embarrassed smiley.

---

### Post by tdk77 on 2012-03-28
Sorry to bring up this old thread...
but if I'm looking for an odt file with the keyword "baxter", and it's on a file in my desktop how would I apply it to this code?

---

### Post by Vaphell on 2012-03-28
you save that code from #8 as a script, mark it executable and invoke it with 2 parameters: path and phrase
```
./script ~/Desktop baxter
```

---

