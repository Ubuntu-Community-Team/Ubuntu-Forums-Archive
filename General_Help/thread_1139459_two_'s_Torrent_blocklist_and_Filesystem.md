---
title: "two ?'s: Torrent blocklist and Filesystem"
date: 2009-04-27
forum: General Help
---

### Post by rock4christ on 2009-04-27
1. im trying to find a torrent program for ubuntu that supports blocklists (like ipfilter.dat in utorrent) and preferably allows easy updating and merging of multiple blocklists(using blocklist manager from bluetack in windows)

2. what filesystem would you suggest for easiest use in both ubuntu and windows? last i heard ubuntu has some hiccups w/ ntfs and windows cant recognize ext at all.

---

### Post by Yashiro on 2009-04-27
Transmission supports blocklists.

NTFS is fine to use as a shared drive between Linux and Windows.

---

### Post by rock4christ on 2009-04-27
ok. so ntfs doesn't have issues in ubuntu? good to know.

is there any way to add to the transmission blocklist? wanna be as safe as I can.

also, will I need to edit max half open tcp connections or anything like I did in windows?

---

### Post by evermooingcow on 2009-04-27
I believe the half open connections limitation is an artificial one built into Windows only to limit the spread of viruses.

---

### Post by Yashiro on 2009-04-27
Yes, use google or read the transmission forums.

No you wont have to tweak stupid stuff like in Windows.

---

### Post by rock4christ on 2009-04-27
OK. added a few more blocklists. is there a way I could get them to auto update? possibly a script to download the gz files and extract to ./transmission/blocklist/

---

### Post by rock4christ on 2009-04-27
ok.... which folder is the one i put the blocklist files in. i tried  ./transmission/blocklist/ in my home folder, but that hasn't changed anything. clicked update too.

---

### Post by Psychopump on 2009-04-27
IMHO Transmission is a horrible program with a horrible interface.
Using it feels like assembling something with small parts while wearing boxing gloves.

I highly recommend Deluge.
It looks and feels a lot like uTorrent, and even has some more useful features, like changing the location of a download during the transfer.

---

### Post by rock4christ on 2009-04-27
anyway I could add more than one block url in deluge?

or set it to just pull from the ipfilter.dat in my windows system?

---

### Post by Psychopump on 2009-04-27
> **rock4christ said:**
> anyway I could add more than one block url in deluge?

or set it to just pull from the ipfilter.dat in my windows system?


Here are 2 links that may help you:

[http://forum.deluge-torrent.org/viewtopic.php?f=9&t=2415](http://forum.deluge-torrent.org/viewtopic.php?f=9&t=2415)

[http://ubuntuforums.org/showthread.php?t=981325](http://ubuntuforums.org/showthread.php?t=981325)

---

### Post by rock4christ on 2009-04-27
im thinking I'll just stick w/ transmission.


anyone know how to setup a script that goes to
[http://list.iblocklist.com/?list=bt_bogon](http://list.iblocklist.com/?list=bt_bogon)
[http://list.iblocklist.com/?list=bt_level1](http://list.iblocklist.com/?list=bt_level1)
[http://list.iblocklist.com/?list=bt_level3](http://list.iblocklist.com/?list=bt_level3)
[http://list.iblocklist.com/?list=bt_rangetest](http://list.iblocklist.com/?list=bt_rangetest)

downloads the .gz files, and extracts the txt files inside to

/home/corey/.config/transmission/blocklists

---

### Post by Psychopump on 2009-04-27
If you can live with that clunky GUI and the lack of control over your torrents, why not?

I for one think Deluge is far superior to Transmission.

---

### Post by mb_webguy on 2009-04-27
If you want a an IP blocker, why not get something that will apply to all of your Internet activity, and not just your torrents?

I use [IPList]("http://iplist.sourceforge.net/").  It applies the Bluetack blocklists to iptables.  The GUI, IPBlock, is simple and straightforward.  You can get it through [this PPA]("https://launchpad.net/~ssakar/+archive/ppa").  I suggest using the level1, ads-trackers-and-bad-pr0n, spyware, bogon, dshield, hijacked, and trojan lists.  Click the Add Url button on the Lists tab to select them from a list.

---

### Post by rock4christ on 2009-04-27
is there a allow http option. I know there are times where I cant access some web pages if http is blocked w/ peer guardian.

---

### Post by mb_webguy on 2009-04-27
Not specifically, but there's a place where you can specify ports to ignore, so all you'd have to do is put 80 and 8080 in that box.  Of course, using the blocklists I suggested, I haven't had any problems whatsoever surfing the web, and I haven't bothered messing with any of the other settings.

---

### Post by rock4christ on 2009-04-28
is there a way I can make sure iplist is working?

---

### Post by mb_webguy on 2009-04-28
Well, first make sure you've clicked the Enable button in IPBlock to, um... enable it.  Now if you look at the Log tab, you can see all of the connections it's blocking.  This will probably be pretty quiet until you start up Transmission and start downloading a torrent.  

IPBlock is just a configuration utility, so you don't have to keep it open for IPList to do it's job.  However, you'll probably want to check Autostart in the Settings tab to make sure IPList starts every time you log in.  Otherwise, you'll have to manually start IPBlock to start IPList.

---

### Post by rock4christ on 2009-04-28
seems like a good prog, but it has been sitting at 'updating' for 15 min and is currently disabled.

---

### Post by rock4christ on 2009-04-28
im getting 'cant find [one item in my list]' and 'failed to start, cleaning up'

---

### Post by mb_webguy on 2009-04-28
Hrm... it usually doesn't take more than a minute or so for it to update for me, but I just tried to update since your last post, and it took a bit longer than normal.  What list can't it find for you?

Also, keep in mind that the Enable/Disable toggle button shows what it's *not*.  So if it says "Disable" at the top, it's currently enabled.

---

### Post by rock4christ on 2009-04-28
it said disabled in the bottom window panel. and it is actually a couple it isn't finding. rangetest, edu, and level3

---

### Post by mb_webguy on 2009-04-28
> **rock4christ said:**
> it said disabled in the bottom window panel. and it is actually a couple it isn't finding. rangetest, edu, and level3

Oooohh...  You don't want those anyway.  The level3 list is the super-paranoid "I wear foil hats so the government satellites can't read my mind" blocklist.  The level1 list blocks the bad guys, the level2 list blocks corporations and proxies, and the level3 list basically blocks *everyone*.

I also don't see the point in using the edu list, especially if you torrent.  That's going to block students, who make up a significant portion of the torrent-using population.

I'm not exactly sure what the rangetest list is, but since it only shows up on the Bluetack "Paranoid" superset, I'd say it isn't necessary unless you're wanted by a major world government.

You can see what the different lists contain on the [Bluetack site]("http://www.bluetack.co.uk/forums/index.php?autocom=faq&CODE=02&qid=17").  I personally use the level1, ads-trackers-and-bad-pron, spyware, bogon, dshield, hijacked, and trojan lists, and feel pretty comfortable.  I wouldn't add the level2 list without making an exception for web browsing, but otherwise it seems alright.

---

### Post by rock4christ on 2009-04-28
now im getting error: no running iplist instance found

---

### Post by rock4christ on 2009-04-28
I managed to get it running by deleting the gz files it had, and manually adding ones from iblocklist.com

still cant get it to update tho

---

### Post by uljanow on 2009-04-28
Only **level1.gz, ads-trackers-and-bad-pr0n.gz, edu.gz, spyware.gz and bogon.gz** are available from a mirror which is more reliable and faster than the servers bluetack uses.

---

### Post by rock4christ on 2009-04-28
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            mark match 0xffff 
INPUT_QUEUE  all  --  anywhere             anywhere            state NEW mark match !0xfffe 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            mark match 0xffff 
FORWARD_QUEUE  all  --  anywhere             anywhere            state NEW mark match !0xfffe 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
BLOCK_MATCH  all  --  anywhere             anywhere            mark match 0xffff 
OUTPUT_QUEUE  all  --  anywhere             anywhere            state NEW mark match !0xfffe 

Chain ALLOW_MATCH (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain BLOCK_MATCH (3 references)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain FORWARD_QUEUE (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 255

Chain INPUT_QUEUE (1 references)
target     prot opt source               destination         
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 253

Chain OUTPUT_QUEUE (1 references)
target     prot opt source               destination         
RETURN     tcp  --  anywhere             anywhere            tcp dpt:www 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:https 
NFQUEUE    all  --  anywhere             anywhere            NFQUEUE num 254


that is the output of sudo iptables -L

does that mean ipblock is working?

---

### Post by freonchill on 2009-04-28
another vote for deluge over transmission (transmission is like default bit torrent client, no features, options, etc)

if deluge still isnt to your liking, then you can use utorrent via wine

---

### Post by rock4christ on 2009-04-28
> **freonchill said:**
> another vote for deluge over transmission (transmission is like default bit torrent client, no features, options, etc)

if deluge still isnt to your liking, then you can use utorrent via wine

does the default nipfilter work well?

anyway i could test both deluge and ipblock are working?

---

### Post by mb_webguy on 2009-04-28
Based on your iptables listing, I'd say that yes, IPList is working.

And it would be a bit difficult to see if *both* IPList and the Deluge blocklist are working.  You can see if IPList is working (by looking Log in IPBlock).  But I don't think Deluge keeps a log of blocked connections, so I don't know how you'd be able to verify it's working.  However, I believe you should be able to use the blocklist used by Deluge in IPList.  So you could actually *just* use IPList to block undesirable IPs.

EDIT:  While I couldn't get IPBlock to add the list used by Deluge directly, I did a bit of research and it turns out that the nipfilter list used by Deluge is simply a combination of the Bad Peers, Bogon, D-Shield, Hijacked, IANA Multicast, IANA Private, IANA Reserved, Level 1 [Anti-P2P], Level 2 [Corporate], Microsoft, and Non Lan lists.  If you have these enabled in IPBlock, using the Deluge blocklist is redundant and serves no purpose whatsoever.

---

### Post by rock4christ on 2009-04-28
I still cant update ipblock. it just sits at updating.

---

### Post by mb_webguy on 2009-04-28
That's odd...  Try completely removing it in Synaptic, then reinstalling.  Then try enabling it without messing with the lists first.  I've installed IPBlock/IPList on quite a few computers without any problems.

---

### Post by rock4christ on 2009-04-29
I got it semiworking. had to use badpeers.gz instead of templist(it was renamed) and I had to manually put the badpeers.gz file in /var/cache/iplist/

---

### Post by mb_webguy on 2009-04-29
Ah.  I know the reason for that (after a quick Google).  The actual blocklist has been renamed "badpeers.gz", even though the URL is the same.  All you need to do is edit the ipblock.lists file with the command "sudo gedit /etc/ipblock.lists".  Look for the following lines:```
# malicious p2p peers
templist.gz		http://www.bluetack.co.uk/config/templist.gz

```
Change the "templist.gz" at the beginning of the line with "badpeers.gz", then save and exit.

Now in IPBlock you'll see badpeers in the "Add URL" list.

---

### Post by rock4christ on 2009-04-29
actually, I just added [http://www.bluetack.co.uk/config/badpeers.gz](http://www.bluetack.co.uk/config/badpeers.gz) to the list

---

### Post by mb_webguy on 2009-04-29
> **rock4christ said:**
> actually, I just added [http://www.bluetack.co.uk/config/badpeers.gz](http://www.bluetack.co.uk/config/badpeers.gz) to the list
That'll work too, but you'll still have testlist in your list.  If you forget about it try to add it later, you'll get the same problems.

---

### Post by rock4christ on 2009-05-01
slightly off topic, but what are the IANA Multicast, IANA Private, and IANA Reserved lists for?

---

### Post by mb_webguy on 2009-05-01
> **rock4christ said:**
> slightly off topic, but what are the IANA Multicast, IANA Private, and IANA Reserved lists for?

The multicast list blocks multicast IPs, which are used to send to multiple computers rather than a specific computer.  You may want to block multicast IP addresses since there's no way to identify where the data is really coming from or going to.

The private list is for IP addresses used by private networks.  You probably don't want to use this if you're on a local network, since it will keep you from connecting to other computers on the network.  So if you enable this block list and suddenly can't open a shared folder on another computer, that's probably why.

The reserved list is for IP addresses reserved by the IANA for various reasons, and shouldn't be currently in use.

---

### Post by uriel1998 on 2010-11-18
> **rock4christ said:**
> im thinking I'll just stick w/ transmission.
anyone know how to setup a script that goes to
[http://list.iblocklist.com/?list=bt_bogon](http://list.iblocklist.com/?list=bt_bogon)
[http://list.iblocklist.com/?list=bt_level1](http://list.iblocklist.com/?list=bt_level1)
[http://list.iblocklist.com/?list=bt_level3](http://list.iblocklist.com/?list=bt_level3)
[http://list.iblocklist.com/?list=bt_rangetest](http://list.iblocklist.com/?list=bt_rangetest)



It's easier than that with Transmission 2.12 (11412); you can specify the URL to the blocklist.  The blocklist that used to be downloaded is:

[http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)

There are more paranoid blocklists at Bluetack's website (you want the eMule version with the .gz extension).  These have the blocklists you're looking for.  Each is updated weekly.

Normal IP Filter:  [http://www.bluetack.co.uk/config/nipfilter.dat.gz](http://www.bluetack.co.uk/config/nipfilter.dat.gz)

Paranoid:  [http://www.bluetack.co.uk/config/pipfilter.dat.gz](http://www.bluetack.co.uk/config/pipfilter.dat.gz)

Sources:
[https://forum.transmissionbt.com/viewtopic.php?f=4&p=50358](https://forum.transmissionbt.com/viewtopic.php?f=4&p=50358)

[http://www.bluetack.co.uk/forums/index.php?CODE=02&autocom=faq&qid=17](http://www.bluetack.co.uk/forums/index.php?CODE=02&autocom=faq&qid=17)

---

