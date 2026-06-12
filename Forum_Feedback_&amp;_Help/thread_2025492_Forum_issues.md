---
title: "Forum issues?"
date: 2012-07-14
forum: Forum Feedback &amp; Help
---

### Post by mips on 2012-07-14
> 
ERROR

The requested URL could not be retrieved

While trying to retrieve the URL: [http://ubuntuforums.org/forumdisplay.php?](http://ubuntuforums.org/forumdisplay.php?)

The following error was encountered:

Connection to ubuntuforums.org Failed
The system returned:

    (111) Connection refused
The remote host or network may be down. Please try the request again. 


Been getting this intermittently today, don't have problems with any other sites. The pages that do load also seem slow.

---

### Post by CharlesA on 2012-07-14
Seems ok for me so far.

---

### Post by Elfy on 2012-07-14
Would be good to see a url for a thread you had an issue with probably.

I've not seen anything untoward all day.

---

### Post by QIII on 2012-07-14
Over the last couple of days I have noticed slow loading from time to time using Firefox, but no failures to load.

Strangely, IE on my Windows machine seems to work fine.

---

### Post by mips on 2012-07-14
> **Elfy said:**
> Would be good to see a url for a thread you had an issue with probably.


No specific link.

I'll clear out my cache an stuff to see if that helps. Probably a problem on my side.

---

### Post by mips on 2012-07-15
Clearing my cache & cookies sorted the problem out ;)

---

### Post by Elfy on 2012-07-15
Thanks for letting us know mips :)

---

### Post by mips on 2012-07-16
Looks like I spoke to soon #-o

Just experienced the same issue again when trying to open,
[http://ubuntuforums.org/showthread.php?p=12107158](http://ubuntuforums.org/showthread.php?p=12107158)

Wonder what it could be as I'm not experiencing issues on any other sites. Will have to dig deeper.

---

### Post by Elfy on 2012-07-16
Not sure what to suggest to be honest - I can see that on both servers. 

Next time try reload and see if you can see whichever thread on a different server - names are at the bottom - lingonberry and bilberry.

Maybe it is a sync thing - but I've as much knowledge about that as I have surgery :)

---

### Post by mips on 2012-07-16
I just updated my browser to the latest version and still the same issue, this was trying to open the community cafe & forum feedback sub forums.

---

### Post by Elfy on 2012-07-16
I have to say I have no idea mips - sorry.

I expect someone else will wander by in due course.

---

### Post by vasa1 on 2012-07-16
It's not uncommon for me but it doesn't happen all the time either. Clearing cache and cookies doesn't help. Which is the main reason I lose out in reporting spam :(

Just to be clear, I can load several other sites while one forum page is loading ... and loading ...

I'd say it's been going on for more than a month.

Sorry I can't be more helpful.

Edit: and it's not limited to any one browser. I see the problem with the latest Chrome, Firefox, Opera and Seamonkey.

---

### Post by QIII on 2012-07-16
I'm not having problems with either IE or Firefox any more on Win or Linux.  What I may have seen could have been just intermittent.

---

### Post by CharlesA on 2012-07-16
> **QIII said:**
> I'm not having problems with either IE or Firefox any more on Win or Linux.  What I may have seen could have been just intermittent.
Same. This has me puzzled.

---

### Post by mips on 2012-07-16
> **QIII said:**
> I'm not having problems with either IE or Firefox any more on Win or Linux.  What I may have seen could have been just intermittent.

Problem happens on Chromium & FF for me, Xubuntu 12.04 base install + XFCE 4.10.

I just started up Win7 in VB and on IE8 & Chrome I got exactly the same problem. Granted VB using NAT still uses my native network stack.

Ok, I just booted up an old laptop I'm working on for someone else with a fresh install of WinXP SP3, latest browser, latest everything and still the same problem.

So this eliminates my desktop as the problem. The only thing left for me to eliminate is my ISP. Gonna switch to a different ISP shortly and see what happens.

---

### Post by mips on 2012-07-16
Ok, just tried another ISP and so far so good. Pages on this forum also load much faster now. Thing is it's specific to this single site.

I'll have a chat to the problematic isp. They are using a their own backbone which differs from the backbone provider of the ISP I'm posting this on.

EDIT: More for my reference & record than anything else but here are the traceroute outputs.

```
**WORKING ISP:**
*username*@obelix:~$ traceroute ubuntuforums.org
traceroute to ubuntuforums.org (91.189.94.12), 30 hops max, 60 byte packets
 1  * * *
 2  196-210-130-129.dynamic.isadsl.co.za (196.210.130.129)  55.505 ms  65.504 ms  75.455 ms
 3  cdsl1-rba-vl2360.ip.isnet.net (196.38.73.133)  99.467 ms  109.480 ms  119.455 ms
 4  cdsl1-rba-vl150.ip.isnet.net (196.38.73.17)  129.536 ms  139.557 ms  149.442 ms
 5  core2b-pkl-te0-0-0-0.ip.isnet.net (196.26.0.63)  159.394 ms  171.382 ms  179.431 ms
 6  168.209.201.85 (168.209.201.85)  371.489 ms  336.137 ms  334.139 ms
 7  195.50.124.33 (195.50.124.33)  332.172 ms  318.254 ms  318.133 ms
 8  vl-3501-ve-115.csw1.London1.Level3.net (4.69.166.129)  322.368 ms vl-3503-ve-117.csw1.London1.Level3.net (4.69.166.137)  320.214 ms vl-3604-ve-228.csw2.London1.Level3.net (4.69.166.157)  322.201 ms
 9  * * ae-1-51.edge4.London1.Level3.net (4.69.139.74)  318.206 ms
10  MNET-INTERN.edge4.London1.Level3.net (212.113.14.198)  322.109 ms  218.180 ms  220.094 ms
11  eth0.peumo.canonical.com (91.189.88.10)  224.229 ms  230.148 ms  234.020 ms
12  * * *

**PROBLEMATIC ISP:**
*username*@obelix:~$ traceroute ubuntuforums.org
traceroute to ubuntuforums.org (91.189.94.12), 30 hops max, 60 byte packets
 1  * * *
 2  41.183.7.1 (41.183.7.1)  53.514 ms  63.500 ms  73.498 ms
 3  41.183.141.25 (41.183.141.25)  93.512 ms  103.494 ms  113.475 ms
 4  41.183.132.68 (41.183.132.68)  127.465 ms  137.409 ms  147.398 ms
 5  41.183.132.82 (41.183.132.82)  155.376 ms  165.413 ms  173.388 ms
 6  196.31.44.185 (196.31.44.185)  185.641 ms  146.011 ms  146.043 ms
 7  am-cr-2.nl--am-tpr-1.nl-a.mtn.net (209.212.111.218)  332.192 ms  322.121 ms  322.120 ms
 8  xe-4-1-0.edge5.Amsterdam1.Level3.net (212.72.41.89)  316.168 ms  314.135 ms  312.129 ms
 9  4.69.162.153 (4.69.162.153)  330.371 ms 4.69.162.149 (4.69.162.149)  316.251 ms 4.69.162.157 (4.69.162.157)  324.448 ms
10  ae-58-223.ebr2.Amsterdam1.Level3.net (4.69.153.209)  322.231 ms ae-59-224.ebr2.Amsterdam1.Level3.net (4.69.153.213)  321.978 ms ae-57-222.ebr2.Amsterdam1.Level3.net (4.69.153.205)  318.257 ms
11  ae-47-47.ebr2.London1.Level3.net (4.69.143.78)  318.322 ms ae-46-46.ebr2.London1.Level3.net (4.69.143.74)  226.152 ms ae-47-47.ebr2.London1.Level3.net (4.69.143.78)  224.179 ms
12  ae-57-222.csw2.London1.Level3.net (4.69.153.134)  244.171 ms  234.161 ms ae-59-224.csw2.London1.Level3.net (4.69.153.142)  236.192 ms
13  ae-2-52.edge4.London1.Level3.net (4.69.139.106)  232.150 ms  222.194 ms  229.900 ms
14  MNET-INTERN.edge4.London1.Level3.net (212.113.14.198)  229.767 ms  234.023 ms  234.035 ms
15  eth0.peumo.canonical.com (91.189.88.10)  238.001 ms  241.922 ms  217.978 ms
16  * * *
```

---

### Post by epikvision on 2012-07-16
I had no problems at all with the site. The link provided led me to an invalid post.

---

### Post by mips on 2012-07-16
> **epikvision said:**
> I had no problems at all with the site. The link provided led me to an invalid post.

That link works for me so maybe you do have problems after all :-k

---

### Post by sammiev on 2012-07-16
The link works great for me as well. Yesterday I had a few slow downs just with this site but no load errors. It slowed enough that I went to other sites of interesting hobbies I have. Today this site has been working great with no slow downs at all.

---

### Post by Elfy on 2012-07-16
> **epikvision said:**
> I had no problems at all with the site. The link provided led me to an invalid post.

Which link? 

There are 2 - the one in the first post will fail for anyone I think :)

---

### Post by CharlesA on 2012-07-16
> **Elfy said:**
> Which link? 

There are 2 - the one in the first post will fail for anyone I think :)
Yep, the first one fails cuz there is no formumid or something. Second link works fine.

---

### Post by mips on 2012-09-11
Ok this has finally been sorted out.

Issue was related to the ISPs proxy server.

I did fill out all the details (long explanations, traceroutes etc etc) back in the day but by the time I finished typing my session had expired and the online submission form came up blank and I have been using other ISPs. Today I sent them a mail with all the info and they localised the problem to their proxy server and this site now bypasses the proxy.

---

