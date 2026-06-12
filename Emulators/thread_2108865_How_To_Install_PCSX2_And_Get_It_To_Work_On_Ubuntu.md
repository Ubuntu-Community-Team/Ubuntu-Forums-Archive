---
title: "How To Install PCSX2 And Get It To Work On Ubuntu"
date: 2013-01-25
forum: Emulators
---

### Post by CrystalDreamer59 on 2013-01-25
Hi I'm having trouble installing the emulator PCSX2 and getting it to work. It was working fine under windows OS but I thought it would be better to switch to Ubuntu since it's free. I really want to be able to play my kingdom hearts game on my Ubuntu computer. Here are my specs the best I know them incase you're wondering. 

computer model: HP Pavilion dv6
OS: Ubuntu 12.10 32 bit 
graphics: AMD Radeon 6700M series 
processor: intel core i7

can anyone help me. By the way I'm a complete beginner so nothing too difficult.

---

### Post by Lightning Dragon on 2013-01-25
Hello,

What is exactly happens when you try to run the emulator or the game? We will need details on the issues in order to offer our best assistance.

---

### Post by CrystalDreamer59 on 2013-01-25
I install it through the terminal using these instructions [http://www.eurobytes.nl/tutorials/pcsx2-under-ubuntu.html](http://www.eurobytes.nl/tutorials/pcsx2-under-ubuntu.html) 

Then I select to open though plugin instead of an .iso and when I put my game disc inside my computer and I get a blank/black screen but I can hear some noise. What am I doing wrong do I have to make an .iso of my game. Also how can I get the playstation menu to show up so I can format the memory cards. I prefer to use the virtual memory cards to save states. By the way everything worked fine with a little tweaking when I had a windows 7 OS. I don't want to go back to windows if I have to since windows isn't free to upgrade and open source and isn't as customizable as Ubuntu.

---

### Post by Lightning Dragon on 2013-01-25
Hello,

So you have the DVD driver plugin? What kind of noises are they? Of the game, or do they sound more like system error sounds?  Yes, you should try making an ISO of the game.  You can easily do that through Brasero. But you can also use AcetoneISO to make an ISO like so;

[IMG]https://lh3.googleusercontent.com/B3XNgU47_Z3aZ7oZnBL2TUwZNfYsUFlXRtIX5LCVO5bRBCm5Ph55dUO2cQWEvsqlGPjtJX3S1CSdX3fFXunHVrCZXw=s512[/IMG]

If the ISO doesn't work, then we will have to look into your settings. Do you have the BIOS? You can't play without it. Also, have you tried pcsx2-unstable? It might work for you better.

---

### Post by CrystalDreamer59 on 2013-01-25
I hear what sounds like the playstation starting up and I'll make an .iso of my kingdom hearts game and find out if that works.

---

### Post by Lightning Dragon on 2013-01-25
Hello,

Alright, I hope it works. But I need to ask if you have the following things or have updated them;

Your drivers
The BIOS for the system
Mesa installed (Latest is 8.0.4 I think)

It really sounds like a driver issue to me. I heard nouveau works with people who experience this problem.

But see if this can fix your issue; 

[http://www.youtube.com/watch?v=IrnYlSXhGs0](http://www.youtube.com/watch?v=IrnYlSXhGs0)

Since you are a beginner I highly suggest you read the [Ubuntu Pocket Guide]("http://www.ubuntupocketguide.com/index_main.html"), or [the manual]("http://ubuntu-manual.org/") to get you started.

---

### Post by CrystalDreamer59 on 2013-01-25
I made an .iso of the game and when I tried to start it up the program froze. I agree that it might be a driver problem, but I don't know where to get drivers for Ubuntu and how to install them. I'll try nouveau and see if that works.

---

### Post by CrystalDreamer59 on 2013-01-25
I changed my graphics plugin to ZZ Ogl PG  0.4.0 [libzzogl-0.4.0] and now when I run the .iso of my game I get a blank/black screen with some sound again. What should I do.

---

### Post by Lightning Dragon on 2013-01-25
Hello,

Definitely sounds like a driver issue. The same thing happens to people with Intel in Ubuntu. Okay, see this link to learn how to install AMD drivers;

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by CrystalDreamer59 on 2013-01-26
I'm having trouble with the tutorial when I install fglrx and restart my computer I get nothing but the wall paper and have to reinstall Ubuntu and it's getting really late where I'm at so I can't keep restoring Ubuntu.

edit: I was following the wrong tutorial. I had to follow the one for hybrid graphic cards. Now my PCSX2 seems to be working fine

---

### Post by Lightning Dragon on 2013-01-26
Hello,

You should have told me it was doing that instead of having to reinstall Ubuntu every time. There could have been a way to uninstall fglrx through the Command Line and fix the issue. 

Did you install via the official drivers from AMD's website, or did you use the terminal method listed on the link I gave you? The issue, if you are lucky, is caused by using the wrong driver. So which did you use?

I was hoping you would not encounter any driver issues, especially with AMD as I don't have that. Perhaps a AMD user can help you, like [Thee (he seemed to have set it up he says in the WoW thread).]("http://ubuntuforums.org/showpost.php?p=12474837&postcount=2503")

---

### Post by CrystalDreamer59 on 2013-01-26
I used a driver from the website. Now everything is working fine except that when I use the onepad plugin to configure my xbox360 controller the joysticks won't work. I configure the top left joystick as the left joystck and I configure the bottom right joystick as the right joystick. I downloaded the xbox360 controller driver so what am I doing wrong.

---

### Post by CrystalDreamer59 on 2013-01-26
Apparently I can't have both the d pad and joysticks configured at the same time on my xbox360 controller using the plugin that came with the linux version of PCSX2. What should I do. Do I need to configure my controller. if so can someone give me step by step instructions.

---

### Post by CrystalDreamer59 on 2013-01-26
by the way when I type xboxdrv to access my xbox 360 controller driver in the terminal I get this error message at the bottom 

-- [ ERROR ] ------------------------------------------------------
USBController::USBController(): libusb_open() failed: LIBUSB_ERROR_ACCESS

I checked and I already have libusb so what's wrong.

---

### Post by Lightning Dragon on 2013-01-26
Hello,

I'm glad you got the screen to work! I'm not sure about why you can't have both of them configured at the same time. It could be because it is a console controller, and not a PC controller. I can find some links for you, but other than that, I haven't the foggiest.

[http://forums.ngemu.com/showthread.php?t=88797](http://forums.ngemu.com/showthread.php?t=88797) (has the same problem as you)
[http://ubuntuforums.org/showthread.php?t=2026231](http://ubuntuforums.org/showthread.php?t=2026231)
[http://www.youtube.com/watch?v=tpJBu96V6do](http://www.youtube.com/watch?v=tpJBu96V6do)
[http://forums.pcsx2.net/Thread-PCSX2-0-9-6-xbox-360-controller](http://forums.pcsx2.net/Thread-PCSX2-0-9-6-xbox-360-controller)
[http://forums.pcsx2.net/Thread-Using-Xbox-Controller-with-PCSX2-1-0](http://forums.pcsx2.net/Thread-Using-Xbox-Controller-with-PCSX2-1-0)
[http://forums.pcsx2.net/Thread-Official-English-PCSX2-configuration-guide-v0-9-8](http://forums.pcsx2.net/Thread-Official-English-PCSX2-configuration-guide-v0-9-8)
[http://forums.ngemu.com/showthread.php?t=95007](http://forums.ngemu.com/showthread.php?t=95007)
[http://ubuntuforums.org/showthread.php?t=93407](http://ubuntuforums.org/showthread.php?t=93407)

---

### Post by CrystalDreamer59 on 2013-01-26
None of the links seem to work they all point to windows programs. I think I need to somehow configure my controller. I downloaded a program called jstest-gtk but I have no idea how to work it. it seems to be the only program out there for ubuntu for controllers.

---

### Post by Lightning Dragon on 2013-01-26
Hello,

Zeropad is for Linux, too (first link I gave you). It might be that you need to use a PS controller, not an Xbox controller, but I doubt that. Are you using a wireless Xbox controller that you just hooked up through a charger cable? I have had trouble with wireless controllers before, so if you are using one, try using a wired controller.

But, how about these;

[http://pcsx2.net/download/viewcategory/9-plugins.html](http://pcsx2.net/download/viewcategory/9-plugins.html)
[http://www.t2e.pl/en/406/134/406/DevBuild/7651/PSX-Pokopom-Xinput-Pad-Plugin-v20-r100#.UQSnxBz5mPs](http://www.t2e.pl/en/406/134/406/DevBuild/7651/PSX-Pokopom-Xinput-Pad-Plugin-v20-r100#.UQSnxBz5mPs) 
[http://forums.ngemu.com/downloads.php?do=cat&id=116](http://forums.ngemu.com/downloads.php?do=cat&id=116)

Plugins should still work in Linux, as they are for the emulator. 

As for jstest-gtk, please check these links;

[http://manpages.ubuntu.com/manpages/precise/man1/jstest-gtk.1.html](http://manpages.ubuntu.com/manpages/precise/man1/jstest-gtk.1.html)
[https://github.com/Grumbel/jstest-gtk](https://github.com/Grumbel/jstest-gtk)
[http://www.addictivetips.com/ubuntu-linux-tips/jstest-gtk-is-a-joystick-testing-and-configuration-tool-for-linux/](http://www.addictivetips.com/ubuntu-linux-tips/jstest-gtk-is-a-joystick-testing-and-configuration-tool-for-linux/)
[http://pingus.seul.org/~grumbel/jstest-gtk/](http://pingus.seul.org/~grumbel/jstest-gtk/)
[http://www.ubunturoot.com/2012/08/how-to-setup-joystickgamepad-in-ubuntu.html](http://www.ubunturoot.com/2012/08/how-to-setup-joystickgamepad-in-ubuntu.html)

[SIZE=1]Let me hook up this emulator, put in my Xbox controller and see if I can figure some things out for you. It might take me a while if I get the same screens, but I'll report back if the above doesn't help you any.[/SIZE]

---

### Post by CrystalDreamer59 on 2013-01-26
I think the problem is the plugin so I downloaded the pokopom file on the first link but I have no idea how to install it on Ubuntu.

edit: I found an ubuntu version of the pokopom file but when I try to put it in the directory where my plugins are I get a message saying I don't have permission to put the file in the folder

---

### Post by Lightning Dragon on 2013-01-27
Hello,

It is a plugin, so there is no installation like installing a program--or so that's how plugins worked the last time I used the emu. You drag it into the plugin folder of the emulator, refresh the folder and then open the emulator and set up the plugin that way. See these links;

[http://forums.pcsx2.net/Thread-Pokopom-KrossX-s-Pad-Plugin](http://forums.pcsx2.net/Thread-Pokopom-KrossX-s-Pad-Plugin)
[http://forums.pcsx2.net/Thread-Configuration-s-for-XBOX-Controller](http://forums.pcsx2.net/Thread-Configuration-s-for-XBOX-Controller)

And consider reading the Official English Guide for the emulator;

[http://pcsx2.net/config-guide/official-english-pcsx2-configuration-guide.html](http://pcsx2.net/config-guide/official-english-pcsx2-configuration-guide.html)

---

### Post by CrystalDreamer59 on 2013-01-27
I can't get my file in the folder where my plugins are. I don't have permission. How do I get permission.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

Open the terminal and type "gksudo nautilus". A window will pop up with an orange tab above the file directory, indicating you are in root permissions. Now you will be able to add, delete or change files.

---

### Post by CrystalDreamer59 on 2013-01-27
Okay I typed in what you said in the terminal and I was able to get the file into the folder, but when I click configure I don't get anything. By the way I'm sorry if I'm a total noob.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

Do not worry, and there is no need to apologize. Everyone has something they do not know, that does not make you a noob/newb. I like to offer assistance, anyway. 

As for the issue, does the configuration window not pop up, or does it not allow you to change anything? And you made sure that you are trying to configure within PCSX2, right?

---

### Post by CrystalDreamer59 on 2013-01-27
the configure window does not pop up at all. and I'm trying to configure within PCSX2.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

Weird! In Linux Mint, it pops up. Okay, does switching back to default PAD configure plugin make the window pop back up? Does the bug box (white box) report any problems? It should tell you if something is wrong.

---

### Post by CrystalDreamer59 on 2013-01-27
no I get no errors in the log says plugins loaded successfully.

edit now I get an error when I try to boot up the emulator

---

### Post by CrystalDreamer59 on 2013-01-27
When I switch back to the original pad plugin everything works fine again.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

And you are sure you are a 32 bit computer, right? Are you using the 32bit .so file not the 64bit .so file? And did you place the file in the plugins folder correctly?

For the 32bit .so file; [http://forums.pcsx2.net/attachment.php?aid=42095](http://forums.pcsx2.net/attachment.php?aid=42095)

edit

What kind of error? Black screen with sound, or something new?

edit 2

Oh, my bad, Pokopom does not allow configuration. It automatically configs, or so it says. That's why it won't allow you. It makes up the settings for you, for solution purposes. But if you can't get the game to work, we can't test the controls. Hmm.

---

### Post by CrystalDreamer59 on 2013-01-27
yes I'm using a 32 bit OS and I'm using the 32 bit version of the file. Originally my computer had a 64 bit windows 7 OS. I think the problem is when I type "gksudo nautilus" in the terminal I don't know how to close it correctly. how do I do that. I know I don't just close the terminal. By the way I get a separate white screen with some kind of error message and the program freezes up.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

I usually close the window the command opens first, and then type the command "exit". That shuts down the terminal. When do you get the error screen? Inside the emulator, or does this happen when you perform the sudo commands?

Do you think you could get an image of the error, or copy the error message for us? It could be because the emulator does not support 12.10--at least according to gregory;

[http://code.google.com/p/pcsx2/wiki/CompilationGuideForLinux#Package_build_system](http://code.google.com/p/pcsx2/wiki/CompilationGuideForLinux#Package_build_system)

See if getting the plugins from this video helps you; [http://www.youtube.com/watch?v=1y8dYlBWOh4](http://www.youtube.com/watch?v=1y8dYlBWOh4) and then check to see if the game you are even attempting to play is compatible with the emulator yet, even your controller.

If all else fails, I seriously suggest asking gregory or the forums about this. They will be able to provide you with better help then this forum. 

[http://forums.pcsx2.net/Thread-PCSX2-for-Debian-Ubuntu](http://forums.pcsx2.net/Thread-PCSX2-for-Debian-Ubuntu)

---

### Post by CrystalDreamer59 on 2013-01-27
okay I closed the terminal like you said and I got this 

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

how do I enable user sharing?

---

### Post by Lightning Dragon on 2013-01-27
Hello,

If you properly used the command "gksudo nautilus" then you shouldn't be experiencing any problems when quitting it. I'm not sure why you are getting that error, so I can't be of much help to that.

But you can try this; [http://ubuntuforums.org/showthread.php?t=878321](http://ubuntuforums.org/showthread.php?t=878321)

---

### Post by CrystalDreamer59 on 2013-01-27
I seemed to have solved the problem but I'm still not getting the configuration settings to come up

---

### Post by Lightning Dragon on 2013-01-27
Hello,

The plugin I led you too is already set (you can't configure it), so if you can't get the game to open with that plugin, switch back to the default plugin. 

Here, try this for your Xbox controller; 

[http://ubuntuforums.org/showthread.php?t=2026231](http://ubuntuforums.org/showthread.php?t=2026231)
[http://www.ehow.com/how_8725674_make-linux-use-xbox-controller.html](http://www.ehow.com/how_8725674_make-linux-use-xbox-controller.html)
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

---

### Post by CrystalDreamer59 on 2013-01-27
I'm finally getting a working screen with the plugin, but it's very slow. Is there another pad plugin for Ubuntu/linux

---

### Post by CrystalDreamer59 on 2013-01-27
by the way I have a .dll file of the pokopom plugin will that work. If so where should I put it.

---

### Post by CrystalDreamer59 on 2013-01-27
okay I managed to find another plugin that should work with ubuntu but I need to compile the files. the plugin is called padwin. unfortunately I can't upload the files as there are too many in the folder, but you can download it here and see if you can figure it out for me.  [http://emulationrealm.net/modules/wfdownloads/singlefile.php?cid=270&lid=344](http://emulationrealm.net/modules/wfdownloads/singlefile.php?cid=270&lid=344)

---

### Post by Lightning Dragon on 2013-01-27
Hello,

No. The files must be .so files, not .dll files. Windows would use .dlls. Here is the PADwin.so file. I went ahead and compressed the rest of the .so files I had and uploaded them, too.

Place the ".so" files, if you haven't found the right folder, into the pcsx2 folder where the rest of the .so files are. For me, the location is;

/usr/lib/games/pcsx2

Inside the last folder there should be some .so files. This is where you place them.

*Please don't forget to mark the thread solved _**if**_ it gets the problem cured and which solution it was that worked.

---

### Post by CrystalDreamer59 on 2013-01-27
Zeropad plugin seems good but it won't recognize my controller. Do you have the latest version for Linux which might recognize my controller.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

I posted some links to the Xbox drivers for Linux a page or two back. What kind of controller are you using? Official brand that comes with the Xbox, or another brand like AfterGlow? And you made sure to turn the emulator off, plug in the controller and then restart the emu, right? I find that it won't recognize controllers if you plug it in while the emu is already running.

---

### Post by CrystalDreamer59 on 2013-01-27
I'm using a madcatz xbox360 controller not a regular kind. I'll try the driver thing on page 2 but it seems a bit complicated. I'll also try what you suggested.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

If the drivers I post resolves nothing for you, please see these links;

[http://ubuntuforums.org/showthread.php?t=1667997](http://ubuntuforums.org/showthread.php?t=1667997)
[http://ubuntuforums.org/showthread.php?t=717079](http://ubuntuforums.org/showthread.php?t=717079)
[https://bbs.archlinux.org/viewtopic.php?id=74384](https://bbs.archlinux.org/viewtopic.php?id=74384) (Arch, but I think it might help)

And in case I did not post it a while back because I spazzed;

[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

Otherwise, I would suggest getting a wired Xbox 360 brand. Or perhaps use a wired PS3 controller or a PC controller.

---

### Post by CrystalDreamer59 on 2013-01-27
These links are too hard for me to understand. I'll go look for something else. By the way my controller is wired.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

Yes, it may be, but it is a Madcatz controller, so it isn't the same. At least not in my experience.

Go to this link: [http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

And follow the instructions below "Binary Package Download". 

If that doesn't work, please follow this instead; [http://packages.ubuntu.com/precise/i386/xboxdrv/download](http://packages.ubuntu.com/precise/i386/xboxdrv/download)

Tell me if that helps.

---

### Post by CrystalDreamer59 on 2013-01-27
I already have xboxdrv installed so I don't know what is wrong.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

The site should be able to help you with xboxdrv. It is most likely because it is Madcatz. The only solutions I could find concerning that brand of controller were the previous links concerning compiling and whatnot.

---

### Post by CrystalDreamer59 on 2013-01-27
I just played a little but of a gamecube game on dolphin and both d pad and analog sticks seem to work together on dolphin.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

But this is PCSX2, so what works in Dolphin might not work in PCSX2 and vice-versa. I do believe development on PCSX2 isn't even being done any more, so it could still be unstable in the PAD plugins department, especially for Linux.

---

### Post by CrystalDreamer59 on 2013-01-27
I really don't want to have to switch back to windows would it help if I was to get a different game pad. which game pad works best on Ubuntu.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

Well, I see a lot of users saying they are using a Logitech controller. Wired Xbox and Afterglow PS3 controllers work, too. I have personally used them. But you can check out these threads;

[http://ubuntuforums.org/showthread.php?t=1676206](http://ubuntuforums.org/showthread.php?t=1676206)
[http://ubuntuforums.org/showthread.php?t=1615200](http://ubuntuforums.org/showthread.php?t=1615200)
[http://ubuntuforums.org/showthread.php?t=1454950](http://ubuntuforums.org/showthread.php?t=1454950)
(HOWTO) [http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)

If you have a friend with either of those controllers, ask him/her if you could borrow them just to see if they work in the system.

---

### Post by CrystalDreamer59 on 2013-01-28
I've checked best buy's website and our local best buy has the logitech controller mentioned in the first link. I could go there and buy it (it's not that much) and see how it works. But first I'm going to switch to the latest version of Mint and see if that works.

---

### Post by Lightning Dragon on 2013-01-30
Hello,

I would highly suggest going for Maya, not Nadia. Maya will offer long time support, and will probably not have as many sound and driver related issues as Mint Nadia does.

I wish you good luck with the controller. Remember to keep the receipt—it might not work.

---

