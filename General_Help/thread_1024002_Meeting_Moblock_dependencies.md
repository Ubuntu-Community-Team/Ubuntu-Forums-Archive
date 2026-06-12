---
title: "Meeting Moblock dependencies?"
date: 2008-12-28
forum: General Help
---

### Post by Trevorius on 2008-12-28
I've been trying to install Moblock, Moblock-control, and Mobloquer for about 2 days now and have been having a number of problems. First, I tried installing using Adept, and it stalled when updating blocklists and finished saying there were errors. When I tried to start Moblock using Mobloquer, Moblock refused to start, saying "* Error 7: Missing file /etc/moblock/guarding.p2p." I figured it was just a common installation error, so I uninstalled it and tried to reinstall, but then Adept refused saying that dependencies weren't met and installation would cause a package break. 

At that point I tried doing it in Konsole using "sudo aptitude purge moblock, sudo aptitude install moblock" and it said that I needed a more recent version of libnfnetlink0 since I have 0.0.30 installed and it needs at least 0.0.33. Well Adept says I have the newest available version, so I scroogled the package and the only newer versions I could find were 32 bit, so I tried installing the 32 bit by using the force architecture command, but it wouldn't complete without removing the old version first, and in order to do that, it also wanted to remove "libnetfilter-queue1" for some reason.

At this point I decided to ask for advice, since I figured I could seriously mess up the system if I started removing packages I wasn't familiar with.

I'm using Kubuntu Hardy with a 64 bit notebook. I had moblock installed on the last version of Kub/Hardy I had before this and I don't recall there being any major issues...

Any suggestions would be helpful since I've read threads on about 5 different site without finding a solution.

---

### Post by Trevorius on 2008-12-29
I'll gladly supply any aditional info that could help shed some light on the situation. :)

---

### Post by Nepherte on 2008-12-29
when it says "missing file guardian.p2p", just create the file with:
```
sudo touch /etc/moblock/guarding.p2p
```

---

### Post by jre on 2008-12-29
@nepherte: Well, that will just stop the symptoms, but Moblock will still not be working as it should. All blocklists from blocklists.list need to be downloaded, so that /etc/moblock/guarding.p2p can be built.

So if someone has blocklist problems: Be patient and try again. Otherwise have a look at /var/log/moblock-control.log and check which blocklist fails to download.
Either try "moblock-control update", or
download it manually and copy it to the correct place, or
remove that list from /etc/moblock/blocklists.list if you don't want to use it.

About the dependency problems: I guess you have the intrepid sources for moblock-deb in your /etc/apt/sources.list. change that to the hardy ones. There is definitely no need to tamper with your installation manually.

---

### Post by Trevorius on 2008-12-31
> **jre said:**
> 
About the dependency problems: I guess you have the intrepid sources for moblock-deb in your /etc/apt/sources.list. change that to the hardy ones. There is definitely no need to tamper with your installation manually.I can assure you, I was very careful when adding sources, and when I checked this file, there was not a single mention of the word "Intrepid". All the sources are Hardy. So as it stands, I still can't install Moblock or Moblock-control with either Adept or APT. 

I'm hoping I can avoid having to reinstall, but I can't imagine running a system for any length of time without MB since I don't want to run Ktorrent without it. However, I remember back when using Azureus with Windows I was able to add the block lists directly into the program. Is there any way to do this with Ktorrent or Utorrent, and if so, would that be as effective as running MB?

---

### Post by jimmy the saint on 2008-12-31
I would recommend trying deluge.  It does everything the others you mentioned does (for the most part) and has a very nice feature: it runs in daemon mode.  That is cool becasue you can control the program from a remote machine using the standard, full featured gui instead of a crappy web interface.  It also has a blocklist plugin so you can have it load whatever list you want.  In order to get the gui/program seperation you need to install the newer version from their site or repos.

I run it on my home server and control it from my main box.  The benifit is that my main machine does not suffer the performance hit that it usually does if it's managing 100's of connections AND I want do something internet related.

---

### Post by Trevorius on 2008-12-31
I really appreciate that great suggestion, and if I can't get Moblock installed I'm definitely going to do that. But I'm still hoping someone might be able to shed some light on Moblock's refusal to install. I suspect there's probably something fairly simple I'm missing.

---

### Post by jre on 2009-01-01
I never heard of these problems from other hardy users, so I guess something is wrong on your site.

I checked the dependencies of MoBlock hardy. They should work for you:
moblock 0.9~rc2-21+hardy depends on
libnetfilter-queue1 (>= 0.0.13) and
libnfnetlink0 (>= 0.0.30)

moblock 0.9~rc2-21+intrepid depends on
libnetfilter-queue1 (>= 0.0.13) and
libnfnetlink0 (>= 0.0.33)

So I can only guess that something is wrong in /etc/apt/sources.list (or a file in /etc/apt/sources.list.d/) or in /etc/apt/preferences.

Make sure you only have the entry
```
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) **hardy** main
deb-src [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) **hardy** main
```
and nothing with intrepid.
Do a "**sudo aptitude update**" to make sure your settings are really applied.  This way you should get the correct amd64 version for hardy.

What's the package version of moblock in aptitude? What's the output of "dpkg -l moblock".


As a last resort you might build your own packages from source as explained on moblock-deb.sf.net.

---

### Post by Trevorius on 2009-01-04
"dpkg -l moblock" gives:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pn  moblock        <none>         (no description available)
```

As far as the files you mentioned, I did a ctrl+F search of the file /etc/apt/sources.list and the file doesn't contain the word "intrepid" anywhere.
The folder /etc/apt/sources.list.d/ only contains two files and they're both medibuntu source lists and both contain only hardy. The file /etc/apt/preferences doesn't exist. I did the sudo aptitude update after reconfirming the sources were correct and yet I'm stil getting the same errors wit Adept saying "There was an error committing changes. There was possibly a problem downloading some packages, or else the commit would break packages" and APT asking for libnfnetlink0 version 0.0.33. 

Once I get the time I'll try building the pkg from source, but I usually hate doing that because it often seems like I spend ages hunting down dependencies.

---

### Post by Trevorius on 2009-01-04
Alrite, instead of building a new MB pkg, I've managed to install iplist which seems to be a good alternative. For some reason it wouldn't download and update the blocklists so I had to do it manually by going to the bluetack site and saving each gz file, but I didn't mind too much due to all the issues I've had with MB. The only thing is that I'll probably have to do this every time I want to update the lists. Thanks for all your help everyone, especially jre with all the research you did. I know the issue isn't really resolved, but I'm going to let it be for now. Of course, if anyone has any new info about the MB issue, I'll always be interested to hear it.

---

