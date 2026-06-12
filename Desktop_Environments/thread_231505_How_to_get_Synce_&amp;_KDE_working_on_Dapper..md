---
title: "How to get Synce &amp; KDE working on Dapper."
date: 2006-08-07
forum: Desktop Environments
---

### Post by scotty64 on 2006-08-07
After spending a lot of time testing I finally got my Fujitsu Siemens LOOX 710 connected to Ubuntu Dapper / Kubuntu. Just to say it in the beginning:
USB syncing did not work, but bluetooth is your friend!
FYI: The PDA I am using uses Windows Mobile 2003.

1. Remove Synce-KDE if it is already installed, the RAKI provided with Dapper seems to be broken.

2. Install the following packages and their .dev packages:
liborange, libdynamite, librapi, librra0, libunshield plus the KDE header files.

3. I am assuming here you have a bluetooth system running. Otherwise install bluez-utils and kdebluetooth.

4. Create a file named "dun" in the /etc/ppp/peers directory containing these six lines:

nodefaultroute
noauth
local
192.168.131.102:192.168.131.201
ms-dns 192.168.131.102
linkname synce-device

5. Use the following commands to set up bluetooth for synce-serial connections:

sudo /usr/bin/dund --listen --msdun call dun
sudo /usr/bin/sdptool add SP

6. Download the following files from the synce project on sourceforge
( [http://sourceforge.net/project/showfiles.php?group_id=30550](http://sourceforge.net/project/showfiles.php?group_id=30550) ):

synce-kde-0.9.1.tar.gz
syncekonnector-0.3.2.tar.gz

7. Compile synce-kde - you may be prompted for missing libraries and headers!

tar -xzf synce-kde-0.9.1.tar.gz
cd synce-kde-0.9.1
./configure
make
sudo make install

8. Compile syncekonnector AFTER synce-kde is compiled and installed:

tar -xzf syncekonnector-0.3.2.tar.gz
cd syncekonnector-0.3.2
./configure
make
sudo make install

YOUR SHOULD BE READY TO GO AHEAD WITH IT NOW!

- Be sure the commands under 5. are issued. You have to do this only once per session! You may want to write a bootscript for doing this.

- Start raki from the KDE Utilities menu or from a command line (not as root!)

- Set up a bluetooth connection for Active Sync on your PDA. The raki icon should turn colored now and you should be able to configure your device for synchronization.

I hope more people succeed with this...
Good Loox!

---

### Post by ivomans on 2006-08-20
Thank you for this post. It helped me a lot to get my Ipaq 6340 connected to Kubuntu.

I experienced I had to install following packages before I could compile synce-kde (this might save others time when trying to compile this):
```
sudo apt-get install kde-devel libmimedir-dev libunshield-dev libdynamite-dev liborange-dev
   libsynce0-dev librra0-dev librapi2-dev kitchensync kdepim-dev
```

I can now run rapi and browse my files on my Ipaq through Bluetooth, using Konqueror with the url rapip://myipaq/  :) 

Unfortunately I got stuck in compiling syncekonnector. :-k 
During the make I get error:
> grep: /usr/lib/libfam.la: No such file or directory
/bin/sed: can't read /usr/lib/libfam.la: No such file or directory
libtool: link: `/usr/lib/libfam.la' is not a valid libtool archive


When I try to 'apt-get install libfam0 libfam-dev' it turns out libfam0 needs to remove almost the complete kde installation, which is obviously not what I intend to. :???: 
Any advice?

---

### Post by ivomans on 2006-08-20
I already found the answer to my question in this thread: [http://www.ubuntuforums.org/showthread.php?t=105464](http://www.ubuntuforums.org/showthread.php?t=105464)

So the solution was:
```
sudo apt-get install libgamin-dev
``` 
Then I could compile the syncekonnector.

Now it looks like there is a synchronize-action happening for the Appointments and Tasks, but in the end I don't see any appointment or task from my Ipaq in Kontact, or the other way around. So somehow the synchronization doesn't have any effect.

When I try to synchronize Contacts the complete Raki application crashes.

Hope somebody got an advice how to get this really functional now.

---

### Post by aurelieng on 2006-11-09
Hi folks,

I have a Dell Axim X50v and I am running Kubuntu Edgy Eft, and I would like to sync my PDA with kontact but it's not working. Here is the story:

What I did:
-----------

It was quite easy to install raki/synce by apt-getting the following packages :

libsynce0
synce-dccm
synce-kde
synce-serial
syncekonnector
kcemirror

Then I created a file /etc/udev/rules.d/60-ipaq.rules containing

# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start"
BUS!="usb", ACTION!="remove", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-abord"
LABEL="synce_rules_end"

What's working properly:
------------------------
- it's possible to access the PDA from konqueror with rapip:/
- it's possible to run kcemirror
- I even see the synce connector from the synchronization panel of kontact.

What's missing:
---------------

The problem is that I can't select Appointments/Contacts/Task in the "configure aximx50x" menu accessible from a left click on the colored raki icon in the systray. I have the following error message:

Wrong library type for [Appointments|Contacts|Task]

Am I the only one facing this problem ? Is there a workaround ? :)

Thanks a lot.

---

### Post by uhuru53 on 2006-12-08
Yes, I can connect with Raki and Kontact, but I get "wrong library type for contact"

anybody could solve this?

I use kubuntu updated and a windows pocket pc 2003 PDA

---

### Post by cleonII on 2006-12-10
Hi!
I can connect my device and execute all the command like pls pcp etc..
but when i start raki, the device connects, and instantly is disconected.
Icant make it work. 
Maybe someone there have the answer to this.
Also, i cant configure it trough USB because the /dev/ttyUSBx doesnt appears after i connect my device.. any advice on this?

by the way, i have kubuntu 6.06 and a smartphone htc s310

thanks in advanced to all!

---

### Post by uhuru53 on 2006-12-16
Still getting "wrong library type for contact" when trying to sync my pda with kontact :confused: ](*,) 

any other has gone throu?

---

### Post by empedocles on 2006-12-31
Finally banished "wrong library" message from my Edgy install.  Did strace to find out what libraries it was failing to load, discovered that I needed to apt-get install  ksync, kitchensync and (possibly) synce-multisync-plugin.  Now if I can just figure out why it wants to crash after syncing my contacts...

---

### Post by empedocles on 2006-12-31
Almost immediately after (nearly) giving up on it I figured out why it keeps crashing after sync.   I needed to go to "pocket pc/configure pocketpc" and highlight one of the things I have checked to sync (Contacts) and click the config button.  Inside there I had to choose a calendar file & address file.  No more explosions, and it syncs just fine w/kontact now.  Hooray!

---

### Post by aurelieng on 2007-01-02
Great, it almost work for me too !

I have a bunch of existing appointments in Kalendar, which are not sent to my PDA, altough it has no defined appointments in calendar. Interestingly, If i create a new appointment in Kalendar, it is sent to the PDA, but existing appointments are not synchronised. Any idea ?

Thanks a lot !

Aurelien

---

### Post by empedocles on 2007-01-03
Aurelien,

Not sure, I started with a blank calendar. It may be that raki thought one of the previous syncs worked, and it's only syncing things after that.  Haven't really dug into how that works yet. 

It looks like raki stores the date of last sync in a .cfg file under 

~/.kde/share/apps/raki

I'd probably try by hunting up the section for your calendar (Name=Appointment) and set the line for LastSynchronized to "LastSynchronized=1969,12,31,19,0,0", which is apparently what it uses for "never synchronized"

if that doesn't work, I'd probably try deleting (or renaming) ~/.kitchensync and repeating the edit above, and obviously all changes with the ppc disconected.

Good luck

---

### Post by aurelieng on 2007-01-03
Thank you for your reply. I tried to solve the problem by manually editing the raki cfg file as you suggested, unfortunately with no luck. Then I removed both ~/.kde/share/apps/raki and ~/.kitchensync, but that didn't solve the problem either :(

So, if by chance you have another idea, feel free to write it :)

Thank you again :)

Aurélien

---

### Post by martijndenerd on 2007-01-04
hmmm 
i can´t get it to work on edy eft. I tried both the packages and the compiling, but when i click  left on my raki icon nothing happens... any idea what that means?

tnx

---

### Post by aurelieng on 2007-01-04
To make it work, I've created a file /etc/udev/rules.d/60-ipaq.rules containing the following lines:

# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start"
BUS!="usb", ACTION!="remove", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-abord"
LABEL="synce_rules_end"

Maybe it can help you :)

Cheers,

Aurélien.

---

### Post by martijndenerd on 2007-01-07
Yes! this definitely helped me a bit,  now my rapip:/ shows the filesystem of my pda. But I am not there yet.. 
The raki applet still says: No devices connected, when I leftclick on it. and synchronising in Kontact (i can see the synce device) crashes Kontact before doing anything..  
I tried the packages and the self-compiled versions of synce-kde and konnector , but no difference. 

I wanted to try to change pocketpc/configure pocketpc as empedocles suggested, but where should it be? I can't find it. 




BTW 
there is a typo in the udev script aurelieng posted, abort is with a T; so it should be:
```

# udev rules file for SynCE
 BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
 # Establish the connection
 RUN+="/usr/bin/synce-serial-start"
 BUS!="usb", ACTION!="remove", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
 # Establish the connection
 RUN+="/usr/bin/synce-serial-abort"
 LABEL="synce_rules_end"


```

---

### Post by aurelieng on 2007-01-07
Well, it's working even with the typo :)

Your problem is strange. Did you choose dccm or vdccm ? Maybe it's worth trying with the other one. Upon connexion, the raki icon should be colored, and a left click allows an easy access to synchronization with, rapip:// and kcemirror. You might have to fix that before synchronizing ?

---

### Post by martijndenerd on 2007-01-07
i advanced one small step again :)  

after removing all the relevant config files from my homedir, raki asked me again whether i preferred dccm or vdccm. I tried both, and listen to this; 
if i select vdccm, it doesn't work
if i select dccm, it doesn´t work either... but
if i select dccm and then later change it to vdccm (in configure...) Raki responds to my pocketpc!!! ( i just love software that has some magic in it)

Unfortunately I am not there yet... The list of 'possible sync types' is empty, although i believe i have all the necessary packages installed; syncekonnector, ksync, kitchensync, multisync... 

Thanks for all the help until now! I am gonna fight with raki for a while to tackle this last problem, any ideas are welcome of course ...

Martijn

---

### Post by martijndenerd on 2007-01-09
It works! After doing everything I already did in different orders, on different moments, wearing different cloths and playing different music on the radio; my pda synchronizes with my kontact!! 

Two minor problems; 
 - the activesync icon on the pda doesn´t stop rotating (the arrows), even when raki already said that the sync is done. 
- recurrent events make the calendar on my pda crash terribly. it keeps thinking and complains about memory... i have to hard reset it to repair it

---

### Post by aurelieng on 2007-01-09
@martijndenerd: I have the two same problems :(

---

### Post by wersdaluv on 2007-05-19
I am a Kubuntu Feisty user who is trying to sync his O2 Xda mini.

I also had the "Wrong library type" problem, then I managed to fix it by installing stuff (thanks to empedocles' instructions!), but Raki crashes everytime I try to sync even after I chose a Calendar file and address file.

It seems that all I can do is to run the KCeMirror.

What can I do to successfully sync?

---

