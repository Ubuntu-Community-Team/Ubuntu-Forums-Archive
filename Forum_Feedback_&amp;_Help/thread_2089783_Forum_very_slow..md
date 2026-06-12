---
title: "Forum very slow."
date: 2012-11-30
forum: Forum Feedback &amp; Help
---

### Post by ajgreeny on 2012-11-30
Over the last few days, (I'm not sure exactly when it started), this forum, and only this forum, has been incredibly slow at finding and displaying the page that I choose by clicking on a link; it does not matter which link it is, from a live-bookmark in firefox, or in chromium, or from a link in a thread I am already reading.  This is not a download speed problem (8Mbits/s) but simply the "Waiting for ubuntuforums.org...." showing when I click on any link; it can take as much as 16 - 20 seconds to connect, other sites are instantaneous, more or less.

All other web-sites are behaving as they have in the past, just this one seems to be the problem.  Has anyone else seen the same, and if so, how did you solve it, if you have solved it, of course?

I have searched the forum and found only this old thread with exactly the same problem, which does not appear to have been solved.

Any idea, anyone; has the forum been changed in some way recently which could account for this slowdown?

---

### Post by vasa1 on 2012-11-30
> **ajgreeny said:**
> Over the last few days, (I'm not sure exactly when it started), this forum, and only this forum, has been incredibly slow at finding and displaying the page that I choose by clicking on a link; ...
Has been reported before :(

---

### Post by Elfy on 2012-11-30
> **ajgreeny said:**
> 
All other web-sites are behaving as they have in the past, just this one seems to be the problem.  Has anyone else seen the same, and if so, how did you solve it, if you have solved it, of course?
I have exactly the same issue here, I've not found a way to solve it.

I have run 

```
mtr ubuntuforums.org
```

in the past and it seems to be the same host/node that plays up (from memory)  (ae-1-52.edge5.London1.Level3.net earlier today)

Maybe try and run it and if there is one with an issue we could compile some sort of pattern to go to canonical IS with

> **ajgreeny said:**
> 
Any idea, anyone; has the forum been changed in some way recently which could account for this slowdown?

No - afraid not.

---

### Post by drmrgd on 2012-11-30
I've noticed this too.  I'm guessing heavy traffic on the ubuntuforums.org server or some kind of network problem on their end.

---

### Post by ajgreeny on 2012-11-30
> **Elfy said:**
> I have exactly the same issue here, I've not found a way to solve it.

I have run 

```
mtr ubuntuforums.org
```in the past and it seems to be the same host/node that plays up (from memory)  (ae-1-52.edge5.London1.Level3.net earlier today)

Maybe try and run it and if there is one with an issue we could compile some sort of pattern to go to canonical IS with



No - afraid not.
Thanks for the info, Elfy.

I ran the mtr command and in my case it was **ae-2-52.edge5.London1.Level3.net **that was at fault with packet loss of 15 - 20%.  All others were 0% loss.

---

### Post by robbie 348 on 2012-11-30
I've always had this problem as well, I thought it must be my system.

---

### Post by Elfy on 2012-11-30
> **ajgreeny said:**
> Thanks for the info, Elfy.

I ran the mtr command and in my case it was **ae-2-52.edge5.London1.Level3.net **that was at fault with packet loss of 15 - 20%.  All others were 0% loss.

I'll keep an eye on this - if people can use the same thing - perhaps we can find a weak link and pass it on to IS.

That said - I'm getting slow page loads here still and nothing showing.

---

### Post by drmrgd on 2012-11-30
I too am seeing about 26% packet loss at that same host, ae-2-52.edge5.London1.Level3.net.  

On a side note, had no idea about the 'mtr' command.  Very nice utility!

---

### Post by Statia on 2012-11-30
> **ajgreeny said:**
> 

I ran the mtr command and in my case it was **ae-2-52.edge5.London1.Level3.net **that was at fault with packet loss of 15 - 20%.  All others were 0% loss.

Same here.

---

### Post by howefield on 2012-11-30
Predictably enough, as soon as I ran the mtr command, things got very much better with page loads pretty much where they should be.

The worst for me is

ae-0-11.edge4.London2.Level3.net with 4% loss.

All other servers are between zero and 1% loss.

---

### Post by Elfy on 2012-11-30
ae-1-51.edge5.London1.Level13.net 18.4%

---

### Post by SlugSlug on 2012-11-30
```
 6. te-4-3.car1.Manchester1.Level3.net                                                                            15.2%    33   14.2  31.4  13.9  94.6  28.2
 7. ae-4-4.ebr1.London1.Level3.net                                                                                12.1%    33   16.1  16.1  14.4  30.9   3.1

```

---

### Post by SeijiSensei on 2012-11-30
I think the problem is on the SQL server end and not the speed of the connection.  The more database-intensive a query, the longer it seems to take.  Generating the "New Posts" page takes quite a while at the moment.  Even extracting single postings from the DB is pretty slow.

---

### Post by ajgreeny on 2012-11-30
I have just this minute run the mtr command again and it is still the **ae-2-52.edge5.London1.Level3.net** server that is so slow; at the moment it has a 20% packet loss, all the rest still showing no problem.

So.....  There's the likely cause; now what can we do about it?

---

### Post by sdowney717 on 2012-11-30
Still running very slow for me. Especially noticeable just doing a search for all my posts or threads. It is taking multiple tens of seconds. It used to be mostly instant.

---

### Post by sdowney717 on 2012-11-30
click new reply takes 5 seconds.
click submit reply takes 10 seconds.

very slow.

---

### Post by Elfy on 2012-11-30
we are just trying something

---

### Post by Elfy on 2012-11-30
Can those of you who posted comment if you still getting the same slowness, bear in mind that at times the forum is slow.

---

### Post by KiwiNZ on 2012-11-30
Yesterday it was sluggish for me however this morning speed is normal.

---

### Post by oldos2er on 2012-11-30
I am experiencing slowness too. ae-2-52.edge5.London1.Level3.net fluctuates between 20% and 30% packet loss.

---

### Post by Elfy on 2012-11-30
It's certainly responding a lot better for me than it has done in the last 12 hours.

---

### Post by lisati on 2012-11-30
I've noticed an intermittent sluggishness too, but it seems back to near normal for me this morning as well.

---

### Post by coffeecat on 2012-11-30
> **Elfy said:**
> It's certainly responding a lot better for me than it has done in the last 12 hours.

+1

Just to add to what Elfy said earlier in the thread. Elfy and I were comparing notes in irc and the forum was slow for both of us. We tried something and it has sped up for both of us, but we can't be sure whether this is cause and effect yet, or whether others in other locations are seeing the same. Feedback from others would be helpful.

---

### Post by sdowney717 on 2012-11-30
Hey you have improved the speed!

---

### Post by sdowney717 on 2012-11-30
search for my posts is now only 2 - 3 seconds. So yes what ever you did helped.
add a post 1 second

---

### Post by Elfy on 2012-11-30
Thanks for the feedback :)

---

### Post by Elfy on 2012-11-30
magic swizzle stick ftw then ...

---

### Post by sffvba[e0rt on 2012-11-30
> Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\<snip>>mtr ubuntuforums.org
'mtr' is not recognized as an internal or external command,
operable program or batch file.

C:\Documents and Settings\<snip>>

That didn't work for me :(


404

PS - Yes yes, I know :p

---

### Post by JKyleOKC on 2012-11-30
Still very slow for me. See attached mtr report.

---

### Post by sdowney717 on 2012-11-30
here is my mtr report

---

### Post by ajgreeny on 2012-11-30
Still slow for me as well, but not so bad as it was earlier when I started this thread.
See screenshot of my mtr report as well; still that **ae-1-52.edge5.London1.Level3.net** server that is causing the losses.

---

### Post by CharlesA on 2012-11-30
Just wanted to report I am experiencing the same thing, but it was fine for me earlier. It looks like the ones I am having problems with are part of the level3.net nodes.

ae-2-52.edige5.Lundon1.Level3.net is the main one with a 10+% of packet

```

 7. xe-7-3-0.edge1.SanJose2.Level3.net                       2.0%   147   34.6  34.4  31.6  60.7   4.6
 8. vlan90.csw4.SanJose1.Level3.net                          1.4%   147   45.4  50.0  44.2  79.3   5.7
 9. ae-91-91.ebr1.SanJose1.Level3.net                        1.4%   147   34.7  35.9  32.8  54.3   3.7
10. ae-2-2.ebr2.NewYork1.Level3.net                          4.1%   147  102.8 103.7 101.1 129.4   3.3
11. ae-62-62.csw1.NewYork1.Level3.net                        6.1%   147  123.8 119.0 106.4 133.8   5.0
    ae-72-72.csw2.NewYork1.Level3.net
    ae-82-82.csw3.NewYork1.Level3.net
12. ae-61-61.ebr1.NewYork1.Level3.net                        4.1%   147  103.4 104.3 101.4 119.0   3.0
    ae-71-71.ebr1.NewYork1.Level3.net
    ae-91-91.ebr1.NewYork1.Level3.net
    ae-81-81.ebr1.NewYork1.Level3.net
13. ae-41-41.ebr2.London1.Level3.net                         2.7%   147  175.5 175.8 170.2 186.8   4.2
    ae-42-42.ebr2.London1.Level3.net
    ae-43-43.ebr2.London1.Level3.net
14. ae-58-223.csw2.London1.Level3.net                        0.0%   147  178.4 173.9 170.4 200.0   3.8
    ae-59-224.csw2.London1.Level3.net
    ae-57-222.csw2.London1.Level3.net
15. ae-2-52.edge5.London1.Level3.net                         8.8%   147  181.4 183.8 180.9 224.2   4.7
16. SOURCE-MANA.edge5.London1.Level3.net                     0.0%   147  173.2 173.5 170.8 204.6   3.9
17. eth0.lutin.canonical.com                                 2.1%   147  181.5 183.7 181.1 199.7   2.9

```

Everything from hop 6 and up is local to me with 0 packet loss.

---

### Post by boogerama on 2012-12-01
... or is it just me?  I'm getting decent speeds on other sites. 

Changing forums or opening posts seem to be taking longer than normal today.

---

### Post by lisati on 2012-12-01
Threads merged.

---

### Post by SeijiSensei on 2012-12-01
Performance improved for a brief period after Elfy's post, but it's been slow again most of today.  Are you sure it's not an SQL issue?  It sure feels that way from here.

---

### Post by CharlesA on 2012-12-02
I don't think so. It looks like it might be an issue of dropped packets, at least from what I have seen.

It was quicker earlier when I checked there was no  dropped packets, but now it is back to being slow. Looks like it's still getting stuck in the level3 realm. :|

---

### Post by catlover2 on 2012-12-02
Earlier in the week: perfect.
Yesterday: unusably slow.
Today: much better.

```
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                                                                                                                               Packets               Pings
 Host                                                                                                                                        Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. <My router>                                                                                                                               0.0%   136    0.5   0.5   0.4   6.3   0.5
 2. 73.90.28.1                                                                                                                                0.0%   136    8.2   8.7   6.4  21.5   2.2
 3. 68.85.148.121                                                                                                                             0.0%   136    8.8   9.0   7.0  16.7   1.8
 4. 68.87.216.121                                                                                                                             0.0%   136   17.1  17.6   9.5 122.7  21.0
 5. pos-1-15-0-0-cr01.seattle.wa.ibone.comcast.net                                                                                            0.0%   136   18.9  17.4  14.4  27.2   1.9
    pos-2-1-0-0-cr01.seattle.wa.ibone.comcast.net
    pos-2-3-0-0-cr01.seattle.wa.ibone.comcast.net
    pos-2-2-0-0-cr01.seattle.wa.ibone.comcast.net
    pos-2-4-0-0-cr01.seattle.wa.ibone.comcast.net
    pos-1-14-0-0-cr01.seattle.wa.ibone.comcast.net
 6. pos-0-0-0-0-pe01.seattle.wa.ibone.comcast.net                                                                                             0.0%   136   15.7  16.0  14.0  23.6   1.4
 7. ix-0-3-1-0.tcore1.00S-Seattle.as6453.net                                                                                                  0.0%   136   20.1  17.3  13.9  54.1   6.7
 8. if-14-2.tcore1.PDI-PaloAlto.as6453.net                                                                                                    0.0%   136   57.0  39.0  34.2  90.6   8.3
 9. if-2-2.tcore2.PDI-PaloAlto.as6453.net                                                                                                     0.0%   136   35.0  38.2  33.5  95.8   9.3
10. if-13-0-0-3255.core3.SQN-SanJose.as6453.net                                                                                               0.0%   135   36.3  36.6  34.5  46.4   1.6
11. Vlan1105.icore1.SQN-SanJose.as6453.net                                                                                                   17.8%   135   39.4  41.6  35.3  54.1   4.5
12. Vlan559.icore1.SQN-SanJose.as6453.net                                                                                                     0.0%   135   60.1  52.8  41.3 103.5   9.1
13. vlan80.csw3.SanJose1.Level3.net                                                                                                           0.0%   135   56.4  55.4  41.2  69.9   5.7
14. ae-81-81.ebr1.SanJose1.Level3.net                                                                                                         0.0%   135   60.8  51.3  40.1  65.1   4.9
15. ae-2-2.ebr2.NewYork1.Level3.net                                                                                                           0.0%   135   96.1  95.8  93.6 113.2   2.1
16. ae-82-82.csw3.NewYork1.Level3.net                                                                                                         0.0%   135  107.3  99.8  93.7 116.5   4.7
    ae-72-72.csw2.NewYork1.Level3.net
    ae-92-92.csw4.NewYork1.Level3.net
    ae-62-62.csw1.NewYork1.Level3.net
17. ae-81-81.ebr1.NewYork1.Level3.net                                                                                                         0.0%   135   98.6  95.9  93.8 109.2   2.0
    ae-91-91.ebr1.NewYork1.Level3.net
    ae-71-71.ebr1.NewYork1.Level3.net
    ae-61-61.ebr1.NewYork1.Level3.net
18. ae-42-42.ebr2.London1.Level3.net                                                                                                          0.0%   135  164.1 164.5 162.4 172.7   1.6
    ae-44-44.ebr2.London1.Level3.net
19. ae-59-224.csw2.London1.Level3.net                                                                                                         0.0%   135  173.1 166.7 162.3 183.4   4.3
    ae-57-222.csw2.London1.Level3.net
20. ae-2-52.edge5.London1.Level3.net                                                                                                         64.9%   135  165.1 165.4 162.2 204.6   6.4
21. SOURCE-MANA.edge5.London1.Level3.net                                                                                                     20.7%   135  169.5 166.9 162.9 368.1  19.7
22. eth0.lutin.canonical.com                                                                                                                  0.0%   135  166.3 164.8 162.7 174.1   1.6
23. feijoa.canonical.com                                                                                                                      0.0%   135  164.6 165.0 162.8 179.9   1.9
```

---

### Post by vasa1 on 2012-12-02
> **lisati said:**
> Threads merged.

[http://ubuntuforums.org/showthread.php?t=2051099](http://ubuntuforums.org/showthread.php?t=2051099)

---

### Post by Elfy on 2012-12-02
> **vasa1 said:**
> [http://ubuntuforums.org/showthread.php?t=2051099](http://ubuntuforums.org/showthread.php?t=2051099)

We know thanks.

---

### Post by Elfy on 2012-12-02
> **SeijiSensei said:**
> Performance improved for a brief period after Elfy's post, but it's been slow again most of today.  Are you sure it's not an SQL issue?  It sure feels that way from here.

To be frank we don't know.

We have no control over any of that, sometimes getting things looked at by IS is quick, sometimes not.

Appearing normal at the moment.

As an aside - if what we did the other day did help - then I'm afraid we can't keep doing it - though it might be worth mentioning it to IS. 

If I get time in the week to talk to them I will.

---

### Post by irv on 2012-12-02
I also was thinking about posting about the slowness of the forum when I found this thread. Running the mtr command If found a lot of lost packets 
[ATTACH]228089[/ATTACH]
I also check my Internet speed at the same time and it looked good.
[ATTACH]228090[/ATTACH]
This forum started to get slow about 4 or 5 days ago in my area.

EDIT: Just took notice that in the Minneapolis1 area I have as high as 90% packets lost.
I tried the mtr command with other websites and found I have no lost packets. I believe the slowness is because of lost packets and that they need to be re-transmitted so many times.

---

### Post by ibjsb4 on 2012-12-02
After several days, it seems to be back to normal now.  Location USA.

---

### Post by CharlesA on 2012-12-02
It has been off-and-on for me. So far it has been stable today, but who knows if it will be the same tomorrow.

---

### Post by JKyleOKC on 2012-12-02
Better this morning but still not fixed. Note hop 13 in the attached shot; it's consistently dropping more than 10% of its packets.

---

### Post by vasa1 on 2012-12-02
Using mtr shows that even help.ubuntu.com and launchpad.net are affected the same way.

---

### Post by JKyleOKC on 2012-12-02
Yes, it seems pretty clear that the problem is in Level3's London facilities.

Incidentally, using "-i 2" option for mtr eliminates a lot of clutter on the intervening hops...

---

### Post by irv on 2012-12-02
I tried doing a mtr on these sites:
> 
ubuntuforums.org
launchpad.net
help.ubuntu.com
linuxforums.org
[ATTACH]228112[/ATTACH][ATTACH]228113[/ATTACH][ATTACH]228114[/ATTACH][ATTACH]228115[/ATTACH]
The linuxforms.org had the least lost packets.

---

### Post by vasa1 on 2012-12-02
> **irv said:**
> ...
The linuxforms.org had the least lost packets.
That may not have too much to do with the present topic.

My feeling is that if there is a common slowest hop but other sites are still snappy, it could point to some forum-specific issue.

For example, I've noticed downloads of .woff that I'm not sure were there a while back. Maybe the .woff stuff is intended to fix forum font issues that some users experienced?

---

### Post by vasa1 on 2012-12-02
Hmm... archive.ubuntu.com also shows a London server to be slowest. But the slowness is less that what I've seen for the forum. I haven't tried looking at both or more than one at the same time. I don't know how to.

If there is a difference, could there be some sort of priority involved?

---

### Post by Statia on 2012-12-03
I just had 50-60% packet loss at ae-2-52.edge5.London1.Level3.net, levelled out to around 30%.

---

### Post by irv on 2012-12-03
> **vasa1 said:**
> That may not have too much to do with the present topic.

When I said The linuxforms.org had the least lost packets. I know it has nothing to do with the slowness of the forum, I was just using it to compare with. I randomly picked another forum website to compare with the Ubuntu forum.

---

### Post by canonicalsysadmin on 2012-12-04
mtr uses what are called ICMP Echo packets to find the route between you and a destination. Unfortunately it is common for core internet routers to discard these, as "real" traffic (e.g., web traffic, email, etc)  is considered more important than an echo request.
Correspondingly it's not at all uncommon to see 20-50% packet loss on core routers. Notice you do not see packet loss to hosts behind that router: if it were actually dodgy, everything behind it should show the same failure rate.

We are undertaking a round of upgrades right now, which may help with slowness issues. We are also looking at a more comprehensive upgrade of the forums infrastructure to land in the coming weeks, which should help as well.

---

### Post by arpanaut on 2012-12-04
> We are undertaking a round of upgrades right now, which may help with  slowness issues. We are also looking at a more comprehensive upgrade of  the forums infrastructure to land in the coming weeks, which should help  as well. 	

YAY!
Thank You!

---

### Post by Elfy on 2012-12-05
Certainly appearing to be much better than it has been for days.

> We are also looking at a more comprehensive upgrade of the forums infrastructure to land in the coming weeks, which should help as well.To clarify, because I for one imagined that to be new shiny hardware, the vBulletin upgrade is closer than ever before :)

---

