---
title: "no wireless in dell inspiron 1520 with 12.04"
date: 2012-05-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RedDriscoll on 2012-05-05
I am brand new to ubuntu and I just installed 12.04 on my dell, had winxp before and the wireless worked just fine.

I was reading other posts with solutions like uninstalling the preset drivers and everything but didn`t work so i decided to post.

lspci -nn | grep 0280 output was

```
0c: 00.0 network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
```

---

### Post by nm_geo on 2012-05-05
Red,

Do you have access to working ethernet cable?

If you do we can get it up with Synaptic Packager or terminal
commands..
If not there are other ways... I can even drop a file here and we can walk you though the installation.

---

### Post by RedDriscoll on 2012-05-05
I don`t have ethernet connection with that laptop, but installing that file you say sounds good

It would be deeply appreciated, thank you.

---

### Post by nm_geo on 2012-05-06
Okay here is the b43.zip folder You can put it on a flash drive and then plug in the flash drive in the laptop.  Extract the b43 folder to the Desktop.

Open a terminal
```
cd Desktop
``` 
```
ls
```

Those will get you to the Desktop and ls will show the b43 folder

In terminal 

```
sudo mv b43 /lib/firmware
```

That will move the b43 to the correct directory.

Hopefully in a few seconds your wifi light will come on,  Sign in to your wifi access point.

---

### Post by RedDriscoll on 2012-05-07
I followed the steps you posted and moved the b43 folder but there has been no change.

Did a couple of reboots too, turned the WiFi switch on and off but nothing 

Am I missing something there?

---

### Post by nm_geo on 2012-05-07
When you extracted the b43.zip to Desktop a folder appeared b43 correct?
When you did the sudo mv b43 the folder left the Desktop correct?
Be sure the folder b43 is now in /lib/firmware.

In terminal try 

```
sudo modprobe b43
```

That should give the b43 a kick to get going. If it does not reboot with wifi we 
might have a blacklist problem.

Did you try the STA driver before?   

Be sure wifi switch is on

```
rfkill list
```

and 

```
lsmod
```

That will tell us if the b43 module and the ssb are loading and might show if a conflict exists.

If all this does not get it the Networking/Wireless Forum is a great resource.  I used to hang there myself.

---

### Post by pablo180 on 2012-05-07
Had the same problem with the Inspiron 1525, till I realised that the hardware switch has to be ON at boot time, otherwise I had no wireless at all, even after turning it on and there seems to be no way to get it back from within Ubuntu without rebooting.

In other versions of Ubuntu you could turn the switch on at any time, not with 12.04. Now I have to make sure the switch is on before I hit the power button. 

You may have already tried that, but though I should mention it, just in case

---

### Post by rafo2001 on 2012-05-07
Thanks a lot!
This works perfect for me, after the modprobe.
Dell Inspiron 1501

Thanks again.

---

### Post by RedDriscoll on 2012-05-08
It is working now!! I checked for the b43 in the folder

Exactly the same for me, after modprobe it worked beautifully.

Absolutely true about the hardware switch has to be ON  at startup, otherwise wont work until reboot

thank you very much, I've learned a lot

---

### Post by nm_geo on 2012-05-08
> **RedDriscoll said:**
> It is working now!! I checked for the b43 in the folder

Exactly the same for me, after modprobe it worked beautifully.

Absolutely true about the hardware switch has to be ON  at startup, otherwise wont work until reboot

thank you very much, I've learned a lot

I am glad it all worked out for you Red.  I was a little worried about the wifi working after a reboot but that would be another issue.  Just as an aside, I had another thread on here that talks about keeping the b43 on a thumb drive for later use you might look through it for the future.

[http://ubuntuforums.org/showthread.php?t=1974013](http://ubuntuforums.org/showthread.php?t=1974013)

---

### Post by Raf33k9 on 2012-07-13
thank u all ... u guys saved me... i had a same problem for couple of days. though mine was dell inspiron 1525. but it worked like a magic. thanks again.

---

### Post by Pinco PallinoUb on 2012-07-29
works fine for me after modprobe, thanks!!!! (inspiron 1501 w/ Ubuntu 12.04) :KS

---

### Post by sadsatan on 2012-08-16
Dell 1520 works fine from the first tutorial. Many thx:guitar:

---

### Post by camel325 on 2012-08-17
same problem for me on 1520, this sorted it right out. thank you so much!

---

### Post by djjoker on 2012-08-26
Add another thanks to the list for getting this Inspiron 1520 connected :)

---

### Post by gunter1959 on 2012-08-29
It also fixed my Acer5310 after upgrading from 10.04 to 12.04.  THANKS!

---

### Post by paulwithap on 2012-09-26
b43 fix worked for my Inspiron 1520!

---

### Post by grendelpz on 2012-10-02
Excellent! Thanks for the file and advice to turn on wifi :guitar:

---

### Post by agkforever on 2012-11-18
thanx
it works perfectly  on dell 1525

---

### Post by jshonk on 2012-11-19
this worked perfect for me, Dell inspiration 1520

---

### Post by BlackhorsePB on 2012-12-02
Seems to be a very popular post - worked on my (newly) installed ubuntu. Many thanks

---

### Post by jerrt on 2012-12-03
going to try this on my 1525 tonight. Glad to have such great help.

strange thing was when I originally installed 12.10 the wifi worked. after the built in update did its things the wifi didn't even show up.

*****update***** [[played to unsolved mystery theme music]]
This thread fixed my problem as well. Great help!  [:

I did have to gedit /etc/modules and add the line "b43" to make it take action on reboot.  Just wanted to put that out there.

---

### Post by vitormiran on 2013-04-03
Wow, thank you very much for your help. I've tried to solve this problem in my Dell Inspiron 1525 in some different ways but I couldn't manage to turn on the wireless device. I was just wondering why the solution indicated throught Ubuntu (using the Additional Drivers functionality) didn't worked. Everytime I've tried to download and install the driver using that screen, I've got this error:[SIZE=2][“Sorry, installation of this driver failed.  Please have a look at the log file for details: /var/log/jockey.log.”]("http://askubuntu.com/questions/102334/sorry-installation-of-this-driver-failed-please-have-a-look-at-the-log-file")[/SIZE]

Thanks.
Vitor Miranda.

---

### Post by Lincinas on 2013-04-09
I was unable to fix wireless network issue for several days. But these recommendations worked like a charm! Thanks for a good post.

Regards
Linas Bartkevicius

---

### Post by Implactus on 2013-05-08
Hi Im quite new to Linux and not really a programmer.
I have installed Ubuntu 12.04 on to a fresh hard disc on a Inspiron 1501 laptop.
No matter what I do I can't seem to get the wireless network card to work and when updated the ethernet port doesn't even initialise.:confused:
I have tried to repeatedly to move the b43 file to the lib/firmware directory with the terminal commands posted above.
When I input the mv b43 lib/firmware command I get this output.
mv: cannot move `b43' to `/lib/firmware/b43': Directory not empty

Does this mean that the file already exists at this location or does it mean the hardware is not responding.
When I revert to an earlier distro I can get the Ethernet port working but on the update it doesn't see the port? 
I have spent several hours trying to get the wireless working and still no joy hence this post.](*,):cry:

---

### Post by J3rH8tr on 2013-10-26
Hi Guys,

Today is fourth day when I try to turn on wifi on Dell insprion 1520. I've used file b43 and followed after instruction. I've reboot laptop a few times. When I've put "[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe b43" terminal was empty next 2 h and [/FONT][/COLOR]nothing happened. Whan can I do more? I'm new in Ubuntu - please help me? Cheers

---

### Post by J3rH8tr on 2013-10-26
done jupi

---

### Post by zKhtdyX on 2013-10-31
> **J3rH8tr said:**
> Hi Guys,

Today is fourth day when I try to turn on wifi on Dell insprion 1520. I've used file b43 and followed after instruction. I've reboot laptop a few times. When I've put "[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe b43" terminal was empty next 2 h and [/FONT][/COLOR]nothing happened. Whan can I do more? I'm new in Ubuntu - please help me? Cheers

Please post the output of the following after you have rebooted you pc (please use code-tags):
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
dmesg | grep 'b43\|wlan'

```

---

### Post by derfettesveeen on 2014-01-09
Hello nm_geo,

thank you a lot for this advice! 
Even in 2014 this is still helpful!

Greetings,
Sven

---

### Post by dreamastermind on 2014-01-23
I also cannot get my wired internet going on my Dell Ispiron 1520 after I just updated to 12.04.  I followed the instructions listed in this thread but I'm also have the error where it says "cannot move 'b43' to '/lib/firmware/b43':  Directory not empty.

I rebooted the computer, copy and pasted this into terminal...

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
dmesg | grep 'b43\|wlan'

I then hit enter and it came up with a bunch of stuff, but nothing changed.

What am I doing wrong?  Please help cause I've been trying to fix this all day!  :(

---

### Post by steven30 on 2014-04-09
Will b43 work for me? I have a dell inspiron b120. I recently replaced my win xp with ubuntu 12.04.  I get wireless fine in my home (I can even see some of my neighbor's ssid), but I went to a couple coffee houses and do not receive a signal there. Before I follow this procedure, can someone encourage me that it will work?

---

### Post by varunendra on 2014-04-10
What will or won't work for you can be told only after knowing which wireless card you are using.

Better start your own thread, and post the result of "wireless_script" in it which you can find in the "Wireless Script" link in my signature (with instructions).

---

