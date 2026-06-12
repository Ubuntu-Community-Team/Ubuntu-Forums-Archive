---
title: "Suspend in Ubuntu 8.10 not working"
date: 2009-04-08
forum: General Help
---

### Post by snorbens on 2009-04-08
Hi,

Please bear with me as I am a newbie and first time poster, also I am no longer a spring chicken, so I may appear a little stupid to some;)

I am using a Toshiba L350 laptop, and when I try to suspend, it just goes to a blank flickering screen,but does not go into suspend. When I try to go back to Desktop nothing happens and I then have to do a hard re-boot using the on/off power button.

I have done a search but have not really found anything pertaining to this problem, or if there is I am such a newbie that I have not recognised it as such.

I would like to suspend this laptop when not in active use as it does get rather warm after a while and would also like to save power when not in use.

Any help would be appreciated.

Mervyn

---

### Post by psychoelf on 2009-04-08
Just checking....but do you have a swap partition setup?  Also, you could try turning of compiz.  There is a program in synaptic called fusion-icon.  That will allow you to switch compiz on and off without losing your settings.  This allowed my laptop to sleep (most of the time) ;)

After you install fusion-icon, press Alt-F2 and type "fusion-icon".  It will load up in the notification area on the top right of your screen.  Right click on the little blue box > Window Manager > Select Metacity.  This will also help with most video flickering.  Just turn Compiz back on for desktop effects.

If you want fusion-icon to load every time you boot go to System >Preferences >Sessions >Click add.  Name it whatever you want and type "fusion-icon" on the command line.  Don't worry about a comment.  Good Luck!

---

### Post by snorbens on 2009-04-08
Hi,
Thanks for reply. I loaded the fusion icon right clicked and enabled metacity. Still went to a flickering page but this time I looked harder and it seemed to me that the flickering is in actual fact, some sort of writing/message but was so indistinct and flickering I could not read it.

I had to switch off/on with the power button to re-load.

As far as the swap is concerned I am sure that I have a swap file or partition. I did manage to get the settings for it up on the terminal once but cannot remember what I input for it:mad: that is age for you.

Thanks for trying.

---

### Post by acimmarusti on 2009-04-08
Hi,

I report the exact same problem running Ubuntu 8.10 on my HP Pavilion dv5035nr notebook. Hibernate works (after a little tweaking) but suspend/sleep doesn't. I tried what you suggested but it didn't work. I have compiz off all the time to increase performance anyways.

---

### Post by snorbens on 2009-04-08
> **acimmarusti said:**
> Hi,

I report the exact same problem running Ubuntu 8.10 on my HP Pavilion dv5035nr notebook. Hibernate works (after a little tweaking) but suspend/sleep doesn't. I tried what you suggested but it didn't work. I have compiz off all the time to increase performance anyways.

Mine is a Toshiba Satellite L350 and even hibernate does not work in mine.

---

### Post by psychoelf on 2009-04-08
Hopefully somebody smarter then me comes along... :p

I've been using Ubuntu since 6.04 but I'm still quite a noob myself.

Until then just comb the forums and try everything!  But always have important data backed up just in case something gets seriously messed up.  Thats always been my method :lolflag:

---

### Post by snorbens on 2009-04-08
> **psychoelf said:**
> Hopefully somebody smarter then me comes along... :p

I've been using Ubuntu since 6.04 but I'm still quite a noob myself.

Until then just comb the forums and try everything!  But always have important data backed up just in case something gets seriously messed up.  Thats always been my method :lolflag:

OK thanks for your help, have been looking around but no luck yet. Yes I will have try some sort of backup as without suspend/hibernate this little darling gets hot and then firefox,opera and all my internet stop until a re-boot.

I do not really want to shutdown when not in use but may have to. I have a desktop in the other room with Vista but as I am disabled,and I now prefer Ubuntu, it is much easier for me to use my laptop. Also my other half would go mental if I put Ubuntu on that one.:p

Thanks for your input

---

### Post by acimmarusti on 2009-04-08
This is how I made hibernation work on my laptop:

First find out the exact amount of memory you have by doing this:

```

free -b

```

First, confirm that the number for swap is larger than that of your total memory. If so then use the value of your total memory for X in the following:

```

sudo -i
gedit /etc/rc.local

```

Now just add this line to the file you opened: echo X > /sys/power/image_size

exit, restart and try hibernating.

THis however, doesn't help in fixing suspend/sleep

---

### Post by snorbens on 2009-04-08
Hi,
Thanks for your help. free -b brings up the following

             total       used       free     shared    buffers     cached
Mem:    1985753088 1000624128  985128960          0   23703552  599113728
-/+ buffers/cache:  377806848 1607946240
Swap:    937639936          0  937639936
mervyn@mervyn-laptop:~$ 

I have 2Gb of RAM. I am sorry if I appear stupid but is that swap enough?

Also when I type sudo -i
gedit /etc/rc.local I get to blank pages come up one "local" and one "rc

I am very sorry but I am a complete newbie at this.

Thanks

---

### Post by KayakJim on 2009-04-08
I have 2 Dell Inspiron laptops both running Ubuntu 8.10 and neither is able to suspend or hibernate.

I believe this is a reported bug already as this has been a problem since 8.10 was released (at least for me).

---

### Post by snorbens on 2009-04-08
> **snorbens said:**
> Hi,
Thanks for your help. free -b brings up the following

             total       used       free     shared    buffers     cached
Mem:    1985753088 1000624128  985128960          0   23703552  599113728
-/+ buffers/cache:  377806848 1607946240
Swap:    937639936          0  937639936
mervyn@mervyn-laptop:~$ 

I have 2Gb of RAM. I am sorry if I appear stupid but is that swap enough?

Also when I type sudo -i
gedit /etc/rc.local I get to blank pages come up one "local" and one "rc

I am very sorry but I am a complete newbie at this.

Thanks

Think I was being stupid..it appears my swap is smaller than my memory, how do I increase the swap size? although it is more important for me to be able to suspend, I wonder whether my suspend problems may be down to swap size?

Also I got the two blank pages up by adding a space between rc.and local rather than just rc.local.
Thanks for your patience and I will learn I promise

---

### Post by snorbens on 2009-04-08
> **KayakJim said:**
> I have 2 Dell Inspiron laptops both running Ubuntu 8.10 and neither is able to suspend or hibernate.

I believe this is a reported bug already as this has been a problem since 8.10 was released (at least for me).

Thanks I am beginning to believe that but would be nice to solve the problem

---

### Post by kidux on 2009-04-08
Same problem here with my Satellite. Just been waiting for Jaunty to come to maturity before upgrading and hopefully getting it fixed.

---

### Post by snorbens on 2009-04-08
> **kidux said:**
> Same problem here with my Satellite. Just been waiting for Jaunty to come to maturity before upgrading and hopefully getting it fixed.

Yes with a bit of luck...but I would have like to stick with Intrepid for a while if only for me to get used to it.  I have only used it for just over two weeks.

---

### Post by ameermawia on 2009-04-08
my system is also having problem while hibernating .when ever i execute this command sudo /etc/acpi/hibernate.sh ,it first try to do some thing but then return to normal functioning with the error 
cat: /etc/network/run/ifstate: No such file or directory
cat: /etc/network/run/ifstate: No such file or directory

any body having any idea how to fix it?
with thanks!

---

### Post by aptenodytes on 2009-04-08
I am also having this problem with my MacBookPro3,1 and Ubuntu 8.10.

---

### Post by acimmarusti on 2009-04-08
Ok guys, the way hibernate works is that it assigns your info stored in your RAM memory to your swap partition and when you wake up it does the opposite. In this line of reasoning you need to have a swap that's at least the size of your RAM, though from what I've read, the standard thing is to use twice what you have of RAM. So, if you have 2 Gb, the best way to go (provided you have a large enough hard drive) is to use 3 to 4 Gb for swap. 

```

free -b

```

Will display your exact RAM (under Mem total) and your swap (under total as well), if your swap exceeds your RAM you can use the procedure I outlined before. If not, you need to increase your swap. The procedure to achieve this can be found here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I'll try to sum up the commands based on snorbens example:

```

sudo dd if=/dev/zero of=/mnt/2048Mb.swap bs=1M count=2048
sudo mkswap /mnt/2048Mb.swap
sudo swapon /mnt/2048Mb.swap

```

At this stage use *cat /proc/meminfo* to check your swap has increased.

```

gksudo gedit /etc/fstab

```

This will open up the fstab file using gedit. Now add this line to the end of the file and save: */mnt/2048Mb.swap  none  swap  sw  0 0*

After this use *free -b* to check that indeed your swap can hold all your RAM memory. If so, then follow the procedure I outlined in my last post. Then restart!

Hope it works for you guys, of course the next step is to try hibernating!, good luck!!, try suspend too and let me know if it also works for ya (it didn't for me, but who knows what will happen with you).

---

### Post by snorbens on 2009-04-08
Hi Andres,
Thanks for that..I have just spent nearly 4 hours using GParted resizing my partitions including my swap partition:p If I had known it was going to take that long I would have left it until tomorrow lol.

As it is 1am in the morning here I will just try to hibernate or and suspend and if it still does not work I will try your method tomorrow especially as I only resized my swap partition to 2.18Gb:mad:

I will post my results tomorrow.

Thanks for your help

---

### Post by snorbens on 2009-04-08
Just a quick update before bed.

Does not work at the moment will add the line you suggested in your first post tomorrow.

Just a quick question. When the file opened,at the end was the line exit 0

Do I add the line you suggest before or after that line?

One other thing that has happened since I re-sized the partitions is that on start up...........it goes hunting for the boot files and then runs a list and has to find other files after which it boots up ok.

Obviously done something wrong there then lol.

I will try and sort it tomorrow.

Thanks

---

### Post by acimmarusti on 2009-04-08
Oh yeah, that's actually very important, add that line before *exit 0*. Then restart and try hibernating: (note that you X value is 1985753088).

Of course resizing the swap partition should work too, once again, as long as swap is bigger than 2 Gb which seems to be your case, so hopefully you won't have to do the other method (which I posted because it's much faster!)

Good luck!

---

### Post by snorbens on 2009-04-09
> **acimmarusti said:**
> Oh yeah, that's actually very important, add that line before *exit 0*. Then restart and try hibernating: (note that you X value is 1985753088).

Of course resizing the swap partition should work too, once again, as long as swap is bigger than 2 Gb which seems to be your case, so hopefully you won't have to do the other method (which I posted because it's much faster!)

Good luck!

Hi,
I will have to try that later, as since I re-partitioned, the swap partition keeps turning itself off on re-boot and I have to re-set to swapon via GParted.

Also now when it boots I get the message "reading files needed to boot" if I remember right. Then it goes through listing etc before finally booting up.

I may have to do a complete re-install of Intrepid.

I did boot into recovery mode and after checks it did not seem to find anything wrong.

As I say I may have to re-install but I hope not.

---

