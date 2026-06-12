---
title: "Ultimate Edition upgrade issues..... very urgent"
date: 2014-03-05
forum: Debian
---

### Post by Haitham_Essam on 2014-03-05
[SUP]&#8203;[/SUP]Hello guys,

i am running Ultimate Edition 3.4 with 12.04... then i decided to upgrade so it upgraded to 12.10
now it ruined my UE and i am trying to upgrade again to the 13.10 but i keep on getting errors


----
Could not calculate the upgrade




An unresolvable problem occurred while calculating the upgrade.




This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu
----


i really hate to reinstall and i just wanted to upgrade and keep my UE or upgrade it...


anything else i can do to fix my UE and upgrade it? and can i upgrade to 3.8 ?
btw my DVD rom doesn't work so i can only use USB.

---

### Post by oldrocker99 on 2014-03-05
As I understand it, UE is no more uprgadable than Mint. I was an enthusiastic UE user a few years ago, and of Mint, but I decided to come back to the Ubuntu source.

---

### Post by Haitham_Essam on 2014-03-05
i am used to it. it has everything and works like charm on my laptop :)

---

### Post by Frogs Hair on 2014-03-07
Ubuntu 12.10 and 13.10 reach EOL next month and the repositories will close but I don't know if  this affects UE . If UE uses the official repositories you wont be able to update anymore.  You could wait and give 14.04 a try in April or keep 12.04. 13.04 is already EOL which would be needed to get to 13.10.

---

### Post by 23dornot23d on 2014-03-09
Just to find out where you are with the system you have ..... do this but answer No to the upgrade

I just want you to post the listing back that you get from it ........ if any.

sudo apt-get update

sudo apt-get install aptitude

sudo aptitude update

```

A long list of things may come back here - just cut and paste them back in a code /code box please.
( We can but try ...... as I managed recently to take Ultimate Edition 2.8 right through to 14.04 and
have still retained a lot of what I like about the Ultimate Edition Distro )

[B]sudo aptitude safe-upgrade
[/B]
[COLOR=#ff0000][B]Answer no to the upgrade - and quit out of it 
[/B][/COLOR]

```

........ we just want to get some information to start with ......
call it a recon ...... as said in previous posts - you may be easier doing a 14.04 install on the 17th April
but that will not keep anything you have now - even a upgrade will try to remove all the Themes from
UE ....... but we can lock them in Synaptic to retain them .... what is the main use of the machine and have
you backed up everything ........ one good thing I found to retain the OS is Timeshift .... which just takes
a snapshot of the OS in its current state ...........

But all home files need backing up separate as they will not be kept with Timeshift .... but all passwords in Firefox
and links etc seem to remain ........... ( just another choice if you wish to take it )

Looks like another option is available too ..... [http://ultimateedition.info/](http://ultimateedition.info/)

---

