---
title: "Easiest way to install Minecraft in Kubuntu 20.04"
date: 2020-09-15
forum: Gaming &amp; Leisure
---

### Post by cedric9 on 2020-09-15
My nephew has been attempting to install Minecraft 1.16.1  onto my desktop PC running Kubuntu 20.04, but each time we attempt to launch the Minecraft game, it displays a message stating "Please wait" but it never actually loads the game.  

I created a user account for my nephew, and made his account part of the sudo group, but this did not seem to make a difference.  Does anyone know what we are doing wrong?  

Any advice is greatly appreciated.

Operating System: Kubuntu 20.04
KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-47-generic
OS Type: 64-bit
Processors: 4 × Intel® Pentium® Gold G5400 CPU @ 3.70GHz
Memory: 7.6 GiB of RAM
Hard Drives:  Two 500 GB Seagate Barracuda

---

### Post by CatKiller on 2020-09-15
Did you remember to install Java?

---

### Post by cedric9 on 2020-09-15
> **CatKiller said:**
> Did you remember to install Java?

Nope, I sure didn't!  Guess I'll give that a try on Friday when he comes back.  Thanks for the info.

---

### Post by mastablasta on 2020-09-16
isn't open JDK installed by default?

installing minecraft on Ubuntu:

[https://linuxconfig.org/how-to-install-minecraft-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-minecraft-on-ubuntu-20-04-focal-fossa-linux)

if you need oracle java it get's more complicated now to install it and to maintain it up to date.
1. you need to sign up to oracle and agree to terms and conditions.
2. each time when there is an update, you need to manually download it and move it to folder accessible by root only. then perform the update.

go down to oracle java:
[https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-on-ubuntu-20-04)

i would suggest you try with openjdk first.

---

### Post by CatKiller on 2020-09-16
> **mastablasta said:**
> isn't open JDK installed by default?

Could be; I really can't remember. I was mostly prodding the OP towards the fact that Minecraft is a Java application, so there needs to be something to run that. I do remember that when I was last setting it up Minecraft itself seemed to do OK with OpenJDK, but OptiFine *really* needed Oracle Java.

I've also remembered that somewhere around 1.14-1.15 the original Minecraft.jar stopped working and you needed to switch out to a newer launcher, but I can't remember the symptoms of using the old one. Just that it didn't work.

---

### Post by mastablasta on 2020-09-16
> **CatKiller said:**
> 
I've also remembered that somewhere around 1.14-1.15 the original Minecraft.jar stopped working and you needed to switch out to a newer launcher, but I can't remember the symptoms of using the old one. Just that it didn't work.

well that explains my problem. suddenly nothing past 1.14.3 ran.

---

### Post by cedric9 on 2020-09-17
Well, it looks like installing Java allowed me to get Minecraft working on my system, but now I'm wondering about something else related to having this game installed on my PC.  I've been doing some reading, and it appears that Minecraft user files can occupy up to an entire gigabyte of space, so now I'm searching for a method to have Minecraft save its data to another partition other than my sda1 partition, where my Kubuntu installation resides.  

According to what I've read, there is a way to configure Minecraft to point to another user directory, once a user profile has been created, but it looks like my problem is going to be that my nephew will have to enter an administrator password each time he wants to mount the partition where his Minecraft user files are being stored.  

I don't really feel like giving him my password, so is there a way that he can mount one of my NTFS without having to enter a password.  Also, I his account to be just a regular user account if I can get away with it.  

Any advice greatly appreciated.

---

### Post by mastablasta on 2020-09-17
the easiest way is to automount at boot: [https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup](https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup)

this will however, give them access to all NTFS drive.

if you used linux file system on it, you could assign and mount only a folder. i am not sure this is possible on linux with NTFS.

for example i put minecraft server on my home server. then i created minecraft user (normla user, no sudo powers or anything like that) that can only acces via SSH their small /home folder and a folder on RAID1 disk that is mounted at boot and only one folder is accessible to this user. it's where minercfat is and where server runs and saves files.

another option, if you had linux files system, would be to symlink a folder from that system to /home./minecraft of this user


finally, is 1 GB still a lot in the era of terrabyte (1000GB+) drives? ;)

---

### Post by cedric9 on 2020-09-18
> **mastablasta said:**
> the easiest way is to automount at boot: [https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup](https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup)

this will however, give them access to all NTFS drive.

if you used linux file system on it, you could assign and mount only a folder. i am not sure this is possible on linux with NTFS.

for example i put minecraft server on my home server. then i created minecraft user (normla user, no sudo powers or anything like that) that can only acces via SSH their small /home folder and a folder on RAID1 disk that is mounted at boot and only one folder is accessible to this user. it's where minercfat is and where server runs and saves files.

another option, if you had linux files system, would be to symlink a folder from that system to /home./minecraft of this user


finally, is 1 GB still a lot in the era of terrabyte (1000GB+) drives? ;)

Well, I really don't want to give him access to all of my NTFS partitions, so I guess what I will have to do is mount the partition for him each time he comes over, which is usually only once or twice a week.  

BTW, we got Minecraft to work, but I can find anywhere within its settings to make it store data to an alternate location?  Any ideas how this works?  

Also, the reason why I'm worried about adding too much to my sda1 partition, is because I usually keep that partition at around 30 Gb in size, that way it is easier/faster to create images of it and to restore them if need be.

---

### Post by CatKiller on 2020-09-18
> **cedric9 said:**
> BTW, we got Minecraft to work, but I can find anywhere within its settings to make it store data to an alternate location?  Any ideas how this works? 

There are lots of things that are set in the launcher rather than in-game; the save location is one of them. Or you can just symlink that user's ~/.minecraft to wherever you want. 

> Well, I really don't want to give him access to all of my NTFS partitions, so I guess what I will have to do is mount the partition for him each time he comes over, which is usually only once or twice a week. 

Even using NTFS, which doesn't understand permissions, there's access and there's access. Mounting a partition somewhere at boot and symlinking ~/.minecraft to a directory on it is functionally the same as having ~/.minecraft as a normal directory unless they go digging around in the filesystem in preference to playing Minecraft. We have no idea if your nephew is someone that would do that.

Or you could use a partition that uses a Linux filesystem, so you have standard permissions available to control access. Or you could have /home as a separate partition to reduce the size of your backup images. Or you could have just that user's Home directory as a separate partition. Or have a separate partition to be used just for that user's ~/.minecraft. Or use NFS to mount a filesystem from a different machine entirely. Lots of options.

---

### Post by agvantibo on 2020-09-23
Try mingling with sudo visudo

---

### Post by Tadaen_Sylvermane on 2020-11-02
Forgive me if I sound rude. I'm confused. So many replies. It's a simple thing really. Install Debian version from [https://www.minecraft.net/en-us/download](https://www.minecraft.net/en-us/download). Then run ```
apt update && apt install -fy
``` to make sure you got everything it needs (should come with everything). Minecraft will only go to /home/"$USER"/.minecraft. Symlink wherever you want to that location and it will work as long as you have read / write permissions on that location. There is no need for sudo or anything fancy (aside from the inital deb install).

Worlds can get big no question. If this is just one player I wouldn't expect it to get that massive really. The wife and I had a server that never broke 1gb and we were running it for a bit less than a year. If you wanted to write a little script he could keep his worlds on a flash drive. This would require a bit of configuration. The function below could help get you started and you would need to have a noauto,user mountpoint for the flash drive to somewhere then copy the folder to /home/"$USER"/.minecraft. Rsync back when game exits. I use the below function to keep my desktop synced with my server for pxe booted machines I have in the house as well.

```
mc_ssd_launch() {    
    MCBACKDIR=/serverhomes/"$USER"
    if ! ps -u "$USER" | grep minecraft-l ; then
        rsync -au --delete "$MCBACKDIR"/.minecraft /home/"$USER"/
        gtk-launch minecraft-launcher
        until ! ps -u "$USER" | grep minecraft-l ; do
            sleep 10
        done
        rsync -au --delete /home/"$USER"/.minecraft "$MCBACKDIR"/
    fi
}
```

---

### Post by QIII on 2020-11-02
I would highly recommend putting a local MineCraft server in a VM and not going on line with it.  With a VM, the youngsters can play from a different machine on your network.  A laptop or what have you.

Oracle Java works best with MineCraft.  Some features hiccup with OpenJDK, particularly the command line goodies.

I have a MineCraft server on a VM on a separate physical machine on my network for the grands to use without worrying about my machines.  I'm generally not a big fan of gaming, but in these days of being locked in due to Covid-19, I thought it appropriate to give them something to do besides breaking farm implements.  Life can get a bit boring at the end of a mile of gravel road.

A Gigabyte is a pittance in these days of Terabyte drives if you have one.  I gave the MineCraft server VM 500GB.  The boys can tear it up.  If they break it, I can decide, at my leisure, if I am going to re-install the OS and the Minecraft server.

---

### Post by Tadaen_Sylvermane on 2020-11-02
Can also docker the minecraft server easily enough if you wanted to. Here is how I do mine at home now. Has ramdisk capability if you wanted it. Some say it's not much better than ssd. I respecfully disagree. Got the ram to spare so I do it for all my minecraft servers

[https://github.com/jmgibson1981/scripts/tree/main/docker/minecraftserver](https://github.com/jmgibson1981/scripts/tree/main/docker/minecraftserver)

---

### Post by mastablasta on 2020-11-03
> **QIII said:**
> 
Oracle Java works best with MineCraft.  Some features hiccup with OpenJDK, particularly the command line goodies.


Oracle Java also works better on a server?


We used OpenJDK and i've put it on bare metal and assigned 2 Gb RAM to it. unfortunately the server is not as strong as i hopped (CPU wise) so it would sometimes lag.

i created special user with access to only Minecraft server folder and i do not allow any connections from internet (only ports for SSH and nextcloud are open)

VM is not a bad idea. though first i experimented and installed it on my kids machine. he has 8 cores and 16 GB ram, so i guess it could also work as server for all 3 users. i used to be "listen" server with my old single core and it used to work well before, but lately with newer updates this is no longer possible. though we are not at the end of the road, they are at home on extended holidays and they can't go out. so having minecraft working reasonably well is quite important these days.

---

### Post by CatKiller on 2020-11-03
> **mastablasta said:**
> he has 8 cores and 16 GB ram, so i guess it could also work as server for all 3 users.

A Raspberry Pi can handle being a Minecraft server for 3 users.

---

### Post by mastablasta on 2020-11-03
well looks like AMD Turion II Neo N40L really can't do it so well. or maybe it's just the OpenJDK i used for server?! when i start it up it already has issues and is reporting that it is behind for a few ticks. though overlal it plays OK there are some delays (lag) during game.

---

### Post by CatKiller on 2020-11-03
To be fair, when I was running a Minecraft server on a Pi, I was using [Spigot](https://www.spigotmc.org/). I moved it to a NUC, since I was running that anyway as an HTPC and Steam In-Home Streaming target, so I haven't tried recent versions on a recent Pi.

---

### Post by mastablasta on 2020-11-03
someday, *when i grow up*, i will have NUC or the small Asus ITX PC (AMD based) for HTPC as well. for now the old RPi will do for some videos and maybe i will get a new version. they have 8 GB ram now.  

This server i sued since it didn't have much use otherwise. special now that there arent' many family pictures &videos that need backup. and mostly it was used just for backup of "phone data" idling and occupying the room in this complex design with RAID1 WD red drives and all sorts of security measures in place. so might as well let is be used more than 5 % and 300 MB ram or whatever it is chugging at now.

---

