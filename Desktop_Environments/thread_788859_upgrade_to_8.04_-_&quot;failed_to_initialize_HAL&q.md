---
title: "upgrade to 8.04 - &quot;failed to initialize HAL&quot;"
date: 2008-05-10
forum: Desktop Environments
---

### Post by waylow on 2008-05-10
I upgraded from 7.10 to 8.04 with the update manager and it has broken my system

I get error - "failed to initialize HAL"
my networking doesn't work so I don;t have any internet

Also now when I boot into the 7.10 kernel - it says the same error however
the networking works

---

### Post by waylow on 2008-05-10
OK so I have seemed to have fixed the "Hal error" but still no networking

I rebooted into 7.10 - did another update
that seemed to fix the "hal error"

but it still has no networking in 8.04 and it looks like it doesn't look like it is seeing my hard drive correctly
in both 7.10 and 8.04

---

### Post by waylow on 2008-05-10
I lied - the Hal problem is still there but not everytime I boot

does anyone know how to help

I don't really want to have to do a re-install

---

### Post by waylow on 2008-05-10
I lied - the Hal problem is still there but not everytime I boot

does anyone know how to help

I don't really want to have to do a re-install

---

### Post by JediJames on 2008-05-14
The attachment below is a screenshot of the error message *I* get when I boot. I usually never reboot this PC, but this time I needed to, to install a new HDD, beside the point here. When I rebooted a was surprised to see that. My NTFS partitions no longer show up in 'places', but my NFS shares which I have in my fstab work and of course mount fine. I do need my NTFS partition as it holds data that I use in Windows as well. It will be wonderful if someone had a fix for this.

[ATTACH]69985[/ATTACH]

---

### Post by btdown on 2008-05-14
I have the same problem....

```
sudo dpkg-reconfigure hal
```fixed it for me yesterday, but it popped back up today after a reboot... Not sure what a permanent fix would be.

-BT

---

### Post by waylow on 2008-05-15
there was a hal update yesterday

but I still get the error

it doesn't happen everytime I boot
(approx 2nd every time)

---

### Post by katchi on 2008-05-15
> **waylow said:**
> there was a hal update yesterday

but I still get the error

it doesn't happen everytime I boot
(approx 2nd every time)

how to order new ver cd

---

### Post by waylow on 2008-05-15
> **katchi said:**
> how to order new ver cd

if you mean where did I get the update

from the update manager

or 

```
sudo apt-get update 
sudo apt-get upgrade 
```

---

### Post by btdown on 2008-05-19
Dunno about you...but my hal is still hosed after the upgrade.. dpkg-reconfigure hal fixes it until reboot...

---

### Post by zakhooi on 2008-07-03
has anyone a solution for this?
I have the same problem and can't get rid of it.

Please advice

Thanks in advance

---

### Post by waylow on 2008-07-03
not really

I rolled back to the older kernal
then it went away after a few updates

no one gave a proper answer (and I think I'm still using the old kernal)

---

### Post by fermin on 2008-08-03
I have this same problem. I updated from 7.10 to 8,04 via the alternate install CD but the installation was interrupted (long story). When i rebooted, i started getting this message "failed to initialize HAL" and non of my drives (other than hardisk) work, neither does internet or network. I already tried instructions from another post:
> 1. Check in your /etc/rc2.d folder for "S12dbus".
2. If it is not there, copy "S12dbus" from /etc/rc3.d/ to /etc/rc2.d. Then restart and the problem may be fixed.

If it is not fixed, all I can advise is that you type:

"sudo dpkg-reconfigure hal" (without the quotes) into a terminal and restart your computer. Please reply if this problem still persists.


but that didn't work. Reconfiguring HAL said "hal is broken or not fully installed" and did nothing else. The s12dbus file was in place. I cant even use Synaptic and when i try to I get a message that says: "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" also "cache->open() failed, please report". When i run the above command i get a lot of error messages saying problems in dependencies, leaving things unconfigured or so and it hangs the terminal.

Please help! I cant even backup my data and do a fresh install because my drives wont work and i cannot backup! :(

---

### Post by Beernut on 2008-08-03
Same problem here did an upgrade and it froze on locals then tried the ```
dpkg --configure -a
``` and the HAL is still broken.  This really sucks! :mad:  It used to be upgrade or update with no problems not anymore.

---

### Post by ubuntubrian on 2008-08-03
> **fermin said:**
> I have this same problem. I updated from 7.10 to 8,04 via the alternate install CD but the installation was interrupted (long story). When i rebooted, i started getting this message "failed to initialize HAL" and non of my drives (other than hardisk) work, neither does internet or network. I already tried instructions from another post:


but that didn't work. Reconfiguring HAL said "hal is broken or not fully installed" and did nothing else. The s12dbus file was in place. I cant even use Synaptic and when i try to I get a message that says: "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem" also "cache->open() failed, please report". When i run the above command i get a lot of error messages saying problems in dependencies, leaving things unconfigured or so and it hangs the terminal.

Please help! I cant even backup my data and do a fresh install because my drives wont work and i cannot backup! :(

this is very similar to my problems, all solved. I had the dpkg issue when doing an upgrade from Dapper to Hardy. I am including what worked for me below in quotes. I started having HAL issues today but for the last 3 days everything was working great so I don't know what would start the HAL error on booting. dpkg -reconfigure hal seems to work.
I suggest doing what I did below to resolve the dpkg issues first, including finishing the upgrade. Of course adapt the commands for the packages that arecausing the dpkg errors but just start with the first package that dpkg borks on. In my case, python-central. there were a couple hundred but purging python-central allowed almost all of the rest to install.
Those dpkg errors won't allow the upgrade to complete. 
Then run the dpkg -reconfigure hal. It worked for me and I have everything back up and running fine.
good luck

Brian

> I solved this with the help of my local users group, NMGLUG. I'm posting the solution as it was written to me. I knew that dpkg was choking on python-central but didn't know how to get past it. I ran and re-ran the commands below, a little differently. I ran
"dpkg -P python-central"
and when that completed I ran:
"apt-get install python-central"
the package installed and then the upgrade continued on its own in terminal. It borked at another python package so I did the same thing for that one and it installed the package but no further running of the upgrade.
I then ran the commands below for apt-get, ran update manager and synaptic, screwed up some permissions and fixed those (don't have a clue how that happened! I wasn't setting permissions)
It all works, everything!
From my group:

"If it's still the timidity and python-central errors, try purging
those packages:

dpkg -P timidity
dpkg -P python-central

You might have to purge a few dependencies, too. Then:

dpkg --configure -a

That's the basic idea anyway for a way to correct this problem that
has worked for me in the past.

Once the configure completes successfully, I'd try:

apt-get -f install

until it does nothing, then finish the upgrade:

apt-get dist-upgrade

repeatedly until it is done. After all that, reinstall timidity and
python-central if you need them."

---

### Post by fermin on 2008-08-03
Thanks for the advice. In my case, the first thing that failed to update through dpkg was xfdesktop4, so i ran
```
sudo dpkg -P xfdesktop4
```
and i got a message that says "dpkg: status database is locked by another process" so I understand i cannot do this at the time. I tried to run this same command from a failsafe terminal session but the same happened. Any other ideas? :(

---

### Post by ubuntubrian on 2008-08-03
that message usually means synaptic or update manager or add/remove or some other package management is running. Are you logged into your desktop? 
try logging in and running system monitor in administration or top in a terminal and see if some latent app is running like those I mentioned. If so, kill it. Try again.
Good luck

---

