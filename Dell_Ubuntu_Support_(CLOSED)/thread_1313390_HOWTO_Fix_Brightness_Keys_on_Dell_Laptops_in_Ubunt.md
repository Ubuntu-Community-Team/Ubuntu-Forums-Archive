---
title: "HOWTO: Fix Brightness Keys on Dell Laptops in Ubuntu 9.10 Karmic Koala"
date: 2009-11-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chenxiaolong on 2009-11-03
I figured out how to fix the problem with the brightness keys on Dell laptops (very easy solution).

Open up the Terminal. Type:

```
sudo gedit /etc/default/grub
```

to change the bootloader settings. Find the line that says:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it so it says:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic"

(that's the letter "l", not the number "1").

Save and close the file.

Then run in the terminal:

```
sudo update-grub
```

and then reboot and enjoy working brightness keys!

---

### Post by vaah on 2009-11-08
Hi, Your instruction did the trick only when I'm at the grub screen. As soon as i got into ubuntu it just doesn't work. I'm running 9.10 32 bit on dell inspiron 11z. What do you think the cause is?

---

### Post by chenxiaolong on 2009-11-08
Could you try booting with "acpi=force noapic nolapic"?

---

### Post by vaah on 2009-11-08
I did whta you told me, It still doesn't work. Does this happen to any dell machine? Im curious.

EDIT: oh btw, when I boot with nolapic, my laptop only detects the cpu as 1 core instead of 2 cores.

---

### Post by nwadams on 2009-11-08
I'm sorry if this is harsh but that is a very ugly fix, messing with grub files that are not supposed to be touched is NOT a good idea. 

ok guys. what kind of brightness issues are you having? Does it not work at all of is it adjusting the brightness by two steps.

My XPS m1330 adjusts the brightness by two steps instead of one with karmic.

---

### Post by chenxiaolong on 2009-11-08
I'm not sure why it's not working. I know for sure it works on Dell Studios and Dell XPS's. You might want to file a bug report for this.

Nwadams, editing the /etc/default/grub file is the recommended way of changing grub settings stated by the Ubuntu wiki. According to the wiki and the grub documentation, change the /boot/grub/grub.cfg "unrecommended" way to changing the settings. 

Anyway, if you want to reverse it, just backspace the lapic part from /etc/default/grub and the run "sudo update-grub".

---

### Post by nwadams on 2009-11-08
oh oops, sorry. ignore what I said then. what are the side effects of the noIacpi?

---

### Post by chenxiaolong on 2009-11-08
There shouldn't be any problems or side effects with it. Nolapic is "no local apic". Dell laptops use smbios rather this apic, but in the default linux boot, apic takes precedence over smbios, so we tell the kernel to disable apic mode.

---

### Post by free2talk.183 on 2009-11-09
I too face this problem ! I use Dell Studio 1555 , (the brightness keys + wifi/bluetooth key + eject key) All these keys work during bootup and work for sometime after desktop has loaded then they dont work ! I am using ubuntu 9.10 64 bit

Note: This problem was also there in ubuntu 9.04

---

### Post by chenxiaolong on 2009-11-09
On my Dell Studio 1555, I had to boot with "acpi=force noapic nolapic" for the brightness to work. In Ubuntu 9.04, I only had to use "noapic". For some reason, the eject button sometimes works and sometimes doesn't, so I made a launcher on the panel to run the "eject" command (and yes, the command is called 'eject').

---

### Post by vaah on 2009-11-10
so what other alternative should i try? So far I can only adjust brightness @ grub screen. As soon as i get into the os these button didn't work but does show notfication. tried the brightness slider in power management preferences, still no go.

My eject button doesn't work, i thought its only normal because my 11z doesn't have dvd-media.=D

---

### Post by zovalik on 2009-11-14
> **chenxiaolong said:**
> On my Dell Studio 1555, I had to boot with "acpi=force noapic nolapic" for the brightness to work. In Ubuntu 9.04, I only had to use "noapic". For some reason, the eject button sometimes works and sometimes doesn't, so I made a launcher on the panel to run the "eject" command (and yes, the command is called 'eject').

On my Dell Studio 1555 ''acpi=force noapic nolapic'' is good for brightness but now I have only 1 core detected... Of course I have 2 Core T4200 Intel.
With "nolapic" brightness is not working. 
Any idea?

EDIT: _**"noapic"**_ works **_great_** for me. Brightness and cores are working!

---

### Post by chenxiaolong on 2009-11-14
That's great! My Dell Studio has a Core 2 Duo T6500 and both cores are detected fine. Anyway, I'm glad it worked for you.

---

### Post by charlie_foxtrot on 2009-11-14
I have a Dell Studio 1555 with T6500 and an intel video card.


my grub.cfg now contains both "nomodeset" and "noapic" to allow for both the brightness controls to work and also the intel video.

---

### Post by fredie007 on 2009-11-21
Thanks, noapic worked for me as well.

---

### Post by mitkob on 2009-12-19
Hi,
Just to mention - for me the brightness keys started working after uninstalling compiz.

---

### Post by gibbylinks on 2009-12-19
Brightness keys have worked all the time on my laptop. System is up to date.

---

### Post by chenxiaolong on 2009-12-19
Well, the Dell 1501 does not use a SMBIOS, so the default kernel settings work with it.:)

---

### Post by vault55 on 2009-12-19
[SIZE=3]Mine do not work either and I have a new Lenovo ThinkPad T400 fresh install of Ubuntu 9.10 last night and everything is up to date.  This is my first experience with this OS. Thanks.[/SIZE]

---

### Post by mjholland on 2010-01-05
> **zovalik said:**
> On my Dell Studio 1555 ''acpi=force noapic nolapic'' is good for brightness but now I have only 1 core detected... Of course I have 2 Core T4200 Intel.
With "nolapic" brightness is not working. 
Any idea?

EDIT: _**"noapic"**_ works **_great_** for me. Brightness and cores are working!

I had this same problem, with only one core being detected. Not sure if you've solved the problem, but I found that I was able to get brightness keys working and both cores detected by only using the noapic option. The line in my /etc/default/grub file:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic"

Whops didn't see your edit sorry, that would've saved me some time lol

---

### Post by chenxiaolong on 2010-01-05
Kernel 2.6.32.2 supports the brightness settings by default without any boot options. It also supports changing the brightness using software, like the Gnome Brightness Applet. You can download and install kernel 2.6.32.2 from the Ubuntu Kernel PPA: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.2/).

---

### Post by mikewhatever on 2010-01-05
I am on a Dell mini 10, and brightness keys didn't work in Karmic, screen brightness being always at 100%. Noapic did nothing in my case, but adding 'acpi_brightness=vendor' instead worked. At least now I can reduce the brightness after startup.

---

### Post by apurbapaul0 on 2010-01-14
> **chenxiaolong said:**
> On my Dell Studio 1555, I had to boot with "acpi=force noapic nolapic" for the brightness to work. In Ubuntu 9.04, I only had to use "noapic". For some reason, the eject button sometimes works and sometimes doesn't, so I made a launcher on the panel to run the "eject" command (and yes, the command is called 'eject').
hi guys I am new in linux. so please tell me where to write the command  "acpi=force noapic nolapic" in beat detail. Please.
Thanks in advance.

---

### Post by Artif on 2010-01-16
These options does not work in Netbook Remix 9.10 on Dell Inspiron 1010 ( mini 10 ):
```
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet acpi_brightness=vendor&quot;
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet nolapic acpi_brightness=vendor&quot;
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet noapic acpi_brightness=vendor&quot;
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet nolapic noapic acpi_brightness=vendor&quot;

#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet acpi=force acpi_brightness=vendor&quot;

#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet acpi=force&quot;
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet acpi=force nolapic&quot;
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet acpi=force noapic&quot;
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet acpi=force nolapic noapic&quot;

#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet nolapic&quot;
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet noapic&quot;
#GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet nolapic noapic&quot;

```All tried - all no luck.

Splash option - it's graphics curtain for user, safely could be removed while system tunning.

Also I noticed there is no files in /sys/class/backlight
When brightness controls are OK in UNR 9.10, then you should have the files, and brightness could be adjustable via Brightness applet or at least via cli
```
sudo su
echo 7 > /sys/class/backlight/compal-laptop/brightness
exit
```where 7 could be in range 1-7.

On my Dell mini 10 there is no mentioned files. Do not know what the reason.
__________________________

I succeed with it.
There is a need to turnoff KMS ( Kernel Based Mode Setting).
You can use options:
GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet nomodeset acpi_backlight=vendor&quot;
or I use
GRUB_CMDLINE_LINUX_DEFAULT=&quot;**quiet acpi_backlight=vendor**&quot;
And brightness can be adjusted with help of gnome-power-manager.

Fn keys combinations works good in LXDE session. Suppose - in Gnome session too. As I cought from Google, for some laptops Fn keys may still not work without newer kernel.

P.S. People say this all is easier in kernel 2.6.32, but it is not stable enough in current days. My current kernel is 2.6.31-17-generic #54-Ubuntu SMP.

---

### Post by casarin on 2010-01-16
(My notebook is a Dell Studio 1555)

Thank you Artif!

As you reported, none of the previous commented configs have worked for me, but the line you posted did the trick:
  **GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_backlight=vendor"**

Booted four times, just to be sure things kept working (as the keys have previously worked without any workaround applied, but on a seemingly random basis), and everything has been fine. Sometimes, though, the keys doesn't seem to be exactly responsive, but I think this is more a notification issue.

Cheers

---

### Post by Can+~ on 2010-01-22
> **chenxiaolong said:**
> Could you try booting with "acpi=force noapic nolapic"?

That worked for me.

(Ubuntu 9.10 64-bit, Dell Studio 1555)

---

### Post by michael37 on 2010-01-28
Just wanted to throw in my two cents. I have Dell Mini 12.

There were two suggestions:

GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_backlight=vendor"

and

GRUB_CMDLINE_LINUX_DEFAULT="quiet nolapic acpi_backlight=vendor"

For me, both work.  However, the nolapic slows down my graphics performance by 20-25%.  Tested with 2D (gtkperf) and 3D (glxgears).

So, use **GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_backlight=vendor"**

---

### Post by gbanis on 2010-01-31
> **michael37 said:**
> Just wanted to throw in my two cents. I have Dell Mini 12.

There were two suggestions:

GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_backlight=vendor"

and

GRUB_CMDLINE_LINUX_DEFAULT="quiet nolapic acpi_backlight=vendor"

For me, both work.  However, the nolapic slows down my graphics performance by 20-25%.  Tested with 2D (gtkperf) and 3D (glxgears).

So, use **GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_backlight=vendor"**

Wicked!
Works for me too.
While booting i had some errors regarding USB devices but i think they are irrelevant.

Thanks:KS

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> I figured out how to fix the problem with the brightness keys on Dell laptops (very easy solution).

Open up the Terminal. Type:

```
sudo gedit /etc/default/grub
```to change the bootloader settings. Find the line that says:



and change it so it says:



(that's the letter "l", not the number "1").

Save and close the file.

Then run in the terminal:

```
sudo update-grub
```and then reboot and enjoy working brightness keys!
PLEASE HELP....... I am new to linux... after spending hours getting everything working on my n210 samsung with ubuntu 9.10 i.e wireless etc i just wanted to bump up the brightness a little and tried this post now grub is holding up will not boot into linux..  What can i do to fix this as i have everything on the computer the way i like it and do not want to start over.   Thanks in advance for all of your support..

---

### Post by chenxiaolong on 2010-03-15
beerock: When you are at the Grub Bootloader, press "e", go to the longest line, or where you put in "nolapic/noapic/acpi_backlight=vendor" and backspace that. Then press Control+X to boot. After you boot up, you can then edit /etc/default/grub again to remove the changes and run "sudo update-grub" to save the changes. 

I hope this helps.

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> beerock: When you are at the Grub Bootloader, press "e", go to the longest line, or where you put in "nolapic/noapic/acpi_backlight=vendor" and backspace that. Then press Control+X to boot. After you boot up, you can then edit /etc/default/grub again to remove the changes and run "sudo update-grub" to save the changes. 

I hope this helps.


YOU R FRIGGIN AWESOME!!!  I cant believe it was that simple to get booted up again.  but would still to know how i might fix the brightness deal as everything with 9.10 and samsung n210 works perfect.  but now i am a bit afraid .  if you would like to help when u have time I would appreciate it greatly!!

thanks again !

Bret :D

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> beerock: When you are at the Grub Bootloader, press "e", go to the longest line, or where you put in "nolapic/noapic/acpi_backlight=vendor" and backspace that. Then press Control+X to boot. After you boot up, you can then edit /etc/default/grub again to remove the changes and run "sudo update-grub" to save the changes. 

I hope this helps.


OK i must be too old r\to learn anything new...LOL i have done this and the nolapic keeps coming back and i have to press 'e' and remove then ubuntu loads right up  what am i doing wrong?   
bret

---

### Post by chenxiaolong on 2010-03-15
Press "e" to edit is a temporary fix to boot. To make this permanent, you will have to remove "nolapic" from /etc/default/grub by running:

```
gksudo gedit /etc/default/grub
```

so it should read:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

instead of:

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic"

Then you can save and exit the file and run:

```
sudo update-grub
```

to regenerate the Grub menu to reflect those changes.

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> Press "e" to edit is a temporary fix to boot. To make this permanent, you will have to remove "nolapic" from /etc/default/grub by running:

```
gksudo gedit /etc/default/grub
```so it should read:



instead of:



Then you can save and exit the file and run:

```
sudo update-grub
```to regenerate the Grub menu to reflect those changes.
yes i have done these steps... I did notiv\ce in the line under default just has "" (empty quotes should there be something in there?

---

### Post by chenxiaolong on 2010-03-15
Could you post the whole file so I can see?

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> Press "e" to edit is a temporary fix to boot. To make this permanent, you will have to remove "nolapic" from /etc/default/grub by running:

```
gksudo gedit /etc/default/grub
```so it should read:



instead of:



Then you can save and exit the file and run:

```
sudo update-grub
```to regenerate the Grub menu to reflect those changes.

i dunno, for some reason the nolapic keeps coming back at the grub boot menu...... i clear it out using 'e' and ubuntu boots right up.

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> Could you post the whole file so I can see?



i dont think i can get all of it but it just looked wierd to me ...
this is the line that you want me to edit back
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"   			 		which i have done and saved i ran the update-grub but the nolapic comes back

under the line i edited says about the same thing but has empty quotes like this:
GRUB_CMDLINE_LINUX=""  			 		i thought something was there before but probably wrong


feel free to call me which may be easier i dunno
Thanks bret

---

### Post by chenxiaolong on 2010-03-15
beerock: I just looked at my /etc/default/grub file and GRUB_CMDLINE_LINUX="" is supposed to be empty. Are you sure you ran "sudo update-grub" rather than "update-grub"? Did it give you any errors?

---

### Post by beerock on 2010-03-15
[QUOTE=chenxiaolong;8973983]beerock: I just looked at my /etc/default/grub file and GRUB_CMDLINE_LINUX="" is supposed to be empty. Are you sure you ran "sudo update-grub" rather than "update-grub"? Did it give you any errors?[/QUOTe

chenx.... jus got off work and can focus a little more on it u there?

I am going to try this again

---

### Post by chenxiaolong on 2010-03-15
beerock: Here's my complete file: (It's from Debian, so don't copy and paste it in your file. Just check for some major differences :D)

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


---

### Post by beerock on 2010-03-15
i really think i just need to reinstall grub is there anyway to easily do this without disturbing the rest of the operating systems...

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> beerock: Here's my complete file: (It's from Debian, so don't copy and paste it in your file. Just check for some major differences :D)
I will check just as soon as i get it restarted again.... Now I ran the commands that you described once again with it still hanging on normal boot I end up with a long page of text that includes at the bottom Busybox blahblah blah and then

(initamfs) [247.064559] monitor-mwait will be used to enter c-2 state

{247.064657] Marking TSC unstable due to TSC halts in idle   and a bunch of other things I do not understand above this.....LOL

Bret

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> beerock: Here's my complete file: (It's from Debian, so don't copy and paste it in your file. Just check for some major differences :D)




chenxiaolong:  not a whole lot of difference. i have another line starts with # grub_hidden timeout....
but other than that the only other real diff is my timeout is 10 yours id\s 5 but i do believe i have something wrong. lol

---

### Post by chenxiaolong on 2010-03-15
beerock: I have no idea either :D. You could try reinstalling the packages:

grub-common
grub-pc

in Synaptic and see if it works then.

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> beerock: I have no idea either :D. You could try reinstalling the packages:

grub-common
grub-pc

in Synaptic and see if it works then.



I sure appreciate your help thus far :)


Bret

---

### Post by beerock on 2010-03-15
> **chenxiaolong said:**
> beerock: I have no idea either :D. You could try reinstalling the packages:

grub-common
grub-pc

in Synaptic and see if it works then.


**:KSchenxiaolong: I dont believe it**..... Simply reinstalling these 2 packages fixed it right up.  sometimes the simplest things isn't it?  Now back to this brightness issue  got any ideas since we no the nolapic doesn't work with mine....lol

Bret:KS

---

### Post by chenxiaolong on 2010-03-16
beerock: :D:D. Brightness: The other two options besides "nolapic" are "noapic" and "acpi_backlight=vendor". I suggest you use the "press e" method to try it, knowing the experience you had with "nolapic" :D.

---

### Post by anantshri on 2010-03-19
thanks for the tips works flawlessly for me since last 5 boots.

and that too i have tested for about 3-4 hrs

and ya besides brightness it lets me work on with power status, wifi, external display key too.

---

