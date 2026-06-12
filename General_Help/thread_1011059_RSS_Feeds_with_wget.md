---
title: "RSS Feeds with wget?"
date: 2008-12-14
forum: General Help
---

### Post by calrogman on 2008-12-14
I enjoy listening to the radio, and, being based in Britain, one of my favorite stations is BBC Radio 1, I enjoy in particular the "Scott Mills Show", which is on 4-7pm GMT, however I am often busy doing other things and can't always listen.  Very convenient then, that the show has daily podcasts.

The problem here is that I would like my laptop to download the latest podcasts maybe every Sunday night.  I've written a bash script that (logic suggest) should do this, but it doesn't work.

Here's the code so far, very heavily commented for human readability (I need to use good programming/scripting habits, what with first learning Visual Basic, it was disgusting).

OK, after the problems with the first script I've rewritten from scratch, using lots of lovely functions! First time I've used functions actually. :)

```

#! /usr/bin/env bash

#Uncomment this line to enable tracing, useful for debugging.
#set -x

function navigate {

	# Go to correct location.
	cd ~/Music/Scott-Mills-Podcast

}

function makedir {

	#Make the necessary directories.
	cd ~/Music
	mkdir Scott-Mills-Podcast

}

function download {

	#Download XML file.
	wget [http://downloads.bbc.co.uk/podcasts/radio1/mills/rss.xml](http://downloads.bbc.co.uk/podcasts/radio1/mills/rss.xml)
	#Try to parse XML for links to .mp3s and download them.
	wget -nc -A=*.mp3 -i rss.xml

}

function purge{

	#Delete the XML file.
	rm rss.xml

}

if [ -d "~/Music/Scott-Mills-Podcast" ] #Check to see if this directory exists.
then
	navigate #If it does call "navigate"
else
	makedir #Otherwise make it.
fi

download
purge

```

The only problem now, is that despite having lots of links to mp3s the XML file does not parse correctly and wget claims that their are no valid URLs.  Any Ideas?

If anyone can diagnose the problem and tell me how to fix it, it would be greatly appreciated.

I await your correspondence, and hope if this script is disgusting that I haven't made any seasoned Linux users sick. :wink:

---

### Post by Tim Sharitt on 2008-12-14
My guess is that wget can't parse xml files. You may need to parse the file via some other tool (not necessarily specific to xml, sed or something similar may work fine) and feed the results to wget.

---

### Post by calrogman on 2008-12-14
> **Tim Sharitt said:**
> My guess is that wget can't parse xml files. You may need to parse the file via some other tool (not necessarily specific to xml, sed or something similar may work fine) and feed the results to wget.

Ok, I'll try that, wish me luck!:D

Edit : Actually, I've had a look at the man-pages for sed, my head hurts, and I have no idea what to do.

Anyway, would you mind maybe giving a quick example of how to filter out everything except for links to .mp3 files? I'd appreciate it.

:oops:

---

### Post by dannytatom on 2008-12-14
Keep us updated.  I'd like to use this if you get it working. :)

---

### Post by calrogman on 2008-12-14
> **dannytatom said:**
> Keep us updated.  I'd like to use this if you get it working. :)

I hope you do, I'll probably write a script that asks for some information about the feed and then creates an update script, that does everything for you!

I can see how lots of people could find it useful, and it's always nice to contribute!


Gotta go to bed now, get some sleep.  I'll be back on about midday GMT to see all tyour lovely contribution, which I'm sure will be very useful.
:p

---

### Post by unutbu on 2008-12-14
Save the following script as fetch_mills.py:
[PHP]#!/usr/bin/env python
from urllib2 import urlopen
import re
import os
url='http://downloads.bbc.co.uk/podcasts/radio1/mills/rss.xml'
content=urlopen(url).read()
contents=content.split()
pat=re.compile('(http://downloads.bbc.co.uk/podcasts/radio1/mills/\S+?\.mp3)')
groups=(pat.search(line) for line in content.split())
tuples=(g.groups() for g in groups if g)
for mp3, in tuples:
    cmd='wget %s'%mp3
    print cmd
    os.system(cmd)
[/PHP]
Put it in your bin directory:```

mkdir ~/bin
mv fetch_mills.py ~/bin
```

Make it executable:```

chmod +x fetch_mills.py

```
Run it like this:```

cd ~/Music/Scott-Mills-Podcast
fetch_mills.py
```

---

### Post by calrogman on 2008-12-15
Aww... you went and ruined it, I was writing the bash script, not only to download some mp3s through an RSS feed, but also as an exercise I set myself to become more comfortable with bash scripting, ah well, thank you very much for your contribution! It's appreciated.

I would still like to finish this bash script, just as an exercise.  I'm not going to be compiling Gentoo from a stage1 tarball (I really want to btw), if I don't get used to using bash!

---

### Post by unutbu on 2008-12-15
calrogman, sorry for crashing the party. Your question was interesting, so I couldn't help myself. 

Good luck with learning bash and installing Gentoo!

---

### Post by calrogman on 2008-12-15
> **unutbu said:**
> calrogman, sorry for crashing the party. Your question was interesting, so I couldn't help myself. 

Good luck with learning bash and installing Gentoo!

It's ok, I was joking about ruining it, it's certainly easier in python, it's just that bash is what I'm trying to learn.  It's definitely alot more elegant than batch scripting, which is what is used in Windows, if you didn't know.

And I won't be installing Gentoo for a *VERY* long time, I am only 14, and having been brought up using Windows it'll be a challenge.

---

### Post by calrogman on 2008-12-19
Still haven't got this working, if anyone who knows how to use sed to parse multiple links from a XML file (it would be useful if the solution worked for more than one link per line, but also worked on files with multiple lines) help would be greatly appreciated!

---

### Post by darkshadow on 2009-01-30
I am having roughly the same problem, I just finished mirroring [www.skins.be](www.skins.be) (yikes over 27GB) and would like to keep it updated automatically from rss and need to know how to parse all links from this file [http://www.skins.be/feeds/en/skins.xml](http://www.skins.be/feeds/en/skins.xml) and run them in this wget command.


wget $URL --no-clobber --directory-prefix=Downloaded/ --exclude-directories=/tags/,/babe-chart/,/wallpaper-chart/,/notification-chart/,/current-chart/,/todays-favorites/,/hall-of-fame/,/members/,/*/uploads/,/*/lyrics/,/*/biography/,/*/related-tags/,/page/,/user-uploads/,/babes/,/botw/,/contact/,/help/,/imagehoster/,/linksharing/,/poll/,/recommend/,/suggest-babe/,/toolbar/,/top-tags/,/webmaster/,/joes-example-page/ --span-hosts --recursive --level=1 --page-requisites --accept jpg,html --domains=www.skins.be,wallpapers.skins.be,wallpaper.skins.be --user-agent="Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.3) Gecko/2008092510 Ubuntu/8.04 (hardy) Firefox/3.0.3" --header="Cookie: lang_key=en; fv_tstamp=20081011192340"

---

### Post by darkshadow on 2009-01-31
Ignore mine I figured it out.

I used this command and got a list I can use with "wget -i"

grep link skins.xml | sed s@"<link>"@@ | sed s@"</link>"@@ | sed [email]s@"http://www.skins.be[/email]/"@@ | sed 's@^[ \t]*@@' | grep http - &> out

---

