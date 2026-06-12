---
title: "Updates break computer again!"
date: 2006-07-12
forum: Desktop Environments
---

### Post by viciouslime on 2006-07-12
This is the second time a new kernel has been released and ubuntu has asked me to update to it before the restricted modules are ready. So, because i have the nvidia driver installed, it breaks everything and X won't start. Why is this? Surely loads of people are using the nvidia driver. Why doesn't it wait until the restricted modules are available. I have had to restart into the .25 kernel now, but some people wouldn't know how to do that, absolute beginners for example.

Will this ever be sorted? Have I got something wrong here? is this just me? ](*,) ](*,) ](*,)


EDIT: To avoid any confusion here, I am talking about the nvidia driver from the repos so you really should be able to update without loosing X.

---

### Post by easyease on 2006-07-12
[http://www.ubuntuforums.org/showthread.php?t=213409&page=2](http://www.ubuntuforums.org/showthread.php?t=213409&page=2) same problem here mate!

---

### Post by easyease on 2006-07-12
im peed off booting between windows and ubuntu trying to sort this out, had enough for one day.lol

---

### Post by kinematic on 2006-07-12
why do you even install updates when they become available?
i always wait at least a week and keep an eye on the forum to see if there are any problems with new updates ;)

---

### Post by easyease on 2006-07-12
cos we like to think we are kool and on the spunking edge mate. silly i know. stuff this im going for a fresh install tonight when i go bed.](*,)  :-D

---

### Post by angkor on 2006-07-12
> **viciouslime said:**
> This is the second time a new kernel has been released and ubuntu has asked me to update to it before the restricted modules are ready. So, because i have the nvidia driver installed, it breaks everything and X won't start. Why is this? Surely loads of people are using the nvidia driver. Why doesn't it wait until the restricted modules are available. I have had to restart into the .25 kernel now, but some people wouldn't know how to do that, absolute beginners for example.

Will this ever be sorted? Have I got something wrong here? is this just me? ](*,) ](*,) ](*,)

No need to restart with another kernel. This always fixes it for me:

Log in at the terminal:

```
sudo apt-get remove nvidia-glx
sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx
sudo /etc/init.d/gdm restart
```

I agree by the way this should be handled by the update manager. I don't remember having to this in breezy.

Edit: The above method will only work if you had the nvidia drivers from the repo.

---

### Post by easyease on 2006-07-12
thanks angkor, I'll try that now. gotta be better than starting from scratch again.lol

---

### Post by vavoem on 2006-07-12
this is because your nvidia driver needs the kernel headers for compiling if they, for whatever reason (like an kernel update), do not match any longer. you have to recompile your nvidia driver.

just reboot with the new kernel and log in to the terminal go to wherever your nvidia driver installer package is and run it using sudo.

answer no to having your xorg.conf changed and then type sudo /etc/init.d/kdm restart or gdm restart depending the X session you use.

---

### Post by viciouslime on 2006-07-12
> **vavoem said:**
> this is because your nvidia driver needs the kernel headers for compiling if they, for whatever reason (like an kernel update), do not match any longer. you have to recompile your nvidia driver.

just reboot with the new kernel and log in to the terminal go to wherever your nvidia driver installer package is and run it using sudo.

answer no to having your xorg.conf changed and then type sudo /etc/init.d/kdm restart or gdm restart depending the X session you use.

Yeah, I understand why it happens, what I don't understand is why it can't do that automatically. If ubuntu wants to be used by everyone you can't have something as simple as an update stop the X server from loading. Even XP isn't THAT bad!

With this one exception ubuntu's default install is maintenance free, if they could just make it so updates didn't stop everyone from being able to boot normally, then it would be much better for n00bs... and much better for none n00bs since it would save them a job.

---

### Post by easyease on 2006-07-12
ok so i just got my x display back. i had to
sudo apt-get remove nvidea-glx
 then i tried 
sudo apt-get install linux-restricted-modules-`uname -r` nvidia-glx (but it couldnt locate the module needed,but i got my nvidea driver from automatix originally)
so I,
sudo dpkg-reconfigure xserver-xorg (and selected the nv option)
then finally i restarted gdm,
sudo /etc/init.d/gdm restart


 Thats a start! thanks for the helpfull words so far. :D

---

### Post by vavoem on 2006-07-12
you're not obliged to use the 3rd party Nvidia drivers
You could try and go with the xgl ones that are in the ubuntu repositories
They'll probably will not mess your system up when a kernel update presents itself.
However if you want the speed and the (nice)nvidia logo when you startx you'll have to live with running the ./Nvidiainstaller once in a while.

I would go for the second option in a heartbeat it takes me less then 5 minutes to do so. 

Advantage is you have your driver compiled exactly for your kernel how sweet is that.

To meet you halfway it would be nice that if a kernel package will present itself for an update it should warn you of problems that might occur in the update manager. ;)

---

### Post by angkor on 2006-07-12
> **easyease said:**
> but it couldnt locate the module needed,but i got my nvidea driver from automatix originally

Ceck the output of 

```
uname -r
```

For me this says:

**2.6.15-26-k7**

So I need to install:

```
linux-restricted-modules-**2.6.15-26-k7**
```

Try installing the restricted modules this way and change the kernel version with the one you got from uname -r. If it works and you reinstalled the nvidia-glx package as well you can try changing the nv driver back to nvidia and restart X by logging out.

I have no experience with automatix but I assume it installs the nvidia driver from the repo, I'm not sure though.

---

### Post by viciouslime on 2006-07-12
> **vavoem said:**
> you're not obliged to use the 3rd party Nvidia drivers
You could try and go with the xgl ones that are in the ubuntu repositories
They'll probably will not mess your system up when a kernel update presents itself.
However if you want the speed and the (nice)nvidia logo when you startx you'll have to live with running the ./Nvidiainstaller once in a while.

I would go for the second option in a heartbeat it takes me less then 5 minutes to do so. 

Advantage is you have your driver compiled exactly for your kernel how sweet is that.

To meet you halfway it would be nice that if a kernel package will present itself for an update it should warn you of problems that might occur in the update manager. ;)

Lol, fair enough.

I am a bit confused though when you say go with the xgl ones in the repos and when you mention running ./Nvidiainstaller... I've never heard of ./Nvidiainstaller and by the xgl ones from the repos, do you just mean as opposed to downloading the driver from nvidias site? If so, then that's not a solution, because I am using (and always have used) the driver from the repos (nvidia-glx not the opensource nv one).

---

### Post by vavoem on 2006-07-12
sorry misunderstood that 
I assumed you had the 3rd party Nvidia driver installed.

My mistake.](*,) 

Then i review my opinion and agree with you they(the guys @ ubuntu) should take account of such a major problem.

However installing the nvidia driver still will get you up and running in under 5 minutes (might be worth looking into) ;)

---

### Post by viciouslime on 2006-07-12
Yeh might just do that, sounds like it is easier than having the repo version!

Thanks

---

