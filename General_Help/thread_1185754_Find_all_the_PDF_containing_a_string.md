---
title: "Find all the PDF containing a string"
date: 2009-06-12
forum: General Help
---

### Post by badook on 2009-06-12
I've written a little bash script that makes it possible to search the contents all the pdfs in a certain folder to find the occurrences of a string. 
It uses a zenity gui so it's quite user friendly; after the search is completed the user is provided with a list of files and a double-click opens evince on the page where the first occurrence of the string is.
I hope it can be useful to somebody!

```

#!/bin/bash

IFS="
"

# Select Directory
NEWPATH=$(zenity --file-selection --directory --title="Select the Directory")
if [ -z "$NEWPATH" ]; then
	echo 'No Directory Selected'
	exit 1
fi
cd $NEWPATH

files=$(ls *.pdf -1)
if [ $? != "0" ]; then
	zenity -error --text='No files to convert!'
	exit 3
fi

#Get Keyword
KEYWORD=$(zenity --entry --text="Enter Keyword" --title="Search in PDF")
if [ -z "$KEYWORD" ]; then
	echo 'No keyword'
	exit 2
fi

#Files text exctraction and matching
( for MYFILE in $files; 
	do
	result=$(pdftotext $MYFILE  - | grep $KEYWORD -i)
	if [ -n "$result" ]; then
		echo $MYFILE >> '/tmp/pdfFinder'
	fi
done
) |  zenity --progress --title='Processing PDFs' --pulsate --auto-close

#Checking Results
list=$(cat '/tmp/pdfFinder')
if [ -z $list ]; then
	zenity --error --text='No pdf found!'
	exit 5
fi
rm '/tmp/pdfFinder'

#Show List until user exits the program or selects a file
while [ 1 ]; do
	fileToOpen=$(zenity --list --column="FileName" --title="Files containing \"$KEYWORD\"" $list)
	if [ $? == '0' ]; then
		if [ -z "$fileToOpen" ]; then
			zenity --error --text='No file Selected'
		else
			#Running pdf viewer already looking for our word
			evince --find=$KEYWORD $fileToOpen
		fi
	else
		exit 4
	fi
done

```

edit. edit a line in order to keep the results window open

---

### Post by blueridgedog on 2009-06-12
Well done.  Thanks for taking time to post this.

---

### Post by dm_research on 2010-04-10
Thanks very much badook - I was looking for something like this.  I also found pdfsearch on sourceforge, but this might be a better option for me since it looks at the pdf files one-by-one.  I'll give it a try...

---

### Post by dm_research on 2010-04-10
It did the job - well done :)

I was impressed with zenity too - must keep it in mind for my scripts.

Good luck.

---

### Post by niziris on 2010-08-23
Hello! 
I am ubuntu newbe :(...and I desperately need pdf searcher
sooo my question is 

how do I start this script? 

I tried with
./FindPdf.sh
from the place where script is

---

### Post by Vaphell on 2010-08-23
and what happened? did you mark it as an executable? and do you have that zenity app installed?

---

### Post by niziris on 2010-08-23
> **Vaphell said:**
> and what happened? did you mark it as an executable? and do you have that zenity app installed?

Well I have zenity installed and 
when I put ./FindPdf.sh
in terminal, response is "permission denied"
then I checked permission for script and I have it (or I thing that I have it)

when I put 
sudo ./FindPdf.sh
after entering pass
response is "command not found" :(

what am I doing wrong?

---

### Post by Forgotten Path on 2010-08-23
Try:
```
$ chmod 755 ./FindPdf.sh
$ ./FindPdf.sh
```
You may need to use sudo to run the chmod command.

Maybe sudo is looking in /bin or /usr/bin for the script.  You could try copying it to each of those locations, but maybe someone has a better idea before you throw extra stuff into the system folders...
```
$ sudo cp ./FindPdf.sh /bin
$ sudo cp ./FindPdf.sh /usr/bin
```

Nice script, badook.

---

### Post by luigi_mb on 2010-08-23
You can always use "beagle" (Synaptic). It indexes all documents, including .pdf files. Then you can search with Beagle Search". Very fast. 

/luigi

---

### Post by niziris on 2010-08-24
> **Forgotten Path said:**
> Try:
```
$ chmod 755 ./FindPdf.sh
$ ./FindPdf.sh
```You may need to use sudo to run the chmod command.

Maybe sudo is looking in /bin or /usr/bin for the script.  You could try copying it to each of those locations, but maybe someone has a better idea before you throw extra stuff into the system folders...
```
$ sudo cp ./FindPdf.sh /bin
$ sudo cp ./FindPdf.sh /usr/bin
```Nice script, badook.

thanks for replay :) I will tray that

> **luigi_mb said:**
> You can always use "beagle" (Synaptic). It  indexes all documents, including .pdf files. Then you can search with  Beagle Search". Very fast. 

/luigi

Thanks for the idea, beagle work great!!

 but I still need to figure out how to start scripts

---

### Post by mps_1 on 2011-05-11
Thanks you very much! **It do what it promise**!! 
Great. Really great!
:popcorn:

---

### Post by guyal on 2012-10-09
Great script, good job!!

I wonder how to make it recursive. The line which should be modified is probably:
[FONT="Courier New"]files=$(ls *.pdf -1)[/FONT]

I thought to use [FONT="Courier New"]find[/FONT] instead but couldn't manage to make it work. Ideas?

---

### Post by overdrank on 2012-10-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

