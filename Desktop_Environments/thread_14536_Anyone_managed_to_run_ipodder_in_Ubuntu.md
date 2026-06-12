---
title: "Anyone managed to run ipodder in Ubuntu?"
date: 2005-02-08
forum: Desktop Environments
---

### Post by SickBoy on 2005-02-08
[http://ipodder.sourceforge.net/index.php](http://ipodder.sourceforge.net/index.php)

I tried to install package with alien but when i try to run it does not seem to start.

---

### Post by 23meg on 2005-05-07
i set it up using the provided install script, installed the missing package wxpython2.5.3 from the repositories, and it works.

---

### Post by 23meg on 2005-05-07
oh, but when i try to download subscribed casts i get the following errors on the console:

```
Figuring out which feeds to scan...
We have 5 feeds to scan.
Scanning...
Uncaught exception!
Traceback (most recent call last):
  File "/opt/iPodder/iPodder.py", line 963, in start
    self.scanenclosures(mask,catchup)
  File "/opt/iPodder/iPodder.py", line 514, in scanenclosures
    scanner.addjob(job, priority=num)
  File "/opt/iPodder/ipodder/engine.py", line 176, in addjob
    self.queue.put((priority, job))
  File "/usr/lib/python2.4/Queue.py", line 88, in put
    self._put(item)
  File "/opt/iPodder/ipodder/engine.py", line 19, in _put
    bisect.insort(self.queue, item)
AttributeError: insert
Exception checking for update at url http://ipodder.sourceforge.net/update/current_version.xml
Last check completed at Sun May  8 06:57:53 2005
``` 

any ideas what's going wrong?

---

### Post by brianlawson on 2005-05-09
If it is any consolation, 23meg, I'm getting the exact same messages in my error log when I try to download something I've subscribed to.

---

### Post by c_dog on 2005-05-10
[QUOTE=SickBoy][http://ipodder.sourceforge.net/index.php](http://ipodder.sourceforge.net/index.php)

I tried to install package with alien but when i try to run it does not seem to start.[/QUOTE]

iPodder workes fine with Hoary, but you need to use v2.0 RC3 if you're going to use Python 2.4 and wxpython 2.5.3. The older version only support Python 2.3. Also make sure you have the the python libraries for Xmms installed and have xmms set as a player.

---

### Post by mtron on 2005-05-10
where did you find v2.0 RC3?

on the sourceForge download dir is ony http://prdownloads.sourceforge.net/ipodder/iPodder-linux-2.0-RC2.tar.bz2

can you please post a link?

---

### Post by 23meg on 2005-05-18
[here](http://sourceforge.net/project/showfiles.php?group_id=118306&package_id=135533&release_id=327398)  it is, but this version won't even run at all. here are the errors:

> Traceback (most recent call last):
  File "iPodderGui.py", line 38, in ?
    import iPodderWindows
  File "/opt/iPodder/iPodderWindows.py", line 6, in ?
    import gui.tree
  File "/opt/iPodder/gui/tree.py", line 16, in ?
    from ipodder import grabbers
  File "/opt/iPodder/ipodder/grabbers.py", line 56, in ?
    from configuration import __version__
  File "/opt/iPodder/ipodder/configuration.py", line 15, in ?
    import players
ImportError: Bad magic number in /opt/iPodder/ipodder/players.pyc


note: i have python2.4-xmms installed.

---

### Post by Cklein on 2005-05-19
I get the same error as 23meg, and I can't see the difference to what is on the [wiki](http://www.ubuntulinux.org/wiki/IPodder) and why it works for some people and not for some other (like me  :mad: )...

---

### Post by 23meg on 2005-05-19
i wonder if those who can get it to run can also get it to actually download things. anyone?

---

### Post by joeh on 2005-05-19
I googled around and found this, which works for me.

Modify PriorityQueue in /opt/iPodder/ipodder/engine.py to look like this:

class PriorityQueue(Queue.Queue):
    """Prioritised Queue, as per bisect module documentation."""
    def _put(self, item):
        #bisect.insort(self.queue, item)
        self.queue.append(item)

---

### Post by 23meg on 2005-05-19
[QUOTE=joeh]I googled around and found this, which works for me.

Modify PriorityQueue in /opt/iPodder/ipodder/engine.py to look like this:

class PriorityQueue(Queue.Queue):
    """Prioritised Queue, as per bisect module documentation."""
    def _put(self, item):
        #bisect.insort(self.queue, item)
        self.queue.append(item)[/QUOTE]
 that doesn't help me here, still not working.

---

### Post by mtron on 2005-05-20
me too, i can start the program, but no download... :???: 

Any other suggestions ?

---

### Post by 23meg on 2005-05-20
i'm totally stuck. with rc2 i can start it, but can't download. and rc3 won't start at all.

---

### Post by joeh on 2005-05-21
I got rc3 to work by following the instructions on the wiki page:

[https://www.ubuntulinux.org/wiki/IPodder]("https://www.ubuntulinux.org/wiki/IPodder")

---

### Post by momo66 on 2005-05-28
[QUOTE=joeh]I got rc3 to work by following the instructions on the wiki page:

[https://www.ubuntulinux.org/wiki/IPodder]("https://www.ubuntulinux.org/wiki/IPodder")[/QUOTE]

I was able to get it working using the wiki.

thanks!!

---

### Post by recover82 on 2005-05-28
here is the error i am receiving when i try to start iPodder:

Traceback (most recent call last):
  File "iPodderGui.py", line 38, in ?
    import iPodderWindows
  File "/opt/iPodder/iPodderWindows.py", line 4, in ?
    import  listctrl  as  listmix
  File "/opt/iPodder/listctrl.py", line 296, in ?
    EVT_DOPOPUPMENU = wx.PyEventBinder(wxEVT_DOPOPUPMENU, 0)
AttributeError: 'module' object has no attribute 'PyEventBinder'

can we say. . . "wtf?"  i have all the packages installed according to the readme and the install.linux file...and i followed along with the howto file on ubuntu wiki.

---

### Post by tube013 on 2005-05-31
I just googled around and found a solution that lets you run it from your home dir in the extracted iPodder-linux folder...

[http://nozell.com/blog/archives/2005/01/04/ipodder-gui-on-linux-debiansarge-mini-howto/](http://http://nozell.com/blog/archives/2005/01/04/ipodder-gui-on-linux-debiansarge-mini-howto/)

from the comments:

```
export PYTHONPATH=/usr/lib/python2.4/site-packages/wx-2.5.3-gtk2-unicode/:$PYTHONPATH-unicode:$PYTHONPATH
./iPodderGui.py
``` 

Still can't run as installed from the script though, same error as above.

---

### Post by rdwtux on 2005-06-02
I found that my problem was having multiple versions of wxpython installed.. remove older vers and only use the latest

---

### Post by brentroos on 2005-10-10
*

---

### Post by 23meg on 2005-10-10
hey, i didn't know it was in Breezy. just checked the repos and it's there, i'm installing right now. thanks for the heads up!

---

### Post by 23meg on 2005-10-10
the packaged version seems to have the same defect: everything seems to work, but no downloads. when i attempt to download a podcast, its status immediately switches to "downloaded" and nothing else happens.

can anyone who's installed ipodder from the breezy repositories confirm this? we should perhaps file a bug report.

---

### Post by 23meg on 2005-10-10
i was going to report this as a bug but it seems the ipodder package isn't listed in Launchpad.. weird.

---

### Post by caporaso on 2005-10-11
I am having the same issue as you 23meg. The only difference is there are a few feeds that result in sucessful downloads. have you managed to file a bug report or come up with any other leads?

---

### Post by 23meg on 2005-10-11
unfortunately not. as i said, i can't file a bug report because the Launchpad bug facility does not accept "ipodder" as a valid package.

---

### Post by dkitty on 2005-10-16
I've had the same problem, in that some of the files that iPodder supposedly downloads show properties of 0 bytes and (natually) don't contain much of anything. Yet some podcasts will download just fine. *shrug* I've been using [bashpodder](http://www.ubuntuforums.org/showthread.php?t=41085) instead and I dig it.

---

### Post by E@zyVG on 2005-10-17
Check out this link from my blog:

[My New Podcast Client - CastPodder]("http://linux.wordpress.com/2005/10/17/my-new-podcast-client-castpodder/")

---

### Post by E@zyVG on 2005-10-17
Check out this link from my blog:

[My New Podcast Client - CastPodder/]("http://linux.wordpress.com/2005/10/17/my-new-podcast-client-castpodder/")

---

### Post by GeneW on 2006-09-04
The packaged version does nothing useful for me either but I guess that I'm glad that I'm not the only one.  Who do we contact to say that the bug Launchpad does not have ipodder as a category?

---

