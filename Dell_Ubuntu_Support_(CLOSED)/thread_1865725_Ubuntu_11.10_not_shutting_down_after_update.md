---
title: "Ubuntu 11.10 not shutting down after update"
date: 2011-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by varunsaini on 2011-10-20
Hi,
 
I have Dell N5010 (Inspiron 15R). I upgraded to Ubuntu 11.10 as soon as it hit the market. It was working fine but from last 1-2 days my machine is not shutting down. It is stuck on UBUNTU icon. I have to force shut down from power button. I have windows on my laptop and it is shutting down properly.
 
Please advice.
 
Thanks,
Varun

---

### Post by tigeronk2 on 2011-10-21
Same problem. Dell Inspiron N5030.

---

### Post by tigeronk2 on 2011-10-21
I tried ...

sudo shutdown now -P

... and it worked. Better than using the power button to force shutdown. See if it works for you.

---

### Post by varunsaini on 2011-10-21
Thanks, Will try that, but it is strange, need some update from Ubuntu team.

---

### Post by naglis on 2011-10-24
Same here. Dell Latitude E6500.

Not sure what causes it.

---

### Post by Ceipheed on 2011-10-25
Similar problem here. sometimes  it gets stuck, sometimes it will work fine.

Studio 15

---

### Post by Andik79 on 2011-10-29
The same problem. AMD Athlon X4.

---

### Post by JoZ3 on 2011-10-31
> **Ceipheed said:**
> Similar problem here. sometimes  it gets stuck, sometimes it will work fine.

Studio 15

Same problem here, AMD Phenom II x3, ati HD4850, 8gb ram

---

### Post by crjackson on 2011-10-31
I've got the same problem on 7 different machines. Desktops and Laptops, Intel and AMD, nVIdia, ATI and Intel video...

Most everyone in the house is moving back to windows it's becoming so annoying.

I'm shutting the down using sudo shutdown -P now but the wife and kids won't mess with that. They want to click a button and walk away.

---

### Post by rv65 on 2011-11-02
This bug does need to be fixed. I can't even get mine to shut down properly, but my D610 works great with 11.10.

---

### Post by clayclai on 2011-11-02
Same problem here on a Samsung N150 Plus netbook

---

### Post by matt_symes on 2011-11-02
Hi

Did all you guys upgrade from 11.04 -> 11.10 or was it a fresh install ?

Kind regards

---

### Post by rv65 on 2011-11-02
I did an upgrade and not a fresh install.

---

### Post by crjackson on 2011-11-02
Clean Install - Several of them

---

### Post by Chris220tri on 2011-11-04
Same problem here - my Dell D620 laptop shuts down nicely but the Desktop (Asus P5W-DH, HD 4670) won't.  Both are on 11.10 via a fresh install.  Very frustrating!

---

### Post by gianninardoia on 2011-11-04
Same problem on Dell M90 (upgrade).
bye.

---

### Post by crjackson on 2011-11-05
Okay, with the help of user [matt_symes]("http://ubuntuforums.org/member.php?u=1067998"), here's what I did. Open up a text editor and make 2 bash scripts. One with the first line of code, one with the second. Name the one that ends with stop to "shutdown", and the other one "restart". Make sure each is executable and you can (if you want to) browse to the shutdown / restart icons and assign to each script.

These are working flawlessly for me, and are decent looking on the desktop too.

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```

---

### Post by Chris220tri on 2011-11-06
I didn't do anything but the Asus P5W-DH is now shutting down gracefully - I'm not sure if it was fixed with an update?  Anyway - its alll good :) :D

---

### Post by nebula12 on 2011-11-06
i have a latitude E5420, but my problem is reversed. when i shut it down graphically it usually shuts down properly.. but when i'm using terminal it stucks after the ubuntu icon, at a black display with white letters

---

### Post by ranjit. on 2011-11-06
I have the same issue, some times when giving shutdown from the GUI, the system gets logged off instead from the GUI and comes to the login screen, Some times the splash screen shows and once it stayed there for hours:confused: now thats really annoying, I used to give halt from the terminal when problems occur, but now i will try sudp shutdown now -p

---

### Post by kingcharles1666 on 2011-11-06
> **crjackson said:**
> Okay, with the help of user [matt_symes]("http://ubuntuforums.org/member.php?u=1067998"), here's what I did. Open up a text editor and make 2 bash scripts. One with the first line of code, one with the second. Name the one that ends with stop to "shutdown", and the other one "restart". Make sure each is executable and you can (if you want to) browse to the shutdown / restart icons and assign to each script.

These are working flawlessly for me, and are decent looking on the desktop too.

```
dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop
```


This is a workaround and not a fix. I have the same shutdown problem on a HP DV6500

Did somebody file a bug report for this problem?
Thanks

---

### Post by crjackson on 2011-11-06
> **kingcharles1666 said:**
> This is a workaround and not a fix. I have the same shutdown problem on a HP DV6500

Did somebody file a bug report for this problem?
Thanks

Sorry, I didn't realize I said it was a fix. It was meant to be a workaround and to help out. I guess I shouldn't have offered up my personal arrangement.

---

### Post by kingcharles1666 on 2011-11-06
> **crjackson said:**
> Sorry, I didn't realize I said it was a fix. It was meant to be a workaround and to help out. I guess I shouldn't have offered up my personal arrangement.

I am glad that you provided the workaround so thanks for that. I didn't mean to criticize.  I just wanted to ensure that this bug gets fixed properly. And a bug report starts that process. I had a quick look in launchpad and didn't find a similar bug. That's why I asked if someone on this thread had done so.

---

### Post by bunjamin on 2011-11-06
Hi,
 
I found [this bug]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240") in the Launchpad. ? the same problem. Sounds v. similar.
 
Regards.

---

### Post by linuxaddix on 2011-11-06
i have a dell inspiron e1505 and have never ran into problems with shutting down.try logging out first then clicking on the power button at the top right.

---

### Post by morganGDFP on 2011-11-07
I have a DELL LATITUDE E6520 with a similar problem..

I upgraded from 11.04 to 11.10 and now I am unable to shutdown or reboot my computer. No matter what I choose I end up at the login screen.
If I attempt to shutdown from login screen the screen goes black for a second and then I am back at login screen.

sudo shutdown now -P works.

---

### Post by gverrilla on 2011-11-07
power button works.
I won't use terminal.

---

### Post by crjackson on 2011-11-07
If you are affected by this bug, please login to launchpad and click on affects me too...

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240?comments=all](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240?comments=all)

---

### Post by jonbonjovi on 2011-11-07
Same problem for me: HP Dv-5 with a clean install of 11.10.

---

### Post by crjackson on 2011-11-08
> **jonbonjovi said:**
> Same problem for me: HP Dv-5 with a clean install of 11.10.

Please add yourself to the bug report so we can get some attention.

---

### Post by ballantony on 2011-11-14
Same here, Dell Inspiron 545.  About to add myself to the bug report...

---

### Post by uche.eke on 2011-11-15
Same here: HP Pavilion dm1-3100 series notebook running Ubuntu 11.10 solely. It was working fine up until a week or so ago.

---

### Post by prophetofpunk on 2011-11-15
Not sure if this helps anyone because i am a newbie to Ubuntu but what i did to fix this problem was i went into user accounts, unlocked the panel and set my automatic login to "ON" and restarted. then i changed it back to off and restarted and it now shuts down and restarts properly.

---

### Post by omiks3 on 2011-11-19
i have a dell inspiron m102z i have the same problem. have u guys tried updating the BOIS? it seems to of fixed it for me

---

### Post by nebula12 on 2011-11-19
i have a dell latitude e5420 and bios A01. there is an A03. how can i update it? may this fix the problem?

---

### Post by musguito on 2011-11-22
same problem to me, SONY vaio VGN-NR10M. hope it is fixed soon

---

### Post by fokuslee on 2011-11-24
for those on ati graphics
installing ati proprietary driver fixed the issue for me
i followed the make pkg method here 
[http://wiki.cchtml.com/index.php/Category:Installation_Documentation]("http://wiki.cchtml.com/index.php/Category:Installation_Documentation")
hope it helps you also

---

### Post by karalho on 2011-11-24
Same as here, same problem after upgrading to 11.10. What is going on UBUNTU?

---

### Post by G-D on 2011-11-29
Same problem on a Dell Vostro 2510 with the 64bit version.  "sudo shutdown now -P" in a terminal works every time but good grief!  This is a BASIC operating system task!  Everyone wants a new look or new features but never at the expense of quality.

---

### Post by Scott Baker on 2011-11-29
Seeing the same problem with a Dell M90 precision and clean install of 11.10. Sometimes I luck out, and my box will shut down. Other times, it's a crap shoot!! ](*,)

---

### Post by crjackson on 2011-11-30
> **Scott Baker said:**
> Seeing the same problem with a Dell M90 precision and clean install of 11.10. Sometimes I luck out, and my box will shut down. Other times, it's a crap shoot!! ](*,)

If you haven't done so already, please add yourself to this bug report [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240)

---

### Post by sonicb00m on 2012-01-03
I have ubuntu 11.10 installed on 4 different machines and the success of the shut down is a bloody lottery.

It's really really irritating!

---

### Post by crjackson on 2012-01-03
> **sonicb00m said:**
> I have ubuntu 11.10 installed on 4 different machines and the success of the shut down is a bloody lottery.

It's really really irritating!

Couldn't agree more....

---

### Post by SycloneMedia on 2012-01-03
What 'sometimes' works for me when it gets stuck, is to tap the power button (on the laptop)... this breaks up whatever clusterf*** is going on and it then proceeds to finally shutdown.

On my fresh new desktop build, same thing happens, HOWEVER...what I found is that if I let it auto shutdown (with the countdown timer) then it shuts down everytime.

Go figure... I hope this helps whatever developers are looking into this...:confused:

---

### Post by KingOss on 2012-01-12
hi people, i had the same problem until 10 seconds ago, when i discover where's the problem: libreoffice.
i was working on a text document and i see that the quickstart was enabled by default, when i disabled it the system shut down in the "normal" way, i maen using the shutdown button!
looking on the web i see that someone had the same problem for some error with the NTFS partition mount, so if you're sure that libreoffice quickstart is off and you still have the shutdown problem try to umount all the NTFS partition and try again.

So the problems can be:
**1. LibreOffice Quickstart**
how to fix: open Libreoffice, in Options>Libreoffice>Principal Memory (i hope is this, i'm using an italian version) and remove the checkmark of "Enable Quickstart".
Then close Libreoffice and check in the System Monitor if the quickstart process is running (the name is soffice.bin or soffice), if it's running just kill that.
now try to shutdown.

**2. NTFS partition mounted**
If the problem is not libreoffice, try to unmount all your NTFS partition, to do that with command line you can do these commands:
```
sudo fdisk -l
```it return something like that:
```
[...]
Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   364191727   182094840    7  HPFS/NTFS/exFAT
/dev/sda2       466591744   488392064    10900160+   7  HPFS/NTFS/exFAT
/dev/sda3       364191744   462043135    48925696   83  Linux
/dev/sda4       462045182   466589695     2272257    5  Esteso
/dev/sda5       462045184   466589695     2272256   82  Linux swap / Solaris
[...]
```now look in the last column for NTFS and do this command to unmount ALL the ntfs partitions (in my case is /dev/sda1 because sda2 is not mounted):
```
sudo umount /dev/sda1
```replace /dev/sda1 with your partition and do that for all your ntfs mounted partition.
now try to shutdown.

i hope that can help you! :)

---

### Post by SGAZ on 2012-01-23
I also was unable to use the GUI Shutdown or Restart options in 11.10 or in 11.04.  For me the issue was LibreOffice as well.

I used Ubuntu software center and Synaptic both to Completely remove LibreOffice and any of its residual configuration files or dependencies or add-ins.  Yeah Woo, I could shutdown and restart from within Unity again (for the first time ever actually).

I then used Ubuntu Software Center to install LibreOffice again and everything still worked fine.

The shutdown/restart process was looking for and not finding a file called soffice.desktop which was causing the shutdown/restart to fail with no error message in the GUI.  Uninstalling, reinstalling LibreOffice corrected this configuration problem.

---

### Post by castironpants on 2012-01-25
Where was this file supposed to be?

---

### Post by RememberWhenItRained on 2012-01-26
same problem. Dell Inspiron 1440 here.

it's a crapshoot.

  usu*sally sudo halt *works but

*sudo shutdown now* works only about 50/50.  When they don't work, it freezes on the purple screen with the orange logo and dots

---

### Post by SGAZ on 2012-01-30
(@CastIronPants)  
Here is the Syslog Content that I should have included in my above post (sorry about that) :  These entries matched the timestamps from my failed "Gui" Shutdown attempts. (My syslog doesn't go back to prior to the change so I scraped these lines out of [**another post**]("http://ubuntuforums.org/archive/index.php/t-1865955.html") in these Forums.)

[INDENT]WARNING: Unable to load desktop file '/usr/lib/libreoffice/program/soffice.desktop': No file or folder of this kind
WARNING: Unable to find desktop file 'soffice.desktop': Unable to find a valid keys file in the search folders
WARNING: Unable to find desktop file 'gnome-/usr/lib/libreoffice/program/soffice.desktop': Unable to find desktop file 'soffice.desktop': Unable to find a valid keys file in the search [/INDENT]

To clarify my particular situation, I removed OpenOffice and installed LibreOffice as soon as it forked.  I installed LibreOffice from Deb again when they changed the install locations.  After that I upgraded to 11.04 and then again to 11.10.  Somewhere in there Ubuntu made LibreOffice the default Office Installation. So, I am not surprised there may have been residual configuration issues in my case.

It's been a week now and all is still working like it is supposed to.

---

### Post by feistybird on 2012-01-31
> **varunsaini said:**
> Hi,
 
I have Dell N5010 (Inspiron 15R). I upgraded to Ubuntu 11.10 as soon as it hit the market. It was working fine but from last 1-2 days my machine is not shutting down. It is stuck on UBUNTU icon. I have to force shut down from power button. I have windows on my laptop and it is shutting down properly.
 
Please advice.
 
Thanks,
Varun

Add "acpi=force" in the kernel command line fixed the similar problems I had, see:  [http://ubuntuforums.org/showpost.php?p=11437602&postcount=25](http://ubuntuforums.org/showpost.php?p=11437602&postcount=25)

---

### Post by rvishu on 2012-03-02
Same problem.

Ubuntu 11.10 (64-bit)
DELL Studio 1558
4 GB RAM
ATI Radeon graphics

Dual boot with WIN 7 Home Premium (64-bit)

---

