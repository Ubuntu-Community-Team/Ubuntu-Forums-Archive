---
title: "A couple of Linux/Ubuntu question"
date: 2005-05-19
forum: Desktop Environments
---

### Post by gopha on 2005-05-19
Well, I finally decided to give Linux a try (again) and installed it on my laptop (thinkpad). Even though everything works alot better then 1 1/2 years ago when last tried linux, there's still some things I'm not too happy about. Please bare with me, some may be really "newbie-like" ;-)

1) I'm used to windows mouse acceleration, or the lack of it, and the sensitivity I use there, so naturally I'd like to use the same in linux. I already figured how to get rid of the annoying mouse acceleration (xset m 1), but I can't seem to figure out how to increase the speed without getting the mouse acceleration back.

2) How do I access my trackpoint/touchpad settings (they are recognized and work without a problem)

3) How do I undervolt my cpu and set the multiplier it should use? Something like Centrino hardware control, but for linux would be great.

4) How can I change the action assigned to my 4th & 5th mouse button (MS Intelli Explorer 3.0)?

5) What's the command to view once cpu speed? ;)

6) Is there a tool to "play" around with the harddrive settings, like having it spin down faster and things like that?

7) And the last question, for tonight at least: How can I access debians packages? mc for example isn't available on the ubuntu one.

In case you need the system specs:

Thinkpad T40
P M 1.5 Ghz (Banias)
2x512 MB RAM
Radeon 7500
WD Scorpio (60 Gb, 5400 rpm)
Ubuntu 5.04

Thanks guys :-)

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=gopha]
7) And the last question, for tonight at least: How can I access debians packages? mc for example isn't available on the ubuntu one.

[/QUOTE]

I can answer this question:

[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

But be careful installing Debian packages, they might not work. If Sid has something you need (never use Sarge) then kindly ask for a backport.


As I said in the welcome letter, anyone with previous Linux experiance needs to post in the other parts of the forums. Please do not be offended that I moved this.

---

### Post by shof2k on 2005-05-20
5) type **more /proc/cpuinfo** in a terminal

---

### Post by Woocash on 2005-05-20
search for topic about ThinkPad T42 on this forum -- there's no big different...

---

### Post by gopha on 2005-05-20
[QUOTE=Woocash]search for topic about ThinkPad T42 on this forum -- there's no big different...[/QUOTE]
 Thanks guys :)

poofyhairguy: Nah, I just figured it fit better into the beginners section. But this works too ;)

[edit] 

After I did some more searching, I'm stuck with some other problems ;)

- cat /proc/acpi/thermal_zone/THRM/temperature is supposed to tell me the temperature of my cpu, at least according to other posts. I don't got the THRM folder though, its THMO and it only gives me an error ("command not found"). 

- Seems my cpu is clocking itself down automatically, which is good. I'd like to set the steps myself though, where can I do this?

- Can't find anything regarding the trackpoint, after looking thourgh endless posts /:

---

### Post by gopha on 2005-05-20
[edit] After reading the manpage for xset I'm kind of confused. If I understood it correctly, there's now way in hell to increase the speed of the mousemovement? I can only change how much faster it goes when I move the mouse more than x pixels?!

---

### Post by tdell on 2005-05-20
Just click on System>Preferences>Mouse>Motion move the slide bars to your preference.

Tom

---

### Post by gopha on 2005-05-20
[QUOTE=tdell]Just click on System>Preferences>Mouse>Motion move the slide bars to your preference.

Tom[/QUOTE]

Which like I said enables the mouse acceleration :%

---

### Post by Grue on 2005-05-20
> **gopha]

4) How can I change the action assigned to my 4th & 5th mouse button (MS Intelli Explorer 3.0)?
[/QUOTE]

Take a look at [this](http://www.ubuntuforums.org/showthread.php?t=28374) thread.

[quote]
5) What's the command to view once cpu speed?  said:**
> 

There is a GNOME applet for exactly that. Right-click on a GNOME bar and choose 'add applet', and there is a CPU Freq Monitor. It's a great applet for laptops :).

[quote]
6) Is there a tool to "play" around with the harddrive settings, like having it spin down faster and things like that?


Have a look at HDparm and [google](http://www.google.com/search?q=hdparm%20hdd%20spin-down) a bit. Beware though. If used incorrectly, hardware could fry, and I'm not taking any responsibility (you have been warned :)). IMO Ubuntu's settings for HDD spin-down are fine on my laptop, but YMMW.

---

### Post by gopha on 2005-05-20
Thanks alot Grue :)

Now the only problem that remains is that with the mouse speed. I'll sum it up again:

When I use the bars in the mouseoptions (system - options - mouse) I'm stuck with mouse acceleration and can't get rid of it. If I disable it with xset m 1 1 the second bar ("mouse sensitivity") doesn't work, but changing the position of the first one gets back that damn mouse acceleration. Right now there's simply no way for me to increase my mouse speed without mouse acceleration.

Thanks for your support so far, good night / morning ;-)

---

### Post by Grue on 2005-05-21
I'm glad I was of help :)

About your mouse problem, try looking [here](http://forums.gentoo.org/viewtopic.php?t=8398) or maybe [here](http://www.google.com/search?hl=en&lr=&q=site%3Aforums.gentoo.org+%22mouse+acceleration%22&btnG=Search).

And night to you too ;).

---

### Post by mohaham on 2005-05-21
[QUOTE=gopha]
- cat /proc/acpi/thermal_zone/THRM/temperature is supposed to tell me the temperature of my cpu, at least according to other posts. I don't got the THRM folder though, its THMO and it only gives me an error ("command not found"). 
 /:[/QUOTE]

You may want to check out this tool:
gkrellm

to install type:(u may need to enable the debian-marillat repositories)
apt-get install gkrellm

this GUI tools shows extensive info about ur CPU like temp., frequency, etc..

---

### Post by stevenyu on 2005-05-21
just install the lm-sensor

**sudo apt-get install lm-sensor**

and run sudo **sensors-detect**

then you can use the gkrellm to monitor all the values. :smile:

---

### Post by gopha on 2005-05-21
Great, those links / postings helped me alot.

I'm not too sure if that "mouseaccelerationthing" changed in the last couple of years (the threads where from 02/03), but if not, then I guess my only chance of getting what I want is to hope that playing around with the mouse resolution helps :/ It would really be a bummer though, since I enjoyed Ubuntu a lot so far, it's better than Windows in every single way. Well, except mousemovement that is :p

[edit] Uhm :D 

xset 3 0 = mouse acceleration
xset 3 1 = no mouse acceleration

Makes no sense to me, but what do I care. The only thing that matters is that I finally can use the mouse under linux without getting a cramp. Thanks again guys, I'm sure I'll find more "problems" as I go *g*

---

### Post by gopha on 2005-05-21
Alright, here I go again ;)

1) [edit] done

2) Where do I change how my cpu "behaves" under load? Currently, as soon as I start an app lication, my clock frequency goes up to 1.5 Ghz and then gradually goes down to 600 Mhz again. I'd like to have it running at 600 Mhz all the time though ;)

3) Can I use Superkaramba with Gnome? Theres simply more good widgets for Superkaramba than there is for gdesklets (imo). Or can I setup KDE to look like Gnome (The standard Ubuntustyle ;) I don't like the standard KDE one, that comes with Kubuntu).

4) I'm getting an "setting sensor limits: failed" during the bootphase, how can I solve it?

---

### Post by gopha on 2005-05-22
[edit] Oops, wrong button.

---

### Post by Grue on 2005-05-22
> **gopha]Alright, here I go again  said:**
> 

Can't help you there mate. On my laptop it's a BIOS setting

> 
3) Can I use Superkaramba with Gnome? Theres simply more good widgets for Superkaramba than there is for gdesklets (imo). Or can I setup KDE to look like Gnome (The standard Ubuntustyle ;) I don't like the standard KDE one, that comes with Kubuntu).


You can see a screenshot of Kubuntu in action [here](http://lwn.net/images/ns/kubuntu.png). It's not the Ubuntu Human theme, but have a look at [http://kdelook.org](http://kdelook.org) and see if there's something nice there. 

About Superkaramba. Why not just try? Can't really do any damage :). 

[quote]
4) I'm getting an "setting sensor limits: failed" during the bootphase, how can I solve it?


Try doing a ```
sensors-detect
``` in a shell and see if that helps. If not, I'm clueless, and you need another one to answer that :).

---

### Post by Seth on 2005-05-22
I have to say, running Kubuntu would solve using SuperKaramba and throttling your CPU all in one swoop.

---

### Post by gopha on 2005-05-23
[QUOTE=Grue]Try doing a ```
sensors-detect
``` in a shell and see if that helps. If not, I'm clueless, and you need another one to answer that :).[/QUOTE]

IF THIS IS AN IBM THINKPAD, PRESS CTRL-C NOW!
 IBM Thinkpads have a severely broken i2c/SMBus implementation, just scanning
 the bus will break your Thinkpad forever!

;-o

---

### Post by angkor on 2005-05-23
[QUOTE=gopha]IF THIS IS AN IBM THINKPAD, PRESS CTRL-C NOW!
 IBM Thinkpads have a severely broken i2c/SMBus implementation, just scanning
 the bus will break your Thinkpad forever!

;-o[/QUOTE]

 :grin: Yeah I remember getting that message...Must have made your heart skip ;)

The dude recommending lm-sensors should have read your first post better.

---

### Post by gopha on 2005-05-23
[QUOTE=angkor]:grin: Yeah I remember getting that message...Must have made your heart skip ;)

The dude recommending lm-sensors should have read your first post better.[/QUOTE]

Yah, especially since the first thing I read was that question about loading the module and "YES/no". So, unpatient like I am, I first typed yes and then read the rest. Oh well, stopped in time before the second one ;)

By the way, I did solve my "cpu throttling" problem pretty much by using powernowd's passive mode paired with a lower limit of 85 and an upper limit of 95. Now there's only that undervolting part left :)

[edit] Does anyone know how I can underclock my ATI-Card?

---

### Post by angkor on 2005-05-23
[QUOTE=gopha]Yah, especially since the first thing I read was that question about loading the module and "YES/no". So, unpatient like I am, I first typed yes and then read the rest. Oh well, stopped in time before the second one ;)[/QUOTE]

:-) Pfew, lucky you, sounds exactly what would have happened to me.

---

### Post by Grue on 2005-05-24
Gopha:

Wow, I'm sorry man. Didn't know Thinkpad had that problem. I'm glad nothing happened, and you didn't break your laptop for ever.

Good thing it put out a warning.

Again, I'm truely sorry.

---

### Post by gopha on 2005-05-25
[QUOTE=Grue]Gopha:

Wow, I'm sorry man. Didn't know Thinkpad had that problem. I'm glad nothing happened, and you didn't break your laptop for ever.

Good thing it put out a warning.

Again, I'm truely sorry.[/QUOTE]
 No problem mate :-)

I'm back with another problem though. I'm trying to install superkaramba, but it's telling me it's missing qt. I'm not sure which package to install though , since synaptics is showing me alot of different ones.

Here's the errormessage;

[i]checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.[/i]

Also I get a problem with "tpb": When I try to launch it, it's telling me it can't access /dev/misc/nvram, because the folder/file doest not exist.

[edit] And yet another problem: I'm trying to install adesklets, but can't get past the configure point: It stops with an error, telling me it can't find the python include dir, even though it detects the rest just fine:
[i]
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for Python include path...
configure: error: cannot find Python include path
[/i]

Any help would be greatly apreciated.

---

