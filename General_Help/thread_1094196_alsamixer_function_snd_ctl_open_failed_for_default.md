---
title: "alsamixer: function snd_ctl_open failed for default: No such file or directory!"
date: 2009-03-12
forum: General Help
---

### Post by tombom62 on 2009-03-12
no sound.  i have a ac 97 card and here's what it says when I try and open alsa mixer
> 
owner@ubuntu:~$alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

What is going on?  I can give any extra info, I JUST REALLY NEED SOUND!  HELP!!!!!!!!!!!

---

### Post by tombom62 on 2009-03-12
(bump)

---

### Post by Neo_The_User on 2009-03-12
Is that the entire error? If so, it looks like a problem with the source code. I can help you indeed. Just feed me all the problems you have with this and I will write up a deep in depth HOWTO on how to fix it for you right here. Don't say I didn't try and help.

---

### Post by tombom62 on 2009-03-12
THanks so much!  So, basically, I have gone to synaptic and installed every damn alsa(ish) package there.  I tried running the alsamixer, and all.  It gave me that weird error.  I also noticed I do not have a /dev/snd folder.  I found somewhre that said to do in terminal:
chmod 777 /dev/snd/*
 or something.

that didn't work, tried with and without sudo.

Also tried a package from realtek... here is the linnk:
[http://www.realtek.com.tw/downloads/ExpressFTPSite.aspx?DownTypeID=3&DownID=8&PFid=23&Conn=3](http://www.realtek.com.tw/downloads/ExpressFTPSite.aspx?DownTypeID=3&DownID=8&PFid=23&Conn=3)

for my ac 97.
actually before i installed that the output sound worked, but input didn't.  now nothing works.  I can give more info.  I am using a dell 2400 with 1 gb ram, intrepid with fluxbox.

thanks,
tombom:popcorn:

---

### Post by Neo_The_User on 2009-03-12
Hmm. Try running a different kernel from the GRUB boot loader menu.

---

### Post by Elfy on 2009-03-12
The first thing you need to is find if the soundcard is actually being recognised now

```
lspci | grep audio
```

If that is ok 

```
aplay -l
```
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by tombom62 on 2009-03-12
> **Neo_The_User said:**
> Hmm. Try running a different kernel from the GRUB boot loader menu.
Whitch one?

> he first thing you need to is find if the soundcard is actually being recognised now

Code:

lspci | grep audio

If that is ok

Code:

aplay -l

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

here's my terminal:

> owner@ubuntu:~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
owner@ubuntu:~$ aplay -l
aplay: device_list:215: no soundcards found...
owner@ubuntu:~$ 



thanks,
tombom

---

### Post by Neo_The_User on 2009-03-12
yeah its a kernel issue.

compile one or choose ANYTHING different. it doesn't matter as long as you don't choose the server kernel jajajaja.

---

### Post by Elfy on 2009-03-12
> **tombom62 said:**
> Whitch one?
here's my terminal:
thanks,
tombom

Hi if using a different kernel doesn't work - you can work through the steps on the troubleshooting guide.

---

### Post by tombom62 on 2009-03-12
> **Neo_The_User said:**
> yeah its a kernel issue.

compile one or choose ANYTHING different. it doesn't matter as long as you don't choose the server kernel jajajaja.
ok, is this a good guide for compiling a new kernel? [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)
I just wanna check cause I don;t want to mess up my system.

---

### Post by Neo_The_User on 2009-03-12
much rather you use the official one.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

Much suited for beginners

---

### Post by tombom62 on 2009-03-12
ok. I will give it a go.:popcorn:;)  Be back in a while, unless my computer blows up in the process.

---

### Post by Neo_The_User on 2009-03-12
> **tombom62 said:**
> ok. I will give it a go.:popcorn:;)  Be back in a while, unless my computer blows up in the process.

hahahaha!!!! good luck.

---

### Post by roger_1960 on 2009-03-12
Hi

I had **exactly** the same errors with 8.04 64bit after trying to install Flash 10.  I eventually solved it by a complete reinstall of Ubuntu (of 32 bit 8.04.2  - for various other reasons as well as curing this problem) which I'm sure was overkill!

---

### Post by Neo_The_User on 2009-03-12
> **roger_1960 said:**
> Hi

I had **exactly** the same errors with 8.04 64bit after trying to install Flash 10.  I eventually solved it by a complete reinstall of Ubuntu (of 32 bit 8.04.2  - for various other reasons as well as curing this problem) which I'm sure was overkill!

hahah yeah it was overkill

---

### Post by Yellow Pasque on 2009-03-12
Compiling a kernel to fix a sound problem is also overkill.

Neo_The_User: Is there any sort of filter between your brain and the keyboard? Sorry, but it just seems like you're posting as fast as possible without actually **thinking**. Too much Adderall today?

---

### Post by Neo_The_User on 2009-03-12
> **Temüjin said:**
> Compiling a kernel to fix a sound problem is also overkill.

Neo_The_User: Is there any sort of filter between your brain and the keyboard? Sorry, but it just seems like you're posting as fast as possible without actually **thinking**. Too much Adderall today?

I have experience with this sorta thing. Either the ALSA module for the sound card isn't properly being loaded by the kernel or its the common gstreamer error. Please see this thread for evidence that my theory is correct (in your face)

[http://ubuntuforums.org/showthread.php?t=1092669](http://ubuntuforums.org/showthread.php?t=1092669)

Try verifying my information is incorrect before saying I'm wrong. Sometimes depending on the problem, gstreamer won't display the error but its still there.

---

### Post by Yellow Pasque on 2009-03-12
> Either the ALSA module for the sound card isn't properly being loaded by the kernel or its the common gstreamer error
Ok, but even if one of those is the cause of the problem, you shouldn't jump to conclusions. Furthermore, why would you instruct naive users to compile a new kernel?
Building ALSA using a script would be a better (but still drastic) option: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

How about if we slow down and get some output from the user to see what the problem actually is before sending the user on a wild chase to do something that probably won't solve his problem?

tombom62 - can you post the output of:
```
sudo lshw -C multimedia
```

---

### Post by Neo_The_User on 2009-03-12
<Bip Bip>

---

### Post by tombom62 on 2009-03-12
OK -- here is the output:
> owner@ubuntu:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0


---

### Post by tombom62 on 2009-03-12
> **Neo_The_User said:**
> It probably will solve his problem Mr. Knowitall. Just because you have over 3,000 posts doesn't mean your god.

-- I think it did actually solve my probelm.  I found out i did have anothyer older kernel, booted it, and I think I have sound!  I am going to go to youtube and check.

---

### Post by tombom62 on 2009-03-12
ok, it doesn't work.  BUT, it seems to know I have a sound device , and alsamixer DOES work, so I am getting somewhere I think.  Thanks for all the help thus far!;)

---

### Post by tombom62 on 2009-03-12
bump/pointing out

I can control the "volume" but nothing out of the speakers.  I can also record with audacity.  I don't know what the probelm is but it seems to now recognise my card!  I htink I am getting somewhere.  any suggestions on why it's not working still?

---

### Post by Neo_The_User on 2009-03-12
ah see! I knew we were heading somewhere!

---

### Post by Yellow Pasque on 2009-03-12
> **Neo_The_User said:**
> Just because you have over 3,000 posts doesn't mean your god.
*you're
and FYI, my post count has no correlation to what I post. I don't put any stock in that number. You, on the other hand, seem to be posting as many short, thoughtless, posts as possible to increase your post count.

---

### Post by Neo_The_User on 2009-03-12
> **Temüjin said:**
> *you're
and FYI, my post count has no correlation to what I post. I don't put any stock in that number. You, on the other hand, seem to be posting as many short, thoughtless, posts as possible to increase your post count.

I kan spll jus fine

---

### Post by tombom62 on 2009-03-12
> **Neo_The_User said:**
> I kan spll jus fine

you remind me of me. i aslo cun spl jus fin.
> ah see! I knew we were heading somewhere! 
yes, we are.  I wonder what;s going on now...

---

### Post by tombom62 on 2009-03-12
I had the cord in the wrong port.  but it still doesn't work. I think that'd have been a probelm, but I know it didn't really work at all, as I hage headphones too and they were in the right port.  same deal, not working, but pretending it;s working and almost working.:popcorn:

---

### Post by tombom62 on 2009-03-12
and just a side note:  I haven't solved my problem if that wasn't clear.  I have confermed that what I did didn't ruin anything and it was never working.  So, i am still at the position of my sound "pretending to work"

---

### Post by Elfy on 2009-03-13
Then I suggest you go back to the link I gave you and start working through it. 

It looks a lot more complicated than it actually is.

Edit - I just found the lshw output - so the card is recognised now it seems, if

```
aplay -l
```

gives you an output this time I would use alsamixer to increase all the channels, if a channel is muted - M to unmute

```
alsamixer
```

If that only gives you the simple pulseaudio channel then

```
alsamixer -Dhw
```

Edit edit - Instead of adding new posts when others haven't answered it would be better to edit posts and append the new information, less chance of people missing information amongst posts.

---

### Post by tombom62 on 2009-03-13
> Then I suggest you go back to the link I gave you and start working through it.

It looks a lot more complicated than it actually is.
K, I will give that a go.

> Edit - I just found the lshw output - so the card is recognised now it seems, if

Code:

aplay -

gives you an output this time I would use alsamixer to increase all the channels, if a channel is muted - M to unmute

Code:

alsamixer

If that only gives you the simple pulseaudio channel then

Code:

alsamixer -Dhw


OK,  aplay - didn 't give output this time, it just held still, and acted like it would do something, but never did.
the alsamixer levels are all up as far as they can be, but the "Sterio mix" won't go up at all.
alsamixer -Dhw seemed to do the same thing as regular alsamixer.

> Edit edit - Instead of adding new posts when others haven't answered it would be better to edit posts and append the new information, less chance of people missing information amongst posts.
sure.  I will do that I suppose.

thanks,
tombom:popcorn:;)

---

### Post by tombom62 on 2009-03-14
(bump)

---

### Post by Elfy on 2009-03-14
Did you work through the troubleshoot guide I linked to - if you did and you got problems then we need to know what they are.

If you haven't yet then can you.

---

### Post by tombom62 on 2009-03-14
I did try them, but one of them wanted to remove "ubuntu-desktop" and I don't want to risk it.  And no the sound isnt working now.

---

### Post by Elfy on 2009-03-14
ubuntu-desktop is a metapackage - it's safe to remove it - I have done on more than one occasion - think of it as a box with things inside, you take the box away and leave the things.

As far as the sound goes - you need to work with the wiki or sound troubleshooting threads there are and give some feedback with where it fails and the messages you get.

---

### Post by tombom62 on 2009-03-15
OK.  I did infact remove it and nothing bad happened, but sadly, nothing good happened either.

---

### Post by tombom62 on 2009-03-16
(bump)

---

### Post by Elfy on 2009-03-16
```
lspci | grep audio
```

```
aplay -l
```

Can you run these again please, we need to know if the second results in

no soundcard found...

---

### Post by tombom62 on 2009-03-16
alright, here's my konsole:
> owner@ubuntu:~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
owner@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Elfy on 2009-03-17
Try opening alsamixer from the terminal again ```
alsamixer
```
look for external amplifier or external - if it is there, does it show MM underneath? If it doesn't use m to toggle that and see if you have sound.

---

### Post by LiamWilson on 2009-03-17
> **tombom62 said:**
> no sound.  i have a ac 97 card and here's what it says when I try and open alsa mixer


What is going on?  I can give any extra info, I JUST REALLY NEED SOUND!  HELP!!!!!!!!!!!

You know, I had the same problem with mine. after 2 years, I ended up buying a new sound card.

[http://www.play.com/PC/PCs/4-/3436355/Trust-SC-5250-5-1-Surround-Sound-PCI-Card/Product.html](http://www.play.com/PC/PCs/4-/3436355/Trust-SC-5250-5-1-Surround-Sound-PCI-Card/Product.html)

But after all this tinkering, It most possibly wont work, and may requre a re-install with Ubuntu. but it should work out of the box after that.

---

### Post by tombom62 on 2009-03-17
> Try opening alsamixer from the terminal again
Code:

alsamixer

look for external amplifier or external - if it is there, does it show MM underneath? If it doesn't use m to toggle that and see if you have sound.
There's only one thing, Master.  Here's a screenshot attached.
> 
You know, I had the same problem with mine. after 2 years, I ended up buying a new sound card.

[http://www.play.com/PC/PCs/4-/343635...d/Product.html](http://www.play.com/PC/PCs/4-/343635...d/Product.html)

But after all this tinkering, It most possibly wont work, and may requre a re-install with Ubuntu. but it should work out of the box after that.
hmm.  I might just buy a new one, but I hope I can get it.  did that one give you sound out of the box?

thanks,
tombom:popcorn:

---

### Post by Elfy on 2009-03-17
Ok no screenshot but I am guessing that it says it is the pulseaudio controls - use 

```
alsamixer -Dhw
```

Hopefully that will get the controls for the intel sound card, then look for external again

---

### Post by tombom62 on 2009-03-17
oops!  Here's a shot. and adding the dhw gave me more controls, as I used to have.  it doesn;t let me turn external up. it just says 00

---

### Post by Elfy on 2009-03-17
Go to the external amplifier channel and then use m to mute it see if that works.

I did already write that in a previous post ;)

If that doesn't do it then I can help no further and you are going to have to work through the troubleshoot guide - also search the forum for your sound card - the intel number you gave earlier.

Good luck

---

### Post by tombom62 on 2009-03-17
if i push m, it changes from 00 to mm and I guess that means it's muted. I suppose external is the [most] important one, right? I guess i will finish through the troubleshooting guide now.

---

### Post by LiamWilson on 2009-03-17
> **tombom62 said:**
> There's only one thing, Master.  Here's a screenshot attached.

hmm.  I might just buy a new one, but I hope I can get it.  did that one give you sound out of the box?

thanks,
tombom:popcorn:


Yeah, it worked perfectly out of the box. If not, it will definately work after a re-install, or with undoing anything you have done.

Say, may I ask, what make is your PC?

---

### Post by tombom62 on 2009-03-17
it's a dell dimension 2400.  [link]("http://reviews.cnet.com/Dell_Dimension_2400/4505-3118_7-30824846.html") only upgraded hdd and 1 gb of ram

---

### Post by tombom62 on 2009-03-17
oh and i went through the sound troubleshooting and no luck.  about the upgrade script though... how do I do that?  I didn't really understand...

---

### Post by mc4man on 2009-03-17
have you tried killing or removing pulseaudio and see if you can get anywhere? (both actions easily restored
(run alsamoxer after killing, see if your card is shown, preferences ->sound, ect. ect.

to kill
pulseaudio -k

to restore
pulseaudio -D

to remove search libpulse in synaptic and remove libpulsecore5 (several others will also be removed

to undo the above simply install libpulsecore5 (will also install everything that was removed

---

### Post by tombom62 on 2009-03-17
konsole:
```
owner@ubuntu:~$ pulseaudio -k
W: ltdl-bind-now.c: Failed to find original dlopen loader.
owner@ubuntu:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
owner@ubuntu:~$ alsamixer
No mixer elems found

owner@ubuntu:~$

```
so it seems I just ruined alsamixer.

---

### Post by Neo_The_User on 2009-03-17
sorry I should have told you not to do that. Now something new just broke. The best thing to do when somebody tells you a terminal command, wait for somebody else to post. I would've said "don't do that" but too late. mc4man, since your advice got him in this situation, try teaching him how to fix it. I'm not getting involved in somebody else's wrong advice, no offense. I meant that is the nicest way possible, seriously.

---

### Post by tombom62 on 2009-03-17
uh oh... I will google while I wait for mc4man.

---

### Post by tombom62 on 2009-03-18
(bump)

---

### Post by Neo_The_User on 2009-03-20
Hmmm.... well if he isn't going to respond, and I don't know how to undo... i'm going to say it... stupid. commands.

I just contacted m4pacman or whatever.

---

### Post by tombom62 on 2009-03-20
> **Neo_The_User said:**
> Hmmm.... well if he isn't going to respond, and I don't know how to undo... i'm going to say it... stupid. commands.

I just contacted m4pacman or whatever.

I hope I can fix it soon.  I might just fresh install hardy, I'm getting a new hard drive, so... maybe.  I think that this has been around so long it;s not gonna be solved soon.  Thanks for all the help though!

tombom:popcorn:

---

### Post by Neo_The_User on 2009-03-21
or switch to Debian sid. I'm waiting for 9.04 because that has later packages than any other distro. More devel support!

---

### Post by orengolan on 2009-11-22
got the same issue.  here are the details of my sound card etc:
[http://ubuntuforums.org/showpost.php?p=8364412&postcount=8](http://ubuntuforums.org/showpost.php?p=8364412&postcount=8)

thanks in advance!

---

