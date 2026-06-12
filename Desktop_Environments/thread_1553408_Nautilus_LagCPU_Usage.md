---
title: "Nautilus Lag/CPU Usage"
date: 2010-08-15
forum: Desktop Environments
---

### Post by Peter7K on 2010-08-15
Recently upon booting up, Nautilus has been significantly slower than usual.  It has an incredibly slow startup, and loading any new folder usually takes much longer.  It's running at a whopping 90% of CPU usage (waaay higher than normal).  I've done multiple apt-get purge nautilus along with all of the other packages that come with it, deleting the .nautilus folder (there wasn't anything in it anyway as I saw later).  I even installed the testing ppa of ubuntu-tweak because it has reset to default settings buttons and reset all of those nautilus settings.  Still slow! :(

Any way to check what's going on with this?  It doesn't seem that running nautilus from a terminal will produce any repetitive errors or anything...

Thanks for your time!

---

### Post by inobe on 2010-08-15
run **top** in terminal to see whats using that much processing power.

let us know your findings

---

### Post by Peter7K on 2010-08-15
Sorry, maybe I wasn't clear enough.  It's not that there's something screwing up in the background, it *is* Nautilus that is running slow.  The CPU usage can get up to nearly 100% when I'm merely opening a new folder with a lot of things in it (it takes 5 seconds to load my music folder now, as opposed to like 1 before).

Also, if it might help, I have these packages that relate to nautilus installed:

backintime-gnome
brasero
gir1.0-nautilus-1.0
gnome-control-center
gnome-icon-theme
intltool
libgnomevfs2-0
libgnomevfs2-common
libgnomevfs2-extra
libnautilus-burn-dev
libnautilus-burn4
libnautilus-extension-dev
libnautilus-extension1
nautilus
nautilus-data
nautilus-sendto
nautilus-share
totem
ubuntu-tweak
ubuntuone-client-gnome

Anything I can do? :/

---

### Post by cebif on 2010-08-16
Same problem here. Nautilus can take 30-40s opening a folder with many items.
I'm using nautilus Version: 1:2.30.1-0ubuntu1.1 on ubuntu 10,04.

---

### Post by cebif on 2010-08-16
I created a new user account with the same privileges. I tried nautilus in this account and all the folders it was slow at opening became fast. I then took ownership of the old user folder from my ne user account with:
[COLOR="RoyalBlue"]sudo chown -R new_username.new_username /home/old_username[/COLOR]
I then opened nautilus in the old_username folder, selected from view, Show Hidden Files, selected them all and copied to my new_username folder.
After that I had to do a restart or logout/in might suffice. I had all my old settings back.
There is now the problem back of a very slow nautilus in certain folders with a lot of stuff. Maybe if I hadn't copied over the settings from the old account but just all the other folders and files I would be alright.

---

### Post by Peter7K on 2010-08-17
Strange.  But if we only copy over the big folders all the other folders will be under the old "slow" settings.  There's gotta be a fix for this somewhere.

I wonder if making a new account and then copying your old folders into it, and then using that new account.  I guess I would have to copy over literally every file though to get all of the settings... and I don't have enough space on my hard drive to have both T____T

---

### Post by cebif on 2010-08-17
To fix the nautillus speed problem it is not necessary to create a new user account. All you have to do is put in the trash (not delete permanently because there might be some settings that are a pain to manually replace) user settings in your user folder. After that a logout/in will put back essential folders/settings. Then there are a few settings that you will have to set again manually.
I tried to just delete all instances of nautilus settings but that did not work. I definitely wanted to keep my email account settings and firefox settings. After trying out different applications for a while you can see if application settings are to your satisfaction, then empty the trash.
I hope this might be some help.

---

### Post by cebif on 2010-08-17
I  sort of arrived by trial an error that it is not necessary to make a new user account. After copying over all my old user folders and files then finding nautillus was back to slow, I realized that it would only have been necessary to delete settings in my old user account. That is what I did in my new user account.
See my post just before.

---

### Post by Peter7K on 2010-08-18
I did as you said, it seems a bit faster but still a bit laggy than a new account...  Oh well this is much more manageable!

---

### Post by cebif on 2010-08-18
I'm not certain what causes nautilus to lag but it might be accumulated old redundant files. Not just with settings but with user data & applications or perhaps fragmentation. Does linux file systems become fragmented? I use reiser 3.5 fs. Maybe copying user files to a new account puts everything in a new blank part of the drive in non fragmented way.

---

### Post by Peter7K on 2010-08-24
Linux is automatically defragged as new files are placed, (Macs do too, only Windows doesn't).  

Another funny thing, is when I have a dialogue open, say from a website, to select a file to upload or something, that dialogue operates with zero lag.  So it really is a nautilus issue, it doesn't appear to be the files, because the file selector operates at comparatively much much greater speed.

---

### Post by cebif on 2010-08-25
> **Peter7K said:**
> Linux is automatically defragged as new files are placed, (Macs do too, only Windows doesn't).  

Another funny thing, is when I have a dialogue open, say from a website, to select a file to upload or something, that dialogue operates with zero lag.  So it really is a nautilus issue, it doesn't appear to be the files, because the file selector operates at comparatively much much greater speed.
So have you gained much benefit by deleting your settings in the user folder.
I gained great benefit by creating a new user and when I copied over my old settings lost it again. After deleting most of the settings again regained nautilus speed and no lag.
There is one thing I lost and haven't been able to get back: been able to speak through the microphone in skype and record sounds. Everything else with sound works though.

---

### Post by Peter7K on 2010-08-25
When I copied my settings back over they slowed it down again

I'll mess with it some more :/

---

### Post by gsiliceo on 2010-08-27
I have this problem too, i used the system monitor and saw the opened files by the nautilus process it seems that is reading ALL files on ALL partitions mounted on /media i got tons on one ntfs partitions and nautilis keep reading ALL of them for some reason, how do i stop it?

---

### Post by Peter7K on 2010-08-28
Interesting... I just checked my /media and there are a bunch of different DVDs and USB Hard Drives (duplicates too) that were still there.  I went ahead and gksudo nautilus /media and deleted them all.

Sadly, the lag remains! :(

---

### Post by wilburg on 2010-09-04
While I have been reading these reports Nautilus has been at 60 to 100 % opening /etc. It has been several minutes so far. What can be done to fix this? It is a very basic operating system fault and should not just be allowed to drag on. Try opening a folder in Windows and see if it takes this kind of time.

---

### Post by frankzen on 2010-09-27
Whoa I thought I was the only one!!! Strange thing on my machine when I run Nautilus under IceWm or Fluxbox both of which I have installed, Nautilus is as fast as it ever was. Go figure, a Gnome program that runs faster when NOT under Gnome!! I have tried everything...renaming the nautilus and gnome directories didn't change a thing. I have filed bugs on this but have not yet heard back from the developers.

---

### Post by frankzen on 2010-09-28
Fixed my problem - I still don't know what was wrong, but I created a new user, and discovered that account was fine..no lags. So I got rid of the .gconf and .gconfd directories in my home directory and all is now fine. When I re-logged in, everything worked as it was supposed to. I did lose some customizations, but they are easy to fix. Apparently some file in one of those two directories was causing the problem.

---

