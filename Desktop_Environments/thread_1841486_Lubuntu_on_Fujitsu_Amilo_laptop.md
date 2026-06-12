---
title: "Lubuntu on Fujitsu Amilo laptop"
date: 2011-09-09
forum: Desktop Environments
---

### Post by ixusubunt on 2011-09-09
Recently loaded Lubuntu on Fujitsu Amilo La1703 (previously Vista) and I have two issues that I can't sort out:
1. No Wifi (worked previously) ... ethernet ok.
2. Minitube will not play any videos

Any advice on either of these problems?
Thanks
Paul

---

### Post by mörgæs on 2011-09-10
For the wifi problem, this forum is a better place:
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

---

### Post by kerry_s on 2011-09-10
you need to use the ppa version for minitube.

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by claracc on 2011-09-10
Lubuntu 11.04 installed on pentium III, CPU 1 GHz, Ram 512 MB, 64 Mb of them for the sis 630/730 videocard. I installed minitube from repositories and I couldn't see any video with it. So I uninstalled.

I installed VLC and I can see youtube videos through the url, also you can try smplayer.

---

### Post by ixusubunt on 2011-09-10
Thanks kerry_s, 
Minitube now plays movies ... almost! If I touch anything it crashes back to the Login screen! (even moving the window or resizing). Is there a setting I need to adjust? Thanks

---

### Post by ixusubunt on 2011-09-10
[[COLOR=#d40000]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075"),
Thanks for the link. I found the instructions for installing the correct WLAN driver and now the WiFi is working! If anyone else has a similar problem with a Fujitsu Amilo La1703 then the answer is here [http://www.uprize.no/?q=node/1](http://www.uprize.no/?q=node/1)
:D

---

### Post by amjjawad on 2011-09-10
Enjoy using Lubuntu and hope all your problems got fixed :)

---

### Post by ixusubunt on 2011-09-10
I spoke a bit too soon regarding the WiFi! When I rebooted the computer the wireless was lost again. I went back through the instructions to fix it and established that I need to put "[FONT=Courier]sudo modprobe ndiswrapper"[/FONT] into the terminal to get it going again. Not a big problem ... but it would be useful if anyone could explain how to stop the computer forgetting!
Thanks

---

### Post by amjjawad on 2011-09-10
> **ixusubunt said:**
> I spoke a bit too soon regarding the WiFi! When I rebooted the computer the wireless was lost again. I went back through the instructions to fix it and established that I need to put "[FONT=Courier]sudo modprobe ndiswrapper"[/FONT] into the terminal to get it going again. Not a big problem ... but it would be useful if anyone could explain how to stop the computer forgetting!
Thanks

What is the output of:

```
sudo lshw -C network

```

Please wrap up the output with "CODE" tags or select and click "#".

---

### Post by ixusubunt on 2011-09-10
Amjjawad,

This is the output

*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:a0:d1:c5:4e:8b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.0.10 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:4800(size=256) memory:d9300400-d93004ff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:30:05:d9:9f:d1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+sis163u driverversion=1.56+Silicon Integrated Systems ip=192.168.0.11 link=yes multicast=yes wireless=IEEE 802.11g


Thanks

---

### Post by amjjawad on 2011-09-11
> **ixusubunt said:**
> Amjjawad,

This is the output

```
*-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:a0:d1:c5:4e:8b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.0.10 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:23 ioport:4800(size=256) memory:d9300400-d93004ff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:30:05:d9:9f:d1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=[COLOR=Red]**ndiswrapper+sis163u **[/COLOR]driverversion=1.56+Silicon Integrated Systems ip=192.168.0.11 link=yes multicast=yes wireless=IEEE 802.11g
```
Thanks

What is the output of:

```
lsmod | grep ndiswrapper
```

I'm trying to check whether there are more than one driver for the same device. I had a similar issue before so I'm just checking.

Please, when posting the output of any command, make sure to wrap up the text with "CODE" Tags or just highlight the text and click "#".
[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

### Post by ixusubunt on 2011-09-11
Here it is
```
ndiswrapper           192828  0 
```

Thanks

---

### Post by amjjawad on 2011-09-11
> **ixusubunt said:**
> Here it is
```
ndiswrapper           192828  0 
```Thanks

Ok, so there is only one driver for your Wireless Card. Good.

I have done this with my system and it helped:

[http://ubuntuforums.org/showpost.php?p=10983947&postcount=5](http://ubuntuforums.org/showpost.php?p=10983947&postcount=5)

Please follow the instructions in this post.
Feel free to explore the whole thread if you are interested.

---

### Post by ixusubunt on 2011-09-11
Amjjawad,

I followed the link, and it recommends running 
[LEFT]```
sudo gedit /etc/pm/config.d/config
```[/LEFT]

followed by adding the code:

SUSPEND_MODULES="your_driver"
In my case "my driver" is listed as > ndiswrapper+sis163u ... should I just insert sis163u or the whole thing?

Thanks

---

### Post by amjjawad on 2011-09-11
> **ixusubunt said:**
> Amjjawad,

I followed the link, and it recommends running 
[LEFT]```
sudo gedit /etc/pm/config.d/config
```[/LEFT]

followed by adding the code:

SUSPEND_MODULES="your_driver"
In my case "my driver" is listed as  ... should I just insert sis163u or the whole thing?

Thanks

I think the whole thing so it will be:
SUSPEND_MODULES="[COLOR=Red]**ndiswrapper+sis163u**[/COLOR]"

---

### Post by ixusubunt on 2011-09-11
I did that but when I tried to save the file, I got an error message stating:
> You do not have the permissions necessary to save the file. 
Please check that you typed the location correctly and try again.Could not save the file /etc/pm/config.d/config.This is getting complicated ... is my config file in the wrong place?!

---

### Post by amjjawad on 2011-09-11
> **ixusubunt said:**
> I did that but when I tried to save the file, I got an error message stating:
This is getting complicated ... is my config file in the wrong place?!

I'm sorry, if you are using Lubuntu then replace "gedit" with "leafpad".

```
sudo leafpad /etc/pm/config.d/config
```If there is no file, you can create it just like I did.

Edit:
I'll go for shopping and will check on this thread later.

---

### Post by ixusubunt on 2011-09-11
Ok, I followed your instructions and created the new config file, but when I re-booted the computer the WiFi was lost again.
I had to run ```
sudo ndiswrapper -l
```then

                        ```
sudo modprobe ndiswrapper
```to get it back again (which is no big problem really)

One thing I should mention ... this laptop drops the WiFi every time it is shut down. I have to press Fn and F2 to get the indicator light back on! I do this as soon as I have pressed the 'on' switch.

Thanks for your patience ... hope you enjoyed your shopping!

---

### Post by amjjawad on 2011-09-11
> **ixusubunt said:**
> Ok, I followed your instructions and created the new config file, but when I re-booted the computer the WiFi was lost again.
I had to run ```
sudo ndiswrapper -l
```then

                        ```
sudo modprobe ndiswrapper
```to get it back again (which is no big problem really)

One thing I should mention ... this laptop drops the WiFi every time it is shut down. I have to press Fn and F2 to get the indicator light back on! I do this as soon as I have pressed the 'on' switch.

Thanks for your patience ... hope you enjoyed your shopping!

I didn't enjoy my shopping ... I left the cart with all the stuff inside and just walked away ... you have no idea how many people were there :S
I felt like there is no more food in the world and today is the last day ... what is wrong with these people?
Yes, you will be surprised that I'm so much patient here but I have ZERO patience  when it comes to shopping.

Feel better after venting out ... sorry!

Back to topic :)

Well, you are not alone. I have a mysterious problem. Every day when I wake up, I have to reboot my Range Expander so that I can receive the WiFi signal in my room. I have change the device but still the same issue. Couldn't fix it until now. That's why Wired Networking is better if you ask me. At least no headache.

I have no idea honestly how to fix your problem :(
I have no experience with "ndiswrapper" at all.

Have you tried to post in [Networking Area]("http://ubuntuforums.org/forumdisplay.php?f=336") of this forum?

---

### Post by ixusubunt on 2011-09-11
amjjawad, 
Sorry about the shopping ... similar for me today except that I persevered and survived the check-out!

Yes, wireless is a common problem ... I looked at the Networking forum and found other people asking for advice about similar issues. I have added a message to one of them.

Thanks again ... it all helps me to understand Ubuntu!

---

### Post by amjjawad on 2011-09-11
> **ixusubunt said:**
> amjjawad, 
Sorry about the shopping ... similar for me today except that I persevered and survived the check-out!

Yes, wireless is a common problem ... I looked at the Networking forum and found other people asking for advice about similar issues. I have added a message to one of them.

Thanks again ... it all helps me to understand Ubuntu!

Well, guess what? I went back to the Supermarket and found my cart as I left it with some stuff added and the Supermarket was about to close so I just removed the stuff that I didn't choose and paid :D What a crazy thing to do but what shall I do? I live next to that Supermarket and that's why I go there. Next time, I will never do that no matter how close it's because of the crowed.

Yes indeed, Wireless is a pain, some or most of the time.

I'm so sorry for that again. I wish I could help.
Try this, perhaps it will give you more results: [www.googlubuntu.com](www.googlubuntu.com)

Yes, each post here will add something to your knowledge; that at least what happened with me :)

---

### Post by ixusubunt on 2011-09-12
Hey amjjawad, I found the solution on the networking forum as you recommended!

See my post here:
[http://ubuntuforums.org/showthread.php?p=11244780#post11244780](http://ubuntuforums.org/showthread.php?p=11244780#post11244780)

So you did help me after all.

I can now switch off my laptop and let it cool down occasionally!!

---

### Post by amjjawad on 2011-09-13
> **ixusubunt said:**
> Hey amjjawad, I found the solution on the networking forum as you recommended!

See my post here:
[http://ubuntuforums.org/showthread.php?p=11244780#post11244780](http://ubuntuforums.org/showthread.php?p=11244780#post11244780)

So you did help me after all.

I can now switch off my laptop and let it cool down occasionally!!

Hey, glad to know that, well done :)
I wish I could have done more for you but my knowledge and experience still limited :)

Good luck and enjoy using Lubuntu, it's super fast ;)

---

