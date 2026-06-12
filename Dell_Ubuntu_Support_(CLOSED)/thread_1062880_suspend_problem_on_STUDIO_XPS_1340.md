---
title: "suspend problem on STUDIO XPS 1340"
date: 2009-02-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by venkyms on 2009-02-07
Hi Friends,

Today i installed Ubuntu 8.10(32bit) on my new STUDIO XPS 1340 laptop, looks nice, but have problem with suspend mode. when i try to wake up my machine from suspend mode, it doesnt wakes up... instead gives beep... beep.... beep... beeep.. and no response. can some one suggest on this problem, will be helpfull.


my laptop configuration is 
core 2 duo P9500 2.53 Ghz, 4 GB RAM(detects only 2.2 on ubuntu!!!), NVIDIA 9500M GE(Hybrid SLI technology), 320 GB 7200 RMP SATA HDD,

Thanks
Venkat

---

### Post by CuraHack on 2009-02-08
> **venkyms said:**
> Hi Friends,


my laptop configuration is 
core 2 duo P9500 2.53 Ghz, 4 GB RAM(detects only 2.2 on ubuntu!!!), NVIDIA 9500M GE(Hybrid SLI technology), 320 GB 7200 RMP SATA HDD,


Venkat

2.2 GB ram instead of 4 GB: Becouse you are using a 32 bits OS, I recommend you to use the 64 bits version of Ubuntu on that laptop;)

---

### Post by venkyms on 2009-02-08
Thanks for the reply, i got problem with the 64bit ISO so tried with 32bit, will try it and let know,

Note : have dual boot with vista

---

### Post by superm1 on 2009-02-08
For starters you'll have to install the nvidia closed driver to get suspend support.  Once you do, since you have hybrid graphics, you'll probably have to use this quirk too:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.10/Issues/No_Hybrid_graphics](http://linux.dell.com/wiki/index.php/Ubuntu_8.10/Issues/No_Hybrid_graphics)

---

### Post by djvishnu on 2009-02-09
I have a fresh intrepid install, with nvidia drivers enabled (180), and suspend does not work.

---

### Post by superm1 on 2009-02-09
> **djvishnu said:**
> I have a fresh intrepid install, with nvidia drivers enabled (180), and suspend does not work.
Is this consistent?  Are you sure it's not just taking 17-20second for resume?  There is another bug opened about that...

If it's consistent, can you provide some more information, dmesg, lspci, and lsusb?

---

### Post by djvishnu on 2009-02-09
> **superm1 said:**
> Is this consistent?  Are you sure it's not just taking 17-20second for resume?  There is another bug opened about that...

If it's consistent, can you provide some more information, dmesg, lspci, and lsusb?

I am 102% sure my system crashed the last two times i suspended, however, the problem seems to have fixed itself. Probably just a cry for attention.

Anyway, thank you for the gpu tip!

---

### Post by venkyms on 2009-02-13
dude,
i am facing the suspend problem still even after runing the python file from the link, The exact result when i wake up the machine is

Keyboard lights are on... screen is black

beep.... beep... beep... beep... 

can you figure it out?
and i tried downloading latest NVIDIA driver and installed and in between of installation something went wrong and restared in command mode... my xwindow didnt start
finally reinstalled 64 bit version.. still facing same suspend problem

laptop without a suspend mode... it sucks man

venkat

---

### Post by djvishnu on 2009-02-13
Actually, the python script did not work for me either, it did  not write anything to xorg.conf. However, it's quite easy to fix manually. I installed the drivers as usual, then edited the device section in xorg.conf to look like: 

```
Section "Device"
	Identifier	"Default Device"
	Busid 	"PCI:3:0:0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

I got the Busid from lspci
```
joern@xps:~> lspci | grep VGA 
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9400M G (rev b1)
```

:) hope this helps, I've had no problems suspending and waking up after installing the proper driver.

(note: not that i think it matters, but i use the nvidia-glx-180 driver, not 177. 180 is in ubutnu's proposed repository)

---

### Post by superm1 on 2009-02-13
> **venkyms said:**
> dude,
i am facing the suspend problem still even after runing the python file from the link, The exact result when i wake up the machine is

Keyboard lights are on... screen is black

beep.... beep... beep... beep... 

can you figure it out?
and i tried downloading latest NVIDIA driver and installed and in between of installation something went wrong and restared in command mode... my xwindow didnt start
finally reinstalled 64 bit version.. still facing same suspend problem

laptop without a suspend mode... it sucks man

venkat
suspend **only** works when the NVIDIA driver is installed.  don't expect it to otherwise.

---

### Post by venkyms on 2009-02-18
Hey dudes...

Finally i resolved the problem, i couldnt reply as i was traveling
thanks guys

regards
venkat

---

### Post by aniketvb on 2009-02-18
Could you post how you solved it!!

---

### Post by venkyms on 2009-02-19
Hi Aniketvb,

After installation of ubuntu, try to get the updates using following command in your terminal

sudo apt-get update

then goto Synaptic Package Manager and search for NVIDIA driver build 180 and install.
For more help [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Then perform following command in the terminal

lspci | grep VGA

this lists all PCI in your laptop and displays the list maching VGA

02:00.0 VGA compatible controller: nVidia Corporation GeForce 9200M GS (rev a1)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 9400M G (rev b1)

Then open your xorg.conf from /etc/X11/

Edit using gedit or vi editor(with super user permission)

And modify the device column as follows

Section "Device"
	Identifier	"Default Device"
	Busid 	"PCI:3:0:0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


Then restart your machine, everything should be fine.

Regards
venkat

---

### Post by djvishnu on 2009-02-19
Actually, do **not** install the 180 nvidia driver if you're using ubuntu 8.10. Use the 177 build.

I've had problems with 180, it does not work properly with 8.10 ref: [http://ubuntuforums.org/showthread.php?p=6760526#post6760526](http://ubuntuforums.org/showthread.php?p=6760526#post6760526)

---

### Post by venkyms on 2009-02-19
hey thankyou for the info, will downgrade to 170 if any problems

regards
venkat

---

### Post by unix-vocab_trainwreck on 2009-02-19
> **superm1 said:**
> suspend **only** works when the NVIDIA driver is installed.  don't expect it to otherwise.

I'm using a Toshiba Satelite with the same problems described, only mine uses an ATI video card. you mentioned an Nvidia Driver. does this mean laptops with ATI card use a completely different method?

---

### Post by superm1 on 2009-02-19
> **unix-vocab_trainwreck said:**
> I'm using a Toshiba Satelite with the same problems described, only mine uses an ATI video card. you mentioned an Nvidia Driver. does this mean laptops with ATI card use a completely different method?
The note that I put about the nvidia driver, this is highly specific to the Studio XPS 1340.  There are tons of laptops that work fine without the binary drivers, this just doesn't happen to be one of them.  Can't comment at all on your Toshiba.  You'll want to check with people that regularly work on them and/or support them.

---

