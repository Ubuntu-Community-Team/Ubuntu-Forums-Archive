---
title: "Dell vostro 1500 sound fix"
date: 2007-11-30
forum: Dell  Ubuntu Support
---

### Post by mushroomcloudwarrior on 2007-11-30
Hi there,

Well, i've been trying to fix sound on my Dell vostro ever since i managed to get gutsy installed on it. Well, i have alsa drivers installed on my laptop but i'm not able to use my laptop in public places while using headphones, because i can't use headphones on it.

I mean, i can plug in headphones and i get sound on the phones, the sound on the laptop (i.e. the laptop speakers don't mute) so it's really annoying, because i can't take the machine down to the library or listen to music on it when my room mates are sleeping etc..

i found this thread on ubuntu forums but i don't think it was of any help;
[http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

and [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

but couldn't get anything working off it. the second link has a flaw which it mentions in itself..

Do you think anyone can help me out with this? :(

---

### Post by thomnor on 2007-12-01
## I am a newcomer to Ubuntu and Linux, so I don't know if this will be helpful for you ##

I have a Dell 1520, and I experienced the same the first time I installed 7.10. I tried the alsa-stuff and a lot of other fixes, but nothing seemed to work. I reinstalled Ubuntu, and this time I had no sound whatsoever. But I finally found a solution to the dumb computer...

First of all, do you have the "headphone jack sense" option in your volume menu? (To access it, double click on the speaker icon, go to Edit, Preferences, and make sure everything is selected. Then browse through the tabs).
I did not have this option, so I tried the following found in another thread:
([http://ubuntuforums.org/showthread.php?t=577469&highlight=1520](http://ubuntuforums.org/showthread.php?t=577469&highlight=1520) -
This thread is for the inspiron 1520, but vostro 1500 is the twin-brother I think).

What I did was to type
```
sudo apt-get install linux-backports-modules-generic
```
in the terminal. I rebooted, and could now choose between 
Ubuntu 7.10, kernel 2.6.22-14-386
and
Ubuntu 7.10, kernel 2.6.22-14-generic
in the GRUB menu.

By choosing the latter, the sound worked perfectly. I edited GRUB so that the 386-option was removed from the startup menu.

---

### Post by mushroomcloudwarrior on 2007-12-01
```
nikhil@nikhil-laptop:~$ sudo apt-get install linux-backports-modules-generic
[sudo] password for nikhil:
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-backports-modules-generic is already the newest version.
linux-backports-modules-generic set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nikhil@nikhil-laptop:~$

```

I have it installed already on mine, but i don't get the choice in the terminal for some reason :(

Did you install, like a new variable of the kernel or something like that? because i think i read about taht quite a bit..

---

### Post by mushroomcloudwarrior on 2007-12-01
Another interesting thing is that, 

When i added 
```
options snd-hda-intel model=dell
``` into the alsa base file, and rebooted..my headphones actually started to work..till the next reboot where it stopped working again. This is very strange behavior indeed, i can't figure out why it would start working on the first reboot and then just stop :S

---

### Post by thomnor on 2007-12-01
> **mushroomcloudwarrior said:**
> I have it installed already on mine, but i don't get the choice in the terminal for some reason :(
You mean a choice in the GRUB menu, right?
All I did was to run the mentioned command, nothing more, nothing less ...

As stated, my knowledge is very limited, so I really don't know what you can do further on, sorry.

---

### Post by sh4ka on 2007-12-01
[http://ubuntuforums.org/showpost.php?p=3494809&postcount=10](http://ubuntuforums.org/showpost.php?p=3494809&postcount=10)

There you have the solution, that worked for me and I have a vostro 1500 too :D

Good luck.

---

### Post by mushroomcloudwarrior on 2007-12-02
Thanks sh4ka,

but i have ALSA drivers installed already, and have sound on my laptop..The problem is, that i am unable to use headphones as the laptop speakers don't shut off.
m using kubuntu and i think it's a kubuntu specific problem :(
o#

---

### Post by ~chinook~ on 2007-12-02
> **sh4ka said:**
> [http://ubuntuforums.org/showpost.php?p=3494809&postcount=10](http://ubuntuforums.org/showpost.php?p=3494809&postcount=10)

There you have the solution, that worked for me and I have a vostro 1500 too :D

Good luck.

The funny thing is you posted my solution, which in fact doesn't solve my headphone problem. I am still looking for a fix.

---

### Post by ~chinook~ on 2007-12-02
> **mushroomcloudwarrior said:**
> Thanks sh4ka,

but i have ALSA drivers installed already, and have sound on my laptop..The problem is, that i am unable to use headphones as the laptop speakers don't shut off.
m using kubuntu and i think it's a kubuntu specific problem :(
o#

Its not Kubuntu specific. Gnome here, same problem.

---

### Post by mushroomcloudwarrior on 2007-12-02
Well, i was able to find [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

which suggests that i follow [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) to get the problem fixed (basically making a new kernel)

I wonder how, for some people, using just the backports code has worked..its strange. What's even more strange is that it actually worked twice for me, but stopped working on reboot. :(

---

### Post by mushroomcloudwarrior on 2007-12-03
Anyone have any news on this?

I thought the Vostro was selling like hotcakes and anticipated more threads by vostro owners..unless, this is a 7.10 specific issue..

chinook and everone else having this problem, what version ubuntu/kubuntu are you running?

---

### Post by ejlamarque on 2007-12-03
Thank you everybody. I fixed my vostro 1500 with the **#3 post**. Bye

---

### Post by mushroomcloudwarrior on 2007-12-03
> **ejlamarque said:**
> Thank you everybody. I fixed my vostro 1500 with the **#3 post**. Bye
Glad to have Helped :KS

 If you could, tell me whether your headphone jack was working fine?

---

### Post by ejlamarque on 2007-12-03
Now everything work properly, before no. You are welcome

---

### Post by mushroomcloudwarrior on 2007-12-03
I think some vostros are just working fine with the backports fix and some are not.

Strange, very strange..

---

### Post by mushroomcloudwarrior on 2007-12-12
Does anybody have any update on the sound issue on the Dell? if so, please help the others by posting it in a thread, maybe making it sticky for a short while?

---

### Post by dyssident on 2007-12-13
Ran the following and sound, along with the headphone jack, Just Worked
```

sudo apt-get install linux-backports-modules-generic

```

Lspci shows
```
dyssident@blackstar:~$ lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

linux-backports-modules-generic version is 2.6.22.14.21

The only thing I can think of that might help you is to enable all repositories as I have done. Good luck.

---

### Post by mushroomcloudwarrior on 2007-12-13
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

Well, mine shows the same too, i already have the backports installed, and just activatd all the repositories. I'm going to try if booting up with the headphone jack in there makes a difference.

Edit: Yep, rebooted with the headphone jack left in there, and it just bypasses the speakers straightaway. The only problem now is that i don't have my speakers when i take the jack out :( 

yeah, it's being cheeky

---

### Post by dyssident on 2007-12-15
Found a quick fix for quiet audio that some are having. 

1. Install the alsamixergui package with Synaptic or `sudo apt-get install alsamixergui`
2. Open Applications > Sound and Video > Alsamixergui
3. Jack the PCM levels all the way up. This apparently resets the maximum volume.
4. Close Alsamixergui and turn sound back down to a reasonable level with the hardware buttons or the task bar volume control widget

Sorry mushroomcloudwarrior, still haven't come across any fix for non-working audio.

---

### Post by mushroomcloudwarrior on 2007-12-16
Well, the only problem i'm having is with the headphone jack not working. My audio works quite well.

I've sort of been eliminating all the little annoying things my laptop doesn't have yet, and this one is right on top of that list now. I want my headphones to work fine, that's one of the main advantages of working off your computer in a public place, you get to listen to music..and i especially want to show off Amarok and it's uber coolness.

---

### Post by dundeemt on 2007-12-22
> **sh4ka said:**
> [http://ubuntuforums.org/showpost.php?p=3494809&postcount=10](http://ubuntuforums.org/showpost.php?p=3494809&postcount=10)

There you have the solution, that worked for me and I have a vostro 1500 too :D

Good luck.

This worked like a charm on my vostro 1500 and 7.10
I used the same fix for 7.04

woohoo! 1280x800 + sound and scrolling mouse -- I'm a happy camper.

---

### Post by enzyme on 2007-12-27
Hello all.

I have a Vostro 1500. When I first installed Gutsy, I had no sound, but after following many of the pieces of advice offered in this thread, I got the sound to work. Honestly, I don't know exactly what got it working, because I must have tried a dozen different things. However, ALSA is really not playing nice with skype, ekiga or any other software that requires microphone input. Oddly, I can record my voice using the sound recorder, but not use skype or ekiga. 

I have ALSA and pulseAudio installed at this point. I really don't know which one is working when I record my voice in the sound recorder. I cannot see pulseAudio as option when I configure skype (beta 2.0 or 1.4 stable). 

I would really hate to have to boot into windoze just to call my family. I really like the penguin!

Any help will be very appreciated.

Cheers.

Luis

---

### Post by mushroomcloudwarrior on 2007-12-27
> **enzyme said:**
> Hello all.

I have a Vostro 1500. When I first installed Gutsy, I had no sound, but after following many of the pieces of advice offered in this thread, I got the sound to work. Honestly, I don't know exactly what got it working, because I must have tried a dozen different things. However, ALSA is really not playing nice with skype, ekiga or any other software that requires microphone input. Oddly, I can record my voice using the sound recorder, but not use skype or ekiga. 

I have ALSA and pulseAudio installed at this point. I really don't know which one is working when I record my voice in the sound recorder. I cannot see pulseAudio as option when I configure skype (beta 2.0 or 1.4 stable). 

I would really hate to have to boot into windoze just to call my family. I really like the penguin!

Any help will be very appreciated.

Cheers.

Luis

Well as i said, i'm guessing we'll just have to wait maybe..

My only problem is that my headphone jack doesn't work. Last week, i actually got my Microphone working as well and i'm able to call people from Skype. Windoze breaks every time i start Skype now which is totally weird.

Anyway, why don't you try this for the microphone.

This fix is for a Dell vostro 1500

   ```
1.Open Volume Control
   2.Go to Edit -> Preferences
   3. Make sure "Digital" and "Digital Input Source" is selected
   4. On the "Recording" tab, make sure the "Digital" slider is non-muted and turned up
   5. On the "Options" tab, make sure the "Digital Input Source" is set to "Digital Mic 1"
```

It's not my fix, taken from [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller#head-1f2c18721a2ecb093f6cf8f64d1ad8ddb13c4d0c](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller#head-1f2c18721a2ecb093f6cf8f64d1ad8ddb13c4d0c)

I hope that works for you and you don't have to boot windows every time you have to use Skype.

Let me know if it worked.

---

### Post by enzyme on 2007-12-27
> **mushroomcloudwarrior said:**
> 

Anyway, why don't you try this for the microphone.

This fix is for a Dell vostro 1500

   ```
1.Open Volume Control
   2.Go to Edit -> Preferences
   3. Make sure "Digital" and "Digital Input Source" is selected
   4. On the "Recording" tab, make sure the "Digital" slider is non-muted and turned up
   5. On the "Options" tab, make sure the "Digital Input Source" is set to "Digital Mic 1"
```



Thanks, mushroomcloudwarrior, I checked my settings and that's exactly what I had, which means that I still can't use skype or ekiga.  I don't think ALSA is working properly or at all. What I don't understand is why I have sound on other programs...

Luis

---

### Post by mushroomcloudwarrior on 2007-12-27
Well, that's strange.

I hope it's not something silly like setting your audio to alsa or something :|

i'm using Kubuntu btw..it's strange that your headphone jack is working well but you're having microphone problems.

---

### Post by enzyme on 2007-12-28
Well I just uninstalled pulseAudio and suddently I got skype to work just fine, and I'm happy for now. I noticed that the front panel multimedia buttons don't work anymore, but that's a minor issue. I have yet to test the headphones and mic jacks, but I'll do that tomorrow. 

Luis

---

### Post by tptbz on 2007-12-30
Hi,

Sound is so basic.  If Dell or any vendor for that matter wants Linux to work on their systems it will. 

Vostro has a thirty day return policy.  Just return it and consider getting Dell's Ubuntu notebook.

---

### Post by mushroomcloudwarrior on 2007-12-30
Well, none of them seemed to work for me.

However, i think i've come to a solution, it's quite impractical but works for me.

I'm going to get  myself externam speakers that are always plugged into the laptop. This would give me sound every time i started my computer through the speakers, and any time i'd like to use headphones..well just take out the speaker jack and insert headphone jack. I don't really require speakers when i'm using the laptop outside my house anyway.

I'm surprised i took so long to come up with this.

---

### Post by enzyme on 2008-01-16
Hello all.

After fiddling with the sound for quite some time, I found that pulseAudio was messing with ALSA, and that's why I wasn't able to use skype. So I uninstalled pulseAudio, now I just have ALSA, which was re-compiled according to the instructions in the posts above and sound works nicely.

Granted, when I plug my headphones to the headphone jack, sound still comes out from the speakers. However, as the headphone jack in my vostro 1500 is so cheap and has so much interference, I had already bought a USB sound "card" for 10 dollars at the source (reg. price around 25). Now I just plug it in, go to system-preferences-sound, and tell ubuntu to use USB for music/movies, or whatever I'm in the mood for.

So, this kills two birds with one stone and now, at last, everything works in my vostro under Ubuntu and I can say good-bye to windows for good.

Luis

---

### Post by mushroomcloudwarrior on 2008-01-17
I would have still liked the headphones to work straight out without using any more hardware though.

Right now, windows actually wins over my linux

> Touchpad works better on windows (i'm already using an application to control touchpad settings on kubuntu)
> My wireless keyboard and mouse are plug and play with windows, however, only the mouse is detected when i plug in AFTER i've booted up
> Headphone works with windows
> Wireless is much faster and efficient on windows (although this might be due to a wrongly installed driver) 
> Still haven't found a way to read/write ntfs partitions on linux (i'm using ntfs-config, am i doing something wrong?)

---

### Post by cawel on 2008-01-21
Here is my hardware:
- DELL Vostro 1500
- 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

and I spent days trying to fix my sound issues. So here are a few thoughts.

I started with a clean install of Gutsy and then installed all the Gutsy updates available at that moment. And that's the reason why I didn't have it working right away (see below).

I knew I needed to compile and install a recent version of the ALSA drivers to fix my sound issues. But when doing so, I suspect you're upgrading the drivers that were installed during the clean Gutsy install, NOT the ones installed during the Gutsy update. So that would explain why Ubuntu kept on loading the old ALSA version, as was indicated with 'cat /proc/asound/version'.

Specifically, I had hda (sound module) stuff in both: 
/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda
/lib/modules/2.6.22-14-generic/updates/sound/pci/hda

Once I erased the hda stuff in the 'updates' directory, things got better...

Also, I did NOT need an 'options' line in /etc/modprobe.d/alsa-base (in fact putting one there preventing it from working), as often seen in the different posts, e.g. 
options snd-hda-intel probe_mask=8 model=3stack

The ALSA version that I currently run is 1.0.15rc1 and it works fine.

---

### Post by glycerine102 on 2008-02-02
Just thought I'd chime in here and say the 1.0.15 drivers fixed my issues.

I used [the scripts from this link]("http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html") to update Alsa to 1.0.15

After running those 2 scripts I can now plug in my headphones and sound is redirected from my main speakers to the headphones.  The main speakers kick back in when I unplug the jack.:)

--Dell Vostro 1500 running Gutsy

---

### Post by ocarinahuff on 2008-02-02
Hi all,
I too have struggled with the headphone problem with my Vostro 1500.  I stumbled across a solution that I don't think anyone else tried.

1.  I did a clean install, updated everything including gutsy-proposed and gutsy-backports.
2.  Installed linux-backports-modules to get sound working
3.  Then, I installed libasound2-plugins.

Now headphones work, turns speakers off when plugged in, then on when unplugged. 

Can anyone else confirm this?
:confused:

---

### Post by sarukun1228 on 2008-03-08
I have a Vostro 1500. At first I had no sound, so I ran the alsa commands and then I had the headphone issue. I ran the backport and that made them work. I actually saved the commands into a text file and just run in terminal. Thanks for all your help. I've attached the file as well. Just use Run in Terminal.

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa
sudo apt-get install linux-backports-modules-generic

---

