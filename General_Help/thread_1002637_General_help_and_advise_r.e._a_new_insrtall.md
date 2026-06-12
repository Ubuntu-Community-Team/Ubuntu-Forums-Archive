---
title: "General help and advise r.e. a new insrtall"
date: 2008-12-05
forum: General Help
---

### Post by vinyl conflict on 2008-12-05
Firstly, hello im new to these forums although i have been lurking for a while. ):P

I was hoping i would be able to get some help and advise regarding a system i wish to set up. im new to linux although i have installed a few distro's before including ubuntu and kubuntu and had a little play.

Basically i have an old athlon xp pc i wish to turn into a server of sorts. i only wish to use it for torrentflux (so i can manage torrents from a different machine) and also to share a drive that is installed in it across my home network for storage and to access the torrents that have been downloaded.

the pc in question has 2 hard drives - one of 40Gb which i intend to use for the install of ubuntu and a 120Gb which i wish to use as a shared network drive and or storage. In any event i would like my windoze pc's on the same network to be able to access the files stored on it.

i need help in how to structure the 40Gb drive. i intend to do the following, can you please advise if this is correct?

200mb = /boot
15Gb = /root
2Gb = swap

remainder (around 22Gb) = /home

which brings me to another question.... what distro would be best for my needs? server edition straight away or can i go down the route of kubuntu and then install the required "lamp-server" files and samba?

I also need to know what is the best file system to use for the 120GB drive EXT3 or NTFS - the drive will be accessed by windoze machines. in effect would the linux machine be acting as a file server using the 120Gb drive?

how does samba work exactly? or would this not be needed?

what ever route i go down a GUI is essential as im useless in the console.

appologies for the dis-jointed post,

please help

Dave

---

### Post by vinyl conflict on 2008-12-05
Anyone?

if it helps the specs are

Athlon xp 2600+ (2.06mhz)
1.5Gb Ram (333mhz)
128Mb Ati Graphics card
40Gb HDD
120Gb HDD

Lan card 10/100 and belkin wireless card

I have loaded Kubuntu and everything works.

please offer some advice

---

### Post by SuperSonic4 on 2008-12-05
I'd give a bit extra to / from /home.With 1.5gb ram you probably only need 1gb of swap if that. I've never had a separate /boot partition so I'd not know.

mine would be:
/ = 18gb 
swap = 1gb swap
/home = 21gb 

As for whether to go with server edition or desktop depends if you want a minimal install or a more friendly install. Personally, you have the space to run a desktop so I'd install desktop and add server stuff.

For your 120gb hdd it depends on where else you'd use it. If it stay in your pc make it ext3 and install ext3 support in windows using: [http://www.fs-driver.org/](http://www.fs-driver.org/)
If it does not use ntfs to get access from more than one pc.

I think samba installs files that windows uses since it and linux use different server styles but I'm not sure and good choice with kubuntu ;)

---

### Post by vinyl conflict on 2008-12-05
Thanks for the reply,

i think i will follow your advise and increse the size of /root as i know understand anything else i do not allocate will come under this .... /boot .... /var ..... /dev for example.

i need a GUI to work so will stick with kubuntu and install anything i need from there. to be honest the pc is plenty powerful for this and will handle the desktop GUI in addition to file serving etc(it will only be used for my home network with 2 other computers)

i will keep the storage drive (120gb) as NTFS as i can see myself possibly needing to transfer to other machines at somepoint for whatever reason.

i think i will try and get samba up and running tonight before attempting to get torrentflux working. one thing i know i will be needing to do is assign this unit a static ip address everytime it boots up, rather than relying on DHCP from the router... how do i go about this in kubuntu?

also what are my best options for remote access on this machine? ie i would like to be able to log into the desktop from another machine on the network to change settings etc. what steps do i need to take?

thanks again

---

