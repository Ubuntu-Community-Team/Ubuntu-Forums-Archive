---
title: "Screen Resolution Issue"
date: 2011-07-10
forum: Desktop Environments
---

### Post by eee101 on 2011-07-10
I have an issue displaying the correct resolution on my laptop screen.  The "Experimental 3D support for NVIDIA cards" driver is activated and currently in use.  My screen is a 16:9 WXGA but the right-hand margin is black and not showing due to the current Monitor settings being a 4:3.  When I change them to the appropriate setting, it stays in 4:3 and the resolution is too large to view anything correctly.  

Also, Unity was disabled after my first log-in.  Maybe due to my graphics card since it is older?

Specs:
Intel® Pentium 4 Mobile 2.4GHz Processor
512MB PC2100 DDR Memory
15.2" WXGA TFT Active Matrix Display
64MB GeForce4 440 Go Graphics Controller

Any help to get my screen running and Unity would be much appreciated! Thanks!!

---

### Post by tripolg on 2011-07-11
If your current distro is not automatically doing it for you, I suggest to check this

[http://ubuntuforums.org/archive/index.php/t-1726534.html](http://ubuntuforums.org/archive/index.php/t-1726534.html)

there's also a bug report when the system crashes. hope it helps ;)

---

### Post by eee101 on 2011-07-11
Hi tripolg- thank you for the response, however, my screen is not blank.  I've attached an image so you can roughly see what I'm looking at.  A screen shot wouldn't work since it shows what it thinks is a "full screen," but that right margin has no activity.

I've already updated Ubuntu and loaded the "Experimental 3D support for NVIDIA cards" to no effect.  I also tried changing resolutions under "Monitor" and none of them make it any better.

Appreciate it!

---

### Post by tripolg on 2011-07-13
do you have the same issue using other OS? If it is, then you might need further help from your OEM. Also, re Unity, does it also show using Classic and Unity2?

---

### Post by eee101 on 2011-07-13
The OEM was loaded originally with Windows XP and always fit the widescreen dimensions correctly.  I wiped out XP and did a full install of Ubuntu. 

The normal Ubuntu login does not load Unity and looks exactly like the Ubuntu Classic login.  Both types do not fit the screen. I have not tried Unity 2 yet.  If I do, will it have an effect on the display?

---

### Post by eee101 on 2011-07-15
Update-

I've removed all the newer Nvidia drivers and tried to load the 96' version, which I cannot do, because there is an error due to prior drivers.  Not sure what the conflict is caused by.

I did install Unity2D which works well.  Now if I could only get my 15.2" WXGA TFT Active Matrix Display to be @1280x854 it would be as perfect as Linux can be at any given time.  I did try some xrandr commands in the terminal, but to no avail.  Any suggestions Ubuntu community?

Thanks in advance!

---

### Post by wildmanne39 on 2011-07-15
> **eee101 said:**
> Update-

I've removed all the newer Nvidia drivers and tried to load the 96' version, which I cannot do, because there is an error due to prior drivers.  Not sure what the conflict is caused by.

I did install Unity2D which works well.  Now if I could only get my 15.2" WXGA TFT Active Matrix Display to be @1280x854 it would be as perfect as Linux can be at any given time.  I did try some xrandr commands in the terminal, but to no avail.  Any suggestions Ubuntu community?

Thanks in advance!Hi, here is a guide that might help with that.
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected)
or this one might be easier
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

Also to get the resolution correct you will need the nvidia driver working. You can run these two commands in a terminal
```
lsmod
```
```
lspci | grep VGA
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by eee101 on 2011-07-16
Wildmanne39, thanks for the second link. I did update the xorg.config,  then restarted my computer. Now I am wondering if I should have gotten the Nvidia driver that you suggested running first because it looks like I've corrupted the OS. I backed up the xorg.config, but can't reach it- no commands  work.  Nothing loads after the line "Starting TiMidity++ ALSA midi emulation..."  I suppose I should reinstall Ubuntu and start from scratch.

---

### Post by wildmanne39 on 2011-07-16
> **eee101 said:**
> Wildmanne39, thanks for the second link. I did update the xorg.config,  then restarted my computer. Now I am wondering if I should have gotten the Nvidia driver that you suggested running first because it looks like I've corrupted the OS. I backed up the xorg.config, but can't reach it- no commands  work.  Nothing loads after the line "Starting TiMidity++ ALSA midi emulation..."  I suppose I should reinstall Ubuntu and start from scratch.Hi hold down the shift key while you boot up and choose recovery, then choose root recovery with network. Run these two commands.
```
sudo rm /etc/X11/xorg.conf
```
```
 sudo dpkg-reconfigure xserver-xorg

```
Also you should install the driver first once installed you may not need to create the xorg.conf file.

---

### Post by eee101 on 2011-07-17
Thanks.  Here is the output of the two commands you wanted to see.

```
wagenaar@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
snd_ali5451            23506  2 
snd_ac97_codec        105614  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_ali5451,snd_ac97_codec
nouveau               621970  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
ttm                    65184  1 nouveau
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 nouveau
hostap_pci             53117  2 
drm                   180037  5 nouveau,ttm,drm_kms_helper
hostap                106544  1 hostap_pci
snd                    55295  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
i2c_ali15x3            12878  0 
i2c_algo_bit           13184  1 nouveau
pcmcia                 39671  0 
snd_page_alloc         14073  1 snd_pcm
lib80211               14570  2 hostap_pci,hostap
psmouse                73312  0 
i2c_ali1535            12777  0 
ali_agp                12957  1 
yenta_socket           27230  0 
ppdev                  12849  0 
lp                     13349  0 
shpchp                 32345  0 
pcmcia_rsrc            18292  1 yenta_socket
serio_raw              12990  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  18951  1 nouveau
parport_pc             32111  0 
parport                36746  3 ppdev,lp,parport_pc
firewire_ohci          31504  0 
8139too                23208  0 
pata_ali               13564  1 
firewire_core          56138  1 firewire_ohci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core
wagenaar@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)

```

---

### Post by wildmanne39 on 2011-07-17
Hi, open synaptic and type in nvidia in the search then remove any drivers in there by right clicking on them and choose remove completely, then scroll down and see if you can install the 96 driver but if it does not install, then reinstall the diver you are using now before you restart your system. Here is a screenshot.

---

### Post by ajay7174 on 2011-07-17
how to manually configure desktop resolution in Ubuntu?

---

### Post by wildmanne39 on 2011-07-17
> **ajay7174 said:**
> how to manually configure desktop resolution in Ubuntu?
Hi, you can do it with this link and please start your own thread if you need more help, with a good title describing your problem because it gets confusing try to help more then one person in a thread.
[http://grenage.com/xorg.html](http://grenage.com/xorg.html)

---

### Post by eee101 on 2011-07-24
I completely removed all the Nvidia drivers.  Then I tried to install the Nvidia 96 driver as called out in your image.  It would not let me, so I reinstalled the original drivers and restarted my computer.  Now Ubuntu boots into the terminal and says the following.

```
[    43.464091] AC'97 1 access is not valid [0xffffffff], removing mixer.
[    43.464183] ali mixer 1 creating error.
```

---

### Post by wildmanne39 on 2011-07-24
Hi, that error has to do with your sound for you speakers it should not have been effected by removing nvidia drivers.

Did you remove anything else? if not it may have just crashed for some strange reason.

---

### Post by eee101 on 2011-07-24
I only removed the Nvidia driver. I tried to install the 96 version, but it did not work, so I reinstalled the original driver and restarted and that was the message. I'm not sure why the sound card error is occuring.

---

### Post by wildmanne39 on 2011-07-24
Hi, I have no idea either it is strange, so you can not boot all the way into ubuntu right?

You can hold down the right shift key when you first turn your system on and you should get the grub menu if you do select recovery, then choose fix broken packages and see if that gets you into ubuntu after you reboot.

---

### Post by .Guest. on 2011-07-27
> **eee101 said:**
> I have an issue displaying the correct resolution on my laptop screen.  The "Experimental 3D support for NVIDIA cards" driver is activated and currently in use.  My screen is a 16:9 WXGA but the right-hand margin is black and not showing due to the current Monitor settings being a 4:3.  When I change them to the appropriate setting, it stays in 4:3 and the resolution is too large to view anything correctly.  

Also, Unity was disabled after my first log-in.  Maybe due to my graphics card since it is older?

Specs:
Intel® Pentium 4 Mobile 2.4GHz Processor
512MB PC2100 DDR Memory
15.2" WXGA TFT Active Matrix Display
64MB GeForce4 440 Go Graphics Controller

Any help to get my screen running and Unity would be much appreciated! Thanks!!
eee101,

Similar resolution issue and solution-
Login screen resolution different from desktop screen resolution.  

Distribution-
Ubuntu 10.04 'Lucid'.
Gnome desktop, gdm.

Problem- 
Login screen resolution - 1152x864 (4:3). 
Desktop screen resolution - 1024x768 (4:3).
Wanted login screen resolution - 1024x768 (4:3).

Solutions-
1.
At terminal,

```
xrandr
```

to print available system resolutions. Select the 
resolution that is wanted for the system.

At terminal,

```
sudo gedit /etc/gdm/Init/Default
```

Look for the lines:

```
PATH=/usr/bin:$PATH
OLD_IFS=$IFS
```

Immediately following those lines add in:

```
xrandr --output default --mode <wanted resolution>×<wanted resolution>
```

Where &#8220;default&#8221; is the name of the screen output to configure and <your wanted resolution>×<your wanted resolution> is the desired gdm resolution.


2.
At terminal, create a file named '/.xprofile' in the 'Home' directory,
```
touch ~/.xprofile
```

Make it executable, 
```
chmod +x ~/.xprofile
```

Print the wanted resolution configuration to the same file, 
```
echo -e '#This sets your VGA monitor as your primary monitor.\nxrandr --output VGA1 --primary\n#This sets login resolution\nxrandr --output VGA1 --mode 1024x768 --rate 60' >> ~/.xprofile
```

Where '#' is the comment line, describing the executable next line.
Where '\n' indicates a 'new line'.
Where 'xrandr --output VGA1 --primary' sets the primary monitor.
Where 'xrandr --output VGA1 --mode <wanted resolution>x<wanted resolution> sets the login scren resolution.

Restart session. 
Login screen should be set to wanted resolution.

Links-
[http://chrisjakeway.wordpress.com/2010/05/19/ubuntu-10-04-default-login-screen-gdm-resolution/](http://chrisjakeway.wordpress.com/2010/05/19/ubuntu-10-04-default-login-screen-gdm-resolution/)

[http://wiki.ubuntu.com/X/Config/Resolution](http://wiki.ubuntu.com/X/Config/Resolution)

Hope this helps.

---

### Post by eee101 on 2011-08-06
Hi .Guest.

I tried your suggestion this morning and proceed up to step 2.  After chmod +x ~/.xprofile, the terminal says access denied.  I tried it with the sudo command, but that did not work either.  Any ideas?  thanks.

---

### Post by realzippy on 2011-08-06
When following .Guest.'s howto it might be a good idea to test desired resolution before editing.You want WXGA ?

```
xrandr -s 1280x768
```

if it not works,show

```
xrandr -q
```

and attach Xorg.0.log file

---

### Post by .Guest. on 2011-08-24
> **eee101 said:**
> Hi .Guest.

I tried your suggestion this morning and proceed up to step 2.  After chmod +x ~/.xprofile, the terminal says access denied.  I tried it with the sudo command, but that did not work either.  Any ideas?  thanks.

eee101,

The procedure worked on a monitor which previously loaded the login screen with a vertical portion of the screen blank. After finding the links listed above, and running the procedure above, the login screen was fixed to the full display of the monitor. 

It may be necessary to 

```

chown <user>:<user> ~/.xprofile

```

if access to the file is denied. Then continue to set the default profile.
That is the procedure that this poster found and compiled that worked to solve a similar monitor configuration error. 

Please confirm if the fix works after changing ownership of `~/.xprofile`. If not, please post the procedure that you found and used to fix your monitor error. 

Good luck.

---

### Post by eee101 on 2011-10-13
I still cannot get my laptop resolution to work with Ubuntu.  Anyone know if it's worth trying again with 11.10?  Thanks.

---

### Post by wildmanne39 on 2011-10-13
Hi, it might be but the only way to know at this point is to try.
Thank you

---

