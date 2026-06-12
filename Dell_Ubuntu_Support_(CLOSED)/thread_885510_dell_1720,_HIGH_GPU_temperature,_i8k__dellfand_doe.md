---
title: "dell 1720, HIGH GPU temperature, i8k* / dellfand does not work !"
date: 2008-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by raaaaraaaa on 2008-08-10
Hello,

i have Dell Vostro(Inspiron) 1720 notebook. Normal temperature is 60 C and during 15 min. of gaming grows up to 90 C ( 194F ) !
**In Ubuntu 8.04 is cooling fan speed constant !**  (windows vista regulate fan speed in a better way < below 80C during gaming).

I installed i8k* apps + gkrellm plugin for dell laptops. I wrote to etc/modules : "i8kmon force=1" ,but after restart ubuntu freezes always after userlogin. 
( Why ? I thought that modules are loaded to kernel sooner then after user login ? I started recovery console and remove i8kmon from etc/modules and ubuntu happily works again...)

Dellfand utility have the same effect, ubuntu freeze and on my laptop two indicators (caps lock + scroll lock indicators) blinking. 

Are there some other ways how to regulate cooling fan speed or some driver "patch" for my notebook...

* i googled that caps lock + scroll lock blinking : 
"blinking keyboard lights means you had a kernel panic. use kdump to dump the kernel and figure out what is causing the panic." ...but i am just newbie, or you want see some kernel dumps guys ? 

thank you !

---

### Post by linux_tech on 2008-08-10
Working with dellfand-

Have you checked this web page to make sure your using correctly
[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)
It basically runs as a daemon in etc/initd

First Download/Build 
dellfand-0.9.tar.bz2 

Extract with 
tar xvf dellfand-0.9.tar.bz2 

cd to that location,
cd dellfand-0.9 

make 

After you make the file, copy dellfand to /usr/sbin
sudo cp dellfand /usr/sbin 

then the script is copied to etc/init.d
sudo cp etc.init.d.dellfand /etc/init.d/dellfand 

next start the program 
sudo /etc/init.d/dellfand start 

configure the program 
sudo dellfand 1 8 30 37 45

---

### Post by raaaaraaaa on 2008-08-11
When i start script in etc/init.d, dellfand start 
cooling fans really change speed ! (thats great) but in few second i got kernel panic again :( 

i tryied to uninstall sensors* and gkrellm apps and use only dellfand but this does not help :(

after hard restart i look on dmesg output but no errors inside, so what i can do now ?

---

### Post by linux_tech on 2008-08-11
It sounds like the kernal or a module may have gotten changed from the gkrellm utility. There are a few other possibilities besides dellfand, but they would probably have same effect.

Have you undone all changes that were made with gkrellm?

Have you tried selecting previous kernal at boot menu and booting to it?

Do you get any kernal panic if you do not use any fan utilities?

Have you run any updates?

Have you tried installing another kernal version yet?

---

### Post by raaaaraaaa on 2008-08-11
> **linux_tech said:**
> It sounds like the kernal or a module may have gotten changed from the gkrellm utility. There are a few other possibilities besides dellfand, but they would probably have same effect.

Have you undone all changes that were made with gkrellm?
 Undone ? Yes all this *krell* *sensors* i8k* utilities are removed.

> Have you tried selecting previous kernal at boot menu and booting to it?
I do not see in boot menu previous version of kernel - i have Ubuntu 8.04.1, kernel 2.6.24-19-generic

> Do you get any kernal panic if you do not use any fan utilities? 
YES, 
I saw kernel panic also when i tryied install modules i8kmon module ( etc/modules : "i8kmon force=1" ) week ago. As i said all sensors, i8k and gkrellm applications are uninstalled now. 

> Have you run any updates?
Yes, just auto-updates i have fully actualized 32bit Ubuntu hardy OS.

> Have you tried installing another kernal version yet?
i install just auto-updates, so i guess no. How i can install new kernel version or do you think i can compile my kernel again ? (i saw some howtos about kernel : [http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way](http://www.howtoforge.com/roll_a_kernel_debian_ubuntu_way) )

---

### Post by linux_tech on 2008-08-11
Did selecting a different kernal in the boot menu still cause the kernal panic w/ dellfand?

is the there any errors listed in /var/logs/-
 sudo cat /var/log/messages


First see what the cpu utilization is- open terminal, type:
 sudo apt-get install htop
htop

If you notice a process that is eating up alot of cpu, you can stop that process

Lowering cpu frequency helps sometimes to lower temp:
To set the CPU frequency lower than full-
$ sudo cpufreq-selector -g powersave
If this helps this can be made into a shell script.

To bring back the CPU to full frequency-
$ sudo cpufreq-selector -g performance

Another fan utility to try is fan-04.tz,
It needs to be compiled, there is a readme in the folder [http://www.angelfire.com/punk4/bofn1001/fan-0.4.tgz](http://www.angelfire.com/punk4/bofn1001/fan-0.4.tgz)

If you want to pursue loading other kernals-
First do a search to find them. Open a terminal type:
apt-cache search linux-image 

If you want to see what you have : dpkg -l "*linux-image*"

Running apt-cache search linux-image gives you a long list of kernals to pick from.  I usually just cut and paste from this list into synaptic pkg
manager, search and apply.  Select x86, 32 or 64 bit, smp (dual core), non-smp etc.  To see what you currently have type cname -a.  If you reselect one that is already in your boot list then it will be reinstalled.  The kernal packages can also include modules, so reinstalling the kernal is reinstalling the modules as well. I use Grub and after I installed the kernal pkg, it edited the boot list as well  so the new kernals are added and can now be selected upon reboot. If you want to uninstall a kernal, go back to synaptic and uninstall.

You can also update the kernal -
Click on System > Administration > Update Manager > Click on Check button > Apply all updates including kernel. 

Bios settings can be reset to default, bios can be reflashed, power management in bios can be togged on and off (if bios settings or power management is causing the heat /kernal issue, then this may help)

Its also possible to do a repair using the cd. Of course you could also reinstall again.

With laptops its a good idea to run some air through the heatsink to remove dust every few months.  Just remove the keyboard and blow the air thru the heatsink, out through the vent in the case. 

I also use a good thermal pad as well when I use a laptop for over 4 hours.

Since your laptop has been running really high temp, I would also replace the thermal grease on the cpu as well.

If it turns out to be a hardware issue, then replacing the cpu and/or system board usually fixes this-- Dell warranty.

I hope some of these ideas are helpful to you and you are able to lower the cpu temp

---

### Post by PinkFloyd102489 on 2008-08-11
Nothing really to with dellfand, but my friend and I have heard that some recently made Nvidia GPUs are defective and overheat. His was and he had to send it back to Dell to get it replaced.

Might want to check into that

---

### Post by raaaaraaaa on 2008-08-12
Thank you, i will try another kernel version. But before i want backup my partition so be patient please. I will contact dell support also.

thank you

---

### Post by zapolsky on 2008-11-01
I have the same trouble with my Vostro 1510 and Debian Lenny (2.6.26 kernel). Kernel crashes after several/ a lot of attempts to get /set fan speed via i8k module (bug of the module). I found workaround.You should remove i8k plugin from gkrealm/gnome-sensors applet or simply don't use any of them.
Speed of fun can be changed using i8kctl fan 1 1  (slow speed) / fan 1 2 (fast speed) / fan 1 0 (disable fan). Don't try to make script because a lot of attempts will cause kernel crash.


P.S. I am trying to fix the bug so shall report when it will be fixed.

---

### Post by aum11 on 2009-02-28
I am having exactly the same problems with a brand new Dell Vostro 1710.

Has any workaround or fix been discovered?

Is there any danger in running the 1710 without the Gkrellm fan utility ?  IE will it overheat?

Suggestions and advise please.

---

### Post by Mr_bleu on 2009-03-05
Download:
[http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)
Save to Desktop.
system>administration>synaptic manager
Install g++ (I clicked the Search button and typed it in)
Untar the file (I'm a former windows user so I double click, then extract)
Open a terminal
$cd ~/Desktop/dellfand-0.7
$chmod a+x dellfand
$sudo cp dellfand /usr/bin
$sudo cp etc.default.dellfand /usr/bin
$sudo cp etc.init.d.dellfand
$sudo dellfand (This will display current fan status output and temp)
$sudo dellfand 1 10 25 35 43 (My personal settings for dellfan)
OR
$sudo dellfand 0 10 25 35 43 (This will output the status until the terminal is closed)
output from the above command:
Fan 0 Status 2->1 Speed 123960 CPU Temp 37C

I have a previous post on getting this running.  I have an e1505 and it works for me.

Currently running 8.10

---

