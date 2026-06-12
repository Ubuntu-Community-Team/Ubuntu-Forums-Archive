---
title: "Dell XPS M1330 temperature issue"
date: 2009-03-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yongkailoon on 2009-03-13
I've read around and searched for possible solutions to this but I really don't know how to solve this. My Dell XPS M1330 is currently running on Ubuntu 8.10, it is dual-booting with Windows Vista.

On Windows Vista, the fan is quite silent (barely able to hear it as it only kicks in when it is needed) and the temperature (based on the palm rest area) is also cool. However, after I decided to install Ubuntu and give it a try, everything seems to work like a charm except for the fan and temperature issue, the fan is at a higher speed (I guess Ubuntu makes this fan speed as default) and the temperature (based on the palm rest area) is really warm and tends to get hot if I run a more intensive application.

Now, what could be the best possible solution to this? Also, it is really warm on the palm rest area especially on the left side which is where the hard disk is, does this got anything to do with the heat?

Thank you all in advance.

---

### Post by nwadams on 2009-03-14
Thats interesting. I have an XPS m1330 as well and have not noticed any temperature difference or extra fan activity. Do you have the latest A15 bios?

---

### Post by bigbrovar on 2009-03-15
what graphic card are you using? intel or nvidia ..

---

### Post by nwadams on 2009-03-15
intel

---

### Post by yongkailoon on 2009-03-15
As for me, I'm using the NVidia GeForce 8400m GS.

---

### Post by sdennie on 2009-03-15
The left side is always the hot side.  From my observations, the video card and hard drive are both jammed into there.  It's probably not (completely) that the hard drive is getting hot, it's that the video card is getting hot and transferring heat to the hard drive where you notice it because that's where your palm rests (rather than where your fingers briefly touch your elevated and so cooled keys above the video card).

Have a look at this guide: [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773").  The settings are meant for power savings but, some of them also reduce heat while the machine is on AC power.  The video card isn't the only influence on the disk temperature and increasing the amount of time it's spun down can reduce the temperature by 2C or 3C in my experience.  The linked guide is aging and so I've made many refinements since then but, it's the general idea.

---

### Post by yongkailoon on 2009-03-15
Thank you for the link, I'll try some steps there and if the problem is still there, I guess I'll just live with it as it isn't a big issue but I'm just afraid that my laptop will die off faster due to heat problems.

---

### Post by sdennie on 2009-03-15
> **yongkailoon said:**
> Thank you for the link, I'll try some steps there and if the problem is still there, I guess I'll just live with it as it isn't a big issue but I'm just afraid that my laptop will die off faster due to heat problems.

In this case, heat levels that are dangerous to the hardware would probably also be associated with physical injury to your left palm.  Yes, depending on what battery is in (so, the airflow by using a 9-cell battery), the surface it's on, the ambient temperature of the room, how you are using the machine, the power savings features you are using, etc, it can get warm.  Warm is different than hot though.  If you touch the machine and think, "This is certain above room temperature", you are probably ok.  If you touch it and think, "I wonder if this could burn me", you need to worry.

---

### Post by yongkailoon on 2009-03-15
Well, if I switch on my air-conditioner then the laptop will just be warm and it is tolerable. If I don't switch on my air-conditioner then the laptop tends to get quite hot especially if I'm watching a movie or just simply by doing something with my laptop.

---

### Post by sdennie on 2009-03-16
How old is your XPS M1330?  Have you ever cleaned all the vents of the machine with compressed air?  It can make a very large difference with respect to heat.  

Out of curiosity, can you post the output of the following when the machine is both hot and not hot:

```

cat /proc/acpi/thermal_zone/THM/temperature
nvidia-settings -q all | grep Temp
sudo smartctl -a /dev/sda | grep Temp

```

For the last one, you may have to first:

```

sudo apt-get install smartmontools

```

---

### Post by Leaf_Killer on 2009-03-17
My M1330 has the exact same issues as yours when running Ubuntu 8.10.

The CPU temp and GPU temp are completely the same as in windows except underneath the laptop beneath the wireless card and touchpad gets scorching hot. If I boot back into windows 7 the area goes back to an acceptable temperature again.

I have no idea what is causing this issue but it is definitely Ubuntu.

I took off all the bottom covers and the CPU + GPU heatpipe was lukewarm to the touch as expected but the wireless card was so hot I couldn't hold my finger on it.

Is there a driver I need to download to make it use some sort of power saving feature for the wireless card or to just cool it down?

---

### Post by sdennie on 2009-03-17
You could enable power savings for the wireless card at all times if you want.  Try running the following commands in the terminal:

```

sudo sh -c "echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level"
sudo iwconfig wlan0 txpower 7

```

If that reduces the heat, you can take steps to make those settings permanent.

---

### Post by eyime on 2009-04-10
Hi,

I've searching for a solution of this problem. I think my laptop is heating too.

This is my output

eugenio@xps-laptop:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             46 C
eugenio@xps-laptop:~$ sudo smartctl -a /dev/sda | grep Temp
[sudo] password for eugenio: 
194 Temperature_Celsius     0x0022   115   094   000    Old_age   Always       -       41 (Lifetime Min/Max 22/48)


What are the right values ?. Is there a way to keep the temperature lower than 40 C ?

Thanks.

---

### Post by nwadams on 2009-04-10
those values seem fine. Nothing wrong with either of them. As long as your HDD stays below 50 you are fine. and your cpu well, i've had mine up to 70 with no problems.

---

### Post by eyime on 2009-04-10
Well, 

now I got this,

eugenio@xps-laptop:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             59 C
eugenio@xps-laptop:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             58 C
eugenio@xps-laptop:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             57 C
eugenio@xps-laptop:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             57 C
eugenio@xps-laptop:~$ sudo smartctl -a /dev/sda | grep Temp
194 Temperature_Celsius     0x0022   115   094   000    Old_age   Always       -       41 (Lifetime Min/Max 22/48)
eugenio@xps-laptop:~$ 

Then, now there is a problem.

---

### Post by nwadams on 2009-04-10
no, the THM/temperature reading is your cpu core. its fine up to 70 atleast. most are rated to 85. 

the second one is your hdd, which 41 is a perfectly normal temp

EDIT: your fan probably doesn't even kick in till 60

---

### Post by eyime on 2009-04-10
>> EDIT: your fan probably doesn't even kick in till 60

Is possible to set on the fan at a lower temp, for example 45C ?

---

### Post by nwadams on 2009-04-10
umm, ya that I do not know. normally its bios driven, also it will depend on load. I'm just doing a basic test of getting the hardest level ai to play chess against itself and my fan kicked in on low at 55 or so. and then its staying that way unless it gets really hot, so at about 70 it goes into fast mode. 

I have the fan on low at 66 degrees right now on heavy load. 

I have the 9 cell battery though so i ahve some xtra clearance for air flow. 

I'll look into adjusting the fan, but i don't think we can, because its bios driven and i dont' think we can adjust how it works at all. The response of the fan to higher temperatures is the same regardless of OS, it was set by dell so it is safe. if u want it cooler u may be able to force the fan to go on...but i'm not sure how.

---

### Post by enbeto on 2009-08-10
Hi!
I have been experiencing the same overheating problem with the same model, also nvidia card. After trying and reading all advices given in that thread including Vor's Howto**** about power savings linked above without any success I decided to open my computer and take a look and... wow! I removed the bottom cover, the one with three screws and another one in the midle, and used a flashlight to see the air output from inside. It was completely full of dust masses which were suffocating my computer. I had to use tweezers and a lot of patience to take all that stuff out but, when I did, yes! everything was solved and my laptot is now cool and fresh as it was when I bought it. Also the fan is almost not working.
By the way, it is just one year old but was enough to develope the tumor.
Now I can compile, compute big stuff and force my machine without ubuntu deciding to stop because of overheat. Also my room is much fresh:)
Hope it helps!

---

### Post by pitbullthe1st on 2009-08-23
:lolflag:I have this over heating problem with my dell xps m1530 with nvidia card and it's only 4 months old.  

Also I can't check if its ok in windows as when I received the laptop the first thing I did was  remove windows. 

However I'm using Ubuntu 9.04.  I would not say it is hot enough to burn but it is to hot to have your hand on for any length of time.

I have tryed some of the options above in this thread but most of them will not work. 

Here is the out put from them:

[INDENT]pitbullthe1st@Dell-XPS-Ubuntu:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             38 C
pitbullthe1st@Dell-XPS-Ubuntu:~$ vidia-settings -q all | grep Temp
bash: vidia-settings: command not found
pitbullthe1st@Dell-XPS-Ubuntu:~$ nvidia-settings -q all | grep Temp
  Attribute 'GPUCoreTemp' (Dell-XPS-Ubuntu:0.0): 60.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.
pitbullthe1st@Dell-XPS-Ubuntu:~$ sudo smartctl -a /dev/sda | grep Temp
194 Temperature_Celsius     0x0022   101   096   000    Old_age   Always       -       46
pitbullthe1st@Dell-XPS-Ubuntu:~$ sudo sh -c "echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level"
sh: cannot create /sys/bus/pci/drivers/iwl????/0000:??:00.0/power_level: Directory nonexistent[/INDENT]

I also have another problem and I'm not sure if it's linked but sometimes it will restart the xserver for no reason that I know of and has on ocation just restarted the computer.

---

### Post by enbeto on 2009-09-10
Hi [pitbullthe1st]("http://ubuntuforums.org/member.php?u=704754"),

first I think you should change in the line "sudo sh -c "echo 5 > /sys/bus/pci/drivers/iwl????/0000\:???:?\:00.0/power_level" the ??? and :???: by whatever you need in your case, which I think depends on the drivers you are using... In my case it is 
/sys/bus/pci/drivers/iwlagn/0000:0c:00.0/power_level.
On the other hand, have you experienced the heat problem from the very begining? Or it is something that "suddenly" appeared when maybe upgrading to jaunty? I'm telling this because I really thought it was due to jaunty but it wasn't... I really expended a lot of time looking and trying different things but the problem was the dust it had inside, really. It was just one year old but I was experiencing this problems since some months ago.... If you have not solved it yet maybe you should consider opening your computer and taking a look inside as explained above...
Regarding your xserver restarting I don't have any idea about what could it be due to...

---

### Post by pitbullthe1st on 2009-09-10
Hi,

Thanks for your reply.  I have tried the command: 

sudo sh -c "echo 5 > /sys/bus/pci/drivers/iwlagn/0000:0b:00.0/power_level"

And I wait to see if it works, but could you please explane the command?

Also yes I have experienced this since I've had it but I will look in to giving it a hoover out as it was a reconditioned laptop.  

I don't know if it makes a difference but I'm using the latest video driver from nVidia not the Ubuntu one. 

Thanks

---

### Post by enbeto on 2009-09-13
Hi,
sincerely, I don't have any idea about what this command is for... I'm sorry!
Concerning the nvidia drivers, I don't either have a clue, sorry again... Maybe you could try using the ubuntu proposed ones and see if there is any difference, who knows...

---

### Post by x C0MMAND0 x on 2009-09-13
I know that compiz increases the heat a lot, because I also have an XPS m1330 and if I am doing a lot of flashy effects it heats up alot.  Also, i feel that the fans on it aren't the best and if I have it flat on a desk it heats up quite a bit.  By putting the back end of the laptop on a small (1cm) book or so that elevates the laptop just a tiny bit, the temperature is in a very normal range.  That is just what I have noticed from experience.

---

### Post by tehownt on 2009-09-28
There's a well documented problem with the XPS M1330, especially the ones w/ nVidia 8400m GPUs (I think there's even also a class action suit against nVidia, and Dell has even extended the laptop warranty because of the problem).

This should help you a _lot_ :
[http://forum.notebookreview.com/showthread.php?t=268081](http://forum.notebookreview.com/showthread.php?t=268081)

It will cost you <15$ and greatly decrease your GPU temperature (on both idle and load) and your CPU too since it's on the same heatpipe.

It will also help your laptop last more than a few years.

For me it dropped the GPU temp from 70°C to 60°C when idle and from 100°C to 70°C on full load.

The CPU dropped to < 50°C idle and 60°C on load.

You can install the i8kmon tool suite in order to "control" the fan, but for me it's only temporary.

---

### Post by 3dinos on 2009-10-01
Confirmed, my xps 1330 with nvidia 8400 was practically
useless for the whole year I got stuck with it. Resets due
to overheat about every half hour, and damaged LCD (the
infamous 'color stripes' problem on youtube) twice
within months. 

I had to replace LCD and GPU three times throughout
the year, to be able to get Dell to give me a replacement;
and even then it was quite a job, defeating arguments,
writing letters, etc..

Anyways the replacement was the studio xps 1340 with
nvidia 9400, which doesn't have any such issues at all.
Actually it's pretty powerful while cool and silent. Better
overall quality too. The only thing I didn't like was the
non-standard keyboard layout.

Dinos

---

### Post by Ivkosky on 2010-06-19
> **sdennie said:**
> You could enable power savings for the wireless card at all times if you want.  Try running the following commands in the terminal:

```

sudo sh -c "echo 5 > /sys/bus/pci/drivers/iwl????/0000\:??\:00.0/power_level"
sudo iwconfig wlan0 txpower 7

```

If that reduces the heat, you can take steps to make those settings permanent.

Hi

I am just struggling with the overheating problem with my Dell M1330 as well. I tried to apply your commands, but this is what I got

```
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; No such device.
```

I have also posted my issue and concerns in this tread:
[http://ubuntuforums.org/showpost.php?p=9322979&postcount=228](http://ubuntuforums.org/showpost.php?p=9322979&postcount=228)

I would be grateful for any help!

---

### Post by neomanaidin on 2010-06-20
Hi guys, 
I am having a similar problem here. I am using a dell XPS m1530 and untill last month I was using windows vista. I decided to use ubuntu 10.04 after its release and I totally removed vista and installed 10.04. It was the only OS in my computer. It worked great and I decided to use it like forever. But I needed windows for a project and I had to partitiion my HDD and install windows there and I installed windows 7 and I also installed ubuntu 10.04 with dual-boot. However now my hdd is burning when ubuntu is working. I can't touch the left side of the touchpad(not literally but it is quite hot compared to windows 7). In windows &#305;t does not heat like this. It is quite normal as it was before. And it was not getting hot like this with ubuntu when it was the only OS in the computer. Does it have anything to do with allocating the HDD? Or are there anything you can help me out? My cooling fans are perfectly clean since I replaced them recently.

---

### Post by schopde on 2011-10-11
Hi, 
I have a Dell XPS m1330 for 3 years now running Vista and subsequently Windows 7 (64 bit). Overheating has always been a problem. It used to get really hot at the back where the fans are and the fans never took a rest.
 
I recently loaded Ubuntu 11.04 (WUBI) and the computer is really cool now at the back with the fans starting only intermittently.
However, the wireless card (i'm assuming thats installed below the touchpad) gets really hot. (Intel Wifi Link 4965AGN)
 
I realize some of you have had this issue in the past. Is there any tried & tested solution for this? Please help.

---

### Post by x C0MMAND0 x on 2011-10-13
I have never heard of a wireless adapter overheating, ever.  It is almost always overheating due to a graphics card or main CPU, or poor ventilation.  Make sure you have the latest nVidia drivers installed for you system and that your fans and everything are clean and running okay as a starting point.

---

### Post by schopde on 2011-10-20
Thanx Command0.

You may be right.. but the truth is the front portion gets really hot... It's the HDD and the wireless card. IT could be that the HDD heat is dissipating to the wireless card and hence the whole area gets hot. But, this never happened with Win 7. Can you please suggest some solution?
Thanks.

---

