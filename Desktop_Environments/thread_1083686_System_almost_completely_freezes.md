---
title: "System almost completely freezes"
date: 2009-03-01
forum: Desktop Environments
---

### Post by flamer on 2009-03-01
I did a clean install of Ubuntu Intrepid. When I login the system almost completely freezes. It looks like it has boot up perfectly but in the taskbar there is only network manager(i have many more). When I want to start up a program (ex. Firefox) it doesn't open. No program does. I can view the Application, Places and System toolbar and move desktop icons and that's  about it. To restore everything to work, I have to do a ctrl-backspace and login again. Can someone help me?

---

### Post by thtrgremlin on 2009-03-01
Just in case, are you sure that it isn't just taking a really long time to load your desktop?

I personally found the gnome splash screen to be helpful to tell me when all startup programs have started up. before that, everything is quite slow. You can set a splasn screen with ```
gnome-splashscreen-manager
```

You can also use```
gnome-session-properties
``` to see what is starting up.

As far as something more incidious, need some more info:
1) What kind of computer, basic specs, laptop / desktop, what came preinstalled?
2) Did you use intrepid before? What initiated you to do a clean install?
3) If it loads to desktop on initial startup and "freezes", but then "ctrl-alt-backspace", do you not have the same problem?
repeat from above, how long have you left it to try and login?
4) How do you connect to your network / the Internet?

I am going to guess that if only network manager is showing up on the taskbar that there could be a relationship, but want to narrow things down first.

---

### Post by flamer on 2009-03-01
**thtrgremlin**

I've mistyped i'm sorry. I meant ctrl-alt-backspace



When I turn ON the splash-screen it shows that file browser is starting in both cases when I do a complete reboot and after when I restart X with the command above. 


As for the gnome sessions. It's all default I haven't changed anything and as far as I know everything looks fine. I think it's the problem with the X.


1) I use a desktop computer with 1GB of ram, ATI Radeon 9600SE graphic and standard Ethernet...


2)Yes, I used Intrepid before and it worked flawlessly (I have LAMP server running on this one). I was changing some partitions and I accidentaly destroyed my partition tables.


3)No. When I do ctrl-alt-backspace and login, everything goes back to normal (till next reboot) 


4) I connect to internet via Ethernet on my Lynksis WRT54GL with tomato firmware and then to cable internet.

---

### Post by thtrgremlin on 2009-03-01
> I've mistyped i'm sorry. I meant ctrl-alt-backspacehe he, I didn't even notice the mistype :)

Are you using auto-login, or does it wait at the GDM for you to put in your name and password?

(I vaguely remember having a problem like this forever ago, and trying to remember what fixed it)

---

### Post by flamer on 2009-03-01
I don't use the auto-login option.

Even when the system is "freezed", LAMP server works fine :).

---

### Post by thtrgremlin on 2009-03-01
in case it needs to be said, you have done a complete update of your system since the clean install, right?

```
sudo apt-get update && sudo apt-get upgrade
```

(While this continues to hurt my brain, want to make sure we havn't overlooked something obvious. still working)

---

### Post by flamer on 2009-03-01
```
miha@miha-laptop:~$ ssh miha@192.168.1.2
miha@192.168.1.2's password: 
Linux miha-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Sun Mar  1 15:56:46 2009 from miha-laptop.local
miha@miha-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for miha: 
Zadetek http://si.archive.ubuntu.com intrepid Release.gpg
Zadetek http://security.ubuntu.com intrepid-security Release.gpg
Prz http://security.ubuntu.com intrepid-security/main Translation-sl
Dobi:1 http://si.archive.ubuntu.com intrepid/main Translation-sl [3173B]
Prz http://si.archive.ubuntu.com intrepid/restricted Translation-sl
Prz http://si.archive.ubuntu.com intrepid/universe Translation-sl
Prz http://security.ubuntu.com intrepid-security/restricted Translation-sl
Prz http://security.ubuntu.com intrepid-security/universe Translation-sl
Prz http://security.ubuntu.com intrepid-security/multiverse Translation-sl
Zadetek http://security.ubuntu.com intrepid-security Release
Prz http://si.archive.ubuntu.com intrepid/multiverse Translation-sl
Zadetek http://si.archive.ubuntu.com intrepid-updates Release.gpg
Dobi:2 http://si.archive.ubuntu.com intrepid-updates/main Translation-sl [3173B]
Prz http://si.archive.ubuntu.com intrepid-updates/restricted Translation-sl
Prz http://si.archive.ubuntu.com intrepid-updates/universe Translation-sl
Prz http://si.archive.ubuntu.com intrepid-updates/multiverse Translation-sl
Zadetek http://si.archive.ubuntu.com intrepid Release                  
Zadetek http://si.archive.ubuntu.com intrepid-updates Release
Zadetek http://security.ubuntu.com intrepid-security/main Packages
Zadetek http://si.archive.ubuntu.com intrepid/main Packages     
Zadetek http://security.ubuntu.com intrepid-security/restricted Packages
Zadetek http://security.ubuntu.com intrepid-security/main Sources
Zadetek http://security.ubuntu.com intrepid-security/restricted Sources
Zadetek http://security.ubuntu.com intrepid-security/universe Packages
Zadetek http://security.ubuntu.com intrepid-security/universe Sources
Zadetek http://security.ubuntu.com intrepid-security/multiverse Packages
Zadetek http://si.archive.ubuntu.com intrepid/restricted Packages
Zadetek http://si.archive.ubuntu.com intrepid/main Sources
Zadetek http://si.archive.ubuntu.com intrepid/restricted Sources
Zadetek http://si.archive.ubuntu.com intrepid/universe Packages
Zadetek http://si.archive.ubuntu.com intrepid/universe Sources
Zadetek http://si.archive.ubuntu.com intrepid/multiverse Packages
Zadetek http://si.archive.ubuntu.com intrepid/multiverse Sources
Zadetek http://si.archive.ubuntu.com intrepid-updates/main Packages
Zadetek http://si.archive.ubuntu.com intrepid-updates/restricted Packages
Zadetek http://si.archive.ubuntu.com intrepid-updates/main Sources
Zadetek http://si.archive.ubuntu.com intrepid-updates/restricted Sources
Zadetek http://si.archive.ubuntu.com intrepid-updates/universe Packages
Zadetek http://si.archive.ubuntu.com intrepid-updates/universe Sources
Zadetek http://si.archive.ubuntu.com intrepid-updates/multiverse Packages
Zadetek http://si.archive.ubuntu.com intrepid-updates/multiverse Sources
Zadetek http://security.ubuntu.com intrepid-security/multiverse Sources
Dobljenih 6346B v 0s (8093B/s)
Branje seznama paketov... Narejeno
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti        
Reading state information... Narejeno
0 nadgrajenih, 0 na novo name&#353;&#269;enih, 0 bo odstranjenih in 0 ne nadgrajenih.
miha@miha-desktop:~$ 

```

Yes I did a full update after I installed it. Sorry the above isn't in English but it says that there are no upgrades :D

---

### Post by thtrgremlin on 2009-03-01
Ok, a thought is that on first startup, the window manager is freezing, and doesn't do a fallback until you do a ctrl-alt-backspace. My guess is that you have your WM set to compiz, and after the ctrl-alt-backspace, it is falling back to metacity whick it would stay at even after logout, but not saved between reboots.

We can confirm this by starting up, and when it freezes to the desktop, run the following from a terminal (ctrl-alt-F1) while it is "frozen"

```
top -bn1 | egrep 'compiz|metacity'
```

then go back to your VT (ctrl-alt-F7), and restart X server and login at the GDM. Once your desktop loads and everything works, go back to the terminal and run the same code above again. I am going to bet that the output will not be the same.

If so, then that would confirm my suspicion. You either need to update your graphics driver:```
/usr/bin/jockey-gtk
``` or change your default window manager: System -> Preferences -> Appearance -> Visual Effects and set to "None".

In my case, if I remember correctly, updating the driver fixed the problem. Also, you having a ATI Radeon 9600SE is likely why compiz was on by default, and if using the default driver, subsequently failed.

---

### Post by thtrgremlin on 2009-03-01
Looking at a number of other pages, apparently the Ati 9xxx series encourages ubuntu to use compiz by default, but that the proprietary driver is required. This was a bug in 7.10, and while the problems didn't exhibit themselves in exactly the way you described, it looked similar.

Intermittent problems SUCK! but this makes sense  :) Here's hoping.

---

### Post by flamer on 2009-03-01
When it's frozen:

```
 5595 miha      20   0  1844  552  452 S    0  0.1   0:00.00 compiz             
 5664 miha      20   0 21820  13m 5844 S    0  1.4   0:01.56 compiz.real        
 5675 miha      20   0  1844  524  440 S    0  0.1   0:00.00 compiz-decorato    
```

after X server is restarted:
```

 6864 miha      20   0  1844  552  452 S    0  0.1   0:00.00 compiz             
 6942 miha      20   0 21776  13m 5872 S    0  1.4   0:01.74 compiz.real        
 6944 miha      20   0  1844  520  440 S    0  0.1   0:00.00 compiz-decorato    
```


The second command shows the Hardware Drivers with the ATI FGLRX driver activated. You've got me thinking. I will remove the FGLRX driver and use Envy to install graphic driver:)

Even if I set the desktop effect to None, the system still freezes.

---

### Post by Kevbert on 2009-03-01
Please try running memtest from the boot menu.

---

### Post by flamer on 2009-03-01
Installed driver by using Envy - No success :(

Kevbert - will try  and post results later.

---

### Post by thtrgremlin on 2009-03-01
when Visual Effects are set to "None", is it still running compiz, or is it running metacity? Instead of just checking the window manager, see if there is any differences between what processes are running between the bugged session and working session.

I am pretty sure there is some setting that is "falling back" when you hit ctr-alt-backspace. Guess it could be the driver just as well.

Sorry, I am about out of ideas.

Personally, I find it unlikely it is a physical problem with your ram. This is a very consistent problem, and not the kind of error you get with bad memory, imho and personal experience.

Hope I was able to help enough to prove what it isn't such that the real solution is revealed to you. Look forward to seeing you post "IT WORKS!!!" soon, and hear what the issue was.

---

### Post by flamer on 2009-03-01
Memtest returned no errors.

---

### Post by thtrgremlin on 2009-03-01
If you are lost for random, throw them out there ideas to try, might I suggest when grub starts, edit your line with the kernel options and remove 'splash' and 'quiet'. This will let you see if anything is failing at startup. Further, while I can't understand how it would necessarily be related:

1) try resetting your bios options to factory default
2) change 'suspend mode' type in the bios to 'none' or 'off'
3a) Add the kernel option 'noacip'
3b) Add the kernel option 'acpi=off'
4) in /etc/fstab, for your root drive, add the option 'noatime'

*3 - try mixing these in each of their possible combinations. It is preferable to not use these options, but can be necessary if they have [buggy / out of date firmware]("http://www.linuxquestions.org/questions/linux-software-2/difference-between-noapic-and-acpioff-kernel-parameters-454675/").

These are separate suggestions, and as I mentioned, just things that I would try if it was my computer, just in case, and if I couldn't think of anything else more obvious worth trying in the mean time.

If you are curious what any of those things actually does or wondering why I mention them, happy to go into more detail. Also, if you are not sure how to do any of the things mentioned above, can give better directions. Just didn't want to throw too much out there in case you were already familiar with those things.

Note: ```
sudo top -bn1 | tee foo1.txt
``` will take all our currently running processes and save them to the text file foo.txt. Just make it foo2.txt for after the re-login to be able to compare.

---

### Post by flamer on 2009-03-01
**thtrgremlin**, I really appreciate your effort. I did a clean install again and everything works now :)

---

### Post by thtrgremlin on 2009-03-01
Sometimes that is the easiest way to go. Guess this will just be a mystery. Happy its working now.

Happy to help... even if it was just to conclude starting over.

Take care

---

