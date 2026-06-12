---
title: "Dual Head Question"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-01-25
Hi,
I've been trying to get a dualhead configuration with my ati X600 but it won't work..
I've attached my xorg.conf file which I edited but it didn't work. When I restarted X (ctrl-alt-return) I just got the same as with the standard xorg.conf file.
Do I have to chance something else too?
(sorry if my English isn't always correct, I do my best:) )

---

### Post by Ramses de Norre on 2006-01-27
Does anyone have an idea? (trying to get the topic on top:) )

---

### Post by Ocxic on 2006-01-27
you have 2 Server layout sections, that would prolly conflict with each other no? try this xorg.conf

---

### Post by Ramses de Norre on 2006-01-28
I tried the conf file but te second monitor wont work, and the first gives a lot of coloured lines in the image. What could be wrong?
I also tried to use the fireglcontrolpanel command and change it there but it wont save my changes..

---

### Post by Ocxic on 2006-01-29
make your 2 device section look like this:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X600 (RV370)"
	Driver		"fglrx"
	Screen 		0
	Option		"MonitorLayout" "CRT,CRT"
	Option 	        "SWcursor" "true"
	BusId		"PCI:3:0:0"
EndSection

Section "Device"
        Identifier      "ATI2 Technologies, Inc. Radeon X600 (RV370)"
        Driver          "fglrx"
	Screen		1
	Option 	        "SWcursor" "true"
        BusId           "PCI:3:0:0"
EndSection

```

tell me if that works

---

### Post by Ramses de Norre on 2006-01-30
I've tried the conf file with your changes, but X wasn't able to start anymore..
The Xorglog.txt is the log after it crashed with that conf file.
I also tried it when I changed the BUSID to "PCI:1:0:0" again, because that's where lspci says my graphics card is. Then I got my primary screen working but with a lot of coloured lines on it and the second didn't give anything, I also included the log file I got with this conf, it's Xorglog2.txt
Any idea what I'm doing wrong?

---

### Post by Ramses de Norre on 2006-01-30
It seemed Xorglog2 was too big, so I cutted it in pieces, because I didn't know which lines to delete.. Hope it isn't to unclear.. Xorglog2 is the first piece, Xorglog22222 the last.
Thx for helping me already!

---

### Post by Ocxic on 2006-01-31
run lspci and post the output, the log says that there is a device with pci bus id 1:0:1 with no device section. that could be the problem

---

### Post by Ramses de Norre on 2006-01-31
This is my lspci output

---

### Post by Ocxic on 2006-01-31
ok, you ahve 2 video cards in your system, are you trying to use one, with a dual output or both video cards, each with a single output. if your using both cards, then try puting 1:0:1 as the bus id for the second ATI device in the xorg.conf

---

### Post by Ramses de Norre on 2006-01-31
I have only one videocard, or could the other one be the onboard videocard? (chipset is ati too) 
I want to use my ati x600 for both screens. Now I'm running one screen from the card with busid 1:0:0. So that's certainly the ati card.
I'll try changing the other one to 1:0:1 tomorrow (I definitely need sleep now), could that just be the second connector of the same card?
I'll post more when I tried.

---

### Post by Ramses de Norre on 2006-02-01
With the bus id of the second screen at 1:0:1 my xserver starts, but my second screen stays black, and I get a lot of faults at my first screen (pieces of windows that don't disappear when minimalized etc.).
I attached my Xorg.0.log file (you should use 'save link as...' and delete the extension .zip, otherwise I would have to split it again. It's just a txt file).
Do you have an idea what's wrong?

---

### Post by Ocxic on 2006-02-01
try running this command, and reboot
```
echo fglrx | sudo tee -a /etc/modules
```

i also found this in the log file
```
(WW) fglrx(0): MonitorLayout is no longer supported. 
               Please use DesktopSetup and ForceMonitors options
```

the "Monitor layout" option you have declared will not work, you'll have to use a different option, or try getting rid of that line completely and see what happens.
also it says that there is no matching device section for instance (BUS ID 1:0:1) so I'm not quite sure how to go about fixing that.

I'm not sure how much more i can help you. tell me what that command getts you and I see what i can do.

---

### Post by Ramses de Norre on 2006-02-04
Sorry for the late reply but I've been working much lately.
Can you explain me what that command means? Because I want to understand what I'm doing so I can do it again later.
I can't find a monitor layout section in my xorg.conf, neither any option called like that. Or is it just the "monitor" section?

---

### Post by Ocxic on 2006-02-04
echo fglrx | sudo tee -a /etc/modules

this command will add the fglrx module to your kernel so you will be able to use it properly, i always had problems before i found that i had to do this.

as for the error, post an update of you xorg.conf and I'll see if i can figure it.

---

### Post by Ramses de Norre on 2006-02-04
I've added the module.
This is the xorg.conf I used the last time I tried. (when I got the latest log I posted)
thx for looking!:)

---

### Post by Ramses de Norre on 2006-02-04
I've just seen that fglrx is now two times in /etc/modules, is this what should be achieved by the command or should I delete one of them?

---

### Post by mediaservant on 2006-02-04
You mentioned that the fglrxconfig wouldn't save your changes when you run it - make sure you do a sudo fglrxconfig so it can write  to the file.

I had problems with my ati dual head config, but installing the latest ATI binary drivers and the tips in the ubuntu wiki really helped.

---

### Post by Ramses de Norre on 2006-02-09
I did the fglrxconfig as sudo and it created a new xorg.conf, but still my second screen remains blank.. I attached the xorg.conf, maybe you can do something with it?
I'd really like to get this screen up and running..

---

