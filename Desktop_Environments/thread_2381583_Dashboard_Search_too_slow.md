---
title: "Dashboard Search too slow"
date: 2018-01-02
forum: Desktop Environments
---

### Post by 171742 on 2018-01-02
Hey,

I got ubuntu 16.4. and suddenly my dashboard search is very slow. The documents come up, but way too late. What to do?

Thanks!

---

### Post by TheFu on 2018-01-03
I'd ask a few questions.
* Did some new storage get added?
* Any storage removed?
* Any network shares added/remoted?
* How is DNS working?  DNS issues show up in the darnedest places.
* Have you checked the log files?  Anything there for the program or hardware? HW issues often show up first as slower computing.
* Are you willing to switch to a different search tool?  Recoll is an option?

---

### Post by 171742 on 2018-01-05
Hello,

i am an utter rookie, so I cant say for sure, but I try:

> **TheFu said:**
> I'd ask a few questions.
* Did some new storage get added?
no, only battery.
* Any storage removed?
no.
* Any network shares added/remoted?
I guess not, but I am not sure what a network share is. I have dropbox.
* How is DNS working?  DNS issues show up in the darnedest places.
What is this?
* Have you checked the log files?  Anything there for the program or hardware? HW issues often show up first as slower computing.
Hello, I dont know, I attached it. 
* Are you willing to switch to a different search tool?  Recoll is an option?
Yes, but recoll is equally slow, tried it.

Thanks in advance!

---

### Post by TheFu on 2018-01-08
And the other answers?

BTW, I won't open attached files here. Sorry.

---

### Post by 171742 on 2018-01-09
Hello,


sorry, which other questions? And can I send you the logfile, or how do we do it?

---

### Post by TheFu on 2018-01-09
Sorry, I didn't see that the answers were inside the quoted text.

Did you look at the log files? Anything funny inside them?  
YOU need to look at the logs for issues, not me.  Look for things with errors or warnings.

As for what DNS is ... that's a huge question. Wikipedia has an article.

---

### Post by 171742 on 2018-01-10
Hello,

I am sorry, but I am as said an utter rookie. For me this is all really funny. Isnt this what this forum kind of is for, that people who know this help people who dont? Or please give a defintion of "funny".

Same for DNS: A friend of mine confirgured this, he knows his stuff (but is unfortunately away now), so I would strongly guess this is not it.

BR

---

### Post by TheFu on 2018-01-10
> **171742 said:**
> Hello,

I am sorry, but I am as said an utter rookie. For me this is all really funny. Isnt this what this forum kind of is for, that people who know this help people who dont? Or please give a defintion of "funny".

Same for DNS: A friend of mine confirgured this, he knows his stuff (but is unfortunately away now), so I would strongly guess this is not it.

BR

Did you see any warnings or errors in the log files?  That is "funny."  Nearby lines to the warnings or errors often say exactly what the issue is.  We've all been there.  My eyes glossed over the first few times I looked at log files too, until I was forced to read them by my coworkers.  Then things became clearer.   Teach a man to fish ...   If you have 10 lines of errors/warnings and have questions, post them inside "code tags" [ Adv Reply (#) ] so things line up correctly.  Nobody wants to see 1,000 lines of junk.

DNS is basically a telephone book for computers. DNS can break or slow down for reasons that have nothing to do with the computer, but sometimes it breaks locally too. Wikipedia can explain what it is better than I, since DNS does other things too.  The point is that if DNS results are slow or aren't working, then all sorts of other things on a computer get slow too.  There are things that don't seem related to network lookups (DNS) that actually are. Dash searching is one of those.  Accessing storage is too.  So until a timeout happens (30+ seconds), no returned values will be displayed.  DNS is normally very fast so all these lookups are fast.

But we don't know anything without checking the log files.  Use your favorite web search tool to find tips for searching/looking at log files that makes sense to you.  Searching for answers is a way to learn Ubuntu and Linux.  I volunteer here to help others who want to learn more.  

Maybe someone else will post with alternative ideas.

---

### Post by vasa1 on 2018-01-10
> **171742 said:**
> Hey,

I got ubuntu 16.4. and suddenly my dashboard search is very slow. The documents come up, but way too late. What to do?

Thanks!
Is your dash set up to include internet search results? I don't use Unity myself but I understand you can turn that off and just have the dash search local files and applications. If local searches are still slow, I'm guessing you need not be concerned with DNS issues.

Does your internet browsing work normally? Once you open a file, are things like paging up and down responsive? If you drag windows about or resize them are things sluggish?

What does *top* say? Open a terminal and run ```
top -bn1 -o %MEM | head -20
```and ```
top -bn1 -o %CPU | head -20
```and post the output here.

Have you updated your system recently? Post the output of```
sudo apt-get update
```and```
sudo apt-get upgrade
```for starters.

---

### Post by 171742 on 2018-01-12
Thank you very much, that sound helpful. For DNS: The search is slow even when offline, and with online connection there are no problems. So I guess thats not it. As for the log filt, herre you go:

```
Jan  5 12:59:44 e-NC10 org.gtk.vfs.Daemon[1408]: message repeated 115 times: [ ** (process:3150): WARNING **: send_infos_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/15 (g-dbus-error-quark, 19)]

Jan  5 13:22:41 e-NC10 org.gtk.vfs.Daemon[1408]: ** (process:3150): WARNING **: send_infos_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)

Jan  5 13:22:41 e-NC10 org.gtk.vfs.Daemon[1408]: ** (process:3150): WARNING **: send_done_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)

Jan  5 13:28:03 e-NC10 org.gtk.vfs.Daemon[1408]: ** (process:3150): WARNING **: send_infos_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
Jan  5 13:28:03 e-NC10 org.gtk.vfs.Daemon[1408]: message repeated 118 times: [ ** (process:3150): WARNING **: send_infos_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)]
Jan  5 13:28:03 e-NC10 org.gtk.vfs.Daemon[1408]: ** (process:3150): WARNING **: send_done_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/2 (g-dbus-error-quark, 19)
Jan  5 13:28:18 e-NC10 kernel: [ 2977.521058] [UFW BLOCK] IN=wlan1 OUT= MAC=01:00:5e:00:00:01:00:90:a9:ce:84:7b:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=45135 PROTO=2 



Jan  5 13:33:13 e-NC10 org.gtk.vfs.Daemon[1408]: ** (process:3150): WARNING **: send_infos_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/21 (g-dbus-error-quark, 19)
Jan  5 13:33:13 e-NC10 org.gtk.vfs.Daemon[1408]: message repeated 116 times: [ ** (process:3150): WARNING **: send_infos_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/21 (g-dbus-error-quark, 19)]
Jan  5 13:33:13 e-NC10 org.gtk.vfs.Daemon[1408]: ** (process:3150): WARNING **: send_done_cb: Keine derartige Schnittstelle »org.gtk.vfs.Enumerator« des Objekts im Pfad /org/gtk/vfs/client/enumerator/21 (g-dbus-error-quark, 19)

Jan  5 13:44:28 e-NC10 gnome-session[1562]: kolourpaint(32063) KSambaSharePrivate::getNetUserShareInfo: We got some errors while running 'net usershare info'
Jan  5 13:44:28 e-NC10 gnome-session[1562]: kolourpaint(32063) KSambaSharePrivate::getNetUserShareInfo: "info_fn: file /var/lib/samba/usershares/xxx is not a well formed usershare file.
Jan  5 13:44:28 e-NC10 gnome-session[1562]: info_fn: Error was Path is not a directory.

Jan  5 13:44:34 e-NC10 gnome-session[1562]: kolourpaint(32063) KSambaSharePrivate::getNetUserShareInfo: We got some errors while running 'net usershare info'
Jan  5 13:44:34 e-NC10 gnome-session[1562]: kolourpaint(32063) KSambaSharePrivate::getNetUserShareInfo: "info_fn: file /var/lib/samba/usershares/xxx is not a well formed usershare file.
Jan  5 13:44:34 e-NC10 gnome-session[1562]: info_fn: Error was Path is not a directory.

n  5 13:46:42 e-NC10 gnome-session[1562]: ** (zeitgeist-datahub:3270): WARNING **: kde-recent-document-provider.vala:131: Couldn't process /home/o/.kde/share/apps/RecentDocuments/Amt-2.jpg.desktop: Error when getting information for file '/home/o/Amt-2.jpg': No such file or directory
Jan  5 13:46:42 e-NC10 gnome-session[1562]: kolourpaint(32267) KSambaSharePrivate::getNetUserShareInfo: We got some errors while running 'net usershare info'
Jan  5 13:46:42 e-NC10 gnome-session[1562]: kolourpaint(32267) KSambaSharePrivate::getNetUserShareInfo: "info_fn: file /var/lib/samba/usershares/xxx is not a well formed usershare file.
Jan  5 13:46:42 e-NC10 gnome-session[1562]: info_fn: Error was Path is not a directory.
Jan  5 13:46:42 e-NC10 gnome-session[1562]: "
Jan  5 13:46:42 e-NC10 gnome-session[1562]: kolourpaint(32267) KSambaSharePrivate::getNetUserShareInfo: We got some errors while running 'net usershare info'
Jan  5 13:46:42 e-NC10 gnome-session[1562]: kolourpaint(32267) KSambaSharePrivate::getNetUserShareInfo: "info_fn: file /var/lib/samba/usershares/xxx is not a well formed usershare file.
Jan  5 13:46:42 e-NC10 gnome-session[1562]: info_fn: Error was Path is not a directory.
Jan  5 13:46:42 e-NC10 gnome-session[1562]: "
Jan  5 13:46:43 e-NC10 gnome-session[1562]: kolourpaint(32267) KSambaSharePrivate::getNetUserShareInfo: We got some errors while running 'net usershare info'
Jan  5 13:46:43 e-NC10 gnome-session[1562]: kolourpaint(32267) KSambaSharePrivate::getNetUserShareInfo: "info_fn: file /var/lib/samba/usershares/xxx is not a well formed usershare file.
Jan  5 13:46:43 e-NC10 gnome-session[1562]: info_fn: Error was Path is not a directory.
Jan  5 13:46:43 e-NC10 gnome-session[1562]: "
```


Sorry, some of it is in German, but I hope it might still work. This is only a few, it goes on for a lot of errors...

---

### Post by 171742 on 2018-01-12
Hello,

thanks!

No, I do not include the internet in the dash service. 

Brwosing works all fine.

[COLOR=#000000]top -bn1 -o %MEM | head -20

[/COLOR]
[COLOR=#000000][/COLOR][COLOR=#000000][FONT=&quot]top -bn1 -o %CPU | head -20[/FONT][/COLOR][COLOR=#000000]

[/COLOR]
[COLOR=#000000][/COLOR]Yes, I upgrade every week at least. 

Thanks again.

---

### Post by vasa1 on 2018-01-12
If you're using Ubuntu (with Unity), why does```
kolourpaint(32267) KSambaSharePrivate
```appear in your logs?

Can you relate the slowness to installing new software? I don't know what *KSambaSharePrivate* is but *kolourpaint* is not present by default in Ubuntu.

---

### Post by TheFu on 2018-01-12
Looks like some KDE programs were installed, if not the full kde desktop.

In computing, it is common to take the error message and put it into a web search engine to see if anyone else has a similar issue. The only trick is **not** to include things that only for your machine - timestamps, machine names, stuff like that.

Samba is a network file sharing protocol.  If the machine thinks there should be a network share to be accessed, then it will probably try to access it, even when offline. If things work fine when online, I'd go through all the network shares, perhaps they have fstab mounts or saved mounted inside some file manager, and clean/remove them.  Then test again.  Your friend (the DNS setup guy) may have setup some network storage access for you.  

But google for the error messages, see where that leads.

Another trick is to create a new userid (a new account) and log in under it. Are things fast again?  That would say it is a userid issue, not an OS issue.  Some settings aren't good for the userid that is slow.  Whenever running any GUI stuff, if things behave oddly, this is a simple, 1st step, to see if it is the entire machine, or just a userid problem.

---

### Post by vasa1 on 2018-01-12
> **TheFu said:**
> Looks like some KDE programs were installed, if not the full kde desktop.
...
Running```
ls /usr/share/xsessions
```and```
apt list --installed | grep -i  plasma
```may give some information.

---

### Post by TheFu on 2018-01-12
But does that even matter?  KDE or some programs - shouldn't matter.

Seeing the output from the 'top' might be helpful too.  If it is like mine, it is always those monster browsers sucking all the CPU and RAM.

---

### Post by vasa1 on 2018-01-12
> **TheFu said:**
> But does that even matter?  KDE or some programs - shouldn't matter.

Seeing the output from the 'top' might be helpful too.  If it is like mine, it is always those monster browsers sucking all the CPU and RAM.
Looks like OP forgot all about that :D

So here goes again!

OP, when you encounter slowness, open a terminal, please run```
top -bn1 -o %MEM | head -20
```and```
top -bn1 -o %CPU | head -20
```**and post the output here**.

---

### Post by 171742 on 2018-01-17
Hey,

thanks. Kolourpaint is a really simple painting program, would be quite suprising if this was it. I really dont know the other app and googleing does not help...

---

### Post by 171742 on 2018-01-17
Sorry, forgot the top:
```

o@e-NC10:~$ top -bn1 -o %MEM | head -20
top -bn1 -o %MEM | head -20
top - 17:48:24 up  8:37,  1 user,  load average: 2,78, 2,03, 1,52
Tasks: 294 gesamt,   2 laufend, 292 schlafend,   0 gestoppt,   0 Zombie
%CPU(s): 11,1 be,  2,5 sy,  0,1 ni, 84,9 un,  1,3 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Spch :  4064528 gesamt,   264248 frei,  2737168 belegt,  1063112 Puff/Cache
KiB Swap:  4117500 gesamt,  1515708 frei,  2601792 belegt.   531964 verfü Spch 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     ZEIT+ BEFEHL
 1996 o         20   0 1917112 411832  32640 S   0,0 10,1   7:33.89 thunderbird
 7198 o         20   0  779856 263628  45872 S   6,2  6,5  11:21.51 chromium-b+
 1980 o         20   0 1310296 214064  44488 S   0,0  5,3  54:56.57 chromium-b+
 1620 o         20   0  497056 207488  21912 S   0,0  5,1  22:03.10 compiz
 7886 o         20   0  519032 145468  10244 S   0,0  3,6   6:54.04 soffice.bin
 9257 o         20   0 1038276 142648  36024 S   0,0  3,5   2:15.21 firefox
 9322 o         20   0  948120 140464  25688 S   0,0  3,5   2:48.48 Web Content
23255 o         20   0 1015088 116808  38076 S   0,0  2,9   0:28.88 Web Content
 1182 root      20   0 1312276 115708  89664 S   0,0  2,8  17:50.04 Xorg
 2389 o         20   0  431680 115476  73528 S   0,0  2,8  12:23.44 chromium-b+
 2651 o         20   0  556632 113432  21120 S   0,0  2,8   1:48.89 chromium-b+
 1822 o         20   0  237696 103696  22312 S   0,0  2,6   0:27.79 gnome-soft+
 6424 o         20   0  649360 103012  40452 S   0,0  2,5   2:06.01 chromium-b+
o@e-NC10:~$ top -bn1 -o %MEM | head -20
top - 17:48:24 up  8:37,  1 user,  load average: 2,78, 2,03, 1,52
Tasks: 294 gesamt,   2 laufend, 292 schlafend,   0 gestoppt,   0 Zombie
%CPU(s): 11,1 be,  2,5 sy,  0,1 ni, 84,9 un,  1,3 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Spch :  4064528 gesamt,   257764 frei,  2743656 belegt,  1063108 Puff/Cache
KiB Swap:  4117500 gesamt,  1515712 frei,  2601788 belegt.   525480 verfü Spch 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     ZEIT+ BEFEHL
 1996 o         20   0 1917112 411832  32640 S   0,0 10,1   7:33.89 thunderbird
 7198 o         20   0  779856 263628  45872 S   0,0  6,5  11:21.51 chromium-b+
 1980 o         20   0 1310296 214064  44488 S   0,0  5,3  54:56.57 chromium-b+
 1620 o         20   0  497056 207488  21912 S   6,2  5,1  22:03.11 compiz
 7886 o         20   0  519032 145468  10244 S   0,0  3,6   6:54.04 soffice.bin
 9257 o         20   0 1038276 142648  36024 S   0,0  3,5   2:15.21 firefox
 9322 o         20   0  948120 140464  25688 S   0,0  3,5   2:48.48 Web Content
23255 o         20   0 1015088 116808  38076 S   0,0  2,9   0:28.88 Web Content
 1182 root      20   0 1312276 115708  89664 S   6,2  2,8  17:50.05 Xorg
 2389 o         20   0  431680 115476  73528 S   0,0  2,8  12:23.44 chromium-b+
 2651 o         20   0  556632 113432  21120 S   0,0  2,8   1:48.89 chromium-b+
 1822 o         20   0  237696 103696  22312 S   0,0  2,6   0:27.79 gnome-soft+
 6424 o         20   0  649360 103012  40452 S   0,0  2,5   2:06.01 chromium-b+
o@e-NC10:~$ ^C


top -bn1 -o %CPU | head -20

e-NC10:~$ top -bn1 -o %CPU | head -20
top - 17:49:31 up  8:39,  1 user,  load average: 3,06, 2,20, 1,62
Tasks: 292 gesamt,   1 laufend, 291 schlafend,   0 gestoppt,   0 Zombie
%CPU(s): 11,1 be,  2,5 sy,  0,1 ni, 84,9 un,  1,3 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Spch :  4064528 gesamt,   266544 frei,  2709404 belegt,  1088580 Puff/Cache
KiB Swap:  4117500 gesamt,  1531344 frei,  2586156 belegt.   539116 verfü Spch 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     ZEIT+ BEFEHL
 9214 root      25   5    2364   1144    964 S  12,5  0,0   0:00.04 mkinitramfs
 1381 o         20   0   60012  15824   3908 S   6,2  0,4   2:27.64 ibus-daemon
 1620 o         20   0  497136 207304  21748 S   6,2  5,1  22:08.79 compiz
 9549 o         20   0    9408   3732   3208 R   6,2  0,1   0:00.01 top
    1 root      20   0   25232   3084   2244 S   0,0  0,1   0:03.43 systemd
    2 root      20   0       0      0      0 S   0,0  0,0   0:00.02 kthreadd
    3 root      20   0       0      0      0 S   0,0  0,0   0:00.47 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0,0  0,0   0:00.00 kworker/0:+
    7 root      20   0       0      0      0 S   0,0  0,0   0:47.65 rcu_sched
    8 root      20   0       0      0      0 S   0,0  0,0   0:00.00 rcu_bh
    9 root      rt   0       0      0      0 S   0,0  0,0   0:00.03 migration/0
   10 root      rt   0       0      0      0 S   0,0  0,0   0:00.13 watchdog/0
   11 root      rt   0       0      0      0 S   0,0  0,0   0:00.12 watchdog/1
o@e-NC10:~$ ^C
```

---

### Post by TheFu on 2018-01-17
Top just says the system isn't busy and RAM is fine.

I'm back to DNS and following the issues listed in the log files for network storage.

Did you create a new userid yet?  I bet that will solve it, since the issues appear to be user-environment specific.

---

### Post by vasa1 on 2018-01-17
It looks like swap is being used.

---

### Post by TheFu on 2018-01-17
> **vasa1 said:**
> It looks like swap is being used.

Swap is almost always used when 2 huge desktop programs are run.  That doesn't mean the system is slow.  TOP on my system looks much like this one. Everything is fine.  Actually, mine is using more swap and has less free RAM, only 143964 free.

---

### Post by greyfaux01 on 2018-01-18
If i can just jump in and try to offer some help from a more noobish perspective, not saying it will help, and OP definitely listen to the other guys, but what i would do, is open up one of your 'task manager' or 'system monitor' (in a gui, thats what the 'top' command is showing, but with the gui task manger open you can watch as you duplicate the issue, you have at least 1 task manger/system monitor installed by default), and then while watching the task manager window, duplicate the issue, start doing searches in the dashboard, and see what starts using your cpu/etc. You can click the 'cpu' (or ram) catagory and make sure the highest cpu %'s are at the top, and try to spot a process that starts using up your cpu as your purposely slowing your system down by searching in the dash. Some of the processes will appear/disappear quickly, so try to keep an eye as you type/search in the dash. You'll probably see 'zeigeist' come to the top, which is normal but still could indicate some problem (look for clues, anything really).

As far as kolourpaint, ime, kde stuff has caused me problems in the past. Its not the program itself, but usually kde (and others) have a lot of dependecies, meaning they have to install a list of other programs/repositorys as well, just to install 1 tiny program. I actually do have a few KDE programs myself, some that have no equal imo (k3b), but i also unistalled a lot of kde programs in synaptic package manager, mainly the ones i could that removed the most dependencies, and my system actually sped up a bit. A long time ago, i had the kde desktop installed, i was always having problems with 'nepomuk', which i think is a program thats always indexing things in the background, i guess kind of like zeitgeist does. If you have the 'right' kde programs installed, like dolphin, you'll probably have nepomuk (maybe called baloo now), and many people have had problems with these programs eating up cpu. Im not sure nepomuk/baloo should even be installed together with zeitgiest (the default ubuntu indexer of all files), because i think they do similar things.

Anyway, i know i dont have a quick fix, but maybe this can help you to find some clues as to whats causing it. I personally dont use unity, but i still utilize the zeitgeist engine with a program called synapse, its instantaneously fast, and can find just about every file/folder/program on my computer. In fact a lot of people in general have problems with unity being slow, thats why i dumped it originally. That said i know you say it was working fast before, so could just be a new bug in unity.

If you have KDE desktop DE installed, i would consider purging that, as well as any other kde programs you dont use, especially if your seeing nepomuk/baloo in task manager. And another great option in perhaps installing a different desktop, like xfce or lxde, on top of ubuntu. This CAN bring its own set of problems, as Fu was educating me on previously, where different DE's share config files, causing conflicts, but for me personally, not making tons of system level changes, ive been fine with xfce and lxde on top of ubuntu, and using synapse to fill the gap of the unity dash. Just some things to consider if you cant get your dash fast again (mine was never fast).

---

