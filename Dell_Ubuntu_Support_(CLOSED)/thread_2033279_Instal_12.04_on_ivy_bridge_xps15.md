---
title: "Instal 12.04 on ivy bridge xps15"
date: 2012-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by katoiam on 2012-07-25
Hello one and all,

  I have a few questions regarding my new xps15 and installing k/ubuntu.

First off, I have been trying to get my head around the ssd card. Mine came with 32Gb. To begin with I was of the understanding that winblos 7 was installed on it, then I got the impression that it was installed on the HDD and the SDD was used only for a cache. Now I'm getting the feeling that winblows is on the SDD, but there is quite a large amount of it un partitioned, which I am begining to believe is used for the cache. 

The main reason why I am trying to get my head round this is (besides wanting to know how my computer works) that I probably use winblows about 5% (maybe less) of the time, only for music production and kubuntu 95% of the time for everything else. So I would ideally like to install kubuntu to the ssd card to make use of its quicker response time. 

How would I go about installing kubuntu on the ssd card with out ******* up how windows works, and having to reinstall etc.

2ndly, I have noticed that Dell have lready partitioned my 1TB HDD drive 3 times. 

**Would this mean that if I decided to install 'nix on my HDD I would need to remove at least one of the dell partitions so I could have my / partition as a primary partition?**

3rdly, whats the deal woith the touch pad?!?!?! I don't have a right mouse button, I can get functionality by setting it either to the right hand bottom corner, or as a 2 finger tap, but this doesn't allow me to use the right and left click paste thingo that I love in linux! 

**Any one got any idea how to get the right click working?**

I hope to hear from Y'all soon,

Cheers,

Liam

---

### Post by oldfred on 2012-07-26
Different model, but is this similar?

 Intel Smart Response Technology.
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

### Post by katoiam on 2012-07-26
Thanks old fred.

Does any one know about the mouse? I had the same issues when trying out my gf's Macbook pro with kubuntu live disk. There must be something I am missing as I imagine quite a few laptops come with this type of touchpad. 

Any help would be muchly appreciated.

Cheers

---

### Post by katoiam on 2012-07-31
So.....

After originally trying the Kubuntu 12.04 live disk, and having issues with my mouse I decided to try out a few other distro's to see if any one of them would work better out of the box. I tried:

Sabayon
Simply Mepis
Chakra
open suse
ubuntu 12.04

None of these worked better than Kubuntu out of the box (Ubuntu was the same, but I prefer kde to gnome/ unity)

So I followed the link given by old fred to install on my msata drive.

All pretty much ran according to plan. 

I then created an extended partitions ( I used an extended partition so I could leave the partition structure that dell had made (Dell recovery, recovery partitions and windows 7) and still add 2 more partitions) on my HDD for my /home/$/downloads and /home/$/music as the 20GB partition on the msata for home isn't going to be enough for my usage.

I then used this:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

as it was a fresh install I didn't need to copy anything from the folders.

So the things that don't work out of the box are:

Touchpad

Nvidia GeForce GT 640m


I tried to install the nvidia-current drivers after seeing this page:

[http://www.techlw.com/2012/06/install-nvidia-driver-in-ubuntu.html](http://www.techlw.com/2012/06/install-nvidia-driver-in-ubuntu.html)

saying that my card was now supported. After rebooting I had 640 x 480 screen size!! Doh! managed to remove (purge) and remove the nvidia-xconfig file and managed to reboot into the normal 1920 x 1080 running on the intel gpu.

So given up on the Nvidia for the moment. To be honest the intel does everything I need it to do for the moment.

EDIT: In the process of removing Nvidia-current I installed Bumblebee. It didn't seem to do anything for me at the time. I have just been playing around with it, and It does seem to work on this card. You just need to run optirun *programme* in the commandline. Using [http://videos.mozilla.org/serv/mozhacks/flight-of-the-navigator/](http://videos.mozilla.org/serv/mozhacks/flight-of-the-navigator/) as a test using firefox normal and optirun firefox the difference is immediate. 

The touchpad how ever is really annoying. After a bit of research around the subject, finding out that lots of people with different laptops are having the similar problem. It seems that the touchpad doesn't have any drivers and the manufacturers don't seem to be making any effort to either write one or open the source, so looks like it might be a while.

Kubuntu by default allows 2 finger touch & bottom right corner  for right click, on top I put 3 finger touch as middle click to allow for pasting. So it kinda works. Its overly sensitive, trying to left click on things can be a bit haphazard and frustrating. 

The graphics card I can live with (for the moment) the mouse is very annoying and stops me from, trying, to convert people to linux.

Battery life is severely reduced as well. I haven't done a proper test but seems to be about 2 1/2 hours.

---

### Post by oldfred on 2012-07-31
I have seen several posts on touchpad issues. Not even sure what model computer.

But my workaround is a mouse. I hate touchpads, the old IBM eraser control and anything else. I just buy an inexpensive smaller wireless mouse. It has always worked except the time I lost USB plug-in.

---

### Post by katoiam on 2012-07-31
I hear ya old fred. This touchpad, is in my opinion very nice though, and I would like it to work. Especially like I said before, when showing off linux to people for the first time. 

My hope now is that as Dell is releasing the xps13 with ubuntu, that it has the same touchpad, and dell will make the drivers for us :)

Edit: Just tried the new driver for the xps13 

[https://launchpad.net/~kamalmostafa/+archive/dellxps](https://launchpad.net/~kamalmostafa/+archive/dellxps)

Unfortunately it doesn't seem to make a difference on xps15 ivy bridge, I believe it helps the xps15z though!

I just edited my previous post as I actually am able to get the Nvidia graphics card working after all!! nooblette!

---

### Post by katoiam on 2012-08-05
UPDATE:

So I managed (in the end) to get everything but the touchpad working well.

Got the touchpad working after a sort (right click nt working and overly sensitive, when trying to left click mouse pointer often moves off the intended target as the touch pad picks up movement when clicking) by using two finger click to right click and three finger click for middle mouse.

This works but is really frustrating.

I came across this:

[http://ubuntuforums.org/showthread.php?t=1772933](http://ubuntuforums.org/showthread.php?t=1772933)

used this command at the bottom of the page:


echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse


this has allowed right click the touchpad is no where near as sensitive, and now it allows me to have a finger over the click area. How ever it doesn't allow multi finger actions.

The touchpad has disapeard from the settings as well and synaptics crashes when started.

If I/ we could find a way to combine the 2 methods then the mouse would be perfect!!

until then..........

---

### Post by paradoxni on 2012-08-07
Thanks for the update. I have just installed 12.04 on the XPS15 (new) and am having the same problems with oversensitivity.

I can handle two finger tap for right click.

Everything else works perfectly!

---

### Post by katoiam on 2012-08-08
Update:

If you decide to use this:

echo "options psmouse proto=imps"|sudo tee -a /etc/modprobe.d/psmouse.conf; sudo modprobe -r psmouse; sudo modprobe psmouse

be aware that it will stick! I thought after I restarted it would be as it was before, but no.

It seems to stop the (k)ubuntu from seeing the touchpad at all. I now get an error from synaptics when logging in and I can't get it working. The touchpad works as a mouse as I said before right, left click and 1 finger touch, but no multi finger touch!!! It is more useable like this, but no 2 finger scrolling etc, is a bit annoying.

If anyone has anything to add or to help would be muchly appreciated.

paradoxni:

Glad to hear some one else has this computer, the more of us trying and searching for a solution, hopefully, the quicker we will find one :)

---

### Post by katoiam on 2012-08-15
UPDATE: Continued looking for fixes to the touchpad problem.

The one mentioned above, was a start, but causes synaptiks to tink I don't have a touchpad, so no multitouch gestures.

Found another fix:

Here is what I did:

1. Create 51-clickpad.conf in /etc/X11/xorg.conf.d directory. Note that xorg.conf.d directory did not exist for me on 12.04 as it did in previous versions so I had to make the directory.
2. Put the following lines in 51-clickpad.conf
Quote:
Section "InputClass"
Identifier "Default clickpad buttons"
MatchDriver "synaptics"
Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"

#Next 3 items added just for the HP Mini to better control the clickpad
Option "LockedDrags" "1"
Option "BottomEdge" "4000"
Option "AreaBottomEdge" "4445"

EndSection
3. Logout / Login for changes to take effect.

The SoftButtonAreas fixes the right click. The BottomEdge items mask off the bottom of the clickpad so the button will not act like the rest of the clickpad when dragging your finger on it.

From: [http://ubuntuforums.org/showthread.php?t=1966016](http://ubuntuforums.org/showthread.php?t=1966016) (there is a patch on that page, which really screwed my mouse up and caused it not to be detected at all!)

I still have no middle mouse button.

if you tried the one above the new method won't work unless you remove:

/etc/modprobe.d/psmouse.conf

incase you want to go back to that method after trying the newer one, before you delete it save it as /etc/modprobe.d/psmouse.conf.bak

and when you want to re-instate it:

sudo cp /etc/modprobe.d/psmouse.conf.bak /etc/modprobe.d/psmouse.conf

if any one manages to get it properly working would be muchly appreciated if you could post it up here :)


On another note, my xps15 has a lot of trouble connecting to my wifi, and often can't even see it when other devices can! After doing some more research, it appears that this is a big problem with the xps 15's and possibly 17's as well. There are a lot of angry people on different forums complaining about the wifi issue. It would appear that Dell is aware and trying to re-assure people, quietly, that they are trying to find a fix. People aren't very convinced. It also appears that dell are blaming it on a driver issue, thoug I have the smae problems it both winblows and (k)ubuntu, so......

---

