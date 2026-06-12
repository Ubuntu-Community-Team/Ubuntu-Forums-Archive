---
title: "Search Text String in Multiple PDFs"
date: 2009-03-02
forum: General Help
---

### Post by fitzbuntu on 2009-03-02
Hi,

Is there an application or tool I could use to search for a string of text in a number of pdf files simultaneously (like 'grep' for text based files)?

I don't want to join the files up.

Thanks.

---

### Post by kaibob on 2009-03-02
The following thread deals with the issue you raise:

[http://ubuntuforums.org/showthread.php?t=1051658](http://ubuntuforums.org/showthread.php?t=1051658)

One post in this thread suggests the following command line:

```
ls *.pdf | xargs -I{} pdftotext {}  - | grep "searchstring"
```

I tried this command line and it does work but there is one issue. The command as written only outputs the text that contains the keyword. I tried a number of grep options but none would output the file name, instead printing "(standard input)". I assume this is due to the pipe. 

There are many grep experts in this forum; perhaps one of them will have a solution.

---

### Post by kaibob on 2009-03-02
If there are no other suggestions, the following shell script will do what you want. It prompts for the search directory and search string and echo's the information to the screen and to a text file. The information consists of the name of the file that contains the search string and the first line in the document that contains the search string. The search is recursive and is not case sensitive. I have included some formatting that can be deleted.

```
#!/bin/bash

# Shell script to search PDF files for text strings.
# Has predefined search locations.
# Allows two noncontiguous search strings. 
# Outputs search results to screen and to text file. 

echo

# Prompt for search location.
while true ; do
	echo -n "Enter (h)ome (r)oot (w)estern or (e)xit: "
	read KEYPRESS
	if [ "$KEYPRESS" = "" ] ; then 
		echo
		echo "You did not make a selection!"
		echo
		elif [ "$KEYPRESS" = h ] ; then 
		SEARCHDIR=/home/bob/
		break
		elif [ "$KEYPRESS" = r ] ; then 
		SEARCHDIR="/ -xdev"
		break
		elif [ "$KEYPRESS" = w ] ; then 
		SEARCHDIR=/media/WESTERN-EXT3/
		break
		elif [ "$KEYPRESS" = e ] ; then 
		echo
		exit 0
		else
		echo
		echo "You did not make a valid selection!"
		echo
	fi
done

echo

# Prompt for 1st search string.
while true ; do
	echo -n "Enter 1st search string or (e)xit: "
	read WORDONE
	if [ "$WORDONE" = "e" ] ; then 
		echo
		exit 0
		elif [ "$WORDONE" != "" ] ; then 
		break
		else
		echo
		echo "You forgot a search string!"
		echo
	fi
done

echo

# Prompt for 2nd search string.
echo -n "Enter 2nd search string or (e)xit: "
read WORDTWO
if [ "$WORDTWO" = "e" ] ; then 
	echo
	exit 0
fi

# Create search text file with search location. 
if [ "$KEYPRESS" = r ] ; then
	echo "Search location: /" > /home/bob/documents/search
	else
	echo "Search location: $SEARCHDIR" > /home/bob/documents/search
fi

echo >> /home/bob/documents/search

# Add search string to search text file. 
if [ "$WORDTWO" = "" ] ; then
echo "PDF search strings: 1) $WORDONE 2) none" >> /home/bob/documents/search ; else
echo "PDF search strings: 1) $WORDONE 2) $WORDTWO" >> /home/bob/documents/search
fi

# Perform search and output to screen and to search text file. 
find $SEARCHDIR -iname '*.pdf' -type f 2>/dev/null | sort -d | while read FILE ; do
	if [ "$WORDTWO" = "" ] ; then
		STRINGMATCH=$(pdftotext -q -layout "$FILE" - | \
		tr -d '\001-\010\013-\037\177-\377' | tr -s ' ' | \
		fgrep -i "$WORDONE") ; else
		STRINGMATCH=$(pdftotext -q -layout "$FILE" - | \
		tr -d '\001-\010\013-\037\177-\377' | tr -s ' ' | \
		fgrep -i "$WORDONE" | fgrep -i "$WORDTWO")
	fi	
	if [ ! "$STRINGMATCH" == "" ]; then 
		echo | tee -a /home/bob/documents/search
		echo "$FILE" | tee -a /home/bob/documents/search
		echo "$STRINGMATCH" | tee -a /home/bob/documents/search
	fi
done

# Add "No matches!" notation to search text file if appropriate. 
SEARCHLINES=$(wc -l /home/bob/documents/search | cut -d ' ' -f1)

if [ "$SEARCHLINES" -le 4 ] ; then
	echo | tee -a /home/bob/documents/search	
	echo "No matches!" | tee -a /home/bob/documents/search
fi

echo
```

EDIT: I decided to enhance this script for my own use and have included this version FWIW. It reports all instances of search strings, although this can be changed so that only the first instance of the search string is shown. This is done with the fgrep "-m 1" option.

---

### Post by yther on 2009-03-02
Have you looked at [Strigi]("http://strigi.sourceforge.net/")?  It seems to be capable of indexing PDF files, and it's present in Ubuntu's package repositories.

I don't know what's involved in setting it up, but if you are going to need to search PDFs often, it might be worth checking out.

---

