---
title: "How do I see how long a machine has been on it's hole life?"
date: 2009-02-25
forum: General Help
---

### Post by linuxisevolution on 2009-02-25
Besides measuring the layers of dust. My Debian server has been up 13 days, it's longest around 2 months ( power failures ). I was just wondering if there was a neat program that could add up all the uptimes or record the total time the server has ever been on even after shutdowns? If there is mine would be around 15 years :p.

---

### Post by lukjad on 2009-02-25
linuxisevolution, while I'm sure it's possible to really find out, say by the wear and tear on components, Unless the computer has never been reinstalled and has been logging everything and logging the logs, I really don't think it's possible.

---

### Post by ibuclaw on 2009-02-25
I concur with lukjad007,

Although, if you have a file/folder that you haven't used since the time you installed, you could run, for example
```
ls -lt /
```

or, if you do a little bash foo
```
ls -lt / | awk '{print $6}' | sort -u 
```

You could perhaps make the **ls** command -R (recursive) if you are willing to wait a while :)
[EDIT]
hmm... actually, scrap that recursion suggestion, I've just tried it and I get dates from all over the place (1913 ... 1921 ... 1992 ...)

try this instead
```
ls -lt -c / -R| awk '{print $6" "$8}' | sort -u | less
```
after some time of hitting PageDown, I get this:
```

2006-01-03 #6046344
2006-03-17 #6051560
2006-07-02 #6053323
2006-09-09 #6053356
20 06:35
2007-01-16 #6045842
2007-07-20 #6039237
2007-12-17 #6047658
2008-01-14 #6045035
2008-01-15 #6043014
2008-03-25 #6040080
**2008-07-04 10-antialias.conf**
2008-07-04 10-autohint.conf
2008-07-04 10-hinting.conf

```
I know I haven't had my machine installed very long, but that looks about right of the day I installed this OS on it (it was also the first file that had a normal name :))

Regards
Iain

---

### Post by mb_webguy on 2009-02-25
But that will only show how old the system is, won't it?  It won't show total uptime...

---

### Post by cariboo on 2009-02-25
I use a program called uprecords, it won't show you the total up time, but it will show you the number of restarts since you installed the package. See screenshot.

Jim

---

### Post by mb_webguy on 2009-02-25
It wouldn't be too difficult to write a script that runs at shutdown that adds uptime to a running tally, but it still wouldn't be able to determine how long the system has been running before the script was created.

Actually, that sounds like a pretty good idea.  I think I'll write it...

---

### Post by yther on 2009-02-25
Well, **smartctl** can tell you how many hours a given hard drive has been powered on, or at least it reports that for mine.  If the same drive(s) have been in your server during its entire lifetime, you could use that to check.  I've had this laptop for almost two years, and I've got 0.92 years (8140 hours) worth of time on my hard drive, so that seems fairly accurate.

---

### Post by heindsight on 2009-02-25
You could probably use something like:
```

awk '{t+=$1}; END{print t >"/var/log/uptime"}' /var/log/uptime /proc/uptime

```
Put that in a script that runs at shutdown (before /proc is unmounted of course), and then have another script, something like 
```

awk '{printf "%ddays %02d:%02d:%02d\n", $1/86400, ($1/3600)%24, ($1/60)%60, $1%60}' /var/log/uptime

```
To display the total uptime in a more human readable form.

Of course this will only give total uptime since you started using this, and of course it's not immune to tampering with /var/log/uptime (which may not be the best place to save the total uptime, but I couldn't quite decide where to put it). Also, it sort of assumes that you always shut your machine down properly, but of course you do that ;)

---

### Post by sdennie on 2009-02-26
To elaborate/steal/combine some of the other posts, here is the smartctl method combined with some awk magic:

```

sudo smartctl -a /dev/sda | grep Power_On_Hours | awk '{ printf "%02d days %02d hours\n", $10/24, $10%24 }'

```

If your disk supports it (and is called /dev/sda), you should get output like:

```

210 days 06 hours

```

You will probably also need to install smartmontools first:

```

sudo apt-get install smartmontools

```

I don't know any other way to get this information unless your BIOS stores it and it's visble from the BIOS screen.

---

### Post by heindsight on 2009-02-26
> **sdennie said:**
> 
```
sudo smartctl -a /dev/sda | grep Power_On_Hours | awk '{ printf "%02d days %02d hours\n", $10/24, $10%24 }'
```

On my machine I had to change that Power_On_Hours to Power_On_Seconds.

Also, wouldn't it be slightly more efficient to do:
```
sudo smartctl -A /dev/sda | awk '/Power_On_Seconds/{ printf "%02d days %02d hours\n", $10/24, $10%24 }'
```

EDIT:
Hmm, on my four year old laptop this reports 464 days 16 hours (that's 1 year and 99 days). I was expecting something closer to 2 years.

---

### Post by sdennie on 2009-02-26
> **heindsight said:**
> 
Also, wouldn't it be slightly more efficient to do:
```
sudo smartctl -A /dev/sda | awk '/Power_On_Seconds/{ printf "%02d days %02d hours\n", $10/24, $10%24 }'
```


It would be if I ever got around to learning awk!  ;)

(I just implied the syntax based on your awk expression...)

---

