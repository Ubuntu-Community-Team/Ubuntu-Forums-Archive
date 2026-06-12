---
title: "system freeze"
date: 2005-07-21
forum: Desktop Environments
---

### Post by art on 2005-07-21
Hi forum
I am having complete system freezes this two days, seemingly out of nowhere. I am running 2.6.12 kernel which I compiled myself, with inotify patch. Is anyone having a similar problem. The last time I noticed there was a scrollkeeper-up process taking 100% CPU  before computer became completely non-responsive. Any help is more than welcome... Is there a way to see which process was the cause of the last freeze?
Thanks a lot!

---

### Post by art on 2005-07-22
Well at this point I kinda thing I found the solution. It only happens when I am at work, and there I use Cisco VPN to connect to wireless, at home I don't. So it must/might be relatated to that. I noticed in BUM I also have Open VPN (even though Synaptic says I don't have it installed, but it is in /etc/init.d), so I think that's where the coflict lies. Hopefully...

---

### Post by Chris Tucker on 2006-08-01
I have the same problem but its NOT related to the use of a vpn... during package installs scrollkeeper-up hogs the process and doesnt seem to do anything other than hog resources.

pressing ctrl+c on the update process seems to kill the child process of scrollkeeper-up, and allow the system to continue installing... 
really REALLY annyoing because its only happening on a server, which i have no physical access to. The system doesnt completely freeze, just slows to an extremely agonizing speed. any ideas are welcomed.

---

### Post by thechanklybore on 2006-12-31
The only fix I can find is to literally make all of the scrollkeeper binaries non-executable.

sudo chmod -x /usr/bin/scrollkeeper*

Not pretty at all - and I assume some documentation bits are no longer being updated, but TBH I'd rather not have processes sitting there with 96% CPU usage on a Dual-Core 3.2Ghz machine!

---

### Post by neverping on 2008-05-26
My system didn't freeze, but i have 90% of CPU usage and after 5 minutes it stopped.

I took a look at his manual...

$ man scrollkeeper

Which says:

"NAME
       ScrollKeeper - An open document cataloging and metadata management system.

DESCRIPTION
       ScrollKeeper is a system for managing document metadata.   Its  primary function  is  to  act as a card catalog for documents, keeping track of what documents are available, where they  can  be  found,  and  various attributes  of  the  documents such as their language, format, subject, version, and position in a contents list.  It also manages other  metadata such as document indices."

Ok, the binaries are other... so:

"SCROLLKEEPER-UPDATE(8)                                  SCROLLKEEPER-UPDATE(8)

NAME
       scrollkeeper-update  - identify new, modified, or removed OMF files and update the scrollkeeper databases

SYNOPSIS
       scrollkeeper-update [ -v ] [ -q ] [ -n ] [ -p database-directory ] [ -o omf-directories ]

DESCRIPTION
       This synchronizes the scrollkeeper database with the OMF directory.  It searches the scrollkeeper OMF directory to identify if any  files  were added,  removed, or modified and updates its internal database files to reflect any changes.

       This utility is generally executed as the last step of  installation, after the OMF file is copied into place.  It is also typically the last step of uninstallation, after the OMF file is removed.  Using this,  an administrator  can easily manually install and uninstall documents into the database.  It can also be run to guarantee the  database  is  fully up-to-date."

I checked its logs, which is:

/var/log/scrollkeeper.log

It was reading some "OMF" files. Sample of the log below:

May 26 09:53:59 scrollkeeper-update: Registering /usr/share/omf/windows/windows-nl.omf
May 26 09:54:00 scrollkeeper-update: Registering /usr/share/omf/windows/windows-nb.omf
May 26 09:54:00 scrollkeeper-update: Registering /usr/share/omf/windows/windows-eu.omf
May 26 09:54:00 scrollkeeper-update: Registering /usr/share/omf/windows/windows-hr.omf


After some time reading those OMF, it stops normally, as seen below:

May 26 09:54:02 scrollkeeper-rebuilddb: Done rebuilding ScrollKeeper database.

I think this process came up after a system update i had this morning. I didn't understand exactly why i need it, but i really want to write my researches here to some other people who googles for this behavior like i did. :)

---

