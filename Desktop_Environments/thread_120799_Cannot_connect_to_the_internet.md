---
title: "Cannot connect to the internet"
date: 2006-01-23
forum: Desktop Environments
---

### Post by seakiwi on 2006-01-23
[QUOTE=darth_vector]ok, it looks like you dont have a gateway entry. you want to add the following under the netmask line:

gateway 192.168.0.1

you will have to edit the file as root```
sudo gedit /etc/network/interfaces
```and then restart networking```
sudo /etc/init.d/networking restart
```

let us know if it works.

by the way, there shouldnt be anything (except maybe a tab) infront of the script grep and map eth0 entries.[/QUOTE]

I did enter a gateway when I set it up so I don't know why it's not appearing ...

OK, so under which network mask line am I adding the gateway address? The one under loopback network interface or the one under primary network interface?

EDIT: This post is appearing (for me anyway) out of thread order - no idea what that's about.

---

### Post by darth_vector on 2006-01-23
you want the following```
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
**gateway 192.168.0.1**
```and then do a```
sudo /etc/init.d/networking restart
```

---

### Post by seakiwi on 2006-01-23
[QUOTE=darth_vector]you want the following```
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
**gateway 192.168.0.1**
```and then do a```
sudo /etc/init.d/networking restart
```[/QUOTE]

THANK YOU! My hero!  :D

---

### Post by TransitMan on 2006-01-23
With respect "darth vector", I also tried that and it failed.

I had to manually edit the entire etc/network/interfaces to get my Kubuntu back online.
Wasn't hard, as I have another Ubuntu machine sitting her, and just played follow along.

However, in searching for answers to the KDE network drop issue, I found that it is a known bug, supposedly fixed in the upcoming Dapper Drake edition for KDE users.

Also, I had followed seakiwi's post from another forum and she was able to get up and running.

---

### Post by seakiwi on 2006-01-23
Hi

I've been using Ubuntu for about two weeks now and had no problems setting up my internet connection, but today I did a clean install of Kubuntu and no matter what I do I can't get online.

My network set up is as follows:

Host machine running XP Home - dial up (always on)  connected via a switch/ethernet to:

My machine running Kubuntu

Third machine running Windows XP Home

I have internet connection sharing enabled on the host machine.

I set it up the same way I did in Ubuntu - with manually assigned IP. The host machine/gateway is 192.168.0.1

My machine is 192.68.0.2 and the other Windows machine is 192.168.0.5

This was working perfectly under Ubuntu. What am I doing wrong? 

PS. I've posted this at the other Kubuntu forums but everyone seems to be asleep today and I really need to solve this urgently.

---

### Post by darth_vector on 2006-01-23
[QUOTE=seakiwi]My machine is **192.68.0.2** and the other Windows machine is 192.168.0.5[/QUOTE]

is that a typo or is that your problem? if its a typo, please post the contents of your /etc/network/interfaces

---

### Post by seakiwi on 2006-01-23
[QUOTE=darth_vector]is that a typo or is that your problem? if its a typo, please post the contents of your /etc/network/interfaces[/QUOTE]


Sorry, that's a typo!

Meanwhile I have another problem ... when I open the network settings window, it will not resize to let me view the Administrator mode button - I have to tab to it and hope I get the right one.

For some reason, now, when I go in as Administrator - enter my password and the red outline comes up on the window to show I'm in Admin mode - I get a 
"checking your configuration" (or words to that affect)  - then nothing. The settings windows do not become active and I can't alter anything. The Admin log in - isn't sticking. 

I can't believe this ....  I've only had this installed for five minutes and I've screwed it up already!  :( 

I'll see if I can figure out how to copy my etc/network/interfaces to this machine ... at this point I haven't got my machine "seeing" the others.

---

### Post by seakiwi on 2006-01-23
OK, I'll have to do it by hand ...

#The loopback network interface

  auto lo
  iface lo inet loopback
  address 127.0.0.1
  netmast 255.0.0.0


#This is a list of hotpluggable network interfaces 
#They will be activated automatically by the hotplug system

  mapping hotplug

` script grep

` map eth 0


# The primary network interface

  iface eth0 inet static
  address 192.168.0.2
  netmask 255.255.255.0

  auto eth0


***************************

Not sure what those little marks are supposed to be in front of the mapping hotplug bit - I might have used the wrong ones.

Any help? :confused:

---

### Post by darth_vector on 2006-01-23
ok, it looks like you dont have a gateway entry. you want to add the following under the netmask line:

gateway 192.168.0.1

you will have to edit the file as root```
sudo gedit /etc/network/interfaces
```and then restart networking```
sudo /etc/init.d/networking restart
```

let us know if it works.

by the way, there shouldnt be anything (except maybe a tab) infront of the script grep and map eth0 entries.

---

