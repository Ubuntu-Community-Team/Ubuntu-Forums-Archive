---
title: "Crappy Cedega Performance"
date: 2005-04-09
forum: Gaming &amp; Leisure
---

### Post by Muchacho_Gasolino on 2005-04-09
Im getting kind of frustrated with not being able to play WoW at my desktop resolution(1280x1024) in Hoary 64 because of the constant sub-20 frames at low settings.
In my old FC3(64 bit), I could do it fine, I was getting 30-40 reliably outside with pretty high settings
So what happened?
I had to do [this](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#UPDATED_AMD64_pure64_w.2F32bit_libs_and_NO_32bit_chroot)
first to get Cedega to work at all
Setting NvAGP to 2 gave me a boost of a couple fps
one thing is I can't seem to get FastWrites enabled for my card. It supports it, but cat /proc/driver/nvidia/agp/status gives me
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

I read [this](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Optimizing_Nvidia_3D_driver) tutorial for enabling them, and this is the end of my bootmisc.sh
#
#	Remove ".clean" files.
#
rm -f /tmp/.clean /var/run/.clean /var/lock/.clean

modprobe nvidia NVreg_EnableAGPFW=1

: exit 0

modprobe nvidia NVreg_EnableAGPFW=1

but nothing happened, I still get the same thing for cat /proc.../status
i put the line twice because I wasn't sure whether it went before or after the exit line
last week the cat /proc../status actually changed and said fastwrites was enabled but I didn't believe it because it made no game difference, and sure enough it went away after a few days
I posted this on the Cedega forums but no one seemed to know what to do
anybody have any suggestions?

---

### Post by subterrific on 2005-04-09
have you tried adding this line to the top of /etc/modutils/nvidia-kernel-nkc ?
options nvidia NVreg_EnableAGPSBA=1 NVreg_EnableAGPFW=1 NVreg_ReqAGPRate=8

I'm just taking a guess, not sure if this is the right way or if it even works.

---

### Post by Muchacho_Gasolino on 2005-04-09
hmm thats interesting but it didn't seem to do anything
maybe i am not reloading the module right, i just control-alt-backspaced
i will see next time i reboot

---

### Post by fackamato on 2005-04-09
Is your cedega configured right? (the vmem sizes, aperture size etc..)

---

### Post by Muchacho_Gasolino on 2005-04-10
my video ram and agp memory settings are correct
another thing i should note is that fedora and ubuntu on my computer have gotten very similar glxgears rates
there is a difference, but not nearly as much as in-game frames
in fedora glxgears averaged 2900-3000, ubuntu it is more like 2800-2900

---

### Post by Giawa on 2005-04-10
I haven't done anything yet except set my vram settings in Cedega, and I too am getting around 15 fps in WoW. I'd be happy to hear some tips on how to increase fps as well.  :-P

---

### Post by Muchacho_Gasolino on 2005-04-11
hey giawa are you using SATA drives by chance?

---

### Post by Giawa on 2005-04-12
No, I'm using two ATA hard drives. I have a tip for you though =D On Hoary world of warcraft seems to get much higher frame rates when windowed, which is odd. Anyways, I've set WoW to run windowed at the widescreen resolution (1280x960 i think.... something around those lines) and then the task bar and menu don't get in the way of my spells and interface. I got a jump from around 15 fps up to 30 fps, which is awesome. Perhaps you'll notice a bump too if you try this?

Good luck

Edit: By the way, 15 fps might just be the top your computer can dish out in Hoary. I'm getting some more fps than you, except I'm getting around 5000 fps in glxgears. I'm not sure how much of a benchmark glxgears is though, so... What kind of system are you running? Here's my specs (heh, not so great :-?) so you can compare and see if your system should be doing better.

AMD XP 2400+ (2ghz)
768MB DDR2700 ram
60GB Seagate (Linux) and 160GB WD (storage and WoW)
Nvidia GeForce fx5600 ultra
AC'97 onboard audio

---

### Post by Muchacho_Gasolino on 2005-04-12
AMD64 3200+
1.5gb pc3200
80gb Seagate SATA, 120gb Seagate SATA
Nvidia FX5700 256mb

i dont know why my glxgears is so low
it was on fedora too, cept i was getting way better WoW framerates
thats a nice tip with the windowed thing, ill try that later when i have some time

---

### Post by fackamato on 2005-04-12
[QUOTE=Muchacho_Gasolino]AMD64 3200+
1.5gb pc3200
80gb Seagate SATA, 120gb Seagate SATA
Nvidia FX5700 256mb

i dont know why my glxgears is so low
it was on fedora too, cept i was getting way better WoW framerates
thats a nice tip with the windowed thing, ill try that later when i have some time[/QUOTE]

Are you using 32bit ubuntu? I suggest you do.

Also try to change "nvagp" (in xorg.conf) from 2 to 1, and from 1 to 2 (reboot x between) and check the glxgears fps. (this changes the agp driver)

---

### Post by Giawa on 2005-04-12
fackamato, I've seen this kind of post before, switching from 1 to 2 and checking framerates. I checked my xorg.conf files (etc/x11) and I can't find any reference to NVagp... Can you let me know where to find this? Also, does anyone know a sure fire way to enable fast write on the nvidia cards? I tried one method that didn't work, it was something like nmod or something, but ya, it had no effect :???: 

Good luck with the windowing to the OP, hopefully it yields some better frame rates.

---

### Post by Muchacho_Gasolino on 2005-04-12
you have to put nvagp in yourself

From my xorg.conf
```
Section "Device"
	Identifier	"NVIDIA Corporation NV36 [GeForce FX 5700]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "RenderAccel"           "true"
	Option          "NvAGP"                 "2"
```

I am using 64. 32-bit kind of sounds like a good idea, with flash etc. as well. Would i see a performance hit in normal operation though?
I will try that 1-2 switching

Unfortunately the windowed mode didn't seem to do much for me, I think I actually lost one or two fps. I just upgraded to Cedega 4.3.1(came out today) and if I'm remembering things correctly I got a huge fps increase inside orgrimmar, at least in places that aren't near the auction house, but outside it didn't seem to make much difference. I cut down draw distances also but that didnt change things much.

---

### Post by crane on 2005-04-12
One other thing you may want to check.
When installing nvidia drivers, nvidia suggests that you comment out or remove the GLCore and the DRI modules.

When I installed nvidia drivers using apt and then tried to play a 3d game it was reall laggy and had low fps.
After inspecting the xorg.conf I found that "load dri was still there. Once I removed it everything ran smooth.

Just a thought, hope it helps.!!

Good Luck :smile:

---

### Post by Muchacho_Gasolino on 2005-04-13
ah no glcore and dri are both gone
thanks though

fackamato- I carried out your suggestion, but performance with NvAGP 1 was much worse. It gave me hope at first because i tried glxgears with it set to 1 and got 3400 when i usually get 2900 with it 2, but then i discovered that was because the terminal window was covering up half of the glxgears window. When i changed that, fps went down to 2100. I also tried in-game, and they were about half that of when it was set to 2.

---

### Post by Dracontopes on 2005-04-15
Maybe this helps?

**Issue:**
I have only 15-30 fps

**Solution:**
renice 17 -p `pgrep wineserver`

([http://www.linux-gamers.net/modules/wfsection/article.php?articleid=32](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=32))

---

