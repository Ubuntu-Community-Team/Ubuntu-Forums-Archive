---
title: "Scheduling download with rtorrent"
date: 2007-11-13
forum: Desktop Environments
---

### Post by petnell on 2007-11-13
Hi Guys ,
              firstly this is a great forum, My question is how to enable download scheduling in rtorrent.

i've added the following couple of lines in rtorrent.rc but still not working correctly.

#Scheduling torrents during ISP off peak time
schedule = throttle_1,01:00,09:00,download_rate=0
schedule = throttle_2,09:01,00:55,download_rate=10


Between 01:00 (1am) to 09:00(9am) i want full download speed and between 09:01(9:01 am) to 00:55 (12:55am) i want to cap speed to 10 kpbs.

So Throttle_2 will be at 10 kpbs between 09:00 to 00:55. Which is just under 16 hours. Throttle_1 at full speed during 01:00 to 09:00

Thanks in advance

---

### Post by konsole on 2007-11-14
> **petnell said:**
> Hi Guys ,
              firstly this is a great forum, My question is how to enable download scheduling in rtorrent.

i've added the following couple of lines in rtorrent.rc but still not working correctly.

#Scheduling torrents during ISP off peak time
schedule = throttle_1,01:00,09:00,download_rate=0
schedule = throttle_2,09:01,00:55,download_rate=10



Your time interval is wrong. From the manpage:
```
 schedule = id,start,interval,command 
```

Read more here:

[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Schedulingdownloadrate](http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks#Schedulingdownloadrate)

---

### Post by petnell on 2007-11-14
Thanks for the swift reply Konsole.


#Scheduling torrents during AANET peak time
schedule = throttle_1,01:00,08:00,download_rate=0
schedule = throttle_2,09:00,16:00,download_rate=5

throttle_1=start downloaded at full spped @ 01:00 (1am) for 8 hours.
throttle_2=downloads from 09:00 (9am) for 16 hours @ 5 kpbs.

Does this look correct? Still playing up currently

---

### Post by petnell on 2007-11-14
looked at the man pages

       schedule = id,start,interval,command
              Call command every interval seconds,  starting  from  start.  An
              interval  of  zero  calls  the  task once, while a start of zero
              calls it immediately. Currently  command  is  forwarded  to  the
              option  handler.   start  and interval may optionally use a time
              format, dd:hh:mm:ss. F.ex to start a task every  day  at  18:00,
              use 18:00:00,24:00:00.

#Scheduling torrents during AANET peak time
schedule = throttle_1,01:00,24:00,download_rate=0
schedule = throttle_2,09:00,24:00,download_rate=5

I also tried this above! LOL im lost :---)

---

### Post by konsole on 2007-11-15
> **petnell said:**
> 

#Scheduling torrents during AANET peak time
schedule = throttle_1,01:00,24:00,download_rate=0
schedule = throttle_2,09:00,24:00,download_rate=5

I also tried this above! LOL im lost :---)

like this: ```

schedule = throttle_1,01:00:00,24:00:00,download_rate=0
schedule = throttle_2,09:00:00,24:00:00,download_rate=5
```

---

