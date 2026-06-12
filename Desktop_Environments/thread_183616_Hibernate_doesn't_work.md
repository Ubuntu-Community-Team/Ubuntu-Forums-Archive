---
title: "Hibernate doesn't work"
date: 2006-05-28
forum: Desktop Environments
---

### Post by ahaslam on 2006-05-28
Hi,

I have done an on-line upgrade from Breezy to Dapper. 
The hibernate option on the log out screen used to work quite well and very reliably.
Now that I'm using Dapper it doesn't work at all. It shuts down but upon reboot I'm greeted with a pin-striped screen and a locked system. I am am on a laptop and often rely upon this to work properly, can anyone help?

Thanks,
Tony.

---

### Post by GarethMB on 2006-05-28
Were you using an optimised kernal before? Whenever i've dist-upgraded i've had to switch my kernal back to the optimised one to get hibernate to work.

---

### Post by ahaslam on 2006-05-28
[QUOTE=GarethMB]Were you using an optimised kernal before? Whenever i've dist-upgraded i've had to switch my kernal back to the optimised one to get hibernate to work.[/QUOTE]

I was using a 2.6.16 kernel configured for my k7. Hibernating worked with every kernel that I used in Breezy, from 2.6.10-i386 to the one I just mentioned, wether from Ubuntu repositories or self compiled.

---

### Post by tenjin on 2006-05-30
Hi,

I have two machines running Ubuntu (laptop and a desktop) and until recently I had hibernate working perfectly on both.

One of the last update I did to my desktop running Breezy killed hibernate - the machine would never actually power off, and when I forced it found that it hadn't yet hibernated. I have now upgraded to Dapper and the machine now won't get past "mounting root file system" when I boot from the latest 686 kernel but that is a problem posted in another thread.

I then installed (clean) Dapper on my laptop from Flight 7. Hibernate worked fine until I got all the latest updates and then I got the effect described here: it looks like it hibernates properly but when you try to restart all you get is a pinstriped display and a locked up computer.

As I've seen problems with two versions of Ubuntu and on two different machines (desktop has an nVidia card; laptop an ATI card) I assume that this must be caused by a recent update applied to both releases?

Any ideas how I get it working on both machines?

Cheers

D.

---

### Post by jazzgossen on 2006-05-30
Just adding to the choir: I have the exact same problem, too. Hibernate used to work, but hasn't done so now for the last few weeks. I also use the latest k7 kernel from the repositories.

---

### Post by viraptor on 2006-05-30
Just checked - same for me - I can't hibernate. In my case nothing happens when I try to. Any launchpad started?

---

### Post by emrys on 2006-05-30
Same here. No hibernation. Suspending right sometimes but not consistenly.

---

### Post by henriquemaia on 2006-05-30
Well, I have just tested and I have hibernation. I had an issue with Nvidia driver in this last update, but that now is corrected.

---

### Post by jazzgossen on 2006-05-30
Those of you who can use hibernation (without the pin-striped screen problem) - which kernel and which nvidia modules do you use?

Are all of us who have this problem (with a garbled screen when restarting the computer after hibernation) using the k7 kernel?

---

### Post by henriquemaia on 2006-05-30
[quote=jazzgossen]Those of you who can use hibernation (without the pin-striped screen problem) - which kernel and which nvidia modules do you use?

Are all of us who have this problem (with a garbled screen when restarting the computer after hibernation) using the k7 kernel?[/quote] 
My kernel:

2.6.15-23-amd64-k8

My Nvidia drivers are the ones available on the repositories.

I have hibernate.

---

### Post by SleepyZ on 2006-05-30
Same problem here, suspend and hibernate don't work. I'm using the latest k7 kernel. 
I also get the garbled screen sometimes after logging out.

---

### Post by popkid on 2006-05-30
Same problem here in dapper, both hibernate and suspend result in pinstriped locked screen on resume with attendant root filesystem corruption... I've only been using ubuntu for a couple of weeks so can't say whether it's something that has changed recently. 

Dell Laptop with ATI video card (an old one, mach64)

pK

---

### Post by 89c51 on 2006-05-30
did anyone got hibernate to work on Sony vaio S series????

i choose hibernate the computer powers of and when i hit the power button again it just makes a regular startup??

---

### Post by blimpyboy on 2006-05-30
FYI 686 kernel with latest updates as of 30/5 and I get the pin strip affect on reboot.

---

### Post by tenjin on 2006-05-30
Hi,

I have the 2.6.15-23-686 kernel and an ATI video card on my laptop.

Interestingly enough I just tried suspend and that worked. I'll try it a few more times to see if that is consistent performance.

Hibernate still doesn't work though.

Cheers

D.

---

### Post by popkid on 2006-05-30
If I click on hibernate in the GDM login screen (in menu bottom left) I just get a message in red above the login name entry box saying that the entry could not be verified and to enter the data in the correct case...

Hmmmm....

pK

---

### Post by ahaslam on 2006-05-30
Has anyone seen the package in Synaptic called 'hibernete'?
It says that it adds support to your kernel to enable hibernation.

Seeing this, I promptly downloaded & installed it. It had no effect on my system, but has anyone else tried it?

---

### Post by ahaslam on 2006-05-31
[QUOTE=tenjin]Hi,

I have the 2.6.15-23-686 kernel and an ATI video card on my laptop.

Interestingly enough I just tried suspend and that worked. I'll try it a few more times to see if that is consistent performance.

Hibernate still doesn't work though.

Cheers

D.[/QUOTE]

Yes, suspend does seem to work ok. I hope that they sort out the hibernete problem soon, as I find these features important on laptops.

---

### Post by btlee on 2006-05-31
[QUOTE=Anthony Haslam]Has anyone seen the package in Synaptic called 'hibernete'?
It says that it adds support to your kernel to enable hibernation.

Seeing this, I promptly downloaded & installed it. It had no effect on my system, but has anyone else tried it?[/QUOTE]

the package is for suspend2, but as far as i know, dapper does not support software suspend2.
it supports only software suspend.

---

### Post by jazzgossen on 2006-06-09
I still have the same problem. Just thought I would describe in more detail what the symptoms are.

When I boot up after hibernation, I am greeted by a screen with vertical light-coloured stripes. If I press alt+ctrl+F7, however, I get back to my hibernated graphical session. All other terminals F1 - F6 are garbled with vertical stripes. The computer is usable after I have switched to alt+ctrl+F7, but some things don't work reliably. I've had some problems with sound and network connections that go away when I reboot "properly".

Still running kernel 2.6.15-23-k7.

---

### Post by bryanlking on 2006-06-09
Just to add to the misery, I too have a problem with hibernat/suspend.

Both working perfectly on Hoary and Breezy!

Now, when I awaken from hibernate, my machine attempts to start X, but then starts an endless loop of cycling through trying to start - retring to start, etc.

On suspend, it works properly only about 30 - 40 percent of the time.  No rhyme or reason.  Very unpredictable.

During the development stage, Flight 6, stock kernel worked okay.  Flight 7, not at all.  

During Flight 7, I submitted a bug report but apparently, it received no love from developers.

Mine:  Fresh install / IBM-G40 Laptop

BK

---

### Post by russianbandit on 2006-06-09
Same thing here.
The screen is garbled with light stripes.

I'm on Inspiron 9300 with Nvidia card.

Is there any work around at all?

---

### Post by ahaslam on 2006-06-27
[QUOTE=jazzgossen]I still have the same problem. Just thought I would describe in more detail what the symptoms are.

When I boot up after hibernation, I am greeted by a screen with vertical light-coloured stripes. If I press alt+ctrl+F7, however, I get back to my hibernated graphical session. All other terminals F1 - F6 are garbled with vertical stripes. The computer is usable after I have switched to alt+ctrl+F7, but some things don't work reliably. I've had some problems with sound and network connections that go away when I reboot "properly".

Still running kernel 2.6.15-23-k7.[/QUOTE]
After the numerous updates I thaught I'd give hibernation a try again... It's not changed, still greated with a pinstriped screen. I tried your 'alt+ctrl+f7' and that just displayed a black & white garbled mess, while completly freezing the system.

The only way that I can safely recover my system after hibernating is to let it boot to the pinstriped screen and press 'ctrl, alt & f2' type my username, followed by my password, then type 'sudo reboot' followed again by my password. I can't see anything during this, but at leat it reboots the system properly.

I hope this is fixed soon.

---

### Post by tcraver on 2006-06-27
I installed Dapper flight 4 from scratch back in February.  I have an Asus Z91e with Intel everything on it, and dapper is the only linux OS that had drivers for everything (more or less) right out of the box.

Hibernate worked from the beginning and all through the numerous updates during development (sometimes over 150/night). But once I did the dist-upgrade to get to the final release, hibernate stopped.  I'm getting the vertical stripes that others have mentioned.  Kernel is 2.6.15-23-686.

Can any developers shed some light on anything?  Are there certain defaults maybe in /etc/apm or some other scripts that may have to be reverted?

---

### Post by memas on 2006-06-28
Is there a tool that we can see the options we have with acpi?
I mean suspend or hibernate, after how many minutes etc.

---

### Post by yahya.mohamed on 2006-07-28
I am having the same problem, I noticed one thing in my case:
If I hibernate ubuntu and the next time I boot ubuntu then it worls well.
On the other hand, if I hibernate ubuntu then load windows, then after turning off windows I boot ubuntu, then this is when I get this stripped screen and I would have to do a hard reboot.

Can anyone help, If I do not get this fixed I will have to move to SUSE or Fedora!!

---

### Post by mariner09 on 2006-07-28
search for suspend2 in this forum, there's a how-to there that looks promising.

I've ysed suspend2 on fedora in the past with promising results.

I'm using SLED10 right now and it seems like hibernate takes longer than a boot.  I'm about to head back to Ubuntu after finding that post.

---

### Post by GI_Josh on 2007-01-29
I see many people are having this same issue as I.  I'm not using k7, but the other one.  Has this been resolved yet?

---

### Post by bryanlking on 2007-01-30
I've stopped using Ubuntu for the time being and have gone to FC5.  I was having the same problem with hibernation with it as well but installed a package called **acpitool**.

It's a command line tool but it works perfectly!  Every time!!

Install the package and then run as root:  acpitool -s, to suspend the machine.  I'm happy with the results.

BK

---

### Post by GI_Josh on 2007-01-30
Wait, I'm confused.  What do you mean "run as root"?  Also, is suspend the same as hibernate?

---

### Post by bryanlking on 2007-01-30
In Ubuntu, you have to run it with the sudo command
$ sudo acpitool -s.

To suspend is to save the current state of your desktop to RAM.  That means it'll be faster to restart your session but it will use a small amount of battery power to maintain.

To hibernate is to also save the current state of your desktop but will write it to disk.  When machine is powered on, it will read from that saved information to restart your session.

The -s option on the above command puts the machine into suspend mode.  I prefer the state of suspend and have not used hibernate.

BK

---

### Post by ahaslam on 2007-01-31
**Has this not been sorted yet?**

Did anyone else loose their swap after attempting hibernation, having to use mkswap?

To anyone who had this problem & now runs Edgy, does it work in Edgy?

A previous post mentioned that it was submitted to Launchpad with no response. I can't find it, does anyone want me to post with a link to this thread?

Tony ;)

---

### Post by GI_Josh on 2007-02-08
UPDATE:

Acpitool won't even suspend my laptop.  I have tried many times, and it suspends correctly, but then my computer won't resume.  I am WAY lost here.

---

### Post by NJC on 2007-03-08
Using 6.06 Hibernate does not work ... I am unfamiliar which kernel I am using but machine is PIII/550Mhz HP. Actually Hibernate performs very oddly: Sometimes it invokes screensaver; other times it blanks screen for a few seconds, then prompt window appears asking me for password to unlock screen (and I don't have that option configured). 

Suspend (or whatever it's called) doesn't work in Win98 on this machine either but I thought it was from buggy software. :mrgreen: 

I haven't tried Suspend yet.

---

