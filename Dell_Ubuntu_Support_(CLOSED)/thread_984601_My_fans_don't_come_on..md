---
title: "My fans don't come on."
date: 2008-11-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Oditius on 2008-11-16
I just installed Ubuntu 8.10 on my Dell XPS M1730. But the fans don't seem to come on. In Vista I used i8k to keep track of tempratures. But the system took care of the fans. I am affraid my laptop over heating. I am new to Linux. So please tell me step by step on where to find this program, and how to install it. I did a search and most of it seems confusing.

---

### Post by boof1988 on 2008-11-16
The [sensors-applet](http://packages.ubuntu.com/intrepid/sensors-applet) may be a good start.  You can install it using Synaptic Package Manager or CLI (your Terminal interface).

My fan doesn't run very much either... the CPU temps are usually (42C,55C).  I think ~55C is when the fan speeds-up/starts and I'm not sure what temp the fan slows/stops (~48C maybe).

Hope this helps.

---

### Post by sirjoebob on 2008-11-16
This is a noted issue with dell notebooks. You need to use i8k utilities. You can easily find more info but for starters, you will need to fire up synaptic and install the i8k-utils and I would recommend gkrellm and the i8k addon to manage fans.

---

### Post by sirjoebob on 2008-11-16
Check [this link]("http://www.osbank.net/winxp-2-dellbuntu/2007/12/ubuntu-fan-control-with-gkrellm.html") for details on using gkrellm to manage dell fans. This is a known issue that affects tons of dell laptops. 

It is an easy fix though and works great. I use it every day.

---

### Post by Oditius on 2008-11-16
> **sirjoebob said:**
> Check [this link]("http://www.osbank.net/winxp-2-dellbuntu/2007/12/ubuntu-fan-control-with-gkrellm.html") for details on using gkrellm to manage dell fans. This is a known issue that affects tons of dell laptops. 

It is an easy fix though and works great. I use it every day.

Easy for some, but the answer still goes over my head. I have gkrellm installed. But I still don't see how to install i8k to it. I am affraid that if I don't get the fans running soon, I will revert to Vista. When I restarted in Vista the temp was 69c. A lot hotter than the norm of 55. So I can't keep these ubuntu sessions too long.

---

### Post by linux_tech on 2008-11-16
Dellfand"
[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/) 

Now, open up the terminal and then navigate to the dellfand folder. 

If you downloaded it to your "home" folder, use this.
cd /home/USERNAME/dellfand-0.9 
make 
Now, copy some files to new locations

```
sudo cp dellfand /usr/sbin 
```
enter your password...

```
sudo cp etc.init.d.dellfand /etc/init.d/dellfand 
```

```
sudo cp etc.default.dellfand /etc/default/dellfand 
```
To start the Daemon, type-

```
sudo /etc/init.d/dellfand start 
```
Now, instead of typing that line, ever time you start your laptop.  It will add Dellfand to your start-up programs.
```
sudo update-rc.d dellfand multiuser 
```

Configure Dellfand.
If you type "sudo dellfand"
the daemon will tell you your computer temperature, the fan being controlled, version, status, and fan speed.

ie.  v0.9: Fan 0 Status 1 Speed 76440 CPU Temp 40C

"sudo dellfand 1 5 28 36 43"[/code]
---> the above command tells dellfand the following.

1 = Work in the background (if you set this to "0" it will continually update about fan speed and CPU temp)
5 = Check CPU temperature every 5 seconds
28 = Turn the fan OFF when below 28 Degrees Celsius.
36 = Turn the fan to LOW when temp reaches 36 Celsius
43 = Turn the fan to HIGH when temperature is over 43 Celsius

You can change these numbers but keep numbers below 60 or it will give you errors

Also, to turn OFF dellfand use

```
sudo /etc/init.d/dellfand stop 
```
IF you don't do this, your BIOS may report that you have incorrect power intake and that there is something wrong with your fans.

---

### Post by Oditius on 2008-11-16
Oh well, that didn't help a lot. I don't have the slighest idea how to get it to work. It took me a minute to find this "terminal" program. I did manage to get to the folder. but that is where I got lost.

oditius@rodney-xps:~/dellfand-0.9$ cd /home/oditius/dellfand-0.9 make
oditius@rodney-xps:~/dellfand-0.9$ sudo cp dellfand /usr/sbin
[sudo] password for oditius: 
cp: cannot stat `dellfand': No such file or directory
oditius@rodney-xps:~/dellfand-0.9$ sudo cp etc.init.d.dellfand /etc/init.d/dellfand
oditius@rodney-xps:~/dellfand-0.9$ sudo cp etc.default.dellfand /etc/default/dellfand
oditius@rodney-xps:~/dellfand-0.9$ sudo /etc/init.d/dellfand start
oditius@rodney-xps:~/dellfand-0.9$ sudo dellfand
sudo: dellfand: command not found
oditius@rodney-xps:~/dellfand-0.9$

---

### Post by sirjoebob on 2008-11-17
> **sirjoebob said:**
> Check [this link]("http://www.osbank.net/winxp-2-dellbuntu/2007/12/ubuntu-fan-control-with-gkrellm.html")

Follow the instructions there for installing i8k-utils and everything you need to get it working. anything it says to "run" just needs to be typed into the terminal.

---

### Post by Oditius on 2008-11-17
> **sirjoebob said:**
> Follow the instructions there for installing i8k-utils and everything you need to get it working. anything it says to "run" just needs to be typed into the terminal.

Been there, sorry to sound like an idiot, and I appreciated the help, but I can read and read, but sometimes things that are suppose to be there, I just can't find. Like the following:

> and check the gkrellm and the gkrellm-i8k packages for installation. 

I did find the gkrellm, but not the gkrellm-i8k package.


> After installing, I opened $EDITOR and saved the following to ~/bin/fan:


I can't seem to find a program called "$EDITOR" on this system. 

Oh Well, this may be unnesssary, becasuse I can hear the fans on now. They are on low, but I can hear them spinning. I just think the temp might be a little high. Like I have said in the prior post here. I like Vista, but I have it running as fast and as well as it could possible go. I am just bored and am experimenting with Linux. It took me about 6 months before I deleted WinXP off my dual boot system. Who knows, I may just do the same with Vista?** Oh BTW, how do you spell check in here?** :(

---

### Post by boof1988 on 2008-11-17
> **Oditius said:**
> **Oh BTW, how do you spell check in here?** :(

I use FireFox browser so (for me) in the browser:

_E_dit >> Prefere_n_ces >> "General" tab... brings up the attached screen-capture.  I then make sure the proper box is checked ["Check my spelling as I _t_ype"].

---

### Post by Oditius on 2008-11-17
Thanks, I will look into that. :guitar:

---

### Post by sirjoebob on 2008-11-17
Sorry that we haven't been able to get this resolved so far. We will keep at it though.. I am watching this thread to try and help you out. I had this same issue when I got my Dell Vostro laptop and had to frantically search to get my fans functioning. 

Try this: Make sure that you have third-party repositories enabled. To do this under synaptic, go to settings>repositories

Go to the third-party software tab and check any that are in there. Close it and allow it to update the packages. Then check again for the gkrellm-i8k. Let me know if this does not do it and I will try to come up with something...

---

### Post by Oditius on 2008-11-17
> **sirjoebob said:**
> Try this: Make sure that you have third-party repositories enabled. To do this under synaptic, go to settings>repositories

Go to the third-party software tab and check any that are in there. Close it and allow it to update the packages. Then check again for the gkrellm-i8k. Let me know if this does not do it and I will try to come up with something...

I am afraid it still isn't there. So I am still lost. :confused: Something I failed to mention. I loaded the 64 bit version of Ubuntu. Is that going to be a problem?

---

### Post by sirjoebob on 2008-11-17
Try just typing into terminal "sudo apt-get install gkrellm-i8k" without quotes. and see what that does. Let me know if it does not work.

---

### Post by Oditius on 2008-11-17
> **sirjoebob said:**
> Try just typing into terminal "sudo apt-get install gkrellm-i8k" without quotes. and see what that does. Let me know if it does not work.

oditius@rodney-xps:~$ sudo apt-get install gkrellm-i8k
[sudo] password for oditius: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gkrellm-i8k
oditius@rodney-xps:~$ 


I guess not. :(

---

### Post by sirjoebob on 2008-11-17
Hmmmm... I honestly don't know why you cant access that package... Anybody else have any ideas to help them out??? 

I have never had an issue with it not finding the packages. Take care running that system until you get it working though and dont run anything to graphic-intensive. this could harm your cpu.

---

### Post by Oditius on 2008-11-17
I have to force a shutdown, the computer froze and lights started blinking all over the place. So I guess I'll stay out of Ubuntu for a a while.

---

### Post by sirjoebob on 2008-11-17
I am sorry I have not been much help. There are good tutorials out there (better  than what I found) but you may have to look around a little.

---

### Post by Oditius on 2008-11-18
I have been looking. Oh well, guess I will just give up on Linux. ](*,) I am not going to fry my laptop over an operating system. [-X I might try tech support and see what they say. I know that they won't support the OS (Because this M1730 came with XP) But the fans are suppose to be controlled by the BIOS, and not software. So maybe I can get help in that manner? I mean, they have already replaced the keyboard once, and just recently they replaced the motherboard. =D> (I broke that little black tab that holds the HD ribbon down.:shock:) So unless they want to come out and replace it again, I might suggest they help me out in getting the fans to work in Ubuntu. ;-)

---

### Post by sirjoebob on 2008-11-18
Have you checked on Dell's support forums? With the amount of Linux pre-installed laptops they sell I imagine they would have a sticky on i8k support.

Also, are you running the standard 32bit or 64bit version of ubuntu?

---

### Post by Oditius on 2008-11-18
I have check the forum, but it is a bit hard to navigate. Also I was using the 64 bit version. I installed Mandriva hoping it would solve the problem, but it seems it is the same. Thanks for you concern and answer. I will keep searching.

---

### Post by sirjoebob on 2008-11-18
I have never ran the 64 bit version. That may be why you were unable to find the gkrellm-i8k package.

---

### Post by Oditius on 2008-11-19
I have reinstalled the 64 bit version. I have a posting I found:

[https://answers.launchpad.net/ubuntu/+question/36311](https://answers.launchpad.net/ubuntu/+question/36311)

in launch-pad that might have had the answer. I did what it said, and I think I hear the fans running on low. [-o< so I hope I have it working.

---

### Post by dt_ on 2008-11-19
I've just installed Ubuntu on my M1530 and haven't noticed problems with the fans, but then again I haven't used it *extensively* yet, and I don't know what's normal or not.

Is the "fans not spinning" issue happening for ALL models or only some? :/

---

### Post by sirjoebob on 2008-11-19
To my understanding, it is all dell laptops.

---

### Post by sirjoebob on 2008-11-19
Just ran across another forum post that may solve this for you:

[http://backports.ubuntuforums.com/showthread.php?t=842775]("http://backports.ubuntuforums.com/showthread.php?t=842775")

---

