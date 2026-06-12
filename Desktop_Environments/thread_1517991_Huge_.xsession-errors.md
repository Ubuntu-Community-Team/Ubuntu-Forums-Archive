---
title: "Huge .xsession-errors"
date: 2010-06-25
forum: Desktop Environments
---

### Post by yvsong on 2010-06-25
Hi,

Just deleted my ~/.xsession-errors bigger than 8G bytes. The new file keeps growing by appending the "fDischargeMeanRate" message. What's happening?

(Linux  2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux)

---

### Post by Zorael on 2010-06-26
As a workaround, you could make a startup script that deletes the file and makes a symbolic link to **/dev/null**, effectively discarding everything written to it.

```
#!/bin/bash

rm ~/.xsession-errors
ln -s /dev/null ~/.xsession-errors
```

Obviously, by doing this you opt out of any interesting tidbits that may be output to there. I found that the only error logs I really ended up reading were **/var/log/Xorg.0.log*{.old}*** and **/var/log/kdm.log** anyway.

---

### Post by Phkillah on 2011-08-22
> **Zorael said:**
> As a workaround, you could make a startup script that deletes the file and makes a symbolic link to **/dev/null**, effectively discarding everything written to it.

```
#!/bin/bash

rm ~/.xsession-errors
ln -s /dev/null ~/.xsession-errors
```

Obviously, by doing this you opt out of any interesting tidbits that may be output to there. I found that the only error logs I really ended up reading were **/var/log/Xorg.0.log*{.old}*** and **/var/log/kdm.log** anyway.


Awesome.
Thanks.
Just deleted a 17.3G xsession-errors file..... doh..

---

### Post by beijbom on 2011-10-31
Hi all, 

I'm having the same problem but mutated and even ugglier. 

Following the suggested workaround I instead got a huge .xsession-errors[jumble of letters].

When I noticed this, I simply deleted the file, and then modified the script to say rm ~/.xsession-errors*.

Alas, what is happening now is that that same file is being created, at least sort of. If I do

lsof | awk '{print $7 $9}' | sort -nr | less

the top 20 hits are that very same (huge) file, with identical inode numbers. 

Needless to day a df call tells me the drive if full, but a search with sudo du -shx at the root tells me ~23 Gb used (out of 100 Gb). Oh, and a restart solves the problem temporarily. The only programs I'm running are matlab and chrome. The pace of which the used portion of the drive (as revealed by df) increases significantly once I start running these.

At this point, I'm quite in despair. Any suggestions would be useful.

---

### Post by bugssoren on 2011-11-05
Had the same problem with 11GB .xsession-errors. Fixed it with a solution I found to disable the recent history too.

rm .xsession-errors
touch .xsession-errors
sudo chattr -i .xsession-errors

Simply delete the file. Create an empty file. Set the immutable attribute. Which makes the file protected against writing and deleting. Nothing can be logged.

Note that until you logout the file space deleted is not unallocated because the file is being held open.

---

### Post by benemorius on 2012-01-17
> **bugssoren said:**
> 
Note that until you logout the file space deleted is not unallocated because the file is being held open.

Thanks for the heads up. I was able to avoid that unpleasantness by truncating the file (echo > ~/.xsession-errors) rather than deleting it. Mine was 119GB. Do I win a prize?:D

---

### Post by dannield on 2012-01-18
nope... 850GB on my machine

---

### Post by IOException on 2012-02-01
I seems I've got the second place with 375G .xsession-errors :)

---

### Post by vikketorr on 2012-02-06
The only way I've gotten it to stop growing it putting it in the recycle bin manually. A simple rm doesn't work as the file is kept open and keeps on growing. I'm running the Linux Spotify client which causes a tremendous amount of errors.

---

### Post by steve8track on 2012-03-08
I'm sorry, but I just had to report this, as I think I'm currently the second place in this thread: 609GB

---

### Post by Zorael on 2012-03-10
As a more system-wide solution, instead of symlinking the .xsession-errors file in your home directory to **/dev/null** (and possibly writing a startup script to re-symlink it if something keeps recreating it as a normal text file), you could change where the log is written to in the first place in **/etc/X11/Xsession**. That file will be overwritten upon updates to the **x11-common** package, mind.

Excerpt from line ~50 or so (11.10);
```
# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession
**ERRFILE=$HOME/.xsession-errors**
```
If you change the **ERRFILE** line to instead point to **/dev/null**, it will discard the log entirely. If you point it to a file in **/tmp/** the log will be accessible there if you suddenly need it, but get deleted upon rebooting.
```
ERRFILE=**/dev/null**
*# or*
ERRFILE=**/tmp/$USER-xsession-errors**
```

The good news is that the behavior changes in 12.04 precise to save it thusly in /tmp/. It still logs *insane* amounts of errors there, but at least the file gets purged every now and then depending on your shutdown/reboot frequency.

Mine is nearly a megabyte after an update of ~7 days. Most of the entries are Gtk/Gdk/GLib warnings, Qt4 QPainter spam and X Bad{Value,Drawable,Window} errors; none of which are a whit of interest to me.

Implied by this is that the drive gets touched and written to regularly. That's inarguably insignificant to most, but if you're on a laptop (that wants to conserve power by limiting drive activity) and/or using an SSD (to which you want to limit your amount of writes anyway), you may want to consider to just take the /dev/null approach -- or mount your /tmp as **tmpfs** and point your log there.

---

### Post by summentier on 2012-03-12
A word of warning: **Do not delete** a huge .xsession-errors (or any logfile running out of bounds and filling up your diskspace, for that matter) **with rm**:
```
rm ~/.xsession-errors   # DO NOT DO THAT - file will linger on
```This will not give you back any diskspace, since the file is still connected (via internal file descriptors) to the processes writing to them (like x-session). It is better to truncate the file by issuing:
```
truncate --size=0 ~/.xsession-errors
```This *will* take some time for large files, but it will free up the disk space eventually. Afterwards, you'll probably want to find the culprit (knotify4 is one candidate on Kubuntu 11.10).

If you, by accident, already rm'ed the file, then there are two ways to fix this:

[LIST]
[*]Reboot your PC -- this will usually trigger a file system check and will remove the dangling inodes
[*]If this is not an option, follow the instructions on [http://glandium.org/blog/?p=211](http://glandium.org/blog/?p=211) : you will essentially have to find out the internal file descriptor and truncate the underlying file:
```
lsof +L1 | grep -m 1 $HOME/.xsession-errors

# Truncates the internal file: replace <PID> with the first number and <FD> with
# the second number of the output above
truncate --size=0 /proc/<PID>/fd/<FD>
```Do not forget to find the process that is filling up your .xsession-errors afterwards!
[/LIST]

---

### Post by biocyberman on 2012-04-01
Thanks summentier for your insights. 

@All: It's nothing to be proud of, however I need to let you know: I got a 4.6TB .xsession-errors :lolflag: 
This monster literally ate up my RAID volume.

---

### Post by chitowner2 on 2012-04-06
Wow, guess I'm a piker by comparison, mine never got over 10G, but my /home is only 25G. 

I gotta wonder what the heck kind of filesystem somebody has that lets .xsession-errors get >100G. Isn't this file always in /home?

Some nice tips here to constrain this disk-***** file, but it would be cool if somebody has an idea to make it scroll somehow, so that after say 1000 lines, older stuff gets deleted. That way the purpose of the file remains relatively intact w/o growing astronomically.

CT

---

### Post by chitowner2 on 2012-04-06
> **biocyberman said:**
> Thanks summentier for your insights. 

@All: It's nothing to be proud of, however I need to let you know: I got a 4.6TB .xsession-errors :lolflag: 
This monster literally ate up my RAID volume.


I see you are a fan of large FS's. I have a couple LVM's ~3T and one ~5.6T, the last has an installed base of 12T available, so it's less than half full, but I get no problems with .xsession-errors on that box, and if I did, /home is only 12G.

CT

---

### Post by Rosuav on 2012-04-26
Well, I'm joining the competition with a 719GB file that would have been bigger except that the volume it was on was only 1TB. Many thanks for the info, especially on truncating after rm (which is exactly what I'd done).

Just one small issue left. I, uhh, toasted my Xsession - by attempting a 'sudo -e' to set it to log to /dev/null, while the disk was full. Is it safe to copy /etc/X11/Xsession from one Ubuntu 10.10 to another?

I think this may be urgent in that my system might not come up again if it reboots now. Hopefully I won't reboot...

---

### Post by Krytarik on 2012-04-26
> **Rosuav said:**
> I, uhh, toasted my Xsession - by attempting a 'sudo -e' to set it to log to /dev/null, while the disk was full. Is it safe to copy /etc/X11/Xsession from one Ubuntu 10.10 to another?
Yeah, sure, you can also pull the default one from here - just open the deb package with Archive Manager, for example:

[http://packages.ubuntu.com/maverick-updates/x11-common](http://packages.ubuntu.com/maverick-updates/x11-common)

Regards.

---

### Post by Rosuav on 2012-04-26
> **Krytarik said:**
> Yeah, sure, you can also pull the default one from here - just open the deb package with Archive Manager, for example:

[http://packages.ubuntu.com/maverick-updates/x11-common](http://packages.ubuntu.com/maverick-updates/x11-common)

Regards.

Thanks! X is such a huge thing that I can never be sure which parts are specific to my video card (etc) and which parts are safely customizeable.

Especially appreciate the fast response. Thank you!

---

### Post by JigglyWiggly_ on 2012-06-01
Someone have the best solution? All of them seem kinda meh.

On 10.04 atm.

---

### Post by jars99 on 2012-06-13
Mine got up to 90GB on my 128GB SSD today.
Could you use logrotate to automatically move the file once it gets over a certain size?

---

### Post by tonig on 2012-06-20
this works for me

rm ~/.xsession-errors
touch ~/.xsession-errors
sudo chattr +i ~/.xsession-errors


[http://ubuntuforums.org/showthread.php?t=1946716](http://ubuntuforums.org/showthread.php?t=1946716)

---

### Post by weaselman on 2012-09-05
Do not rm ~/.xsession-errors!
The processes that have it open will hang on to it, and keep writing, and eating up your disk space.
Linking to /dev/null seems to help for a while, but then something seems to recreate the damn file!
I tried many different ways, and here is what worked:


sudo echo "*/1 * * * * $USER echo>$HOME/.xsession-errors" > /etc/cron.d/truncate-stupid-xerr

The stupid thing was eating like a GIGABYTE per minute. Now it is under control.

---

### Post by SantaFe on 2012-09-05
I'm Using Xubuntu 12.04/ Xfce 4.8 and am wondering what did I do wrong?  I tried what you said here:
```
# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession
ERRFILE=/dev/null

```

I then deleted the .xsession-errors file by right clicking & clicking delete.  I then rebooted.  After it booted, I opened Thunar & a new one was generated.

Did I type it wrong? ;)


Whoops, didn't see the post just above me when I replied.  Still would like to know why it doesn't seem to work for me though. ;)

---

### Post by SantaFe on 2012-09-05
> **weaselman said:**
> Do not rm ~/.xsession-errors!
The processes that have it open will hang on to it, and keep writing, and eating up your disk space.
Linking to /dev/null seems to help for a while, but then something seems to recreate the damn file!
I tried many different ways, and here is what worked:


sudo echo "*/1 * * * * $USER echo>$HOME/.xsession-errors" > /etc/cron.d/truncate-stupid-xerr

The stupid thing was eating like a GIGABYTE per minute. Now it is under control.

Tried that, assumed you meant for me to replace USER with my user name.  Got "bash: /etc/cron.d/truncate-stupid-xerr: Permission denied" back in Thunar.  Even tried it unchanged, got the same error message. ;)

---

### Post by weaselman on 2012-09-06
> **SantaFe said:**
> Tried that, assumed you meant for me to replace USER with my user name.  Got "bash: /etc/cron.d/truncate-stupid-xerr: Permission denied" back in Thunar.  Even tried it unchanged, got the same error message. ;)
Hm. You didn't forget the "sudo" in the beginning of the command, did you?
$USER is a shell variable, that is automatically set to your username. You don't need to replace it with anything, just make sure you don't miss the dollar sign. Same goes for $HOME (that would be your home directory).

---

### Post by SantaFe on 2012-09-06
Nope, I highlighted the whole line and opened the Xfce terminal & pasted it.  Then when I hit enter got the above text.

---

### Post by LucidREM on 2012-10-10
this was very good info .. i found this hidden file in my home directory and was shocked at the size .. i delegated 100GB to my linux partition and somehow 82GB was taken by ~/. and the xsession-errors was 80GB of that .. whew ! what a relief .. there was no way i was occupying 99% of the drive as there are NO media files (photos, videos, music, etc) at all on the linux partition

---

### Post by ginsujim on 2012-10-10
.

---

### Post by LewisTM on 2012-10-10
> **weaselman said:**
> Do not rm ~/.xsession-errors!
The processes that have it open will hang on to it, and keep writing, and eating up your disk space.
You CAN rm the file if you replace it with an immutable block of granite which is what the [FONT="Courier New"]sudo chattr +i [/FONT]command does. Nothing can write to an immutable file.

---

### Post by mons00n on 2012-10-12
will the chattr command work if I already rm'd the file and created a new blank one?  I also redirected the error output to /dev/null yet I'm still getting a full hard drive, and lsof returns this:

```
bob@Newton:~$ lsof |grep -i deleted
gnome-ses 2686           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
gnome-set 2736           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
gsd-print 2753           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
metacity  2755           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
gnome-pan 2771           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
nm-applet 2779           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
bluetooth 2780           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
polkit-gn 2781           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
nautilus  2782           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
vino-serv 2786           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
gnome-fal 2793           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
dropbox   2809           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
dropbox   2809           bob    3u      REG               8,49           0  270905 /tmp/tmpfP0B-G (deleted)
gdu-notif 3028           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
telepathy 3031           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
gnome-scr 3039           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
zeitgeist 3040           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
update-no 3098           bob    2w      REG               8,49 19870789632 1841695 /home/bob/.xsession-errors (deleted)
```

Even when the hard drive is full the .xsession-errors file has no size...so it seems to be creating this file irregardless of the current empty .xsessions-file.  This problem is really annoying because it stops all server processes that have to write to a log file (apache, mumble, VNC...etc etc).

---

### Post by LewisTM on 2012-10-12
You have to logout or reboot for the change to take effect. Open files have to be closed.
Another tip:
Instead of using the [FONT="Courier New"]sudo chattr +i[/FONT] command, just run this:
```
rm ~/.xsession-errors
mkdir ~/.xsession-errors
```
You can't 'write' data to a dir entry so you get the same result but no need for sudo.

Cheers!

---

### Post by mons00n on 2012-10-12
> **LewisTM said:**
> You have to logout or reboot for the change to take effect. Open files have to be closed.
Another tip:
Instead of using the [FONT="Courier New"]sudo chattr +i[/FONT] command, just run this:
```
rm ~/.xsession-errors
mkdir ~/.xsession-errors
```
You can't 'write' data to a dir entry so you get the same result but no need for sudo.

Cheers!

Yea I have been rebooting whenever this happens.  It is totally random so I have no idea what causes it.  Thanks for the tip, I've already tried the chattr command so we'll see if it works.

---

### Post by fgr on 2013-01-09
tried this??

I did, but I can not say if it made an changes, cause first I made the .xsession-erros file immuteable (few posts before)

[http://wiki.ubuntuusers.de/Baustelle/xsession-errors](http://wiki.ubuntuusers.de/Baustelle/xsession-errors)

---

### Post by jzarob on 2013-03-10
I succeeded in getting the file back down to normal size (or non existent at all) by reinstalling compiz-core. 
Just run the following command in the terminal to reinstall the compiz-core files:
```
[FONT=courier new]sudo apt-get install --reinstall compiz-core[/FONT]
```

---

### Post by jreed69 on 2013-06-10
> **jars99 said:**
> Mine got up to 90GB on my 128GB SSD today.
Could you use logrotate to automatically move the file once it gets over a certain size?

I added [COLOR=#000000]xsession-errors  [/COLOR]to /etc/logrotate.d :

/home/user/.xsession-errors
{
rotate 3
size 100M
missingok
not if empty
compress
}
[URL="http://linux.die.net/man/8/logrotate"]
http://linux.die.net/man/8/logrotate[/URL]

---

### Post by Timothy_Sesow on 2013-10-11
Here's a simple thing that caused my .xsession-errors file to grow out of control.
Vino-server was turned on in one of my desktop systems and configure with uPNP
to allow outside VNC requests.  I notice a brute force attack on the desktop (I had
a good password), and the log fills with the invalid attempts to connect to VNC.  
The log will have something similar to the following:

11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      host-130.97-90-209-dedication.srv.nethosting.com
11/10/2013 06:12:21 AM      hosting.media-dsign.de
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM      50-192-221-54-static.hfc.comcastbusiness.net
11/10/2013 06:12:21 AM Client Protocol Version 3.4
11/10/2013 06:12:21 AM Ignoring minor version mismatch


** (vino-server:23797): WARNING **: Deferring authentication of '50-192-221-54-static.hfc.comcastbusiness.net' for 5 seconds




** (vino-server:23797): WARNING **: VNC authentication failure from '50-192-221-54-static.hfc.comcastbusiness.net'

The xsession-errors file grew to 700GBytes eventually.

---

