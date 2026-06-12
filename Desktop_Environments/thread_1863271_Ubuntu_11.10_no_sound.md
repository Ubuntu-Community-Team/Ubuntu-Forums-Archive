---
title: "Ubuntu 11.10 no sound"
date: 2011-10-17
forum: Desktop Environments
---

### Post by sgoranov on 2011-10-17
Hi all,

I've got 11.10 but there is no sound at all. It's really strange I even tried with HDMI, but again - there is no sound. Any idea, how to fix it if it's possible of course?
I assume it's something related to 11.10 because on 11.04 I had no problems like this. Sound card works well.

Thanks in advance,
S.

---

### Post by BigCityCat on 2011-10-17
I had no sound in gnome shell even though the sound was turned all the way up. I logged into Unity and it was all the way down. I turned it up and logged back into shell and my sound was back.

---

### Post by sgoranov on 2011-10-18
> **BigCityCat said:**
> I had no sound in gnome shell even though the sound was turned all the way up. I logged into Unity and it was all the way down. I turned it up and logged back into shell and my sound was back.

Hm, It is strange because I'm using Unity not Gnome,but can try switch to Gnome and check sound again. Any idea how to switch?

Regards,
S.

---

### Post by randlieb on 2011-10-18
To get Gnome you have to install gnome shell. Then you can log out and have the option of logging in to Unity or Gnome.

I also have the no sound problem in Unity 11.10. So far my searches haven't come up with a solution.

Anybody?

---

### Post by shahryareiv on 2011-10-18
My problem was fixed by :

Installing/Compiling the latest ALSA drivers for the new Kernel 3.0.0.12 by :
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

removed & reinstalled pulseaudio things. (reinstall indicator-sound also)

Not working again, but I noticed that while aplay -l does not work sudo aplay -l works, so then I did this:
chmod -R a+rwX /dev/snd
Things worked for the headphones at least. Use alsamixer for tuning other things.

---

### Post by Tares on 2011-10-18
Try to install pavucontrol and check if don't have your output muted.

---

### Post by eumetaxas on 2011-10-19
After 5hours of searching::


```
sudo modprobe snd_hda_intel
```

worked!!!!!


Edit: You need to run that command in every restart. Anyways to make it permanent?

---

### Post by ThePunkPerspective on 2011-10-20
hey guys, im having the same problem and its really driving me bonkers, when I first installed it, it worked fine, but now that I am transferring files from my original windows 7 operating system over to my Unbuntu 11.10, my sound stopped working. I am not as smart as a lot of these computer smart people are, but I really would like some help on trying to figure out what I need to do to get my sound working!!!! Thank you for reading my post, and hopefully someone will get back to me on this quickly!

---

### Post by ballantony on 2011-10-20
I'm having a similar problem, only the sound seems to work on alernate boots.  Installed the new ALSA drivers as mentioned above, still no joy.  Bizarre.

---

### Post by FGC JUSTICE IT on 2011-10-20
What kind of files are you transferring? What verion # are you running I am 0n 11.10 and have no problem I did but found out that te problem was actually in my qjack audio setup, my setup wasn't properly pointing to my alsa drivers. I personally try to keep most of my stuff from windows such as music or files that can be accessed on and what isn't compap a separated usb  memory card or external hard drive.

, when I first installed it, it worked fine, but now that I am  transferring files from my original windows 7 operating system over to  my Unbuntu 11.10, my sound stopped working.

 This makes me wonder if something in these files is causing this problem or what. I would make sure that you have your sound set up correctly in you control panel and then in any other programs you rely on to emulate it.

 this makes me wonder if something

---

### Post by bmcneely76 on 2011-10-20
I haven't transferred any files and did a fresh install. Still no sound. I have tried everything on this page and nothing has seemed to work thus far.

---

### Post by RomanSB on 2011-10-20
I'm also having this problem, after an upgrade. Also have gnome installed and no sound on either that or unity.

Also also tried sudo modprobe snd_hda_intel with no success.

---

### Post by ballantony on 2011-10-21
This worked for me...

[http://ubuntuforums.org/showthread.php?t=1861477&highlight=banshee](http://ubuntuforums.org/showthread.php?t=1861477&highlight=banshee)

---

### Post by selectedusername on 2011-10-22
Have any of you guys tried this?

[http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound](http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound)

---

### Post by RomanSB on 2011-10-23
Ah, I strangely got it fixed by going into Gnome (classic) from the login menu. The volume was muted and it now works on regular gnome also.

Cheers

---

### Post by petermck on 2011-10-23
As Ballantony stated above, this post
[http://ubuntuforums.org/showthread.p...hlight=banshee]("http://ubuntuforums.org/showthread.p...hlight=banshee")
seems to have the answer, at least to my problem.
I did this:
```
sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
```

When removing alsa-base, apt-get also removed some ubuntu-desktop associated stuff so I also:
```
sudo apt-get install ubuntu-desktop
```
and then rebooted.

This also appears to have fixed problems I had with Firefox:
[LIST]
[*]hanging for a long time when trying to right click and open a link in a tab or new window
[*]not playing video in Youtube
[*]generally operating slowly.
[/LIST]

As far as I can tell, everything seems to be working properly now. The only remaining issue I see is that the speaker icon has disappeared from the toolbar.

My installation was a fresh install of 11.10 64-bit.

---

### Post by alexthunder on 2011-10-25
I had problem with sound when using my M$ USB headset. The following has helped me:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by bofkentucky@gmail.com on 2011-11-09
> **eumetaxas said:**
> After 5hours of searching::


```
sudo modprobe snd_hda_intel
```worked!!!!!


Edit: You need to run that command in every restart. Anyways to make it permanent?

sudo echo "snd_hda_intel" >>/etc/modules

---

### Post by lisanels47 on 2011-11-09
OK, I also just upgraded from a working 11.04 system to 11.10.
My sound is acting up too.  Here's what I see.
Go into sound setting, and my output vol is at 100%.  Click Sound Effects tab.  I notice the Alert volume is about 5%.  I can click it up to about 90%, and hear the "drip" sound effect fine.  But right after the click, it drops back to about 5%.  It's kinda psychotic!  Jumps all over when I'm clicking in the adjustment bar.
I'm sure that whatever is causing it to freak out is my sound problem... 
I'm going to try removing and installing sound again... Like others have done.  But maybe a few of you will see the same thing with the Alert volume in the sound settings.

---

### Post by garyjmellor on 2011-11-12
Hi all,

I had this same problem. One minute I was listening to content on YouTube and the next I had no sound at all. No alert sounds, nothing coming from Banshee and nothing from YouTube. One minute it was there the next it just stopped working. I tried all the things in this thread but nothing worked except my sound icon disappeared from the top panel so I had to look up how to get that back (sudo apt-get install indicator-sound).

I then went into 'Sound Settings' by clicking the sound icon and selecting it from the menu that appeared. Now I've never opened this on Ubuntu 11.10 (my current installation) since I installed it but I noticed that in the 'Output' tab the HDMI hardware had been selected. As I understand it, from reading elsewhere, the HDMI stuff as far as sound is concerned is disabled in 11.10 with the new kernel (3.x ?) so why this became selected when I'd never been in the sound settings is a total mystery. I simply reselected the analogue stereo option and voila - sound again. Very, very strange.

Hope this helps someone.

---

### Post by xXSanitariumXx on 2011-11-15
[IMG]http://i39.tinypic.com/2iw9krq.png[/IMG]

This should fix your problem which is what I use just now after freshly installing Ubuntu Desktop 11.10 32-Bit. I had been using Windows 7 Ultimate 64-Bit but wanted to install Ubuntu again since I haven't used it in a while.

If you set your settings as shown above it should fix your problems without the needs of typing anything in your terminal or downloading a bunch of random useless junk. Just go to the Ubuntu Software Center & search for "Pulse Audio" then change the settings as you see above.

:popcorn:

---

### Post by igorc on 2011-11-16
This worked for me [http://ubuntuforums.org/showthread.p...hlight=banshee](http://ubuntuforums.org/showthread.p...hlight=banshee)


For the missing sound indicator:

$ sudo aptitude install indicator-sound

then log out and log in again.

Once I got the HDMI sound working I ran

$ sudo alsactl -f /var/lib/alsa/asound.state store

to store the alsa settings.

---

### Post by arasbm on 2011-12-13
I am still having issues with the sounds. I tried all the suggested solutions here but it still does want seem to work.
When I play music I can see activity in the pulse audio volume control (under the playback tab there is a progress bar that shows activity). But there is no sound coming out of either front or rear 3.5mm jacks or the HDMI (through monitor). I have Unity, Gnome3 and XFCE installed side by side and neither of them make a squawk!
I have searched around and so far nothing seem to work. The sound was working perfectly fine in 11.04 but I dont think it broke immediately after the upgrade. I think one of the updates to the kernel might have caused the issue. :confused:
Anyways, I really like to know how to debug and fix this issue. I need sound!

---

### Post by reinski on 2012-01-17
Hi all, my sound system stopped working suddenly and I tried most of the suggestions above with no success. It turned out that the problem was within my dual boot system Windows 7/Ubuntu 11.10 as described in Step 9 here: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

I switched back to Windows and put the speakers to full volume. After that it worked with Ubuntu 11.10 as well.

---

### Post by ptemple on 2012-01-23
I had sound in Windows 7, but nothing in Ubuntu. Plugging in a new nVidia graphics card killed Ubuntu from booting at all. Tried fixing drivers from the command line but got in a mess as Ubuntu was insisting on building in 173* and I then had a mess of 295* drivers installed.

I put the latest Ubuntu 11.10 on a USB key and booted from there. I selected "Upgrade from 11.10 to 11.10". PC chugged away for a while, I rebooted, and now I have both sound and video working perfectly! All my apps and data remained intact.

Hope this is of help,

Phillip.

---

### Post by tenach on 2012-02-03
> **bofkentucky@gmail.com said:**
> sudo echo "snd_hda_intel" >>/etc/modules

This worked perfectly for me in Lubuntu 11.10! Thank you both quite a bit! :D

---

### Post by forever1 on 2012-02-04
_**This is a fix for probing sound cards(Intel)**_
[LIST=1]
[*]sudo gedit /etc/modprobe.d/alsa-base.conf
[/LIST]
[LIST=1]
[*]add to bottom “options snd-hda-intel model=auto”
[/LIST]
[LIST=1]
[*]restart computer
[/LIST]
[LIST=1]
[*]open console run “alsamixer” and turn up audio on all and set channels to 6.
[/LIST]

_**If you have installed a update driver that's not working**_
[LIST=1]
[*]sudo apt-get install --reinstall linux-image-$(uname -r)
[/LIST]
[LIST=1]
[*]Then repeat the above fix for probing
[/LIST]

---

### Post by sardhwk on 2012-02-19
I installed Edubuntu 11.10 on an Acer Aspire 1 D255. After recommended upgrades and PAV control I lost the login sound (drums).
I checked Gnome Login sound in startup appl. Edit shows a file in usr/share/gnome/autostart/libcanberra-login-sound.desktop
At that location I found a desktop configuration file. Opening it gives the drum sound. Thus the file is there.
A post of Fractalman Oct 2011advised this command  "gksudo gedit /usr/share/gnome/autostart/libcanberra-login-sound.desktop" to check on "No display=false".
I did so but it returns with a prompt and it looks like the command is not executed.
I also tried to look into to file using "gksu nautilus" but  no file that I can edit just the sound file. What is wrong and wt should I do to get the login sound back.

---

### Post by forever1 on 2012-02-20
Hi Sardhwk,

please use "sudo" instead of "gksu" and you are editing root config files and not your own thats why its not working.

---

### Post by sardhwk on 2012-02-20
Hi Forever1. Thanks for responding. I tried sudo nautilus and got this:
Initializing nautilus-gdu extension
** (nautilus:2812): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-open-terminal extension
Initializing nautilus-ideviceinfo extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.Nautilus-Share-Message:  Called "net usershare info" but it failed: 'net usershare' returned  error 255: net usershare: cannot open usershare directory  /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> l2049
--> inode/directory
--> root

(nautilus:2812): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

--- Hash table keys for warning below:
--> file:///
--> file:///usr
--> file:///root
--> file:///usr/share/gnome
--> file:///usr/share

(nautilus:2812): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 5 elements at quit time (keys above)
Shutting down nautilus-ideviceinfo extension
Shutting down nautilus-open-terminal extension
Shutting down nautilus-gdu extension

---

### Post by wpawan on 2012-02-20
hi, i am new to Ubuntu,having 3 months of experience,i dont get the default sound after login. it worked during first few days.For rest of apps. sound works well.

---

### Post by ScottieMUNCHER on 2012-03-08
HI guys.
i recently encountered a similar problem however my solution was deceivingly simple. lol

In " system settings"-->"sound" 
under the "Hardware" tab. 
there is a drop box for "profile"
Mine had changed itself to say "analog audio input"
Changed it to say "analog audio output" worked just fine.
Hope this helps someone. :D 

[IMG]http://i382.photobucket.com/albums/oo264/Shortie_174/Screenshotat2012-03-09085058.png[/IMG]

---

### Post by richgreene on 2012-04-03
After 3 days of trying to get my audio fixed, this one did the trick!

Many Thanks!!!

---

### Post by richgreene on 2012-04-03
Forgot to mention, it was post #5 that did it for me:

> Installing/Compiling the latest ALSA drivers for the new Kernel 3.0.0.12 by :
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)


---

### Post by arijit_bosco on 2012-06-09
Faced this issue with 11.10 for a week.

Finally, "rm -rf $HOME/.pulse" followed by reboot solved this problem for me.

---

