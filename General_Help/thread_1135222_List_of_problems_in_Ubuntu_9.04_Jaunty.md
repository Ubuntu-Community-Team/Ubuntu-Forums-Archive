---
title: "List of problems in Ubuntu 9.04 Jaunty"
date: 2009-04-24
forum: General Help
---

### Post by unimatrix on 2009-04-24
All the things that are broke when I "upgraded" from 8.10 to 9.04. I'll get right down to it:

[LIST=1]
[*] [s]My IR remote doesn't work anymore. The signal can be seen in /dev/snd/midiC0D1, but the programs that were configured (rhythmbox, volume, etc) don't react to it.[/s] [MANUALLY FIXED: the update replaced my lirc config files, but fortunately kept the original ones]

[*] [s]On my laptop the usplash is completely busted, split into two parts, one on each side of the screen, with ugly colors (looks like 256 colors) and the wrong resolution.[/s] [MANUALLY FIXED, using [map84]("http://ubuntuforums.org/showpost.php?p=7135773&postcount=18")'s suggestion]

[*] The touchpad scrolling is now set to two-finger scrolling, which is horribly annoying, because now I cannot use the two-finger tap to do a middle click.

[*] [s]Rhythmbox keeps crying about some imaginary codecs that need installing (even though they're obviously already installed) evety time I run it.[/s] [Bug [#204566]("https://bugs.launchpad.net/rhythmbox/+bug/204566")] [WORKAROUND: sudo rm /usr/bin/gstreamer-codec-install]

[*] [s]My laptop sometimes doesn't [s]reboot or[/s] shut down completely. I need to [s]reboot it with ctrl+alt+del and[/s] shut it down by holding the power button.[/s] [FIXED in Karmic Koala]

[*] The touchpad on my laptop became extremely inaccurate. The minimal distance the cursor can be moved seems to be about 4 pixels. It feels horribly jumpy.

[*] [s]It sometimes reboots or freezes my desktop for no reason.[/s] [MANUALLY FIXED: Either by switching back to ext3 or by installing nvidia's 185 drivers. One of those two things must have worked.]

[*] [s]The new notifications sometimes cause artifacts to appear in programs. With and without compiz.[/s] [FIXED in Karmic Koala]

[*] [s]PulseAudio 0.9.14 sucks compared to what could've been 0.9.15. Whoever decided .14 would be in Jaunty should get fired. I could've been enjoying 24/96 sound, but thanks to that idiot I'm stuck with the shitty 16/44.1.[/s] [FIXED in Karmic Koala]

[*] [s]Pidgin keeps hogging up my CPU. I have to restart it at least twice daily.[/s] [FIXED in Karmic Koala]

[*] It is literally impossible to use the computer while burning a CD or DVD. Everything lags, even the mouse. It used to be like this in Intrepid, but only for DVDs. Now in Jaunty it happens when burning CDs too.

[*] Rhythmbox randomly stops playing music (with message "Disconnected: Connection Terminated") when I play it from a samba share. EDIT: I think it happens locally too, but less often.

[*] [s]VLC plays videos in a separate window.[/s] [Bug [#314038]("https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/314038")] [FIXED in Karmic Koala]

[*] [s]In Firefox the text sometimes disappears (or renders in a clearly incorrect way). The only fix is to restart Firefox every time.[/s] [FIXED in Karmic Koala]

[*] Vino is broken and does not update changes. [Bug [#367682]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/367682")] [POOR WORKAROUND: turning off compiz ([source]("http://ubuntuforums.org/showpost.php?p=7214210&postcount=5"))]

[*] [s]The microphone doesn't work in Skype (due to PulseAudio ... which would have been fixed in 0.9.15).[/s] [FIXED in Karmic Koala]
[/LIST]

I probably missed some stuff. I'll add later when I encounter them again.
Bottom line: upgrading to Jaunty was a really bad idea.

Share your troubles with Jaunty.

---

### Post by Teabicky on 2009-04-24
I am having the same problem with rhythmbox and also I cannot get Brasero to work (it crashes).  I have tried serpentine and that does not even load up.

Other than that though I am impressed.  Ubunut just seems to be getting better at just "doing" with minimal fuss.

---

### Post by befana on 2009-04-24
I have only two problems with Jaunty:
1. Can't enable desktop effects (Intel graphic) and 
2. My rtl8187b wirelees has a speed of only 1Mb/s.

---

### Post by StormRoBoT2 on 2009-04-24
for me no problem at all, everything work fine for me.. using acer aspire 1690 (DDR2) (1692WLMi)

---

### Post by meeples on 2009-04-24
brasero is a big problem for me too i lose nautilus when i insert a  cd :O

---

### Post by Almighty on 2009-04-24
I can't get all 3 of my monitors to work :(

---

### Post by Gunbullet on 2009-04-24
1) I'm having the issue regarding power down, have to switch off by holding down the main power button on the computer (HP Pavilion dv2750).

2) Update Manager/Synaptic/Software Sources is a hit or miss, sometimes I'm able to update or check the repositories and other times it's a big no no.

3) Don't know if it's Jaunty or Firefox but the later chrashes sometimes which was a rare thing on Intrepid. 

Bottom line; not that happy with Jaunty at the moment. :(

---

### Post by hthury on 2009-04-24
I'm using Acer Aspire 5315. The only problems I noticed was:

1. Flickering screen. It's becomes dark and the bight again so fast maybe it could cause a epilepsy attack on a epileptic child.
2. Problem with that black floating box that appears on the top of the screen when you change brightness through keyboard. Cause flickering screen when changing brightness e aways shows zero brightness.
3. Can't turn the visual effects to extra/turbo, so I can't see all that funny windows effects anymore.

Other than that it's okay, releasing a few fix will make it all okay again.

---

### Post by Mokou on 2009-04-24
My only problem is the shutdown.As i heard the problem is in 64 bit if you install jaunty 32 bit it will be ok.

---

### Post by zaipai on 2009-04-24
Can't enable Compiz, Intel x3100 graphics card on a Sony Vaio DFZ240E. It was an upgrade over 8.10, however Compiz is not working even from Live CD.

---

### Post by El Zoido on 2009-04-24
Only some minor problems :)

1. Restricted drivers were only selectable after I restarted (didn't show up the first time)
2. Synaptics is showing the infobox everytime I start it, no matter how often I check "Do not show again"
3. Think this is actually the same as with earlier versions, but for convenience it could be adressed: 
Getting Encrypted DVD to play is a bit counter-intuitive, a simple window stating the reasons why it wont do so out of the box would be enough

---

### Post by zebbers on 2009-04-24
I never have had any luck with brasero(coasters). Gnome baker on the other hand has never failed. It should have been the default burner app.

---

### Post by aniruddha on 2009-04-24
With respect to video drivers, I found that just restarting fixed the install issues. Restart also fixed pulseaudio issues. Sometimes its just best to start over with a clean slate I guess...

---

### Post by matthew.ball on 2009-04-24
> **Mokou said:**
> My only problem is the shutdown.As i heard the problem is in 64 bit if you install jaunty 32 bit it will be ok.
I'm on 32-bit, and I have a very similar problem.

Edit: Though I had it before 9.04, I'm inclined to say different issue...

---

### Post by tbullock on 2009-04-24
After the upgrade I have lost the ability to left click after I open a browser. It will also happen if I click around a little without opening the browser but almost immediately with the browser. It lasted the longest in Epiphany. I have to restart to get it back and then it only lasts a little while. I am on Windows again until I can figure this out. Good thing that is not my only computer. I would pull my hair out dealing with tabbing everywhere.

---

### Post by Almighty on 2009-04-24
> **Almighty said:**
> I can't get all 3 of my monitors to work :(

Oh and what's up with getting rid of ctrl+alt+backspace to restart the xserver!? The umpire who made that call should be fired. Aside from kernel upgrades, there shouldn't be much of a reason to reboot.

---

### Post by unimatrix on 2009-04-24
> **Almighty said:**
> Oh and what's up with getting rid of ctrl+alt+backspace to restart the xserver!? The umpire who made that call should be fired. Aside from kernel upgrades, there shouldn't be much of a reason to reboot.

I have mixed opinions about that. I didn't really need it, and I can still do the same thing by relogging. But on the other hand, it was rather convenient sometimes.
Anyway, you can always re-enable it: [click]("http://albertomilone.com/wordpress/?p=335")

---

### Post by map84 on 2009-04-24
> **unimatrix said:**
> All the things that are broke when I "upgraded" from 8.10 to 9.04. I'll get right down to it:

[*] On my laptop the usplash is completely busted, split into two parts, one on each side of the screen, with ugly colors (looks like 256 colors) and the wrong resolution.


I had the same problem than you. Removing the option "vga=xxx" from the kernel-bootstring in /boot/grub/menu.lst helped. Give it a try!

---

### Post by Almighty on 2009-04-24
> **unimatrix said:**
> I have mixed opinions about that. I didn't really need it, and I can still do the same thing by relogging. But on the other hand, it was rather convenient sometimes.
Anyway, you can always re-enable it: [click]("http://albertomilone.com/wordpress/?p=335")
Thanks for the link!

---

### Post by higashi on 2009-04-26
can't enable compiz

---

### Post by Seventh Reign on 2009-04-26
I had to wait 2 years for the best release ever... what, thats a problem!

---

### Post by schloss on 2009-04-26
Couple things I've noticed:
[LIST]
[*]Running normal compositing effects under Jaunty, my Thinkpad T41 is slower than when I was running extra effects under Intrepid.
[*]Running Firefox in full screen mode (not what the system thinks is full screen, what Firefox does -- that happened in Intrepid too, should be fixed) the screen will randomly change to a blank desktop (as in it will just show the desktop background and nothing else) for a few seconds.
[/LIST]

---

### Post by wsonar on 2009-04-26
Sorry I just can't find any problems yet.

Did beta on one machine
Did and 8.10 to 9.04 upgrade on my latitude d620
Did a clean release candidate install from CD on another box

I like the box with the clean install I choose ext4 and can tell a big difference in performance

Hope everyone get things sorted out

One thing I noticed on the clean install there was not a notification for me to enable the restricted drivers for my nvidia.
I knew where to go but a lot of new folks might not.

---

### Post by iamah on 2009-04-26
installation won't detect my hard drive... 8.10 detected on install but needed bios hacks to boot from it... 9.04 won't even install cause doesn't see disk... adios, linux... winxp sp2 runs fine...

---

### Post by elasto1mania on 2009-04-26
can't use my mobile phone on jaunty (on intrepid I could)
Sometimes i get blask squares or black lines that disaper when the page is refreshed.
The most annoying one moves the display and makes ubuntu unusable. Hard restart only helps ...

---

### Post by reeko124 on 2009-04-26
Laptop touchpad won't work so I can't do anything

---

### Post by nick09 on 2009-04-26
The video drivers do not work for my ATI 3450. I could login as usual but Ubuntu does not load the Desktop for some strange reason. So far I'm just gonna use 8.10.

---

### Post by slowmoe on 2009-04-26
> **nick09 said:**
> The video drivers do not work for my ATI 3450. I could login as usual but Ubuntu does not load the Desktop for some strange reason. So far I'm just gonna use 8.10.

got the same problem (see here: [http://ubuntuforums.org/showthread.php?t=1136843](http://ubuntuforums.org/showthread.php?t=1136843) )

what kind of card do you have? (agp-version?) could you be so kind and maybe get a error-message from the Xorg.0.log-file to see if it is related to the problem I have? at the moment nobody is reacting seriously to my thread, if somebody else has the same problem things hopefully change...

if you don't know how to get the log-file: start ubuntu and when the desktop fails loading, open tty1 by pressing ctrl+alt+space, don't let go ctrl+alt and press F1, then you should be able to surf through your files with the command line... go to /var/log and search for Xorg.0.log - best thing is to save it on a thumb-drive/external drive and open it later on your intrepid :) would be a nice move of yours if you take a minute to do that...

EDIT: ok, after reading again, I don't think it is the same error, but maybe you should give the log-files a try anyway?

---

### Post by kapetus on 2009-05-04
Hello,

the only problem I have is with rtl8187b wireless, it only works and perfectly at a close range, with all configurations enabled (wpa/wpa2, dhcp, etc...)if I get a litle far from router, I lost connection to internet, but still can get IP adress from router...

---

### Post by lbelloq on 2009-05-04
> **unimatrix said:**
> All the things that are broke when I "upgraded"
Stopped reading right there.
With all the incidents posted in this forum, I'd tend to assume everyone already realized that "upgrading" is in fact a bad idea.
Just backup, do a clean install and enjoy.

---

### Post by Nopposan on 2009-05-04
I think I'll wait a month and then try upgrading.  I do appreciate all of you pioneers though; if we all wait then the problems won't be noticed until later.

Cheers.

-- Coward

---

### Post by alligoodw on 2009-05-04
I couldn't agree with you more.  

I backed up all my music, videos, documents and etc., and then did a fresh install of Ubuntu 9.04; overall, my experience has been very positive.  As a matter of fact, my wireless worked automatically for the first time, ever, since using an Ubuntu distribtion.  I just entered my password and off I went.  Using ex4 has really increased the speed of the system significantly.  

I really like what I see in this version (9.04).

---

### Post by jack57 on 2009-05-04
Mine Asus eeePC 900 have same problems (nearly same as on 8.04):

- wireless lan don't work.
- keybord fix has to be done.
- earlier notes for older versions of Ubuntu don't work (all), so they have to be updated after someone finds solution for fix on 9.04.

After that next step is to try, if Option Icon 225 broadband adapter works (worked on 8.04, but update broke driver ?, and after that I couldn't get it working). And if don't, try to find solution on 9.04.

:guitar:

---

### Post by EmptyCinema on 2009-05-28
I must just be lucky... been doing upgrades since 5.04 and never experienced any major issues from upgrades.

If you have something that worked under Intrepid and doesn't under Jaunty, I suggest filing a bug report and including "Regression: " in the bug subject line.  I suspect it's more likely to get attention that way.

---

### Post by zerny89 on 2009-05-29
Hello...
I have problem with my Ubuntu 9.04 after upgrade from 8.10....:(

the problem is..
-when play a movie in fullscreen, my Ubuntu suddenly hang & blank screen appear..
-so I can play a movie without fullscreen..very bad...
this thing cannot happen in my old Ubuntu 8.10..

so the seniors out there please help me to solve it....please....

thanks...

---

### Post by MattThLinuxNewb on 2009-05-29
> **El Zoido said:**
> Only some minor problems :)
2. Synaptics is showing the infobox everytime I start it, no matter how often I check "Do not show again"

Read it carefully - I seem to remember the label saying "Show this every time" rather than "Do not show this again" :p

---

### Post by HavocXphere on 2009-05-29
> **unimatrix said:**
> 
[*] It is literally impossible to use the computer while burning a CD or DVD. Everything lags, even the mouse. It used to be like this in Intrepid, but only for DVDs. Now in Jaunty it happens when burning CDs too.
Chipset issue. Switch usb mouse & keyboard to a different USB part. The ports go in pairs, so you'll have to try a few.

---

### Post by cb951303 on 2009-05-29
I had many problems with pidgin. I upgraded it to 2.5.6 through getdeb.net packages, now it works like a charm.

---

### Post by blastbar on 2009-05-29
when i power down it still shuts down just the whole screen goes bright red and flashes

i have no mouse pointer either (prob because i running a microsoft mouse atm)
any clues?

---

