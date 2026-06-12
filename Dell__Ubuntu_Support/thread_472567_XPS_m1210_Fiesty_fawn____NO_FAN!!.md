---
title: "XPS m1210 Fiesty fawn    NO FAN!!"
date: 2007-06-13
forum: Dell  Ubuntu Support
---

### Post by newtimes on 2007-06-13
just noticed fan has not come on since 7.04 was loaded.

any suggestions?

---

### Post by damn66 on 2007-06-13
> **newtimes said:**
> just noticed fan has not come on since 7.04 was loaded.

any suggestions?
i've noticed it too and downloaded gkrellm to monitor cpu temp..temp been hovering ard 47C-51C..

---

### Post by fjgaude on 2007-06-13
I did installed Gkrellm also. Its shows my temp between 47C to 56C, and I can't recall hearing any fan or fans come on yet. Box seems to run cool for a powerful, Core 2 Duo. Yes, it's quiet.

frank

---

### Post by newtimes on 2007-06-14
my m1210 seems to be in those same parameters but I would like the fans to come on.

when I was running vista the fans seem to run all the time.  is there a fan control software?

---

### Post by dannyboy79 on 2007-06-14
if your're saying that you think you have a case fan adn that it's not on and you want it to turn on, I would say the only way that'll happen is if it's connected to the motherboard just like the CPU fan and you'll most likely have to talk to dell about that one.

OR

if you're saying that you're CPU fan isn't running than I would say that you're going to burn out your cpu any minute! I would trust the temp in the bios before I trust the spotty ACPI support in linux or whatever tool  is used in linux to read the temps from the bios.

---

### Post by newtimes on 2007-06-14
> **dannyboy79 said:**
> if your're saying that you think you have a case fan adn that it's not on and you want it to turn on, I would say the only way that'll happen is if it's connected to the motherboard just like the CPU fan and you'll most likely have to talk to dell about that one.

OR

if you're saying that you're CPU fan isn't running than I would say that you're going to burn out your cpu any minute! I would trust the temp in the bios before I trust the spotty ACPI support in linux or whatever tool  is used in linux to read the temps from the bios.

This is a laptop that im using and have been for 4 days with 7.04 but fan has never come on.
I am worried about overheating.

---

### Post by dannyboy79 on 2007-06-14
i would call Dell to make sure this is normal

---

### Post by newtimes on 2007-06-15
> **dannyboy79 said:**
> i would call Dell to make sure this is normal

I called dell XPS support and they said they have no way to trouble shoot the problem and referred
 me to Canonical.  But he did tell that the temp should be running at 98 degrees F at top end
and 39 Degrees C at top end   so Fawn is running a little hot but not enough to worry according to the XPS tech.

---

### Post by arvevans on 2007-06-15
Go to Synaptic Package Manager and search for i8kutils:

[INDENT]utilities for Dell Inspiron and Latitude laptops
This is a collection of utilities to control Dell Inspiron and Latitude
laptops. It includes programs to turn the fan on and off, to read fan
status, CPU temperature, BIOS version and to handle the volume buttons
and Fn-keys.

The package includes also a small Tk applet, designed to be swallowed in the
gnome panel, which monitors the CPU temperature and controls automatically
the fans accordingly to user defined thresholds.

The programs require the kernel module i8k.o which can be compiled from
the package sources or found in Linux kernel 2.4.14 and later versions.
The kernel module has been tested only on Inspiron 8000 laptops but it
should work on any Inspiron and Latitude laptops.[/INDENT]

_._

---

### Post by kripkenstein on 2007-06-15
I'm no expert, but here are my thoughts:

1) If the CPU fan or case fan wasn't working at all, you should experience overheating very quickly (typically modern computers shut themselves off or reboot in such cases). So perhaps the fan is just very quiet?

2) Assuming that indeed one of your important fans isn't working, it should be easy to find out if this is a hardware issue or a software one. Do this: check what happens **before** you load the OS. For example, go into the BIOS settings and wait a bit. If the fan doesn't spin before the OS loads, it can't be the OS's fault. If it works before the OS loads but doesn't later, then it is an OS issue.

3) While you are in the BIOS, check for fan speed readings, many BIOSes have that nowadays. Also look at the temp readings (there may be several: CPU, case, HD, GPU, etc.)

Good luck, and keep us posted.

---

### Post by newtimes on 2007-06-15
> **kripkenstein said:**
> I'm no expert, but here are my thoughts:

1) If the CPU fan or case fan wasn't working at all, you should experience overheating very quickly (typically modern computers shut themselves off or reboot in such cases). So perhaps the fan is just very quiet?

2) Assuming that indeed one of your important fans isn't working, it should be easy to find out if this is a hardware issue or a software one. Do this: check what happens **before** you load the OS. For example, go into the BIOS settings and wait a bit. If the fan doesn't spin before the OS loads, it can't be the OS's fault. If it works before the OS loads but doesn't later, then it is an OS issue.

3) While you are in the BIOS, check for fan speed readings, many BIOSes have that nowadays. Also look at the temp readings (there may be several: CPU, case, HD, GPU, etc.)

Good luck, and keep us posted.


I thought of that.  maybe the fan is very slowly spinning.
what makes me say it is not working is because in vista it was like a hairdryer blowing out the side of my XPS but with Fawn  there is some heat but no forced air coming out.

---

### Post by newtimes on 2007-06-15
ok got both fans working now using this:

Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k


Thanks to all!

---

### Post by dannyboy79 on 2007-06-15
> **newtimes said:**
> ok got both fans working now using this:

Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k


Thanks to all!
you should almost create a thread within the HOW-TO section regarding this if there isn't already one as I am sure other's will notice the same thing with not only Dell laptops but possibly others. Also, this may help people who are having freezing or lockup issues if they can make sure that everything stays cool enough by forcing the fans to run. Just a thought.

If you don't want to create the thread, I will and give ya cred, just respond and let me know if you're going to do it so this way we don't both do it.

---

### Post by mättu on 2007-06-15
On my laptop (not a dell) there are trip-points specified in

/proc/acpi/thermal_zone/TZ1

critical (S5):           93 C
passive:                 91 C: tc1=1 tc2=2 tsp=100 devices=0xeffce7e0
active[0]:               78 C: devices=0xdffe14e0
active[1]:               72 C: devices=0xdffe1440
active[2]:               67 C: devices=0xdffe13c0
active[3]:               55 C: devices=0xdffe1340

Means: under 55C, there's no fan at all. My fan is off most of the time, unless on hot summer days or when the CPU is working *hard*.
All I know from vista is that it uses system ressources massively. Will your fan turn on if you make your computer work 100% for some time?
Here's my stupid perl-script to heat up my CPU a little. ;-) I wrote it because of some sort of a strange error: My fan never completely shut down unless I overstepped a trip-point..

```

#!/usr/bin/perl

while(){
	open (TEMP, '/proc/acpi/thermal_zone/TZ1/temperature'); #given there is your temperature stored.
	
	$a = <TEMP>;
	close TEMP;
	$a =~ s/\D//g;
	exit if ($a > 67);
	for $b (1..1000000){}
	system (cat, '/proc/acpi/thermal_zone/TZ1/temperature', '/proc/acpi/thermal_zone/TZ1/state');
        #..adjust if your temperature and thermal_zone messages are found somewhere else in /proc
}

```
(launch from terminal to see temperature & fan state)

cheers
:m)

---

### Post by raxso on 2007-11-03
Thanx,

Great How-To i have been looking for this for hours on the internet coz i couldn't get my i8kutils run.

Runs on my Dell Inspiron 6400

Keep it up:KS

---

### Post by Vevmesteren on 2007-12-11
Hey, I installed i8kutils and they are running fine. There is one value that worries me though. The AC Temperature, displayed right under the two proccesors usage percentage. It goes VERY high. The highest was 91 C, that scared me so I turned my mache off. What on earth drives my heat so high. I can barely put my laptop on my legs, if I wouldn't be wearing pants I would not be able to put it on my lap for sure. So something isn't right, I am sure. Help?

V

---

