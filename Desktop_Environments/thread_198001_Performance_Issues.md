---
title: "Performance Issues"
date: 2006-06-16
forum: Desktop Environments
---

### Post by xiliax on 2006-06-16
Hi, I am new to this forum (please excuse me if the thread isn't in the right section). So..I have a little experience with Hoary and Breezy and with different environments (xfce, kde and gnome) and I can't get my system to work fast enough. Now I am running fresh install of Kubuntu Dapper and it's really slow. Here's my system specs : Athlon 2200+@2Ghz; 256mb ram; gf4mx440 64mb; 120gb Seagate ATA which is divided to 2 fat 32 partitions, 1 nfts, 1 ext3 and 1 swap which is ~500mb (is it enough?). I read some howtos and did some tweaking.
Here's what i have done up to now: 
[LIST]
[*]I have disabled KDE's animations, effects etc.
[*]I have DMA enabled.
[*]I have disabled 2-6 ttys.
[*]I have disabled unneeded services.
[*]I am using -k7 kernel (I havent compiled my own yet cause it's veeery slow (at least it was in hoary and breezy)..)
[*]I have the latest nvidia drivers and enabled 3D and fastwrite and I get 40-50 fps in Counter-Strike @ 1024x768 and it's practically unplayable on Windows I get 70.
[*]I have tweaked my ext3 filesystem using [this howto]("http://ubuntuforums.org/showthread.php?t=107856")
[*]I am using prelink.
[/LIST]
I wanted to try initng but there aren't any packages to download on the site [http://alioth.debian.org/projects/pkg-initng/](http://alioth.debian.org/projects/pkg-initng/) ??
Is there something i have missed, is there something i shouldn't have done? Please give me some advices cause I am about to delete my linux partition...

---

### Post by lowey23 on 2006-06-16
Just a guess, but I think your 256M ram may be just enough. I have 512M and could possibly use more. 
Just my 2c.

---

### Post by H.E. Pennypacker on 2006-06-17
> I can't get my system to work fast enough.

I can see you're probably someone used to the fast life, because you have a 2GHz processor.  That's not a bad thing.  It's actually a good thing, and you certainly don't have to sacrifice your need for speed with Linux.  I am sure the issue you're facing is more geared towards your settings than Linux in general.

> 1 swap which is ~500mb (is it enough?). I read some howtos and did some tweaking.

Change it to at least 512MB.  It should be at least double your RAM.  I made a mistake somewhere, and my SWAP partition is now 6**GB**.  Everything seems to go faster with Ubuntu than it does with Windows, especially start-up.

> 
I have disabled KDE's animations, effects etc.

Are you sure you even want KDE?  I know you've played around with Gnome, but I can tell you Gnome is not as heavy as KDE.  Besides, KDE puts an unnecessary load of software on your back.  I would honestly recommend Gnome, and my experience with Gnome has proven better than my experience with KDE.

> I wanted to try initng

initNG sounds very promising, and it goes to show what community involvement can do.  Can you imagine calling Microsoft and complaining about something?  They may upgrade things with the next release, but expect no promises, and you certainly don't know what's to come.  Besides, there's no involvement and OSes take a long time to be released.

initNG is a project driven by the Linux community, because we've had the same things on mind, and we've been able to work together.

Everything you may want to know about initNG should be here:

[https://wiki.ubuntu.com/InitNG](https://wiki.ubuntu.com/InitNG)

Because those Wiki instructions don't exactly explain things very well, here's my explanation:

1.  Start the terminal.
2.  Type in su.
3.  Type in your password.
3.  Type in gedit /etc/apt/sources.list - This opens up sources.list in gEdit.
4.  Add at the bottom the following lines:

deb [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
deb-src [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main

Those two lines will add the new location of the DEB files. 

5.  Open up Synaptic.
6.  Search for "initNG."
7.  You should now see "initNG" and "initNG-ifiles."
8.  Instead of installing it through the terminal as the Wiki suggests, try installing those two files through Synaptic.

The problem is that Linux users seem to want to make things more difficult, especially by instructing other users to use the Terminal.  For the sake of everything good, let's abandon the terminal.  Anyhow, ignore the first few lines about adding the repository links to the above file if you are able to succesfully add the two new repositories through Synaptic.  I had to do it manually because Synaptic was acting up.

By the way, initNG has a new repository home:

[http://blog.space-based.de/2006/05/initngs-apt-repo-has-a-new-home/](http://blog.space-based.de/2006/05/initngs-apt-repo-has-a-new-home/)

---

### Post by 23meg on 2006-06-17
Sorry for going off-topic, but
> The problem is that Linux users seem to want to make things more difficult, especially by instructing other users to use the Terminal.
- Launch Synaptic
- Click "Settings", and then "Repositories"
- Click "Add", and then "Custom"
- Enter deb "http://debian.space-based.de/debs/ experimental main" and click "Add channel"
- Click "Add", and then "Custom" again
- Enter deb-src "http://debian.space-based.de/debs/ experimental main" and click "Add channel"
- Click "Close"
- Click "Reload"

vs.

- Launch the terminal
- Highlight and paste "sudo nano /etc/apt/sources.list" and hit enter
- Highlight and paste 
deb [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main
deb-src [http://debian.space-based.de/debs/](http://debian.space-based.de/debs/) experimental main 
(two lines at once)
- Hit Ctrl+X and then Y
- Highlight and paste "sudo apt-get update"

Which is more difficult?
> I had to do it manually because Synaptic was acting up.
Bash just about never acts up. If it does it's most likely you're totally hosed anyway.

xiliax, if you decide to try initNG be aware that it's a critical system component and is very much in development, so it may have serious bugs with system-wide effects. Make sure you have your valuable data that may be difficult to recover backed up. It's designed to just speed up the boot process anyway, not improve actual system performance.

---

### Post by H.E. Pennypacker on 2006-06-17
23mg, you're absolutely right, but then again, there's a reason I used the terminal.  I was getting a weird error with Synaptic, so I resorted to the terminal, which appears to have solved my problem.

I think there's something wrong with those two repositories, because I am getting some GPG error about a public key.  Well, I'll go see what that's all about.

---

