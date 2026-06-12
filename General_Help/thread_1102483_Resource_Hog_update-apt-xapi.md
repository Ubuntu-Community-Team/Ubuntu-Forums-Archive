---
title: "Resource Hog: update-apt-xapi"
date: 2009-03-21
forum: General Help
---

### Post by GuiGuy on 2009-03-21
I see a process update-apt-xapi that brings my system to an unusable state each morning

update-apt-xapi

Shades of Windows!

Is this thing really necessary, or can I 

sudo apt-get autoremove --purge apt-xapian-index
sudo apt-get autoremove --purge

without breaking something else?

NB: It has been suggested this problem occurs on low resource system only. Wrong; my PC is high end, dual core, 4G RAM.

Thanks

---

### Post by zvacet on 2009-03-21
You can go to the synaptic and find that package and **lock version**.That way it will be no more upgraded.You can also 

```
sudo aptitude hold package_name
```

---

### Post by GuiGuy on 2009-03-21
> **zvacet said:**
> You can go to the synaptic and find that package and **lock version**.That way it will be no more upgraded.You can also 

```
sudo aptitude hold package_name
```

Thanks

---

### Post by fcormier on 2009-04-10
I have the same issue, but my system is rather old (P3 with 256 MB of RAM) and running Xubuntu.

Here is what I did to disable it:
```
sudo chmod 644 /etc/cron.weekly/apt-xapian-index
```
It makes the file not executable.

---

### Post by ashmew2 on 2009-07-07
Was having the same issue ,  Jaunty 32 Bit, this site helped : [http://reformedmusings.wordpress.com/2009/06/05/fixing-update-apt-xapian-in-ubuntu-9-04-jaunty/](http://reformedmusings.wordpress.com/2009/06/05/fixing-update-apt-xapian-in-ubuntu-9-04-jaunty/)

Thanks to the person who wrote it!! :D

---

### Post by alias_knagg on 2009-09-03
Nice enough tale, but why not just "nice" it?
 
in /etc/cron.weekly/apt-xapian-index

Change
       ```
$CMD --quiet
```
to
       ```
nice -n20 $CMD --quiet
```

---

### Post by klausner on 2009-09-23
> **alias_knagg said:**
> Nice enough tale, but why not just "nice" it?
 
in /etc/cron.weekly/apt-xapian-index

Change
       ```
$CMD --quiet
```
to
       ```
nice -n20 $CMD --quiet
```

I thought the highest positive value for nice was 19.

---

### Post by Eiríkr on 2010-05-15
[size=+1]Hallelujah, a Fix![/size]

For anyone else bitten by this bug, [the Launchpad discussion](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/363695) makes it clear that a fix exists and will be incorporated into Ubuntu at some point.  For those impatient to get the fix working now, [this post](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/363695/comments/43) from the Launchpad thread includes the following:

```
#!/bin/sh

CMD=/usr/sbin/update-apt-xapian-index
IONICE=/usr/bin/ionice

# Rebuild the index
if [ -x $CMD ]
then
	if [ -x $IONICE ]
	then
		nice -n 19 $IONICE -c 3 $CMD --update --quiet
	else
		nice -n 19 $CMD --update --quiet
	fi
fi
```
Fire up your favorite text editor with [font=courier]sudo[/font], open the [font=courier]/etc/cron.weekly/apt-xapian-index[/font] file, and edit the contents to match the above.

[size=+1]What This Does[/size]

[font=courier]update-apt-xapian-index[/font] helps maintain an index of packages, and this helps speed up searching for packages in Synaptic, and possibly in other package managers as well.  

[font=courier]cron[/font] is a utility for scheduling tasks to run at certain times.  System tasks run weekly are, unsurprisingly, stored in the [font=courier]/etc/cron.weekly[/font] directory.  You can also set up personal tasks to run pretty much whenever you want.  For that, have a look at [font=courier]man crontab[/font].

Looking at the internals of the code we're using here, the first line, the "crunchbang" line (#!), tells the system what executable to use to run the contents -- in this case, [font=courier]/bin/sh[/font], or your basic **_sh_**ell.  

The next two lines establish two shorthand variables.  Variables in shell scripts are generally defined in ALL CAPS for easy readability.  This is more of a best practice than any hard-and-fast requirement.  When referenced later in the script, the variable names are prefixed with a $.  Here, [font=courier]CMD[/font] is simply shorthand for the path to the [font=courier]update-apt-xapian-index[/font] binary, and [font=courier]IONICE[/font] is shorthand for the path to the [font=courier]ionice[/font] utility for getting or setting a process's I/O scheduling class and priority.

In the [font=courier]if[/font] statements, the [font=courier]-x[/font] checks to see if the next argument exists, so [font=courier]if [ -x $CMD ][/font] will check to see if [font=courier]/usr/sbin/update-apt-xapian-index[/font] exists in the filesystem.  

[font=courier]nice -n[/font] is basically how you assign a priority to a process.  **An important caveat**, however, is that [font=courier]nice[/font] is just that -- a high [font=courier]nice[/font] value (up to a maximum of [font=courier]-n 19[/font]) means the process is nice and gets out of the way, and a low [font=courier]nice[/font] value (down to a minimum of [font=courier]-n -20[/font]) means the process is *not* nice and barges to the front of the line to be the first to use system resources.  Niceness defaults to 10 if not otherwise specified, and apparently the default [font=courier]update-apt-xapian-index[/font] setup does not specify any value.  

[font=courier]ionice[/font] is new in this fix.  It works along similar lines, affecting a process's input/output niceness, only using the flag [font=courier]-c[/font] for "class".  The [font=courier]ionice[/font] man page describes [font=courier]-c[/font]:
> **-c** _class_
The  scheduling  class. _0_ for none, _1_ for real time, _2_ for best-effort, _3_ for idle.


Finally, we have the two options passed to [font=courier]update-apt-xapian-index[/font] itself, [font=courier]--update[/font] and [font=courier]--quiet[/font].  [font=courier]--quiet[/font] just tells it to not generate much text, only outputting for fatal errors, which makes sense for a background process.  [font=courier]--update[/font] is **new** here in this fix together with the [font=courier]nice[/font] value and the [font=courier]ionice[/font] prioritization, and is a real kicker: it tells [font=courier]update-apt-xapian-index[/font] to *only update those items in the index that have actually changed*.  This seems like a no-brainer, since the index includes *every* package installed in the system, but unfortunately the default [font=courier]update-apt-xapian-index[/font] setup in a fresh install of Jaunty, Karmic, or Lucid all leave this option out, meaning that [font=courier]update-apt-xapian-index[/font] will rebuild the ENTIRE package index every time it runs.  No wonder it eats up so much memory and CPU time!  With [font=courier]--update[/font], it should take much less resources and much less time.

----------

Hope this helps, folks!

Cheers,

-- Eiríkr

---

### Post by pete_m on 2010-05-15
Hello ErikR - 
Thanks for your script - ran it successfully and the size of xapi/index1 came down by more than 20Mb.
However - the 2 big files . .termlist.DB and postlist.DB still occupy more than 90Mb.

I'm trying to keep everything including a modest /home on a single partition of 4Gb in the interest of making USB sticks of this size or less.

Under what circumstances would it be possible to zap these 2 files ? 
perhaps when no apt work is anticipated immediately prior to preparing .iso images.
or . . 

Any help with this and the related issue of minimizing disk usage would be much appreciated.


I'm an EEE PC user planning an imminent move from Karmic to Lucid  .  .
in the hope of performance improvements and the benefit of tieing in to a fresh LTS release.

i've put some work into my existing Ubuntu install based on 9.10 karmic nbr2 and am very happy with the results - full credit and thanks to all

First screenshots - more soon - of my work in progress at

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)


P.S.
 if anyone reading this knows how & when it is possible to create 'live' USB's with persistent storage from .iso images prepared with remastersys
i just started a thread about this .. [http://ubuntuforums.org/showthread.php?t=1484555](http://ubuntuforums.org/showthread.php?t=1484555)

---

### Post by scared0o0rabbit on 2010-06-22
Tagging so that I can easily find this later on.

---

### Post by klausner on 2010-06-22
> **scared0o0rabbit said:**
> Tagging so that I can easily find this later on.

You could also just use the "Thread Tools" to silently subscribe.

---

### Post by yaztromo on 2010-07-14
I just did

sudo apt-get purge apt-xapian-index

on a lucid system with no ill effects. Now my movie watching is no longer randomly paused.

---

### Post by pete_m on 2010-08-21
->  . . yes, one can just subscribe . .but it gives a sign to others on the thread that it is of interest.

->jaztromo - thanks for doing that remove sucessfully, I'll feel confident to destroy those 2 giant files when space gets tight again . .
Though isn't it likely that it was the cron'ed update process messing up your movie-viewing arbitrarily ? ( as discussed here )

---

### Post by jopakowa on 2010-09-01
Thank you very much, Eiríkr ! And for the explanations as well, I don't understand code, but it's nice to have an idea of what the solution does.

---

### Post by Selanit on 2011-02-12
A follow-up:

I was having this problem in 10.10.  I'm on a single-core system, and this sucker was rendering it unusable (not to mention roasting my lap).  But my /etc/cron.weekly/apt-xapian-index file already had the fix from earlier in the thread, and it was happening a lot more often.  It felt like daily. 

Sure enough, there's a call to update-apt-xapian-index in the file /etc/cron.daily/apt:

```
if [ -x /usr/sbin/update-apt-xapian-index ]; then
            nice ionice -c3 update-apt-xapian-index -q
        fi
```

You'll note that although it's been called using nice, they didn't set a nice value, and the xapian index bit doesn't have the --update option.  Grargh!

It should read:

```
if [ -x /usr/sbin/update-apt-xapian-index ]; then
            nice -n 19 ionice -c3 update-apt-xapian-index --update -q
        fi
```

Just a note for future sufferers.  Sorry to necro the thread.

---

### Post by space_agent on 2011-04-03
@Selanit: 
Thanks for giving the additional information ! Actually it does not matter how old the thread is as long as the information you provide is good and it is in this case.

@Eiríkr:
Thank you for the good explanations, very useful.

---

### Post by helpdeskdan on 2011-05-01
I'll be danged - I knew it was running from someplace else.  Thanks.

---

### Post by prioritythinking on 2011-05-09
[Eiríkr]("http://ubuntuforums.org/member.php?u=468055") Thank you works great ! My 11.04 was almost unusable after update .  slow ,freezing , choppy video hulu . cpu was at 90 %

---

### Post by Ekevoo on 2011-06-01
Thanks Selanit! I was having the same problem but it's now fixed! :)

---

### Post by theDaveTheRave on 2011-06-06
Thanks guys.

I had this problem some time back and it re-occured?? so I've re-issued the required fix.

I'm running lucid (on LXDE)
```

uname -a
Linux Dartagnon 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011 i686 GNU/Linux

```

If I get further problem I'll obviously come back to this thread.

David.

ps. it seems that the update is still going on in the background, but at least it isn't holding up everything else now!

I don't know if it is related but I don't get notification from the update manager anymore, more likely an lxde problem though.

---

### Post by kowsik on 2011-08-30
Thank you Elikir for the fix and for the nice explanation.

---

### Post by gerymate on 2011-11-14
It's still an issue in Ubuntu 11.10. The proposed solutions in this thread (#8 and #15) hopefully will help; thanks!

---

### Post by Emblem Parade on 2011-11-21
There is an open bug on this for Oneiric:

[https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/830333](https://bugs.launchpad.net/ubuntu/+source/apt-xapian-index/+bug/830333)

I've added information about Selanit's fix.

---

### Post by soldar79 on 2012-03-07
Excellent!

it should be the way you explained by default. Thx!

---

### Post by Dumpy Dumpster on 2012-04-10
Thank you Eiríkr.  I used your solution from post #8 and my problem has been solved.
Thanks also Selanit, I went on to incorporate your fix in post #15.

---

### Post by John Peterson on 2012-04-25
It runs at low priority (PR 39, NI 19) but it still seems to make other tasks slower.
```
user@ubuntu32:~$ top
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
25102 root      39  19  245m 229m 4420 D 39.8 46.3   2:29.87 update-apt-xapi
user@ubuntu32:~$ cat /etc/issue
Ubuntu 11.10 \n \l
```

---

### Post by jfmxl on 2012-07-21
I note this is TWO YEARS  - 11.10, and 12.04 is out - after this posting and I have just typed in the "fix", if it is one, for the problem of ubuntu crippling my machine ... literally making it unusable.

I hope this works.

---

### Post by Statia on 2012-10-01
> **jfmxl said:**
> I note this is TWO YEARS  - 11.10, and 12.04 is out - after this posting and I have just typed in the "fix", if it is one, for the problem of ubuntu crippling my machine ... literally making it unusable.

I hope this works.

Yes, it is telling that a two year old bug that is well known and so easy to fix is still present.
I was reading up on this and came across this thread, checked my /etc/cron.daily/apt and yes:

 ```
if [ -x /usr/sbin/update-apt-xapian-index ]; then
            nice ionice -c3 update-apt-xapian-index -q -u
```Still no nice value. They did add the -u switch however, I'm assuming that -q -u equals --quiet --update.

---

### Post by Agent24 on 2012-10-01
I have not yet noticed the problem with either Xubuntu or Lubuntu.

---

