---
title: "CPU and Network? Odd bug"
date: 2012-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Zinou87 on 2012-05-15
I have a very odd problem, i run ubuntu 11.10 on a Dell inspiron N4050 which has an Intel Core i3 CPU. For internet i have a CDMA broadband modem connection.

After a time of inactivity sometimes few seconds, sometimes 2 or three miutes or even more CPU2 3 and 4 spike then go to zero and only CPU1 still works. when activity is resumed by moving the cursor for example all CPUs are put on and the connection goes down as if the modem is completely disconnected and you have to physically disconnect the USB cable of the modem and reconnect it to be able te reconnect internet again

If you keep  the computer in activity by moving the cursor continuously this bug never happen

I don't know if putting off the three last cores of the CPU is an option to reduce power consumption or something like that... but it sure is annoying to have to recconect every few seconds

Every bit of help is appreciated, thanks in advance  

Here's some images

[[IMG]http://s18.postimage.org/3wqijhu2t/Capture_du_2012_05_13_23_14_26.jpg[/IMG]]("http://postimage.org/image/3wqijhu2t/")

[[IMG]http://s9.postimage.org/fgear7opn/Capture_du_2012_05_13_23_16_55.jpg[/IMG]]("http://postimage.org/image/fgear7opn/")

[[IMG]http://s15.postimage.org/nb8cg1ndj/Capture_du_2012_05_13_23_17_34.jpg[/IMG]]("http://postimage.org/image/nb8cg1ndj/")

---

### Post by DELL JonathanS on 2012-05-16
I work for Dell and I wanted to try to be of assistance for your issue. It's possible there is a problem with power management or the CDMA card drivers. The Inspiron 14 has Intel SpeedStep capability. You might try disabling that in BIOS by pressing F2 during POST to get into System Setup and going to the Advanced Tab, and set Intel SpeedStep to disabled, then go to the Exit tab and choose Save Changes and Reset. If it has no effect on the wireless card you may want to leave it enabled it since it can reduce power consumption. Also can you try to disable power management in Ubuntu and see if that changes this behavior? You can do that according to these steps: [http://ubuntuforums.org/showpost.php?p=5047303&postcount=4](http://ubuntuforums.org/showpost.php?p=5047303&postcount=4). I don't see that Dell has a Linux driver for any of the supported mobile broadband cards for this model. Which mobile broadband card and driver are you using?

---

### Post by Zinou87 on 2012-05-17
Thanks JonathanS, I already tried disabling SpeedStep from the BIOS interface, it actually made it worse, since when ubuntu boots up, it initially detects only one core of the CPU and the computer is too slow after working for a while the other cores are detected and the computer comes back to normal speed, but infortunately the same problem occurs.

Next, turning off the power management using the method described in the thread above insists on installing a program that is dependant on "menu" while this last one is installed on earlier versions of ubuntu than 11.10 which usus "unity", so i need to find another method that works on ubuntu 11.10.

Last for the internet i don't have a mobile broadband "card" but a mobile broadband modem: "ZTE  WF920F" and it sure needs no driver to function since it's working properly on a desktop PC (With Intel Core2 Duo CPU). with the same version of ubuntu

---

### Post by DELL JonathanS on 2012-06-06
Zinou I haven't been able to find any specific information about your broadband modem driver. Does the problem seem to get worse with time? Can you access the power management settings without Unity like shown here: [http://askubuntu.com/a/67361](http://askubuntu.com/a/67361) ?

---

### Post by Zinou87 on 2012-06-07
Jonathan, I was able to turn off power management via the method that you precised, but the problem still persists

---

### Post by DELL JonathanS on 2012-06-08
Do you find any output in the logs mentioned at [https://help.ubuntu.com/community/LinuxLogFiles#System_Logs](https://help.ubuntu.com/community/LinuxLogFiles#System_Logs) which seems to occur right around the time that the CPUs stop and the broadband modem disconnects? What does it say?

---

### Post by Zinou87 on 2012-06-09
Hello Jonathan, finally i  found the reason of the bug and i've been able te resolve it.
The source is a bug in a program named "powernap" and here's it's descripton from the software center"

> PowerNap watches a series of configurable monitors.  When no activity has occurred on any of these monitors for some specified time, PowerNap deems the system inactive, and takes action, as configured by the system administrator.

PowerNap can monitor:

User Activity (Console, Keyboard, Mouse)

System Activity (Load, Processes, Process IO)

Network Activity (wake-on-lan, UDP ports, TCP ports)

Some of these are event-based, while others are poll-based.  PowerNap's polling interval, INTERVAL_SECONDS, is configurable.

The required length of inactivity, ABSENT_SECONDS, is configurable.

The action taken by PowerNap when the system is active, is configurable, and might be one of pm-powersave, pm-suspend, pm-hibernate, poweroff, or any executable script as chosen by the system administrator.

See /etc/powernap/config for all configurable options and defaults.


What is weired is that i don't remember installing this program considering that is isn't a standard  service, so i checked the Software center's logs and found out that it was installed along when i installed "Synaptic" which is even weirder because "powernap" is not a dependancy for synaptic???

Anyway after uninstalling powernap everything became normal.
About the CPU cores going off, i don't have much information, but it's still hapening without causing any problem. Ad in some forums they say that it is an option of the Intel corei3 CPU.

THANKS!! Jonathan

---

