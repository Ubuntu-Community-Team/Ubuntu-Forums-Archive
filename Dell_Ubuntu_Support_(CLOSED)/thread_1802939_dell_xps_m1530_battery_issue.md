---
title: "dell xps m1530 battery issue"
date: 2011-07-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by woodsyboredom on 2011-07-12
HI. would love some help. 

I am having issues with my dell XPS M1530 laptop. The battery is dead. I bought a new battery. That is also now dead. When the ac power is plugged in the battery monitor says that the batter is full. If, however, I unplug the battery the computer shuts down because the battery is dead. This seems to be a common problem and I found much information about it on this forum and others. Solutions have ranged from simple (change the BIOS) to the complex (change the mother board). I don't want to get into an expensive drawn out repair with Dell because I have done that and they have the WORST customer support I have ever encountered. 

I would like to try to change the BIOS before doing anything drastic of a hardware nature. I found this lovely page, 

[http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate)

 and followed the instructions. Everything went swimmingly until the very last step (dellBiosUpdate -u -f ./bios.hdr) I kept getting and error claiming that the computer was unable to find bios.hdr. It was however sitting quite plainly on my desktop. I included the location (./home/woodsy/desktop/bios.hdr). It couldn't find that either. 

Does anyone have any ideas as to how get my computer to find this file which I can find quite easily? 

woodsy

---

### Post by ajgreeny on 2011-07-12
You have a mistake/typo in your pathway to the file you are running, **./home/woodsy/desktop/bios.hdr** but it should be **./home/woodsy/[COLOR=Red]D[/COLOR]esktop/bios.hdr**.

Don't forget linux is case sensitive, unlike windows.

Give that a try.  I have never flashed a BIOS, so can not give you any help on that, I'm afraid.

---

### Post by woodsyboredom on 2011-07-14
Thanks but capitalizing Desktop did not help. this is driving me crazy. It's right there on the desktop. It's called bios.hdr. 
this is what terminal says 

Performing BIOS update...
Traceback (most recent call last):
  File "/usr/sbin/dellBiosUpdate", line 115, in <module>
    def ensureRbuDriver():
  File "/usr/sbin/dellBiosUpdate", line 153, in main
    exit_code = updateBios(HdrFile(options.hdr), options)
  File "<libsmbios_c._peak_util_decorators.rewrap wrapping libsmbios_c.rbu_hdr.__init__ at 0x09FEFAAC>", line 3, in __init__
  File "/usr/lib/python2.7/dist-packages/libsmbios_c/trace_decorator.py", line 108, in trace
    result = func(*args, **kw)
  File "/usr/lib/python2.7/dist-packages/libsmbios_c/rbu_hdr.py", line 58, in __init__
    self.fd = open(filename, "rb")
IOError: [Errno 2] No such file or directory: './home/woodsy/Desktop/bios.hdr'

I don't under stand the file or directory bios.hdr is on my Desktop. 

arrrghh! I just want to charge my battery!

---

### Post by coreysthe1 on 2011-07-18
woodsy,
 
I have the same model at home.  My bios version I think is A12 (from memory, not at home on my pc right now).  
 
Is your laptop's OS strictly ubuntu/kubuntu or other linux?  or do you have it set to dual boot with windows on another partition?  I have never flashed my bios in an ubuntu environment.  
 
If it were me, and there was an option of doing it in windows XP/Vista/Win7, my preference would be to do the flash in windows over linux.  It's just simpler--click the downloaded bios file and follow the on screen instructions.  
 
But flashing the bios is not something to take lightly in doing.  If the flash does not work/finish or the wrong bios are flashed you can mess up the ROM Bios.  But I'm sure you've probably read all that already.  My thoughts are if its possible to do so in a windows environment, I'd rather do it that it and download the bios file from dell and click the icon.

---

### Post by woodsyboredom on 2011-08-04
I'v only got unbuntu 11.04 os no windows nothing. I just want the damned battery to charge. It will only work if plugged in. I have drained two batteries because of this. Do you or have you had this problem, coryshe?

---

