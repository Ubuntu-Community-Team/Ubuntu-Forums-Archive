---
title: "Deluge website down (domain expired)!"
date: 2009-11-10
forum: Desktop Environments
---

### Post by hamishau on 2009-11-10
Hi everyone

The Deluge website is currently, down. It looks like the domain name has expired and needs to be renewed (deluge-torrent.org).

Does anyone at Canonical or in the Ubuntu community know how to get in touch with the project organisers and get it renewed?

Thanks,
Hamish
Melbourne, Aus

---

### Post by kellemes on 2009-11-10
Seems to be fixed.

---

### Post by nexoncore on 2009-11-10
I beg to differ, its not working for me either 

"
         Sorry! We could not find [www.deluge-torrent.org](www.deluge-torrent.org)       
                It may be unavailable or may not exist.

"

---

### Post by kellemes on 2009-11-10
Again.. it is working fine for me.
Although sub-links from the menu are broken.

---

### Post by lovinglinux on 2009-11-10
> **kellemes said:**
> Again.. it is working fine for me.
Although sub-links from the menu are broken.

I guess some parts of the site are in your cache, because nothing is working for me.

---

### Post by b0rkster on 2009-11-11
Aargh! and i was going to install deluge today! Any updates? :???:

---

### Post by lovinglinux on 2009-11-11
> **b0rkster said:**
> Aargh! and i was going to install deluge today! Any updates? :???:

```
sudo apt-get install deluge
```

or

[click here](apt:deluge)

---

### Post by durand on 2009-11-11
The website doesn't work here either :(

---

### Post by sisco311 on 2009-11-11
Deluge is in the universe repository. 

The latest version (1.2.0~rc3-2 for karmic,jaunty and hardy and 1.1.9+dfsg-2 for intrepid) is available from the PPA repository:

[https://launchpad.net/~deluge-team/+archive/ppa]("https://launchpad.net/~deluge-team/+archive/ppa")

---

### Post by xpod on 2009-11-13
> **sisco311 said:**
> Deluge is in the universe repository. 

The latest version (1.2.0~rc3-2 for karmic,jaunty and hardy and 1.1.9+dfsg-2 for intrepid) is available from the PPA repository:

[https://launchpad.net/~deluge-team/+archive/ppa]("https://launchpad.net/~deluge-team/+archive/ppa")


The sites still down though and anybody using the default Blocklist settings will need to change them ...for now.

---

### Post by silverdulcet on 2009-11-13
According to the topic on the official IRC channel at:
irc.freenode.net
#deluge

The site has moved to: [http://deluge-torrent.info/]("http://deluge-torrent.info/")

---

### Post by kbtarl on 2009-11-13
I can not get deluge to show open port even though transmission shows same port to be open. Any Help?

---

### Post by JBAlaska on 2009-11-13
If anyone needs a url to a Level 1 blocklist (From Bluetack), this one from ```
http://iblocklist.com
``` works just fine.
```
http://list.iblocklist.com/?list=bt_level1
```

---

### Post by lovinglinux on 2009-11-13
> **kbtarl said:**
> I can not get deluge to show open port even though transmission shows same port to be open. Any Help?

That's because Deluge web site is down. The port testing feature of Deluge needs to connect to the site IP to test port. Since the site is down and thus not responding, Deluge thinks the port is closed, when in fact is not.

There is a better method of testing the port in the troubleshooting section of the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923).

---

### Post by brookie on 2009-11-13
Just another note, 

If you can't add the blocklist above because the buttons are grayed out in deluge blocklist preferences, 'check download import' & 'force download import'. 

Just go to your home folder and hit 'ctrl h' to fiew hidden folders. Go to /home/your_home_dir/.config/deluge, and rename blocklist.conf to back it up. Then close deluge, go back to block lists, and enter your new block list. The 'force download import' button should work now. 

BTW, the block list above is not blocking any sites, so let me know if you find one that works. The blocklist downloads but shows blocking 0% on the bottom panel of deluge. 

Hopefully the deluge site will be back up soon. 

Cheers, 
brook

ps i got it to work following another users advice on [this]("http://iblocklist.com/list.php?list=bt_level1") page. just search for deluge and you can check out how the prefs were set up to work. ;)

---

### Post by JBAlaska on 2009-11-13
> **brookie said:**
> Just another note, 

If you can't add the blocklist above because the buttons are grayed out in deluge blocklist preferences, 'check download import' & 'force download import'. 

Just go to your home folder and hit 'ctrl h' to fiew hidden folders. Go to /home/your_home_dir/.config/deluge, and rename blocklist.conf to back it up. Then close deluge, go back to block lists, and enter your new block list. The 'force download import' button should work now. 

BTW, the block list above is not blocking any sites, so let me know if you find one that works. The blocklist downloads but shows blocking 0% on the bottom panel of deluge. 

Hopefully the deluge site will be back up soon. 

Cheers, 
brook

ps i got it to work following another users advice on [this]("http://iblocklist.com/list.php?list=bt_level1") page. just search for deluge and you can check out how the prefs were set up to work. ;)

Restarting Deluge also refreshes the blocklist. ```
http://list.iblocklist.com/?list=bt_level1
``` is blocking 224231 ip's on my Deluge v. 1.1.9

---

### Post by Ubulindy on 2009-11-13
Site IS still down as of right now, as well as the blocklist wont download. In some cases you wont be able to re-install the blocklist without having first gone to: /.config/deluge   and delete both the  blocklist and the conf files. Sometimes it wont let you re-download the blocklist if the file already exists. Other than that, as far as grabbing Deluge from the repos, that may not work either if the server is down. I have heard nothing about when this issue will be fixed. Wish I knew.

---

### Post by lovinglinux on 2009-11-13
> **Ubulindy said:**
> Site IS still down as of right now, as well as the blocklist wont download. In some cases you wont be able to re-install the blocklist without having first gone to: /.config/deluge   and delete both the  blocklist and the conf files. Sometimes it wont let you re-download the blocklist if the file already exists. Other than that, as far as grabbing Deluge from the repos, that may not work either if the server is down. I have heard nothing about when this issue will be fixed. Wish I knew.

Blocklist download and installing deluge from the repos are not related to the fact that Deluge's web site is down, although the feature that check if the port is opened should not work without the site.

---

### Post by Ubulindy on 2009-11-13
So, ok then, Im on the new page so to speak for Deluge:    [http://deluge-torrent.info/](http://deluge-torrent.info/)
Do you know what any of the new blocklist URS are, and if so, link me to the page please?? None of the previous URLs are good being the site wont load. Thanks!  :-D I found a link on another forum, that didnt download and install either.

---

### Post by lovinglinux on 2009-11-13
> **Ubulindy said:**
> Do you know what any of the new blocklist URS are, and if so, link me to the page please?? None of the previous URLs are good being the site wont load.

The blocklist is not provided by Deluge, but [iBlocklist](http://iblocklist.com/lists.php) or [Bluetack](http://www.bluetack.co.uk/forums/). 

Apparently Bluetack changed they way blocklists are downloaded recently, requiring user authentication first. I'm not sure if this is true, but I recommend using iBlocklist instead.

Another option would be downloading the list you want manually, extracting it somewhere and using the local path in Deluge. This is the way I always configured Deluge, because I didn't use a single list, but several lists merged together.

You can automate the list download with with a script:

```
#!/bin/bash

wget --timeout=30 --tries=3 --no-directories -O $HOME/bt-level1.gz http://list.iblocklist.com/?list=bt_level1

aunpack --extract-to=$HOME/bt-level1.p2p $HOME/bt-level1.gz
```

Unfortunately I can't test deluge's blocklist plugin right now, because I switched to Ktorrent, which is very good too.

---

### Post by kbtarl on 2009-11-13
Mine shows 0 ip block. Does it download the list and unzip it? I saw it download but how do I know it put it in correctly?

I looked on Iblock but didn't see any way to "search" deluge. Could you cut and past more directions?

---

### Post by lovinglinux on 2009-11-13
> **kbtarl said:**
> Mine shows 0 ip block. Does it download the list and unzip it?

Yes, it unzips the file, although I don't think is necessary. Nevertheless, you need to install [atool](apt:atool) to use the unzip command from my script.

> **kbtarl said:**
> I saw it download but how do I know it put it in correctly

You need to put the path to the unzipped file into the blocklist plugin option.

> **kbtarl said:**
> I looked on Iblock but didn't see any way to "search" deluge. Could you cut and past more directions?

You won't find anything related to deluge there. IBlocklist publishes a series of IP blocklists. You need to choose which list you want and copy the url into the BitTorrent client blocklist configuration or download it manually. The script I have provided will download the same list that is the default in Deluge.

---

### Post by Ubulindy on 2009-11-13
Well, mine says downloading the list, the bar moves across, then it says installing the list, and basically does nothing from there. No matter what format of the file, which URL I seem to use for the blocklist, I get same results. Doesnt matter . And the addresses listed in Wiki are no good either:
    1.  [http://dev.deluge-torrent.org/wiki/BlocklistPlugin](http://dev.deluge-torrent.org/wiki/BlocklistPlugin) ( page doesnt exist )
    2.  [http://www.deluge-torrent.org/blocklist/pipfilter.dat.gz](http://www.deluge-torrent.org/blocklist/pipfilter.dat.gz) (Emule)
    3.  [http://www.deluge-torrent.org/blocklist/nipfilter.dat.gz](http://www.deluge-torrent.org/blocklist/nipfilter.dat.gz) (Emule) 
Neither of those successfully download or install
Im googling as we speak.
    [http://dev.deluge-torrent.info/ticket/1059](http://dev.deluge-torrent.info/ticket/1059)
These do not load or install either:
    [http://iblocklist.com/lists.php](http://iblocklist.com/lists.php)

Dont know what to do

---

### Post by lovinglinux on 2009-11-13
> **Ubulindy said:**
> Well, mine says downloading the list, the bar moves across, then it says installing the list, and basically does nothing from there. No matter what format of the file, which URL I seem to use for the blocklist, I get same results. Doesnt matter . And the addresses listed in Wiki are no good either:
    1.  [http://dev.deluge-torrent.org/wiki/BlocklistPlugin](http://dev.deluge-torrent.org/wiki/BlocklistPlugin) ( page doesnt exist )
    2.  [http://www.deluge-torrent.org/blocklist/pipfilter.dat.gz](http://www.deluge-torrent.org/blocklist/pipfilter.dat.gz) (Emule)
    3.  [http://www.deluge-torrent.org/blocklist/nipfilter.dat.gz](http://www.deluge-torrent.org/blocklist/nipfilter.dat.gz) (Emule) 
Neither of those successfully download or install
Im googling as we speak.
    [http://dev.deluge-torrent.info/ticket/1059](http://dev.deluge-torrent.info/ticket/1059)
These do not load or install either:
    [http://iblocklist.com/lists.php](http://iblocklist.com/lists.php)

Dont know what to do

That's the main reason I switched to Ktorrent. I like Deluge a lot and it was my default BitTorrent client for a long time, but Ktorrent works perfectly for me now, including the blocklist plugin and UPnP, that I couldn't make work properly on Deluge.

BTW, those links you are trying to reach are on the old Deluge domain.

---

### Post by Ubulindy on 2009-11-13
Well, if you have a link to the site handy Id sure love to have it, because I did go to the new domain I think, and I didnt see any info on there that points to any new URLs for the blocklist.
And yes, Ive used kTorrent.. does work just fine, I just preffered Deluge.  Links please?

---

### Post by lovinglinux on 2009-11-13
> **Ubulindy said:**
> Well, if you have a link to the site handy Id sure love to have it, because I did go to the new domain I think, and I didnt see any info on there that points to any new URLs for the blocklist.
And yes, Ive used kTorrent.. does work just fine, I just preffered Deluge.  Links please?

Go back to posts #13, #16 or #20.

---

### Post by Ubulindy on 2009-11-13
Thanks for all your help. I did just manage to find a Bluetack URL  :-P  And it worked and looaded

[http://bluetack.co.uk/config/level1.zip](http://bluetack.co.uk/config/level1.zip)  ( SafePeer/zipped )

---

### Post by kbtarl on 2009-11-13
YEA!   Worked great!  Thanks for the help. Is that the only one we need? If I found another and had it download, would it just add to that list or replace it?

---

### Post by Ubulindy on 2009-11-13
> **kbtarl said:**
> YEA!   Worked great!  Thanks for the help. Is that the only one we need? If I found another and had it download, would it just add to that list or replace it?
It would replace it, and yes, that should be the only one that we'll need. It should update on its own according to how the site that maintains the list updates.  Sweee, Im so glad I got the thing working, lol. Was a thorn in my side.

---

### Post by quixotic-cynic on 2009-11-14
This will now work: [deluge-torrent.info/blocklist/nipfilter.dat.gz]("deluge-torrent.info/blocklist/nipfilter.dat.gz")

It would have been nice if they had managed the transition somewhat more smoothly (if it was intentional)...

---

### Post by Ubulindy on 2009-11-14
Thanks for the additional info... Ive now started a folder with the lists, lol

---

### Post by andrewabc on 2009-11-14
Off topic, but found this thread because I wanted to know why website down (has been answered).

With 1.2.0RCx, I have disk cache. I have lots of ram available, so I've increased settings.
Disk cache GUI only became available in 1.2.0RC1
> Add a Cache preferences page to adjust cache settings and examine cache status 

Ubuntu installed to SSD, and torrents going to ntfs hard drive partition. Wanted to decrease writing small amounts of data all the time.

Anyone tinkered with settings to get optimal stuff?

For me settings currently:
Cache size: 5120
Cache expiry: 120

current status (size):
Cache size: 5117
Read cache size: 5043

I presume cache expiry flushes cache in that time whether or not it has reached full cache? I tried 51200 cache size, but cache never got that big (I presume because expiry flushed it out before it could ever get that big). But according to free memory, I was getting low on 'ram' because of large cache usage (3gb total, normally 1.5 gb available), even though deluge wasn't reporting much cache used.

---

### Post by bark50 on 2009-11-15
> **Ubulindy said:**
> Thanks for all your help. I did just manage to find a Bluetack URL  :-P  And it worked and looaded

[http://bluetack.co.uk/config/level1.zip](http://bluetack.co.uk/config/level1.zip)  ( SafePeer/zipped )

Thanks!

---

### Post by 2hot6ft2 on 2009-11-19
I didn't scan thru all the posts but I just installed Ubuntu Ultimate Edition 2.4 which is Ubuntu 9.10 and installed Deluge. The blocklist wouldn't download with the URL
[http://deluge-torrent.com/blocklist/nipfilter.dat.gz](http://deluge-torrent.com/blocklist/nipfilter.dat.gz)
in the URL box but it worked just fine after changing the .com to .info making it
[http://deluge-torrent.info/blocklist/nipfilter.dat.gz](http://deluge-torrent.info/blocklist/nipfilter.dat.gz)

Screen shot attached of how it looks if you're not sure what I mean. From the main window in Deluge go to Edit > Preferences > Blocklist

---

### Post by brookie on 2009-11-19
these guys are still kickin' 
just having some site issues
you can find out more on their [forum]("http://forum.deluge-torrent.info/viewtopic.php?f=10&t=25815&sid=b0b874015984ccf511ea09d3dd68c4aa")
;)
__

---

### Post by sysghost on 2011-02-05
As of today, deluge-torrent.org AND deluge-torrent.info are down/parked.
The .org seems completely down, and it looks like the .info one are parked.
Google seems to be EXTREMLY slow on this "topic", no information about this at all.

Anywhere else to find any information about this?... or did the deluge team put the last nail in the coffin?

---

### Post by silverdulcet on 2011-02-05
> **sysghost said:**
> As of today, deluge-torrent.org AND deluge-torrent.info are down/parked.
The .org seems completely down, and it looks like the .info one are parked.
Google seems to be EXTREMLY slow on this "topic", no information about this at all.

Anywhere else to find any information about this?... or did the deluge team put the last nail in the coffin?

I'm not sure about earlier, but it deluge-torrent.org works fine for me currently. Perhaps a routing problem between you and their host? You can also get in touch with the developers on via IRC chat in #deluge on irc.freenode.net

---

