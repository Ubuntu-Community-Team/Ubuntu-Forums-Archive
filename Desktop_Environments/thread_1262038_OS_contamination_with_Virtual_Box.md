---
title: "OS contamination with Virtual Box?"
date: 2009-09-09
forum: Desktop Environments
---

### Post by pacobuntu on 2009-09-09
Hello all!
I'd like to setup my system with two partitions: one Ubuntu, and the other XP(I know some purists sigh at the thought, but I'm not savvy enough yet to make Ubuntu work for everything I want to do), and run XP as a virtual machine in Virtual Box.  

My question is if I run internet in ubuntu as my host OS is my guest OS (XP) still safe from the general crapware floating around on the net, or do I still have to worry about malware affecting my XP side?

---

### Post by Isarii on 2009-09-09
Yeah, I'm in the same boat and I'd like to know this too.  /lurk

---

### Post by vasiliymeshko on 2009-09-09
As long as the virtual OS has no connection, then this should be a non-issue. For my virtual XP, I leave 'Cable Connected' option unchecked by default. It can be enabled from the statusbar, if absolutely necessary. 

Now if you are planning to have the guest os connected to the net, then its a different story. It *will* be affected by viruses/spyware/etc just like a non-virtual Windows is.

---

### Post by ugm6hr on 2009-09-09
Yep.

Use internet or other virus-laden files in a VM abd the VM is at risk.

A VM behaves exactly like a separate computer; for most purposes it can be considered as such.

The upside is that creating a Virtual Disk image for backup and easy restoration is very straightforward.

---

### Post by aesis05401 on 2009-09-09
From experience, leaving your VM without any net connection will get tiresome quickly - especially if you are using network printing or programs that need bug fixes downloaded etc...  This advice probably   applies most to users who occasionally need to spend a couple days straight inside an MS environment, but don't want to be toggling adapters from within the environment (ie: you want your VM and programs within to act like they are online even when they are not... )

I use brctl and tunctl utilities to create a host bridge and VM client tap connections.  I don't actually connect the taps to the bridges until I want the VM to see the rest of the network, but the VM behaves as if it is online because the virtual interface it uses is up the whole time (ie: both VBox and XP display cable connected, but any outbound signals time out because they don't actually go anywhere).

If you do not have brctl or tunctl you can find them through Synaptic.

```

# Create a fake interface for my VM using tunctl (I will use tap0 as
# the name for my fake interface as per a tutorial I read somewhere):

sudo tunctl -u <your-user-name> -t tap0


# Configure tap0 for operation on your real network for when you want to 
# hook it up

sudo ifconfig tap0 <ip-address> ... <any-other-required-settings> up


# Ensure permissions are proper on the /dev/net/tun file

sudo chmod 666 /dev/net/tun


# Open VirtualBox and add tap0 as the network interface for your VM
# Boot Vm - you should see the network connection reported as present
# but you can't actually get out to anywhere.

```

Now you should set up your host bridge.  The following example is just the fastest way to do this as far as set-up goes.  You should research promiscuous mode as it has some security side-effects, side-effects on busy LANs, and of course, allows you to sniff and spoof responses to all traffic on your LAN which is what we want for our quick and dirty method:
```

# Prepare physical interface to join bridge

sudo ifconfig eth0 0.0.0.0 promisc


# Create bridge, add eth0 to bridge

sudo brctl addbr br0
sudo brctl addif br0 eth0 


# Dhclient the bridge for host visibility

sudo dhclient br0

```

So now, unless you need to modify your firewall settings, you are exactly one step away from connecting your VM to the internet.

```

# Simply enter this command from the host to go online with your VM

sudo brctl addif br0 tap0


# Enter this command from the host to go back offline.. 

sudo brctl delif br0 tap0


```

Once you have played around with this I would recommend writing simple scripts to manage everything.  I turn off network-manager and use the /etc/interfaces file to make sure my machine boots with no interfaces loaded.  Then I use scripts to bring up different interfaces/modify firewall rules depending on what VM's I need to run and how concerned I am about exposure to the internet... 

Provided you are not setting up new VM's every day, but only running a few for interop reasons, these scripts should serve you well for a long time.  Just be sure to research the various methods of creating a host bridge/managing your physical interfaces, there are advantages and drawbacks to each.

Finally, if you are going to be running VM's and have concerns I would recommend learning about iptables firewall/NAT configuration and log reading.  With these tools you can turn your computer into a really nice VM platform w/solid security.

Hope this helps.

---

### Post by adam.d.clemons on 2009-09-09
I did not have good luck with Virtual Boxing windows XP inside of ubuntu. unless your hardware supports hardware virtualization, your virtual box will not have as good of specs as your actual machine. For the full benefits of having windows there, i would recomend just partitioning off a small bit of harddrive for it and just reboot when you want to switch. I've managed to run more under wine than on my virtual XP.

---

### Post by aesis05401 on 2009-09-09
> **adam.d.clemons said:**
> I did not have good luck with Virtual Boxing windows XP inside of ubuntu. unless your hardware supports hardware virtualization, your virtual box will not have as good of specs as your actual machine. For the full benefits of having windows there, i would recomend just partitioning off a small bit of harddrive for it and just reboot when you want to switch. I've managed to run more under wine than on my virtual XP.

There is a good point about reduced performance, but if you dual boot you are reduced to working from within the MS environment again.  If you have concerns about the integrity of your installation or potential activity taking place via rootkit you need to reinstall (or reflash your image if you keep current .iso backups).  

If you are running via VM getting your MS install rooted is simply another day of fun in the sun :)

You can recreate the benefits of running within a VM partially by running the net connection through packet inspection on a different machine, but this requires two dedicated boxes now instead of one.  

Just a thought.

---

### Post by pacobuntu on 2009-09-10
Thank you eveyone!
This kind of help is one reason why I want to run Ubuntu as my primary OS more than Windows.  Though I dont have the terminal know-how to do what [aesis05401]("http://ubuntuforums.org/member.php?u=736896") said to do for net connection in VM.  For my purposes I dont need to use net in xp, except for updates and maintenence.  in which case I should be able to disconnect from the net in my host and then the hardware is available in my guest, right?  

Also, I read somewhere that I need to have a partition of my drive unformatted to install XP, is that true because i already formatted it?

---

### Post by ugm6hr on 2009-09-10
If you want to install XP in a VM, there is no need for a separate partition at all.

It is easiest to just install it from a virtual disk image.

---

