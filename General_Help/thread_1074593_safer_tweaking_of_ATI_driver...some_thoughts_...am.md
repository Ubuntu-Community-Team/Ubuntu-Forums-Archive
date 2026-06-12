---
title: "safer tweaking of ATI driver...some thoughts ...amdpcsdb"
date: 2009-02-19
forum: General Help
---

### Post by zika on 2009-02-19
every now and then users complain about ATI proprietary driver. I wish to share a bit of experience in order to help them solve their problems. it is going to be quite short and I really hope someone will get a use of it.

namely, we all start tweaking ATI driver by changing our /etc/X11/xorg.conf. we add a couple of switches (called Option) and (very few) use```
aticonfig --input=/etc/X11/xorg.conf
``` to make driver aware of the change we made. every time we do that we update a file **/etc/ati/amdpcsdb**. 

and, {if,when} we are unhappy with the outcome we simply remove the option from the xorg.conf and believe that the switch was turned off. well, it is not even if You've *aticonfig --input=/etc/X11/xorg.conf*. 

it stays in the aforementioned file even though that option was removed from xorg.conf. and that is the (in my opinion) the root of many problems. we are mislead by the fact that the xorg.conf was backed-up to a file xorg.conf.fglrx-(0 and so on). 

in order to undo the change You've made it is **not** enough to put back the xorg.conf that was there before You've made the change but You have either to switch that Option in /etc/X11/xorg.conf by changing the value of the **(remaining)** option and do *aticonfig --input=/etc/X11/xorg.conf* or to change the value in aforementioned file. 

I've always taken the former path and I am not sure about the latter but I do believe it would work since it is textual file. so, all Your tweaking with the ATI driver accumulates in the /etc/ati/amdpcsdb file. [B]*even *bad* options You tried are kept there, even though they do not work or are illegal ... what is worse, those settings get inherited by the new version of the driver ...*
[/B] 
if You want a clean start You think that```
aticonfig --initial -f
```will do the job.
or ```
cp /etc/ati/amdpcsdb /etc/ati/amdpcsdb.backup
cp /etc/ati/amdpcsdb.default /etc/ati/amdpcsdb
```but it will not. changing the values in /etc/ati/amdpcsdb does not stick. it bounces back to the state before edit.

so, once You really messed up with ATI driver the only thing is to uninstall it (sudo sh /usr/share/ati/fglrx-uninstall.sh), delete /etc/ati/* and make a clean install. even better, through one ```
sudo dpkg --reconfigure -phigh xserver-xorg
``` just to be sure.

at the beginning I thought it would be easier but ... it proved that its better to try all this before it breaks down ... it helped me a lot with the transition to he new kernel weeks ago.

---

### Post by zika on 2009-02-20
I've just DL-ed ATI Catalyst + driver 9.2 (Ctalyst 2.5, driver 8.582) and done unistall of the previous driver, removed everything from /usr/share/ati and installed new driver+Catalyst  with aticonfig --initial and reboot...

to my surprise **all** the values from my previous driver and of all of my previous tweaking **are still there in new** amdpcsdb :( it is immortal ... ;)

I'm out of ideas how to clean that. if anybody has any idea, please do not hesitate ... ;) where that data could be stored?

there is a long "solution". I could set all the values again in xorg.conf (or by aticonfig ...) but with the default values ... that will be long journey. 

nevertheless the new driver is promising ... if only I could make it to use defaults to have a clean start. :)

---

### Post by notoriousdbp on 2009-02-20
Does it solve the flickering video problem and does logging out and switching users work OK now as I had tried version 9.1 and had problems.

---

### Post by zika on 2009-02-20
I did it! just list the amdpcsdb as a text file and locate Your options. they are, usually in DDX section. just do ```
sudo aticonfig --del-pcs-key=DDX,option_that_You_want_to_remove
```now I have a clean start point for this new driver ... :) it took some time to delete them all but it was worth it ...

still I do not know where they were stored to survive all the cleaning I've done before install-ing a new driver ...

---

### Post by zika on 2009-02-20
> **notoriousdbp said:**
> Does it solve the flickering video problem and does logging out and switching users work OK now as I had tried version 9.1 and had problems.
I did not have those problems even with 9.1 so I could not tell. XV video is now just OK. no more X11 ... ;)

---

### Post by Pitboss on 2009-02-22
If I understood you right you wanted me to post this

```

[AMDPCSROOT/SYSTEM/DDX]OGLFMTA2R10G10B10Enable=V0
[AMDPCSROOT/SYSTEM/DDX/RECENTMODE]
EnableRestore=V1
[AMDPCSROOT/SYSTEM/DDX/RECENTMODE/SCREEN00]
Width=V1680
Height=V1050
Refresh=V60

```

The upper is the only match of the string AMDPCSROOT/SYSTEM/DDX

```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

My xorg.conf is configured by the command

```

aticonfig --initial -f

```

---

### Post by zika on 2009-02-22
is there anything else between 
[AMDPCSROOT/SYSTEM/DDX] and [AMDPCSROOT/SYSTEM/DDX/RECENTMODE]
except 
OGLFMTA2R10G10B10Enable=V0 ?

thank You for participating. ...

if there is not, then I have no hint. if there is, I might ...

---

### Post by Pitboss on 2009-02-22
> **zika said:**
> is there anything else between 
[AMDPCSROOT/SYSTEM/DDX] and [AMDPCSROOT/SYSTEM/DDX/RECENTMODE]
except 
OGLFMTA2R10G10B10Enable=V0 ?


Unfortunately, except **OGLFMTA2R10G10B10Enable=V0** there is nothing else there. I think it's pretty odd that you don't experience the memory leak bugs. I don't know what to think now :)

Last time I installed 9.2, I removed /etc/ati/* so I don't expect the bug to have something with the driver's options.

---

### Post by zika on 2009-02-22
> **Pitboss said:**
> Unfortunately, except **OGLFMTA2R10G10B10Enable=V0** there is nothing else there. I think it's pretty odd that you don't experience the memory leak bugs. I don't know what to think now :)
Last time I installed 9.2, I removed /etc/ati/* so I don't expect the bug to have something with the driver's options.

You're just on the track. that is why I've asked You to send me this peace of puzzle. if You read my previous posts in this thread You'll see that that is just what I'm searching for. on my machine the history of my tweaking of ATI driver somehow survived erasing even /etc/ati/*. now I'm erasing it bit by bit and I think I'm finally close to it. for example, I've just deleted 3 keys from the amdpcsdb that I even do not know who introduced: EnableRandr12, RequestMSI, EnableMonitor. there must be the third piece of stuff that keeps these Options, first being xorg.conf, second amdpcsdb ... I'll keep looking now that the cleaning operation is (almost) over. it seems that a proper way of dealing with ATI driver is through```
aticonfig --set-pcs-val=PREFIX,KEY,VALUE
or
aticonfig --set-pcs-str=PREFIX,KEY,STRING
and
aticonfig --del-pcs-key=PREFIX,KEY
```
while checking every step through /var/log/Xorg.0.log since even in a ATI documentation there are mistakes, for example, about TLS ... a string instead of value.

by clearing this stuff I would be able to comprehend and control this driver, I beleive, more efficiently. but, on the other side, this is a futile effort since we are going to have new FOSS driver (radeonhd) in JJ with different philosophy ... ;) I hope ...

---

### Post by zika on 2009-02-22
> **FormerSlacker said:**
> Nothing fancy here.

amdpcsdb
```
[AMDPCSROOT/SYSTEM/DDX]
OGLFMTA2R10G10B10Enable=V0
EnableRandR12=SFALSE
RequestMSI=SFALSE
MultiviewXineramaNo3D=V1

```xorg.conf
```
Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection
```

can You trace where```
EnableRandR12=SFALSE
RequestMSI=SFALSE
MultiviewXineramaNo3D=V1
```comes from? it is not in Your xorg.conf, at least it is not now ... ;)

do You have multiple displays? and, what would happen if You would remove those keys from You amdpcsdb ... please, do not do anything You are not comfortable with. I'm not sure what would happen so do not take this as my advice... just, if You, in any given moment, do remove those keys please give us here the summary of the outcome. I had first of those keys and I have removed them with no visible effect but that does not mean that that is the rule. please do not do anything You are not comfortable with. just try to remember if You have added those keys in some tweaking.
(there is above method how to, in the right way, remove those keys)

---

### Post by FormerSlacker on 2009-02-22
Thanks for the advice, but that didn't seem to help. Removing the mysterious options in DDX didn't solve it.

---

### Post by zika on 2009-02-25
just for sake of (whim)-testing I reverted my machine to open-source video driver (ATI-radeon) from ATI restricted 9.2 and I've seen massive decrease in memory usage by Xorg. and, what is even more important, memory usage is contained regardless of kind of applications and videos etc used ... since I do not use compiz and similar stuff I'm hooked on open-source driver for some time.
it showed improved stability also. compiz and similar are small price to pay for what I see as a gain. sorry, ATI ...

---

### Post by jvdurme on 2009-10-24
The only way to permanently delete the **amdpcsdb **file is to copy amdpcsdb.default over it while X is not running, because when fglrx loads and quits, the file is being written.
So start Ubuntu in recovery mode, choose root prompt and copy amdpcsdb.default over amdpcsdb.
Restart and you should have a clean database.

cheers.

---

### Post by zika on 2009-10-25
> **jvdurme said:**
> The only way to permanently delete the **amdpcsdb **file is to copy amdpcsdb.default over it while X is not running, because when fglrx loads and quits, the file is being written.
So start Ubuntu in recovery mode, choose root prompt and copy amdpcsdb.default over amdpcsdb.
Restart and you should have a clean database.
cheers.Yes, that is one efficient way of doing it. I've used that method at the time I used fglrx. I've turned to open-source in February and never turned back ...

---

### Post by jvdurme on 2009-10-29
> **zika said:**
> Yes, that is one efficient way of doing it. I've used that method at the time I used fglrx. I've turned to open-source in February and never turned back ...

I guess you are not using 3d rendering then, Zika?
I need it almost everyday, so I have to use the fglrx driver. Which is working ok now, even in dual screen mode.
Suspend/hibernate can't wake up though. It's a compromise I have to accept. ;)

---

### Post by zika on 2009-10-29
> **jvdurme said:**
> I guess you are not using 3d rendering then, Zika?
I need it almost everyday, so I have to use the fglrx driver. Which is working ok now, even in dual screen mode.
Suspend/hibernate can't wake up though. It's a compromise I have to accept. ;)Totally right. I think You should try 2.6.32 kernel with radeon.modeset=1 without fglrx and You will be pleasantly surprised.
Update: I've just checked, even without radeon.modeset=1 it works, very well indeed. I check 3D only once in a while since I really do not have a need for it. Mathematicians do not make great difference between number of dimensions except when it really matters ...

---

