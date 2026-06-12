---
title: "Rubicon X install"
date: 2007-01-17
forum: Gaming &amp; Leisure
---

### Post by Duncan_Idaho on 2007-01-17
hi!
i found this game called rubicon X
so I compiled and installed the alephone engine but I dont know what to do with the data files :S
where should they go in?
and where should I put the marathon files to?

---

### Post by bob301 on 2007-03-10
I could use soem help as well. I am using Feisty Fawn.

I have downloaded the Rubicon X files from here:
[http://www.marathonrubicon.com/](http://www.marathonrubicon.com/)

I also downloaded and installed the Aleph One engine:
[http://superb-west.dl.sourceforge.net/sourceforge/marathon/AlephOne-20060701-nolibs.tar.bz2](http://superb-west.dl.sourceforge.net/sourceforge/marathon/AlephOne-20060701-nolibs.tar.bz2)

I installed all the necessary dependencies as explained here:
[http://ubuntuforums.org/showthread.php?t=261577&page=2&highlight=marathon](http://ubuntuforums.org/showthread.php?t=261577&page=2&highlight=marathon)

And...that's where I am stalled. I do not have the files in the right place, when I try to run Aleph One I get the error below:

FATAL: Please be sure the files 'Map', 'Shapes', 'Images' and 'Sounds' are correctly installed and try again. (error -1)

I am not sure how to get RubiconX to run. Can someone point me in the right direction?

---

### Post by Perfect Storm on 2007-03-11
extract the linux client into the data folder, open the terminal and **cd** to the data folder now execute the linux client file, you may chmod it first.

---

### Post by Duncan_Idaho on 2007-03-11
thank to the links bob301 posted I compilled alephone
but I got the same error he gets :confused: 
plus I dont understand artificial inteligence's instructions :confused:

---

### Post by sbabstock on 2007-03-27
right, after a bit of searching, and just so I can leave this one to posterity for those who have not managed to find this out themselves.

I am a relative linux/ubuntu noob, so please forgive me if I say anything that's blindingly obvious to anyone who knows a lot more than me.

once you have configured, maked and install alephone, you should have an alephone folder in usr/local/share/Alephone. You should also be able to find the executable in usr/local/bin/ . Everything I've read seems to say that you should move the Alephone executable file into wherever the RubiconX files are, but I had the same error as above. Thus, after much searching and changing of search terms, I found this out... *it's the other way around*. 

I.e. you need to move the data files for RubiconX to the folder /usr/local/share/Alephone . And then put the executable there as well.

The easiest way I found to do that was to start up a terminal from wherever you untarred the RubiconX data files and do - cp -R * /usr/local/share/AlephOne  -- once that has finished, simply copy the executable Alephone from /usr/local/bin and put it in the /usr/local/share/Alephone folder as well.

You may need to sudo the cp... I did.

This seems to have solved the problem and now I can play from the first folder as well, so it would seem that it's a problem with my paths, but I wouldn't have a clue how to work that one out. HTH and works for anyone else trying out this game.

---

### Post by Perfect Storm on 2007-03-27
I just made a howto for Rubicon X: [http://gaming.gwos.org/e107_plugins/content/content.php?content.59](http://gaming.gwos.org/e107_plugins/content/content.php?content.59)

---

### Post by KIAaze on 2007-05-05
I followed the instructions from the page you gave and everything executed without any errors (except the name of the files which has changed because of the version), however I get the following error message when trying to run the game:
> > alephone 
Aleph One SDL linux-gnu i686 May  5 2007
[http://marathon.sourceforge.net/](http://marathon.sourceforge.net/)

Original code by Bungie Software <http://www.bungie.com/>
Additional work by Loren Petrich, Chris Pruett, Rhys Hill et al.
TCP/IP networking by Woody Zenfell
Expat XML library by James Clark
SDL port by Christian Bauer <Christian.Bauer@uni-mainz.de>

This is free software with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
For details, see the file COPYING.

Built with network play enabled.
FATAL: Please be sure the files 'Map', 'Shapes', 'Images' and 'Sounds' are correctly installed and try again. (error -1)


---

### Post by Perfect Storm on 2007-05-06
There was an error in the installation guide, the guide have been fixed and tested on feisty x86.

There error was;
mv Rubicon*/ rubiconX

it should have been

mv Rubicon*/* rubiconX

---

### Post by KIAaze on 2007-05-07
Thanks. :)
Well, that looks like an error I should have been able to figure out... ^^

---

### Post by go_beep_yourself on 2008-09-17
> **Artificial Intelligence said:**
> I just made a howto for Rubicon X: [http://gaming.gwos.org/e107_plugins/content/content.php?content.59](http://gaming.gwos.org/e107_plugins/content/content.php?content.59)

I just tried your link and it's not working. Page not found.

---

### Post by Perfect Storm on 2008-09-17
It's old - we have changed pages since then. Here's another one I made long ago, I don't know if it works - you properly needs to adjust it a bit;

[http://gaming.gwos.org/doku.php/guides:32bit:alephone#alephone](http://gaming.gwos.org/doku.php/guides:32bit:alephone#alephone)

---

### Post by Kirkhelek on 2010-11-03
To install Rubicon X you can do theses steps on the Troubbleshooting Linux > Multiple Scenarios:
[http://traxus.bungie.org/index.php/AlephOne:Install_Guide](http://traxus.bungie.org/index.php/AlephOne:Install_Guide)

The bash script have a fail, the correct way to run fine is declarating the PREFIX variable on it:
```

#!/bin/sh
PREFIX=/usr/local;
export ALEPHONE_DATA=*$PREFIX*/share/rubiconx:*$PREFIX*/share/AlephOne;[I]
exec $PREFIX[/I]/bin/alephone "$@";

```

I know it's an old post, but there aren't enought information on the web.

Hi to all.

---

