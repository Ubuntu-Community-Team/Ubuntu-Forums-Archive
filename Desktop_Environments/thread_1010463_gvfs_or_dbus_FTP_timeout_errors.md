---
title: "gvfs or dbus FTP timeout errors"
date: 2008-12-13
forum: Desktop Environments
---

### Post by flexgrip on 2008-12-13
Hello,

I am trying to use Intrepid/Gnome + Gedit for web development. I installed all the gedit plugins and got everything to fit like a glove.

I have all of my company's sites bookmarked. I connect and start editing sites and everything is beautiful EXCEPT...

After sitting on an ftp for so long (however long the ftp connection timeout is) everything fails. I try to save something and it tells me it cant save and generally has trouble reconnecting to save. Freezes, and goes grey with this as a result:

----------
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
----------

Basically what I am looking for is two things: Is there something I can do to fix this on my system? or is there something that I might change on my FTP servers to help (sometimes we don't host our clients sites so the best answer would be fixing something on my system)?

Thanks and let me know what logs/information you might need. I am hoping I am not the only web developer that has run into this problem.

Thanks again.

Ohh I forgot, I am also getting this error in Nautilus after letting an open FTP window sit for too long.

---

### Post by tyyp88 on 2009-03-02
Basically I'm having same problems. I'm using for development 8.04.2 + Gnome + Komodo EDIT and FTP acess hangs randomly. Gonna give a try with KDE and see does it makes any differences.

---

### Post by finalwebsites on 2009-08-11
Hi,

I have the same problem, if I open a remote file from a mounted ftp connection and keep this open for a while, the whole session hangs.

The problem is that some ISP provide different "connections"?

I have currently 2 providers:

Never had this problem with my ADSL provider but now with my new cable broadband provider.

Because this problem is also related to your ISP's connection this "timeout" bug is never solved in years (see similar post from 3 years ago)

So where is the option for timeout and/or re-connect in nautilus?

BTW I don't think this problem is related to gedit, if I open a connection with gftp or konquerer and edit the file with gedit the problem doesn't exists.

---

### Post by finalwebsites on 2009-08-11
It seems that this will help:

# sudo gconf-editor

inside the editor:

desktop -> gnome -> session

I raised the "idle" time to 60 minutes

---

### Post by airtonix on 2009-09-16
> **finalwebsites said:**
> It seems that this will help:

# sudo gconf-editor

inside the editor:

desktop -> gnome -> session

I raised the "idle" time to 60 minutes

Ubuntu Intrepid 8.10 , key you mention isn't present in that location for me.

---

### Post by finalwebsites on 2009-09-16
I thought that this was the solution for my problem, but it still exists.

Seems to be something with my connection? Don't have the problem on other Internet connections.

---

### Post by sturnus on 2009-11-26
I had a similar problem, it is all about the timeout on the distant end.

I am currently using an SFTP site to provide network attached storage in a cross platform environment. ssh is easier for me.

I used places to map the drive initially, but after that I use the command line and the startup applications to remount the share when I log in.

The problem is that after some idle time it would disconnect and I would get errors when working with remote files.  Maybe some type of keepalive mechanism should be implemented in gvfs. 

Until then... If you can schedule a job, you can set up your own dirty keepalive/reconnect.  If you can't schedule, do a loop with a sleep...

I use the at command and do an if -d on one of the directories on the share.  I guess you could use touch as well and just touch the file every x minutes.  The remount was just the first thing I thought about.


Here is the script:

```

#!/bin/bash
loc={part of the name of the share to mount}
if [ ! -d "/home/{username}/.gvfs/{location name}/{directory to check}" ]
  then
    grep $loc ~/.gtk-bookmarks | cut -d ' ' -f 1 | xargs gvfs-mount
fi

echo "/home/{username}/checkmount.sh" | at now + 10 minutes

```It works for me. I haven't had any problems but you may lose connectivity for a couple minutes if the timing isn't right.

Sturnus

---

### Post by boomshop on 2010-01-15
Yes it's really annoying. Because I need some more flexibility I just wrote a python script (which is attached) to keep all my connections up and running.

It keeps all once mounted ftp servers connected until you restart your session or the script. It's a bit quick'n'dirty but I don't have the need for a graphical user interface to prevent servers from being remounted or something like this atm.

You have to configure the script to fit your local language since gvfs mounts the servers on folders with located names. In german they're called "FTP als foo auf bar.de" for example so the configuration has to look like "FTP als {USER} auf {HOST}". And you can set a timeout. In my case 5 minutes (300 seconds) seems to work fine.

I added it to the sessions autostart programs so I don't have to deal with ftp connections anymore. But remember: *every* ftp server mounted once will be kept alive. If you shut your computer down every night or don't deal with hundrets of servers it shouldn't become a problem anyway.

Greetings, Markus.

---

### Post by mxsteini on 2011-01-18
Hey boomshop,
your script works like a charm.
Many thanks.
My ftp-session is still open after lunch. 

Thanks
:popcorn::guitar:

---

### Post by dvdangelo on 2011-04-26
> **finalwebsites said:**
> It seems that this will help:
 
# sudo gconf-editor
 
inside the editor:
 
desktop -> gnome -> session
 
I raised the "idle" time to 60 minutes
 
Immediate Fix. I had a bookmarked an FTP folder for my WebServer. And when ever i tried to connect to it it would give me a DBus Error. After i made this change it fixed the issue and i can connect to the FTP with out problems.
 
Thanks!

---

### Post by lcruz007 on 2011-09-24
Hello,

Sorry for bumping up this thread, I am aware it was posted a while ago. But I kept having this same problem when connecting to my remote FTP server. Recently changed my ISP, and encountered this annoying error.

I know it is a timeout problem, it disconnects after being idle some minutes. I don't know why it is caused though. I even tried the python script user boomshop wrote, but didn't work unfortunately. His program was intended to keep active the gvfs ftp session... 

Well I wrote a similar program, but a **SIMPLER** program.. What it does is that it simply writes something to a text file every 30 seconds (or depending on the user's specification if you edit the script) located in the remote server in order to keep the ftp server-client session active.

I attached the files if anybody wants to try it out, it seems to have solved the problems for me, at least temporary, let me know if it works for you.... Just extract the zip file, copy the files (both the python and the text file) in your remote server and then open it using terminal.

---

### Post by rm -rf / on 2011-11-15
I'm surprised more people haven't had this issue.  It does appear to be an ISP related issue.  It only started happening when I switched to Verizon FiOS, and was present in both my 11.10 Laptop and 11.04 desktop.  I lost a few pages that I had spent hours coding, they were just blanked.  When I booted into Windows, and used Dreamweaver I didn't have the issues.

Amazing it has gone this long. Huge thanks to all who have contributed solutions!

---

### Post by Alex1331 on 2011-11-20
I have had problems with this for several years, it is not related to the ISP. When the connection dies gvfs will not reconnect.
This makes other programs (eg. gEdit) to freeze if they attempt to open a file and gvfs will not connect again.

> I lost a few pages that I had spent hours coding, they were just blanked.
I have experienced it a few times, in Ubuntu 11.04. The file was saved, but without any content. Have you experienced it in 11.10?

[Bug on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/888365") - Importance: Low :(

I think it should be high, because this is a problem that has existed for several years and have never done anything with. The problem can be quite damaging if editing a web page and the file is saved without content. That is, if the empty file error still exists in 11.10.

---

### Post by aprohal on 2012-02-12
ubuntu 11.10

alt+F2

dconf-editor

org > gnome > desktop > session

set idle-delay in seconds for your needs (eg 86400 a whole day)...

but don't forget: usually there is an other idle time settings on server side,
so probably got an error message, don't panic save again...

---

