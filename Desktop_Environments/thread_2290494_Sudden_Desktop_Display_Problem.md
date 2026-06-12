---
title: "Sudden Desktop Display Problem"
date: 2015-08-12
forum: Desktop Environments
---

### Post by Geoff_Lane on 2015-08-12
Ubunto 12.04 LTS

Folks,

I have been running 12.04 for some time not with hardly any issues.

A couple of weeks back I unknowingly created a large file which reduced by disk space to virtually zero, system wouldn't start.

Eventually I found the problem and using a different Ubuntu system accessed my 12.04, deleted the file, got my disk space back and it burst back into life, relief.

But I've lost my wobbly windows.

Previously I had proprietary drivers working (ATI Radeon) but if I run jocket-gtk I get 'No Proprietary drivers is use on this system

I installed Catalyst Control Centre and it says 'No AMD graphic driver is installed or it is not functioning, so tried aticonfig and I get 'No Supported adapters detected'.

I have a functioning 14.04 system but to date 12.04 has been my main usable system which I'd like to keep.

Any clues appreciated folks?

Geffers

---

### Post by CantankRus on 2015-08-12
Hi Geoff,

Install **inxi** (small system information script).
```
sudo apt-get install inxi
```

Post the output of the terminal command
```
inxi -b 
```

***May not be in 12.04 repos.
If not, you can install by adding the unit193/inxi repo
```
sudo apt-add-repository ppa:unit193/inxi 
sudo apt-get update
sudo apt-get install inxi
```

[SIZE=3]**or**[/SIZE] 

If you don't want to add the inxi ppa, here is a direct download link to [**_[COLOR="#B22222"]inxi_2.2.27-0ubuntu1~12.04_all.deb[/COLOR]_**]("https://launchpad.net/~unit193/+archive/ubuntu/inxi/+files/inxi_2.2.27-0ubuntu1~12.04_all.deb")

---

### Post by Geoff_Lane on 2015-08-13
> **CantankRus said:**
> Hi Geoff,

Install **inxi** (small system information script).
```
sudo apt-get install inxi
```

Post the output of the terminal command
```
inxi -b 
```



Now that's thrown some light on it.

```
CPU:       Dual core AMD Athlon X2 QL-65 (-MCP-) clocked at 1050.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV710/M92 [Mobility Radeon HD 4530/4570/545v] 
           X.Org: 1.11.3 drivers: ati (unloaded: fbdev,fglrx,vesa) FAILED: radeon Resolution: 1366x768@60.0hz 
           GLX Renderer: N/A GLX Version: N/A


```

Shows the Xorg driver seems to have failed.

Geoff

---

### Post by Geoff_Lane on 2015-08-14
> **CantankRus said:**
> Hi Geoff,

Install **inxi** (small system information script).
```
sudo apt-get install inxi
```

Post the output of the terminal command
```
inxi -b 
```



On your advice installing inxi I got the error 'X.Org: 1.11.3 drivers: ati (unloaded: fbdev,fglrx,vesa) FAILED'

Did a Google search and followed instructions from the following site;
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

under the Removing Catalyst/fglrx section.

Now all working.

Thanks for pointer CantankRus

Geffers

---

