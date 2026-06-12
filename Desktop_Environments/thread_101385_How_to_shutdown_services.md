---
title: "How to shutdown services"
date: 2005-12-09
forum: Desktop Environments
---

### Post by ShirishAg75 on 2005-12-09
Hi all,
         This is the from looking at the GUI boot process as well as some things while shutting down the system
            Starting up :-
           Starting RAID Devices
           Starting Enterprise Volume Management Services
           Starting clock synchronization to ntp.ubuntulinux.org

        Now I have no RAID Devices, neither did I install as a server or something, I did the default installation so why these services are starting is a mystery to me.
        Now while shutting down Ubuntu the following services are shutting down :-
             cupsd
             HP Printing Services
             Bluetooth services
             rsync
                        AFAIK cupsd  & HP printing System are useful if a printer is installed, I have no printer,
similarly Bluetooth I have no bluetooth devices. rsync would be useful for wake on lan or something like this which is not needed by me. My main aim is to use the limited memory to the stuff which I would like to work with. Also gave a top -I list & it gave 68 services out of which 67 are sleeping & 1 top is the only 1 running. If somebody needs can send the output for top to him/her. Hoping to get some info. how to shutdown these services so they don't start up. Also at least how it arrived at RAID stuff & all when mine is a simple IDE 133 7200 rpm 80 GB HDD.
                Somebody told me there's a package called vum which has a good GUI to disable or uninstall these services which are not needed. I don't have a working Net connection through Linux but 've got good connectivity through windows, so if any files are to be downloaded their locations in [http://,](http://,) ftp:// in that way atleast for now as well as how to install the packages after they've been downloaded. thnx in advance.

---

### Post by Lambert on 2005-12-09
I think they meant bum which you can get [here]("http://http://packages.ubuntu.com/breezy/admin/bum"). 
Then you just use sudo dpkg -i name.deb to install

You'll want to make sure you have all dependencies installed though which are these.

2.1.3-1 - gksu (0 (null)) sysv-rc (0 (null)) perl (0 (null)) libgtk2-perl (2 1.100-1) libglib-perl (2 1.100-1) liblocale-gettext-perl (0 (null)) libgtk2-gladexml-perl (0 (null))

If you can get some kind of connection though and do this from synaptic it would be easier as dependicies would take care of themselves.

If you need any of the dependecies search [here]("http://packages.ubuntu.com/breezy/allpackages").

You can also look into the command update-rc.d This command basically removes the link from your run level to the startup script. Removing the raid part would be something like this.

sudo update-rc.d mdadm remove

read more in the man page.

---

### Post by ShirishAg75 on 2005-12-10
thnx but how do I find the dependencies is there or not, justgiving each package name & -v for version is good enough or something else. Although will be trying out the stuff but what is a good way to know if the dependencies have been installed from the cd or not?

---

### Post by ShirishAg75 on 2005-12-10
people, lookin for some replies here :)

---

### Post by syncme on 2005-12-10
You might want to have a look at this thread:

"HowTo: Speed up ubuntu boot process - the way you can feel it."
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

It talks about services and streamlining the system. 

I hope you find this useful, I did. Please let me know either way.

Syncme

---

### Post by ShirishAg75 on 2005-12-10
if I was able to use apt-get then there would've been no problems, the issue starts with not having a network connection with GNU/Linux, once that is there then these things can be looked for, my issue is getting tht perl-script sys-rc-conf, is that on the Ubuntu CD or that needs to be downloaded from the net. If it needs to be downloaded then the exact location as using windows for all download/surfing needs, (driver issues with the modem/router) anyway also would be needing instruction as to what dependencies are there & how to check for if the dependencies meet the requirement. Although 've downloaded the whole document & will be reading the thread off-line later on. Anybody knows anything how to go about doing this.

---

