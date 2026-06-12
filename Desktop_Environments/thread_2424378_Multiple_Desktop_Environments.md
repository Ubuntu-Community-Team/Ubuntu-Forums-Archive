---
title: "Multiple Desktop Environments"
date: 2019-08-07
forum: Desktop Environments
---

### Post by Shibblet on 2019-08-07
I am sure this question has been asked before, but I am going to add a little more data to this itteration.

Can you install multiple Desktop Environments WITHOUT having conflict between them and all of their specific applications installed?

i.e.  I have Kubuntu installed, but when I add ubuntu-desktop, I get the entire pile of apps that I do not want.

What I would like to do is install Ubuntu, Kubuntu, Xubuntu, Ubuntu-MATE, and Ubuntu-Budgie, and be able to switch between them without it being on a VM.

I will be testing some software for performance, so a VM destroys that idea.

Can anyone help?

---

### Post by sevendogs1337 on 2019-08-07
You are describing complete OS's, not desktops. Ubuntu has Gnome, Kubuntu KDE, Xubuntu Xfce4, Mate`, well, self-explanatory. If you want all of those desktops, just install each desktop. Each install will pull in a ton of extras though, so someone more versed in apt and the specific desktop you are looking for may be able to better guide you on how to install just the desktop environments you are looking for.

---

### Post by Shibblet on 2019-08-07
> **sevendogs1337 said:**
> You are describing complete OS's, not desktops.  Ubuntu has Gnome, Kubuntu KDE, Xubuntu Xfce4, Mate`, well, self-explanatory.

Yep.  That's what I meant.

> **sevendogs1337 said:**
> If you want all of those desktops, just install each desktop. Each install will pull in a ton of extras though, so someone more versed in apt and the specific desktop you are looking for may be able to better guide you on how to install just the desktop environments you are looking for.

Any idea what kind of conflict there will be between the desktop environments?  I'm imagining Budgie and Gnome work well together, but does Xfce4 or KDE cause any conflict?  Would I be better off doing an independent install of each OS, along with their DE?

---

### Post by #&amp;thj^% on 2019-08-07
> **Shibblet said:**
>  Would I be better off doing an independent install of each OS, along with their DE?

My view,Yep!
Desktop environments will often "fight" with each other and overwrite IE: Themes settings. For example, installing KDE on a system will very often break a Unity installation by overwriting GTK or similar properties. Similarly, installing Unity will break KDE most of the time.
The greatest difference I can see is that between KDE/Qt and GTK systems. Unity, Gnome and KDE/Plasma are all rather large and complex (compared to Xfce. LXDE, Openbox, Fluxbox).

---

### Post by sevendogs1337 on 2019-08-07
I think Budgie requires Gnome for a "full experience" or some other nonsense they have on docs I read. I don't think KDE or Xfce4 would walk on each other. What you may find though is KDE and Gnome each have their own file indexers which may impact performance. Maybe better to have multiple users each with their own environment so you don't muck up a single /home directory?

---

### Post by crip720 on 2019-08-07
You can try Linux AIO, multi desktops, but not up to date.  They seem to keep different desktops from interfering with each other, which happens when we do it ourselves

---

### Post by TheFu on 2019-08-07
> **sevendogs1337 said:**
>  Maybe better to have multiple users each with their own environment so you don't muck up a single /home directory?

THIS!  Use a different userid for each DE. That will keep the user-specific configs separate.

---

### Post by guiverc on 2019-08-07
I love having multiple desktops on my machines; with my selecting which I use at login My current Ubuntu 19.10 machine also has lubuntu-desktop (LXQt), xubuntu-desktop (XFCE) and ubuntu-mate-desktop (MATE).

I haven't added `kubuntu-desktop` in awhile as it seemed to clash with ubuntu-mate-desktop though I could never find the actual cause (in testing I could install Kubuntu and add ubuntu-mate-desktop without issue and likewise the reverse, but the clash always occurred once others or some program I use regularly was in the mix).  In my experience the more you add, the more clashes & problems you can expect - but yes many play well together - but unless you get someone who's had that exact combination (with the same release, as I've found different releases cause different results)  you'll have to test the combination yourself for your results.

---

### Post by andrew.46 on 2019-08-08
> **1fallen said:**
> Desktop environments will often "fight" with each other and overwrite IE: Themes settings.

It dows not have to be this way, although this is certainly true for Ubuntu. An example where things are a lot easier is Slackware where a simple ncurses interface (xwmconfig) allows painless switching between 7 desktop types. Some of these desktops are admittedly not 'front of the pack' but 3rd party offerings can certainly be added in...

---

### Post by yetimon_64 on 2019-08-08
> **sevendogs1337 said:**
> ... Maybe better to have multiple users each with their own environment so you don't muck up a single /home directory?
Wish I had of thought about that a few years ago when running about 6 or 7 DEs on the one Trusty install. I didn't seem to have much problems with settings clashing generally but the menus were a right royal pain to clean up, that can be done with a LOT of work by editing the desktop config file for each app that shows up where it isn't wanted.

> Would I be better off doing an independent install of each OS, along with their DE?sevendogs1337's suggestion or the idea above are both good, this is how I am currently doing it on this laptop. I currently have 5 full installs on the one drive; Ubuntu Xenial/Unity, Xubuntu Bionic/xfce, UbuntuMate Bionic, Manjaro/xfce and Lubuntu/lxde. I did have Kubuntu Bionic as well for a while but it was not to my tastes and is now replaced by Manjaro.

My previous multiboot setups involved a lot of work as grub was installed into each set up and the main install handling the grub boot screen had to be manually updated for each install after updates, a heck of a lot of work. Nowadays I keep a full grub2 install in each system and have installed rEFInd to act as a boot manager; all I have to do now is update all the separate systems and reboot, rEFInd scans and finds the latest kernel for each system saving me a lot of work, a screenshot of my boot manager ...
[ATTACH=CONFIG]283754[/ATTACH]
[[COLOR=#0000ff]--full resolution link for the above screenshot (3430x2200)--[/COLOR]]("https://drive.google.com/file/d/1cwAbdxQb81CoACP_Scu9199zgFnvS6UT/view?usp=sharing")
3 of my installs are flavors of Ubuntu Bionic; using a multiboot also allows for different releases of ubuntu as well, Xenial is the 1st icon in the screenshot above, or even other distros like Manjaro as in this example (2nd from right hand side). If you go with a multiboot and have grub in all the installs I can definitely recommend rEFInd as a boot manager rather than grub itself. There is quite a bit of work initially in setting it up and customizing it (if you are inclined to customizing things like boot managers) but it is well worthwhile in the end.
BTW, the screen shown above is a touch screen and there is a setting in refind.conf for enabling touch screens, all those icons will work if they are touched. Though I read touchscreen support is not guaranteed even if enabled in the config file, I was one of the lucky ones :D.

A single install using the idea discussed above (from sevendogs1337) is probably the easiest method but the multiboot and rEFInd is definitely a rewarding task from my work on it over the last week or two, and you can test/experiment with other releases of Ubuntu or even other distros as well.

Regards, yeti.

---

### Post by oldfred on 2019-08-08
My one experience with adding a different desktop did not work and I generally do not want to mess up my main working install. So I always do another install.

But I turn off os-prober and use my own 40_custom to boot other installs. You do not even have to update grub in main working install if you use configfile, or boot the link to most current kernel.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

From my 18.04 I boot Eoan this way. If I reinstall & reformat, I do have to reset label of partition.

```
menuentry "Eoan 19.10 on sdb9 test" {
    search --set=root --label eoan --hint hd2,gpt9
    configfile /boot/grub/grub.cfg
}


```

Or my other copy of 18.04 on HDD using link to most current kernel.
```
menuentry "Bionic 18.04 on sda7" {
    search --set=root --label bionic --hint hd0,gpt7
        #set root=(hd0,gpt7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}

```

---

### Post by #&amp;thj^% on 2019-08-09
> **andrew.46 said:**
> It dows not have to be this way, although this is certainly true for Ubuntu. An example where things are a lot easier is Slackware where a simple ncurses interface (xwmconfig) allows painless switching between 7 desktop types. Some of these desktops are admittedly not 'front of the pack' but 3rd party offerings can certainly be added in...

Yes I'm aware, I run 5 different environments now. ("I" just don't recommend it, To avoid confusion to a normal user.) Also to avoid wrong guess's when helping users in the forums.
**However** the Devs _don't appreciate_ this when filing bugs.(Testing, bug triaging,Gnome & KDE Plasma) 
On my play and daily work machines I'll have multiple DE's.
The OP was asking what would happen, and I did not feel they were in a testing mind set just yet. (I could be wrong though.:))
My advice is to help the user fully enjoy their experience, if an advanced user wants advice then thats a different story. :)
Reminds me of an old adage "If you have to ask, then probably not"

---

### Post by lammert-nijhof on 2019-08-12
What is the problem of using VMs? Yes the performance will be different, but for comparison it will be good enough. I use my VMs daily on top of ZFS and in some cases my performance is better than on bare metal. I reboot the Linux VMs in 6 to 10 seconds, my response times are instantaneous, because of the memory caching of ZFS. The performance of bare metal Ubuntu using EXT4, ZFS or BTRFS will also be different too and sometimes significantly different.

With ZFS you could easily create a datapool/partition for all Ubuntu OSes and have a dataset/folder per Ubuntu OS. In Ubuntu 19.10 they will support to boot from ZFS. I already boot from ZFS and have two different installations one Ubunu 19.04 with Virtualbox and another Ubuntu Mate 19.04 with QEMU/KVM. The snapshots of ZFS would probably be an advantage in your line of work! Those snapshots saved me twice once with a VM and once after a power-failed upgrade of Ubuntu Mate..

Currently I install the system on an ext4 partition (16 GB) kept free for the purpose. Afterwards I move the system to a ZFS dataset, chroot into it, run update grub, add an entry to /etc/grub.d/40_common of my main system, etc etc (approx 10 terminal commands in total) and I have another Ubuntu OS bootable from ZFS.

---

### Post by Shibblet on 2019-08-12
> **lammert-nijhof said:**
> What is the problem of using VMs? Yes the performance will be somewhat worse, but for comparison it will be good enough. I use my VMs daily on top of ZFS and in some cases my performance is better than on bare metal. I reboot the Linux VMs in 6 to 10 seconds, my response times are instantaneous, because of the memory caching of ZFS.

Gaming.

---

### Post by hk42 on 2019-09-01
Hi
I recently installed 19.04 on a Beelink BT3pro mini PC.
After various newbie's problems I ended with a log in menu offering:
Ubuntu
Ubuntu wayland
XFCE
Kodi
Gnome 
All seems to work OK
Most off my problems were due to the fact that I deactivated admin rights for all my users
When it is grayed it is in fact activated.
My advice is :
Do tests on a brand new installation not a heavily optimized one
Have several users with different rights
Keep at least one in English
Use short passwords for a start.

---

