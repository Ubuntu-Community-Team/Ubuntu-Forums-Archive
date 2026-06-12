---
title: "Gnomebaker won't work"
date: 2006-06-30
forum: Desktop Environments
---

### Post by ColinG on 2006-06-30
Help please!

I just installed gnomebaker via Automatix and I'm not impressed. It will not burn anything yet the basic Gnome cd/dvd creator software seems to be ok.

Below is the error reported by Gnomebaker. Any ideas out there?

WARNING: /dev/hda already carries isofs!
About to execute 'mkisofs -gui -V GnomeBaker data disk -A GnomeBaker -p Colin Grant -iso-level 3 -l -R -hide-rr-moved -J -joliet-long -graft-points easyubuntu=/home/colin/easyubuntu | builtin_dd of=/dev/hda obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
:-( Failed to change write speed: 2770->3324

Thank a mil
Colin

---

### Post by jrattner on 2006-06-30
Personally I would use k3b.  Yes it has KDE dependencies but its by far the best and simplest burner for linux.

Plus its pretty : )

---

### Post by ColinG on 2006-06-30
You're so right - it's pretty and it works.

Sometimes I wonder why I bother with Gnome - I use K3b (now), DigiKam, Kmymoney and AmoraK (although I'm trying Listen which is looking good), plus Open Office which is cross desktop anyway.

I may as well go to Kubuntu. But then I do like the Gnome look and feel :) 

Thanks for the help =D> 

Colin

---

### Post by wylfing on 2006-06-30
There is nothing wrong with using applications written for "the other team." Part of the goodness of Linux is the low incidence of lock-in.

---

### Post by shrift on 2006-06-30
I don't know why you installed gnomebaker from Automatix. Gnombaker is in the Ubuntu universe repositories. If you don't have those open, then do that and reinstall it from that. I bet that will work much better.

Gnomebaker is just as good as k3b, and no kde dependencies. 

Personally I use Gnome because it just plain feels better.

---

### Post by wpshooter on 2006-06-30
[QUOTE=shrift]I don't know why you installed gnomebaker from Automatix. Gnombaker is in the Ubuntu universe repositories. If you don't have those open, then do that and reinstall it from that. I bet that will work much better.

Gnomebaker is just as good as k3b, and no kde dependencies. 

Personally I use Gnome because it just plain feels better.[/QUOTE]

Shrift:

When you say it is on the universe repositories, is this the same as what shows up on the add/remove applications section of Ubuntu ?  

It seems to me that I tried installing the Gnomebaker program from there (add/remove applications section) and I could never get it to do what I needed, but when I installed the K3b program, it worked exactly as I expected and the way I basically was used to the Roxio Easy CD Creator program that I used under M/S windows.

Also, since you seem very knowledgeable on this topic, let me ask you about the wisdom of marking ALL of the repository entries that are shown by default in the Ubuntu installation.  Should I mark all of the repositories that are in this listing and if so, is there any possibility that doing so would in any way be detrimental to the Ubuntu O/S installation, i.e. if I marked all of these and then did a download of all the found software, would the installation of anything be harmful to the system, or in other words is all of the software in these other repositories as dependable as those that are officially endorsed by Ubuntu ?

Thanks.

---

### Post by ColinG on 2006-06-30
Agreed. K3b works Gnomebaker does not, even if installed via synaptic.

---

### Post by shrift on 2006-07-01
Well, I'm bummed it doesn't work for you guys. I think it is a superiour application. But that is all a matter of taste I suppose.

Wpshooter

It is safe to use all of the universe and multiverse repositories. I run my system with all of the repositories enabled, and it is rock solid. Go for it.

---

### Post by ColinG on 2006-07-01
Maybe Gnomebaker fails because we don't know how to use it :confused:  I read somewhere about the need to mount and umount cd/dvds. Against that, K3b is totally intuitive for me anyway.

---

