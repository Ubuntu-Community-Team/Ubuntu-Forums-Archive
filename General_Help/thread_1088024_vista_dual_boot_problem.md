---
title: "vista dual boot problem"
date: 2009-03-05
forum: General Help
---

### Post by meinvateristnein on 2009-03-05
when i start up vista form the GRUB kernelpage it says starting up......... but ive waited 30 mins and nothing happens...... what is the problem

---

### Post by harunahi on 2009-03-20
I am having exactly the same problem.

- I used GParted to shrink the vista parition
- I unstalled Ubuntu in the free space
- The Vista wouldn't boot 
- Grub displays Vista as a boot option but just says 'Starting...' and hangs
- I tried repairing Vista using Vista DVD. It did one or two things and claims there isn't now a problem, but same result. Hangs at 'Starting ...'
- I can see and access the Vista partition from Ubuntu.

I feel it might be a Grub config issue but I haven't a clue what to do about it!!

Please help!

Thanks

---

### Post by meierfra. on 2009-03-20
**meinvateristnein:**

In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.


**harunahi** I did post a reply in your own thread.

---

### Post by 0per4t0r on 2009-03-20
First of all, you should've NEVER edited your Windows partition while using ubuntu in any way! Well, have you tried booting windows in safe mode?

---

### Post by Flash858 on 2009-03-20
Booting multiple OSes has some inherent problems. There is a great utility called "Super Grub Boot Disk" that is a huge help, and has had me worry-free for a while now.

I boot Ubuntu, Mint, PCLinuxOS, Puppy Deep Thought, Windows XP, and Windows Vista from my hard drives(I also have Mandriva, Puppy 4 and Fedora on Flash drives), and I never have any boot issues any more.

The trick is to install grub to the ROOT PARTITION of the drive where you are installing rather than the MBR, and to copy and paste Grub's boot/grub/menu.lst into every boot/grub folder once you have it the way you want it. I keep the colors different for each partition in the menu.lst so I know where the MBR is currently residing, as the SGBD allows you to change this simply by booting from it.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Good luck!

---

### Post by 1ronlung on 2009-03-20
I've always found brute force and ignorance along with the following commands have served me well...
In Windows:
FIXBOOT
FIXMBR

And of course, the aformentioned super grub disk - helps cover a multitude of sins  :)

---

### Post by dtom2444 on 2009-03-20
I had a similar problem using GParted, only i got the BSoD! it happened after editing the Windows Vista partition using the GParted live cd. 
Solution: I had to reformat the partition and reinstall Vista.
I've now learned to NEVER use GParted again! ;)

---

