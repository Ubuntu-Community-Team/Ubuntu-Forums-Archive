---
title: "Article for setting up a swap file on Ubuntu Studio."
date: 2022-11-06
forum: Desktop Environments
---

### Post by 28su on 2022-11-06
Can you recommend me an article to properly setup swap file hibernation in ubuntu studio?

Is this a good one?
[https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html](https://www.linuxuprising.com/2021/08/how-to-enable-hibernation-on-ubuntu.html)

I don't want to break the system.

---

### Post by TheFu on 2022-11-07
Hibernation with a swap file has been a problem.  The better solution is to create a swap partition and use that instead,  but it is much more complex.  Hibernation is being deprecated, so perhaps now is the time to carefully consider if standby mode shouldn't be used instead?

Also, it would be really helpful to have some basic information about the exact release being used.
```
inxi -bz | head -2
```
will provide 2 lines of summary. Very basic stuff.  If you feel like providing more information, use 'inxi -bz'  The -z option removes any sensitive information.

'inxi' isn't installed by default, but it is a very handy system info tool to have along with lshw. It is one of the first little information tools that I install on every system. Linux Mint installs it by default.

---

### Post by oldfred on 2022-11-07
Experimented with TheFu's command. A few more lines gives model & update of UEFI/BIOS.
```

[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ inxi -bz | head -7  [/COLOR]
System: 
  Kernel: 5.15.0-52-generic x86_64 bits: 64 Desktop: KDE Plasma 5.24.6 
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish) 
Machine: 
  Type: Desktop Mobo: Gigabyte model: Z170N-Gaming 5 v: x.x 
    serial: <superuser required> UEFI: American Megatrends v: F23f 
    date: 03/09/2018 
```

And if you want documentation of your hardware.
Hardware doucumentation script, one line using && \ to make as one entry
[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && \
chmod +x system-info && \
./system-info

[/FONT]

---

### Post by TheFu on 2022-11-07
> **oldfred said:**
> Experimented with TheFu's command. A few more lines gives model & update of UEFI/BIOS.
```

[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ inxi -bz | head -7  [/COLOR]
 

Not really my command.  This is all about the inxi from an excellent team of people to whom I'm grateful.  BTW, the amount of inxi output on a line is dynamic based on the width of the terminal, so 
[code]$ inxi -bz | head -6
System:    Host: hadar Kernel: 5.4.0-131-generic x86_64 bits: 64 Desktop: FVWM 2.6.7 Distro: Ubuntu 18.04.6 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: N/A
           BIOS: American Megatrends v: 4602 date: 08/17/2021
CPU:       6 core AMD Ryzen 5 2600 Six-Core (-MT-MCP-) speed/max: 1321/3400 MHz
Graphics:  Card: NVIDIA GP108 [GeForce GT 1030]
           Display Server: x11 (X.Org 1.20.8 ) driver: nvidia Resolution: 1920x1200@59.95hz

```
or
```
$ inxi -bz | head -6
System:    Host: hadar Kernel: 5.4.0-131-generic x86_64
           bits: 64
           Desktop: FVWM 2.6.7 Distro: Ubuntu 18.04.6 LTS
Machine:   Device: desktop Mobo: ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx serial: N/A
           BIOS: American Megatrends v: 4602 date: 08/17/2021
CPU:       6 core AMD Ryzen 5 2600 Six-Core (-MT-MCP-)
```
Just depends on the terminal width   The 2nd version just had a 
```
$ resize
COLUMNS=63;
LINES=17;
export COLUMNS LINES;
```
terminal setup so wrapping was different as passed to the head command.  'head' is useful, but quite a hack. ;)

'inxi' has different options to dig deeper for most subsystems. I have a vimwiki to capture/organize useful stuff:
```
* inxi -Fxz     - Full overview w/ sensitive filtered
* inxi -Gx      - GPU+driver
* inxi -Ax      - Audio+driver
* inxi -Dx      - disks
* inxi -pl      - disk partitions/labels
* inxi -dupl    - disks labels + UUIDs + mounts
* inxi -Rx      - RAID
* inxi -Nnxz    - networking w/ extra information and sensitive data filtered 
* inxi -iz      - network IPs w/ link information and sensitive data filtered 
* inxi -I       - uptime, process, ram, shell overview
* sudo inxi -m  - detailed RAM modules
* inxi -rx      - Repos
* inxi -t cm    - Top CPU/RAM for top 5 processes
```

---

### Post by ne29914 on 2022-11-07
> **TheFu said:**
> Hibernation with a swap file has been a problem.  The better solution is to create a swap partition and use that instead,  but it is much more complex.  Hibernation is being deprecated, so perhaps now is the time to carefully consider if standby mode shouldn't be used instead?

I'd more say that Hibernation is being frowned upon by people using triple-level encryption to avoid NSA snooping (OK, hyberbole. A little joke). Unfortunately Canonical shares this opinion, so it's disabled by default.
Setting it up is not hard, but using a swapfile is problematic. A swap partition always works.

---

### Post by 28su on 2022-11-07
@TheFu


Thanks for chiming in!

[FONT=monospace]---[/FONT]
[FONT=monospace][COLOR=#000000]$ [FONT=monospace][COLOR=#000000]inxi -bz | head -7
   [/COLOR]
System: 
  Kernel: 5.15.0-52-lowlatency x86_64 bits: 64 Desktop: KDE Plasma 5.24.6 
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)[/FONT][/COLOR]
---

Kubuntu and Xubuntu installers gave me option to select Hibernation.
Why is it off by default in ubuntu studio?

[/FONT]

---

### Post by 28su on 2022-11-07
> **ne29914 said:**
> I'd more say that Hibernation is being frowned upon by people using triple-level encryption to avoid NSA snooping (OK, hyberbole. A little joke). Unfortunately Canonical shares this opinion, so it's disabled by default.
Setting it up is not hard, but using a swap file is problematic. A swap partition always works.

Is triple-level encryption compatible with a swap partition, or better not have swap for hibernation?
Hibernation is better to save energy and avoid unnecessary heating of laptop; but if it's strongly advised against, I'm fine putting the laptop to sleep (when i don't want it powered off).

---

### Post by ne29914 on 2022-11-07
The "triple-encryption" thing was a joke and marked as such, OK?
For any normal user I see no problem in using Hibernation. If you're 007/James Bond it might be one.
But then I don't use encryption myself. No need.

---

### Post by 28su on 2022-11-07
> **ne29914 said:**
> The "triple-encryption" thing was a joke and marked as such, OK?
For any normal user I see no problem in using Hibernation. If you're 007/James Bond it might be one.
But then I don't use encryption myself. No need.

Got it.
In windows waking from hibernation still prompted bitlocker key so this should be possible to setup on linux too.
I currently don't have encryption neither, but i might set it up again.

---

### Post by TheFu on 2022-11-07
> **28su said:**
> Is triple-level encryption compatible with a swap partition, or better not have swap for hibernation?
Hibernation is better to save energy and avoid unnecessary heating of laptop; but if it's strongly advised against, I'm fine putting the laptop to sleep (when i don't want it powered off).

What heating of a laptop is there in standby? It should be sipping a tiny amount of power to keep the volatile RAM powered, but not much more. Storage, networking, fans, CPU, any USB connections should be powered off.

My laptop is encrypted using LUKS.  With that, we don't really use partitions, but logical volumes instead.  I've never used hibernation, but I do use standby every night on that laptop.  The swap LV is contained inside the encrypted container along with the OS and everything except the /boot and /boot/EFI/efi partitions.  This setup is susceptible to the "evil maid" attack.  My swap LV (4.1G) isn't sized to be large enough to hibernate into because the system has 8GB of RAM. I can't trivially test it. Sorry.  Plus, it isn't running 22.04 and probably never will due to the snap package mandates. I'm not a fan of snap packages.

 ne29914 : The reasons to use encryption are many, even for normal people.  When you storage fails and you sent it in for warranty replacement, wouldn't you like to know that the vendor sees random data, not all the data?  I can appreciate that some people believe they have nothing to hide.  [https://en.wikipedia.org/wiki/Nothing_to_hide_argument](https://en.wikipedia.org/wiki/Nothing_to_hide_argument)  OTOH, just because we don't have anything to hide, that doesn't mean we want other people riffling through our files either.  If you are in a group that isn't popular or might be illegal in some parts of the world, you definitely don't want that data becoming public by any means.  Say your home country has minor laws against saying anything bad about the govt or leaders, but you are in a free country at University and take advantage of the freedom in that country?  Your home country may not appreciate that freedom and might send agents to your temporary home to hassle you for not actively confronting others from your country living in the same area.  A number of "state actors" are known to do this, so it isn't a made up situation.  Imagine that you travel to many different countries, either for work or for vacations.  Anything negative that can be attributed to you, say 65% accuracy, could get you into hot water if you have to transit through one of those countries.  My laptop storage is fully encrypted (except the /boot and EFI stuff) using a hardware device to unlock it.  If I'm traveling through certain parts of the world, I'll only boot from a microSD flash storage system and not even bring my yubikey with me.  I literally cannot unlock the internal storage and nothing can make it be unlocked.  Sadly, more and more of the normal countries we consider to have "freedom" at their core have passed laws saying that encrypted devices have to be decrypted at the border.  I'd rather lose the storage than unlock the device for any govt to take a look over. Heck, the SSD inside is worth only $50.  For a long time, I traveled with a chromebook and was never hassled at borders.

I've seen a friend and business partner have 2 devices stolen in 2 days and his wallet with cash and all credit cards which required spending about 6 hours trying to change computer credentials, cancel financial cards, and sit in a police station to get the police report for insurance.  Because he was a business partner and didn't encrypt or even lock his devices, I got to disable his account access on the server-side.  That was relatively easy - just a few minutes - compared to him trying to get replacement credit cards sometime during the remaining 3 weeks of our trip across 5 countries.   BTW, he never was able to get the replacement credit cards during the trip - seems offices weren't in any of the cities we were visiting or weren't open on weekends, so those advertisements about "we'll get you a replacement card within 24 hours" were just lies.  One company actually expected him to travel 300 miles to a different city to get a replacement card - 600 miles total.  They were unwilling to fedex overnight a replacement to the hotel we were at.  The other credit cards were even worse.  His experience taught me much about keeping cash and credit cards in multiple locations while traveling. Fortunately, I've never needed to deal with that.  Since then, we play "finger the pickpocket" every time we are in crowds and tourist locations.  The odd thing is, they are really easy to spot, when you look for them.

For me, all those possible situations means that any portable device or portable storage needs to be encrypted.  You'll need to make your own choices.  For desktops, the choices aren't nearly so clear. For servers, I've wanted to setup a redundant, network-aware, method to have encrypted storage automatically decrypted if a specific network device is seen that also contains the decryption key. Because LUKS decryption happens very early in the OS boot, this isn't really so easy.

---

### Post by ne29914 on 2022-11-07
@TheFu, I agree on all your thinking about encryption, and can understand some users needing to do this.
It just doesn't apply to my use case. Let's leave it at that.

Concerning suspend vs. hibernate: suspend will keep your (laptop on battery) storage alive for around 8...12 hours. Then it's dead. Hibernate will keep it forever.
If those hours are OK for you, fine. they're not for me, which is why I need hibernate.

That's where the choice lies for me.

---

### Post by 28su on 2022-11-08
@TheFu,

I agree. Encryption is an added layer of security. Nothing to loose having it.

What's the verdict on hibernation with ubuntu studio?
Why isn't this option available on the installer. Like it is with Kubuntu?

---

### Post by TheFu on 2022-11-08
> **28su said:**
> @TheFu,

I agree. Encryption is an added layer of security. Nothing to loose having it.

What's the verdict on hibernation with ubuntu studio?
Why isn't this option available on the installer. Like it is with Kubuntu?

You'd have to ask the Ubuntu Studio team.  If you make backups for every file (or do a system backup) before starting to follow some instructions, what's the risk in trying them?  I don't understand.  Ubuntu can boot without any swap enabled. Certainly enough to get in and put things back the way they were.
Swap is just 
a) a device - which can be an Logical Volume or partition
b) formatted as a swap - mkswap is the command - you'll need to add an option.
c) add the swap device/LV to the /etc/fstab and remove the old one.  Both can be used, if you like.  Just keep the one you want and remove/comment out the one you don't need.

That's really it.  Using the mkswap, swapon/swapoff commands (with appropriate options as clearly spelled out in the manpage for each), and I don't even think the system needs to be rebooted to migrate from swap file to swap LV/partition.

Obviuously, setting up the device is outside the scope, but that's easy too - either with lvcreate (to create a new LV) or gparted (to create a new partition).  If you want swap to be encrypted, then the partition or LV need to be inside the LUKS encryption container. Usually that's a LV setup, if you checked "use encryption" during the installation.  How you size the device to allow hibernation is slightly larger than the amount of RAM in the system.  If you have 8GB of RAM, make the swap 8.1GB.  If you have 64GB of RAM, make the swap 64.1GB.  I'm talking for the new partition/LV, not total.  the existing swap file is probably much too small.  Assume you'll delete it after the new swap device is created and formatted and added to the /etc/fstab and you've removed the old swapfile using swapoff.

It is useful to remember that in Unix, everything is a file.  That goes for swapfiles, swap logical volumes, swap partitions. We pick a specific file/device file for those and pass them into the commands.  Don't pick the wrong device or you could tell the OS to reformat everything as swap.  That would be catastrophic for any data. Only a backup would be able to retrieve it.  Don't have a bad day. Measure 10 times, enter commands and check them 10x, then press enter once.  AND have a backup of anything you cannot lose.  We all have bad days and make mistakes.  In the 1990s, I wiped my OS a few times. ;)  Then I learned how disks, partitions, device files and storage slices were named.

---

