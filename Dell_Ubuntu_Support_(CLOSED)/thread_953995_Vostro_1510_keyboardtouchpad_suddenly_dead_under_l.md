---
title: "Vostro 1510 keyboard/touchpad suddenly dead under linux..??"
date: 2008-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hallenberg on 2008-10-20
Hi.. Apologies if this problem has been answered elsewhere but I've been googling for several hours without joy - I cannot find any other post that describes my predicament.

In short my problem is that the keyboard & touchpad on my Vostro 1510 have inexplicably stopped working under anything but Windows..

The laptop tri-boots Ubuntu, XP and Vista; I set this up several months ago and it's all been working fine. Then yesterday I performed several updates in Ubuntu; everything was STILL FINE after several reboots. So I went and had some dinner, came back, booted into Windows for a few hours to play with music software and feed my delusion that I can still be a rock star.. Then I woke up and rebooted into Ubuntu...but I find I can't login because my keyboard isn't working; and neither is the touchpad..

I get x and gdm out of the picture by rebooting into single mode; I find that the keyboard won't even work in console. So then I tried booting the previous kernel to gui and console - but I get the same result..

USB mouse and keyboard work ok so I logged in using those and checked the system logs for clues, but I didn't see anything obvious. So I googled and tried various things but no joy. The reason I'm skimming here is because...I then tried booting Knoppix, and to my surprise I got the same thing - the keyboard and touchpad don't work under Knoppix now either. WTF? Now I'm getting concerned..

Ok so the keyboard works at bios, and at grub, no worries. Beyond that, it's Windows only. 

For info, here are the changes I made in Ubuntu just prior to the problem arising.. Firstly I let the package manager perform all its recommended updates (including kernel update from 2.6.24-19-generic to 2.6.24-21-generic), and I rebooted (with new kernel), no problem. Then I went surfing and noticed that Sun had updated VBox, so I wanted to update that on my machine too. I followed their suggestions at [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) and I installed dkms before updating VBox via apt and their repository. Again no apparent problem. And that's it..

What the hell has happened that I now can't even get the keyboard or touchpad to work under Knoppix??

Any help appreciated; thank you..

---

### Post by hallenberg on 2008-10-22
In today's episode I find that I can get linux to pick up the keyboard and touchpad if I jump up and down on the keys continually during boot-up...although it has to be keyboard keys; tapping or rubbing away at the touchpad or its buttons during boot-up has no effect. Setting numlock on by itself doesn't do the trick either, by the way, but the behaviour of its LED might give some clues, I don't really know.

So my problem is now manageable but still basically unresolved - the laptop is pretty new, I'll be fecked if I'm going to accept having to bash away at the keyboard on every boot.

My gut feeling points to a minor hardware glitch; one that bothers linux but not Windows. Otherwise it seems pretty weird that the problem arose in both ubuntu AND knoppix simultaneously..? My utterly ignorant theory is that keyboards are designed to respond in particular ways when they are queried in a passive state by the OS...and that my keyboard has somehow lost its ability to respond in the way linux (in particular) expects..? Any thoughts?

..Or is this going to be a one-man affair? \\:D/

---

### Post by insomniacity on 2008-11-08
I'm getting precisely this issue on precisely this model of laptop - started this morning. You are not alone!

The workaround works for me too.

Did you get anywhere with fixing it? Does anyone else have any ideas?

---

### Post by insomniacity on 2008-11-08
OK - I have a proper fix, even if I don't understand how it works or why it broke.

In short: add i8042.reset to your kernel parameters.

In long:

1. Backup your /boot/grub/menu.lst somewhere else, possibly off the machine?
2. Run: ```
sudo nano /boot/grub/menu.lst
```, and enter your password when requested. Obviously, you can use whatever editor you like.
3. Find the line beginning *# kopt=*. **Don't remove the #.**
4. Add ```
i8042.reset
``` to the end of the line, so that your final line looks something like:
```
# kopt=root=UUID=c10a4641-f9b2-8b06-7127-bb1ba1fe45d4 ro i8042.reset
```
5. Save the file.
6. Run ```
sudo update-grub
```

Now, that option should be automatically added to whatever kernel you boot. I hope this helps somebody.

---

### Post by hallenberg on 2008-11-08
Hey, fine work :) As it happens my issue disappeared with a clean install of ubuntu 8.10 but I will surely keep your fix in my pocket.

---

### Post by LeDmagNeT on 2009-07-17
I had the same problem with Kubuntu 8.10 with the Dell Vostro 1510.

Installing 9.04 or Debian Lenny did not fix it.
Problem also affected the setup process where I had to use an external mouse & KB to complete installation.

Thanks for your post as this has solved the problem for me too :)

I found that this relates to Ubuntu Bug #341094

---

### Post by homeblend on 2009-07-27
[insomniacity]("http://ubuntuforums.org/member.php?u=613399") is a genius - had this problem (many years on) and this patch seems to have fixed it! FTW! 

:popcorn:

---

### Post by Wilbefast on 2009-08-10
I have the same problem - however if you plug it in and charge it up fully it will pick up the keyboard... sometimes, so you just need to turn it on and off until it does ;) I'll try your (more sensible fix)
Was just about to post this as a new thread actually - and seems a shame to waste my draft, so here it is:
 
 
*subject: Vostro 1510 - keyboard/mouse not detected*
 
*Just put Ubuntu on my laptop and having wee bit of trouble with the keyboard and touch-pad :confused:*
 
*If I boot the it up and it's **not** plugged in then Ubuntu will not pick up the keyboard or touch-pad (I've checked and the keyboard works with the BIOS every time) - the only thing I can do is to turn it off and back on again. It WILL pick up a USB mouse if I plug that in, but unfortunately I have no other keyboard, and the whole point of a laptop is that you can use it, well, as is, _without_ peripherals :(*
 
*If the laptop** is** plugged in and fully charged up then it will only mostly not pick up the keyboard, so I just turn it off and back on again until it does. Once the keyboard and mouse have been detected it runs fine, no problems with keyboard or touchpad, and I can unplug it and carry it around or whatever, the only problem being that if I turn it off again I won't be able to use it until I've found a power point and recharged it fully, and even then only if I get lucky!*
 
Hope this works :S
 
 
William
 
 
edit: Hell yeah - it works! Huzza! Cheers man.
 
Nano's too restro for me :S I used "sudo oofice -writer". Do you know what the code is for the normal text editor?


edit2: hmm - seems I spoke too soon: it will now sometimes pick up the keyboard when unplugged some of the time, but still sometimes doesn't :-S

---

### Post by Wilbefast on 2009-08-12
Yeah, the fix definitely isn't working for me - I'm bumping this because, well, it's bloody inconvenient :(

---

### Post by gordonh on 2009-08-14
> **Wilbefast said:**
> 
Nano's too restro for me :S I used "sudo oofice -writer". Do you know what the code is for the normal text editor?
ome of the time, but still sometimes doesn't :-S

sudo gedit

---

### Post by yelirekim on 2009-08-23
Had this exact same problem, just chiming in to say thanks :)

Does anyone know exactly why this works?

---

### Post by Wilbefast on 2009-09-04
Dang - well this fix seems to be working for everyone else... I'll try again, see if I can't get it to work for me. One of the bug report pages suggest you also add i8042.nomux, i8042.nopnp and i8042.noloop - worth a shot - the line should look like this anyway:

```

# kopt=root=UUID=be684e00-93b8-4263-8598-c1b7a66918a1 ro i8042.reset i8042.nomux i8042.nopnp i8042.noloop
```Wish me luck :o

William


EDIT: Awesome! It works all the time now (or so it seems) I think I may have forgotten to update the widget having edited the doobidacka - my bad.


Willliam

---

### Post by overflyer on 2009-09-26
Hi guys,

I know that this works because Ive tried it with the "old" Grub already and I was very happy. But Karmic now uses grub2 and I dont know in what file at which line I have to add  i8042.reset i8042.nomux i8042.nopnp i8042.noloopf to make my keyboard & touchpad work again.

Could somebody tell me where I have to add it.

Thanks a lot

Greetz
over

---

### Post by grover66 on 2009-10-27
modify /etc/default/grub;

edit the line;

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"

(all one line)

then run;

update-grub

Cheers,

Mike :)

---

### Post by orawax on 2009-11-06
> **overflyer said:**
> But Karmic now uses grub2 and I dont know in what file at which line I have to add

You should add custom boot options to /etc/grub.d/40_custom
and then run *sudo update-grub2*

See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Although for some reason i got the error 'unknown option: i8042...' or something like that at boot now...

---

### Post by TDK800 on 2011-04-10
Thank You!!!

Dell Vostro 1510, seems that this problem still exists on Ubuntu 10.10 and Ubuntu 11.04 Beta.

---

### Post by syed.rakib.al.hasan on 2011-05-06
> **TDK800 said:**
> Thank You!!!

Dell Vostro 1510, seems that this problem still exists on Ubuntu 10.10 and Ubuntu 11.04 Beta.

my Dell Vostro 1510 touchpad has been fine until upgrade to 11.04........ could u solve it????

---

### Post by justb13 on 2011-07-31
Just chiming in to add a note :
Environment : Ubuntu 11.04
Machine : Vostro V13 64 bit

I found that when I tried to reboot from a 'hibernate' state, my touchpad was not being detected. 

The following two commands in the terminal window got it working everytime :

```

$ sudo rmmod psmouse
$ sudo modprobe psmouse

```

Hope this helps someone out there..

---

### Post by syed.rakib.al.hasan on 2011-07-31
> **justb13 said:**
> ```
$ sudo rmmod psmouse
$ sudo modprobe psmouse
```

i have tried this..... here is what my command returned.
```
rakib@rakib-laptop:~$ sudo rmmod psmouse
[sudo] password for rakib: 
ERROR: Module psmouse does not exist in /proc/modules
```

---

