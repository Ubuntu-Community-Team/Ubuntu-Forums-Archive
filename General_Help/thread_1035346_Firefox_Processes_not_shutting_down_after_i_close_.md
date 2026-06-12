---
title: "Firefox Processes not shutting down after i close it"
date: 2009-01-09
forum: General Help
---

### Post by Firestem4 on 2009-01-09
Hello, I was hoping someone would be able to help me fix this problem or find some way aroudn it.

I installed Mozilla Firefox (via UbuntuZilla). Whenever I close down firefox, the processes firefox adn firefox-bin are still running. So when i try to reopen the internet browser i get an error message stating another instance of Firefox is already running. And i have to close the other one if i want to start [the new instance]

All i have to do is end the processes, but I constantly start up, and close down Firefox. I don't want to have to open the system monitor each timme i want to run it.

Im running Kubuntu 8.10, KDE 4.1x.

---

### Post by binbash on 2009-01-09
i have same problem at kde4, i am also bored giving pkill firefox command.Solutions are welcome

---

### Post by nanotube on 2009-01-09
and this does not happen when you use the firefox from the repos? (if you installed mozilla's build with ubuntuzilla, then the ubuntu-repos firefox should be available by running command "firefox.ubuntu". )

---

### Post by Flecko on 2009-01-10
I have this same problem and I'm using the official Ubuntu from the repos. Intrepid 8.10 with all the updates installed. Just noticed this in the last 3 days or so.

Also, after a bit of browsing, firefox refuses to load any new pages. I'm becoming increasingly annoying with its performance/stability lately. Its getting pretty crazy.

Writing this from Epihphany btw.

---

### Post by todak on 2009-01-10
Read this [http://support.mozilla.com/en-US/kb/High+memory+usage](http://support.mozilla.com/en-US/kb/High+memory+usage)  or here [http://support.mozilla.com/en-US/kb/Java-related+issues#Java_applet_causes_Firefox_process_to_remain_in_memory](http://support.mozilla.com/en-US/kb/Java-related+issues#Java_applet_causes_Firefox_process_to_remain_in_memory) and see if any of the suggestions help.

---

### Post by nicoelba on 2011-10-19
Hi to everyone.

I've the same problem: > Firefox-bin is already running even if I've closed it properly..

I have to kill it manually..

I'm using Ubuntu 10.04 with Firefox 3.6.23

Any solution??

---

### Post by Ceiber Boy on 2011-10-19
> **nicoelba said:**
> Hi to everyone.

I've the same problem:  even if I've closed it properly..

I have to kill it manually..

I'm using Ubuntu 10.04 with Firefox 3.6.23

Any solution??

I'm using ubuntu 10.04 LTS and this happens to me also from time to time, it really is annoying!

The firefox install is what was installed at time of OS install, and the updates as and when they come through.

Any answers to this would be much appreciated.

---

### Post by Ceiber Boy on 2011-10-19
> **todak said:**
> Read this [http://support.mozilla.com/en-US/kb/High+memory+usage](http://support.mozilla.com/en-US/kb/High+memory+usage)  or here [http://support.mozilla.com/en-US/kb/Java-related+issues#Java_applet_causes_Firefox_process_to_remain_in_memory](http://support.mozilla.com/en-US/kb/Java-related+issues#Java_applet_causes_Firefox_process_to_remain_in_memory) and see if any of the suggestions help.

In the second website listed in the quote, it assigns the fault to Java not shutting down correctly!

Any help would still be appreciated.

Thanks

---

### Post by nicoelba on 2011-10-20
> In the second website listed in the quote, it assigns the fault to Java not shutting down correctly!
But even when I don't use any kind of Java app it happens....

---

### Post by Jean-Claude Tergal on 2011-10-20
Hi!
I've the same problem related here: 
[http://ubuntuforums.org/showthread.php?t=1865552](http://ubuntuforums.org/showthread.php?t=1865552)

---

### Post by Ceiber Boy on 2011-10-25
Anyone know how to solve this?

---

### Post by nicoelba on 2011-10-26
I've followed this thread of the Italian Ubuntu Forum:
[http://forum.ubuntu-it.org/index.php/topic,472544.0.html](http://forum.ubuntu-it.org/index.php/topic,472544.0.html)

The suggested solution for this problem is this:

[LIST]
[*]uninstall Firefox and delete /home/.mozilla
[*]reinstall Firefox
[*]set to false ALL the ipc entries in the "about:config"  page of the browser
[/LIST]
They are something like this:> 
dom.ipc.plugins.enabled 
dom.ipc.plugins.enabled.libflashplayer.so 
dom.ipc.plugins.enabled.libnptest.so

In my case this is the solution..
Hope to help!

---

### Post by Jean-Claude Tergal on 2011-10-27
Thank you Nico for your help.
It seems be efficient in my case.

Note that I've neither uninstall FF, nor remove .mozilla.
I've only made modification in about:config.

Note: I use three FF sessions with three differents profiles.
I have make the modification for only one of them but it works for all (!?)
It seems that only one session has generate a process who cannot be closed by quitting FF... This process locks the other sessions.
Bizzare, bizarre...


> **nicoelba said:**
> 
The suggested solution for this problem is this:

[LIST]
[*]uninstall Firefox and delete /home/.mozilla
[*]reinstall Firefox
[*]set to false ALL the ipc entries in the "about:config"  page of the browser
[/LIST]
They are something like this:

In my case this is the solution..
Hope to help!

---

### Post by reset3x on 2011-11-13
> **nicoelba said:**
> I've followed this thread of the Italian Ubuntu Forum:
[http://forum.ubuntu-it.org/index.php/topic,472544.0.html](http://forum.ubuntu-it.org/index.php/topic,472544.0.html)

The suggested solution for this problem is this:

[LIST]
[*]uninstall Firefox and delete /home/.mozilla
[*]reinstall Firefox
[*]set to false ALL the ipc entries in the "about:config"  page of the browser
[/LIST]
They are something like this:

In my case this is the solution..
Hope to help!


Works like a charm for me!! 

Cheers!!

Reset :)

---

