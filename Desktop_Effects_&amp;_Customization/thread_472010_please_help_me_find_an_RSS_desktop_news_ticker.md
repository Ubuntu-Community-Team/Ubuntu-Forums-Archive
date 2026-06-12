---
title: "please help me find an RSS desktop news ticker"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by lcohen999 on 2007-06-12
I have tried in earnest to get GNUsTicker to work in my Feisty Installation

see attachment for the error.

Google has turned up nothing.

Can anyone recommend a google desktop / microsoft sidebar / RSS news ticker that goes on the desktop (not a separate program)

Thanks!

---

### Post by Hortinstein on 2007-06-13
you can use conky with the help of a shell script....there are many help topic on this throughout the forums

here is the shell script that you use within conky....i am assuming you know a little coding

```

#!/bin/bash
# RSS Display Script by Bill Woodford (admin@sdesign.us) v1.0
#
# This script is designed to output story titles for most any RSS Feed.
#
# This script depends on curl.  Please ensure it is installed and in your $PATH
# Gentoo: emerge -av net-misc/curl
# Debian: apt-get install curl
# Homepage: http://curl.haxx.se/
#
# Usage:
# .conkyrc:	${execi [time] /path/to/script/conky-rss.sh URI LINES TITLENUM}
#	URI = Location of feed, ex. http://www.gentoo.org/rdf/en/glsa-index.rdf
#	LINES = How many titles to display (default 5)
#	TITLENUM = How many times the title of the feed itself is specified, usually 1 or 2 (default 2)
#
# Usage Example		
#		${execi 300 /home/youruser/scripts/conky-rss.sh http://www.foxnews.com/xmlfeed/rss/0,4313,1,00.rss 4 2}

#RSS Setup - Don't change unless you want these values hard-coded!
uri=$1							#URI of RSS Feed
lines=$2						#Number of headlines
titlenum=$3						#Number of extra titles

#Script start
#Require a uri, as a minimum
if [[ "$uri" == "" ]]; then
	echo "No URI specified, cannot continue!" >&2
	echo "Please read script for more information" >&2
else
	#Set defaults if none specified
	if [[ $lines == "" ]]; then lines=5 ; fi
	if [[ $titlenum == "" ]]; then titlenum=2 ; fi

	#The actual work
	curl -s --connect-timeout 30 $uri |\
	sed -e 's/<\/title>/\n/g' |\
	grep -o '<title>.*' |\
	sed -e 's/<title>//' |\
	head -n $(($lines + $titlenum)) |\
	tail -n $(($lines))
fi

```

to learn how to use conky just browse the forums

this is my fav desktop news reader/computer stats giver...its simple and lightweight

---

### Post by svdb on 2007-10-15
Conky is ugly, takes too much desktop space and I don't know anything about "coding", so, any other suggestion of a news ticker (not a new reader!) that would work out of the box?
Thanks.

---

### Post by Be_Linux on 2007-10-27
I have the same problem .. Do you solve it ?

---

