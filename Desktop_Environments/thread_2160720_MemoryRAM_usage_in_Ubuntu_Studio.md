---
title: "Memory/RAM usage in Ubuntu Studio"
date: 2013-07-08
forum: Desktop Environments
---

### Post by su:bhatta on 2013-07-08
Hi, I am using Ubuntu Studio 13.04 which comes with the lightweight Xfce DE....
Now my concern is, the system takes quite some time to boot up.. my vanilla Ubuntu used to boot faster...

I would like to mention I hav my Home Directory encrypted, I am guessing that mounting the said Volume takes up time...
Also my memory/RAM usage when no applications are open r in the range of 400~450 MB...(my available RAM is 3430MB)

That is not lightweight... I checked out in xfce forums, people get machines runnin at 130-200 MB...

Does Ubuntu Studio use more Ram? 
I hav a screenShot of the Session StartUp applications attached...
[ATTACH=CONFIG]244501[/ATTACH]
any light in the subject is welcome...

---

### Post by ohnonot on 2013-07-09
in my opinion xfce is medium-weight, not lightweight.
but yes, 400+ MB seems too much.
open task manager and see what takes so much ram.

for your screenshot:

depends what you need and want, but you can uncheck dropbox, f.lux, pidgin, screensaver, ubuntuOne, updatenotifier, zeitgeist.

[explanation:
if you uncheck your screensaver your power manager takes care of screen blanking, so make sure it is set up to your liking
if you uncheck update notifier you should update before you install new software]

if you don't use bluetooth, uncheck that, too.

see if that helps.
i have ubuntu studio installed, i can boot into it and see how it runs on my machine.

ps: maybe the LTS version would be better

---

### Post by snowpine on 2013-07-09
It doesn't matter what your RAM usage is; it only matters the %. Your RAM is at only 13% so there is no problem; you still have 87% free. :)

[http://linuxatemyram.com](http://linuxatemyram.com)

I can't help you with your bootup time, except to say, it is not something I worry much about personally, since I only turn my computer on once per day a few extra seconds don't matter to me. :)

---

### Post by su:bhatta on 2013-07-10
> **ohnonot said:**
> in my opinion xfce is medium-weight, not lightweight.
but yes, 400+ MB seems too much.
open task manager and see what takes so much ram.

for your screenshot:
depends what you need and want, but you can uncheck dropbox, f.lux, pidgin, screensaver, ubuntuOne, updatenotifier, zeitgeist.


ps: maybe the LTS version would be better

Thanks for the suggestions: i have unchecked the following:
Bluetooth,Dropbox,Pidgin,UbuntuOne,Zeitgeist(I have no clue what zeitgeist does)

I am attaching a screenshot of the taskmanager, i hav no clue about half the processes running....

Also, since 14.04 is so near(i am a optimist) so i thought i will bide my time & wait for it...

I was previously using ElementaryOS & Ubuntu vanilla on this machine & while Ubuntu was fast, ElementaryOS was blitzkrieg....

Can my panel, which has nearly 15 launchers & all indicator plugins, been eating my ram away?

[ATTACH=CONFIG]244581[/ATTACH]

---

### Post by su:bhatta on 2013-07-10
> **snowpine said:**
> It doesn't matter what your RAM usage is; it only matters the %. Your RAM is at only 13% so there is no problem; you still have 87% free. :)

[http://linuxatemyram.com](http://linuxatemyram.com)

I can't help you with your bootup time, except to say, it is not something I worry much about personally, since I only turn my computer on once per day a few extra seconds don't matter to me. :)

Thanks for the great link, didn't know half of those....

But you see, I plan on recording audio in this UStudio install, and my concern is if a clean system is using 450 odd MB, then maybe when i try to record there will be many dropouts while recording...

I also bootup once maybe in 2-3 days, so even an extra minute is never a problem, but as i said in my earlier post, Ubuntu vanilla used to boot faster, and elementaryOS was Very fast... hence the concern...

---

### Post by ohnonot on 2013-07-10
about your screenshot:
since you are worried about memory consumption, you have to make it visible in the task manager. in preferences there must be sth like choose columns, there you should choose all ram/mem related.

i tend to agree with snowpine - take a look at the webpage. it's telling the truth. read it closely, compare it to what your task manager shows.
try the 'free' command in a terminal.
you could also try the [little program](http://www.linuxatemyram.com/play.html).

about startup time, how long does it take in absolute terms and what kind of cpu do you have?

generally, just try things out. close all other applications before starting to record. take a look at other linux multimedia studio solutions. 
you can also: create a few 10-20GB partitions on your hd and one big partition for all the data. then you can install various systems and try them out.
i have good experiences with [AVLinux](http://www.bandshed.net/AVLinux.html).

---

### Post by su:bhatta on 2013-07-10
Thanks for the AVLinux link.... surely am going to check that out....
As for my partitions, I have only 3, One 45 GB for Win8, another 40GB(36GB for / + 4GB for swap) for Ubuntu Studio, rest 388GB for data alone...
I have a AMD A4 Vision GPU & in absolute terms it takes 30 secs from when I enter my password to the system being ready for use...

My only concern is dropouts in case i try to record something, otherwise I have no problems...

Will AVLinux give a fresh GRUB to choose OS at bootup? I am only asking because I had a bad experience with Solaris, which does not recognize any other Linux OS and doesn't show them at options at startup...
Anyways will look at AVLinux & maybe install it too...

---

### Post by ohnonot on 2013-07-10
> **bhattabhishek said:**
> 40GB(36GB for / + 4GB for swap) for Ubuntu Studio, rest 388GB for data alone...
...
I have a AMD A4 Vision GPU & in absolute terms it takes 30 secs from when I enter my password to the system being ready for use...
...
Will AVLinux give a fresh GRUB to choose OS at bootup?
you could halve the partition and install both ubuntu studio & avlinux. actually avlinux should be happy with much less than 10GB.
...
i don't know what amd a4 vision is. i was asking for actual GHz and number of cpu's.
the username/password from ubuntu's display manager? or some bios password?
...
i don't remember the avlinux installation process anymore. if it gives you an option to NOT install grub, choose that and make a grub update from ubuntu studio.
if it doesn't and you can't boot anything else anymore, it's not a big thing, just call back here.

ps: 
resizing partitions takes ages and i don't recommend it! if you choose what i suggested, it's probably easier to delete that partition, create 2 smaller ones instead, reinstall ubuntu studio from scratch. and whatever else you choose to install.
also, your swap probably won't be recognized anymore. but no worries, that's an easy one.

also have a look here: [http://wiki.linuxaudio.org/apps/categories/distributions](http://wiki.linuxaudio.org/apps/categories/distributions)

---

### Post by su:bhatta on 2013-07-10
Hi, i just stopwatched it at 28 secs from giving Xfce log in /password...
AMD A4 dual core 1.8 Ghz processor, & from what i read up at AMD , it automatically overclocks to 2.5Ghz...

Once the grub fails i hav no other option to call u here :) 

thatz my problem, this is my only laptop, i am a underfed entrepreneur... & gettin things done on a shoestring budget mate ;)

---

### Post by snowpine on 2013-07-10
Are you actually having recording dropouts, or are you just worried that you might? The first is much easier to help you troubleshoot than the latter. ;)

When I used to do recording stuff, I installed the lightweight Fluxbox windows manager and used that for best performance. Gnome was installed too, and I used that for ease-of-use for everyday non-recording tasks.

---

### Post by su:bhatta on 2013-07-10
haven't recorded yet, but there will be recordings in ardour this saturday... 
once i am playing then i wont be really accessin the forums for a fix, hence the concern....;)

---

