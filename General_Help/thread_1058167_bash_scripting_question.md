---
title: "bash scripting question"
date: 2009-02-02
forum: General Help
---

### Post by easoukenka on 2009-02-02
Ok I need to sort a file and delete duplicate content all from the terminal in my bash script.  I know there is uniq and some sed options available but my situation is a little tricky I have a list of the ends of urls like this

?d=603W2UZ6
?d=TPWQRB05
?d=48LZRRP9
?d=UJRT4R03

however if they have already been downloaded my script adds a # to the beginning so the file could look like this 

#?d=603W2UZ6
#?d=TPWQRB05
?d=48LZRRP9
?d=UJRT4R03

when I add a a file I want it to not only delete duplicates but also delete the duplicates if they have a # before them.

so if I add ?d=603W2UZ6 to my file I want it to check for exact duplicates and if #?d=603W2UZ6 exists then realize it is a duplicate also

Ok you really dont need to see my script but it may be interesting to someone it is below as follows do not make fun of it I am learning :) 

#!/bin/bash

#this is where the files will be downloaded too
#DOWNLOAD_PATH=~/sandbox/mega/downloads
DOWNLOAD_PATH=~/downloads/megavideo

#filename with links can be whatever you want
LINKSLIST=linkslist

#### should not be a reason to modify below ####

#dont want no files found and I want to clean up for files left when user breaks early
touch temp/returned_url
rm temp/returned_url*

#this script excepts a download speed parameter if blank it will run full speed
DOWNLOAD_SPEED=$1

#create random number so when sharing on for instance a server files will not collide
THISRANDOM=$RANDOM

#makes my job possible to remove allt he / from the file can't figure it out without it.
TRIMMED_LINK_REGEX="http:\/\/www\.megaupload\.com\/"

#keep this here it needs to match what your taking out with the regex above
TRIMMED_LINK_REAL="http://www.megaupload.com/"

#going to trim links in file easier to work with in this script 
sed "s/$TRIMMED_LINK_REGEX//g" -i $LINKSLIST

#this will check for duplicate lines so you dont redownload stuff


#end of development


#prep the file
exec < $LINKSLIST
#count not used yet but I will implement output that shows how many files later
count=0;
#we are going to loop through the file now
while read line; do
	((count++));
	#files are marked with # when they have already been marked as completed I like to keep a running inventory and I will later implement duplicate download checking
	if [[ ${line:0:1} != "#" ]]; then 
		DOWNLOAD=$line;
		#check if first character is # which according to later in this scripts means the download has already been completed
		if [ ${DOWNLOAD:0:1} != "#" ]; then
			#feed the library now to get the premium link
			bash_libs/muspider.sh "$TRIMMED_LINK_REAL$DOWNLOAD" > temp/returned_url$THISRANDOM
			PREMIUM_LINK=`cat temp/returned_url$THISRANDOM`;
			#download now
			if [ "$DOWNLOAD_SPEED" == "" ]; then
				wget -c -P $DOWNLOAD_PATH "$PREMIUM_LINK";
			fi
			if [ "$DOWNLOAD_SPEED" != "" ]; then
				wget -c -P $DOWNLOAD_PATH --limit-rate=$DOWNLOAD_SPEEDk "$PREMIUM_LINK";
			fi
			#lets do a quick check make sure connection is ok so we dont accidently delete files because of a disconnect
			if ping -c1 google.com 
			then
				echo "******************************************************************************"
				echo ""
				echo "DOWNLOAD COMPLETE... MARKING YOUR ENTRY AS COMPLETE"
				echo ""
				echo "******************************************************************************"
				#mark that download as complete with a #
				sed -i -e "s/${DOWNLOAD}/#${DOWNLOAD}/g" $LINKSLIST
			else 
				echo "******************************************************************************"
				echo ""
				echo "YOU ARE NOT ON THE INTERNET"
				echo ""
				echo "******************************************************************************"
			fi

		fi
	fi
done
rm temp/returned_url$THISRANDOM
echo "******************************************************************************"
echo ""
echo "DOWNLOADS COMPLETE"
echo ""
echo "******************************************************************************"

---

### Post by sdennie on 2009-02-02
I believe that what you want is:

```

sed -e "s/^#//" some_file | sort | uniq

```

---

### Post by easoukenka on 2009-02-03
Hello thank you for the help however the data returned strips all the # from my files and now my script can't determine what has already been downloaded.

---

### Post by easoukenka on 2009-02-03
not very well but I got it thank you for the help 

#extremely inefficient but working this will only add a file if it is a new entry 

#backing up and trimming the master list to help with getting diff
cp $MASTERLIST temp/masterlist$THISRANDOM
sed -e "s/^#//g" -i temp/masterlist$THISRANDOM

#creating a backup file to work with
cp $LINKSLIST temp/list$THISRANDOM
#combining lists
cat $MASTERLIST >> temp/list$THISRANDOM

sed -e "s/^#//g" -i temp/list$THISRANDOM

sed -e "s/^#//" temp/list$THISRANDOM | sort | uniq -d > temp/duplicate_lines$THISRANDOM

#prep the file
exec < temp/duplicate_lines$THISRANDOM
#we are going to loop through the file now
while read line; do
	sed -e "s/$line//g" -i temp/list$THISRANDOM
done
#deleting blank lines
sed -e "/^$/d" -i temp/list$THISRANDOM
#going to pull the diff and store it in a variable direct cat'n buggy
NEW_ENTRY=`diff temp/list$THISRANDOM temp/masterlist$THISRANDOM | grep \< | cut -d ' ' -f2` 
echo "$NEW_ENTRY" >> $MASTERLIST
#we now have appended the masterlist with only new downloads!

---

