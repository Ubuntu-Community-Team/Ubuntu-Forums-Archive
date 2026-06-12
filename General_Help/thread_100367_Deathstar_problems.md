---
title: "Deathstar problems"
date: 2005-12-07
forum: General Help
---

### Post by Kaah on 2005-12-07
As you all probably knows, Hitashi deskstars is known as deathstars.
And now my one and only ibm deskstar has crashed?
I have some dmesg logs here.
> [4294796.110000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4294796.110000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4294796.236000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4294796.236000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4295644.758000] hda: dma_timer_expiry: dma status == 0x21
[4295654.758000] hda: DMA timeout error
[4295654.758000] hda: dma timeout error: status=0xd0 { Busy }
[4295654.758000]
[4295654.758000] ide: failed opcode was: unknown
[4295654.758000] hda: DMA disabled
[4295654.808000] ide0: reset: success

Im running ubuntu with latest kernel.

I wonder if the powersupply is causing the problem?
or is it just a nice harddrive failure :)

---

### Post by teaker1s on 2005-12-07
mine died too my advice is to run the hitachi disk diagnostic utility and or place disk at a different angle, does yours make any clicking noises/grinding?


mine was out of warranty by a mere couple of months and either the nvram corrupted or more likely the heads died I was quoted 25% recovery chance and near &#163;1000  -I grudgingly accepted my loss and have an external hd for backups now
hitachi support is useless

---

### Post by Rackerz on 2005-12-07
I had one. Got rid of it as soon as i researched and found it to be called the deathstar, although it was already playing up.

---

### Post by Kaah on 2005-12-07
Hmm i have now done an full image of the ubuntu installation with acronis true backup, Hope my new Samsung P80 80gb will do the job better :D..

It should be something wrong with the image, i got amazed that the image creation of the deathstar was a success.

An photo of the crash :)
[http://hispan.se/~swift/swift/arkiv/DSC02232.JPG](http://hispan.se/~swift/swift/arkiv/DSC02232.JPG)

---

### Post by poptones on 2005-12-07
I now swear by hard drives in threes. They're cheap and it's handy in 1000 ways not to mention a lifesaver when someone sends you up the bomb. Raid5 is the coolest invention since color graphics...

---

### Post by Gray. on 2005-12-07
So that explains why my hard drive sucks. Kind of funny because my PC's name is Deathstar.

---

### Post by Kaah on 2005-12-11
Well i got my new samsung disk, and the ubuntuinstallation worked fine...
for 2 days. Then the same problem came up again!!! This is getting expensive :(.
Have now orderd a new Powersupply.

---

### Post by teaker1s on 2005-12-11
look at this as a bonus deathstars are unreliable I lost loads as I couldn't be bothered with backups

---

### Post by Ocxic on 2005-12-11
[QUOTE=Kaah]Well i got my new samsung disk, and the ubuntuinstallation worked fine...
for 2 days. Then the same problem came up again!!! This is getting expensive :(.
Have now orderd a new Powersupply.[/QUOTE]

how old is your computer???
Check all of your ide cable's and replace them with 80-conductor cable if there old,cracking, or has been bent/folded alot.
check you bios, maybe do an update.
ensure there is adiquate(sp?) cooling for you hard drives-heat is not there friend.

at last but not least if all else fails, and it's not the power supply, you may need a new motherboard, the onboard IDE controller may be going.

---

### Post by Kaah on 2005-12-12
MSI KM4AM
2600+ Athlon XP
512MB Twinmos PC3200

I will replace all ide cables and check conductors after work..
Cooling is no problem, the server room temperature is around 16C by default.. so its quite cold in there :).

---

### Post by Kaah on 2006-01-05
Well it's been a time now, and i have solved the problem.
The server has been online for more than 10 days now, i disabled acpi in grub.

---

### Post by PryGuy on 2006-01-05
Backup your Deathstar if you can and THROW IT AWAY as soon as possible!!! I got two of them crashed!!! 
I recommend Seagate Barracudas! ;)

---

### Post by lgmdaniel on 2006-01-05
its funny I worked at IBM for 6 years and the last 3 years we where replacing them at a rate 2-4 a week. Though it did, drop off to 1-2 a month in the last year. But then we did have over 500 Unix server and 5TB's of external storage.
I'm just surprised you can still get them.
Then I there are other IBM drives that never fail, I even have one at home thats been though all sorts.

---

### Post by Kaah on 2006-01-05
Well my iBM disk havent krashed :D, works fine.. I replaced it if it would crash.

---

### Post by Kaah on 2006-01-12
17 days of uptime, crashed today.. im getting tired of this.

> Jan 12 06:09:01 localhost /USR/SBIN/CRON[3696]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jan 12 06:09:01 localhost /USR/SBIN/CRON[3698]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Jan 12 06:17:01 localhost /USR/SBIN/CRON[3812]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 12 06:25:01 localhost /USR/SBIN/CRON[3930]: (root) CMD (test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily)
Jan 12 06:37:19 localhost -- MARK --
Jan 12 06:39:01 localhost /USR/SBIN/CRON[4106]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Jan 12 06:39:01 localhost /USR/SBIN/CRON[4107]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jan 12 06:52:38 localhost dhclient: DHCPREQUEST on eth0 to 192.168.1.1 port 67
Jan 12 06:52:38 localhost dhclient: DHCPACK from 192.168.1.1
Jan 12 06:52:38 localhost dhclient: can't create /var/run/dhclient.eth0.leases: Permission denied
Jan 12 06:52:38 localhost dhclient: bound to 192.168.1.105 -- renewal in 15478 seconds.
Jan 12 07:09:02 localhost /USR/SBIN/CRON[4525]: (root) CMD (  [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Jan 12 07:09:02 localhost /USR/SBIN/CRON[4527]: (root) CMD (  [ -d /var/lib/php4 ] && find /var/lib/php4/ -type f -cmin +$(/usr/lib/php4/maxlifetime) -print0 | xargs -r -0 rm)
Jan 12 07:17:01 localhost /USR/SBIN/CRON[4642]: (root) CMD (   run-parts --report /etc/cron.hourly)
Jan 12 07:30:01 localhost /USR/SBIN/CRON[4824]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Jan 12 07:30:01 localhost anacron[4848]: Anacron 2.3 started on 2006-01-12
Jan 12 07:30:01 localhost anacron[4848]: Will run job `cron.daily' in 5 min.
Jan 12 07:30:01 localhost anacron[4848]: Jobs will be executed sequentially
Jan 12 07:35:01 localhost anacron[4848]: Job `cron.daily' started
Jan 12 07:35:01 localhost anacron[4916]: Updated timestamp for job `cron.daily' to 2006-01-12
Jan 12 07:35:09 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport0: Permission denied: io/hpiod/ppdevice.cpp 827
Jan 12 07:35:09 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport1: Permission denied: io/hpiod/ppdevice.cpp 827
Jan 12 07:35:09 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport2: Permission denied: io/hpiod/ppdevice.cpp 827
Jan 12 07:35:09 localhost hpiod: unable to ParDevice::Open hp:/par/ANY?device=/dev/parport3: Permission denied: io/hpiod/ppdevice.cpp 827
Jan 12 07:36:31 localhost exiting on signal 15

---

### Post by Kaah on 2006-02-14
Well.. more updates.

Stable for 30 days now, it is windows 2000 server on vmware that created the problem, with vmware disabled the server is fine.

yay! :)

---

### Post by gremlin hunter on 2006-02-14
I think that *ide=nodma* could have solved the original problem.

---

### Post by Kaah on 2006-03-15
thx, i will try that. It crashed again a few days ago.

---

