---
title: "[How-To]Install Dell Tweaks on your Dell (if you didnt buy a preloaded system)."
date: 2008-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Diggs808 on 2008-08-21
I consider myself very lucky that Ubuntu on my Dell &#8220;Just Works&#8221; right out of the box.  However, there are some tweaks and additions on my system to better manage the way it runs.  Dell has made these available for all Dell Ubuntu users.  However, there is a little more involved in getting it to work than simply pointing and clicking.  The main tweak I have been able to find is flashing the system BIOS from within Linux.  However, I have found that Ubuntu doesn't do such a great job at running the fans on a Dell system.  I think that has to do more with the way the BIOS interacts with the Kernel rather than Ubuntu itself.  

 

 **Temperatures and Fan Control.  ** 
 

 I personally use _i8k_ from the repos for this because I have the ability to set the fan thresholds using a GUI tool (which my dyslexia and ADD addled brain understands better than CLI stuff any day).   
 

 
[LIST=1]
[*]Go to     System>Administration>Synaptic Package Manager
[*]Search for &#8220;i8k&#8221; (without the     parentheses of course)
[*]Click to install: i8kutils and     gkrellm-i8k
Note: there is a dependancy to install _gkrellm_     which is a system monitor for Linux.
[*]Click apply to install the     programs
[*]We now need i8k to be loaded into     the kernel so we can configure everyting without having to reboot     our system.  So type:  sudo modprobe i8k force=1
[*]Then we need to make a small edit     in our modules file to make certain that this loads every time.      Type in a terminal:  sudo gedit /etc/modules
[*]Add this line to the end of the     file:  i8k force=1
[*]Click save and close out the Gedit     window.
[/LIST]
 

 Note: Adapted from ( [http://ubuntuforums.org/showthread.php?t=396018](http://ubuntuforums.org/showthread.php?t=396018)  ) to include the GUI method of installing.
 

 **Use Gkrellm to Set default Temperatures**
  

 
[LIST=1]
[*]     Alt+F2 to open a run application dialog
[*]     type gkrellm
[*]     When gkrellm starts, press the F1 key to open the configuration     dialog for Gkrellm.
[*]     Under Plugins, click the check box to enable the Dell I8K plugin
[*]     Expand the menu to open up the settings for Dell I8K Plugin
[*]     Click on the Temps tab to set specific temperatures for your system.
[*]      Under the Built-ins expandable menu I have disabled everything     (Since I use Conky) but the Dell I8K plugin.  Click on each option     and uncheck the enable box for each sensor.
[/LIST]
  

  I use Gkrellm simply because it gives me the option to not only have a GUI to set the temperatures (I really dont like trying to do that in a command line), but it also gives me the ability to change the speed of the fans manually (great for things like games that make your system run hot).   
  

 

 The other option (and from what I can tell, it does not depend on a 32 bit kernel) is _Dellfand_
 (Going to quote here since I havent ever actually USED this method)
 

 Quoting: [http://www.ubuntu-forums.com/showthread.php?p=5381557](http://www.ubuntu-forums.com/showthread.php?p=5381557) 
 

 [I][http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)

you might need to install build-essential from the repos (just to ensure a compiler and libc etc, however, I am fairly confident everything you need to compile this is included by default). if not:

[/I]```
 sudo apt-get install make build-essential
```
 **Flashing the Bios using Dell's Software Repositories automatically.**
 

 There are a couple of different ways to achieve this.  Thankfully neither one of them require extradonary steps to achieve.  These are all taken from Dell's site and supplimented by information from Ubuntu Forums  
 

 To do this you will need to first allow your system to pull from the Universe Repository.   
 

 1.  Go to **System>Administration>Software Sources .  **On the Ubuntu Software tab click on the option that says &#8220;Community-Maintained open source software (Universe)&#8221;
 

 2.  Open a terminal and run the following commands:   [FONT=monospace]

[/FONT]```
sudo wget -q -O - [http://linux.dell.com/repo/firmware/bootstrap.cgi](http://linux.dell.com/repo/firmware/bootstrap.cgi) | bash  

sudo apt-get install firmware-tools

sudo aptitude install firmware-addon-dell  

sudo aptitude install $(bootstrap_firmware -a) 

sudo update_firmware 
```[FONT=Times New Roman, serif][SIZE=3]

3. The system will need to reboot to flash the bios.  Once that is done you have successfully flashed your bios on your Dell.[/SIZE][/FONT]  [FONT=Times New Roman, serif][SIZE=3]_If you would like your system to automatically update your firmware:_[/SIZE][/FONT] [FONT=Times New Roman, serif][SIZE=3]In a terminal type:[/SIZE][/FONT] [FONT=Times New Roman, serif][SIZE=3]perl -p -i -e 's/^#rpm_mode=.*/rpm_mode=auto/' /etc/firmware/firmware.conf[/SIZE][/FONT] 

**[FONT=Times New Roman, serif][SIZE=3]Flashing your Bios Manually[/SIZE][/FONT]** [FONT=Times New Roman, serif][SIZE=3]This seems to be a cleaner (IMHO) way to flash the bios on a Dell system.  [/SIZE][/FONT] 
[LIST=1]
[*][FONT=Times New Roman, serif][SIZE=3]Install     from Synaptic:  libsmsbios-bin[/SIZE][/FONT]
[*][FONT=Times New Roman, serif][SIZE=3]In     Terminal type: [/SIZE][/FONT]```
sudo getSystemId 
```
[*][FONT=Times New Roman, serif][SIZE=3]Make     a note of your System ID It should look similar to (0x01BD)[/SIZE][/FONT]
[*][FONT=Times New Roman, serif][SIZE=3]Go     to [http://linux.dell.com/repo/software/bios-hdrs/](http://linux.dell.com/repo/software/bios-hdrs/)     and download bios.hdr from the matching folder.  [/SIZE][/FONT]
[*][FONT=Times New Roman, serif][SIZE=3]In     terminal type: [/SIZE][/FONT]```
sudo modprobe dell_rbu
```
[*][FONT=Times New Roman, serif][SIZE=3]In     terminal, navigate to the folder that you saved the bios.hdr file     to.  If you saved the file to your home folder you do not need to     navigate to the folder.  [/SIZE][/FONT]
[*][FONT=Times New Roman, serif][SIZE=3]In     terminal type: [/SIZE][/FONT]```
 sudo dellBiosUpdate -u -f ./bios.hdr
```
[*][FONT=Times New Roman, serif][SIZE=3]This     will install the bios.hdr file [/SIZE][/FONT]
[*][FONT=Times New Roman, serif][SIZE=3]Reboot.      During the reboot the screen will flash white, flash the bios and     then continue to boot up.  [/SIZE][/FONT]
[/LIST]
 [FONT=Times New Roman, serif][SIZE=3]Bios information adapted from: [http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)[/SIZE][/FONT]
 
All you Dell users (who did NOT buy a system with Ubuntu Pre-loaded) out there,  I know that this is just a start.  I want to make this as comprehensive as possible.  If I missed something or there is a tweak for your Dell (specifically for a Dell) please PM me / comment  with some instructions or a location I can get information from and I will add it here.

---

### Post by anjilslaire on 2008-08-21
Just for clarity, recommend you use [ code ]  [ / code ] tags to point out the commands like so:

```

sudo modprobe i8k force=1

```

```

sudo wget -q -O - http://linux.dell.com/repo/firmware/bootstrap.cgi | bash

sudo aptitude install firmware-addon-dell sudo aptitude install $(bootstrap_firmware -a)

sudo update_firmware

```
```

perl -p -i -e 's/^#rpm_mode=.*/rpm_mode=auto/' /etc/firmware/firmware.conf 
```

```

sudo getSystemId 
sudo modprobe dell_rbu
sudo dellBiosUpdate -u -f ./bios.hdr

```

Good stuff though. I'll definitely try it on my 1420

---

### Post by StefAndrew on 2008-08-21
Looks good.  Will have to try this out when I get home on my Vostro 1500.  Thanks for the How-To!

---

### Post by Yink on 2008-08-25
I run the commands fine but when I try running the final comman
```
yas@ladybird:~$ sudo update_firmware
sudo: update_firmware: command not found
```

any idea where I'm going wrong ?

---

### Post by Diggs808 on 2008-08-26
> **Yink said:**
> I run the commands fine but when I try running the final comman
```
yas@ladybird:~$ sudo update_firmware
sudo: update_firmware: command not found
```any idea where I'm going wrong ?

Sorry for the late reply....Long work days right now :-)

Anyhow...

Did you install Firmware-addon-dell ?  That is what that command calls on to run. 


[FONT=Times New Roman, serif][SIZE=3][/SIZE][/FONT]

---

### Post by RedRat on 2008-08-27
Diggs808
Thanks for your good documentation, but a word of caution and advice and minor picking of nits. When you tell someone "type Gkrellm", they will get an error. Linux is case sensitive and the correct command is "gkrellm".

Keep in mind that there are many newbies here from the Windows world where case sensitivity does not really exist.

---

### Post by Diggs808 on 2008-08-27
Thanks RedRat.....

I have corrected the nit....

Sorry...its my first raygun, err um Ubuntu how to.......

:-)

---

### Post by Yink on 2008-08-27
Hello Diggs808

Thanks, I did manage to get it working but I had to type the following command first

```
sudo apt-get install firmware-tools
```

then 

```
sudo aptitude install firmware-addon-dell sudo aptitude install $(bootstrap_firmware -a)

sudo update_firmware
```

And then it did the business. Thank you.

---

### Post by antiOST on 2008-08-28
Hi

Great post already been playing around with my fans :-)

I ran into problem with the bios part though, whether I try automatic or manually

```
sudo apt-get install firmware-tools
```
or
```
sudo apt-get install libsmsbios-bin
```

I get "E: Couldn't find package" same thing through Synaptic.

Did I miss something? and Yeah I have enabled universe repositories...

- Kim - running Gutsy

---

### Post by Nizarus on 2008-09-05
This how-to is not valid for amd64 :( there is not a i8k packages

---

### Post by say2sky on 2008-09-05
To: Diggs808

very useful How-To and I have flashed the bios by manually update. 

I hope to ask if it is possible to set the bios setting from command line. I have searched for it but not found so I hope to get this info from Diggs808.

---

### Post by medic8ted on 2008-09-06
What are the advantages of updating the BIOS?  And will this work on Dell desktops as well as laptops?

Desktop Optiplex SX280 40G HD 512 MB RAM P4 3.2G Ubuntu only
Laptop Latitude d510 30G HD 1G RAM P3 1.4G Dual Boot WinXP
Hardy 8.04.1 on both

---

### Post by Diggs808 on 2008-09-06
unfortunately I haven't come across a way to do this from the command line, if you do please pass it on and I will update the how-to.

---

### Post by Diggs808 on 2008-09-06
> **medic8ted said:**
> What are the advantages of updating the BIOS?  And will this work on Dell desktops as well as laptops?

Desktop Optiplex SX280 40G HD 512 MB RAM P4 3.2G Ubuntu only
Laptop Latitude d510 30G HD 1G RAM P3 1.4G Dual Boot WinXP
Hardy 8.04.1 on both
 

It should work on all dell systems since the Dell Bios is pretty ubiquitous on Dell Systems.  

The advantage to updating the bios is to take advantage of fixes to firmware components from dell.  For instance, some people using certain Nvidia cards ran into an overheating problem that Dell provided a work-around to by kicking on the fans earlier in the boot process (if my tired brain is working correctly).  There are also updates to the firmware and tweaks that dell provides in the bios update.  Also, updating the bios allows the computer to use new hardware devices or fix bugs in the post behavior of systems.  I recommend reading [http://computer.howstuffworks.com/bios1.htm](http://computer.howstuffworks.com/bios1.htm) for more information about what Bios does.

---

### Post by Ken4000 on 2008-09-12
Hi there
I just follow the steps and it worked out of the box on my Inspiron 8600 (1,7GHz Centrino, ATi Radeon Mobility 9600 Turbo Pro)! Very good How-To.

I just have some questions I hope someone can answer.
What is the left fan for and what is the right fan for. I know it's for the CPU and GPU, but which one is for the left and right? 

What's the settings for the low and high temperature?

Best regards
Kenneth

---

### Post by Ken4000 on 2008-09-12
Hi again
I have now tested my system:
		Temp min	Temp max	Temp normal
Left fan (CPU)	41 C		60 C		51 C
Right fan (THM)	42 C		61 C		52 C

The "Temp min" is when the fans are running at high speed for 10 minutes without touching the computer. The "Temp max" is when the CPU is using 100% running fgl_glxgears for 10 minutes. The "Temp normal" is when I use firefox, download the new ati driver and writing my settings in a txt file :) So I have setup the low temp 53 C and high for55 and 60 C. It's working fine :D

Best regards
Kenneth

---

### Post by molvistan on 2008-09-25
i tried tweaking my dell vostro 1510 like u said, but it freezes as soon as i click the dell plugin

> 4  Under Plugins, click the check box to enable the Dell I8K plugin

i have to reboot the machine, and tried a few times but same problem. any ideas?

---

### Post by Diggs808 on 2008-09-28
> **molvistan said:**
> i tried tweaking my dell vostro 1510 like u said, but it freezes as soon as i click the dell plugin



i have to reboot the machine, and tried a few times but same problem. any ideas?

The Dell i8k may not work on your vostro.  It may have something to do with the motherboard or the other possibility is that you have a 64 bit processor.  

What kind of processor do you have on your system?

---

### Post by molvistan on 2008-09-28
i have a 32 bit processor. Btw, if it doesnt support my system then is it possible to find more plugins?

---

### Post by Fr33d0m on 2008-10-31
Fails on my XPS M1330:

 sudo wget -q -O - [http://linux.dell.com/repo/firmware/bootstrap.cgi](http://linux.dell.com/repo/firmware/bootstrap.cgi) | bash
bash: line 230: /etc/apt/sources.list.d/dell-software-temp-bootstrap.list: Permission denied
Downloading GPG key: [http://linux.dell.com/repo/GPG-KEY-libsmbios](http://linux.dell.com/repo/GPG-KEY-libsmbios)
    Importing key.
gpg: no writable keyring found: eof
gpg: error reading `GPG-KEY': general error
gpg: import from `GPG-KEY' failed: general error
GPG-KEY import failed.
   Either there was a problem downloading the key,
   or you do not have sufficient permissions to import the key.

---

### Post by Diggs808 on 2008-11-02
> **Fr33d0m said:**
> Fails on my XPS M1330:

 sudo wget -q -O - [http://linux.dell.com/repo/firmware/bootstrap.cgi](http://linux.dell.com/repo/firmware/bootstrap.cgi) | bash
bash: line 230: /etc/apt/sources.list.d/dell-software-temp-bootstrap.list: Permission denied
Downloading GPG key: [http://linux.dell.com/repo/GPG-KEY-libsmbios](http://linux.dell.com/repo/GPG-KEY-libsmbios)
    Importing key.
gpg: no writable keyring found: eof
gpg: error reading `GPG-KEY': general error
gpg: import from `GPG-KEY' failed: general error
GPG-KEY import failed.
   Either there was a problem downloading the key,
   or you do not have sufficient permissions to import the key.

It looks like you do not have sufficient permissions to install the key.  Try running this from a root terminal.

---

### Post by michael37 on 2009-12-19
I see several problems with this guide.  Dell Linux site has been changed so the firmware suggestions don't work.

i8k doesn't work as suggested on 64-bit systems. gkrellm-i8k does not exist for 64-bit.

---

### Post by cybrsaylr on 2009-12-24
> **michael37 said:**
> I see several problems with this guide.  Dell Linux site has been changed so the firmware suggestions don't work.

i8k doesn't work as suggested on 64-bit systems. gkrellm-i8k does not exist for 64-bit.

Thanks for the clarification.
I was wondering about that since I have a 64 bit system.

---

### Post by michael37 on 2009-12-24
> **cybrsaylr said:**
> Thanks for the clarification.
I was wondering about that since I have a 64 bit system.

I got the i8k stuff to work on 64-bit system [thread=1132923]here[/thread].

---

