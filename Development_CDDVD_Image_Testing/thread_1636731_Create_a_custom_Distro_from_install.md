---
title: "Create a custom Distro from install"
date: 2010-12-03
forum: Development CD/DVD Image Testing
---

### Post by wililupy on 2010-12-03
Hello,

I have been messing around with Reconstructor to create a custom distribution of Ubuntu where I work. 

Basically, we want to create thin-clients to connect to our VMware-View Environment on older PC's and don't want to have a Windows foot print on them. 

For ease of use, we would like it to boot up into Ubunutu, and on the desktop be our VPN client, RDP client and VMware-View client. No other applications will be installed (except the neccissities for gnome and ubunut, but no office, mulitmedia, games, internet except firefox and above mentioned tools).

I have an ubuntu desktop already setup for this, but the base images is over 2 GB in size. I think this is a bit bloated since I did a full desktop install, then used the Ubuntu Software Center to remove everything I didn't want, and it does not totally delete everything off the box when used.

To get to the bottom line, I would like to basically image my install into either a live boot CD ROM or even better, in to a PXE boot environment.

Any ideas on where to start? Does anyone know of any hurdles that I may run into?

Thanks,

---

### Post by ggallozz on 2010-12-05
YESSS ! I'm interested too.

I really appreciate having my old laptop Ubuntu install to ba on a CD, yet customised, for any happenings...
;-)


tnks in advance to any geek would help us, poor newbies.... :-)

---

### Post by TechWiz2100 on 2010-12-05
Well, don't know if this is exactly what you are looking for, but Ubuntu server does not have all those extra packages installed because its console only but you can choose to install an interface like KDE or Gnome during installation and the footprint is relatively small.

Or you can have it load Ubuntu Server and automatically run a script on login that will load your VMware software or whatever else is needed.

Other than that, I would say pick a different distro like DSL which has a minute footprint or a netboot linux like PXELinux since those 2 distro's are designed for what you have in mind.

---

### Post by ggallozz on 2010-12-06
> **TechWiz2100 said:**
> ...... Other than that, I would say pick a different distro like DSL  ....

sorry, but you're out of the matter.

We want our distro install,(already done and customised) to be simply stored in a replicable, re-distributable image, that's it.

it's OK for you, [wililupy]("http://ubuntuforums.org/member.php?u=412977") ?

I think that [REMASTERSYS]("http://www.geekconnection.org/remastersys/") is for now the one that can answers to our needs, it compresses the install's image so that should fit in a CD. 

What I complain that I didn't find any tool that can "lighten"  the installed distro more than manually uninstall unneeded packages.

I'm still working on it.....

---

### Post by TechWiz2100 on 2010-12-06
> **ggallozz said:**
> sorry, but you're out of the matter.

We want our distro install,(already done and customised) to be simply stored in a replicable, re-distributable image, that's it.

it's OK for you, [wililupy]("http://ubuntuforums.org/member.php?u=412977") ?

I think that [REMASTERSYS]("http://www.geekconnection.org/remastersys/") is for now the one that can answers to our needs, it compresses the install's image so that should fit in a CD. 

What I complain that I didn't find any tool that can "lighten"  the installed distro more than manually uninstall unneeded packages.

I'm still working on it.....

Like I said, Ubuntu Server is a "lightened" version of Ubuntu because servers don't need all that other stuff added to Desktop Ubuntu and what you want is a kind of "Live CD" setup for Ubuntu Server set up with Gnome or KDE (similar to how windows does "thin" clients)

Basically what I'm saying is that you can install Ubuntu server with the necessary packages for a secure Gnome or KDE install which then becomes your "lightened" install image which you can then replicate via hard disk images. (~1-2GB)

For a streaming solution you can always try to set up something like OS X's live CD streaming thing for network installs of OS X because all Ubuntu Desktop CD's are Live CD's. (No client space needed)

And of course your final option is then to actually create a "bootable USB" out of your thin client's hard drive and throw in the Ubuntu CD that will then start Live CD. (~700MB)

I then suggested DSL so that you have the smallest possible footprint (~50MB) out of all the hard install options so that DSL will auto launch your VMware software instead of straight linux anything, and PXELinux for the same purpose but no hard install.

None of my options involve uninstalling anything to "lighten" Ubuntu, I'm simply giving you options that are already light.

Although I think a Ubuntu Thin Client "remix" might be pretty awesome if Ubuntu Server gets added compatibility with the thin clients. Then Ubuntu can take on Windows in the Enterprise world as well as the Academic world where thin clients are key to prevent system deterioration due to user abuse.

---

### Post by wililupy on 2010-12-09
Basically, what I have done so far is taken the Alternate install ubuntu disc, and gone through and pretty much removed everything that I don't need. I then added my Open View client for VMWare View and created custom.seed and splash graphics. 

The only thing I keep running into now is recreating the packages.gz file to exclude everything I have removed and include my custom deb package for View.

It has shrunk a little now that there is no OpenOffice.

I will take a look at those smaller distro's that you mentioned.

Thanks!

---

### Post by ggallozz on 2010-12-13
We are speaking about **client** install, not server.

so I made some try with Remastersys, and as wililupy, after cleaned out the installation , in my case Xubuntu, then made a Remastersys CD. I think is a good solution, the CD obtained this way (about 690Mb)  is also usable as Live CD.

for now I find this the simplest way to get our goal.

PS. Techwiz, talking here in Ubuntu forum about DSL or other such distros, isn't fair, i guess .... :-)
Also: DSL or similar, don't allow to have Synaptic software resources, neither the Ubuntu LTS main releases and such improving evolution.

---

### Post by TechWiz2100 on 2010-12-15
> **ggallozz said:**
> We are speaking about **client** install, not server.


Server installs like client and can be used as such with slight modifications to settings and the installation of certain packages.

> **ggallozz said:**
> PS. Techwiz, talking here in Ubuntu forum about DSL or other such distros, isn't fair, i guess .... :-)
Also: DSL or similar, don't allow to have Synaptic software resources, neither the Ubuntu LTS main releases and such improving evolution.

I spoke on DSL because its an option and just because this is a Ubuntu forum doesn't mean I can't suggest other alternatives to better suit your needs. =P

Also, you're probably right about DSL not being able to use Synaptic repos but Ubuntu server definitely has APT installed and definitely has the ability to add repos of any kind including the Synaptic's repos. I've used Ubuntu server for some time in the past and I was able to install X and Gnome on it to convert it into a desktop. I just as I said, needed to add some extra repos and packages.

If you want you can drop me a PM and I'll link you to some of the resources I used during the conversion from server to client-like

---

### Post by ggallozz on 2010-12-20
OK guys, 
I've had taken a trial with REMASTERSYS, and In doaed the work as we guessed.

Made a copy of the installed system (Xubuntu 10.04) whithout client settings to reduce the amount of data to be recorded, it made the job in a tenth of minutes. Got an .ISO file of about 650 Mb., burned it on a CD.

then I booted my PC with that CD and launched the install procedure. It took a bit long time, but I'm working on Pentium III -1200mhz.
Had just to specify newly my keyboard layout and partition settings as a new install, but everything I did install before, is on the disk now.
partitions were:
1 primary mounted as / (root), recreated and formatted
1 extended mounted as /HOME, just re-mounted as-is
1 for swap, just re-mounted

Anyway I've got back my system running normally with peripherals, custom appearance, home folders, etc.

so REMASTERSYS definitely does the job. One thing only I'd appreciate to be improved:
the ability to choose among custom settings to add to the back-up, only those that really are useful, like keyb layout.

best linux greetings to all !
:-)

---

