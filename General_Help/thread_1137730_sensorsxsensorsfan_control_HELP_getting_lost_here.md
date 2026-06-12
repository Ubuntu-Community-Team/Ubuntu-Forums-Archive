---
title: "sensors/xsensors/fan control HELP getting lost here"
date: 2009-04-25
forum: General Help
---

### Post by smartsmokey on 2009-04-25
hi! I'm having trouble with my Thinkpad T60 - I noticed it was heated up pretty bad, so I did some searching and came across the "sensor" thing, so I ran the sudo sensor stuff and it found the integrated thermal monitoring thing on my laptop. So in terminal I can type sensors and get a readout of all kinds of info. like fan speed (says 3,300 rpm) and the temps of the two cores? (it gives me two main core/processor temps + a bunch of other ones) and these are always about 58 Celsius. 
   Now, I wanted to try and get the fan going like ALL the time to make it cool and efficient, and I tried the fancontrol thing but it won't work. I installed Xsensor, and I get this - 

smartsmokey@smartsmokey-laptop:~$ xsensors
Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.
smartsmokey@smartsmokey-laptop:~$ 

First - I have no idea WHAT the "use -c option" stuff is about. I don't know where this "lm-sensors configuration file" is. Or WHAT it is. 
  I just really want to properly access my fan controls so that I can bring that 58 Celsius down to like 40 or something.

---

### Post by smartsmokey on 2009-04-26
HELP! this is what I get for pwmconfig


smartsmokey@smartsmokey-laptop:~$ sudo /usr/sbin/pwmconfig
Password or swipe finger: 

This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is thinkpad
   hwmon1/device is coretemp
   hwmon2/device is coretemp

Found the following PWM controls:
   hwmon0/device/pwm1
hwmon0/device/pwm1_enable stuck to 2
Failed to set hwmon0/device/pwm1 to full speed
Something's wrong, check your fans!
smartsmokey@smartsmokey-laptop:~$ 


HELP!!!!!!!!!!!!!!!!!!!!!!

---

### Post by smartsmokey on 2009-04-26
smartsmokey@smartsmokey-laptop:~$ pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon0/device is thinkpad
   hwmon1/device is coretemp
   hwmon2/device is coretemp

Found the following PWM controls:
   hwmon0/device/pwm1

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon0/device/fan1_input     current speed: 3272 RPM

As you are not root, we cannot write the PWM settings.
Please run as root to continue.
smartsmokey@smartsmokey-laptop:~$ 

BUT WHEN I ADD "SUDO" BEFORE THE COMMAND I GET THE OTHER ERROR LISTED IN PREVIOUS POST

---

### Post by smartsmokey on 2009-04-26
here's what I get when i try "fancontrol" (as I type my hands are literally burning as they come into contact with the laptop)
smartsmokey@smartsmokey-laptop:~$ fancontrol
/usr/sbin/fancontrol: line 46: /var/run/fancontrol.pid: Permission denied
Loading configuration from /etc/fancontrol ...
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
Some mandatory settings missing, please check your config file!
smartsmokey@smartsmokey-laptop:~$

---

### Post by lovinglinux on 2009-04-26
Correct me if I'm wrong. After using the command for the first time, you weren't able to turn the fan back again and your computer is becoming even hotter? 

If this is the case, I suggest you turn of the computer and wait until some expert replies. I also suggest you remove the command from your previous posts or put a warning like DON'T DO THIS.

---

### Post by smartsmokey on 2009-04-26
no it's the same, it seems to peak for no reason. I don't know. This is a nightmare.

---

### Post by lovinglinux on 2009-04-26
> **smartsmokey said:**
> no it's the same, it seems to peak for no reason. I don't know. This is a nightmare.

I found an article a little bit old and for a Debian install. Anyway, this might help you:

[http://www.kraus.tk/installnotes/T60/ThinkPad-T60.htm](http://www.kraus.tk/installnotes/T60/ThinkPad-T60.htm)

---

### Post by smartsmokey on 2009-04-26
thanks man. It mentions there's some kind of inherent nuisance with the Thinkpads...the video card gets hot. Not TOO hot, but frequently like 80% of safe temp. range. I found this and managed to get it going - 
[http://www.surban.net/mediawiki/index.php/ThinkPad_Fan_Control](http://www.surban.net/mediawiki/index.php/ThinkPad_Fan_Control)
I've got the application running fine. Sort of. The application is designed to allow users "annoyed" by their fan to change the setting so it kicks in only at really high temps. But I'm using it for the opposite - have the fan kick in at lower temps. 
  So I'm in the application but I don't understand the terms it gives me for the settings of the individual temperature gauges - one will say #5 or something, what temp it's at, and then when I click on it there's options for "15%, 30%" all the way to "100%" then stuff like "full" and then "hardware controlled." The latter seems the safest for now...but if I wanted to get the fan to kick in/have super-cooling happening, would I want the 100% option? Or the "full" option? What's the difference? Ugh.

---

### Post by lovinglinux on 2009-04-26
> **smartsmokey said:**
> thanks man. It mentions there's some kind of inherent nuisance with the Thinkpads...the video card gets hot. Not TOO hot, but frequently like 80% of safe temp. range. I found this and managed to get it going - 
[http://www.surban.net/mediawiki/index.php/ThinkPad_Fan_Control](http://www.surban.net/mediawiki/index.php/ThinkPad_Fan_Control)
I've got the application running fine. Sort of. The application is designed to allow users "annoyed" by their fan to change the setting so it kicks in only at really high temps. But I'm using it for the opposite - have the fan kick in at lower temps. 
  So I'm in the application but I don't understand the terms it gives me for the settings of the individual temperature gauges - one will say #5 or something, what temp it's at, and then when I click on it there's options for "15%, 30%" all the way to "100%" then stuff like "full" and then "hardware controlled." The latter seems the safest for now...but if I wanted to get the fan to kick in/have super-cooling happening, would I want the 100% option? Or the "full" option? What's the difference? Ugh.

I don't know. Try different settings and run an application like avidemux for example, to see when the fan kicks.

---

