---
title: "[SOLVED] VM Swapping"
date: 2008-12-22
forum: General Help
---

### Post by ExemplarUbuntu on 2008-12-22
A few weeks ago I upgraded a good Heron to the latest Ibex and although the installation didn't have any nasty problems (had to fix graphics and missing sound) I have a lot of problems with the laptop grinding to a halt with eternal disc access.

As long as I don't do anything with the PC it's fine but as soon as it is asked to do anything it soon gets slower and slower and does more and more HD access until it is unusable.

It's so bad I think the only way to fix it is to back-out Ibex and replace it with Heron if there is an easy way to do this. I've been using Ubuntu since the Warty days and upgrades have always been a one-way trip.

---

### Post by tigerstripedcat on 2008-12-22
We'll probably need more info to diagnose.  What does 'top" say is using all the cpu when it happens?  Can you see anything odd in /var/log/messages around the time it happens?  Are you running any NVidia/ATI drivers, or stock drivers?

---

### Post by gTinker on 2008-12-22
> **ExemplarUbuntu said:**
> A few weeks ago I upgraded a good Heron to the latest Ibex and although the installation didn't have any nasty problems (had to fix graphics and missing sound) I have a lot of problems with the laptop grinding to a halt with eternal disc access.

As long as I don't do anything with the PC it's fine but as soon as it is asked to do anything it soon gets slower and slower and does more and more HD access until it is unusable.

It's so bad I think the only way to fix it is to back-out Ibex and replace it with Heron if there is an easy way to do this. I've been using Ubuntu since the Warty days and upgrades have always been a one-way trip.

The symptoms you describe sound to me like your system is slowing down because it is swapping. The first question I want to ask is how much RAM do you have. Since you've been upgrading for a while, I imagine you have an older processor and system which probably came with what, these days, is not considered much RAM. If I am correct, and you can add more RAM the problem will likely be diminished. I'm not sure I understand your choice of title for this post.

---

### Post by redilyn on 2008-12-22
I suspect gtinker is correct and you do not have enough ram in your system.

Regardless you could try the following although I'm not sure it is recommeneded.

```

sudo gedit /etc/sysctl.conf

```

Add the following line somewhere in this file

```

###Tweak To Limit Swapping
vm.swappiness=10

```

Save and close the file then run the following

```

sudo sysctl -p

```

This will limit swapping until it is absolutely necessary.

Hope this helps.

---

### Post by ExemplarUbuntu on 2008-12-23
It's impossible to see the logs as it happens, the laptop is unusable by that point. Afterwards there is nothing in the logs around that time.

Top doesn't show anything hogging the cpu.

This laptop has had Drake, Heron and now Ibex and it was fine with the first two. Has Ubuntu become such fatware that it won't run an a slightly older machine ?

I suspect what is more likely is that there is a problem somewhere either in the swapping or that is being highlighted by the swapping.

---

### Post by Zack McCool on 2008-12-23
"Slightly Older" doesn't say anything.  What are your machine's specs?  What CPU, How much RAM?

New versions have higher system requirements.  Just a fact of life...

---

### Post by ExemplarUbuntu on 2008-12-23
It's a Toshiba Satellite S1800 Intel Celeron with about 255Mb memory. Not a quick PC but quick enough to run Windows XP perfectly well even when it had several Oracle 8 databases installed on it.

Like I've all ready said, Heron ran well, is Ibex really that much fatter ?

Synaptic update manager crashed it again when trying to get more updates and I had to fetch them with apt-get yet again. Afterwards I managed to run Firefox on YouTube for 15 minutes without a crash.

Update Manager seems to be the biggest problem at the moment.

---

### Post by redilyn on 2008-12-23
Add the system monitor to your panel and set it up to monitor your RAM usuage (or just open system monitor). If you are using all of your memory then you found your problem.

256mb is really low....

---

### Post by ExemplarUbuntu on 2008-12-23
>$ free -m
             total       used       free     shared    buffers     cached
Mem:           232        223          9          0          2         42
-/+ buffers/cache:        178         54
Swap:            0          0          0

The monitor shows about 80% of RAM used and 0% Swap while running a bash shell and typing this in Firefox.

Does this mean that my swap has vanished ?

UPDATE:
Running Synaptic, the mem usage got to almost 90% and then it froze up again.
Swap file still said 0%

---

### Post by redilyn on 2008-12-23
You do not have any swap space. This would explain your crashs.

First you need to get a swap file turned on.

Do you know what partition your swap file is on?

If so do the following

```

swapon /dev/sdaX

```

If you don't know check your fstab to see if it is listed.

```

sudo gedit /etc/fstab

```

If you followed my directions earlier about vm.swappiness be sure to undo that change. Your are ram limited and that tweak will not be good for your system!!

```

sudo gedit /etc/sysctl.conf

```

Change vm.swappiness=10 to vm.swappiness=70

Or just remove the line entirely. I would try vm.swappiness=70 so ubuntu will start swapping stuff out of mem faster.

---

### Post by redilyn on 2008-12-23
Oh, if you do not have a swap file setup and you can not find it in fstab you could try the following as a quick fix if you have a USB key which you can erase.

To do this you will be using a script called Swapboost

Plugin your USB and let ubuntu auto mount it

Open a terminal and follow these steps.

Download Swapboost
```

wget http://zelut.org/projects/misc/swapboost.sh

```

Make it executable
```

chmod +X swapboost.sh

```

Setup Swap On USB Key
```

./swapboost.sh -n

```

Check that it worked
```

swapon -s

```


Do the following to remove the swapfile from your usb key after you have created a swap file on your hard drive.
```

./swapboost.sh -d

```

---

### Post by ExemplarUbuntu on 2008-12-23
According to GParted I have a 690MiB swap file which I have now turned on with swapon.

Sys Monitor now shows it growing and shrinking as it should do.
Do I have to do anything to make this chage permanent ?

Many thanks, I think that this may cure it.

I wonder if the swap was disabled during the upgrade from Heron ?

Peter

---

### Post by redilyn on 2008-12-23
Nope, just check fstab and make sure the entry for swap is there

```

sudo gedit /etc/fstab

```

Look for a line similar to this

```

# /dev/sda2
UUID=6c8b3d67-fb60-46d1-a29e-5970bb845e79 none            swap    sw              0       0

```

---

### Post by ExemplarUbuntu on 2008-12-23
I just rebooted and the swap was off again.

I have a /dev/sda5 line like the one you show for the swap in /etc/fstab and I am starting it with sudo swapon /dev/sda5

---

### Post by ExemplarUbuntu on 2008-12-23
I think I have found the answer here :

[http://ubuntuforums.org/showthread.php?t=691986](http://ubuntuforums.org/showthread.php?t=691986)

PS

Well I though I had but blkid doesn't show a uuid for swap:

$ sudo blkid
/dev/sda1: UUID="11d483b5-4701-4b06-9cde-1f96bda95807" TYPE="ext3" 
/dev/sda5: TYPE="swap" 

Maybe this is the cause of the problem ?

---

### Post by ExemplarUbuntu on 2008-12-23
Since my swap didn't appear to have a uuid I did this:

$ sudo swapoff -a
$ sudo mkswap /dev/sda5
Setting up swapspace version 1, size = 706824 KiB
no label, UUID=3bb7f3d8-d1c4-4378-b1ad-3a876418f18e
$ sudo blkid
/dev/sda1: UUID="11d483b5-4701-4b06-9cde-1f96bda95807" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="3bb7f3d8-d1c4-4378-b1ad-3a876418f18e" 
$ sudo swapon /dev/sda5

and then put the uuid in fstab. Hopefully this will survive a reboot.

---

### Post by ExemplarUbuntu on 2008-12-23
That worked :)

Many thanks again for your time and effort on helping with this. I was about ready to reinstall XP.

---

### Post by redilyn on 2008-12-23
your welcome.

Anytime you have to find your UUID just do the following.

```

sudo vol_id /dev/sdaX

```

---

