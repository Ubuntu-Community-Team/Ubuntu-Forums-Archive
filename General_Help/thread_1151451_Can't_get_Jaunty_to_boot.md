---
title: "Can't get Jaunty to boot?"
date: 2009-05-06
forum: General Help
---

### Post by kyle94481 on 2009-05-06
Well today I decided to dual install Jaunty 9.04 with XP Pro on an older system I have.  The install seemed to have gone fine.  I booted up, selected Jaunty, and booted into Ubuntu.  Everything was fine until I rebooted (my router was messing up, completely irrelevant).  When I tried to boot back up during the boot splash the screen had weird markings on it, like green pixels and such scattered.  After the boot finished all that came up past the splash was a black screen.  Nothing else.  Every time I try and boot into Ubuntu now it does the same thing.  Weird boot splash, black screen.  Prior to the first reboot, I installed some extra RAM I had lying around and rebooted.  Thats when the splash looked weird and such.  I haven't removed the RAM because It was working perfectly fine in the other system it was in (Another XP Pro system).  Even though it was working fine before, I ran Memtest from Grub for 4 and like 3/4ths passes.  No errors were reported.  I don't know what to do now :(.  Any advice is welcomed :)

PS - I'm a first time Linux user!

---

### Post by mb_webguy on 2009-05-07
Don't know that I've ever heard quite that particular problem before...  It could be your video driver, I suppose.  Try booting into recovery mode from the Grub menu.  Once you're at the command line, type "nano /etc/X11/xorg.conf".  Look for the "Device" section, and change the value of "Driver" to "vesa".  Save and exit, then type "reboot" to reboot your system.

---

### Post by kyle94481 on 2009-05-07
Thanks a ton :)

This helped me a lot and now I can boot into ubuntu!

Thanks again

---

### Post by raywood on 2009-05-09
This got me partway.  I still got a black screen after doing this, but at least I saw the Ubuntu splash screen and progress bar for a moment before the black screen.  So that's an improvement.

On reset, back in recovery mode bootup, I ran dpkg and fsck.  dpkg advised running apt-get update and apt-get autoremove.  I didn't realize I could scroll down to an xfix option on that menu; when I found that, I ran that too.  But no luck; still a black screen.  

Subsequent reboots gave me the splashscreen/progress bar combination on normal bootup, but not after going through recovery mode.  Either way, though, I ended up with a black screen.  I didn't try that before, so maybe the solution suggested by mb_webguy here actually didn't make any difference.

By the way, the cause seemed to be the installation of fusion-icon.  Things were fine until then.  I'm using nvidia drivers, or at least I was until I made the change suggested here.  I uninstalled compiz per some other suggestion, and that apparently took fusion-icon along with it, but the damage was done.

I didn't try the mouse integration solution; this didn't seem to be that kind of problem.  In my case, there was no cursor of any kind; the screen was totally black.  See [http://forums.virtualbox.org/viewtopic.php?f=3&t=16439&start=0](http://forums.virtualbox.org/viewtopic.php?f=3&t=16439&start=0)

A lot of people seemed to be having this problem.  See [http://ubuntuforums.org/tags.php?tag=black+screen](http://ubuntuforums.org/tags.php?tag=black+screen)

Ctrl-Alt-F3 during splashscreen didn't provide a workaround.

Found a good parallel discussion underway (no solution yet) at [https://answers.launchpad.net/ubuntu/+source/gdm/+question/69596](https://answers.launchpad.net/ubuntu/+source/gdm/+question/69596)

Tried cold rebooting (5-minute delay).  See [http://ubuntuforums.org/showthread.php?t=1149879](http://ubuntuforums.org/showthread.php?t=1149879)
This achieved nothing.

Closer observation suggested the screen was not completely black.  There seemed to be a tiny bit of backlight -- a very dark grey.  I thought it might be the counterpart of the completely white screen (except for mouse cursor) that I got after installing fusion-icon.

This dual-boot machine was still able to boot into Windows XP without a problem.

That's where I left off.  Any ideas?

---

### Post by krazykookmany on 2009-05-15
//

---

### Post by TMAB2003 on 2009-05-23
Has there been any solution to this problem?

I have been searching for quite some time..tried different solution methods..none of them worked.

---

