---
title: "Make a shell script that downloads webcomics"
date: 2009-03-28
forum: General Help
---

### Post by transmition on 2009-03-28
I was wondering if someone could help me create a shell script that would download the newest webcomic from each of these sites:

[http://xkcd.com/](http://xkcd.com/)
[http://www.penny-arcade.com/comic/](http://www.penny-arcade.com/comic/)
[http://www.dilbert.com/fast](http://www.dilbert.com/fast)
[http://www.explosm.net/comics/new/](http://www.explosm.net/comics/new/)
[http://www.questionablecontent.net/QCRSS.xml](http://www.questionablecontent.net/QCRSS.xml)
[http://www.smbc-comics.com/#comic](http://www.smbc-comics.com/#comic)

I realize that I would have to use something like wget, but I have no idea how to go about doing this.

Thank you.

---

### Post by PhrankDaChickenGeek on 2009-03-29
Here's an idea of how to do it - 
Create a script and edit it-
```
touch get_xkcd.sh
chmod a+x get_xkcd.sh
gedit get_xkcd.sh
```

In the script:
```

#!/bin/sh

# Script for downloading webcomic XKCD
# By Phrankdachicken

# Download the front page of xkcd
wget xkcd.com -O xkcd.html

# Get just the line with the image URL on it and
# clean up the HTML on either side of the link
IMAGEURL=$(cat xkcd.html  | grep embed | sed 's/^.*\: //g' | sed 's/png.*$/png/g')

# Delete the downloaded front page
rm xkcd.html

# Download the Image
wget $IMAGEURL -O todays_xkcd.png

```

Run the script
```

./get_xkcd.sh

```

You'll have to change it a little bit for each website. View the page source and image URL to see if there are common factors that can be used in a script. A lot of comics use naming conventions by date, so you could accurately get the image URL by a simple 'date +%??' command. See "man date" for more details

---

### Post by transmition on 2009-03-29
Ok, thank you. One question though, can you explain:

```

 sed 's/^.*\: //g' | sed 's/png.*$/png/g'

```

---

### Post by PhrankDaChickenGeek on 2009-03-29
Yes ;-P

sed is doing a search and replace
'cat xkcd.html  | grep embed' Prints out the downloaded front page and searches for the word 'embed'. Since this only occurs once on the page, we get one line from the html file:
'<h3>Image URL (for hotlinking/embedding): http://imgs.xkcd.com/comics/well.png</h3>'

Now we use sed to strip away everything except for the image URL.

sed 's/^.*\: //g' does a search and replace. It will search for the text between the first two // and replace it with the text between the middle and last /.
'^' means the beginning of the line
'.*' means all characters in between
and then '\: ' means ': '
So we're searching for "Beginning of line until : " and replacing it with nothing. This deletes "<h3>Image URL (for hotlinking/embedding): " from our string.

We take what we have left: "http://imgs.xkcd.com/comics/well.png</h3>" and run it through sed again - sed 's/png.*$/png/g'
'$' means end of line.
So we search for "png to end of line" and replace it with just "png"

This leaves us with just the URL of the image: "http://imgs.xkcd.com/comics/well.png"
which we can feed to wget to download!

---

### Post by transmition on 2009-03-29
Ok, that works for xkcd, and I can grep to get the line containing the image. However, every other site has something along the lines of:

```

<div class="simplebody"><img src="/images/2009/20090327.jpg" alt="The Law Of Unintended Consequences" width="750" height="376" /></div>

```

So the image is listed as: /images/2009/20090327.jpg

When the full path is: penny-arcade.com/images/2009/20090327.jpg

So I tried:
```

IMAGEURL=$(cat penny.html | grep simplebody | sed '/^.*\src=" penny-arcade.com/g' | sed 's/jpg.*$/jpg/g')

```

To replace 
```

<div class="simplebody"><img src="

```

with
```

penny-aracade.com

```

Unfortunately this produces an error stating:
```

Resolving <div... failed: Name or service not known.
wget: unable to resolve host address `<div'
--2009-03-29 15:41:32--  http://class=%22simplebody%22%3E%3Cimg/
Resolving class="simplebody"><img... failed: Name or service not known.
wget: unable to resolve host address `class="simplebody"><img'
--2009-03-29 15:41:37--  http://src=%22/images/2009/20090327.jpg
Resolving src="... failed: Name or service not known.
wget: unable to resolve host address `src="'

```

---

### Post by Gunman1982 on 2009-03-29
uhm you could use dosage to do the job.
type 'sudo apt-get install dosage' in the console and you get it.

Just remember: people who make those webcomics earn what little money they can by advertisement on the page. They don't really like it when people just download the comic without visiting the webpage.

---

### Post by transmition on 2009-03-29
Well, I use adblock, so the whole advertising point is moot anyway.

Also, it is quite important that this is done with a shell script. So, if someone can help me fix my error, that would be appreciated.

---

### Post by PhrankDaChickenGeek on 2009-03-29
You must filter special characters with a back slash '\', otherwise sed with think they are part of the command

So try something like:
```

IMAGEURL=$(cat penny.html | grep simplebody | sed 's/^.*\src\=\" penny\-arcade\.com//g' | sed 's/jpg.*$/jpg/g')
```


EDIT: Fixed command, forgot "s" at beginning of first sed command

---

### Post by transmition on 2009-03-29
Ah! Thank you. I thought I tried that with ", forgot that = is a special character also.

EDIT: Still get an error: 
```

sed: -e expression #1, char 33: unknown command: `/'

```

---

### Post by amauk on 2009-03-29
Ha
I have this exact thing to grab the daily Dilbert comics

I also run it through Imagemagick's mogrify to increase the image size as the Dilbert comics are a little small

**grab_daily_dilbert**
```
#! /bin/bash

if [ -n "$1" ];
then
	DIL_YEAR=$1
else
	DIL_YEAR=$(date +%Y)
fi

if [ -n "$2" ];
then
        DIL_MONTH=$2
else
        DIL_MONTH=$(date +%m)
fi

if [ -n "$3" ];
then
        DIL_DAY=$3
else
        DIL_DAY=$(date +%d)
fi

if [ ! -f "/media/raid5/raid5-tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH/$DIL_YEAR-$DIL_MONTH-$DIL_DAY.gif" ];
then

	HTML=`wget -q -O - "http://www.dilbert.com/fast/$DIL_YEAR-$DIL_MONTH-$DIL_DAY/index.html" | grep '.gif' | sed 's|src=\"\(/[^\"]*strip[^\"]*gif\)\"|\nhttp://www.dilbert.com\1\n|g' | grep 'http://www.dilbert.com'`

	if [ "$HTML" != "http://www.dilbert.com/dyn/str_strip/default_th.gif" ];
	then
		if [ ! -d /media/raid5/raid5-tony/Webcomics/dilbert/$DIL_YEAR ];
		then
			mkdir /media/raid5/raid5-tony/Webcomics/dilbert/$DIL_YEAR
		fi
		if [ ! -d /media/raid5/raid5-tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH ];
		then
			mkdir /media/raid5/raid5-tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH
		fi

		wget -q -O /media/raid5/raid5-tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH/$DIL_YEAR-$DIL_MONTH-$DIL_DAY.gif $HTML
		mogrify -resize 200% /media/raid5/raid5-tony/Webcomics/dilbert/$DIL_YEAR/$DIL_MONTH/$DIL_YEAR-$DIL_MONTH-$DIL_DAY.gif
	fi
fi
```

Run the above script without any arguments to download todays comic

```
./grab_daily_dilbert
```

Run the above with year, month & day arguments to grab a comic from that date

```
./grab_daily_dilbert 2008 04 12
```



I also made this script
This will cycle backwards in time, from today all the way back to the first 

```
#! /bin/bash

for ((i=0;i<=7300;i+=1));
do
	T_YEAR=`date --date="$i days ago" +%Y`
	T_MONTH=`date --date="$i days ago" +%m`
	T_DAY=`date --date="$i days ago" +%d`

	echo "${T_YEAR}-${T_MONTH}-${T_DAY} - $i"

	/home/lounge/scripts/grab_daily_dilbert $T_YEAR $T_MONTH $T_DAY
done
```

There's hard-coded paths in these scripts, so you'll have to edit to suit

---

