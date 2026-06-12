---
title: "Remove upstart"
date: 2010-04-26
forum: Desktop Environments
---

### Post by pksings on 2010-04-26
How does one remove upstart and go back to sysV init?

Can it be done?

PK

---

### Post by Skaperen on 2010-04-26
I feel your pain.

It can be done.  But it is a pain all its own because an increasing number of things expect upstart.  Such dependencies exist in the packages which want to put in an upstart style script.

---

### Post by sisco311 on 2010-04-26
May I ask you why?

Ubuntu uses Upstart since 6.10. Upstart is backwards compatible with sysvinit scripts. 

While in theory is possible, there is no easy way... I don't see any benefits...

---

### Post by pksings on 2010-04-27
Why?

Because I cannot find what to edit or change to make my machine boot all the way, stops when it cannot mount my SATA disks, which then required me to drop to the command prompt, type mount -a, then exit, and then it would finish booting. I no longer could reboot remotely if I updated it while not at home, which I have done during business trips. And it in fact made rebooting a pain. Not needed often,but painful when it was.

Just to close the thread, I decided to try 10.04, the new LTS release and upgraded yesterday, it's still Beta, but seems to solve this problem, boots just fine.

---

### Post by keybuk on 2010-04-28
> **pksings said:**
> Why?

Because I cannot find what to edit or change to make my machine boot all the way, stops when it cannot mount my SATA disks, which then required me to drop to the command prompt, type mount -a, then exit, and then it would finish booting. I no longer could reboot remotely if I updated it while not at home, which I have done during business trips. And it in fact made rebooting a pain. Not needed often,but painful when it was.

Just to close the thread, I decided to try 10.04, the new LTS release and upgraded yesterday, it's still Beta, but seems to solve this problem, boots just fine.

Did you file a bug?  We could have probably solved it.

Though from the sounds of it, we fixed the problem you were having if it's all working in 10.04?

---

### Post by 3rdalbum on 2010-04-28
> **pksings said:**
> Why?

Because I cannot find what to edit or change to make my machine boot all the way, stops when it cannot mount my SATA disks, which then required me to drop to the command prompt, type mount -a, then exit, and then it would finish booting. I no longer could reboot remotely if I updated it while not at home, which I have done during business trips. And it in fact made rebooting a pain. Not needed often,but painful when it was.

Just to close the thread, I decided to try 10.04, the new LTS release and upgraded yesterday, it's still Beta, but seems to solve this problem, boots just fine.

Yeah I was going to say that the "mountall" package in Ubuntu 10.04 has had many bugfixes, and that I remembered reading the changelogs for one version saying something about fixing this problem.

---

### Post by Skaperen on 2010-04-28
Desktops environments tend to work on a more careful basis in terms of not messing things up when something unexpected happens.  If a permanent drive cannot be mounted, that's unexpected.  Dropping to a command prompt right then lets the user determine the issue and deal with it (despite often requiring guru level knowledge to do it).  I'm not sure I'd want it to be any other way for a desktop.

For a server, that can be different.  They can be remote.  I want a server to make every effort to come up, no matter what.  I have built a whole init system just for that purpose (it wasn't BSD style or SYSV style or UPSTART style ... it was a whole different scheme ... and it was built on top of Slackware).  I now run some Ubuntu servers, and have a few times had a problem where they fail to come up and so I run into the computer room to see what's wrong (in many cases various bugs with other things, such as ifup/ifdown, and I deploy workarounds to deal with it).  For distant remote servers, I would not run Ubuntu Server at all, unless someone would always be on site there to deal with it.

---

### Post by diazepam on 2010-05-22
Yeah i agree -- im rolling out production servers and now i have this beta-style software replacing[FONT=monospace] [/FONT]/sbin/init daemon.  

LTS Server Platforms are mean to be  time proven, robust systems not playgrounds for new concepts like upstart and samba4.  If it was ubuntu desktop edition i woulnt mind as much but on a production machine (where time is money) i cant see the benefit.

---

### Post by 3rdalbum on 2010-05-22
> **diazepam said:**
> Yeah i agree -- im rolling out production servers and now i have this beta-style software replacing[FONT=monospace] [/FONT]/sbin/init daemon.  

LTS Server Platforms are mean to be  time proven, robust systems not playgrounds for new concepts like upstart and samba4.  If it was ubuntu desktop edition i woulnt mind as much but on a production machine (where time is money) i cant see the benefit.

It has to be implemented some time, and it's not like Upstart is new (been in Ubuntu for years, albeit emulating Init) and the LTS is the "playground" for the new technology (Upstart is in its current form in Ubuntu 9.10). Fedora is also moving across to Upstart.

Init may be mature, but it's also slow and inflexible for modern systems. Init starts services based on a hardcoded list of everything that you could possibly need. Upstart starts services based on a system of dependencies, so depending on your system's hardware and software configuration, things will start in a more appropriate order (or might not start at all, if they're not needed). Init certainly has problems with how distro developers choose what order things should start in to get everything to actually come up.

---

### Post by diazepam on 2010-05-22
Yeah i guess that is my point - Fedora is RedHats playground for **Bleeding Edge**/experimental software.  Its the place they test before they implement into a server environment.  

Innovation is great but test it out on the desktop first - this is the exact reason that the Fedora project exists.  It  lets people play and get used to it, file bugs and smooth things out  

However Ubuntu LTS server edition is not the place to put software that is 'under development'.  Im sure if you gave the example of Fedora as you did in the above post that it would make more than a few CIO anxious about adopting Ubuntu in production environments.

---

### Post by Legend1222 on 2010-05-24
Yeah, I've got to chime in here. I've given upstart a chance for many versions now, as pointed out above. It is a nightmare. Its not more configurable, its less configurable and radically unstable, AND undocumented. Everything everyone used to claim about Linux is now true. 

Upstart has taken away the benefit of running Linux machines. Unfortunately this is me and my boss talking. We've been searching for six hours now to try and figure out how to get one stinking runlevel to boot to the command line. All we can find is that its an all or nothing deal. Thats BS. Whos stupid idea was it to integrate gdm like that? And the answer isn't edit  /etc/init/gdm.conf. That doesn't work. It gives a huge font and leaves you on the wrong tty. 

If we wanted windows, we would have gone to Windows (and if all Linux distros are going to upstart, be may... :( ).

There is/was a way to implement upstart while still maintaining the SysV logic and stability. Ubuntu choose not to do that. I can only hope that Red Hat does better. 

Upstart is a deal breaker in a professional environment right now.

---

### Post by pete_m on 2010-05-31
in the middle of a tortuous but interesting upgrade from Karmic to Lucid/ Sid...i've been confronted with the new(ish)  dependency-based boot using LSB in init.d scripts.

and a number of my init scripts are not equipped, despite the fact that none of these are mentioned on the debian( lintian) reports about this.  .which implies it should be fixed.

i'm a comparitive Linux-newbie and came across this interesting thread . .
although i've read plenty suggesting that fresh installs of new releases are often advisable, i have put and configured enough extra stuff on my system to wish to pursue an upgrade path .. 



but. . 
apt-get dist-upgrade ( -s ) does a huge bunch of stuff and then wants to remove Upstart but ( presumably in the policy part of the package ) advises against it .  .
unless you know exactly what you're doing  - which i don't yet.  . .

i've tried 
aptitude why upstart  . .only ubuntu-minimal is shown . .
perhaps this indicated that all the others who may have been using upstart would now be content with the LSB dependency-based boot . ..

if i could remove upstart  "Yes,do as i say !"
 - perhaps the LSB system would then be able to be put in place.
 Perhaps a pity that [this thread]("http://ubuntuforums.org/showthread.php?t=1454106") is closed . .

Any guidance, wisdom, links and observations around this would be much appreciated.  


First screenshots - more soon - of my work in progress at

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)



BTW.
is there ( or could there be ) an apt-get command to say

what - ( do i need ) for pkg - my dependencies 
what-if ( i removed) pkg  - who depends on me

---

### Post by epoch1970 on 2010-06-16
Upstart is an absolute pita on a server. I was a bit hasty in switching to Ubuntu from Debian when 10.04 LTS came out, it seems:
 - NFS breaks (portmapper) -> upstart issue.
 - bridging a bonded interface fails -> upstart issue.

I guess nobody wants NFS, bridged VMs, and link aggregation on a server...

Lenny is not under upstart. I'll have a look at the state of KVM in Lenny and if its ok, I'm switching back pronto.

I'll have a few ubuntu machines in VMs..

Greets.

---

### Post by pete_m on 2011-01-29
Belated update in case it's of interest...

Dumped upstart. using sysvinit locked to 2.88 -still don't waant to mess with the parallel boot LSB thingies !
All works well but had to replace network

Why dump upstart ? - because itdoes  seem to want to lock users in to Ubuntu- perhaps in the interests of a stable advanced desktop enironment. But it  idoes also seem to close the doors on the limitless flexibility of vanliall sysvinit.
Everything worked fine with the exceptfor of Wifi, and I've installed wicd as a very satisfactory solution,


more in this veincoming  at
[http://placid-linux.icefactory.heliohost.org ]("http://placid-linux.icefactory.heliohost.org")

---

