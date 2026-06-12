---
title: "Getting ubuntu-desktop (back)?"
date: 2009-01-26
forum: General Help
---

### Post by Moptop650 on 2009-01-26
Ok, so I've installed eeebuntu on my 900HA netbook. I'm trying to get the regular ubuntu's gnome desktop on it, because the one eeebuntu comes with is honestly crap. I installed linux to have linux, if I wanted eye candy and something hard to use I'd just use windows.

Anyways, someone on IRC mentioned sudo apt-get install ubuntu-desktop, which I ran, and it only changed the cursor to the normal ubuntu one. (A step in the right direction, I suppose). Yes I rebooted and chose the gnome session.

What else do I have to do?

---

### Post by snowpine on 2009-01-26
Hi Moptop,

It sounds like you should have installed this version of eeebuntu instead of the netbook remix: [http://eeebuntu.org/index.php?page=standard](http://eeebuntu.org/index.php?page=standard)

I think you can turn the netbook remix off by going to System->Sessions and Services and unchecking the netbook remix and maximus items. I haven't used eeebuntu in a while, so this is from memory. :)

---

### Post by snowpine on 2009-01-26
ps You can also run "regular" Ubuntu (as in "not eeebuntu") on the eee simply by following these instructions: [http://array.org/ubuntu/setup-intrepid.html](http://array.org/ubuntu/setup-intrepid.html)

---

### Post by Moptop650 on 2009-01-26
That doesn't say it supports the 900HA, but I'll do it anyways. I've installed ubuntu and that package source, installed the eeepc kernel. What do I have to do to get wifi working? I /think/ thats the only thing currently non-functional.

---

### Post by snowpine on 2009-01-26
Hi Moptop, let's back up a minute... Exactly which distro are you using on your 900ha? Are you running in "live" mode or installed to your hard drive? 

Now, let's talk about the wireless problem... 

I also have a 900ha, and I've tried a bunch of different distros. I've never had any trouble getting wireless working by carefully following the array.org instructions... the array.org kernel is pre-installed in many of the top eee-specific distros (like eeebuntu, ubuntu-eee, easy peasy, and cruncheee).

---

### Post by Moptop650 on 2009-01-26
I've got Ubunto 8.10 installed and booting from the SD Card.

As for the array.org, I've got it's source installed already, and I've installed the kernel from it. Other then that, I haven't found anything relating to wifi on their site, or any instructions to do stuff other then get the kernel.

Edit: Actually, I've got it now. I copied some lines from the [Riceeey Tweak](http://eee.ricey.co.uk/files/eee/RiceeeyTweak.sh), for the wifi section of it.

```
wget 'http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz'
tar zxf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
cd madwifi-hal-0.10.5.6-r3875-20081105
make clean
make
sudo make install
```

Other then that, I ran all the sections except: UI Icons, Smaller toolbar icons, Lid close suspend, Battery warning, ACPI (didnt work), Overclocking "Modules and driver", OSD, shutdown problem, disk atime.

Thanks for the help =D

Edit: On second thought, maybe not. The network thing in the top panel, when I select my wifi network and enter a password, spins for a minute or two, then the password prompt comes back up, and it doesn't connect.

Edit: On *third* thought, Maybe not-not! I did the disconnect-battery-and-power-cable-press-power-button-then-reattach trick I read somewhere, and now its all working again! :D

---

### Post by Moptop650 on 2009-01-27
Actually, upon further use, I've noticed that after suspending I have to reboot before wifi works again - any fixes known?

---

