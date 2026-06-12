---
title: "&quot;Your session only lasted less than 10 seconds...&quot;"
date: 2006-02-21
forum: Desktop Environments
---

### Post by jigantor on 2006-02-21
I've been using Breezy for a couple of weeks and until this morning it was going great. I should also point out that I'm still quite a newbie, so as they say, "talk to me like I'm a 5 year old."

This morning I started my computer, Ubuntu booted up and got to the login screen completely normally. I entered my username and password, but instead of loading the desktop an error message appeared telling me that "Your session only lasted less than 10 seconds", and this might be because of a lack of disk space or an installation problem. Given that I have at least 120GB free space on my HDD, the first option seems unlikely. The error script it gave me was:

[FONT="Courier New"]_IceTransNoListen: unable to find transport: tcp
_IceTransMkdir: ERROR: euid! = 0, directory /dev/X will not be created
_IceTransMkdir: ERROR: cannot create /dev/X
_IceTransPTSOpenServer: mkdir /dev/X failed, errno = 13
_IceTransOpen: transport open failed for pts/Engelbert
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: protocol is not supported by a ISC connection
_IceTransOpen: failed for isc/Engelbert
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by by a SCO connection
_IceTransOpen: transport open failed for sco/Engelbert
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

**(gnome-session: 8452): WARNING**: unable to read ICE authority file: /home/tim/.ICEauthority[/FONT]

I think I transcribed that right from my scrawl...

All the sessions except the terminal one give me exactly the same error, so along with the errors themselves I assume the problem is to do with GNOME. I don't really know my way around the terminal on my own, so if anyone can give me some guidance on what do to it'd be very much appreciated!

---

### Post by codejunkie on 2006-02-21
[QUOTE=jigantor]I've been using Breezy for a couple of weeks and until this morning it was going great. I should also point out that I'm still quite a newbie, so as they say, "talk to me like I'm a 5 year old."

This morning I started my computer, Ubuntu booted up and got to the login screen completely normally. I entered my username and password, but instead of loading the desktop an error message appeared telling me that "Your session only lasted less than 10 seconds", and this might be because of a lack of disk space or an installation problem. Given that I have at least 120GB free space on my HDD, the first option seems unlikely. The error script it gave me was:

[FONT="Courier New"]_IceTransNoListen: unable to find transport: tcp
_IceTransMkdir: ERROR: euid! = 0, directory /dev/X will not be created
_IceTransMkdir: ERROR: cannot create /dev/X
_IceTransPTSOpenServer: mkdir /dev/X failed, errno = 13
_IceTransOpen: transport open failed for pts/Engelbert
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: protocol is not supported by a ISC connection
_IceTransOpen: failed for isc/Engelbert
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by by a SCO connection
_IceTransOpen: transport open failed for sco/Engelbert
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

**(gnome-session: 8452): WARNING**: unable to read ICE authority file: /home/tim/.ICEauthority[/FONT]

I think I transcribed that right from my scrawl...

All the sessions except the terminal one give me exactly the same error, so along with the errors themselves I assume the problem is to do with GNOME. I don't really know my way around the terminal on my own, so if anyone can give me some guidance on what do to it'd be very much appreciated![/QUOTE]
try pressing ctrl+alt+F1 to switch to the command line login with your username & password and enter
```
sudo chown tim:tim /home/tim/.ICEauthority
```
then 
```
sudo chmod 600 /home/tim/.ICEauthority
```
restart gdm with 
```
sudo /etc/init.d/gdm restart
```
and try logging in again.

---

### Post by jigantor on 2006-02-21
Well, that fixed it. Thanks!

Out of curiosity, what actually happened and why might it have? Mostly so I can avoid doing it again...

---

### Post by codejunkie on 2006-02-22
[QUOTE=jigantor]Well, that fixed it. Thanks!

Out of curiosity, what actually happened and why might it have? Mostly so I can avoid doing it again...[/QUOTE]

the permissions of that file got changed, 
it could have happened many different ways for example.
if you right click on a file go to the permissions tab and change the permissions, by using the "chmod" or "chown" commands on a file, by running a script that changes it. it's hard to say with 100% certainty how it got changed but those are a few things that could of happened.

---

### Post by bored2k on 2006-02-22
Every once in a while, K3B is responsible for messing that file up too.

---

### Post by John Jason Jordan on 2006-02-22
[QUOTE=bored2k]Every once in a while, K3B is responsible for messing that file up too.[/QUOTE]
It's not just k3b. Lots of KDE programs can do it to you. I had it happen to me after installing and running kivio.

And I use a slightly different solution when it happens. It turns out that the system will create a new .ICEauthority file, so you can just delete it. I just Ctrl-F1 to the command line, navigate to /home/jjj, and then do "rm .ICEauthority." Then I Ctrl-F7 back to the login prompt, and I can log in as usual again.

---

### Post by jphantom on 2006-02-22
Chances are you ran a program with a GUI using sudo instead of gksudo

---

### Post by Mujaheiden on 2006-02-24
Same here
the rm .ICEautohirty did the trick, THX.

I had to remove some directories from another users ~, and started 
sudo konqueror for that. Was that wrong?

---

### Post by NoNo_231 on 2006-03-01
I had he same problem. I installed the k3b and when trying to write to a cd asked to do something (I think to mount CDRW) using sudo. Reading the previous I have to say that probably that sudo used in k3b did the problem.

However I used another way to solve the problem. I got in the command lin and opened .ICEauthority with openoffice (using sudo). I realised that some characters probably were not in utf-8 because I got some question marks. I booted in another computer with live cd, saw the differences and fixed it. I am not very sure what I did; They only thing I did is to delete the questionmarks and make it the same as .ICEauthority of live system, with the only difference the computer name. The 4 lines text became 2 lines. I saved it and then booted ok. Does anybody knows if this could make the system unstable? The only diference I noted so far is that it is faster (I really don;t know how but it is). And the user/bin/X11 is a shortcut to usr/bin. (I think that was a dir before that, but I'm not sure). 

Thanks

---

