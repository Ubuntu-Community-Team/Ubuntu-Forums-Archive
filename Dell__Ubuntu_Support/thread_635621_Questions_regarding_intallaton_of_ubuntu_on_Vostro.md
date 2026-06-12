---
title: "Questions regarding intallaton of ubuntu on Vostro 1500"
date: 2007-12-08
forum: Dell  Ubuntu Support
---

### Post by Lectos on 2007-12-08
Hi,
I want to install ubuntu for the first time in my new Dell Vostro 1500 but i have some questions regarding this stuff...

The config of my notebook is the following 
Intel core 2 duo 2.0 GHz T1250
2.0Gb RAM DDR2
NVIDIA 8600M GT 256MB
120 Gb HDD
Windows Vista home Basic

There are four partitions right now:
Partition 1: Almost 100 Gb with Vista installed on it(90 gb free, i would like to leave this partition with 25GB with vista, having around 15GB free)
Partition 2: Dell utilities (around 70mb)
Partition 3: Mediadirect (I think is installed, altought Windows shows that the space in that partition is free. This partition could go away, although I think without this the front multimedia keys wont work) (2.5GB)
Partition 4: 10GB with the recovery... I think that this one can be deleted but i would like to know if the things included in this partition are the same as the ones included in the DELL's Vista DVD

Now i have some questions:

1- Regarding partition 4, is the info contained in the partition the same as the one contained in the DELL's Vista DVD? If so what will be the best way to delete this partition?

2- Concerning the MediaDirect, without it the multimedia buttons of the front of the notebook still work?

3- What are the Dell utilities?

3- Now, I understand that i need 2 free partitions for instalin Ubuntu. The 1st one for creating an ext3 partition for Ubuntu and the 2nd other for creating secondary partitions for documents and swap and possibly a fatv. I am correct in this? What will be a good partition size of swap with my 2gb of ram?

4- I cannot get the Ubuntu AMD64 version working if it is not on safe graphics mode. And with the 32-bit compatibility with some of the programs and the things i need to instal them or get them working and considering that is my first time in linux (althought i do not have any real problem learning)... I would want to ask what is the difference between a 64-bit and using a 32-bit Ubuntu. Is it noticable? Or will i just get a hard time getting all working in the 64-bit? Which one will it be best for the beginner?

5- It will be better to make the partitions windows vista or during ubuntu installation?

Thanks :)

---

### Post by Eldar11 on 2007-12-09
Well first of all, the Dell Utilities partition has files and executables that can help maintain your system, and you would need two partitions for Ubuntu, one ext3 for the file system and one Linux swap that doesn't have to be very big.  The easiest way to resize, modify, and delete partitions is to use GParted, which is a Gentoo based partition editor, you would have to download it burn it as an image to a disk and boot from it as a live CD.  From there you can select partitions, resize, delete the ones you want and make it so you can install you Ubuntu.

The GParted download can be found [[COLOR="Blue"]here[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")


I don't know about the media direct buttons, but most of the extra buttons still work in Ubuntu, though I am not sure about those

you would need to make space for Ubuntu before installing, having two partitions free before inistalling, once Ubuntu is installed you will be able to choose which OS you would like to boot upon start up.

Considering that you have an Intel Core 2 Duo, the AMD64 would not work at all because there is no AMD chip.

Hope you have good luck installing

---

### Post by wilsaj on 2007-12-10
*2- Concerning the MediaDirect, without it the multimedia buttons of the front of the notebook still work?*

No. In fact, very bad things will happen if you press them after you've repartitioned things so they aren't where it expects them. And according to dell tech support there's no way to turn off the buttons either :/
It's not unfixable though. So try not to press the buttons, but if you do:

[http://ubuntuforums.org/showthread.php?t=628229](http://ubuntuforums.org/showthread.php?t=628229)

is a good resource for repairing the damage.


*4 - I cannot get the Ubuntu AMD64 version working if it is not on safe graphics mode. And with the 32-bit compatibility with some of the programs and the things i need to instal them or get them working and considering that is my first time in linux (althought i do not have any real problem learning)... I would want to ask what is the difference between a 64-bit and using a 32-bit Ubuntu. Is it noticable? Or will i just get a hard time getting all working in the 64-bit? Which one will it be best for the beginner?*

You need the 32 bit version because that's the one designed to work with your type of processor.



As for the partitioning questions, here are some good resources:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

---

### Post by catchxxii on 2007-12-12
> 4 - I cannot get the Ubuntu AMD64 version working if it is not on safe graphics mode. And with the 32-bit compatibility with some of the programs and the things i need to instal them or get them working and considering that is my first time in linux (althought i do not have any real problem learning)... I would want to ask what is the difference between a 64-bit and using a 32-bit Ubuntu. Is it noticable? Or will i just get a hard time getting all working in the 64-bit? Which one will it be best for the beginner?

You need the 32 bit version because that's the one designed to work with your type of processor.
 

Direct from the Intel Website: [http://www.intel.com/products/centrino/duo/description.htm](http://www.intel.com/products/centrino/duo/description.htm)
> Inte® 64 Architecture
An built-in technology that can take advantage of 64-bit applications as they become available.


Just a heads up.

---

