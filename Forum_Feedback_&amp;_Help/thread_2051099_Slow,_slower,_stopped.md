---
title: "Slow, slower, stopped"
date: 2012-09-01
forum: Forum Feedback &amp; Help
---

### Post by Lars Noodén on 2012-09-01
I'm having trouble accessing the forum these last few weeks.  The pages often take over a minute to load.  Other web sites are not so slow.  Is there anything I can do to diagnose and solve the problems?  For a few days a week ago, the forum was completely unavailable to me and did not respond at all.

---

### Post by vasa1 on 2012-09-01
> **Lars Noodén said:**
> I'm having trouble accessing the forum these last few weeks.  The pages often take over a minute to load.  Other web sites are not so slow.  ...
I've been seeing this for quite a few months and since no one else complains, I thought it was just me even though other sites remain snappy as ever at the time a forum tab is loading and loading and loading ... It's not all the time but much of the time.

And it isn't browser-specific. I can check with three other browsers (kept cookie and cache-free) and the same thing happens.

(*Sometimes*, I can help things along by single-clicking in a blank space in the browser's address bar and hitting enter. I don't know why or how that works but I doubt it is coincidence.)

---

### Post by Elfy on 2012-09-01
on and off I have had the same issue. 

Ther are more than a few threads in here about the same thing - regardless of user permisssion status. 

Nothing is ~ (othr than when we DO know) obvious.

---

### Post by tienlbhoc on 2012-09-01
clean cache in your browser

---

### Post by KiwiNZ on 2012-09-01
In order for us to log a fault with Canonical we need some more information such as

Date and time
Section of the Forum involved
Time to load/access
Is it both servers or Lingonberry or Bilberry.
Browser used.

Thanks

---

### Post by vasa1 on 2012-09-01
> **KiwiNZ said:**
> ...


[1]Date and time
[2]Section of the Forum involved
[3]Time to load/access
[4]Is it both servers or Lingonberry or Bilberry.
[5]Browser used.

...

My response is a bit vague but ..

1a. ... several months

1b. I find the forum **responsive** at around this time (2 am to 4 am, UTC). Rest of the day, things are unpredictable. 

2. Any section I visit. I don't visit screenshot threads, the conky thread or any of the "games." Posting answers or questions or reporting posts are all affected.
 
3. When things are troublesome, the time to load can easily exceed a couple of minutes. **But**, some times, single clicking in the url bar and hitting enter loads a troublesome tab immediately. It happens quite frequently and I don't think it's coincidence.

4. I don't know how to know which server I'm using or how to switch servers.

5. Latest versions of Chrome, Firefox, Opera, and Seamonkey. (The last two are "clean": no cache, no cookies, no history, no extensions.)

If someone helps with point 4 that would be nice.

---

### Post by oldsoundguy on 2012-09-02
I use the old Windows trick .. I re-boot.  Trying to run down the cause when I have a 1/2 dozen windows open and a 1/2 dozen tabs in the browser would take a lot more time than a simple re-boot.  (but usually the issue is something at Facebook or another site I frequent), but again I re-boot .. thus clearing the cache and cookies!

---

### Post by lisati on 2012-09-02
> **vasa1 said:**
> 4. I don't know how to know which server I'm using or how to switch servers.> **vasa1 said:**
> 
If someone helps with point 4 that would be nice.
It usually says at the bottom right of the page.

---

### Post by vasa1 on 2012-09-02
> **lisati said:**
> It usually says at the bottom right of the page.

Okay, now it's showing lingonberry and now bilberry without logging out or doing anything at all.

---

### Post by vasa1 on 2012-09-02
That reply took about 2 min to load.

If there's anything I can do to pin things down and it's within my means I'll do it.

---

### Post by cariboo on 2012-09-02
Open a terminal and type:

```
mtr ubuntuforums.org
```

to see if there is anything along the route that could cause the slow down. See the screenshot. As you can see, there is a bit of lose from my own ISP and a server in the Netherlands.

---

### Post by Lars Noodén on 2012-09-02
A couple of nodes seem to be really off.  Sometimes the CPH node is up at 98%  The slow downs happen in multiple browsers both with and without using a proxy/cache.  Just right now it is fast and responsive, I'll get a date-time stamp next time it gives problems.  Last week there were two days I could not get through at all.

```

                             My traceroute  [v0.82]
lubuntu (0.0.0.0)                                      Sun Sep  2 22:13:36 2012
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                       Packets               Pings
 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
<snip>
 4. olucore2-o-1-1-0-0.datanet.tele. 10.6%   208   18.7  19.0  15.0  29.2   1.9
 5. hkicore2-o-4.datanet.tele.fi     10.6%   208   30.7  36.7  25.2 109.9  17.5
 6. hkiasbr2-s0-0-0.datanet.tele.fi  10.6%   208   33.3  44.6  25.2 170.2  25.2
    hkiasbr1-o-4.datanet.tele.fi
 7. hls-b1-link.telia.net            10.6%   208   30.4  31.5  24.6  91.4   9.9
    hls-b2-link.telia.net
 8. s-bb1-link.telia.net             10.6%   208   35.0  42.1  32.0 158.0  19.1
    s-bb2-link.telia.net
    s-bb2-link.telia.net
    s-bb1-link.telia.net
 9. s-b1-link.telia.net              11.1%   207   39.1  36.9  32.7  81.0   6.1
    s-b1-link.telia.net
    s-b1-link.telia.net
    s-b1-link.telia.net
10. level3-117311-s-b3.telia.net     11.1%   207   32.9  37.4  31.2  99.4   8.9
    level3-ic-130907-s-b1.c.telia.net
11. ae-2-7.bar1.Copenhagen2.Level3.n 61.6%   207   48.2  47.0  41.1  78.1   5.4
12. ae-0-10.bar1.Copenhagen1.Level3. 11.1%   207   40.8  45.2  39.5  96.2   4.9
13. ae-7-7.ebr1.Dusseldorf1.Level3.n 11.1%   207   62.8  65.1  56.8  75.9   4.4
14. ae-23-23.ebr2.Dusseldorf1.Level3 11.1%   207   66.7  61.3  55.4  72.1   4.0
15. ae-48-48.ebr1.Amsterdam1.Level3. 11.1%   207   56.5  56.7  53.1  61.9   2.0
16. ae-1-100.ebr2.Amsterdam1.Level3. 11.1%   207   56.4  56.6  52.7  74.5   2.4
17. ae-47-47.ebr2.London1.Level3.net 11.1%   207   62.4  64.2  59.3  87.3   2.8
    ae-45-45.ebr2.London1.Level3.net
    ae-46-46.ebr2.London1.Level3.net
    ae-48-48.ebr2.London1.Level3.net
18. ae-58-223.csw2.London1.Level3.ne 11.1%   207   62.2  65.1  59.3  72.4   3.5
    ae-56-221.csw2.London1.Level3.net
19. ae-2-52.edge4.London1.Level3.net 51.5%   207   72.0  68.6  63.5 112.2   4.9
20. MNET-INTERN.edge4.London1.Level3 11.1%   207   63.9  67.6  60.8 269.5  21.0
21. eth0.lutin.canonical.com         81.1%   207   65.2  68.3  65.2  72.7   1.9
22. feijoa.canonical.com             11.1%   207   67.7  67.9  62.6 115.1   5.0

```

---

### Post by Old_Grey_Wolf on 2012-09-02
The Loss% has been declining; however, ae-2-52.edge4.London1.Level3.net seems to be in my traceroute and Lars Noodén's.

```
                              My traceroute  [v0.80]
owner-Dell (0.0.0.0)                                      Sun Sep  2 17:58:57 2012
owner@owner-Dell:~$ ^Cmode   Restart statistics   Order of fields   quit
                      owner@owner-Dell:~$ Packets               Pings
 Host                                   Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. myrouter.home                        0.0%    52    0.4   0.4   0.4   0.5   0.0
 2. L100.DLLSTX-VFTTP-34.verizon-gni.ne  0.0%    52    7.0   7.5   6.0  11.5   1.1
 3. G0-3-1-6.DLLSTX-LCR-21.verizon-gni.  0.0%    52   10.7  10.0   8.8  11.8   0.7
 4. so-4-1-0-0.DFW9-BB-RTR1.verizon-gni  0.0%    52    8.3  16.2   8.3  97.4  19.4
 5. 0.xe-9-0-0.BR1.DFW13.ALTER.NET       0.0%    52    9.0  13.4   8.5  74.2  11.6
 6. ae6.edge2.dallas3.level3.net         0.0%    52    9.5  11.0   8.4  50.2   5.7
 7. vlan80.csw3.Dallas1.Level3.net       0.0%    52   12.9  13.9  10.8  23.1   3.2
 8. ae-82-82.ebr2.Dallas1.Level3.net     0.0%    52   10.6  10.6   8.7  13.7   1.3
 9. ae-3-3.ebr2.NewYork1.Level3.net      0.0%    51   53.1  52.3  50.9  53.9   0.8
10. ae-92-92.csw4.NewYork1.Level3.net    0.0%    51   60.6  54.8  51.4  64.3   3.7
11. ae-91-91.ebr1.NewYork1.Level3.net    0.0%    51   50.8  52.6  50.6  54.0   0.8
12. ae-43-43.ebr2.London1.Level3.net     0.0%    51  124.9 125.0 123.3 128.3   0.9
    ae-44-44.ebr2.London1.Level3.net
    ae-42-42.ebr2.London1.Level3.net
13. ae-58-223.csw2.London1.Level3.net    0.0%    51  119.9 122.9 119.1 130.9   3.5
    ae-56-221.csw2.London1.Level3.net
14. ae-2-52.edge4.London1.Level3.net    34.0%    51  123.2 123.3 120.9 131.5   2.0
15. MNET-INTERN.edge4.London1.Level3.ne  0.0%    51  130.4 131.1 128.6 160.6   4.5
16. eth0.lutin.canonical.com             0.0%    51  126.8 126.0 123.0 135.2   2.0
17. feijoa.canonical.com                 0.0%    51  118.8 124.7 118.8 134.1   4.3

```

---

### Post by vasa1 on 2012-09-02
> **cariboo907 said:**
> Open a terminal and type:

```
mtr ubuntuforums.org
```

to see if there is anything along the route that could cause the slow down. See the screenshot. As you can see, there is a bit of lose from my own ISP and a server in the Netherlands.
Here's mine ...
London is highest even though the forum is currently responsive for me.
It will be interesting to see where the issue is when things are really slow.

Next time, I'll post code instead of an image.

---

### Post by Lars Noodén on 2012-09-03
It was really slow at Mon Sep  3 13:29:49 UTC 2012
but mostly it's been improved.  That was going to the server 'lingonberry'


```

                                My traceroute  [v0.82]
lubuntu (0.0.0.0)                                             Mon Sep  3 16:31:27 2012
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                              Packets               Pings
 Host                                       Loss%   Snt   Last   Avg  Best  Wrst StDev
<snip>
 4. olucore2-o-1-1-0-0.datanet.tele.fi      33.3%    18  261.0 228.3  45.1 477.2 134.1
 5. hkicore2-o-4.datanet.tele.fi            38.9%    18  272.9 270.3  27.3 461.4 120.1
 6. hkiasbr2-s0-0-0.datanet.tele.fi         33.3%    18  226.8 232.5  47.3 446.9 124.1
    hkiasbr1-o-4.datanet.tele.fi
 7. hls-b1-link.telia.net                   27.8%    18  248.6 241.0  39.0 468.8 123.2
    hls-b2-link.telia.net
 8. s-bb1-link.telia.net                    27.8%    18  260.4 256.8  47.2 480.6 148.6
    s-bb2-link.telia.net
    s-bb1-link.telia.net
    s-bb2-link.telia.net
 9. s-b1-link.telia.net                     33.3%    18  332.3 261.5  52.6 482.5 141.2
    s-b1-link.telia.net
    s-b1-link.telia.net
10. level3-117311-s-b3.telia.net            27.8%    18  328.2 243.7  62.7 478.5 136.2
    level3-ic-130907-s-b1.c.telia.net
11. ae-2-7.bar1.Copenhagen2.Level3.net      94.1%    18   89.5  89.5  89.5  89.5   0.0
12. ae-0-10.bar1.Copenhagen1.Level3.net     50.0%    18  325.9 210.5  46.5 388.3 127.8
13. ae-7-7.ebr1.Dusseldorf1.Level3.net      27.8%    18  353.9 283.5  62.6 514.1 147.0
14. ae-24-24.ebr2.Dusseldorf1.Level3.net    27.8%    18  365.7 293.4  62.3 535.9 152.6
15. ae-47-47.ebr1.Amsterdam1.Level3.net     27.8%    18  343.5 283.6  74.2 491.7 139.1
16. ae-1-100.ebr2.Amsterdam1.Level3.net     27.8%    18  323.3 282.9  71.0 491.7 139.6
17. ae-46-46.ebr2.London1.Level3.net        27.8%    18  350.3 290.8  70.6 555.4 142.2
18. ae-58-223.csw2.London1.Level3.net       27.8%    18  374.3 298.2  66.2 557.2 147.0
19. ae-2-52.edge4.London1.Level3.net        94.1%    18  123.6 123.6 123.6 123.6   0.0
20. MNET-INTERN.edge4.London1.Level3.net    27.8%    18  458.1 294.1  65.1 513.2 149.5
21. eth0.lutin.canonical.com                29.4%    18  279.4 275.1  99.5 482.8 134.8
22. feijoa.canonical.com                    35.3%    18  283.2 275.2  89.9 461.6 128.8


```

---

### Post by Old_Grey_Wolf on 2012-09-03
This is another one from a few minutes ago.
```
                               My traceroute  [v0.80]
owner-Dell (0.0.0.0)                                        Mon Sep  3 16:59:01 2012
owner@owner-Dell:~$ ^Cmode   Restart statistics   Order of fields   quit
                      owner@owner-Dell:~$   Packets               Pings
 Host                                     Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. myrouter.home                          0.0%   108    0.4   0.4   0.4   0.5   0.0
 2. L100.DLLSTX-VFTTP-34.verizon-gni.net   0.0%   108    7.1   8.1   6.0  46.0   4.0
 3. G0-3-1-6.DLLSTX-LCR-21.verizon-gni.ne  0.0%   108    9.8  10.1   8.4  25.9   2.2
 4. so-4-1-0-0.DFW9-BB-RTR1.verizon-gni.n  0.0%   108   10.3  16.6   8.1 135.2  19.4
 5. 0.xe-9-0-0.BR1.DFW13.ALTER.NET         0.0%   108   10.8  12.4   8.2  64.0   8.1
 6. ae6.edge2.dallas3.level3.net           0.0%   108    9.2  10.5   8.3  43.5   4.5
 7. vlan80.csw3.Dallas1.Level3.net         0.9%   107   13.4  15.4  10.8  28.5   4.4
 8. ae-82-82.ebr2.Dallas1.Level3.net       0.0%   107    9.2  10.4   8.4  14.1   1.3
 9. ae-3-3.ebr2.NewYork1.Level3.net        0.0%   107   52.3  52.3  50.6  54.2   0.8
10. ae-92-92.csw4.NewYork1.Level3.net      0.0%   107   63.0  55.2  50.8  63.7   3.9
11. ae-91-91.ebr1.NewYork1.Level3.net      0.0%   107   53.1  52.8  50.7  63.1   2.2
    ae-71-71.ebr1.NewYork1.Level3.net
12. ae-43-43.ebr2.London1.Level3.net       0.9%   107  126.0 125.1 122.0 128.1   0.9
    ae-42-42.ebr2.London1.Level3.net
    ae-44-44.ebr2.London1.Level3.net
13. ae-58-223.csw2.London1.Level3.net      0.0%   107  124.2 123.1 118.3 131.4   3.4
    ae-57-222.csw2.London1.Level3.net
    ae-56-221.csw2.London1.Level3.net
14. ae-2-52.edge4.London1.Level3.net      68.9%   107  123.1 123.9 120.9 151.9   6.0
15. MNET-INTERN.edge4.London1.Level3.net   0.0%   107  139.8 142.3 131.2 161.8   4.6
16. eth0.lutin.canonical.com               0.0%   107  140.6 136.7 125.3 145.5   4.1
17. feijoa.canonical.com                   0.0%   107  135.6 135.7 121.4 147.9   5.5

```

---

### Post by coldraven on 2012-09-03
Yes I have had this problem. I put it down to congestion on the interwebs :)
When it happens I just go somewhere else.
Sorry but I know this does not help diagnosis.

---

### Post by Old_Grey_Wolf on 2012-09-03
It looks to me that ae-2-52.edge4.London1.Level3.net node is dropping packets. There probably isn't much the forum can do about it. I monitored it for a time and it seems to be periodic and not constant. I have had to monitor it for 10 minutes to see packet losses fluctuate from 0% to 90%. 

It is just an annoyance.

---

### Post by vasa1 on 2012-09-03
> **Old_Gray_Wolf said:**
> ... There probably isn't much the forum can do about it. ...
It is just an annoyance.
I see. Thanks.

---

### Post by Lars Noodén on 2012-09-04
> **KiwiNZ said:**
> In order for us to log a fault with Canonical we need some more information such as

Date and time
Section of the Forum involved
Time to load/access
Is it both servers or Lingonberry or Bilberry.
Browser used.

Thanks

Tue Sep  4 14:23:37 UTC 2012

Forum Feedback & Help 

About half a minute to load

Lingonberry

Chromium Version 20.0.1132.47 Ubuntu 12.10 (144678)

It's not as slow this week as last.

---

### Post by KiwiNZ on 2012-09-05
I have tried to replicate this behaviour but unable to do so. My load times are normal which of course is murphy's law.

---

### Post by Lars Noodén on 2012-09-13
It's still slow a lot.  Here is another data point:


Thu Sep 13 14:43:13 UTC 2012
Chromium Version 20.0.1132.47 Ubuntu 12.10 (144678)
lingonberry
Main Support Categories > Server Platforms


Sometimes it can take around a minute to load a page and somtimes there are even server not responding errors.

---

### Post by mips on 2012-09-14
Node/port/interface:  ae-2-52.edge4.London1.Level3.net 
IP Address:  4.69.139.106

The above node is dropping somewhere between 30-90% of all packets passing through it.

Canonical will have to take this up with Level 3 or their intermediary to Level 3.

---

### Post by vasa1 on 2012-09-14
How come only a few people are affected?

---

### Post by Lars Noodén on 2012-09-14
It's probably that only a few people are commenting or reporting the error.  Many (too many) take a fatalistic approach to computer technology and accept any situation as unavoidable and unfixable.  I myself sat on the problem for many weeks before writing about it.

---

### Post by vasa1 on 2012-09-14
Part of fatalism is to assume that whatever happens happens for the best.

---

### Post by cariboo on 2012-09-14
Depending on where you are the routing is different, I'm in Western Canada, my traceroute looks like this:

---

### Post by PaulW2U on 2012-09-18
> **mips said:**
> Node/port/interface:  ae-2-52.edge4.London1.Level3.net 
IP Address:  4.69.139.106

The above node is dropping somewhere between 30-90% of all packets passing through it.

Canonical will have to take this up with Level 3 or their intermediary to Level 3.

There were definitely problems this morning (London time 0600) on both the forums and the repositories. A 'traceroute' to various Canonical sites showed a definite problem in the final hop from Level 3 to Canonical. Everything seems back to normal now.

---

### Post by Lars Noodén on 2012-09-24
The trail to cranberry is today so slow as to be unusable.

```

                             My traceroute  [v0.82]
lubuntu (0.0.0.0)                                      Mon Sep 24 18:08:54 2012
Keys:  Help   Display mode   Restart statistics   Order of fields   quit
                                       Packets               Pings
 Host                                Loss%   Snt   Last   Avg  Best  Wrst StDev
 1. 192.168.2.1                       0.0%   242    0.3   0.3   0.3   0.4   0.0
 2. dsl-roibrasgw1-fe80fb00-1.dhcp.i  0.0%   242   10.3  10.3   6.9  53.0   4.8
 3. roicredger01-e-4-4.datanet.tele.  0.0%   242   10.3  10.4   6.9  53.2   5.4
 4. olucore1-o-1-1-0-0.datanet.tele.  0.0%   242   12.2  12.8   8.8  41.2   2.9
 5. hkicore1-e-1-1-0.datanet.tele.fi  0.0%   241   23.3  32.2  20.8 102.3  18.4
 6. hkiasbr1-s0-0-0.datanet.tele.fi   0.0%   241   25.2  44.1  23.0 196.9  39.2
    hkiasbr2-o-4.datanet.tele.fi
 7. hls-b2-link.telia.net             0.0%   241   25.1  28.1  21.1  91.2  10.7
    hls-b1-link.telia.net
 8. s-bb1-link.telia.net              0.0%   241   33.2  39.1  26.7 206.5  25.8
    s-bb2-link.telia.net
    s-bb1-link.telia.net
    s-bb2-link.telia.net
 9. s-b2-link.telia.net               0.0%   241   31.1  32.4  28.7  85.1   6.4
    s-b2-link.telia.net
    s-b2-link.telia.net
10. level3-ic-155475-s-b2.c.telia.ne  0.8%   241   37.1  32.0  28.7  65.3   4.1
11. ae-2-7.bar1.Copenhagen2.Level3.n  0.0%   241   39.1  41.7  36.8  95.5   6.9
12. ae-0-10.bar1.Copenhagen1.Level3. 33.2%   241   69.1  40.5  36.8  80.9   4.5
13. ae-7-7.ebr1.Dusseldorf1.Level3.n  0.0%   241   57.0  61.8  54.8  71.9   5.5
14. ae-21-21.ebr2.Dusseldorf1.Level3  0.0%   241   68.9  61.6  54.7  70.4   4.3
15. ae-45-45.ebr1.Amsterdam1.Level3.  0.0%   241   56.8  57.5  54.7  65.1   1.0
16. ae-1-100.ebr2.Amsterdam1.Level3.  0.0%   241   54.8  54.9  50.9  63.1   1.5
17. ae-45-45.ebr2.London1.Level3.net  0.0%   241   62.7  63.0  58.8  73.2   1.5
    ae-47-47.ebr2.London1.Level3.net
18. 4.69.153.142                      0.0%   241   62.7  64.8  59.3  76.7   3.9
    ae-57-222.csw2.London1.Level3.net
19. ae-2-52.edge4.London1.Level3.net 98.8%   241   64.6  64.5  63.6  65.4   0.9
20. MNET-INTERN.edge4.London1.Level3  0.0%   241   64.6  62.3  58.7  89.0   3.7
21. eth0.lutin.canonical.com          0.0%   241   64.5  63.5  61.3  70.7   0.8
22. cranberry.canonical.com           0.0%   241   66.4  62.8  58.9  67.4   1.8

```

---

