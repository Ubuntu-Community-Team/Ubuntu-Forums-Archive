---
title: "HOWTO: Seamless MS Windows in Edgy with VirtualBox and Beryl!"
date: 2007-05-04
forum: Desktop Effects &amp; Customization
---

### Post by mikeytag on 2007-05-04
Alright, I have finally done it. I have integrated Windows XP Professional into my Ubuntu desktop using VirtualBox. Words cannot begin to describe how incredibly sweet and productive this kind of setup is. Imagine being logged into your Ubuntu desktop and whenever you want to run a Windows app you simply click on the Windows Start Menu at the bottom of your screen and run it. Well that's what this guide will walk you through setting up. Take a look at this screen shot to get an idea for what I am talking about:

[IMG]http://www.creditlearningcenter.com/images/seamless_screenshot.png[/IMG]

Imagine if you are a developer that needs to run Visual Studio repeatedly. Or maybe you are a web developer like me that goes into Flex and Flash occasionally. (Both are products from Adobe with no Linux port, you will see from the screenshot that I am running Photoshop 9 CS2 like this)  Needless to say, having this setup would help you save a lot of time, if not solely for the purpose of impressing your friends. Oh, and to top it all off, it runs under Beryl just fine. Almost all the effects in Beryl affect the other windows. (See bottom of guide to find out which effects won't work)

There are some limitations, like full 3D support for games and such, but for the most part it runs all Windows programs flawlessly. Also, as a side note I was able to get this whole configuration working using Edgy. There are a few issues that could pose problems in Feisty, mainly Network Manager messing with the config. I will post another tutorial for Feisty when I get the chance to upgrade my desktop.

[SIZE="5"]Step 1: Install and Configure VirtualBox[/SIZE]
VirtualBox is one of the best virtualization apps I have ever seen. I put it right up there against VMWare Workstation, and it tends to perform better in my opinion.
In Edgy, you can download and install VirtualBox by either using Automatix ([http://www.getautomatix.com](http://www.getautomatix.com)) or by installing the .deb from [http://www.virtualbox.org](http://www.virtualbox.org)
I personally installed it through Automatix and find that the easiest route as it makes sure you have everything else you need for it. You can find VirtualBox under the Virtualization section of Automatix.

Ok, once you have VirtualBox installed we are going to make a new virtual machine.
[SIZE="4"]Step 1a: Setting Up a Virtual Machine [/SIZE]
[LIST]
[*]Open up the VirtualBox app by selecting it from Applications->System Tools->InnoTek VirtualBox.
[*]Click the &#8220;New&#8221; button at the top to bring up the New Virtual Machine Wizard.
[*]Click Next
[*]Type in a name for your Windows installation. I labeled mine: Windows XP Professional, but you can name yours whatever you feel like.
[*]Choose your Os Type from the dropdown. (Important note: this seamless setup will only work with a version of Windows that can act as a Terminal Server that means XP Pro NOT Home, and Vista Business or Ultimate, Windows Server 2003, and/or Windows 2000 Professional)
[*]Next adjust your base memory size. VirtualBox recommends 192MB for Windows XP, but I personally find that XP runs a bit slow at this level. I have 2GB of RAM on my machine so I gave XP 600 MB. Choose whatever amount you are comfortable with, and this can always be adjusted later.
[*]Next we will choose our &#8220;hard disk&#8221; to boot into. Click the &#8220;New&#8221; button unless you already have a VirtualBox image ready, then click the &#8220;Existing&#8221; button.
[*]After clicking New, you will be greeted by the Virtual Disk Wizard, click Next
[*]Choose whether or not you want a Dynamically expanding image. I personally like using it because I am not entirely sure how much space I will use, but that it is up to you. After choosing, click Next.
[*]Pick a name for your image file and adjust the size to the amount of space you would like to offer for your drive. Then click Next.
[*]To finish the new drive creation click Finish
[*]Your new disk you just created should be selected, click Next.
[*]Click Finish to complete setting up your new Virtual Machine
[/LIST]

[SIZE="4"]Step 1b: Configuring Your Virtual Machine[/SIZE]
[LIST]
[*]Select your new machine from the list of machines on the left and click the Settings button at the top of VirtualBox.
[*]Select CD/DVD-ROM and click Mount CD/DVD Drive, then choose whether or not you would like to mount your physical CD drive or an iso file. ( I personally ripped my XP Install CD to an ISO file because I think the install goes faster than off the physical CD)
[*]Now, select Network and from the &#8220;Attached to&#8221; dropdown box select Host Interface. In the Interface Name field type in: tap0
[*](This will make more sense later)
[*]Now, select Remote Display and check Enable VRDP Server.
[*]Finally, click the OK button to save all of these settings.
[/LIST]

Ok, we now have our VirtualBox Machine ready to boot up and install windows, however we are going to configure a few things on the Ubuntu side first.

[SIZE="5"]Step 2: Setup Ubuntu Networking[/SIZE]
Before I go down this road with you there are a few things I need to make known. First, I have only tested this setup on a desktop with a physical, wired network connection. It may work wirelessly, but I have not tested it. Also if you make use of Network Manager, you will need to make sure it doesn't run anymore. You can do that easily, without uninstalling it, by simply creating two files with the word: exit as the only thing in them. Use your favorite editor, mine is pico, and create these files  like this:
(Quick pico reference: to exit a file and choose whether or not to save it use: Ctrl+x)

```
sudo pico /etc/default/NetworkManager
sudo pico /etc/default/NetworkManagerDispatcher
```

If you had to add those two files then you can reboot to see that Network Manager will not start up anymore. To turn it back on simply remove those files. If you are sitting there and are thinking &#8220;But I HAVE to use Network Manager, my <insert wireless card here> is only supported by it!&#8221; Then my friend, I apologize but you may be SOL. Start digging through the forums to see if there is an alternative way to run your connection. My guess is there probably is.

Ok, now that that's out of the way let's move on.
[LIST]
[*]We first need to install some important packages:
```
sudo apt-get install bridge-utils uml-utilities
```
[*]Next we are going to setup our /etc/rc.local file.
```
sudo pico /etc/rc.local
```

Append the following information directly above the line that says &#8220;exit 0&#8221;

 ```
tunctl -t tap0 -u <username>
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 <vbox_ip> up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host <main_ip> dev tap0
 arp -Ds <main_ip> eth0 pub
```

Ok, there are some EXTREMELY important things to note here. 

First off replace <username> with the username you use to login to your Ubuntu desktop. (Mine is michael).

Next, you need to replace <vbox_ip> with an IP that is within your subnet. It doesn't matter what it is, I use 192.168.1.161 simply because it was open. The only requirement is that there isn't another device on your network with this IP. This IP will come in handy when your Windows install is not accessible over the network. Confusing I know, but it will make more sense later.

Next, you need to replace <main_ip> with the IP of your Ubuntu installation on your network. If you use DHCP be careful. I do, but I setup my router to always give me the IP of 192.168.1.160. Static or DHCP, you need to put your IP here.

Lastly, take a look at all the places where I have eth0. For many installations this will probably be your main network device, but it could be something else like ath0,eth1,etc. Make sure you change eth0 to whatever your primary network interface is. (The device that you access the network with)

[*]Ok, if you feel up to it you can parse out all the lines we just put in the /etc/rc.local file and run them one by one. Or you can easily activate these settings by simply rebooting.
[/LIST]

[SIZE="5"]Step 3: Configure your Windows Virtual Machine[/SIZE]
Ok, now we are going to boot up our Windows Virtual Machine. Go ahead and boot up your VM by opening up Applications->System Tools->InnoTek VirtualBox and then selecting your virtual machine and clicking the &#8220;Start&#8221; button.

I am not going to walk you through installing Windows, because it is mind numbingly boring and I am betting, that if you are reading this guide,  chances are you have wasted many hours of your life reinstalling Windows. When you are done installing it come back to this guide to continue.

Welcome back! I hope you had a fun time. ;) Now there are several Windows settings we will need to do. (Note: These settings worked for me in Windows XP Pro, if you are using another edition of Windows they may be the same, i.e. registry keys and such, or not. However I can personally confirm that they work flawlessly in Windows XP Pro.)

[LIST]
[*]First thing you have to do in Windows is enable Remote Connections and set a password for your user.
[*]Go to Start -> Control Panel -> Sytem and click the Remote tab.
[*]Check the box that says &#8220;Allow users to connect remotely to this computer&#8221; and click OK
[*]In the Control Panel click &#8220;User Accounts&#8221;
[*]Click the user that you would like to login as and then click &#8220;Create a password&#8221;
[*]Type your password in the boxes provided and then click the &#8220;Create Password&#8221; button.
[/LIST]

If you are thinking to yourself, &#8220;Well. it would just be easier to not have a password.&#8221; Stop right there and set one anyway. It is not an issue of security. If you don't setup a password then you will not be able to login to your Windows VM seamlessly.

[LIST]
[*]Next, download this file: [http://howtoforums.net/downloads/seamlessrdp.zip]("http://howtoforums.net/downloads/seamlessrdp.zip") and extract it to C:\seamlessrdp
[/LIST]

Now we are going to adjust a couple registry keys that drove me up the wall. By default XP Pro comes configured to only allow remote access at 16 bit color. Well, frankly this looks like butt on your desktop especially when you have a slick Beryl interface. So we are going to change that.

[LIST]
[*]Go to Start and select Run, in the box type regedit and hit OK
[*]In the registry editor navigate to the following key: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server\WinStations\RDP-Tcp
[*]In the right hand pane, highlight the ColorDepth key and right-click. Select Modify and change the &#8220;Value Data&#8221; field to 4
[/LIST]

Next, we need to set it up so that your Windows install only displays the Task bar and not the desktop on login.
[LIST]
[*]In the registry editor navigate to the following key: HKEY_CURRENT_USER\Software\Microsoft\Windows\Current Version\Policies\Explorer
[*]Create a new DWORD value that you'll call NoDesktop and set its value to 1
[/LIST]

Now, we need to set our Windows install up so that it logs in your specified user in automatically.
[LIST]
[*]Go to Start -> Run. type control userpasswords2 into the box and click OK
[*]Uncheck &#8220;Users must enter a user name and password to use this computer&#8221; and click Apply
[*]A box will come up asking what user name and password you would like to have logged in automatically. Fill this out with whatever user/pass info you have setup.
[/LIST]

Now we need to install VirtualBox's Guest Additions for seamless mouse movements (thanks merovius for pointing this out)
[LIST]
[*]Click the VM dropdown list at the top of your Virtual Machine window
[*]Click Install Guest Additions
[*]Follow the onscreen installer to install the additions
[/LIST]

Our last step is to read the network IP that Windows is using
[LIST]
[*]Go to Start -> Control Panel -> Network Connections
[*]Right click Local Area Connection and click Status
[*]Click the Support tab and record the IP Address, it will become important later
[/LIST]

Note: This IP address has to be DIFFERENT than the Virtual Box IP that you put in the /etc/rc.local file. If it is not different then configure windows to use a different IP or configure your router to give your Windows install a different IP.

[LIST]
[*]Finally, go to Start and shut down your Windows installation. Not Reboot, Shut Down.
[/LIST]

[SIZE="5"]Step 4: Configure your VirtualBox install to run headless and automatically[/SIZE]
VirtualBox has this awesome feature where you can run your Virtual Machines headless. Meaning you can start and stop them from the command line and they simply run in the background. Remember when I had you check the box to Enable VRDP? Well, that's what that does. It enables your virtual machine to run headless.

[LIST]
[*]First we are going to run your machine from the command line, so in a terminal window type this:
```
VBoxManage startvm "Windows XP Professional" -type vrdp
```

Replace &#8220;Windows XP Professional&#8221; with the name of your virtual machine if it's different.
[*]Now we are going to setup Ubuntu to start our Windows installation automatically for us upon login.
[*]Go to System->Preferences->Sessions and click the Startup Programs tab
[*]Click the Add button and type the command above into the text field and click OK
[/LIST]

[SIZE="5"]Step 5: Integrate into your Ubuntu panel[/SIZE]
Ok, the next step is to run your whole Windows seamless setup. First run the following commands from a terminal window to make sure they work, and then I recommend making a Custom Application Launcher in your Ubuntu Panel. I use this icon if you are looking for a nice one:
[IMG]http://www.creditlearningcenter.com/images/windows_flag.png[/IMG]
 (I will assume that most readers know how to do this, right click your top panel and you are on your way :))

First we need to make sure that our bottom panel is hideable, so that we can get to our start bar if we want to. You will notice from my screenshot that I have a dual monitor setup and the Windows bar is across the entire bottom of my screen. That is because I moved my bottom panel up to the top of my right monitor so it is out of the way. However, if you don't want to do that, or you only have one monitor then do this:
[LIST]
[*]Right click a blank area in your bottom panel and click Properties
[*]Check the box that says &#8220;Show hide buttons&#8221; and click OK
[*]You will now have a left arrow button on the left and a right arrow button on the right of your panel that will allow you to hide your bottom panel by clicking one of them
[*]Next, let's make sure you have rdesktop installed, it should be by default I think:
```
sudo apt-get install rdesktop
```
[/LIST]

Now, let's run our Windows install seamlessly for the first time!
[LIST]
[*]Open a terminal window and type this:
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <IP recorded from Windows>:3389 -u "<Your Windows Username>" -p <Your Windows Password>
```

Replace <IP recorded from Windows> with the IP you recorded from Windows earlier. (Gosh, did I even need to type that). Also replace <Your Windows Username> and <Your Windows Password> with your Windows username and Windows password respectively.
[*]You should have seamless.......OH CRAP the whole desktop is viewable and you are not seamlessly integrated. That is because your Windows install has to be logged off first before seamless ability will work. You may be thinking, &#8220;Michael, you are an idiot. You told me to make my Windows install login automatically!&#8221; Hold your horses. If you didn't do that then you wouldn't get anything to show up at all. For reasons unbeknownst to me, Windows XP will not listen for Remote Connections until you have actually logged in once.
[*]Simply hold down your alt key and click anywhere on the Windows desktop and move it up so that you can see the Start button.
[*]Click the Start button and choose Log off.
[*]Ok, run that command one more time and hope that you followed all the instructions correctly.
[/LIST]

Woohoo! You should have seen the desktop flash and you will be presented with a lovely blue Windows taskbar at the bottom of your screen. If your bottom panel is in the way, then just click one of the hide arrows to see your new Windows taskbar.

That's it! Easy huh. Well, it's not too difficult it is just time consuming to setup and get running. Good news is that now you can run it at will by clicking your panel launcher or running the rdesktop command again. Only downside, is that the first time you run it you will have to Log Off once before seamlessness will be in effect. Maybe someone can whip up a VB app that will log out the Windows user only on first login so this is done automatically. :)

Have fun enjoying your new setup.

P.S. Here are some important things to know about your new setup

[LIST=1]
[*]If for any reason you cannot get the rdesktop command to actually do anything you can login to your Windows VM by doing this:
rdesktop -rsound -A -s &#8220;c:\seamlessrdp\seamlessrdpshell.exe c:\windows\explorer.exe&#8221; <your vbox_ip from /etc/rc.local>:3389 -u <Your Windows Username> -p <Your Windows Password>

[*]You will notice that many apps run quickly and without much lag at all. This is a testament to how great VirtualBox is at virtualizing. However, occasionally I see slow redraw rates. This is probably due to the fact that we are accessing our virtualized Windows machine over RDP.

[*]VirtualBox claims 3D support, but it is not full. Don't expect to run any graphically intense games on this setup. You can surely try, but it will probably be laggy.

[*]As far as Beryl effects go, almost all of them will work with your Windows windows. However, if you drag a Windows app with the Windows titlebar, it won't be wobbly. This is because when you do this, rdesktop is moving the window not your window manager, i.e. Beryl. However, if you hold down alt and move the window it will be wobbly. Maybe they could add Beryl support in a future release of rdesktop to make them wobbly all the time :).
[/LIST]

---

### Post by Xala on 2007-05-05
Would this tutorial work with Feisty? i would hope so because this setup would solve all my problems.:)

Edit, i just re-read your post again, i noticed that you are going to repost this when you have got it working for Feisty.

---

### Post by rolf-c on 2007-05-05
Amen to what Xala said.  I've bookmarked this thread!

If I can move my work-required Windows apps to my Feisty box...hubba.

---

### Post by starfry on 2007-05-05
I have just tried this on Feisty and the problem I have is that the mouse position is not syncd between the Upuntu mouse and the Windows one, hence you see two pointers and this prevents it from working for me. I am searching for a solution and will post here if I find one.

---

### Post by Merovius on 2007-05-05
I believe you need to install "guest additions" to Virtualbox. My mouse moves seamlessly across both desktops.

---

### Post by mikeytag on 2007-05-05
> **starfry said:**
> I have just tried this on Feisty and the problem I have is that the mouse position is not syncd between the Upuntu mouse and the Windows one, hence you see two pointers and this prevents it from working for me. I am searching for a solution and will post here if I find one.

Like merovius said, I would recommend installing the VirtualBox Guest Additions. Boot up your Virtual Machine via the app and click the VM dropdown and then click "Install Guest Additions". This may solve your problems.

Hey if any of you guys get it running great in Feisty, let me know what differences there were from this tutorial and we can post another one for Feisty users.

---

### Post by starfry on 2007-05-05
I've just installed the guest additions.
When I fire up the rdesktop session, I get a big blue screen and I can use ALT to move the screen to see the START menu. The windows cursor is the pointer/hourglass combination one and the mouse does move it around. However clicking it does nothing. I can't click on "start" to log it off as per the instructions.

merovius - when you say yours works, is that all under Feisty?

note: when I said about mouse problems I meant when in "rdesktop" not when running the virtualbox in the foreground - the mouse works in that and alwasy has, it's just in rdesktop that it is a problem. I use rdesktop for other remote machines and it is fine.

---

### Post by rolf-c on 2007-05-05
I'll add there is a Feisty deb at [http://www.virtualbox.org/download/1.3.8/](http://www.virtualbox.org/download/1.3.8/)

```
Index of /download/1.3.8

Name                                        Last modified      Size                                                  -   
vbox-kernel-module-src-1.3.8.tar.bz2        14-Mar-2007 09:05  115K  
VBoxGuestAdditions_1.3.8.iso                14-Mar-2007 09:03  2.2M  
VirtualBox-1.3.8_mdv2007.1-1.i586.rpm.run   14-Mar-2007 08:36   10M  
VirtualBox-1.3.8_openSUSE102-2.i586.rpm.run 14-Mar-2007 13:42   10M  
VirtualBox-1.3.8_rhel4-1.i586.rpm.run       14-Mar-2007 08:37   12M  
VirtualBox-OSE-1.3.8.tar.bz2                14-Mar-2007 08:39   17M  
VirtualBox_1.3.8_Debian_etch_i386.deb       14-Mar-2007 11:03   10M  
VirtualBox_1.3.8_Debian_sarge_i386.deb      14-Mar-2007 08:36   10M  
VirtualBox_1.3.8_Linux_x86.run              14-Mar-2007 08:49   12M  
VirtualBox_1.3.8_Ubuntu_dapper_i386.deb     14-Mar-2007 08:37   10M  
VirtualBox_1.3.8_Ubuntu_edgy_i386.deb       14-Mar-2007 08:38   10M  
VirtualBox_1.3.8_Ubuntu_feisty_i386.deb     22-Apr-2007 20:50   11M  
VirtualBox_1.3.8_Win_x86.msi                14-Mar-2007 08:52   13M  
```

---

### Post by Jose Catre-Vandis on 2007-05-05
Excellent stuff! Weird to have this integration and the speed compared to VMware!

I am on Edgy!

Some questions/suggestions....

Is it possible to "gracefully" shut down the windows session? I see you can:
```
 VBoxManage controlvm "Windows-XP-Pro" poweroff
```
but is this graceful enough to stop XP complaining about a crappy shutdown?
~~~~~~~~~~~~~
I too needed the VBox Guest Extensions to get the mouse working properly
~~~~~~~~~~~~~
I proabably don't need to do this as I rarely venture into XP using VMware, but can anyone suggest a script that will handle both commands; a) start the headless session and b) start the desktop, once the session has loaded. I don't need to load up the headless session on boot, partly because of use, partly because of overhead.
~~~~~~~~~~~~~
All my filesystem mounts seem to have disappeared, and 
```
sudo mount -a
```
doesn't bring them up. This is partitions on the same drive and NFS shares I have on a server (different machine). I can access the partitions on my HDD if I dive down into /media but not the NFS shares? I'll do some testing around this and report back. 
~~~~~~~~~~~~~
and it is taking my desktop an extra 1 minute 45 seconds to be ready for business, and opening up anything nautilus / terminal / whatever takes between 20 seconds and a minute to come up on screen
~~~~~~~~~~~~~

Removing:
```
tunctl -t tap0 -u <username>
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 <vbox_ip> up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host <main_ip> dev tap0
 arp -Ds <main_ip> eth0 pub
```
from rc.local solved the above two problems, so it looks like this integration solution is not for my system :-(
~~~~~~~~~~~~~~
I can't live without my ubuntu panel being at the bottom of the screen, in view. I tried moving the XP start menu to the top of the screen, ( by running a normal Vbox session of XP) but this sits on top of any windows I have open.
~~~~~~~~~~~~~

Other than that...fantastic work, well done mikeytag!

---

### Post by woodgdo1 on 2007-05-05
Pretty cool idea. I think I will give it a shot with my vmware install to see if that works.

---

### Post by Jose Catre-Vandis on 2007-05-06
Decided to give virtualbox a chance to get their network bridging act together (ala VMware) before switching over.

---

### Post by mseewald on 2007-05-06
Excellent! I can confirm it works in Feisty Fawn!

Regards,
Michael

---

### Post by Zyrshnikashnu on 2007-05-06
Impressive, but Windows XP is refusing my connection when I run the rdesktop command. Does anyone have any clue what might cause this? I'm fairly certain I turned off whatever firewall XP SP1 comes equipped with.

```
$ rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.1.8:3389 -u "MyUsername" -p MyPassword
Autoselected keyboard map en-us
ERROR: connect: Connection refused
```

I don't think I need to open port 3389, since it's on my internal network, but I tried anyway. Failure. I also know that 192.168.1.8 is on my network because I can ping it. Furthermore, the Windows install can connect to my network, but it can't connect to the Web.

EDIT:
[http://forums.suselinuxsupport.de/lofiversion/index.php/t23773.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t23773.html)

Apparently XP Home doesn't support Remote Desktop. Screwed again by Microsoft even when I'm *trying* to use its product.

---

### Post by rolf-c on 2007-05-06
> **mseewald said:**
> Excellent! I can confirm it works in Feisty Fawn!

I also have it working under Feisty using your guide with two slight modifications.

1.)  I configged it without the tap option.
2.)  I had to use the ip assigned in rc.local to access the virtual XP box with rdesktop.

My mods were due to laziness...no initial tap option so rather than get it enabled I skipped it.


Seamless...happy.  **Mikey, thanks for your work on this.**

---

### Post by mikeytag on 2007-05-06
> **rolf-c said:**
> I also have it working under Feisty using your guide with two slight modifications.

1.)  I configged it without the tap option.
2.)  I had to use the ip assigned in rc.local to access the virtual XP box with rdesktop.

My mods were due to laziness...no initial tap option so rather than get it enabled I skipped it.


Seamless...happy.  **Mikey, thanks for your work on this.**

Great. It's nice to see people getting it to work with Feisty.

I think what would make this setup great is if VirtualBox created a way to accomplish this same effect without rdesktop. There has to be some amount of lag forcing everything to go through the rdesktop interface. I am going to see if I can petition the VBox devs to take a swing at it.

---

### Post by Cud on 2007-05-07
Hello, My XP pro virtualbox (on Ubuntu Edgy) keeps crashing. When I run it a terminal I get a segmentation fault (core Dump). Whats weird is that it doesn"t happen right away, but only after I surf to a site, or try to play solataire or something like that. Otherwise this was a GREAT how-to. Can anybody give me any ideas where I could start looking for the problem?

Thanks,
Jess

---

### Post by starfry on 2007-05-07
Well, I have it working now.
I reinstalled XP completely and had the same problems as before but, after installing XP Service Pack 2 I got it working.

A couple of strange things I've noticed though:
"Command Prompt" windows don't show. Other windows do, however (Explorer, Control Panel, etc). Command Promot does run and you see a button in the blue bar for it. If you run, say, explorer, and move the window quickly you can see the command prompt lurking behind it but there is no way to use it however.

Also, the Virtualbox Folder sharing causes the VM to BSOD and reboot. It's a known issue that can be seen at this link: [http://www.virtualbox.org/ticket/57](http://www.virtualbox.org/ticket/57)

Otherwise, looks very good. I'm going to install some Windows apps to my VM and see how usable it is!

---

### Post by woodgdo1 on 2007-05-07
One thing to note for corporate users. 

If you are part of a domain, you won't be able to use the shell -s flag with rdesktop as it is disabled due to "Fast User Switching" and the "Splash screen" being disabled. 

The way I get around it is to connect to the console session of the XP box using the -0 switch in rdesktop and then launch seamlessrdpshell "someprogram" from within that full rdesktop window. I created an alternate shortcut to outlook with the path like "c:\seamlessrdp\seamlessrdpshell.exe  c:\Program Files\Microsoft Office\Outlook11\Outlook.exe" This will take all open windows also and transfer them to your Linux desktop (even the taskbar and desktop).  

I also used the regedit from this post to disable my desktop so I only pass over my Windows taskbar.

---

### Post by blazercist on 2007-05-07
This  looks incredible, however, there is just one problem for me.  Can't use 3d intensive apps like games, well I have everything else that I need natively running in Ubuntu, I just can't get some of my games working with wine... It would be great if this worked for games.

---

### Post by Jose Catre-Vandis on 2007-05-07
Having abandoned this approach using virtualbox, thought I would try it out with my VMware Server installation. It works! In much the same way and following the majority of mikeytag's howto to get set up. VMware also allows command line start ups for a headless VM, and the same command for rdesktop brings home the bacon!
I have not tested extensively, but I get the task bar and menus, and still have to logon twice! and no command prompt window either.

All this in uptodate Edgy


To run a vmware OS you can use the following command in Terminal:
```
vmrun start "/full/path/to/your//VirtualMachine/Windows XP Professional.vmx"
```
(you need the quotes if you have any spaces)

then run the rdesktop command:
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <VM-IP>:3389 -u "user" -p pass
```

I hope this adds to the good work done above :-)

[EDIT]

Found an alternative command line utility that works under this setup, to resolve the problem of the command prompt not showing up. Go here:
```
http://jameser.blogspot.com/2006/07/tip-21-customizable-command-prompt-for.html
```
and follow the link to download Console 2.0 :-)

---

### Post by ravinsp on 2007-05-08
Everything works fine for me. But my problem is the guest OS (XP) doesn't detect USB drives. When I plug a USB pen drive ubuntu mounts it normally. Guest os does not respond to it.

Thanks
-RavinSP-

---

### Post by rolf-c on 2007-05-08
> **ravinsp said:**
> Everything works fine for me. But my problem is the guest OS (XP) doesn't detect USB drives. When I plug a USB pen drive ubuntu mounts it normally. Guest os does not respond to it.

Thanks
-RavinSP-

I had the same issue and found [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox) as a work-around:

```

 Enable USB devices

You will need to modify a configuration file. You may user any editor you like, I use vim, you can user nano or gedit if you like :


gksudo gedit /etc/udev/rules.d/40-permissions.rules


Change this line :

SUBSYSTEM=="usb_device", MODE="0664"


To:

# Edited to enable USB devices with VirtualBox 
# Original line commented out # SUBSYSTEM=="usb_device", MODE="0664" 

SUBSYSTEM=="usb_device", MODE="0666"


(the # comments out the first line in case you need to change the file back)

Now in virtual box, select your machine, select USB Controller, Select the Enable USB controller box, add usb devices.

Boot your virtual machine. On the bottom of the window is an icon to add usb devices to the virtual machine.
Warning: The USB device can be used by either the virtual machine or the host, but not both at the same time. Your usb device will be unmounted when you boot the virtual machine by brute force, be prepared ...

This can lead to data loss. 
```

---

### Post by garren on 2007-05-08
I'm having problems with rdesktop--everything works fine for a few seconds, but then I get a contstant stream of errors, all the same error: 
> ERROR: select: bad file descriptor
Windows freezes up from the errors.  I have no idea what is causing it.  The first time I tried, the errors occured before I had a chance to do anything, the second time, I was able to click on the start menu, the third time I was able to click on the start menu and logout (I then saw it seemless!) then I clicked on the start menu and it froze.... (I haven't tried a again)

One complication--I'm using vmware-server rather than virtualbox.  I did just the same as Jose Catre-Vandis, though sadly he hadn't posted yet, and being a noobie it took me a lot of searching on the internet and interpreting stuff I don't understand to discover that one line of code to get vmware running headless!

---

### Post by Jose Catre-Vandis on 2007-05-08
> **garren said:**
> 
One complication--I'm using vmware-server rather than virtualbox.  I did just the same as Jose Catre-Vandis, though sadly he hadn't posted yet, and being a noobie it took me a lot of searching on the internet and interpreting stuff I don't understand to discover that one line of code to get vmware running headless!

Hey garren, I had to do the googling to to find out how to do the vmware headless thing too, so you are not the only noob :-)

Not sure what your problem is, best to try a run through of the howto again and check you made all the changes to Windows?

---

### Post by quickwitt on 2007-05-08
I have it working in Feisty. My only trouble is I can't get the desktop integration working. The script to start VirtualBox on boot works but I can't access the XP desktop. If I disable the startup on boot i can start VirtualBox and boot into XP no problem. Any ideas???

I guess my only other issue is having to use my wired connection to give the VM network access. But I am certain the community will come up with a fix soon!

---

### Post by ravinsp on 2007-05-09
Actually we don't have to disable ubuntu network manager to connect the vm to network.

These are the lines i added to **rc.local** file (I did it according to the VirtualBox user manual with a slight modification) :

[FONT="Lucida Console"]tunctl -t tap1 -u <Ubuntu user name>
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
sudo ifconfig br0 <Host static IP> netmask 255.255.255.0 up
sudo route add default gw <Internet gateway IP> br0
brctl addif br0 tap1
ifconfig tap1 up[/FONT]

With this, I can connect my virtual machine to internet through the network. The real network of host machine also works fine.

Good luck
-RavinSP-

---

### Post by woodgdo1 on 2007-05-09
I'm seeing the same issue with my Vmware install and have noticed that it only occurs when I redirect sound to my physical ubuntu install. For now I just don't use that rdesktop switch.
> -r sound:local

> **garren said:**
> I'm having problems with rdesktop--everything works fine for a few seconds, but then I get a contstant stream of errors, all the same error: 

Windows freezes up from the errors.  I have no idea what is causing it.  The first time I tried, the errors occured before I had a chance to do anything, the second time, I was able to click on the start menu, the third time I was able to click on the start menu and logout (I then saw it seemless!) then I clicked on the start menu and it froze.... (I haven't tried a again)

One complication--I'm using vmware-server rather than virtualbox.  I did just the same as Jose Catre-Vandis, though sadly he hadn't posted yet, and being a noobie it took me a lot of searching on the internet and interpreting stuff I don't understand to discover that one line of code to get vmware running headless!

---

### Post by SargeZT on 2007-05-09
Unfortunately, I'm having problems with this. I have the RDP server running, all of the registry keys changed, and all that good stuff. However, when I rdesktop into Windows, it seems seamlessrdp isnt doing its job, as the entire windows screen pops up.

If anyone has any ideas, I'd greatly appreciate them.

Edit: In fact, even if I remove the -s "c:\seamlessrdp\seamlessrdpshell.exe" line alltogether, it makes no difference.

Edit2: Moreover, I'm fairly confident it isn't an rdesktop problem, as I recompiled it from both the stock 1.5 source and latest CVS source, none of which made any difference.

---

### Post by sphatiga on 2007-05-09
to SargeZT

Did you login with RDesktop thru the IP that you find in Windows? If you use the one that you put in your rc.local file (i.e. the arbitrary one that you makeup) it will bring up a full windows xp window. You aren't actually logging in through the Remote Desktop. You have to use the IP that windows reports in the Network Connections/Status thing.

This was driving me nuts too when I was trying to get this configured but that was the mishap for me. After I used the correct IP address you login through remote desktop and it will work fine after that.

---

### Post by SargeZT on 2007-05-09
> **sphatiga said:**
> to SargeZT

Did you login with RDesktop thru the IP that you find in Windows? If you use the one that you put in your rc.local file (i.e. the arbitrary one that you makeup) it will bring up a full windows xp window. You aren't actually logging in through the Remote Desktop. You have to use the IP that windows reports in the Network Connections/Status thing.

This was driving me nuts too when I was trying to get this configured but that was the mishap for me. After I used the correct IP address you login through remote desktop and it will work fine after that.

Ah, well that is probably the problem. However, the IP I have set in windows doesn't seem to be transferring through to linux. I saw a post on the second page about success in Feisty without using tap0. Any experience with that, or ideas?

---

### Post by SargeZT on 2007-05-09
> **SargeZT said:**
> Ah, well that is probably the problem. However, the IP I have set in windows doesn't seem to be transferring through to linux. I saw a post on the second page about success in Feisty without using tap0. Any experience with that, or ideas?

Just wanted to give a little data, in case anyone has any ideas.

Here's the output from ifconfig:

```

br0       Link encap:Ethernet  HWaddr 00:18:E7:07:49:07  
          inet addr:172.17.2.92  Bcast:172.17.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28255079 (26.9 MiB)  TX bytes:3228195 (3.0 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80412 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80412 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:111472931 (106.3 MiB)  TX bytes:111472931 (106.3 MiB)

tap0      Link encap:Ethernet  HWaddr D6:B3:3C:3B:90:76  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3142 errors:0 dropped:3402 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:112683 (110.0 KiB)  TX bytes:587962 (574.1 KiB)

eth0     Link encap:Ethernet  HWaddr 00:18:E7:07:49:07  
          inet addr:172.17.2.92  Bcast:172.17.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:32477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26495 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28617889 (27.2 MiB)  TX bytes:3391726 (3.2 MiB)

```

The tap0 interface is set in windows to 192.168.0.5 with a 255.255.255.0 subnet. When trying to ping 192.168.0.5 after the VBox session has started, I get a 'No route to host' error. I'm assuming I've screwed this up somehow, but if anyone can point out my folley, that'd be nice. :)

---

### Post by garren on 2007-05-09
> **woodgdo1 said:**
> I'm seeing the same issue with my Vmware install and have noticed that it only occurs when I redirect sound to my physical ubuntu install. For now I just don't use that rdesktop switch.
I discovered what my problem was--I hadn't configured the rc.local file properly.  Also, I used the configuration mentioned just a couple posts above, rather than the one in the howto, and it seems to be working great (despite the fact I'm running VMWare Server instead of VirtualBox).

---

### Post by Jose Catre-Vandis on 2007-05-09
> **garren said:**
> I discovered what my problem was--I hadn't configured the rc.local file properly.  Also, I used the configuration mentioned just a couple posts above, rather than the one in the howto, and it seems to be working great (despite the fact I'm running VMWare Server instead of VirtualBox).


Ah,...... I didn't do anything to rc.local, because vmware "should" resolve all the networking, NAT and bridging issues for you :-)

---

### Post by chris.olsen on 2007-05-09
What is the purpose of the rdesktop?  I have had VirtualBox installed for a couple days and the one thing that I need is the ability to go full screen instead of being restricted to 1024x768.  Does rdesktop solve this problem?

---

### Post by sphatiga on 2007-05-09
SargeZT:
I used the tap0 bridge in Fiesty. I wasn't able to get it to work without it for some reason. I basically followed the directions that the OP posted and it works fine in Fiesty with no real changes. Like i said the only issue I had was with the IP things, but I couldn't get it to work using the NAT networking settings. 

I believe if you use VMWare it installs a bridge network so like some of the other people using VMWare server instead of VirtualBox, that step can be skipped.

chris.olsen:
This howto makes it so that the windows you are running thru the Virtual Machine actual show up on your host desktop (ubuntu in this case), hence the seamlessness. I was wondering about this too cuz the OP's screenshot is too small so you don't really get to see the details. Once you get it setup correctly, what happens is you get the windows xp startbutton taskbar on the bottom of your screen and it works just like if you were booting up into windowsxp. All your WinXP windows open up as if they were like ubuntu windows and if you have beryl you get nice effects to those WinXP windows. Bottom line is yea you can maximize a window to fullscreen, thats the reason why I liked using this setup.

---

### Post by Gbone on 2007-05-09
I also tried the HOW TO on Feisty,  I can obtain Internet connection on the host and in the VM only with the NAT config, but it is not seamless. 

I have not got  a router. I have a DSL modem, which is using pppoe and DHCP to obtain IP address. 

If I use the tap0 config posted in the first post but I cannot get online with tap0 config. I think I have to change the rc.local file to work with it, because i cannot access my VM with this command and get the 'No route to host' error
> rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <IP recorded from Windows>:3389 -u "<Your Windows Username>" -p <Your Windows Password> 

but if I use this command

> rdesktop -rsound -A -s &#8220;c:\seamlessrdp\seamlessrdpshell.exe c:\windows\explorer.exe&#8221; <your vbox_ip from /etc/rc.local>:3389 -u <Your Windows Username> -p <Your Windows Password> I can access the VM, but I have got  internet connection only on the host machine.

I use eth0 for pppoe and here is my ifconfig output:

```
br0       Link encap:Ethernet  HWaddr 00:18:F3:B6:A4:D2  
          inet6 addr: fe80::218:f3ff:feb6:a4d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1152682 (1.0 MiB)  TX bytes:10766 (10.5 KiB)

br0:avahi Link encap:Ethernet  HWaddr 00:18:F3:B6:A4:D2  
          inet addr:169.254.10.203  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:18:F3:B6:A4:D2  
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:1492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1166098 (1.1 MiB)  TX bytes:315736 (308.3 KiB)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:18:F3:B6:BA:B2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth0:avah Link encap:Ethernet  HWaddr 00:18:F3:B6:A4:D2  
          inet addr:169.254.10.203  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          Interrupt:19 

eth1:avah Link encap:Ethernet  HWaddr 00:18:F3:B6:BA:B2  
          inet addr:169.254.10.131  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1482453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1482453 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:401491983 (382.8 MiB)  TX bytes:401491983 (382.8 MiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:195.56.15.7  P-t-P:194.149.1.50  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1390 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1118582 (1.0 MiB)  TX bytes:228065 (222.7 KiB)

tap0      Link encap:Ethernet  HWaddr 76:0E:BF:9E:33:27  
          inet addr:192.168.1.56  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::740e:bfff:fe9e:3327/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:29 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:15723 (15.3 KiB)  TX bytes:4104 (4.0 KiB)
```

Please help me how to edit my rc.local file to work it seamlessly. Which IP, gateway, and mask I have to use to get it work? and Do I have to setup Server Port in VirtualBox at the VM settings?  Thanks for your help in advance.

---

### Post by kbzona on 2007-05-09
Have you tried doing this with Windows VISTA ULTIMATE or BUSINESS??? :confused: 
works great with XP but with VISTA ULTIMATE/BUSINESS i only get the whole desktop :( :(

---

### Post by sphatiga on 2007-05-09
Gbone:

Make sure you do this part correctly. You are having the same problem that I was pulling my hair out about last night as well.

> 
Our last step is to read the network IP that Windows is using

    * Go to Start -> Control Panel -> Network Connections
    * Right click Local Area Connection and click Status
    * Click the Support tab and record the IP Address, it will become important later


Note: This IP address has to be DIFFERENT than the Virtual Box IP that you put in the /etc/rc.local file. If it is not different then configure windows to use a different IP or configure your router to give your Windows install a different IP.

Check for that IP Address and use that in your Rdesktop command line. What I did was to login using the IP from the /etc/rc.local. That way you get in using the rdesktop window but its not seamless. Then do the above and record that IP address. Close the Rdesktop window and then try the command line again but with that new IP address.

If you did the rest of the config correctly it should work fine after that.
I'm not sure if you might be having a problem without having a NAT but i doubt it. I hope that trying this helps

Maybe the OP needs to make this part more clear, in terms of logging in using the IP from the etc/rc.local vs using the one you record from Windows XP. I think that part was a little confusing. 
Thanks OP for the HOWTO

---

### Post by Visceral Monkey on 2007-05-09
Wow, this looks pretty damm cool. However, the even present blue bar at the bottom is something I could do without. Anyone know of a "fit" so my normal ubuntu bar is down there?

Edit: Nm, I realize now I can just toggle the bottom bar over it should I decide too. Anyone comment on performance? Does using rdesktop slow things down over the normal performance hit from virtualization? This is quite a coup actually, if you could automate the process you'd be looking at something at least as useful as automatix is to Ubuntu these days. Good way to make a name for yourself...

---

### Post by Visceral Monkey on 2007-05-09
*Next, you need to replace <main_ip> with the IP of your Ubuntu installation on your network. If you use DHCP be careful. I do, but I setup my router to always give me the IP of 192.168.1.160. Static or DHCP, you need to put your IP here.*


Ok, I'm stuck here and I admit I'm not sure where to find the physical address of my Ubuntu installation...I know I use DHCP when getting an IP, is that IP what I need? Also, if it changes I assume I need to re-enter it. Anyway to avoid this?

---

### Post by cumanzor on 2007-05-10
> **kbzona said:**
> Have you tried doing this with Windows VISTA ULTIMATE or BUSINESS??? :confused: 
works great with XP but with VISTA ULTIMATE/BUSINESS i only get the whole desktop :( :(

AFAIK, Vista uses RDP 6.0, which lets running only one application, making seamlessrdp unneeded. Thing is, I'm not sure if rdesktop supports RDP 6.0. If you want (and help me out with the doubt), you could try creating a vm with vista on a windows host, and then using RDP from Windows to Windows (heh) to see if it works. If it does, then seamlessrdp isn't needed anymore! And we will have to update rdesktop so it works with rdp 6.0. 

Do note that if you have any version below Vista, you can upgrade the RDP client to 6.0 from the MS site.

---

### Post by kvonb on 2007-05-10
Can anyone tell me how much RAM and CPU% this uses on average?

I'm thinking of running this on my server so that anyone on my internal network can connect to it, ie my wife who uses a few Windows progs.

Her computer isn't beefy enough to run a VM, so running it over the network would be a possible option but I don't want to bog the server down too much either.

---

### Post by kilou on 2007-05-10
This is an interesting topic! However I'm wondering how much RAM it takes to run VirtualBox on startup because VirtualBox doesn't seem to have a dynamic RAM amount ie you have to set the RAM dedicated to VirtualBox and once it is running this amount of RAM won't be useable anymore from the host. So on a 1Gb RAM machine, if you assign 512Mb to the virtual machine the Ubuntu host will "only" have 512Mb RAM left to use even if yore not using any windows apps...

It would be nice to fully integrate the Windows apps in Ubuntu this way:

1) Add shortcut to windows apps in the Ubuntu menu so that once you click on it it first checks whether the virtualmachine is started or not. If it is already started, just launch the application and if it is not started, start the visrtual machine and launch the app.

2) When closing a windows apps, check if other windows apps are running. If other apps are running just close the selected app but if no other windows app is running, close the selected app AND shutdown (save state) the virtual machine.

If this is possible this would allow to totally get rid of windows taskbar (like make it hide all the time)...and would allow to leave all RAM available to the Ubuntu host when you don't need any windows app :KS 

Anyone would know how to build these kind of scripts to start/close windows applications from Ubuntu and check the state of the Virtual machine ??

---

### Post by Dawk on 2007-05-10
I tried this with vmware workstation and I can't get seamless working automatically. When I log on with 
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\Windows\explorer.exe" 10.23.18.57:3389 -u "domain\username" -p XXXXXXXX
```
I get a blue background and little bit of the taskbar at the bottom. I then have to open the Task Manager, kill explorer.exe and run 
```
c:\seamlessrdp\seamlessrdpshell.exe c:\windows\explorer.exe
```
and then it works!
Any idea what I need to change in order to get it working properly?

TIA
Dawk

P.S. It screws up when the windows screen "locks" (due to domain policy).

---

### Post by EXCiD3 on 2007-05-10
Wow, you guys here on the forums are awesome. This is exactly what I have been wanting. Since Wine cannot do everything, i want some kind of vm and Virtual Box being able to do this is just what I needed! :guitar:

---

### Post by Dawk on 2007-05-10
The problem I had with seamlessrdpshell.exe not being loaded (probably due to my vmware box being member of a domain) has been solved!
By editing HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit, changing it from 
"C:\WINDOWS\system32\userinit.exe," 
into 
"c:\seamlessrdp\seamlessrdpshell.exe C:\WINDOWS\system32\userinit.exe,"
I got seamlessrdpshell to load automatically.
I still don't know what to do about the locked screen problem, though. If my XP has been idle for 10 minutes, the screen locks, and that makes the XP desktop visible. I'd like to avoid that if possible.

Dawk

---

### Post by quickwitt on 2007-05-11
I don't know what I did differently but the seamless integration WORKS!!!
I only have one program that I regularly use WIN XP for but the geek factor here is very high.
Thanks to this awesome forum yet again!
Cheers!

---

### Post by nuahs on 2007-05-11
Got this to work, and I must say it is awesome! One problem I'm having thought is I am still getting two mouse pointers? I have the  VBox guest additions installed  but, when I move my mouse over the windoze taskbar the other pointer shows up underneath? And also when I open a window under ms. Anyone else have this problem? If I start up VBox normally and log-in the mouse works fine? I only see one pointer, only under remote login do I see two.

And is there a way to keep beryl from adding effects to the VirtualBox windows? It seams a little buggy when it tries to control the microsoft windows under VirtualBox using remote login.

Thanks for the tut btw!! Very helpful in getting me going. This is the ultimate in uber'ness :D
I love ubuntu but, still need to go back to XP once in a while to do some of my work, this a great alternative!!

---

### Post by drmartens on 2007-05-11
Did anybody managed to run programs from commandline using rdesktop instead of menu Start?
I want to run Internet Explorer, but I HAVE to do it from command line. I tried different tricks and it SOMETIMES works, but only once per virtual boot. The second time I try it, I get only blue background window...

I tried notepad, Internet explorer. Worked, but only once per boot. Would be great to solve it...

---

### Post by kilou on 2007-05-11
Since seamlessness is so nice I'd like to be able to copy some text from the web in Firefox (launched in host) and paste it in MSWord (in virtual machine). Is this possible or is this a specific feature that VMWare and VirtualBox do not have?

---

### Post by drmartens on 2007-05-11
I believe copy&paste actually works in VMWare, but not in VirtualBox yet.

---

### Post by starfry on 2007-05-11
How do you shut the VM down cleanly (I mean not doing "poweroff" but actually signalling to XP to shut down cleanly...?

---

### Post by kilou on 2007-05-11
> **starfry said:**
> How do you shut the VM down cleanly (I mean not doing "poweroff" but actually signalling to XP to shut down cleanly...?

AFAIK you need to shutdown XP as if it was your primary OS so simply Start menu and then shutdown but instead of shutting down your computer it will power off the VM cleanly. However a "clean shutdown" is also performed if you save the session. It act like an hibernation of XP so that on next start of the VM you'll get the desktop as it was when you left it...and it start MUCH faster than a full boot from scratch.

---

### Post by flowingfire on 2007-05-12
Okay... I'm working in Feisty and I got everything to work and all the registry items changed... I got the thing working beautifully as far as I'm concerned, and surfed the Internet with IE6.... So on the last step, why do I get a timeout every single time?  Heck, I even extended the time-out period.  No help there.

Here is my terminal stuff stuff:
-----------------------------------
david@David:~$ VBoxManage startvm "Windows XP" -type vrdp
VirtualBox Command Line Management Interface Version 1.3.8
(C) 2005-2007 InnoTek Systemberatung GmbH
All rights reserved.

Waiting for the remote session to open...
Remote session has been successfully opened.
david@David:~$ rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 10.0.2.15:3389 -u "username" -p password
Autoselected keyboard map en-us
ERROR: connect: Connection timed out


Peace,
-David

---

### Post by TabletGuy on 2007-05-12
Hi all

Thanks for this wonderful thread.

Here's how I get my seamless windows VM to shut down using a command from my gnome menu
1. Download the shutdown.exe application from here:
[http://www.aumha.org/downloads/shutdown.zip]("http://www.aumha.org/downloads/shutdown.zip")

2. Unzip the shutdown.exe application somewhere on your Windows VM c drive. (I use the c:\ folder for ease of use).

3. Inside your windows machine make a bat file which will excute the shutdown command.
3.A) Open windows explorer and find the c:\ folder.
3.B) Right click in the folder and create a new text document (right click > new > text document).
3.C) Name the text document shutdown.bat
3.D) Right click on your new shutdown.bat file and choose edit, notepad will pop up
3.E) enter this command into the bat file:
c:\shutdown.exe -u -f

If you put shutdown.exe into a different folder you need to put the whole path in place of 'c:\'

And that's it you now have a shut down command that can be called from your remote desktop connection like any other connection.

So from the command line you can shut down your vm by issuing:
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\shutdown.bat" <IP OF YOUR WINDOWS VM:3389 -u "<WINDOWS USERNAME>" -p "<WINDOWS PASSWORD>" 

I stick this into a menu option on my launcher.

I hope this is useful. A better option of course would be if there was a VBox script which could be called from the command line but if there is I haven't found it yet.

The next step is to have ubuntu call this command when it closes down.

EDIT:
When first posting this I forgot to mention that it is a good idea to use a different windows user for your shut down and reboot commands.
If you use your main windows user then you will find that the command do not execute. Rdesktop does not seem to excute a second shell command if connecting to a session with a user which is already open. 

So I use my windows administrator user to connect and execute the shut down and reboot commands.

---

### Post by TabletGuy on 2007-05-12
> **flowingfire said:**
> Okay... I'm working in Feisty and I got everything to work and all the registry items changed... I got the thing working beautifully as far as I'm concerned, and surfed the Internet with IE6.... So on the last step, why do I get a timeout every single time?  Heck, I even extended the time-out period.  No help there.


To get around this problem I added a second Network Adapter which is nat'ed through the host machine.

When I have time I'll sit down and figure our the networking problem (since the bridge should just let everything through) but in the meantime this works for internet and host machine connectivity.

Cheers,

---

### Post by kilou on 2007-05-12
I think we would need 2 other things to have a full seamless experience:

- have a windows startup script that would logoff the user immediately after it has been logged in
- make a script that first check the status of the VM (if it is launched or not) before issuing the rdesktop command to start an app. If the VM is started an application can be launched with rdesktop but if the VM is not yet started, it would first start the VM (and use the startup script above to logoff the user) and then issue the rdesktop command to start the application. The same should be performed when you close an app: if there is no other MS application openened in the VM, the VM should be powered off (save state).

This would allow to have a full automatic system to launch MS applications from Ubuntu but would give all RAM back to Ubuntu when no MS application is opened (there is no need to start the VM automatically when you start Ubuntu because if you're not going to use any MS app, you'll loose some precious RAM for nothing).



I have another question however: I've installed the XP SP2 patch for remote server (the one supposed to allow multiple applications to be launched). However I still can't launch 2 MS applications from Ubuntu at the same time :( Is there anything more I should do to use this patch or any setting to adjust??

Thanks

---

### Post by TabletGuy on 2007-05-12
One of the annoying things about this step up is that the first time you use the rdesktop connection you need to log in and log off before you can start using apps.

To get around this you can set windows to automatically log you off when the machine first starts up. This puts the machine in a state to receive seemless rdesktop connections.

Here how to do this:

As it my post above it is easiest to use the shutdown.exe app.
You can skip to step 3 if you have already downloaded and unzipped it.
1. Download the shutdown.exe application from here:
[http://www.aumha.org/downloads/shutdown.zip](http://www.aumha.org/downloads/shutdown.zip)

2. Unzip the shutdown.exe application somewhere on your Windows VM c drive. (I use the c:\ folder for ease of use).

3. Inside your windows machine make a bat file which will excute the shutdown command.
3.A) Open windows explorer and find the c:\ folder.
3.B) Right click in the folder and create a new text document (right click > new > text document).
3.C) Name the text document logoff.bat
3.D) Right click on your new logoff.bat file and choose edit, notepad will pop up
3.E) enter this command into the bat file:
c:\shutdown.exe -l -f

Now we need to make windows call this bat file each time the machine starts (but not when a user logs on).
4. Add a call to the bat file to the startup scripts using the Group policy editor:
4.A) In your windows VM click start > run and type in mmc.
4. B) Open the group polcy editor: 
Click File > Add/Remove Snap-In (up pops the add/remove dialog box)
Click Add
Scroll down to Group Policy and select it
Click Add, then finish, then close
Click ok

4. C) Find the Windows start up/shutdown scripts
Expand the Local Computer Policy > Computer Configuration > Windows Settings and select Scripts (Startup/Shutdown)

4.D)  Double click on StartUp

4.E) Click Add to add a new script

4. F) In the script name box enter:
c:\logoff.bat

4.G) Click OK and Ok again and you done.

No more need to log off on first rdesktop connection.


EDIT:
When first posting this I forgot to mention that it is a good idea to use a different windows user for your shut down and reboot commands.
If you use your main windows user then you will find that the command do not execute. Rdesktop does not seem to excute a second shell command if connecting to a session with a user which is already open.

So I use my windows administrator user to connect and execute the shut down and reboot commands.

---

### Post by cisforcojo on 2007-05-12
I got Windows installed and it was working great until I rebooted Ubuntu and now I get this error:

Failed to start VM execution (PERR_PGM_MAPPING_CONFLICT)

I got this same error when I still had VMWare installed and I was trying out VirtualBox.
Any idea how to solve this?

---

### Post by jordn on 2007-05-12
hey guys,

i must admit this is looking absolutely fantastic. I have got as far as configuring the network for Ubuntu and Setting up the Windows XP VM, but when i try and boot it i get a permissions error:


[I]VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
[/I]

any ideas? 

thanx in advance,

jordn

EDIT: I'm using Feisty, if this makes a difference.

---

### Post by drmartens on 2007-05-12
for example
chmod 666 /dev/vboxdrv

---

### Post by shanike on 2007-05-12
```

VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

wtf is this?!?

---

### Post by drmartens on 2007-05-12
> **shanike said:**
> ```

VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

wtf is this?!?

It's a message from the VirtualBox GUI

---

### Post by jordn on 2007-05-12
> **drmartens said:**
> for example
chmod 666 /dev/vboxdrv

thankyou very much drmartens, but now i get the following error:

[I]
Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
[/I]

do i need to use chmod on any other files?

thanx again.

---

### Post by drmartens on 2007-05-12
> **jordn said:**
> thankyou very much drmartens, but now i get the following error:

[I]
Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
[/I]

do i need to use chmod on any other files?

thanx again.

Have you set a correct interface in the 'Network' section of your virtual machine configuration?

---

### Post by jordn on 2007-05-12
> **drmartens said:**
> Have you set a correct interface in the 'Network' section of your virtual machine configuration?

yes i do believe i have. the network interface has been set up as instructed: Set to host only, and enter tap0 in the interface name field.

---

### Post by drmartens on 2007-05-12
> **jordn said:**
> yes i do believe i have. the network interface has been set up as instructed: Set to host only, and enter tap0 in the interface name field.

Then paste your ifconfig output, let's see what's there

---

### Post by jordn on 2007-05-12
here is the complete ifconfig output:

```
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:DF  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fea7:58df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:195023299 (185.9 MiB)  TX bytes:10299093 (9.8 MiB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1572 (1.5 KiB)  TX bytes:1572 (1.5 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.157.1  Bcast:192.168.157.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.185.1  Bcast:172.16.185.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

---

### Post by drmartens on 2007-05-12
And where's your tap0 interface? ;-)

---

### Post by jordn on 2007-05-12
> **drmartens said:**
> And where's your tap0 interface? ;-)

oh crap your right. how would i enable the tap interface? i set it up by editing the /etc/rc.local file as said the first time. i'll reboot and see if it shows up.


**EDIT: Rebooted, still no tap :( **

---

### Post by drmartens on 2007-05-12
> **jordn said:**
> oh crap your right. how would i enable the tap interface? i set it up by editing the /etc/rc.local file as said the first time. i'll reboot and see if it shows up.


**EDIT: Rebooted, still no tap :( **

You obviously did something wrong, so it's not set up.
You didn't have to reboot - you could just type the stuff from the rc.local file in the command line and see if it works.

You can do it right now and see which command fails or check your logs - there should be some information on what did go wrong while parsing your rc.local file after reboot.

You can also paste the contents of your rc.local file, so we gonna see if it's correctly set up.

---

### Post by jordn on 2007-05-12
The contents of my rc.locl file:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

tunctl -t tap0 -u <jordn>
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
 ifconfig tap0 <192.168.1.161> up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host <main_ip> dev tap0
 arp -Ds <192.168.0.2> eth0 pub
exit 0

```

thankyou once again for helping.

---

### Post by drmartens on 2007-05-12
Uhh...
you shouldn't use those <> when you tell the username or IP address..
So it should be
tunctl -t tap0 -u jordn
etc.

And you left <main_ip> without a real value

You should reread a few first pages of this thread - everything's there. I used it and it worked immediately.

Some user posted a bit simpler solution, which also works and doesn't need network manager to be switched off
I use the following configuration (note, that I'm using DHCP, but I always receive the same IP, so I can use it as a static one in the config)

You obviously have to change ethX/netmask/IP adresses/username to match your own.

```

tunctl -t tap1 -u drmartens 
chmod 0666 /dev/net/tun
brctl addbr br0
ifconfig eth1 0.0.0.0 promisc
brctl addif br0 eth1
ifconfig br0 192.168.10.12 netmask 255.255.255.240 up
route add default gw 192.168.10.1 br0
brctl addif br0 tap1
ifconfig tap1 up

exit 0

```

---

### Post by Jose Catre-Vandis on 2007-05-12
> **TabletGuy said:**
> One of the annoying things about this step up is that the first time you use the rdesktop connection you need to log in and log off before you can start using apps.

To get around this you can set windows to automatically log you off when the machine first starts up. This puts the machine in a state to receive seemless rdesktop connections.

Here how to do this:

As it my post above it is easiest to use the shutdown.exe app.
You can skip to step 3 if you have already downloaded and unzipped it.
1. Download the shutdown.exe application from here:
[http://www.aumha.org/downloads/shutdown.zip](http://www.aumha.org/downloads/shutdown.zip)

2. Unzip the shutdown.exe application somewhere on your Windows VM c drive. (I use the c:\ folder for ease of use).

3. Inside your windows machine make a bat file which will excute the shutdown command.
3.A) Open windows explorer and find the c:\ folder.
3.B) Right click in the folder and create a new text document (right click > new > text document).
3.C) Name the text document logoff.bat
3.D) Right click on your new logoff.bat file and choose edit, notepad will pop up
3.E) enter this command into the bat file:
c:\shutdown.exe -l -f

Now we need to make windows call this bat file each time the machine starts (but not when a user logs on).
4. Add a call to the bat file to the startup scripts using the Group policy editor:
4.A) In your windows VM click start > run and type in mmc.
4. B) Open the group polcy editor: 
Click File > Add/Remove Snap-In (up pops the add/remove dialog box)
Click Add
Scroll down to Group Policy and select it
Click Add, then finish, then close
Click ok

4. C) Find the Windows start up/shutdown scripts
Expand the Local Computer Policy > Computer Configuration > Windows Settings and select Scripts (Startup/Shutdown)

4.D)  Double click on StartUp

4.E) Click Add to add a new script

4. F) In the script name box enter:
c:\logoff.bat

4.G) Click OK and Ok again and you done.

No more need to log off on first rdesktop connection.

Nice work TabletGuy and for the shutdown script as well :-)

---

### Post by TabletGuy on 2007-05-12
Thanks Jose. I have updated my posts to include a note about using the administrator account on the windows machine to issue the shutdown or reboot commands.

So now I have one more problem to solve and then I will have seamless launching of any windows application from my Ubuntu Applications menu without having to have a windows application manager (ie the start menu) at the bottom of my screen.

The problem is that when exit an app which uses the seamless shell the rdesktop session remains open. This means that when I then open the next app rdesktop does not execute the shell command on the windows client and the whole thing falls over.

To solve this I need to either:
A) have a separate user for each application that I want to launch (annoying)
B) have rdesktop log off when I close each app opened with seamlessrdp (is this possible)?
C) force rdesktop to execute a shell command when I connect to  a previously opened connection (is this possible).
D) write an shell script which will connect to windows, logoff the previous session and then launch the new session (clumsy).

Options B or C seem best, does anyone know how to do this?

Thanks,

---

### Post by TabletGuy on 2007-05-13
or to answer my own post above:

E) Make a vbs script for each application you want to start and have it automatically log out of windows when you close the app.

This works fine.

So now I have fully integrated windows apps in my gnome menu

I have a choice of a) opening each application in single use mode where only one can be opened at a time.
or
b) opening a Ubuntu themed start menu which gives me access to the full windows system.

Very cool.

---

### Post by kilou on 2007-05-13
> **TabletGuy said:**
> 
...

Here's how I get my seamless windows VM to shut down using a command from my gnome menu
1. Download the shutdown.exe application from here:
[http://www.aumha.org/downloads/shutdown.zip]("http://www.aumha.org/downloads/shutdown.zip")
...
.

What more does this shutdown.exe file bring compared to the command **shutdown -L** typed in the windows terminal (or launched through a bat file)?? Does the shutdown.exe allow to logoff only on automatic login but not when a user enter the password manually to login??

---

### Post by jordn on 2007-05-13
i think i must be the only person who cant get this up and running.

my rc.local file looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

tunctl -t tap1 -u jordn
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
sudo ifconfig br0 192.168.0.2 netmask 255.255.255.0 up
sudo route add default gw 212.74.111.24 br0
brctl addif br0 tap1
ifconfig tap1 up

exit 0
```
where it says "add default gw...." does that mean of the host machine? because that is what i have added. my ifconfig is this:

```
jordn@jordn-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:XX  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fea7:58df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:303627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:322014475 (307.0 MiB)  TX bytes:62686820 (59.7 MiB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1318 (1.2 KiB)  TX bytes:1318 (1.2 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.157.1  Bcast:192.168.157.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.185.1  Bcast:172.16.185.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

so i have no tap interface working. i have re-read through the instructions and i still can't seem to get past this point. help would be much appreciated!

thanx in advance.

---

### Post by TabletGuy on 2007-05-13
> **kilou said:**
> What more does this shutdown.exe file bring compared to the command **shutdown -L** typed in the windows terminal (or launched through a bat file)?? Does the shutdown.exe allow to logoff only on automatic login but not when a user enter the password manually to login??

As far as I know shutdown.exe is essentially the same as shutdown -L, it was just the first thing I found when Googling. It might have more options though.

It logs off the automatic login and when a user has logged in manually.

---

### Post by TabletGuy on 2007-05-13
> **jordn said:**
> i

so i have no tap interface working. i have re-read through the instructions and i still can't seem to get past this point. help would be much appreciated!

thanx in advance.

You have no br0 or tun1 interface.

What happens when you try to go through the script line by line in a terminal? There must be an error occuring  which might reveal somthing meaningful.
(Remeber to sudo each line when you put it in the terminal)

Did you install the bridge and uml libraries?

```
sudo apt-get install bridge-utils uml-utilities
```

---

### Post by jordn on 2007-05-13
> **TabletGuy said:**
> You have no br0 or tun1 interface.

What happens when you try to go through the script line by line in a terminal? There must be an error occuring  which might reveal somthing meaningful.
(Remeber to sudo each line when you put it in the terminal)

Did you install the bridge and uml libraries?

```
sudo apt-get install bridge-utils uml-utilities
```

yes i have got this package installed:

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
bridge-utils is already the newest version.
uml-utilities is already the newest version.

```

---

### Post by xboxer21 on 2007-05-13
> **TabletGuy said:**
> One of the annoying things about this step up is that the first time you use the rdesktop connection you need to log in and log off before you can start using apps.

To get around this you can set windows to automatically log you off when the machine first starts up. This puts the machine in a state to receive seemless rdesktop connections.

Here how to do this:

As it my post above it is easiest to use the shutdown.exe app.
You can skip to step 3 if you have already downloaded and unzipped it.
1. Download the shutdown.exe application from here:
[http://www.aumha.org/downloads/shutdown.zip](http://www.aumha.org/downloads/shutdown.zip)

2. Unzip the shutdown.exe application somewhere on your Windows VM c drive. (I use the c:\ folder for ease of use).

3. Inside your windows machine make a bat file which will excute the shutdown command.
3.A) Open windows explorer and find the c:\ folder.
3.B) Right click in the folder and create a new text document (right click > new > text document).
3.C) Name the text document logoff.bat
3.D) Right click on your new logoff.bat file and choose edit, notepad will pop up
3.E) enter this command into the bat file:
c:\shutdown.exe -l -f

Now we need to make windows call this bat file each time the machine starts (but not when a user logs on).
4. Add a call to the bat file to the startup scripts using the Group policy editor:
4.A) In your windows VM click start > run and type in mmc.
4. B) Open the group polcy editor: 
Click File > Add/Remove Snap-In (up pops the add/remove dialog box)
Click Add
Scroll down to Group Policy and select it
Click Add, then finish, then close
Click ok

4. C) Find the Windows start up/shutdown scripts
Expand the Local Computer Policy > Computer Configuration > Windows Settings and select Scripts (Startup/Shutdown)

4.D)  Double click on StartUp

4.E) Click Add to add a new script

4. F) In the script name box enter:
c:\logoff.bat

4.G) Click OK and Ok again and you done.

No more need to log off on first rdesktop connection.


EDIT:
When first posting this I forgot to mention that it is a good idea to use a different windows user for your shut down and reboot commands.
If you use your main windows user then you will find that the command do not execute. Rdesktop does not seem to excute a second shell command if connecting to a session with a user which is already open.

So I use my windows administrator user to connect and execute the shut down and reboot commands.

I believe we can also shut down the virtual machine with the following command.
[HTML]VBoxManage controlvm <Name of your Virtual machine> poweroff[/HTML]
Let me know if I'm wrong.

---

### Post by TabletGuy on 2007-05-13
> **xboxer21 said:**
> I believe we can also shut down the virtual machine with the following command.
[HTML]VBoxManage controlvm <Name of your Virtual machine> poweroff[/HTML]
Let me know if I'm wrong.

Nope that just cuts the power to the VM machine. It doesn't shut windows down properly.

---

### Post by xboxer21 on 2007-05-13
> **TabletGuy said:**
> Nope that just cuts the power to the VM machine. It doesn't shut windows down properly.

Thanks for the clarification.

---

### Post by kilou on 2007-05-14
I've installed the terminal server patch on my XP SP2 guest but I still cannot launch 2 different applications seamlessly :( I opened Internet Explorere and then tried to open MSPaint but it just switch to Internet Explorer again. Has anyone achieved to have the terminal server patch on XP Pro SP2 working properly??

---

### Post by TabletGuy on 2007-05-14
> **kilou said:**
> I've installed the terminal server patch on my XP SP2 guest but I still cannot launch 2 different applications seamlessly :( I opened Internet Explorere and then tried to open MSPaint but it just switch to Internet Explorer again. Has anyone achieved to have the terminal server patch on XP Pro SP2 working properly??

The terminal server patch lets more than one session be open at a time but you still can't have more than one session for each user for this setup under XP.

So there are two work arounds:
A) open explorerer (or another programme launcher) which you can use to start lots of apps
B) set up several user accounts, give each account remote desktop access and then use each account to start a new app.

You could set up an excel user, a word user, etc.

---

### Post by TabletGuy on 2007-05-14
> **kilou said:**
> I've installed the terminal server patch on my XP SP2 guest but I still cannot launch 2 different applications seamlessly :( I opened Internet Explorere and then tried to open MSPaint but it just switch to Internet Explorer again. Has anyone achieved to have the terminal server patch on XP Pro SP2 working properly??

The terminal server patch lets more than one session be open at a time but you still can't have more than one session for each user for this setup under XP.

So there are two work arounds:
A) open explorerer (or another programme launcher) which you can use to start lots of apps
B) set up several user accounts, give each account remote desktop access and then use each account to start a new app.

You could set up an excel user, a word user, etc.

---

### Post by kilou on 2007-05-14
Oh I didn't know that. It's probably easier to launch apps through the command prompt then. I wonder if creating multiple users would work because on a single user system the accont must be first logged in then logged off in order to work. I don't know if on a multi-user each user must first be logged in as well.....whcih would be a real pain :)

But what would be the command to launch the command prompt (cmd) and open internet explorer through it for instance??? For now I use:

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" IP:3389 -u user -p password

---

### Post by ssc351 on 2007-05-14
ok i finally got everything going except for a couple of hopefully minor problems.  All of my desktop items on the windows remote have disappeared, I can't do anything with the desktop as well, ie add icons. Next, the resolution chnages itself...here's what happens when i run the redesktop command:

Autoselected keyboard map en-us
WARNING: Remote desktop changed from 1440x900 to 720x400.
WARNING: Remote desktop changed from 720x400 to 640x480.
WARNING: Remote desktop changed from 640x480 to 1432x768.

so the screen doesn't full integrate into ubuntu...it still looks like another window in ubuntu.  So my desktop screen is the basic ubuntu one then i click on the rdesktop and there is another window.  Not seamless i guess is what I am getting at.  I have a dell 640m with a widescreen and running fiesty.  Let me know what you guys think!  I will try and post a screen shot.

---

### Post by ssc351 on 2007-05-14
here is a screenshot.

---

### Post by hiazle on 2007-05-15
> **ssc351 said:**
> so the screen doesn't full integrate into ubuntu...it still looks like another window in ubuntu.  So my desktop screen is the basic ubuntu one then i click on the rdesktop and there is another window.  Not seamless i guess is what I am getting at.  I have a dell 640m with a widescreen and running fiesty.  Let me know what you guys think!  I will try and post a screen shot.

Please pardon me as this is my first post. I read through all the posts in this thread before I posted. However I am a little lost because I use VMware Server instead of VirtualBox. I can access my headless virtual machine from the command line by issuing the following commands:
```
vmrun start "/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx"

```
then
```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.3.103:3389 -u <username> -p <password>
```
where 192.168.3.103 is the IP reported in Windows. I too get my windows session in a "window" and not seamless. My understanding is that since I use VMware, I do not have to edit the rc.local file since VMware handles that for me. 
> **Jose Catre-Vandis said:**
> Ah,...... I didn't do anything to rc.local, because vmware "should" resolve all the networking, NAT and bridging issues for you :-)
Did I understand this correctly? Would this be the reason why my windows desktop is not seamless?

T.I.A.

---

### Post by hiazle on 2007-05-15
>     * You should have seamless.......OH CRAP the whole desktop is viewable and you are not seamlessly integrated. That is because your Windows install has to be logged off first before seamless ability will work. You may be thinking, &#8220;Michael, you are an idiot. You told me to make my Windows install login automatically!&#8221; Hold your horses. If you didn't do that then you wouldn't get anything to show up at all. For reasons unbeknownst to me, Windows XP will not listen for Remote Connections until you have actually logged in once.
    * Simply hold down your alt key and click anywhere on the Windows desktop and move it up so that you can see the Start button.
    * Click the Start button and choose Log off.
    * Ok, run that command one more time and hope that you followed all the instructions correctly.

To answer my own questions..... I had not read all of the instructions carefully. I thought this applied only to the "VERY FIRST" time you log in.

However, I have another question. I now get my taskbar on my Ubuntu desktop, but it keeps flashing very fast. I have to click it several times to catch it and get a response. Anyone experienced this at all?

---

### Post by ssc351 on 2007-05-15
I tried all sorts of combinations, and using previous posts,etc but i still can't get it to be "seamless"  Any input??? Anyone? Anyone?

---

### Post by TabletGuy on 2007-05-16
> **kilou said:**
> Oh I didn't know that. It's probably easier to launch apps through the command prompt then. I wonder if creating multiple users would work because on a single user system the accont must be first logged in then logged off in order to work. I don't know if on a multi-user each user must first be logged in as well.....whcih would be a real pain :)


No for some reason only the first terminal services connection needs to be logged off.

From then on each additional user just logs in and gets a seamless desktop as normal. I have this set up working quite well (with a VBS script to logout the user when I close the application). It is a bit of a hassel to set up though.

Because they are using rdesktop connections I can even cut and paste between the applications.

---

### Post by TabletGuy on 2007-05-16
> **ssc351 said:**
> ok i finally got everything going except for a couple of hopefully minor problems.  All of my desktop items on the windows remote have disappeared, I can't do anything with the desktop as well, ie add icons. Next, the resolution chnages itself...here's what happens when i run the redesktop command:



You cannot access your icons on your windows desktop because of this step in the instructions:

```
Next, we need to set it up so that your Windows install only displays the Task bar and not the desktop on login.

    * In the registry editor navigate to the following key: HKEY_CURRENT_USER\Software\Microsoft\Windows\Curre nt Version\Policies\Explorer
    * Create a new DWORD value that you'll call NoDesktop and set its value to 1

```

What this does is set you Windows so that the desktop icons and things are turned off.
At this point you can't have your desktop icons, background picutre, etc seamlessly - they need to be switched off.


> **ssc351 said:**
> 
Autoselected keyboard map en-us
WARNING: Remote desktop changed from 1440x900 to 720x400.
WARNING: Remote desktop changed from 720x400 to 640x480.
WARNING: Remote desktop changed from 640x480 to 1432x768.

so the screen doesn't full integrate into ubuntu...it still looks like another window in ubuntu.  So my desktop screen is the basic ubuntu one then i click on the rdesktop and there is another window.  Not seamless i guess is what I am getting at.  I have a dell 640m with a widescreen and running fiesty.  Let me know what you guys think!  I will try and post a screen shot.

There are a couple of things that might be wrong with your set up:
A) This screen you are getting might be the initial log in screen which you need to log out of to enable the seamless connection.
Each time you power on the windows VM your first rdesktop connection needs to be manually logged out. Your second rdesktop connection will be the one which is seamless.

So you need to start the VM, connect using rdesktop, log out and the connect again.

This can be avoided using the instructions I posted earlier.

B) You need to check the command you are sending to start rdesktop. The remote desktop on initial connection should be the same size as your Ubuntu screen. The remote desktop window on your screenshot is smaller than your Ubuntu desktop.

---

### Post by kilou on 2007-05-16
> **TabletGuy said:**
> No for some reason only the first terminal services connection needs to be logged off.

From then on each additional user just logs in and gets a seamless desktop as normal. I have this set up working quite well (with a VBS script to logout the user when I close the application). It is a bit of a hassel to set up though.

Because they are using rdesktop connections I can even cut and paste between the applications.

But is there a way to use a single user but launch programs through command prompt (cmd.exe) and do this automatically from Ubuntu?? For example it is possible to launche internet explorer from windows like this:

c:\windows\system32\cmd.exe /C "c:\program files\internet explorer\iexplore.exe"

However if I insert this command into the rdesktop command into Ubuntu it doesn't work :( There is probably a problem with the "", I tried to remove them or use ' but it didn't work either. 

Also in your multi-user setup why do you have to logoff a user after using a program?? Isn't the user automatically logged off when you close the remote program?

---

### Post by colonelmac on 2007-05-16
I run Ubuntu Feisty Fawn on a Dell Inspiron B130. So far I have been lucky and the wireless card works fine with Network Manager. I have tried switching to Wifi Radar, but I couldn't figure out how to get WPA support (my home network uses WPA). Would switching to Wifi Radar suffice? If so can someone help me get WPA working? Thanks. :)

---

### Post by TabletGuy on 2007-05-17
For any one who is interested:

I have been using this set up full time for most of this week now and I have already decided to switch back from VirtualBox to VMware to run the virtual machine.

The performance is much better under VBox but it just can't match VMware's features:
1. Networking - this is a breeze on VMware. I just use a host only network and my VM and host are always on the same IP. I guess this is possible for VBox but its not easy to configure.

2. USB devices. Using VMWare I can just assign a device and it works. On VBox the devices just aren't always shared through to the VM. About 50% of the time my iPod doesn't come through.

3. Easier start up and shut down on host machine start.

4. VMware is now a package easily installed and thus updated at an official level.

So those who are struggling with VBox might want to give VMware a try.

---

### Post by ssc351 on 2007-05-17
> **TabletGuy said:**
> 

There are a couple of things that might be wrong with your set up:
A) This screen you are getting might be the initial log in screen which you need to log out of to enable the seamless connection.
Each time you power on the windows VM your first rdesktop connection needs to be manually logged out. Your second rdesktop connection will be the one which is seamless.

So you need to start the VM, connect using rdesktop, log out and the connect again.

This can be avoided using the instructions I posted earlier.

B) You need to check the command you are sending to start rdesktop. The remote desktop on initial connection should be the same size as your Ubuntu screen. The remote desktop window on your screenshot is smaller than your Ubuntu desktop.


Ya...i tried logging out manually, shutting down, restarting, logging out and it, etc.  Pretty much tried every combo of logging out/in and shutting down/restarting.  I followed all the instructions from the intial post exactly and quadruple checked.  Then I also tried your logoff how to post  and I couldn't get it to work properly, it wouldn't log off, just a terminal screen would pop up.  Any ideas?  Need my to post anything?

---

### Post by lequytuan on 2007-05-17
I try it but it not work . an error below :
cms@cms-laptop:~$ sudo rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.169.3.131:3389 -u "cms" -p cms
Autoselected keyboard map en-us
ERROR: connect: No route to host
cms@cms-laptop:~$ 

file rc.local is :
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
tunctl -t tap0 -u <cms>
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth1 192.169.3.174 promisc
 /usr/sbin/brctl addif br0 eth1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 <192.169.3.131> up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host <192.169.3.174> dev tap0
 arp -Ds <192.169.3.174> eth1 pub
exit 0

---

### Post by bdalzell on 2007-05-17
As of today - May 17 2007 - neither the apt installation nor the installation from the VirtualBox home page will work for me on my Edgie machine.

When trying to install automatix2 either with apt or with synaptic:

Package python-gtkhtml2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

When trying to get VirtualBox from the projects web page:

I get an error that I have a missing library so the install will not work 

Error: Dependency is not satisfiable: libasound2

But i seem to have libasound2 installed according to synaptic. I reinstalled it anyway just to be sure.

I am only a beginnng linux person and I am at a loss what to do in this instance.

---

### Post by kilou on 2007-05-17
Stupid question about seamless MS applications in Ubuntu: do they use RAM from the host or the RAM that is assigned to the guest system in VirtualBox? 

I'm now trying to launch multiple seamless MS application from the same rdesktop connection. This is not supposed to be possible with XP except with dirty tricks like creating several users but I came across this:

[https://www.fontis.com.au/rdesktop](https://www.fontis.com.au/rdesktop)

This is a patch for seamlessrdp and rdesktop that allow to launch multiple applications in a single rdesktop connection. Sounds good! I'm trying to install this and have succeeded in applying the patches but I can't understand how to compile this thing because there is no configure file inside (rdesktop folder has a configure.ac file and seamlessrdp folder doesn't have any such thing). Any help would be appreciated!

---

### Post by kraz on 2007-05-17
Thanks a lot..very usefull, and VMWare now goes to the bin!

---

### Post by BaukeKeulen on 2007-05-18
Great stuff! I managed to get it working on my dual screen desktop, just following instructions.

On my toshiba 1440x900 screen laptop i can't get headless windows, although I did exactly the same thing (I think)... I'm getting the full windows screen every time. And also: WARNING: Remote desktop changed from 1440x900 to 1024x768. 

Is there something extra I should consider?

**EDIT:**
With ifconfig i'm receiving the following output:

```

br0       Link encap:Ethernet  HWaddr 00:0F:B0:A5:4D:36
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fea5:4d36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:64225427 (61.2 MiB)  TX bytes:3017704 (2.8 MiB)

eth0      Link encap:Ethernet  HWaddr 00:0F:B0:A5:4D:36
          inet6 addr: fe80::20f:b0ff:fea5:4d36/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:47386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:64894592 (61.8 MiB)  TX bytes:3032935 (2.8 MiB)
          Interrupt:22 Base address:0xe800

eth1      Link encap:Ethernet  HWaddr 00:13:CE:BD:A7:23
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Base address:0x8000 Memory:bc005000-bc005fff

eth1:avah Link encap:Ethernet  HWaddr 00:13:CE:BD:A7:23
          inet addr:169.254.7.50  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0x8000 Memory:bc005000-bc005fff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:38609267 (36.8 MiB)  TX bytes:38609267 (36.8 MiB)

tap0      Link encap:Ethernet  HWaddr 2E:26:B8:1D:3A:5D
          inet addr:192.168.1.161  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c26:b8ff:fe1d:3a5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:53 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

And the LAN connection in the Windows session is on IP 10.0.2.15 while gateway is 10.0.2.2.

Also, the file /etc/rc.local is like this:

```
tunctl -t tap0 -u bauke
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.1.161 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.1.102 dev tap0
 arp -Ds 192.168.1.102 eth0 pub
```

The virtual machine is started in a session: "BoxManage startvm "Windows XP Professional" -type vrdp". 

The actual RDP is started with: rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.1.161:3389 -u <"user"> -p <pass>

Also IP 192.168.1.102 can be used to get a RDP session (?!)

When trying to connect to IP 10.0.2.15 (this is the IP in the actual windows session) nothing happens exept: "Autoselected keyboard map NL". Only Ctrl-C helps to stop this command.

---

### Post by kilou on 2007-05-18
I finally got multiple applications openeing seamlessly with the rdesktop patch available here: [https://www.fontis.com.au/rdesktop](https://www.fontis.com.au/rdesktop)

I just had to install the following packages to be able to build/compile the patched rdesktop:
autoconf
automake
automake1.9
libX11-dev

Then just follow the instructions on the link above (download and unpack seamlessrdp_server.zip in c:\seamlessrdp on the xp guest) and you should be good to go. 

I could launch the first app (command prompt) with:

cd /usr/local/bin
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\windows\system32\cmd.exe" GuestIP:3389 -u username -p password

Then I could launch a second app (notepad) using:
rdesktop -l "notepad"

You can open multiple applications with a single rdesktop connection using this patch! The only thing is that Beryl's scale plugin is not very happy when multiple MS applications are opened in a superposed way in the guest and you see parts of other applications on the scaled windows. Not a big deal but it would be nice to have a workaround in beryl for this.....

---

### Post by TabletGuy on 2007-05-18
> **kilou said:**
> I finally got multiple applications openeing seamlessly with the rdesktop patch available here: [https://www.fontis.com.au/rdesktop](https://www.fontis.com.au/rdesktop)

I just had to install the following packages to be able to build/compile the patched rdesktop:
autoconf
automake
automake1.9
libX11-dev

Then just follow the instructions on the link above (download and unpack seamlessrdp_server.zip in c:\seamlessrdp on the xp guest) and you should be good to go. 

I could launch the first app (command prompt) with:

cd /usr/local/bin
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\windows\system32\cmd.exe" GuestIP:3389 -u username -p password

Then I could launch a second app (notepad) using:
rdesktop -l "notepad"

You can open multiple applications with a single rdesktop connection using this patch! The only thing is that Beryl's scale plugin is not very happy when multiple MS applications are opened in a superposed way in the guest and you see parts of other applications on the scaled windows. Not a big deal but it would be nice to have a workaround in beryl for this.....

Thanks for this - I had been trying to get this working for the last couple of days but hadn't realised the additional patches were necessary.

I sure hope this patch makes it's way into rdesktop - it is really useful to be able to launch apps from the same session.

To make this patch work on my machine I also needed to install:
```
 sudo apt-get install build-essential 
```
and
```
sudo apt-get install openssl libssl-dev libx11-dev
```

as detailed on this thread:
[http://ubuntuforums.org/showthread.php?t=224212]("http://ubuntuforums.org/showthread.php?t=224212")

---

### Post by tyfn on 2007-05-18
when I tried start vbox I'll take this error :


VirtualBox kernel driver not accessible, permission problem. Make sure that the current user has write permissions to /dev/vboxdrv by adding him to the vboxusers groups. Don't forget to logout to take the change effect.
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by tyfn on 2007-05-18
ok i did it :)

---

### Post by kilou on 2007-05-18
Now I'm also using an adapted version of the perl script proposed on [www.fontis.com.au/rdesktop](www.fontis.com.au/rdesktop) to launch the MS application seamlessly. As described the script allows to launch an application without having to know if it is the first application to start (need -A -s options) or if it is another one (need -l option). Here is the final script that works for me:

#!/usr/bin/perl

my $bin = '/usr/local/bin/rdesktop';
my $host = '[COLOR="Red"]X.X.X.X[/COLOR]'; [COLOR="Red"]#Put your guest IP address here[/COLOR]
my $socket = '/home/[COLOR="Red"]username[/COLOR]/.rdesktop/seamless.socket';
my $shell = 'C:\seamlessrdp\seamlessrdpshell.exe';
my $username = '[COLOR="Red"]username[/COLOR]';
my $password = '[COLOR="Red"]password[/COLOR]';

if (@ARGV != 1) {
    print "usage: rdesktop-wrapper \n";
    exit;
}

# if socket and master session exist,
# launch command in slave mode
$numprocs = `pgrep -c -U [COLOR="Red"]username[/COLOR] -x rdesktop`;
if (-e $socket and ($numprocs == 1)) {
    exec($bin, '-l', $ARGV[0]);
# otherwise, start new master mode
# only if no other sessions running
} elsif ($numprocs == 0) {
    exec ($bin, '-A', '-s', $shell . " $ARGV[0]", $host, '-u', $username, '-p', $password);
}

Change the things in red according to your settings. Now save this into a text file and name it rdesktop.pl. Make it executable by running sudo chmod +x ./rdesktop.pl (you must be in the directory where you saved the file)

Now you can launch any application simply by typing ./rdesktop.pl "application path" and it will launch any application. The same command is used to launch the first or subsequent applications. Really cool :) Now we are even closer to the perfect seamless experience. The last things I can think of would be to fix the beryl scale plugin issue with MS applications and maybe find a way to avoid the login screen that shortly appears after we launch the first MS aplication (peanuts though...). To fix the beryl issue I'm looking into installing virtual desktops in XP and make each new application start in a new desktop. I wonder if this would fix the problem with the scale plugin.....

---

### Post by kilou on 2007-05-18
Is it possible to disable the window decoration of windows and use Emerald on the seamless MS applications opened in Ubuntu instead???

---

### Post by s1ightcrazed on 2007-05-19
> **kilou said:**
> Is it possible to disable the window decoration of windows and use Emerald on the seamless MS applications opened in Ubuntu instead???

Short answer - no.

Long answer - Aahhhh, no. 

:lolflag:

---

### Post by kilou on 2007-05-19
Why do some beryl functions work on the seamless windows but it is not possible to use Emerald?

---

### Post by bsleys on 2007-05-20
I could have missed it but if anyone using VMWare to do this could help I'd appreaciate it.

First off how do you have networking setup in VMware?  I'm using VMServer and I had to set the Ethernet 1 for the virtual machine to Custome /dev/vmnet1.  However in this config the virtual mathine can't access the web IE Windows can't access the web.

---

### Post by TabletGuy on 2007-05-20
> **bsleys said:**
> I could have missed it but if anyone using VMWare to do this could help I'd appreaciate it.

First off how do you have networking setup in VMware?  I'm using VMServer and I had to set the Ethernet 1 for the virtual machine to Custome /dev/vmnet1.  However in this config the virtual mathine can't access the web IE Windows can't access the web.

I'm using Vmware now.

You need to run vmware-config-network.pl and alter your settings.

You should end up with three types of network adpater for your machine.
A) bridged,
B) NAT
C) Host only

Which one of these you will actually use will depending on the type of connection your machine has.

When using the vmware-config-network.pl script you might need to use the editor rather that the wizard to set up the connections.

For example I had to use the editor to change my bridged adapter from eth0 (wired) to eth1 (wireless).

Once the network adapters are set up you can use the VM machine settings to add more network adpaters to the virtual machine. I have two on my set up, a host only adapter and a bridged adapter. I use the host only one for my rdesktop connection as the IP doesn't change when I switch wireless networks.

If this doesn't work try searching the forums - there are lots of posts on networking in VMware.

Good luck.

---

### Post by xolast on 2007-05-29
I'm getting this error:

console output:
-------------------------------------------------------------------------------------
$ rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.1.144:3389 -u WINDOWSUSER -p WINDOWSPASSWORD
Autoselected keyboard map es
ERROR: connect: No route to host
-------------------------------------------------------------------------------------

I have this Ip 192.168.1.66 
and I'm in a WIRELESS NETWORK

And I choose the 192.168.1.144

All Ip are set via DHCP but I always get the 66 in my machine

this is my rc.local file:
-------------------------------------------------------------------------------
tunctl -t tap0 -u LINUXUSERNAME
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth1 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.1.144 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.1.66 dev tap0
 arp -Ds 192.168.1.66 eth1 pub

exit 0
---------------------------------------------------------------------------------

When I start windows normaly in  VM Window.  Network  late a little bit searching an Ip so it ends with a limited network with this Ip: 169.254.195.235


I tried doing with both Ips(169.254.195.235 and 192.168.1.144) and nothing.

this is my iwconfig output:
-------------------------------------------------------------------------------
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

tap0      no wireless extensions.

br0       no wireless extensions.

eth1  IEEE 802.11b/g  ESSID:"MYESSID"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:3F:19:09:21   
          Bit Rate=11 Mb/s   
          Link Quality=73/100  Signal level=21/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
-------------------------------------------------------------------------------------

and my ifconfig output:

-------------------------------------------------------------------------------------
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:20:55:D5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:11:A3:02:F6:A9  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:a3ff:fe02:f6a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2317 errors:0 dropped:226 overruns:0 frame:0
          TX packets:1861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:828596 (809.1 KiB)  TX bytes:170498 (166.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2906 (2.8 KiB)  TX bytes:2906 (2.8 KiB)

-----------------------------------------------------------------------------------------------------


Any Idea?

Thanks for your time.

---

### Post by Neomanar on 2007-05-30
I'm using feisty and VirtualBox. I've followed all the steps but when I click the "Windows" button it opens a window (which can't be maximized) containing the remote windows desktop. In the bottom panel appears "rdesktop 10.100.15.36" and the window is not seamless and has background. I can re-locate the window using the Alt key, but I guess this is not this tutorial proposes. Any guides, suggestions?

---

### Post by animusFL on 2007-05-30
> **ravinsp said:**
> Actually we don't have to disable ubuntu network manager to connect the vm to network.

These are the lines i added to **rc.local** file (I did it according to the VirtualBox user manual with a slight modification) :

[FONT="Lucida Console"]tunctl -t tap1 -u <Ubuntu user name>
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
sudo ifconfig br0 <Host static IP> netmask 255.255.255.0 up
sudo route add default gw <Internet gateway IP> br0
brctl addif br0 tap1
ifconfig tap1 up[/FONT]

With this, I can connect my virtual machine to internet through the network. The real network of host machine also works fine.

Good luck
-RavinSP-

Thanks RavinSP! This worked wonderfully!

 Thanks to MikeyTag for this awesome tweak! And also to TabletGuy for the mod
for vmware! Works with Kubuntu fiesty just great.:popcorn: Gots my friends eyes
buggin' out of their heads!  Here's some of my info...

animus@green:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:04:61:6C:73:49
          inet addr:192.168.254.1  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::204:61ff:fe6c:7349/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15651 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:10383554 (9.9 MiB)  TX bytes:1642126 (1.5 MiB)

eth0      Link encap:Ethernet  HWaddr 00:04:61:6C:73:49
          inet6 addr: fe80::204:61ff:fe6c:7349/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:5478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4743937 (4.5 MiB)  TX bytes:2375377 (2.2 MiB)
          Interrupt:18 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1600 (1.5 KiB)  TX bytes:1600 (1.5 KiB)

tap1      Link encap:Ethernet  HWaddr 56:0A:70:C7:3F:AA
          inet6 addr: fe80::540a:70ff:fec7:3faa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:807 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.62.1  Bcast:192.168.62.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.129.1  Bcast:192.168.129.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

I used bridged in the vmware eth settings...

also omitted the -rsound option in rdesktop

If you have any questions, hollah!

   animusFL

---

### Post by animusFL on 2007-05-31
BTW, anyone get this working with Win2kPro????  How do you setup the Win side? All the 
googling I've done on it point to using VNC instead of having remote desktop like XP does.
Thanks in advance for any help.
 animusFL
(SOLVED)
 FYI this does NOT work with win2k PRO, you need 2003 SERVER or later. w2kpro doesnt have terminal server.

---

### Post by chikko on 2007-06-02
hey guys - i need some help with that procedure:

i've done everything right (i hope) but when i try and run the final command i get the "no route to host"
here are some details:

i'm working with a wireless router.  the IP it gives me is 192.168.2.101 - on eth1.
the windows IP address is 10.0.2.15 when the gateway (if in any importance) is 10.0.2.2.

when i try to run kubuntu (feisty) with following change in rc.local *i cannot access the internet anymore* (so for now i'm simply "#"ing it so i can write you this post)

_**rc,local**_
```

tunctl -t tap0 -u chikko
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth1 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.2.111 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.2.101 dev tap0
 arp -Ds 192.168.2.101 eth1 pub

```

when trying to run:
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 10.0.2.15:3389 -u "chikko" -p xxxxx
```
i get (as mentioned before) the no route to host error.

if i try to run the same command with the made-up ip address (192.168.2.111) i can see the windows screen correctly - but ofcourse - no seamless work..

_**ifconfig before changing rc.local**_
```

eth0      Link encap:Ethernet  HWaddr 00:0A:E4:D8:F6:4F
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x2400

eth1      Link encap:Ethernet  HWaddr 00:15:00:2B:F1:C6
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe2b:f1c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:447 errors:1 dropped:1 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:282876 (276.2 KiB)  TX bytes:80899 (79.0 KiB)
          Interrupt:18 Base address:0x2000 Memory:b0106000-b0106fff

eth0:avah Link encap:Ethernet  HWaddr 00:0A:E4:D8:F6:4F
          inet addr:169.254.9.190  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x2400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1692 (1.6 KiB)  TX bytes:1692 (1.6 KiB)

```

the ifconfig is a little different after running kubuntu with the changes in rc.local - but again: no working internet connection, so i'm trying to avoid the thing for now.. :)

i'm using virtualbox, and not VMware.

i read about something that has to do with making a bridge in kubuntu so that it will recognize windows's IP..  don't know if it is relevant, nor how to do such a thing.. :(

any help at all would be very appreciated!  ;)


**_update:_**
same thing has happened when i tried to run it on another computer - this time it was one which is connected to the net via a "normal" IP (not via router).  it's connectivity to the net was also destroyed after making the above changes to rc.local..
i guess it's the connection to the net which makes all the problems.. how can i fix it?..  :(

---

### Post by nidzo on 2007-06-02
i have a dual boot laptop: win xp and ubuntu feisty.
my question is: is there any way to start ubuntu and use some kind of virtualization (virtual machine?) in order to open also xp and its applications?

the point is that i don't want to reinstall everything, and i don't want another copy of xp on a virtual machine.

nidzo

---

### Post by animusFL on 2007-06-02
> **chikko said:**
> hey guys - i need some help with that procedure:

i've done everything right (i hope) but when i try and run the final command i get the "no route to host"
here are some details:

i'm working with a wireless router.  the IP it gives me is 192.168.2.101 - on eth1.
the windows IP address is 10.0.2.15 when the gateway (if in any importance) is 10.0.2.2.

when i try to run kubuntu (feisty) with following change in rc.local *i cannot access the internet anymore* (so for now i'm simply "#"ing it so i can write you this post)

 
  Hey, I think your client(WinXP) IP needs to be on the same subnet as everything else,
ie 192.168.2.* . I let my router assign IP's for everything then use ifconfig/ipconfig
to figure out what they are. If your gateway uses the subnet of 10.0.2.* then setting
your eth1 to 192.168.2.* will break your internet connection. Hope this helps
   animusFL

---

### Post by animusFL on 2007-06-02
> **nidzo said:**
> i have a dual boot laptop: win xp and ubuntu feisty.
my question is: is there any way to start ubuntu and use some kind of virtualization (virtual machine?) in order to open also xp and its applications?

the point is that i don't want to reinstall everything, and i don't want another copy of xp on a virtual machine.

nidzo

 nidzo, try this website [http://www.motin.eu/www/mirror/physvmware/](http://www.motin.eu/www/mirror/physvmware/)  for some info,
I think this is what your trying to do. You might want to google it & see if there are other
techniques that work.
   animusFL

---

### Post by ssc351 on 2007-06-03
I still don't understand why I can't get the seamless to work...everything works, but its still another window.  I followed TabletGuy's post and it works great. But, after it logs out, it brings up the windows log-in screen.  I then need to log in manually...is this correct?  Also, should I log in under my windows admin or my standard name (by the way, doing either still does not make it seamless.)  Should I reinstall/redo the seamlessrdp file?  I am getting fairly frustrated.

---

### Post by chikko on 2007-06-03
> **animusFL said:**
> Hey, I think your client(WinXP) IP needs to be on the same subnet as everything else,
ie 192.168.2.* . I let my router assign IP's for everything then use ifconfig/ipconfig
to figure out what they are. If your gateway uses the subnet of 10.0.2.* then setting
your eth1 to 192.168.2.* will break your internet connection. Hope this helps
   animusFL

umm.. i think you're right - but i really don't know how to assign a new IP address to the winXP..
do you think i should try and change the XP IP, or maybe the IP configuration in the router itself..?
can you guide me?... :(
:p

---

### Post by animusFL on 2007-06-03
> **chikko said:**
> umm.. i think you're right - but i really don't know how to assign a new IP address to the winXP..
do you think i should try and change the XP IP, or maybe the IP configuration in the router itself..?
can you guide me?... :(
:p
 I haven't used virtualbox, just vmware, so I'm not sure how it handles your eth* and 
DHCP. Quick question, forgetting the seamless part for a minute, when you fire up
your XP guest, does it get assigned an internal IP by your router ( ipconfig in a command
console) & can you surf the web, see your host (ubuntu) when browsing the local network?
 If the answer is no, then I would assume virtualbox needs tweaking to allow your guest
OS onto your local network. Hope this helps.
  animusFL

---

### Post by animusFL on 2007-06-03
> **ssc351 said:**
> I still don't understand why I can't get the seamless to work...everything works, but its still another window.  I followed TabletGuy's post and it works great. But, after it logs out, it brings up the windows log-in screen.  I then need to log in manually...is this correct?  Also, should I log in under my windows admin or my standard name (by the way, doing either still does not make it seamless.)  Should I reinstall/redo the seamlessrdp file?  I am getting fairly frustrated.

 SSC, 
   When I logon the first time & log off, it kicks me right off the rdesktop, then I have to run that again to get the seamless going. Sounds like you missed a step about the auto login
in XP. When you fire up your virtual machine/XP normally, and logoff XP does it log you right back in?? That's what needs to happen. If you get the xp login screen you might want to 
dbl check your xp auto login settings. Hope this helps.
 animusFL

---

### Post by ssc351 on 2007-06-04
sorry, Im a little confused...based on Tableguy's post, don't I need 2 users?  One to log-in then log-out, called "reboot" and another called "ME" to relog-in?  Isn't this why it doesn't relog-in automatically?  Do I need to get rid of one of the users?  also Animus, you are correct, I think something needs to be fixed on my auto log-in.  Before I set-up the 2 users, when I would logout it would not automatically log in.  Also, I don't have the option to rerun the rdesktop command in terminal...should I be able to?

---

### Post by animusFL on 2007-06-04
ssc, 
 I think TG was just trying to automate the process & add a clean way of shutting down
XP inside of your virtual server. I just have one user. I'd remove a user and reset the 
XP auto login again. as far as re-running rdesktop in a terminal, my terminal stays open,
the rdesktop program just closes & drops me back to a prompt. I just up arrow to the 
rdesktop command & run it again, and I have a seamless login. Fall back to page one
of this thread & go thru MikeyTag's instructions again. Good Luck!
   animusFL

---

### Post by nidzo on 2007-06-04
> **animusFL said:**
> nidzo, try this website [http://www.motin.eu/www/mirror/physvmware/](http://www.motin.eu/www/mirror/physvmware/)  for some info,
I think this is what your trying to do. You might want to google it & see if there are other
techniques that work.
   animusFL

i'll have a look, thanks a lot...
nidzo

---

### Post by ssc351 on 2007-06-04
Ya went through the whole thing again and same thing...my problem is definitely stemming from the fact that when I logout of windows, it does not open up a new command prompt.  I tried open up a new terminal and running it that way but nothing.  Note, I deleted the other user and now it logs in automatically, so I am following mikeys tag.

---

### Post by ran_foru on 2007-06-05
Hi ...

Hey i m newbie in linux. I installed xp successfully through virtualbox and  network is also working fine in xp.
but i m facing two problem

first..

when i write in  rc.local file to create new tap i got connected network  in xp but my ubuntu lost the internet connection

and second

the final command rdesktop ... gives error that no route to host


some one help me


Thx :(:(

---

### Post by dannemil on 2007-06-05
> **ssc351 said:**
> Ya went through the whole thing again and same thing...my problem is definitely stemming from the fact that when I logout of windows, it does not open up a new command prompt.  I tried open up a new terminal and running it that way but nothing.  Note, I deleted the other user and now it logs in automatically, so I am following mikeys tag.

I have exactly the same problem. I tried to follow the post but 2 problems persist:

1. When I run rdesktop -A -s blah blah, it automatically drops from full screen to windowed. My understanding is that it should open full screen, log you in and drop to the Windows taskbar. Instead, I get another window with Windows running in it, but of course no desktop/icons because I followed the post about setting a nodesktop value in regedit.

2. Although I have autologin set up for me as the user, when I log out, it just kicks me back to the Windows login screen instead of kicking me off the rdesktop and back to the terminal prompt or loggin me back in automatically.

I am running XP Pro SP2 in vbox. I looks like there is something I am doing wrong with rdesktop since it does not appear to be opening properly in full screen mode. I also tried opening it with the -f flag, but you can't use that with the -A (seamlessrdp) flag.

Thanks in advance for any help.:D

Added: Here is some output from an attempt to run rdesktop and seamless. You can see that it immediately starts changing the window size , but I can't figure out how to stop this.

Ubuntu:~$ rdesktop -A -s "c:\program files\seamlessrdp\seamlessrdpshell.exe C:\windows\explorer.exe" 192.168.2.111:3389 -u xxxxxx -p xxxxxx 
Autoselected keyboard map en-us
WARNING: Remote desktop changed from 1920x1200 to 720x400.
WARNING: Remote desktop changed from 720x400 to 640x480.
WARNING: Remote desktop changed from 640x480 to 1192x875.

---

### Post by zach12 on 2007-06-05
coool!

---

### Post by Ace2016 on 2007-06-05
[B][COLOR="Blue"]

Hi all

i made a howto [COLOR="Red"]entirely of screenshots[/COLOR] ;) for every single step after you install virtualbox, it has everything from sharing folders with windows, to solving the first login/logout before being able to run rdesktop problem and after its setup all you have to do is use nice Alt+F2 commands :D

[http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop](http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop)

(also this method for the login/out thing isn't as good as the new method so check the screenshots out)[/B]

[/COLOR]

ok here is what i did for an easier time starting the thing up;

[COLOR="#0000ff"]HERE I HAVE USED GEOSHELL TO CUSTOMISE THE LAYOUT[COLOR="Red"] YOU CAN STILL USE PLAIN EXPLORER!!![/COLOR]  AND RUN LOTS OF APPS[/COLOR]

Screenshot of final desktop  (see where geoshell at the bottom right, i use that as a start menu to run windows apps);

[[IMG]http://img525.imageshack.us/img525/8784/linuxoffice2009we8.th.png[/IMG]](http://img525.imageshack.us/my.php?image=linuxoffice2009we8.png)

[COLOR="Red"]firstly make sure you have more than one user account, make these changes to the account that logs in by default when you start xp, this is also the one that you use when you run apps [/COLOR]

i have 3 accounts;

Ace1   <<   autologs in on startup, and logs out  (has a password)
Ace2  << runs programs, and is what you'll use to login  (because of what the rest of the guide does Ace1 will not be usable) (has a password)
Ace3 <<  unsed backup, just incase (has no password)

[COLOR="Blue"](do this after you have followed the guide and have seamless stuff working)[/COLOR]

download these two apps (geoshell if you want it) and install them;

can someone virus scan these, i know startup cpl is ok but directshutdown is  untested

[http://www.dlao.com/directshutdown/](http://www.dlao.com/directshutdown/)   (DirectShutdown)  
[http://www.mlin.net/StartupCPL.shtml](http://www.mlin.net/StartupCPL.shtml) (Startup Control Panel)
[http://www.geoshell.com/](http://www.geoshell.com/)  (GeoShell)        <<<<<<<<<<<<<<<   ignore if your going to use explorer as your shell, check out my screenshots to see what xgl+beryl+kde+rdesktop/seamlessrdp looks like

now start the virtual machine
let it autologin, in my case  it logs in as Ace1
install the first two apps
open control pannel
switch to classic view
go into startup  
HKCU/run tab
select DirectShutdown (right click) > Edit 
where it says enter the path to the program, go to the very end of the text and add -l  (thats L as in ...jk[COLOR="#ff0000"]L[/COLOR]mnop...
click ok
now test it :)
logout
relogin back in, the second you login it should kick you right back out to the login screen, if so success! :D

now login into Ace2   [COLOR="#0000ff"](MAKE SURE ACE2 HAS A PASSWORD) [/COLOR]

install geoshell    [COLOR="Red"](SKIP THIS IF YOU PLAN TO USE EXPLORER)[/COLOR]
(change the screen resolution of the xp to match your linux resolution, i know this may make it hard to work with but you need to make the toolbars and stuff align correctly)
customise it with a theme of your choise
This is what mine looks like in windows:

[[IMG]http://img525.imageshack.us/img525/887/desktopfromwithinwindowac7.th.png[/IMG]](http://img525.imageshack.us/my.php?image=desktopfromwithinwindowac7.png)

now logout of Ace2

(exit to linux)

now back in linux make these files;


sudo nano /usr/bin/startxp

> #!/bin/sh
VBoxManage startvm XPPRO -type vrdp  #change XPPRO to your virtualbox image
#(leave a blank line here, at the end)


sudo nano /usr/bin/xp

> #!/bin/sh
rdesktop 192.168.1.16   #IP ADDRESS IFCONFIG SHOWS!!! not the one inside xp
#(leave a blank line here, at the end)


sudo nano /usr/bin/userxp       (change the name to whatever you want)  [COLOR="#ff0000"]

(FOR GEOSHELL)[/COLOR]

> 
#!/bin/sh
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Shell\WinShellEx\WinShellEx.exe" -c "c:\seamlessrdp" 192.168.1.3 -u "Ace2" -p password  #NOW USE THE IP ADDRESS YOU GET FROM INSIDE XP!!!  and edit username and password and the command to run
#(leave a blank line here, at the end)


[COLOR="#ff0000"](FOR EXPLORER)[/COLOR]

> 
#!/bin/sh
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" -c "c:\seamlessrdp" 192.168.1.3 -u "Ace2" -p password  #NOW USE THE IP ADDRESS YOU GET FROM INSIDE XP!!!  and edit username and password and the command to run
#(leave a blank line here, at the end)


sudo chmod +x /usr/bin/startxp
sudo chmod +x /usr/bin/xp
sudo chmod +x /usr/bin/userxp      (change the name to whatever you want)

now its time to run this yay!!

so Alt+F2, and run startxp, wait (might take some time) untill you should hear the startup sound of xp and the logout sound, wait a bit more (a few seconds should do) and it gets to the login screen

now Alt+f2 and run userxp, and this starts geoshell in the correct place on the desktop

[COLOR="#ff0000"]TOSHUTDOWN[/COLOR]; start > programs > DirectShutdown > Shutdown PC

[COLOR="#ff0000"]QUICKER WAY[/COLOR]; copy the  C:\Documents and Settings\All Users\Start Menu\Programs\DirectShutdown\ Shutdown PC link
to C:\Documents and Settings\All Users\Start Menu 

Now you can do start > shutdown PC  (at the top)

Tell me if you have any issues, i attached the apps just incase the servers go down or anything :D

---

### Post by ran_foru on 2007-06-06
Hi

hey i have guest as window xp and i m using Feisty.I m facing one problem. I m able to connect  internet in window xp but my ubuntu has no internet connection. when i remove all the all the line in rc.local Feisty is get connected to internet but xp got disconnected.

In one line problem  is **      I m not able to connect to internet in both os simeltiniously**.


plz help me some one:(

---

### Post by Ace2016 on 2007-06-06
> **ran_foru said:**
> Hi

hey i have guest as window xp and i m using Feisty.I m facing one problem. I m able to connect  internet in window xp but my ubuntu has no internet connection. when i remove all the all the line in rc.local Feisty is get connected to internet but xp got disconnected.

In one line problem  is **      I m not able to connect to internet in both os simeltiniously**.


plz help me some one:(

Can you post the output of ifconfig before and after running the commands

---

### Post by ran_foru on 2007-06-06
right now i not having my pc

when rc.local is empty ( i have not remember exactly)
but if config show 
eth0 .......  
lo   ......

when i write all those command as given(i dont have remember exactly)

br0......
br0.....
eth0
lo....
tap0.....





i ll post ifconfig exact output  after some time

---

### Post by pacut on 2007-06-06
Well...first of all: this is GREAT !

I have easily installed under Feisty, even if I am currently making XP running into a window - next step will be the fully integration within Ubuntu.

The only difficulty I get is this: each time I launch the VM and then my XP, I get this:

============
Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
=======

Then if I run on a separate window the chmod command described above, everything gets working. What's wrong with my installation ? This is my rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
tunctl -t tap0 -u paolo
chmod 0666 /dev/net/tun
/usr/sbin/brctl addbr br0
/sbin/ifconfig eth0 0.0.0.0 promisc
/usr/sbin/brctl addif br0 eth0
/sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
ifconfig tap0 192.168.1.20 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
route add -host 192.168.1.2 dev tap0
arp -Ds <main_ip> eth0 pub
exit 0



THANKS

---

### Post by ran_foru on 2007-06-06
> **pacut said:**
> Well...first of all: this is GREAT !

I have easily installed under Feisty, even if I am currently making XP running into a window - next step will be the fully integration within Ubuntu.

The only difficulty I get is this: each time I launch the VM and then my XP, I get this:

============
Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
=======

Then if I run on a separate window the chmod command described above, everything gets working. What's wrong with my installation ? This is my rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
tunctl -t tap0 -u paolo
chmod 0666 /dev/net/tun
/usr/sbin/brctl addbr br0
/sbin/ifconfig eth0 0.0.0.0 promisc
/usr/sbin/brctl addif br0 eth0
/sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
ifconfig tap0 192.168.1.20 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
route add -host 192.168.1.2 dev tap0
arp -Ds <main_ip> eth0 pub
exit 0



THANKS


change  arp -Ds <main_ip> eth0 pub    to      arp -Ds 192.168.1.2  eth0 pub 


:D:D

---

### Post by Ace2016 on 2007-06-06
> **pacut said:**
> Well...first of all: this is GREAT !

I have easily installed under Feisty, even if I am currently making XP running into a window - next step will be the fully integration within Ubuntu.

The only difficulty I get is this: each time I launch the VM and then my XP, I get this:

============
Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
=======

Then if I run on a separate window the chmod command described above, everything gets working. What's wrong with my installation ? This is my rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
tunctl -t tap0 -u paolo
chmod 0666 /dev/net/tun
/usr/sbin/brctl addbr br0
/sbin/ifconfig eth0 0.0.0.0 promisc
/usr/sbin/brctl addif br0 eth0
/sbin/dhclient br0
/usr/sbin/brctl addif br0 tap0
ifconfig tap0 192.168.1.20 up
bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
route add -host 192.168.1.2 dev tap0
arp -Ds <main_ip> eth0 pub
exit 0



THANKS

Well instead of putting that stuff in rc.local i put it in a different place, i put it in ~/.kde/Autostart/net and made it executable, here is my net file;

ace@Linux:~$ cat ~/.kde/Autostart/net

#!/bin/sh
sudo modprobe vboxdrv               (custom kernel needs this)
sudo tunctl -t tap0 -u ace
sudo chmod 0666 /dev/net/tun
sudo chmod 666 /dev/net/tun        (a different howto had this line and the net won't work without it)
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.1.16 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.1.2 dev tap0
sudo arp -Ds 192.168.1.2 eth0 pub

---

### Post by pacut on 2007-06-06
Hello ran.

aaahg....what a shame ! I thought my file was accurate 100% ;)
THANKS

---

### Post by ran_foru on 2007-06-06
Originally Posted by ran_foru View Post
Hi

hey i have guest as window xp and i m using Feisty.I m facing one problem. I m able to connect internet in window xp but my ubuntu has no internet connection. when i remove all the all the line in rc.local Feisty is get connected to internet but xp got disconnected.

**In brief problem is I m not able to connect to internet in both os simeltiniously.**


plz help me some one

Can you post the output of ifconfig before and after running the commands

Hi 
I  m posting the some out put here 

**my  rc.local file**

# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
tunctl -t tap0 -u ranjan
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth1 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.1.160 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.1.189 dev tap0
 arp -Ds 192.168.1.189 eth1 pub!/bin/sh -e


exit 0


 **ifconfig  command output**

br0       Link encap:Ethernet  HWaddr 00:08:5C:8B:20:B2  
          inet6 addr: fe80::208:5cff:fe8b:20b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6544 (6.3 KiB)  TX bytes:4935 (4.8 KiB)

br0:avahi Link encap:Ethernet  HWaddr 00:08:5C:8B:20:B2  
          inet addr:169.254.6.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:00:E8:50:1B:59              #my ethernet without any cable 
          inet6 addr: fe80::200:e8ff:fe50:1b59/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:08:5C:8B:20:B2     # the usb throug i connect to net
          inet6 addr: fe80::208:5cff:fe8b:20b2/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:8543 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9331 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8581800 (8.1 MiB)  TX bytes:1865551 (1.7 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228 (228.0 b)  TX bytes:228 (228.0 b)

tap0      Link encap:Ethernet  HWaddr B2:CD:EB:03:8D:E5  
          inet addr:192.168.1.160  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b0cd:ebff:fe03:8de5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:29 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



[B]i m postin  the outputs plz some one point out error why i m not able to connect to internet in both os
simeltiniouly
[/B]

Thx in Advance

---------------------------------------------------------------------

---

### Post by pacut on 2007-06-06
> **ran_foru said:**
> change  arp -Ds <main_ip> eth0 pub    to      arp -Ds 192.168.1.2  eth0 pub 


:D:D

I did it and now it works !
I also have integrated the environment into my Ubuntu...wooowww !!! This is incredibly nice.
Finally I can remove my dual boot with Windows and my wife won't bother any longer (she will keep on using Windows...bleahhh !!  :popcorn:

Another question: is there any way I can access to existing Windows' partitions that I currently have on my PC ?

Last question (I promise): I have set up the environment on running on 2G of hard disk. How can I increase fearlessly ?

Ciaoooo
Paolo

---

### Post by ran_foru on 2007-06-06
> **pacut said:**
> I did it and now it works !
I also have integrated the environment into my Ubuntu...wooowww !!! This is incredibly nice.
Finally I can remove my dual boot with Windows and my wife won't bother any longer (she will keep on using Windows...bleahhh !!  :popcorn:

Another question: is there any way I can access to existing Windows' partitions that I currently have on my PC ?

Last question (I promise): I have set up the environment on running on 2G of hard disk. How can I increase fearlessly ?

Ciaoooo
Paolo


Hey ....

Can you post the output of ifconfig 


Thx

---

### Post by pacut on 2007-06-06
Ifconfig ?
Here it is


paolo@paolo-desktop:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:13:8F:8D:4B:85  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe8d:4b85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35465145 (33.8 MiB)  TX bytes:3541057 (3.3 MiB)

eth0      Link encap:Ethernet  HWaddr 00:13:8F:8D:4B:85  
          inet6 addr: fe80::213:8fff:fe8d:4b85/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:4791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4991237 (4.7 MiB)  TX bytes:568780 (555.4 KiB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1068 (1.0 KiB)  TX bytes:1068 (1.0 KiB)

tap0      Link encap:Ethernet  HWaddr 4A:27:D5:7A:43:A1  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4827:d5ff:fe7a:43a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33196 errors:0 dropped:61 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:32369583 (30.8 MiB)  TX bytes:4289531 (4.0 MiB)


And all of this....for what ? I am confused
THANKS

---

### Post by ran_foru on 2007-06-07
> **pacut said:**
> Ifconfig ?
Here it is


paolo@paolo-desktop:~$ ifconfig
br0       Link encap:Ethernet  HWaddr 00:13:8F:8D:4B:85  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:8fff:fe8d:4b85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:47607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35465145 (33.8 MiB)  TX bytes:3541057 (3.3 MiB)

eth0      Link encap:Ethernet  HWaddr 00:13:8F:8D:4B:85  
          inet6 addr: fe80::213:8fff:fe8d:4b85/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:4791 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4991237 (4.7 MiB)  TX bytes:568780 (555.4 KiB)
          Interrupt:19 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1068 (1.0 KiB)  TX bytes:1068 (1.0 KiB)

tap0      Link encap:Ethernet  HWaddr 4A:27:D5:7A:43:A1  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4827:d5ff:fe7a:43a1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33196 errors:0 dropped:61 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:32369583 (30.8 MiB)  TX bytes:4289531 (4.0 MiB)


And all of this....for what ? I am confused
THANKS


Actuallly my internet is not working in Feisty although it is working in xp so i was just verifying that is any thing wrong in my configuration......

**I m still looking for some help**  :(


Thx anyway

---

### Post by pacut on 2007-06-07
Mine works perfectly; I am sorry for you, also because I cannot provide any help :(
Good luck ;) I am sure you'll get rid of that issue.

---

### Post by Ace2016 on 2007-06-07
ran_foru; what commands are you running in rc.local to start the system

remove it from rc.local and restart, then run the commands in the command line to see if there are any errors

sudo modprobe vboxdrv     ## initng users need it unless you edit the scripts and stuff
sudo tunctl -t tap0 -u ace
sudo chmod 0666 /dev/net/tun
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.1.16 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.1.2 dev tap0
sudo arp -Ds 192.168.1.2 eth0 pub

does your eth0 have a static ip or a dynamic ip address? replace the 192.168.1.16 with the ip you want to give to vritualbox guest os, and change 192.168.1.2 to whatever your ip is when you first run ifconfig before these commands have been run

---

### Post by QuarlesLT on 2007-06-07
Hey guys,
I followed this HOWTO, using Feisty.

I am using eth0 that is static, not dhcp. First I followed the guide normally, using the steps listed. However, when I log into Windows, the LAN says it is aquiring an address for a few minutes, then says limited or no connectivity. Then I tweaked my rc.local file according to another user in this thread, I believe on page 3. Here is my current rc.local:

tunctl -t tap0 -u lamar
chmod 0666 /dev/net/tun
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
ifconfig br0 192.168.1.21 netmask 255.255.255.0 up
route add default gw 192.168.1.1 br0
brctl addif br0 tap0
ifconfig tap0 up

But when I log into Windows, the same thing happens, and I have no connectivity. Under my VirtualBox settings, I have the networking set to host and the name is tap0. The Internet on the host machine works fine.

---

### Post by ran_foru on 2007-06-07
Hi ..

I m Posting the detailed out put of command in rc.local file as some asked about that .

[B]Again in brief my problem is that when i run this rc.local file i get connect in xp but my

Feisty get disconnected[/B]
Out is in next post

Thx ..

---

### Post by ran_foru on 2007-06-07
> **Ace2016 said:**
> ran_foru; what commands are you running in rc.local to start the system

remove it from rc.local and restart, then run the commands in the command line to see if there are any errors

sudo modprobe vboxdrv     ## initng users need it unless you edit the scripts and stuff
sudo tunctl -t tap0 -u ace
sudo chmod 0666 /dev/net/tun
sudo chmod 666 /dev/net/tun
sudo /usr/sbin/brctl addbr br0
sudo /sbin/ifconfig eth0 0.0.0.0 promisc
sudo /usr/sbin/brctl addif br0 eth0
sudo /sbin/dhclient br0
sudo /usr/sbin/brctl addif br0 tap0
sudo ifconfig tap0 192.168.1.16 up
sudo bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
sudo route add -host 192.168.1.2 dev tap0
sudo arp -Ds 192.168.1.2 eth0 pub

does your eth0 have a static ip or a dynamic ip address? replace the 192.168.1.16 with the ip you want to give to vritualbox guest os, and change 192.168.1.2 to whatever your ip is when you first run ifconfig before these commands have been run

Hi again....

here i m posting ouput of each line of rc.local command as u told
**I m not able to connect internet in  both os xp and Feisty simeltiniously**
[B]output of ifcommand when rc.local file was empty
[/B]

ranjan@ranjan:~$ **ifconfig**

eth1      Link encap:Ethernet  HWaddr 00:08:5C:8B:20:B2  
          inet addr:192.168.1.189  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:5cff:fe8b:20b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52573 (51.3 KiB)  TX bytes:11704 (11.4 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

###** Here i want to show that my network is working fine ....**
ranjan@ranjan:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=2.38 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.15 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=2.04 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 1.158/1.862/2.388/0.517 ms


### **now executing each command one by one which is inside rc.local**
root@ranjan:~# [B]modprobe vboxdrv
[/B]root@ranjan:~# **tunctl -t tap0 -u ranjan**
Set 'tap0' persistent and owned by uid 1002
root@ranjan:~#  **chmod 0666 /dev/net/tun**
root@ranjan:~# **chmod 666 /dev/net/tun**
root@ranjan:~#  **/usr/sbin/brctl addbr br0**

#### [B]up to here network is working fine
[/B]root@ranjan:~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.29 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.61 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.44 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=1.29 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 1.293/1.413/1.614/0.131 ms


root@ranjan:~# [B]/sbin/ifconfig eth1 0.0.0.0 promisc
[/B]
### **Now problem get started network get disconnected**
root@ranjan:~# ping 192.168.1.1
connect: Network is unreachable

root@ranjan:~#** /usr/sbin/brctl addif br0 eth1**
root@ranjan:~# **/sbin/dhclient br0**
There is already a pid file /var/run/dhclient.pid with pid 5576
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/br0/00:08:5c:8b:20:b2
Sending on   LPF/br0/00:08:5c:8b:20:b2
Sending on   Socket/fallback
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 14

DHCPDISCOVER on br0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

root@ranjan:~# 

root@ranjan:~# **/usr/sbin/brctl addif br0 tap0**
root@ranjan:~#** ifconfig tap0 192.168.1.160 up**
root@ranjan:~#** bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'**
root@ranjan:~#** route add -host 192.168.1.189 dev tap0**
root@ranjan:~# **arp -Ds 192.168.1.189 eth1 pub**

### **Network is still unreachable**
root@ranjan:~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.160 icmp_seq=2 Destination Host Unreachable
From 192.168.1.160 icmp_seq=3 Destination Host Unreachable
From 192.168.1.160 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5001ms
, pipe 3


###**Ifconfig after executing all these command**

root@ranjan:~# ifconfig
br0       Link encap:Ethernet  HWaddr 00:08:5C:8B:20:B2  
          inet6 addr: fe80::208:5cff:fe8b:20b2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120 (120.0 b)  TX bytes:11891 (11.6 KiB)

br0:avahi Link encap:Ethernet  HWaddr 00:08:5C:8B:20:B2  
          inet addr:169.254.6.92  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

eth1      Link encap:Ethernet  HWaddr 00:08:5C:8B:20:B2  
          inet6 addr: fe80::208:5cff:fe8b:20b2/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1117 (1.0 KiB)  TX bytes:16237 (15.8 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:772 (772.0 b)  TX bytes:772 (772.0 b)

tap0      Link encap:Ethernet  HWaddr 42:3C:F0:A7:C7:3E  
          inet addr:192.168.1.160  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::403c:f0ff:fea7:c73e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:56 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Some come with solution I m using Feisty and my network ip is static not dhcp ...........

Thx

---

### Post by Ace2016 on 2007-06-07
[http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop](http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop)

I modified the method i use;

Ifconfig before:

root@Linux:/home/ace# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:33:A6:3A
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:72347 (70.6 KiB)  TX bytes:30627 (29.9 KiB)
          Interrupt:20 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Commands i run

sudo modprobe vboxdrv             (i use initng with a custom kernel)
sudo tunctl -t tap0 -u ace
sudo chmod 0666 /dev/net/tun
sudo chmod 666 /dev/net/tun
sudo brctl addbr br0
sudo ifconfig br0 192.168.1.16 netmask 255.255.255.0 up
sudo ifconfig eth0 0.0.0.0 down
sudo ifconfig eth0 0.0.0.0 up
sudo route add default gw 192.168.1.1 br0
sudo brctl addif br0 eth0
sudo brctl addif br0 tap0
sudo ifconfig tap0 up


this is my ifconfig after

br0       Link encap:Ethernet  HWaddr 00:0D:87:33:A6:3A
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:184 (184.0 b)  TX bytes:378 (378.0 b)

eth0      Link encap:Ethernet  HWaddr 00:0D:87:33:A6:3A
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:72707 (71.0 KiB)  TX bytes:30837 (30.1 KiB)
          Interrupt:20 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2240 (2.1 KiB)  TX bytes:2240 (2.1 KiB)

tap0      Link encap:Ethernet  HWaddr 76:50:E9:F8:E9:5A
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Router IP 192.168.1.1
XP's IP address; 192.168.1.20

i can ping 192.168.1.1 and 192.168.1.16 and when xp has started i can ping 192.168.1.20

these are the xp settings, hope it helps  (Don't Forget to add the dns servers as 192.168.1.1, i just realised i forgot to add those and i was wondering why the net wasn't working in xp, lol)

[[IMG]http://img522.imageshack.us/img522/4373/linux2010cy1.th.png[/IMG]](http://img522.imageshack.us/my.php?image=linux2010cy1.png)

---

### Post by flowingfire on 2007-06-08
I'm having a problem I've noticed several others mention, but nobody really answered it.

I have everything set up to-the-letter in Feisty, and Windows' networking integration seems to be working perfectly.  I have all the registry entries perfect.  I have seamlessrdp in the C: drive.  I have a beautiful Windows XP installation fully interoperable with Kubuntu on a networking level.

BUT- Despite my best efforts, every single time I command the thing to open, it opens in a new window.  Yes, I read carefully, and understand that you have to log out and log in again for it to work.  I did that.  No seamless integration.  I'm still in a window marked "rdesktop <ip.a.d.d.r.e.s.s>," and when I "log out" it brings me to the Windows login screen.  

I close the window and attempt to log back in-- same rdesktop window.  I shut down the virtual machine, start it back up and do the same.  Still in a window.  I try everything.  Still in a window.

So, in my desperation, I edited the registry with the suggestion to help Windows start up seamlessrdp.  Bad more.  Now, Windows opens in a window except now I don't have a start menu.  Uhh... No icons, no desktop, no start menu... All still in a rdesktop session window.... 

ARRGH!  Please, someone help me before my computer gets a brick thrown at it. (by me of course)  

I don't want to have to re-install Windows, but I might have broken it. :(  

If I re-install Windows and get it working again, how do I get it to NOT run in a window?  

(It might be telling that I get this particular error when I run the virtual machine through rdesktop:
/dev/dsp: Device or resource busy

Seeking Help,
-David

---

### Post by onosenday on 2007-06-08
Thanks for the tuto!!!

It's working perfectly, but.... (Always a but)

How can a i setup the network connections to allow the guest get out by a different gateway than the host??

Thanks in advance!

---

### Post by ran_foru on 2007-06-08
> **Ace2016 said:**
> I modified the method i use;

Ifconfig before:

root@Linux:/home/ace# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:87:33:A6:3A
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:72347 (70.6 KiB)  TX bytes:30627 (29.9 KiB)
          Interrupt:20 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Commands i run

sudo modprobe vboxdrv             (i use initng with a custom kernel)
sudo tunctl -t tap0 -u ace
sudo chmod 0666 /dev/net/tun
sudo chmod 666 /dev/net/tun
sudo brctl addbr br0
sudo ifconfig br0 192.168.1.16 netmask 255.255.255.0 up
sudo ifconfig eth0 0.0.0.0 down
sudo ifconfig eth0 0.0.0.0 up
sudo route add default gw 192.168.1.1 br0
sudo brctl addif br0 eth0
sudo brctl addif br0 tap0
sudo ifconfig tap0 up


this is my ifconfig after

br0       Link encap:Ethernet  HWaddr 00:0D:87:33:A6:3A
          inet addr:192.168.1.16  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:184 (184.0 b)  TX bytes:378 (378.0 b)

eth0      Link encap:Ethernet  HWaddr 00:0D:87:33:A6:3A
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:72707 (71.0 KiB)  TX bytes:30837 (30.1 KiB)
          Interrupt:20 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2240 (2.1 KiB)  TX bytes:2240 (2.1 KiB)

tap0      Link encap:Ethernet  HWaddr 76:50:E9:F8:E9:5A
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:11 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


Router IP 192.168.1.1
XP's IP address; 192.168.1.20

i can ping 192.168.1.1 and 192.168.1.16 and when xp has started i can ping 192.168.1.20

these are the xp settings, hope it helps  (Don't Forget to add the dns servers as 192.168.1.1, i just realised i forgot to add those and i was wondering why the net wasn't working in xp, lol)

[[IMG]http://img522.imageshack.us/img522/4373/linux2010cy1.th.png[/IMG]](http://img522.imageshack.us/my.php?image=linux2010cy1.png)




Thanks Bro !!
ur code  worked  perfectly 

once again thx ..... :D:D:D:D

---

### Post by dubravkor on 2007-06-08
I run it from Feisty. Here are differences from this HOWTO:

1. Set network in NAT mode: Settings -> Network -> Attached To: NAT
2. Set port forwarding. Type in terminal:
```
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/Protocol" TCP
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/GuestPort" 3389
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/HostPort" 3388

```
3. Run VM:
```
 VBoxManage startvm "Windows XP" -type vrdp
```
4. Run rdesktop:
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" localhost:3388 -u "<WINDOWS_USERNAME>" -p <WINDOWS_PASSWORD>
```

Sorry for my bad english ;)

---

### Post by Ace2016 on 2007-06-10
[B][COLOR="Blue"]Hi all

i made a [COLOR="Red"]howto entirely of screenshots[/COLOR] ;) for every single step after you install virtualbox, it has everything from sharing folders with windows, to solving the first login/logout before being able to run rdesktop problem and after its setup all you have to do is use nice Alt+F2 commands, and it has working sound too 

i made a howto with screenshots check it out here

[http://ace2016.hostistry.com/index.php/2007/07/11/seamlessly-run-windows-apps-in-linux-using-seamless-remote-desktop/](http://ace2016.hostistry.com/index.php/2007/07/11/seamlessly-run-windows-apps-in-linux-using-seamless-remote-desktop/)

:D[/COLOR][/B]

---

### Post by ran_foru on 2007-06-11
> **Ace2016 said:**
> Hi all

i made a howto with screenshots check it out here

[http://ace2016.65gb.com/index.html](http://ace2016.65gb.com/index.html)

:D

Edit:Site is back up again

HI again..

i want to share some folder as given  manul i am running the command as below
root@ranjan:~# mount -t vboxfs share /media/MySharedFolder

but i m getting the error message 
mount: unknown filesystem type 'vboxfs'


And in xp when i use the command
net use x:   \\ranjan\shared
it is asking for user name and password 
after entering both is giving error not valid user


Help me again

---

### Post by Ace2016 on 2007-06-13
> **ran_foru said:**
> HI again..

i want to share some folder as given  manul i am running the command as below
root@ranjan:~# mount -t vboxfs share /media/MySharedFolder

but i m getting the error message 
mount: unknown filesystem type 'vboxfs'


And in xp when i use the command
net use x:   \\ranjan\shared
it is asking for user name and password 
after entering both is giving error not valid user


Help me again

*cough* vbox[COLOR="Blue"]**sf**[/COLOR] *cough*

Edit: I realised your using a linux guest ;)

---

### Post by Ace2016 on 2007-06-14
> **Ace2016 said:**
> [B][COLOR="Blue"]Hi all

i made a [COLOR="Red"]howto entirely of screenshots[/COLOR] ;) for every single step after you install virtualbox, it has everything from sharing folders with windows, to solving the first login/logout before being able to run rdesktop problem and after its setup all you have to do is use nice Alt+F2 commands, and it has working sound too 

i made a howto with screenshots check it out here

[http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop](http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop)

:D[/COLOR][/B]

OK now i just tested the entire site, the thumbnail problem is fixed and the images all work, tell me if you find anything, worng, PM me

---

### Post by klisics on 2007-06-15
Hi

after two days of trying I'm about to give up. of course network problem. I have pppoe.

Before connecting to net by pon dsl-provider
```
eth0      Link encap:Ethernet  HWaddr <##HWaddr##>  
          inet6 addr: <inet addr>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:7412 (7.2 KiB)
          Interrupt:22 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr <##HWaddr##>
          inet addr:169.254.6.178  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1306 (1.2 KiB)  TX bytes:1306 (1.2 KiB)
```


After connecting to net:

```
eth0      Link encap:Ethernet  HWaddr <##HWaddr##> 
          inet6 addr: <inet addr>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:660 (660.0 b)  TX bytes:9992 (9.7 KiB)
          Interrupt:22 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr <##HWaddr##>  
          inet addr:169.254.6.178  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2560 (2.5 KiB)  TX bytes:2560 (2.5 KiB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:91.120.64.84  P-t-P:194.149.1.53  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:54 (54.0 b)  TX bytes:54 (54.0 b)
```

From the data above I couldn't manage to find out how to use the commands in the rc.local. I feel I've tried every combination exists on earth.

If you have time and want to help me pls don't hesitate :)

ps. virtualbox and xp install was succesfully done. It's feisty by the way...

thanks in advance

---

### Post by MKdon on 2007-06-16
Hi,
I have set up to run Vbox and windows XP pro under feisty,  everything works but it is not seamless the whole windows frame appears every time it starts, logging in and out does not help. Anyone else tried this under feisty, with success?

---

### Post by albesan on 2007-06-16
Hello team,

I went through this how to a couple of times, including re-installation of windows.
I can get vbox working but I can't get seamless virtualization to work.

So everything works on the vbox, network, internet etc... I added vbox to the startup programs and when I reboot I can't see any part of the windows desktop. Not the desktop itself nor the start bar at the bottom of the screen.
If I open innotech virtual box app it says that it is running, but I can't use it.

any ideas??

thanks 

a.

Edit: On start up I can even hear the windows welcome sound but I can't see anything.

---

### Post by herbster on 2007-06-16
Right when I am about to do the Windows install, after loading up VirtualBox and hitting Start on the virtual drive, I get this:

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

Anyone? I really want to get this going, looks so good! :)

---

### Post by klisics on 2007-06-16
> **herbster said:**
> Right when I am about to do the Windows install, after loading up VirtualBox and hitting Start on the virtual drive, I get this:

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

Anyone? I really want to get this going, looks so good! :)

Maybe you can try add yourself to Group **vboxusers** in: Users and Groups/Manage Groups/vboxuser/Properties

Edit:
_short status report_
I can ping the guest IP (what XP uses) from linux but I **can't ping anything** from Windows.
I can connect with rdesktop to XP by that IP but I can't get it seamless.
I think it is because of my network settings (I copied in above post) but I can't figure it out.

---

### Post by Ace2016 on 2007-06-16
tried my screenshot howto?

it has the networking setup and seamless settings all in there

Update: [http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop](http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop)

---

### Post by pascalp on 2007-06-16
Hi,

I am trying to get seamless windows working but everything I tried didn't work.

I can connect to the host, but the desktop always show up and the application I choose to launch never came up...

I modified the registry with the NoDesktop Dword.

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 100.0.7.11:3389 -u pascal -p *****

I can't find my anything, if anyone have an idea....

---

### Post by Tyke91 on 2007-06-16
phew... not trying THAT again anytime soon... i followed the instructions on the first page and nearly wound up reinstalling ubuntu... spent two hours trying to figure out how to fix a problem where the entire screen goes black and you can only acess the terminal before i finally fixed it :D

hurray feeling of satisfaction!

---

### Post by klisics on 2007-06-17
> **Ace2016 said:**
> tried my screenshot howto?

it has the networking setup and seamless settings all in there

[http://ace2016.65gb.com/index.html](http://ace2016.65gb.com/index.html)

I tried it (it's very good indeed), but I can't make it work. First of all I don't know why the pingback from XP doesn't work.
by the way I did (or tried to do) everything by your howto. I used the nodesktop registry, the 3 users, etc. etc.

for now maybe I have to be satisfied with a working xp and leave seamless things for the (near) future...

regards

---

### Post by Ace2016 on 2007-06-17
@klisics; Did you try using the instructions dubravkor gave on using nat instead?

> **dubravkor said:**
> I run it from Feisty. Here are differences from this HOWTO:

1. Set network in NAT mode: Settings -> Network -> Attached To: NAT
2. Set port forwarding. Type in terminal:
```
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/Protocol" TCP
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/GuestPort" 3389
VBoxManage setextradata "Windows XP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/guestssh/HostPort" 3388

```
3. Run VM:
```
 VBoxManage startvm "Windows XP" -type vrdp
```
4. Run rdesktop:
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" localhost:3388 -u "<WINDOWS_USERNAME>" -p <WINDOWS_PASSWORD>
```

Sorry for my bad english ;)

---

### Post by albesan on 2007-06-17
Hey Ace2016,

Thanks for the how to,very effective indeed.
I still can not get the desktop to go away.
I followed [http://ace2016.65gb.com/index.html](http://ace2016.65gb.com/index.html) , and everything works, but I'm still getting a desktop and XP runing on a window.

Any ideas on what I could do to fix this?

thanks

a.

---

### Post by Magimog on 2007-06-17
I cant get the command to run virtualbox for some odd reason. this is my error output:

[!] FAILED calling virtualBox->FindMachine(Bstr(argv[0]), machine.asOutParam()) at line 4026!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070057
[!] Text        = Could not find a registered machine named 'Windows XP Professional'
[!] Component   = VirtualBox, Interface: IVirtualBox, {d1a2295c-d257-4a4c-a9a6-843d87db6f45}
[!] Callee      = IVirtualBox, {d1a2295c-d257-4a4c-a9a6-843d87db6f45}

But my machine name IS "Windows XP Professional". thats the weird part!

---

### Post by Ace2016 on 2007-06-17
> **albesan said:**
> Hey Ace2016,

Thanks for the how to,very effective indeed.
I still can not get the desktop to go away.
I followed [http://ace2016.65gb.com/index.html](http://ace2016.65gb.com/index.html) , and everything works, but I'm still getting a desktop and XP runing on a window.

Any ideas on what I could do to fix this?

thanks

a.

Only think i can think of is that you might be using the wrong ip to connect to xp, are you using the one that you see in the network properties in xp?

---

### Post by ssc351 on 2007-06-17
> **flowingfire said:**
> I'm having a problem I've noticed several others mention, but nobody really answered it.

I have everything set up to-the-letter in Feisty, and Windows' networking integration seems to be working perfectly.  I have all the registry entries perfect.  I have seamlessrdp in the C: drive.  I have a beautiful Windows XP installation fully interoperable with Kubuntu on a networking level.

BUT- Despite my best efforts, every single time I command the thing to open, it opens in a new window.  Yes, I read carefully, and understand that you have to log out and log in again for it to work.  I did that.  No seamless integration.  I'm still in a window marked "rdesktop <ip.a.d.d.r.e.s.s>," and when I "log out" it brings me to the Windows login screen.  

I close the window and attempt to log back in-- same rdesktop window.  I shut down the virtual machine, start it back up and do the same.  Still in a window.  I try everything.  Still in a window.



Yup, I am still having the same problem as well.  Still haven't gotten an answer from anyone....Any help? Anyone Anyone?

---

### Post by Leftblank on 2007-06-18
> **Ace2016 said:**
> Only think i can think of is that you might be using the wrong ip to connect to xp, are you using the one that you see in the network properties in xp?

I was having the same issue, but following the instructions posted by Dawk solved it for me;
[quote=dawk]The problem I had with seamlessrdpshell.exe not being loaded (probably due to my vmware box being member of a domain) has been solved!
By editing HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit, changing it from
"C:\WINDOWS\system32\userinit.exe,"
into
"c:\seamlessrdp\seamlessrdpshell.exe C:\WINDOWS\system32\userinit.exe,"
I got seamlessrdpshell to load automatically.
I still don't know what to do about the locked screen problem, though. If my XP has been idle for 10 minutes, the screen locks, and that makes the XP desktop visible. I'd like to avoid that if possible.

Dawk[/quote]

A little showoff of my own setting; [[IMG]http://img164.imageshack.us/img164/8964/lindowszv4.th.png[/IMG]](http://img164.imageshack.us/img164/8964/lindowszv4.png) (direct link to the image, no popups)
I've installed the Clearlooks for XP theme to make it a bit more seamless, but I'll apply the mods to get rid of the sidebar soon, it's taking up a lot of space now ;)

---

### Post by greg.hagen on 2007-06-20
Whoa, there is a WAAAY easier way to set up the rdp forwarding for the network that doesn't involve host network adapters or anything. You can set up VirtualBox's NAT networking to forward ports!

Turn off your virtual machine, set your network card to NAT in the virtualbox settings menu and run this, replacing "Winxp" with the name of your VM:

> 
VBoxManage setextradata "WinXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rdesktop/Protocol" TCP
VBoxManage setextradata "WinXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rdesktop/HostPort" 3389
VBoxManage setextradata "WinXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rdesktop/GuestPort" 3389


Now you can connect with:

> 
rdesktop -A -s "c:\SeamlessRDP\seamlessrdpshell.exe C:\Windows\explorer.exe" localhost:3389 -u "name" -p password


This has a bunch of advantages. You don't need to check your windows ip address before connecting. In fact, it should work without even being connected to a network. Also, it only exposes the windows rdp port to the network, so is less chance of your virtual machine getting owned by some dude if you are in a coffee shop. Also, this method has a SIGNIFICANT speed boost for things like video because you are not bouncing all of your window images off of the local router. Youtube videos went from unwatchable to perfectly normal.

The disadvantages: there is no separate ip address for the virtual machine and it will not automatically share anything. If you are planning to run some kind of server (including bittorrent and itunes music sharing) it's not going to work unless you forward those ports in the same manner.

---

### Post by greg.hagen on 2007-06-20
Oops, I meant to reply to the first post. Oh well.

I also found that you can use the Alsa sound driver in virtualbox and "-r sound:remote" instead of "-rsound" for better sound sync and no grabbing of /dev/dsp. :D

I can watch futurama in windows and it looks pretty good in virtualbox :D

---

### Post by klisics on 2007-06-21
> **Ace2016 said:**
> @klisics; Did you try using the instructions dubravkor gave on using nat instead?

That works! Thanks to dubravkor & you.

---

### Post by xl_cheese on 2007-06-21
Does the seamless thing work for vista?

I'm able to run vista in vmware server.  I'm also able to run the rdesktop commands from the command line to start vista.

However it is not seamless I have a black looking desktop with a ubuntu frame.  Would someone mind taking a look?  thanks.

I should also mention that running straight from vmware there is no lag, but when using rdesktop there is a lot of lag navigating inside of vista.

Here's my ifconfig:
br0       Link encap:Ethernet  HWaddr 00:18:8B:5B:EC:D0  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe5b:ecd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18795595 (17.9 MiB)  TX bytes:3281229 (3.1 MiB)

eth0      Link encap:Ethernet  HWaddr 00:18:8B:5B:EC:D0  
          inet6 addr: fe80::218:8bff:fe5b:ecd0/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:12965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14793893 (14.1 MiB)  TX bytes:3597639 (3.4 MiB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:652 (652.0 b)  TX bytes:652 (652.0 b)

tap0      Link encap:Ethernet  HWaddr D2:3F:20:60:28:94  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d03f:20ff:fe60:2894/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:320 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.13.1  Bcast:192.168.13.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.161.1  Bcast:172.16.161.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



My rc.local:

tunctl -t tap0 -u wes
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 Localhost up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.1.255 dev tap0
 arp -Ds 192.168.1.255 eth0 pub

I'm running using this:

rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.1.2:3389 -u wesVirtual -p ****

---

### Post by dannymichel on 2007-06-22
Any tips for someone on a college campus for setting up the network?

---

### Post by xl_cheese on 2007-06-22
> **Dawk said:**
> IThe problem I had with seamlessrdpshell.exe not being loaded (probably due to my vmware box being member of a domain) has been solved!
By editing HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit, changing it from
"C:\WINDOWS\system32\userinit.exe,"
into
"c:\seamlessrdp\seamlessrdpshell.exe C:\WINDOWS\system32\userinit.exe,"
I got seamlessrdpshell to load automatically.
I still don't know what to do about the locked screen problem, though. If my XP has been idle for 10 minutes, the screen locks, and that makes the XP desktop visible. I'd like to avoid that if possible.

Dawk.

Well, I tried this on vista and now I only get a black screen trying to run the VM.  I guess I'll reinstall the vm now.

---

### Post by dannymichel on 2007-06-22
I'm confused.  it says "If you are thinking to yourself, “Well. it would just be easier to not have a password.” Stop right there and set one anyway. It is not an issue of security. If you don't setup a password then you will not be able to login to your Windows VM seamlessly.
Next, download this file: [http://howtoforums.net/downloads/seamlessrdp.zip](http://howtoforums.net/downloads/seamlessrdp.zip) and extract it to C:\seamlessrdp"

C:?
Ho wam I going to download that file and put it in C: if the guide isn't done yet and I haven't been able to connect to the internet yet
THIS is very confusing

Here is what I have seen. I know that when I used the value that came up on BCAST after I typed ifconfig eth0 | grep inet is NOT the subnet mask that I was supposed to use because when I did use that value and re-booted my PC, I was NOT able to connect to the internet.
Bu twhen I changed it back to 192.168.1.(anything) I was able to connect to the internet
NOT THROUGH WINDOWS, but through my Ubuntu.
I was never able to connect via VM to the internet
I know I must be doing something wrong.
The thing is I'm on a college campus and my settings might be slightly different than others.

---

### Post by Yumi32 on 2007-06-22
Hello,

Thanks for this tutorial. That works very good. I've used the LogOff.bat script to get the transparent desktop at the "first" connection.
But I have a question : 

How can you change CD/DVD iso loaded in the VirtualBox systeme without rebooting it. Because when you don't use the VRDP method, you can click the icon on the bottom of the VBox window to change the iso while running. But without this window ?
Is that possible using VBoxManage ? I've tried but I get this : 

```
10:25 yumi@Ubuntu ~% VBoxManage modifyvm "Windows XP" -dvd none

VirtualBox Command Line Management Interface Version 1.4.0
(C) 2005-2007 innotek GmbH
All rights reserved.

[!] FAILED calling virtualBox->OpenSession(session, uuid) at line 3206!
[!] Primary RC  = 0x80070005
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070005
[!] Text        = A session for the machine 'Windows XP' is currently open (or being closed)
[!] Component   = Machine, Interface: IMachine, {0332de0e-ce75-461f-8c6f-0fa42616404a}
[!] Callee      = IVirtualBox, {d1a2295c-d257-4a4c-a9a6-843d87db6f45}
zsh: exit 1     VBoxManage modifyvm "Windows XP" -dvd none

```

Thanks for reply

---

### Post by dannymichel on 2007-06-22
This wont work for Vista Home Premium.

---

### Post by NZ-Wanderer on 2007-06-22
Hi all, well I have spent the last few days on this now, and I've lost count on the number of times I have installed XP and Vista Ultimate...

I'm not worried about the "seemingless" part of it, as I don't want it there all the time (just when I load it)

1) Installs XP Pro and Vista Ultimate without any trouble at all...
2) Both Vista and XP talk to the Internet with no trouble at all..

3) Both XP and Vista will NOT talk to Kubuntu, Kubuntu doesn't even show up in the networking of Vista or XP :(

I have followed all steps down to the beginning of step 3)

Anyone got any ideas?? (in newbie speech please :) )

(I know I can share cause up till a few days ago I was using Vmware server, and it saw my shared drive on Kubuntu.)

I really like this Virtualbox, but I really need to see my home network...

---

### Post by Magimog on 2007-06-22
I still cannot load the VBoxManage line because it says my machine (Windows XP Professional) cant be found. It is named EXACTLY that as well, so I'm lost.


Any help is appreciated!

---

### Post by dannymichel on 2007-06-23
I'd really like to do the same thing with VMWare.
I would really like to get VMWare running headless.

---

### Post by dannymichel on 2007-06-23
> **Jose Catre-Vandis said:**
> Having abandoned this approach using virtualbox, thought I would try it out with my VMware Server installation. It works! In much the same way and following the majority of mikeytag's howto to get set up. VMware also allows command line start ups for a headless VM, and the same command for rdesktop brings home the bacon!
I have not tested extensively, but I get the task bar and menus, and still have to logon twice! and no command prompt window either.

All this in uptodate Edgy


To run a vmware OS you can use the following command in Terminal:
```
vmrun start "/full/path/to/your//VirtualMachine/Windows XP Professional.vmx"
```
(you need the quotes if you have any spaces)

then run the rdesktop command:
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <VM-IP>:3389 -u "user" -p pass
```

I hope this adds to the good work done above :-)

[EDIT]

Found an alternative command line utility that works under this setup, to resolve the problem of the command prompt not showing up. Go here:
```
http://jameser.blogspot.com/2006/07/tip-21-customizable-command-prompt-for.html
```
and follow the link to download Console 2.0 :-)

I get 
```
danny@danny-desktop:~$ vmrun start "/var/lib/vmware/Virtual Machines/Windows Vista (experimental)/Windows Vista (experimental).vmx"
danny@danny-desktop:~$ rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 10.200.128.139:3389 -u "danny" -p danny123
Autoselected keyboard map en-us
ERROR: connect: Connection refused
danny@danny-desktop:~$ rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 10.200.128.139:3389 -u danny -p XXXXXX
Autoselected keyboard map en-us
ERROR: connect: Connection refused
danny@danny-desktop:~$ 

```

---

### Post by bradmayne on 2007-06-23
i set up virtual box today and installed windows XP Pro.  I can't get on the new with Win XP.  I am using madwifi-ng and DHCP.  I do have an old orinoco gold card from agere that i could use if it comes down to it.  Can someone do a walkthrough and tell me what to edit in the /etc/rc.local file so i can go on wirelessly?  I'd really appreciate it! thanks guys.

---

### Post by ViperKnight on 2007-06-23
This sounds great...although it didn't really work perfectly on my comp.

But I'm happy using the VBox Full-Screen mode and hiding the Gnome Panels.  That way Windows only occupies one desktop space and avoids the remote desktop lag;)

Although, I'm going to try and see if somehow I can use "full-screen" but change the resolution so it is rendered in between my Gnome Panels.....no idea where to start though:p

---

### Post by dannymichel on 2007-06-24
I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]

---

### Post by Nigmah on 2007-06-24
[COLOR=DarkOrange][B]Ok i've follow the instructions almost exactly up to installation of windows everytime i try i get an error talking about my hardware. Heres the technical info it gives me

exit: 0x00000012 (0x00000001 0x00000000 0x00000000 0x00000000)
[/B][/COLOR]

---

### Post by dannymichel on 2007-06-24
> **Nigmah said:**
> [COLOR=DarkOrange][B]Ok i've follow the instructions almost exactly up to installation of windows everytime i try i get an error talking about my hardware. Heres the technical info it gives me

exit: 0x00000012 (0x00000001 0x00000000 0x00000000 0x00000000)
[/B][/COLOR]
Isn't that a Qemu message?
> **dannymichel said:**
> I'm having a real hard time making my VMWare with Vista 32 bit Home Premium installed on my Ubuntu Feisty seamless as if it's a part of Ubuntu as I have seen on other guides and posts.

So far what I've done is:
[LIST]
[*]Install RDesktop
[*]Install Vista (Home Premium 32 bit) on VMWare
[*]InstallVMWare Tools on my Vista (Home Premium 32 bit) VM
[/LIST]

Some issues:
[LIST]
[*]One issue is that I can't connect to the internet on my VM when I use a "Host Only" connection.
[*]No sound card installed on VM
[/LIST]
I guess noone knows how to do this with VMWare?

---

### Post by Nigmah on 2007-06-24
[COLOR=DarkOrange][B]qemu? what do you mean?

anyways im going to try it with vmware
[/B][/COLOR]

---

### Post by EXCiD3 on 2007-06-24
Since i dont have a wired network, will using wireless effect any of this tut?

---

### Post by yagood on 2007-06-25
Nice HOWTO. One thing - there's really no need for setting up Host networking, you can just use VirtualBox's built-in DHCP and NAT. Just set guest's network adapter to NAT, it'll get IP like 10.0.2.15 from VirtualBox. Of course it's not going to be visible to the host system, but that's not a problem since VirtualBox has the ability to forward ports. Like this:

> 
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/Protocol" TCP 
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/GuestPort" 3389
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/HostPort" 6666


Now any communication sent to host's port 6666 will be forwarded by VirtualBox to guest's port 3389, so you need to change the connection command:

> rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" localhost:6666 -u <username> -p <password>

And that's it.

Of course setting up Host networking has its advantages - guest becomes a part of the local network so you can easily do some resource sharing or whatever, but doing it the way I described above is a quick and easy set up if you want to just check how seamless integration works.

---

### Post by jms830 on 2007-06-26
Help! How do I add myself? I tried doing it through the System>Administration menu, but it wont work

```
WARNING: You are not a member of the "vboxusers" group.  Please add yourself
         to this group before starting VirtualBox.

         You will not be able to start VMs until this problem is fixed.
VirtualBox Command Line Management Interface Version 1.4.0
(C) 2005-2007 innotek GmbH
All rights reserved.

```

---

### Post by yagood on 2007-06-26
> **jms830 said:**
> Help! How do I add myself? I tried doing it through the System>Administration menu, but it wont work


Like this:

> 
sudo usermod -a -G vboxusers <username>


---

### Post by Magimog on 2007-06-26
Can anyone explain why the NoDesktop entry does not work for me? All it did was turn the background color black...

---

### Post by hotplainrice on 2007-06-27
Thanks.. It rocks.

Running on vmware 6.0

Just wondering, anyone knows how can I have a hide button on the XFCE panel?

---

### Post by T0MA on 2007-06-28
After you made the changes in the registry restart the vm, log in and then log off! Otherwise rdesktop will bring the whole desktop.

---

### Post by Magimog on 2007-06-28
I finally got it working! 

Now my only problem is that the start menu is continually blinking as if it has a border aorund it... anyway to stop that?

---

### Post by Nigmah on 2007-06-28
im trying to get windows running in ubuntu but everytime i try to i get this error 
 
A problem has been detected and Windows has been shut down to prevent damage to your computer.  
 
TRAP_CAUSE_UNKNOWN 
 
If this is the first time you've seen this Stop error screen, restart your computer. If this screen appears again, follow these steps: 
 
Check to make sure any new hardware or software is properly installed. If this is a new installation ask your hardware or software manufacturer for any Windows updates you might need. 
 
If problems continue, disable or remove any newly installed hardware or software. Disable BIOS memory options such as caching or shadowing. If you need to use Safe Mode to remove or disable components, restart your computer, press F8 to select Advanced Startup Options, and then select Safe Mode. 
 
Technical information: 
 
*** STOP: 0x00000012 (0x00000001,0x00000000,0x00000000,0x00000000) 
 
I believe it may be related to a bios error i get every time i start up ubuntu 
 
MP-BIOS bug: 8254 timer not connected to IO-APIC 
(though its missing a couple number at the beggining in [ ]) 
 
please help and much thanks for help!

---

### Post by Magimog on 2007-06-28
**Nigmah** -I'm not 100% certain on this but I don't think Vbox looks at your actual bios, just one that Innotek provides...

---

### Post by Nigmah on 2007-06-28
[COLOR=DarkOrange][B]ok i managed to get it to install by pressing e when grub boots up and e on kernel and appending noapic nolapic acpi=off pci=noacpi
but the problem with that is that my computer doesn't recognise any of by usbs, very annoying for an external + wireless keyboard which both run off usb.

I've narrowed it down to needing noapic to get ride of the error but if i just use noapic then ubuntu won't boot.

alsoif someone knows a way to fix this how do i change the size of my xp install i'm already outa of the 5 gigs.
[/B][/COLOR]

---

### Post by robinl on 2007-06-29
This is great... if it had worked... Following this tutorial in the networking part completely kills my host internet connection, so I went with VMWare Server instead and done everything except logging in with rdesktop. It keeps on saying "Connection Reset By Peer" and my guest OS can't really access my host OS (I can ping both ways, but I can't see samba shares and can't see my Apache server form my guest OS). It's set in bridged mode but I've tried NAT mode is well and have the same results. Anyone have any ideas?

---

### Post by T0MA on 2007-06-29
> **robinl said:**
> This is great... if it had worked... Following this tutorial in the networking part completely kills my host internet connection, so I went with VMWare Server instead and done everything except logging in with rdesktop. It keeps on saying "Connection Reset By Peer" and my guest OS can't really access my host OS (I can ping both ways, but I can't see samba shares and can't see my Apache server form my guest OS). It's set in bridged mode but I've tried NAT mode is well and have the same results. Anyone have any ideas?

You can use NAT with Virtualbox, just skip the networking part of the tutorial and port-forward a connaction to the vm by applying these settings:

VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/Protocol" TCP
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/GuestPort" 3389
VBoxManage setextradata "xp" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/HostPort" 6666

You will be able to connect with rdesktop to the vm at localhost:6666

---

### Post by robinl on 2007-06-30
Ah yes THANK YOU that worked perfectly!

---

### Post by althea on 2007-07-02
Great tutorial. Everything works except no integration. I get the full desktop (minus desktop icons due to the policy change). Any ideas?

---

### Post by Nigmah on 2007-07-03
[B][COLOR=DarkOrange]For future reference of anyone i believe i've found a fix to my problem by appending acpi_skip_timer_override to the end of my kernel options

ok new problem im on this part
[/COLOR][/B]rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <IP recorded from Windows>:3389 -u "<Your Windows Username>" -p <Your Windows Password>
but everytime i do i get this
rdesktop: A Remote Desktop Protocol client.
Version 1.5.0. Copyright (C) 1999-2005 Matt Chapman.
See [http://www.rdesktop.org/](http://www.rdesktop.org/) for more information.

Usage: rdesktop [options] server[:port]
   -u: user name
   -d: domain
   -s: shell
   -c: working directory
   -p: password (- to prompt)
   -n: client hostname
   -k: keyboard layout on server (en-us, de, sv, etc.)
   -g: desktop geometry (WxH)
   -f: full-screen mode
   -b: force bitmap updates
   -L: local codepage
   -A: enable SeamlessRDP mode
   -B: use BackingStore of X-server (if available)
   -e: disable encryption (French TS)
   -E: disable encryption from client to server
   -m: do not send motion events
   -C: use private colour map
   -D: hide window manager decorations
   -K: keep window manager key bindings
   -S: caption button size (single application mode)
   -T: window title
   -N: enable numlock syncronization
   -X: embed into another window with a given id.
   -a: connection colour depth
   -z: enable rdp compression
   -x: RDP5 experience (m[odem 28.8], b[roadband], l[an] or hex nr.)
   -P: use persistent bitmap caching
   -r: enable specified device redirection (this flag can be repeated)
         '-r comport:COM1=/dev/ttyS0': enable serial redirection of /dev/ttyS0 to COM1
             or      COM1=/dev/ttyS0,COM2=/dev/ttyS1
         '-r disk:floppy=/mnt/floppy': enable redirection of /mnt/floppy to 'floppy' share
             or   'floppy=/mnt/floppy,cdrom=/mnt/cdrom'
         '-r clientname=<client name>': Set the client name displayed
             for redirected disks
         '-r lptport:LPT1=/dev/lp0': enable parallel redirection of /dev/lp0 to LPT1
             or      LPT1=/dev/lp0,LPT2=/dev/lp1
         '-r printer:mydeskjet': enable printer redirection
             or      mydeskjet="HP LaserJet IIIP" to enter server driver as well
         '-r sound:[local|off|remote]': enable sound redirection
                     remote would leave sound on server
         '-r clipboard:[off|PRIMARYCLIPBOARD|CLIPBOARD]': enable clipboard
                      redirection.
                      'PRIMARYCLIPBOARD' looks at both PRIMARY and CLIPBOARD
                      when sending data to server.
                      'CLIPBOARD' looks at only CLIPBOARD.
   -0: attach to console
   -4: use RDP version 4
   -5: use RDP version 5 (default)

 or

ERROR: connect: No route to host

[COLOR=DarkOrange][B]and i did make the toolbar
oh and yes i've chekced to make sure theres no toolbar below the toolbar
[/B][/COLOR]

---

### Post by ajeffreys on 2007-07-04
One question before I follow this tutorial. Will it work with XP Home or is it only for XP professional?

---

### Post by mr_byte on 2007-07-07
Ajeffreys: This only works with Pro, or so they say.


I will attempt to consolidate what I did to make this work for me, as the information is in this post, but it's strewn thru and it's time consuming to parse the whole post to find it.

I run Kbuntu Feisty, I'm using VirtualBox and XP Pro.  I have not yet made this autorun at KDE boot. I installed VBox via Automatix.

1. You do not need to disable network manager, nor do you need a configure a bridge.  Using VBoxManage you can redirect a port on the host machine to connect to a port on the VM. Or, redirect the VM to a port on the Host. I use a script to run the VM and redirect the port:

```

VBoxManage startvm "SeamlessXP" -type vrdp
VBoxManage setextradata "SeamlessXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/Protocol" TCP
VBoxManage setextradata "SeamlessXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/GuestPort" 3389
VBoxManage setextradata "SeamlessXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/HostPort" 6666
```

This allows you to redesktop using localhost:6666 as IP to connect to, without the nasty side effects of disabling network manager, if you are in the group that must have it, like me :D

2.  It is possible to automagically logoff the VM, avoiding the need to do the "first logoff" bit.. I have my VM set to logon automatically as administrator:

Inside your VM, go to Start/Run -> control userpasswords2

Check then uncheck the "Require all users to log in" or some such at the top of this app, then apply.

Windows will ask you for a username and password to log in as.  I use Administrator and my admin password.  This would require you to have a seperate user account.  I use Jeff for seamless goodness, and administrator within the VM, when running it in a window.

Now, to change a policy, ala TabletGuy:

> 3. Inside your windows machine make a bat file which will execute the shutdown command.
3.A) Open windows explorer and find the c:\ folder.
3.B) Right click in the folder and create a new text document (right click > new > text document).
3.C) Name the text document logoff.bat
3.D) Right click on your new logoff.bat file and choose edit, notepad will pop up
3.E) enter this command into the bat file:

I changed to this:

```
c:\windows\system32\logoff.exe
rem There is no need to download the Shutdown.exe program.  XP has this stuff already.

```

> Now we need to make windows call this bat file each time the machine starts (but not when a user logs on).
4. Add a call to the bat file to the startup scripts using the Group policy editor:
4.A) In your windows VM click start > run and type in mmc.
4. B) Open the group polcy editor:
Click File > Add/Remove Snap-In (up pops the add/remove dialog box)
Click Add
Scroll down to Group Policy and select it
Click Add, then finish, then close
Click ok

4. C) Find the Windows start up/shutdown scripts
Expand the Local Computer Policy > Computer Configuration > Windows Settings and select Scripts (Startup/Shutdown)

4.D) Double click on StartUp

4.E) Click Add to add a new script

4. F) In the script name box enter:
c:\logoff.bat

4.G) Click OK and Ok again and you done.

No more need to log off on first rdesktop connection.


3. Using VBoxManage to power off the VM seems to work ok for me.  When I run the VM in windows mode, there is never a CHKDSK window that you'd expect from a non-normal shutdown.  I suppose an alternative to this would be a link in the quicklaunch bar to shutdown the VM.  There is probably a way to get this onto the start menu, overriding the behavior that removes shutdown from the menu when we are connected "remotely" by editing some registry entry, but I'm not Windozy enough to know this. :D

I'm not yet KDE'y enough to have figured out how to make this all autorun at startup, but I'll get that, or someone may generously post it here ;)

This is what works for me. YMMV.

Jeff

---

### Post by JAmerican on 2007-07-09
Amazing work!! Works great. I haven't read every post but my solution to the Log On then Log Off problem is to just run XP in VBox and log in then log out. Then I place it in my fourth workspace. This is so that I can still mount CDs and disk images as well as still have control of the virtual machine.

JAmerican :) I'm installing Visual Basic as well. BTW, I did your tutorial over NoMachine's NX Remote Desktop software with minor problems that delt with permissions and VBox. Other than that, works great :)

So I did the tutorial remotely wih my Mac laptop connected to Ubuntu installing Windows. That's everything in one :).

JA

---

### Post by spiderman1369 on 2007-07-10
Ace2016,

The link for the download.zip file at [http://ace2016.atspace.com/seamless/index.html](http://ace2016.atspace.com/seamless/index.html) doesn't seem to be working. Can you please update the link or the file? Thanks!

---

### Post by mr_byte on 2007-07-10
> **JAmerican said:**
> Amazing work!! Works great. I haven't read every post but my solution to the Log On then Log Off problem is to just run XP in VBox and log in then log out. Then I place it in my fourth workspace. This is so that I can still mount CDs and disk images as well as still have control of the virtual machine.

VBoxManage controlvm <VM Name> dvdattach <full path and name of file> mounts CD images.

VBoxManage controlvm <VM Name floppyattach <full path and name of file> mounts floppy images. 


I added some stuff to my seamlessstart script, and to my logoff.bat to coordinate when to start the remote session.

seamlessstart:
```

# first delete the flag file.
rm -f /home/jeff/flag.txt


VBoxManage startvm "SeamlessXP" -type vrdp
VBoxManage setextradata "SeamlessXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/Protocol" TCP
VBoxManage setextradata "SeamlessXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/GuestPort" 3389
VBoxManage setextradata "SeamlessXP" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/rd/HostPort" 6666


while [ ! -e /home/jeff/flag.txt ] ; do
  sleep 10
done

rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\windows\explorer$

```

logoff.bat
```

net use x: \\vboxsvr\jeff
echo done!>>x:\flag.txt
logoff.exe

```

Note that you will need to set up a share in VirtualBox sharing your home directory (mine is jeff...) to do the flag.txt thing.

There might be a better way to do this, using something less ugly, but this works well enough for me. I grabbed the windows-logo from the OP's post and used that for my icon and stuck it in my quicklauncher.  

Still working on a shutdown script for the windows session.  I tried Start/Run -> shutdown -f  but that leaves the machine running according VirtualBox.

Probably google up an answer, eventually.

Jeff

---

### Post by SyberKowboy on 2007-07-10
[SIZE="4"]For anyone who has had trouble getting this too work here are some of my suggestions![/SIZE]

1. Make sure you install Beryl before you start doing anything. Not really sure what this thing does other then somekind of gui framing software and I could have read about it on the site but I just jumped straight to the wiki and followed the how-to for Ubuntu install. Not to terribly hard to follow. I think that was why it didn't work the first go around.

2. Use the "localhost" method first posted by dubravkor and quoted by others. It is way easier to play with. I followed the first section by mikeytag to get the VM setup. Ace2016's image set is really good too, but a couple of the later links are down or something and his first set is great if you have a fixed network with static IPs or your router is set to hand out the same IPs all the time. If you have a network manager(i.e. wireless) or are using a large DHCP network I would let VirtualBox handle the IP, DHCP, and bridging via NAT.  I think mr_byte has an excellent explanation with a little added goodness. I'm using the logoff.bat he and miketag suggested. Make sure you set up the admin acount as default and use the "user" account for terminal (RDP).

3. If you use the port mapping technique, write a script to map the the ports on start up and either do as mr_byte did and then start the VM during your system startup with Preferences>Sessions>Startup "Add". The way I did it was to create a new script in /usr/bin (or anywhere else for that matter) and add the mapping lines and/or the vmstart command (if you are really confused by this point this mod is not for you) and then call it at startup.  Then make another script to start the rdesktop command and make a new quick launch icon on you Ubuntu taskbar. Or if you don't want it running all the time (the VM version of XP) write a script that starts the vm and waits 35 seconds or so with the sleep command and then launches rdesktop. Then within xp you can run taskmanager and shut the vm down when you're done. In this way I can control when the vm runs, log in via rdp or VirtualBox's gui, and can free up resources when I need to.

Anyway this is a badass thread and thanks to everyone who help clear up the massive confusion about the rc.local bit. BTW has anyone got the vm working with a network manager and dhcp for all us wireless junkies? seems like you could create some kind of script with conditional resolution to set the guest ip etc. I'd love to see that work. Thanks again,

:KS

---

### Post by SyberKowboy on 2007-07-10
> **mr_byte said:**
> 

Note that you will need to set up a share in VirtualBox sharing your home directory (mine is jeff...) to do the flag.txt thing.

There might be a better way to do this, using something less ugly, but this works well enough for me. I grabbed the windows-logo from the OP's post and used that for my icon and stuck it in my quicklauncher.  

Still working on a shutdown script for the windows session.  I tried Start/Run -> shutdown -f  but that leaves the machine running according VirtualBox.

Probably google up an answer, eventually.

Jeff

This is some good stuff. I was using a 35 sec sleep delay but the flag is way better. BTW, if you want to shutdown easy just start "Task Manager" by right clicking the taskbar select task manager and then goto Shutdown>Turn off. You most likely know this but others may not.

---

### Post by mitsuo on 2007-07-11
after appending the following lines to rc.local i cant access the internet anymore:

```
tunctl -t tap0 -u mitsuo
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.10.5 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.10.4 dev tap0
 arp -Ds 192.168.10.4 eth0 pub
```

what did i miss out?

---

### Post by Ace2016 on 2007-07-11
Hi all my exams are now over and i made this new guide:

[http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop](http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop)

Its a much better version than the one before :KS

Its back, new hosts, paid one this time, and a new domain, should work fine from now on :)

---

### Post by ZX3Junglist on 2007-07-12
> **Ace2016 said:**
> Hi all my exams are now over and i made this new guide:

[http://ace2016.hostistry.com/index.php/2007/07/11/seamlessly-run-windows-apps-in-linux-using-seamless-remote-desktop/](http://ace2016.hostistry.com/index.php/2007/07/11/seamlessly-run-windows-apps-in-linux-using-seamless-remote-desktop/)

Its a much better version than the one before :KS

Edit: The server had some downtime but now its working fine

Absolutely awesome!!!!

I plan on using this when I find the time.

---

### Post by mitsuo on 2007-07-12
indeed, helped me solve the issue..
but there is an issue i can't solve yet, the video i play has awful lag.. when i play it naturallyin the vm its ok..
another thing id when i load video into aegisub in vm, i can see the video, wherease when i load it via rdesktop, video sections appears pitch black... however the sound is still there..

---

### Post by two-sheds on 2007-07-12
I came across this howto as part of trying to get rdesktop setup for use on my Nokia 770.  I came up with an interesting setup which works rather well.  If there was any need to use Windows more often, I can actually run both simultaneously.  The Windows XP was upgraded to a Vista like shell that seems to run a lot smoother than explorer. 

Take a look at:

[http://www.youtube.com/watch?v=imBqb6vK2x4](http://www.youtube.com/watch?v=imBqb6vK2x4)

---

### Post by two-sheds on 2007-07-12
> **mitsuo said:**
> indeed, helped me solve the issue..
but there is an issue i can't solve yet, the video i play has awful lag.. when i play it naturallyin the vm its ok..
another thing id when i load video into aegisub in vm, i can see the video, wherease when i load it via rdesktop, video sections appears pitch black... however the sound is still there..

In a sense, the video is all being streamed to a remote client even though they are on the same screen.  When trying to watch videos, both the screen and the video have to be streamed from the server to the client. As a consequence there will be a decrease in performance.

---

### Post by Espreon on 2007-07-12
Will this work with XP Home? and If I want to do this on an nLighted install what components do I need to keep?

---

### Post by SyberKowboy on 2007-07-12
Looks super! Thanks for the great work! :)

---

### Post by SyberKowboy on 2007-07-12
> **Espreon said:**
> Will this work with XP Home? and If I want to do this on an nLighted install what components do I need to keep?

I don't think XP Home supports terminal services (RDP) and that is the main component of this process working so no, I don't think it'l work on XP home.

---

### Post by mitsuo on 2007-07-12
> **two-sheds said:**
> In a sense, the video is all being streamed to a remote client even though they are on the same screen.  When trying to watch videos, both the screen and the video have to be streamed from the server to the client. As a consequence there will be a decrease in performance.

is there any workaround for that?

---

### Post by EXCiD3 on 2007-07-12
Umm, yeah...watch the video in Ubuntu, not with Windows.

---

### Post by Tuxbee on 2007-07-13
> logoff.bat
```

net use x: \\vboxsvr\jeff
echo done!>>x:\flag.txt
logoff.exe

```

Note that you will need to set up a share in VirtualBox sharing your home directory (mine is jeff...) to do the flag.txt thing.

Jeff

This script worked for me, but only after I put it in the **menu 'Startup'**, under 'Start', 'all programs'
If I add it to 'startup scripts' with the 'group policy manager' I get an error window, no flag file written, and then logout.

thx

---

### Post by two-sheds on 2007-07-13
> **mitsuo said:**
> is there any workaround for that?

export XLIB_SKIP_ARGB_VISUALS=1  globally or launch  rdesktop with  XLIB_SKIP_ARGB_VISUALS=1 rdesktop "$@"

[http://www.davtar.org/blog/?p=25](http://www.davtar.org/blog/?p=25)

---

### Post by two-sheds on 2007-07-13
> **mitsuo said:**
> is there any workaround for that?

I am not sure that there is a perfect solution but you can try:

export XLIB_SKIP_ARGB_VISUALS=1 from the command prompt before running rdesktop 
or launch  rdesktop with  XLIB_SKIP_ARGB_VISUALS=1 rdesktop "$@"

[http://www.davtar.org/blog/?p=25](http://www.davtar.org/blog/?p=25)

---

### Post by xl_cheese on 2007-07-13
Can someone please help me out?:confused:

ifconfig:
```
br0       Link encap:Ethernet  HWaddr 00:18:8B:5B:EC:D0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe5b:ecd0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:198077662 (188.9 MiB)  TX bytes:13576419 (12.9 MiB)

eth0      Link encap:Ethernet  HWaddr 00:18:8B:5B:EC:D0  
          inet6 addr: fe80::218:8bff:fe5b:ecd0/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:150516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:201030335 (191.7 MiB)  TX bytes:14198964 (13.5 MiB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:86716 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86716 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:322441147 (307.5 MiB)  TX bytes:322441147 (307.5 MiB)

tap0      Link encap:Ethernet  HWaddr B6:A9:47:A0:BE:39  
          inet addr:127.0.0.1  Bcast:127.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::b4a9:47ff:fea0:be39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:2796 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.13.1  Bcast:192.168.13.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.161.1  Bcast:172.16.161.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

rc.local:  I've been trying either variation posted in this thread.

```
#tunctl -t tap0 -u wes
# chmod 0666 /dev/net/tun
# /usr/sbin/brctl addbr br0
# /sbin/ifconfig eth0 0.0.0.0 promisc
# /usr/sbin/brctl addif br0 eth0
# /sbin/dhclient br0
# /usr/sbin/brctl addif br0 tap0
# ifconfig tap0 192.168.1.163 up
# bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
# route add -host 192.168.1.2 dev tap0
# arp -Ds 192.168.1.2 eth0 pub
####################################
tunctl -t tap1 -u wes
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
sudo ifconfig br0 192.168.1.169 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.2 br0
brctl addif br0 tap0
ifconfig tap0 up
exit 0
```

Executing:

```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 10.0.2.15:3389 -u wes -p password
```

It doesn't work.  

I've been trying to do it on both of my computers with no sucess.  Trying vista ultimate on one and xp pro on the other.

the virtual box is able to boot to windows, but I can't get these scripts working.

-seamlessrdp.exe exists in the correct location
-reg keys are configured correctly

From windows VM:

IPv4 IP Address                          10.0.2.15

Not really sure what I'm doing wrong?

thanks.

---

### Post by Nigmah on 2007-07-13
[COLOR=DarkOrange]**using this guide(as posted before)**[/COLOR]
[COLOR=DarkOrange]**[http://ace2016.hostistry.com/index.php/2007/07/11/seamlessly-run-windows-apps-in-linux-using-seamless-remote-desktop/#comment-27](http://ace2016.hostistry.com/index.php/2007/07/11/seamlessly-run-windows-apps-in-linux-using-seamless-remote-desktop/#comment-27)**[/COLOR]
[COLOR=DarkOrange][B]i get up to step(or stage whichever you wan&#8217;t to call it) 188, or the stage where i'm starting up remote desktop (i&#8217;m not running kubutu but ubuntu) 
[/B][/COLOR]
[COLOR=DarkOrange]**i get an error**[/COLOR]
[COLOR=DarkOrange]**upon trying to boot the vm i get this error**[/COLOR] [COLOR=DarkOrange]**Failed to start VM execution (VERR_PDM_CFG_MISSING_DRIVER_NAME).**[/COLOR]
 [COLOR=DarkOrange][B]Result Code:
0×80004005
Component:
Console
Interface:
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}[/B][/COLOR]
 ****
[B][COLOR=DarkOrange]I tried using sudo /etc/init.d/vboxdrv setup multiple times and i also reinstalled vbox using synaptic package manager, which didn&#8217;t work.
sudo modprobe vboxdrv doesn&#8217;t not give me an output as it should.[/COLOR][/B]


**[COLOR=DarkOrange]help much appreciated[/COLOR]**

---

### Post by xl_cheese on 2007-07-14
> **Ace2016 said:**
> Hi all my exams are now over and i made this new guide:

[http://ace2016.hostistry.com/index.php/2007/07/11/seamlessly-run-windows-apps-in-linux-using-seamless-remote-desktop/](http://ace2016.hostistry.com/index.php/2007/07/11/seamlessly-run-windows-apps-in-linux-using-seamless-remote-desktop/)

Its a much better version than the one before :KS

Edit: The server had some downtime but now its working fine

I followed your guide to the T.  Started fresh.  Double checked EVERY step.  Still would not work completely.  I got closer tho.  Was able to get vista with a black desktop.

At any rate I have since not been able to boot up my ubuntu box.  It hangs during boot just before the splash screen.

Reinstalling the entire OS now.:(

I don't know why I can't do this?  I'm a F#$kin' moron.

---

### Post by John Jason Jordan on 2007-07-14
Thanks for the great tutorial. I got VirtualBox installed with no problems on my Feisty amd64 desktop. Then I installed Windows 2000 Pro. (I have a spare license for XP, but MS allows you to use the newer license for the older OS if you wish.) Windows 2000 runs great and everything is working - sound, network, etc.

I have Crossover Office installed as well, and everything I need works fine, except I can't get InDesign to install under Crossover Office. Therefore, that is my whole purpose for installtin VirtualBox. I installed InDesign 1.5 and the setup went fine. However, when I tried to launch it I got an error message that it requires at least 256 colors. Checking the desktop properties I find that I was running Windows 2000 at 640 x 480, 16 colors. You can change it to 800 x 600 (and I did), but you still can't get more than 16 colors. 

Feisty is running at 1680 x 1050 on my 20" widescreen with nVidia GeForce 6150. I don't need the VM to run that high, but I do need a bigger screen and decent color depth. I skimmed through this entire thread (pages and pages and pages!) but I didn't see any discussion of this. Have I missed it? If so, would someone kindly point me to it? Or just tell me the answer?

Edit: Installed Guest Additions and problem resolved.

---

### Post by Nigmah on 2007-07-15
[COLOR=DarkOrange]**Just to let Ace know if he doesn't already, his site is down.**[/COLOR]

---

### Post by Ace2016 on 2007-07-15
> **Nigmah said:**
> [COLOR=DarkOrange]**Just to let Ace know if he doesn't already, his site is down.**[/COLOR]

Thanks, it got deleted by hostistry, no warning and no reason at all was given, now i'm back with a paid host and a good domain name

[http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop](http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop)

I had a backup but lost the comments

---

### Post by Zyrshnikashnu on 2007-07-15
This is an excellent tutorial, and the NAT method is a great way to avoid losing NetworkManager. It's bloody nice to have this VM available anywhere.

However, the seamless integration is failing for me. Everything else is flawless. Logging out and calling rdesktop fails. It simply takes me back to the login screen, where I left it. Shouldn't the command log me in at the least?

---

### Post by rjs82vette on 2007-07-15
I just got done doing this to my system...... All I got to say is that you guys are sick.......

what nut wants to have Ubuntu and Windows on the same desktop?

well besides me that is......... 

^ ^ ^ Joke ^ ^ ^ before any really up tight person get offended ^ ^ ^ Joke ^ ^ ^

Good job on the howto, I only had a few small issues because I cant follow directions... 

and when I run "VBoxManage startvm "WindowsXP" -type vrdp" in terminal it says my sound card is busy so I don't get any sound in windows.... other than that it seems to be working good....

Thanks for sharing.....

---

### Post by John Jason Jordan on 2007-07-15
> **John Jason Jordan said:**
>  ... Checking the desktop properties I find that I was running Windows 2000 at 640 x 480, 16 colors. You can change it to 800 x 600 (and I did), but you still can't get more than 16 colors. 

Feisty is running at 1680 x 1050 on my 20" widescreen with nVidia GeForce 6150. I don't need the VM to run that high, but I do need a bigger screen and decent color depth. I skimmed through this entire thread (pages and pages and pages!) but I didn't see any discussion of this. Have I missed it? If so, would someone kindly point me to it? Or just tell me the answer?

Edit: Installed Guest Additions and problem resolved.

OK, that worked, but I later discovered that 4 GB is not a big enough disk size, so I had to start over. I successfully created a new machine and installed Windows 2000 in it. To get a decent resolution I clicked on Machine > Install Guest Additions. Last time after doing this I could select lots of resolution options, but this time it doesn't work. I'm still stuck with 16 colors and VGA at either 640x480 or 800x600.

When I clicked on Machine > Install Guest Additions nothing happened. I wonder if they're really installed. It seems to me that last time there was a little icon for Guest Additions down in the lower right corner of the VM window. This time there is no icon there at all. 

Why would clicking on Machine > Install Guest Additions not install the guest additions? How can I be sure they are or are not installed? Is there an alternate way to install the guest additions?

---

### Post by SyberKowboy on 2007-07-16
> **rjs82vette said:**
> I just got done doing this to my system...... All I got to say is that you guys are sick.......

what nut wants to have Ubuntu and Windows on the same desktop?

well besides me that is......... 

^ ^ ^ Joke ^ ^ ^ before any really up tight person get offended ^ ^ ^ Joke ^ ^ ^

Good job on the howto, I only had a few small issues because I cant follow directions... 

and when I run "VBoxManage startvm "WindowsXP" -type vrdp" in terminal it says my sound card is busy so I don't get any sound in windows.... other than that it seems to be working good....

Thanks for sharing.....

I think I had a similar problem when I was messing about with it. I'm not sure but I think the problem has something to do with ALSA running some process. If I wasn't running any sound related devices it worked great. Might need to have the Guest side apps installed too. Either way I don't have that problem anymore.

---

### Post by Ace2016 on 2007-07-16
You have to unmount any isos that are mounted at the moment and also remove any disks from your physical drive, virtualbox installs the addons using an iso, its is located here:

/opt/VirtualBox-1.4.0/additions/VBoxGuestAdditions.iso

---

### Post by T0MA on 2007-07-18
does anyone know if there is a way to automatically save the state of the virtual machine when I restart or power off my computer?

---

### Post by starfry on 2007-07-18
Hi, after following the above parrot-fashion I thought I'd delve in and try and understand it. I've found the networking setup is very simple. All I needed was:

To create a bridge and put eth0 into it: replace the eth0 setup in /etc/network/interfaces with this:
```

auto br0
iface br0 inet dhcp
    bridge-ports eth0

```

In a virtualbox network "start application" script:
```

iface=$(/usr/sbin/tunctl -b -u $SUDO_USER)
/sbin/ifconfig $iface up
/usr/sbin/brctl addif br0 $iface

```

In a virtualbox netwok "terminate application" script:
```

sudo /usr/sbin/brctl delif br0 $2
sudo tunctl -d $2

```

These scripts can then be called from Virtualbox on startup by putting their paths (prefixed with "gksudo") in the appropriate places on the Network Settings screen.

The only other thing needed is to make "/dev/net/tun" world writable.

That's it! No promiscuous mode, no proxy_arp, no adding routes or priming the arp cache. I've read the theory and I think some of these *should* be needed but my tests have shown they aren't.

I have tested this on Feisty with both Virtualbox and QEmu and it seems fine. I can't help thinking the other commands are needed for other reasons I haven't encountered and, if so, would like to know what these reasons are. Can anyone enlighten me...

---

### Post by rjs82vette on 2007-07-18
Now I have it all setup the way I want it...... I have a few question....

Video performance is really bad, and as I understand it there is not much I can do about it.

Would the performance be any better if I was running xp on a different box? That way my system would only run Ubuntu and rdesktop and the other machine would run windows xp. 

if I take the virtual machine part out all together can I still make it seamless?

---

### Post by dirken on 2007-07-24
hey everyone,

i was wondering if anyone could help me.
My laptop is a dell inspiron 6000 and is having wireless internet on an ubuntu feisty system.
I get my ip through dhcp but i am having always the same ip: 192.168.1.2
My gateway address is 192.168.1.1. In VirtualBox i have set up a network card with NAT.
Can you help me getting it all to work. Tried almost everything in this topic but nothing happens.
I installed Windows XP pro, did all the modifications concerning the registery and the automatic logon.
I already was able to get it working with VMware but that's slowing down my system a lot so i prefer VirtualBox. What I need to know is how my rc.local file must look like and if i have to do extra things in my VM.
Little note: i am using feisty WITH network manager and don't like to disable it :)

Really hopes anyone can help me!!!

Kind Regards,

---

### Post by airbornespent on 2007-07-26
> **dirken said:**
> hey everyone,

i was wondering if anyone could help me.
My laptop is a dell inspiron 6000 and is having wireless internet on an ubuntu feisty system.
I get my ip through dhcp but i am having always the same ip: 192.168.1.2
My gateway address is 192.168.1.1. In VirtualBox i have set up a network card with NAT.
Can you help me getting it all to work. Tried almost everything in this topic but nothing happens.
I installed Windows XP pro, did all the modifications concerning the registery and the automatic logon.
I already was able to get it working with VMware but that's slowing down my system a lot so i prefer VirtualBox. What I need to know is how my rc.local file must look like and if i have to do extra things in my VM.
Little note: i am using feisty WITH network manager and don't like to disable it :)

Really hopes anyone can help me!!!

Kind Regards,
dirken:
Follow the steps below and go to VBox settings and change the network from NAT to attached to and put tap1 in the interface name box below. These settings worked fine for me. Also pay particular attention to the HOWTO where michael mentions to get the IP from inside the windows VM, use that to login with rdesktop.

> **ravinsp said:**
> Actually we don't have to disable ubuntu network manager to connect the vm to network.

These are the lines i added to **rc.local** file (I did it according to the VirtualBox user manual with a slight modification) :

[FONT="Lucida Console"]tunctl -t tap1 -u <Ubuntu user name>
brctl addbr br0
ifconfig eth0 0.0.0.0 promisc
brctl addif br0 eth0
sudo ifconfig br0 <Host static IP> netmask 255.255.255.0 up
sudo route add default gw <Internet gateway IP> br0
brctl addif br0 tap1
ifconfig tap1 up[/FONT]

With this, I can connect my virtual machine to internet through the network. The real network of host machine also works fine.

Good luck
-RavinSP-

---

### Post by airbornespent on 2007-07-26
I've got it mostly working, but my windows taskbar is acting quirking, though it could be due to the age of the machine I am working on. When I have my ubuntu taskbar on the bottom, the windows bar sits on top of it, black with a gray border pulsing about once a second. If I move the ubuntu bar to the top or to the side the windows bar drops and is readable, but is still pulsing/flashing once a second. When I open a program via the start menu however, their windows display just fine.

Like I said though, it could be because this is a dual PIII 800 with a rage 128 and only 256 megs of RAM. I think the only reason XP runs is because I used [nlite]("http://www.nliteos.com/nlite.html") to remove just about everything I didnt need and the install footprint is about 820MB and memory usage just after boot is only around 50MB.

---

### Post by dirken on 2007-07-26
> **airbornespent said:**
> dirken:
Follow the steps below and go to VBox settings and change the network from NAT to attached to and put tap1 in the interface name box below. These settings worked fine for me. Also pay particular attention to the HOWTO where michael mentions to get the IP from inside the windows VM, use that to login with rdesktop.

Hey airbornespent, thx for helping me out here but it isn't quite working.
When making the changes you told me to do i rebooted the computer just to make sure everything should be ok, with this computer i still can connect to the internet but my VM won't get a valid ip. I'm getting this ip: 169.254.94.137

Using ifconfig in Ubuntu i'm getting this ouput (cleared what's not important!)
```
br0       Link encap:Ethernet  HWaddr 00:13:CE:2D:9C:48  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe2d:9c48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3889311 (3.7 MiB)  TX bytes:312804 (305.4 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:CE:2D:9C:48  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe2d:9c48/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:6182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3917551 (3.7 MiB)  TX bytes:320227 (312.7 KiB)
          Interrupt:18 Base address:0xa000 Memory:dfcfd000-dfcfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1633 (1.5 KiB)  TX bytes:1633 (1.5 KiB)

tap1      Link encap:Ethernet  HWaddr 32:30:F2:5A:C2:00  
          inet6 addr: fe80::3030:f2ff:fe5a:c200/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:32 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:22680 (22.1 KiB)  TX bytes:684 (684.0 b)
```

My rc.local file looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

tunctl -t tap1 -u dirk
brctl addbr br0
ifconfig eth1 0.0.0.0 promisc
brctl addif br0 eth1
sudo ifconfig br0 192.168.1.2 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 br0
brctl addif br0 tap1
ifconfig tap1 up

exit 0
```

Any more help plz!
Greetz...

---

### Post by T0MA on 2007-07-26
yes, it did this to me as well but if I run compiz it doesnt blink anymore

---

### Post by dirken on 2007-07-27
I almost got i working good. In fact when I was not reveiving any IP in my VM I set up a fixed IP in the Windows VM and now I can connect to it but the problem is that within Windows (my VM) I'm not having an internet connect wich would be very usefull to.

I'm also having another question, the bidirectional clipboard (or whatever it's called) is enalbed in within VirtualBox but when running my VM seamless it doesn't work. Is there something I should add to my connection command? And if I should what exactly do I have to add?

Thx,
Dirken

---

### Post by airbornespent on 2007-07-28
> **dirken said:**
> I almost got i working good. In fact when I was not reveiving any IP in my VM I set up a fixed IP in the Windows VM and now I can connect to it but the problem is that within Windows (my VM) I'm not having an internet connect wich would be very usefull to.

I'm also having another question, the bidirectional clipboard (or whatever it's called) is enalbed in within VirtualBox but when running my VM seamless it doesn't work. Is there something I should add to my connection command? And if I should what exactly do I have to add?

Thx,
Dirken

Ok, that is good that you can connect, it means your tap is working. Since you set a static IP you may need to set a DNS server as well, your router is supposed to act as a DNS gateway, but it may only do it for DHCP connected machines. Assuming the internet works fine in your host, add 207.172.3.8 as a DNS server in windows. You can add 207.172.3.9 as a secondary DNS. Let me know how that works.

As to the clipboard, I haven't even tried that yet. But I did read an earlier post mentioning that is "had not been implemented yet". You've tried copying and pasting both ways?

---

### Post by couzin2000 on 2007-08-05
Maybe I'm a newbie...  I'm just not getting this right, and somehow I haven't seen this adressed in the thread.

I've done most of the steps, I'm at the point where I've created my .iso image, mounted it, and now I'm hitting Start in Virtualbox. This is what I get:


[COLOR="DarkSlateBlue"][FONT="Trebuchet MS"]Failed to open '/dev/net/tun' for read/write access. Please check the permissions of that node. Either do 'chmod 0666 /dev/net/tun' or change the group of that node and get member of that group. Make sure that these changes are permanently in particular if you are using udev.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}[/FONT][/COLOR]

What am I missing here? I've actually CHMODded the TUN file, but to no avail. What gives with this machine?

**EDIT1**: ok, sorry -- did find the post on this... now facing different set of problems:

[COLOR="DarkSlateBlue"]Failed to initialize Host Interface Networking.
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
[/COLOR]

**EDIT2**: ok, you know what? never mind. I got it working. I don't know how the reboot got it to work, but after 3-4 reboots in a row, it works fine now -- including my wifi connexion. I guess I'm better at playing around in Linux than I thought!
Thanks guys!

---

### Post by Zyrshnikashnu on 2007-08-06
Try the NAT method for networking. It tends to be simpler.

---

### Post by Martindale on 2007-08-07
[Dugg!](http://digg.com/microsoft/HOWTO_Seamless_MS_Windows_in_Edgy_with_VirtualBox_and_Beryl)

---

### Post by sdowney717 on 2007-08-07
dont know if this guide was mentioned but it is also good.

[http://doc.gwos.org/index.php/VirtualBox#Introduction_.2F_FAQ](http://doc.gwos.org/index.php/VirtualBox#Introduction_.2F_FAQ)

It gave me my shared folder and  usb devices and copy and paste

What I would like to do is print to a network LAN HP4000 laserjet.
Tha means it is plugged into my local LAN using a network cable and has an IP number.
I can do this in regular XP and ubuntu just fine.

I can also goto the web admin page for the printer using firefox.
But I can not ping the printer, I assume because there is no network 'tap'??

All i have is the shared folders.

---

### Post by Apache777 on 2007-08-07
Man I love this HOWTO ... I've never thought that this is even possible ... it's the best solution for me, no more wine or whatever.

THANKS A LOT BUDDY. :guitar:

---

### Post by ashmew2 on 2007-08-19
Thanks for the great HowTo man , really thanks,  Ive been banging my head on the table for getting yahoo messenger (the windows one) to work under cedega , wine , etc.  But its finally working , 
But i still need some help.
First , i need to know how to get audio input to work under xp (the guest os). Ive got audio output working by selecting ALSA in the Vbox settings.Also , im not using the Rdesktop thing. 
But im experiencing major lag. Is there anyway to get rid of it ?
Thanks

---

### Post by darkmaster on 2007-08-22
> **sdowney717 said:**
> dont know if this guide was mentioned but it is also good.

[http://doc.gwos.org/index.php/VirtualBox#Introduction_.2F_FAQ](http://doc.gwos.org/index.php/VirtualBox#Introduction_.2F_FAQ)

It gave me my shared folder and  usb devices and copy and paste

What I would like to do is print to a network LAN HP4000 laserjet.
Tha means it is plugged into my local LAN using a network cable and has an IP number.
I can do this in regular XP and ubuntu just fine.

I can also goto the web admin page for the printer using firefox.
But I can not ping the printer, I assume because there is no network 'tap'??

All i have is the shared folders.

the link doesn't work !!! Can you correct it?

---

### Post by Dark Star on 2007-08-22
:o Awesome work there. Flawless and nice write up :)

---

### Post by dirken on 2007-08-23
> **airbornespent said:**
> Ok, that is good that you can connect, it means your tap is working. Since you set a static IP you may need to set a DNS server as well, your router is supposed to act as a DNS gateway, but it may only do it for DHCP connected machines. Assuming the internet works fine in your host, add 207.172.3.8 as a DNS server in windows. You can add 207.172.3.9 as a secondary DNS. Let me know how that works.

As to the clipboard, I haven't even tried that yet. But I did read an earlier post mentioning that is "had not been implemented yet". You've tried copying and pasting both ways?

1) Internet is now working on both the host and the client
2) Copying in both directions works just fine if I run XP in virtualbox but cannot get it working when using XP seamless

---

### Post by EXCiD3 on 2007-08-23
Is there anything I should know if I install this on a laptop. Are there workarounds for disabling the network manager? I would prefer to use it over anther application. PM me, if this has already been posted in the thread. I haven't had a chance to read through it yet...

---

### Post by dirken on 2007-08-23
> **EXCiD3 said:**
> Is there anything I should know if I install this on a laptop. Are there workarounds for disabling the network manager? I would prefer to use it over anther application. PM me, if this has already been posted in the thread. I haven't had a chance to read through it yet...

If you read my previous posts it is explaned somewhere in there.

Greetz..

---

### Post by EXCiD3 on 2007-08-23
lol, thanks, i figured as much...time to start reading...

---

### Post by holmrun on 2007-08-25
Looking for a little help here... I had this installed and working fine for the last 3 or 4 months however something is not working correctly anymore. I can go into the virtual windows just fine via the virtual box console and everything works. My user auto logs in and everything works fine - network/internet etc. However, when I autostart or try to manually run the VBoxManage startvm "VWindows" -type vrdp  command the terminal window flashes and that is it. Nothing else happens. If I go into the virtual box console I can see that the virtual machine is now in an aborted state. I can then start the machine from the console just fine again. Any ideas? The log in virtual box is less than helpful.

edit - looks like changing the scripts to run as an application instead of app in terminal windows might have done the trick.

---

### Post by AusIV4 on 2007-08-25
I just set this up slightly modified to use VMWare (It's not headless, but I keep it minimized and tucked away). I didn't have to do anything special for networking. I'm using NetworkManager, and I just did an ipconfig in windows to get the IP, then I pointed the rdp client to that IP.

I played with this once before, but I had not seen anything that allowed you to have a Windows taskbar, so you had to start with a windows command prompt and find the executables for any programs you wanted to run. This is infinitely more usable.

Only complaint is that sound is lagged about 3 seconds. Fine for music and most other applications I need windows for, but not good for video.

I didn't use Windows in a VM much before, and I won't use it much more now, but this will make it a more pleasant experience for most applications.

---

### Post by RoflCake on 2007-08-27
So...has anyone got this to work on wireless yet? I don't know how to correctly configure Ubuntu to allow VirtualBox to recoginize a connection.

---

### Post by MNICY on 2007-08-28
Ok, so i got to the point where you type
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <IP recorded from Windows>:3389 -u "<Your Windows Username>" -p <Your Windows Password>
``` into the terminal (replacing the IP, username and password of course ;))
What happens, is it just sits there for a minute, and nothing happens. Then, after a little while, it says "Connection timed out"
Im using Kubuntu Feisty

any idea why its not working?

EDIT:
i just tried it again, after rebooting my system...
Now it instantly says "EROR: connect: Connection refused"

---

### Post by cresny on 2007-08-28
does anyone else have non-working navigation keys in windows apps? My arrow, Home, End and Delete don't work. My keyboard is standard laptop style - no number pad. I googled around rdesktop issues, no luck. All works fine direct in VirtualBox vm session.

Any ideas? :confused:

---

### Post by Matakoo on 2007-08-29
> **mikeytag said:**
> 
Only downside, is that the first time you run it you will have to Log Off once before seamlessness will be in effect. Maybe someone can whip up a VB app that will log out the Windows user only on first login so this is done automatically. :smile:


Actually, there is quite an easy way to do that. It works on my setup, but let me first say that I don't use the method of integrating the windows startbar. I prefer to create launchers for KDE/Gnome to run the specific windows program I need instead. I'm not sure if this approach would work using the integrated approach. With that said, what you do is (as extras to what your how-to do that is).

On the windows side, go to [http://www.steve.org.uk/Software/logoff/](http://www.steve.org.uk/Software/logoff/)
and download the zipfile. Extract the archive and copy logoff.exe into c:\windows

Start notepad and create a script like this:

```
@echo off
logoff /q
```save it as logoff.cmd, also saved in c:\windows

Create a shortcut to this cmd-file in the start-menu Autostart folder. Logout.
Everytime windows start up, your preferred user is logged in and automatically logged out immediately. And, as it happens, immediately when VirtualBox is started headlessly.

Now, on the linux side. Try this at a shell-prompt (after a reboot to make sure it all works after a fresh start of your linux host):

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\system32\sol.exe" 192.168.0.104:3389 -u "username" -p password
```Of course, substituting the IP-adress, username, and password for yours. In this case, solitaire should start seamlessly. And windows does not log out here, because it is explorer.exe that launches the logoff.cmd file, and explorer.exe is not your loginshell when you run stuff seamlessly like this.

All that remains to do now is to create a menu-entries in Gnome or KDE using varieties of the above commandline to launch the window apps you need.

Oh, and if you do need access to the complete desktop (for installing new software for instance) just do

```
rdesktop 192.168.0.110
```Substitute the IP for the one you gave to your tap0 interface. Now the usual windows loginscreen shows up. Type in your password and hit enter. Hold down shift while windows logs you in, and the autostart entries are bypassed.

Hope this is of some help!

---

### Post by wislon on 2007-08-30
MNICY : this may be a dumb question, but have you made sure your windows firewall is turned off, or set to allow incoming remote desktop connections? Just a thought...

---

### Post by MNICY on 2007-08-31
> **wislon said:**
> MNICY : this may be a dumb question, but have you made sure your windows firewall is turned off, or set to allow incoming remote desktop connections? Just a thought...Thanks for the reply :)
Yes, i thought of that, and i turned off windows firewall. (i hate it anyway :lolflag:)

Anyway, it works now. Its not because of windows firewall (still wasnt working after i checked that). It randomly started working, for no reason i can see....

I can use rdesktop to connect to virtualbox running windows xp home!
The problem now is, i cant seem to get it to run seamlessly. 
It is there, but it is in its own window. 
I tried loging off like the guide suggests, but it does not work.
Anyone know any reason why?


EDIT:
also, does anyone know how to do this:
> # Now we are going to setup Ubuntu to start our Windows installation automatically for us upon login.
# Go to System->Preferences->Sessions and click the Startup Programs tab
# Click the Add button and type the command above into the text field and click OK
EDIT2:
More info:
If i run it with Compiz-Fusion, it goes full screen instead of windowed.... but it doesnt seem to be quite seamless (cant put my Windows windows (lol) into KUbuntu workspace)
 in Kubuntu?

---

### Post by MNICY on 2007-08-31
Anyone?

---

### Post by MNICY on 2007-09-01
I tried it with both XP Home and Pro..
both gave same results :confused:

---

### Post by mephistophilis on 2007-09-01
VirtualBox 1.5 support seamless Windows now.

---

### Post by MNICY on 2007-09-01
> **mephistophilis said:**
> VirtualBox 1.5 support seamless Windows now.

How can i download VIrtualbox 1.5?
i went to virtualbox.org, and they only have 1.4

---

### Post by MNICY on 2007-09-01
Its very annoying. there are several refrences to "virtualbox 1.5.0" on the internet, but all of them point to [http://www.virtualbox.org/download/1.5.0/](http://www.virtualbox.org/download/1.5.0/)
which gives me a 

> Forbidden

You don't have permission to access /download/1.5.0/ on this server.

---

### Post by gavinjb on 2007-09-01
I have just tried to set this up, I have got as far as booting into Windows in VirtualBox, but Windows takes ages to pick up the IP/subnet mask but has no default gateway, so I cant connect to the internet through Windows.

if it helps my config of rc.local is as follows

```

tunctl -t tap0 -u gavin
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth1 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.1.97 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.1.2 dev tap0
 arp -Ds 192.168.1.2 eth1 pub

```

```

gavin@gblaptop:~$ ifconfig tap0
tap0      Link encap:Ethernet  HWaddr 4A:F5:99:36:11:00  
          inet addr:192.168.1.97  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::48f5:99ff:fe36:1100/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:25 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:6714 (6.5 KiB)  TX bytes:264 (264.0 b)

```

Can anyone help.

Thanks,

Gavin,

---

### Post by MNICY on 2007-09-01
> **gavinjb said:**
> I have just tried to set this up, I have got as far as booting into Windows in VirtualBox, but Windows takes ages to pick up the IP/subnet mask but has no default gateway, so I cant connect to the internet through Windows.

if it helps my config of rc.local is as follows

```

tunctl -t tap0 -u gavin
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth1 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.1.97 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.1.2 dev tap0
 arp -Ds 192.168.1.2 eth1 pub

```

```

gavin@gblaptop:~$ ifconfig tap0
tap0      Link encap:Ethernet  HWaddr 4A:F5:99:36:11:00  
          inet addr:192.168.1.97  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::48f5:99ff:fe36:1100/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:25 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:6714 (6.5 KiB)  TX bytes:264 (264.0 b)

```

Can anyone help.

Thanks,

Gavin,Did you close the network manager?

---

### Post by gavinjb on 2007-09-01
yes, I have closed the network manager and re-booted the machine

---

### Post by MNICY on 2007-09-01
Hmm.... well i dont know then :(
When it did that to me, i realized i actually had to close the netowork manager ;) and then that error stoped
maybe you need to turn windows firewall off or somthing...

Anwyway, i finally got it to work! :guitar:
What i learned:
1. Follow the instructions carfully and exactly. One mistake screws you up. Double check. Tripple check.
2. Use Windows XP Pro. Home DOES NOT WORK. (i hate pro so much. i really wish home had worked)
3. kill Microsoft for giving me a screwed up ip address when i checked it. it gives me one like 15.10.0.1, and that *kind* of works, but then i go back and check the next day and it changed to 192.160.0.107... and that works perfectly.
4. Make shure you put the seamlessrdp into C:\seamlessrdp ;)

---

### Post by ashz on 2007-09-01
If you want the latest Virtualbox.

Then go into synaptic and add this to your repos.

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) feisty non-free

You also need to add this key to authenticate it.

[http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc)

You can see al this on their download page.

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

laters
ash

---

### Post by Matakoo on 2007-09-01
> **MNICY said:**
> 
3. kill Microsoft for giving me a screwed up ip address when i checked it. it gives me one like 15.10.0.1, and that *kind* of works, but then i go back and check the next day and it changed to 192.160.0.107... and that works perfectly.


That sounds like a brain-damaged or mis-configured dhcp-server to me. According to the command-lines you posted, you really should get an address in the 192.168.0.* net and not in the 15.*.*.*.* net. Furthermore, if this is in a private LAN the addresses should be in the 10.*.*.* (not 15) and the 192.168.*.* (not 192.160), simplified a bit. And if Windows can't find a dhcp-server, you would (if my memory serves) an address in the 172.16.*.* net (the third privately reserved net).

If you have an internal dchp-server (like a broadband router) I would check the configuration of that one first.

---

### Post by gavinjb on 2007-09-01
> 
Hmm.... well i dont know then
When it did that to me, i realized i actually had to close the netowork manager and then that error stoped
maybe you need to turn windows firewall off or somthing...


I take it that network manager is disbaled it isnt showing up at the top of the screen adn I have added exit to /etc/default/NetworkManager & NetworkManagerDispatcher

I have just tried it again and I am now getting an gateway address (takes awhile to come through though) only problem is it is the same as the IP address, and until I get this setup I cant download and install the seamlessrdp into Windows.


IP Address : 169.254.24.57 
Subnet : 255.255.0.0
Gateway : 169.254.24.57

---

### Post by MNICY on 2007-09-01
> That sounds like a brain-damaged or mis-configured dhcp-server to me. According to the command-lines you posted, you really should get an address in the 192.168.0.* net and not in the 15.*.*.*.* net. Furthermore, if this is in a private LAN the addresses should be in the 10.*.*.* (not 15) and the 192.168.*.* (not 192.160), simplified a bit. And if Windows can't find a dhcp-server, you would (if my memory serves) an address in the 172.16.*.* net (the third privately reserved net).
I figured somthing like that.
And i typed thoes numbers in from memory, so they are probaly wrong ;)

edit:
It is working great - better then i thought it would - there is just one thing:
I thought i was supposed to get effects being applied on "Windows" windows, as well as Ubuntu windows.
Im running Compiz-Fusion, and it works with all my Ubuntu windows, but does not seem to effect the "Windows" windows...

---

### Post by gavinjb on 2007-09-01
Hi,

I have just installed v1.0.5 plus Gust Addons 1.0.5 and seamless as mentioned above is integrated into the system, at the moment it is a bit buggy, but looks like it has a lot of promise and it much easier to setup (just press Host + L)

V 1.0.5 only seams to be available if you add Virtual Box source and download through synaptic, the main advantage I can see is you don't have to disable Network Manager and you aren't tied to one user.

Thanks,



Gavin,

---

### Post by gundumfx on 2007-09-01
thanks for the post this was useful

---

### Post by stinger30au on 2007-09-01
i have just installed virutalbox my self to tinker with XP Pro and try a few things out.
the esiest way to install virtual box is from the repo's from automatix 2.

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

when you go to this page scroll down a little and you will see a title that says " Installing Automatix2 with Apt" and follw the directions for what ubuntu your using be it fiesty, edgy or dapper.

once automatix is installed start it up and in there under virtual machine you will find virtualbox.just select it and let it install.

i then put my xp pro dics in the drive and told virtualbox to mount the cd in the drive and it booted, and installed no dramas. piece of cake.

---

### Post by Martje_001 on 2007-09-02
Hi.
I can't fill in tap0 :(. Can somebody help me? (see screenshot)

---

### Post by gavinjb on 2007-09-02
> 
I can't fill in tap0 . Can somebody help me? (see screenshot)


Thats because you have NAT selected and not Host Interface

---

### Post by MNICY on 2007-09-02
I really wish 1.5.0 of virtualbox was available for download :(
Would make everything so much easier. The 1.5.0 manual says that to get seamless all you need to do is install your OS, and press [host]+L
Then it goes into seamless....
so much easier then what we have now.

---

### Post by gavinjb on 2007-09-02
> 
I really wish 1.5.0 of virtualbox was available for download
Would make everything so much easier. The 1.5.0 manual says that to get seamless all you need to do is install your OS, and press [host]+L
Then it goes into seamless....
so much easier then what we have now.


if you add the source to your sources.list you can download it easily (just goto [www.virtualbox.org](www.virtualbox.org) download page for details), only problem I have found is to use in seamless mode, you need to have Compiz disable or if not you have no end of issues.

You also need to make sure you install the 1.0.5 Guest Add On's before you can you seamless mode (this has me for a while)

---

### Post by MNICY on 2007-09-02
Ah. They finaly decided to put it back up. 
I swear they put it up (peopel were talking about having it), then took it down when i tried yesterday...
downloading right now.
Hmm... to bad about Compiz... I might have to stick with what we are doing here :(

---

### Post by MNICY on 2007-09-12
Got a workaround for this :D
Download somthing that creates a floating window, such as Google Desktop (and set it to "Floating Deskbar")
fixes the problem!

---

### Post by lime4x4 on 2007-09-13
i'm running feisty got virtualbox installed but i can't start it when i have the network set to host interface. This is the error i'm getting

Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

if i set the network to NAT it works fine other then it gets a weird ip address that ain't even in my network.

---

### Post by MNICY on 2007-09-14
> **lime4x4 said:**
> i'm running feisty got virtualbox installed but i can't start it when i have the network set to host interface. This is the error i'm getting

Unknown error creating VM (VERR_HOSTIF_INIT_FAILED).
VBox status code: -3100 (VERR_HOSTIF_INIT_FAILED).

if i set the network to NAT it works fine other then it gets a weird ip address that ain't even in my network.

Im not shure what your problem is. But, you may want to try the "seamless integration" that comes with the latest version of virtualbox. it works amazingly if you dont have compiz/beryl/compiz-fusion installed, but if you do, there are a few work arounds to get it to work (read the last couple of posts)
and go here: [http://forums.virtualbox.org/viewtopic.php?t=1550](http://forums.virtualbox.org/viewtopic.php?t=1550)

---

### Post by GSF1200S on 2007-09-16
I went through all the hassel, when all I had to do is use the seamless feature with vbox 1.5.0. Oh well.

Anyone know if its possible to put icons on the (Linux) desktop to open windows (guest) applications? I would imagine you could make a shortcut that would tell vbox to input something in windows... I dont know- any ideas?

I still have everything setup as it is in this howto. For some reason, I got a syntax error with the rdesktop command, so I dont whats up with that.

Host+L works nice now on 1.5.0

---

### Post by MNICY on 2007-09-16
By using the rdesktop (not the nice seamless that comes with virtualbox, but the weird thing described in this thread) you can access single programs. You could make a shortcut on your desktop which runs a command which opens up a program, but i think that would be to complicated.
I would just put icons into the "quick launch" thing, beside the Start button in your windows taskbar.

---

### Post by GSF1200S on 2007-09-16
> **Matakoo said:**
> Actually, there is quite an easy way to do that. It works on my setup, but let me first say that I don't use the method of integrating the windows startbar. I prefer to create launchers for KDE/Gnome to run the specific windows program I need instead. I'm not sure if this approach would work using the integrated approach. With that said, what you do is (as extras to what your how-to do that is).

On the windows side, go to [http://www.steve.org.uk/Software/logoff/](http://www.steve.org.uk/Software/logoff/)
and download the zipfile. Extract the archive and copy logoff.exe into c:\windows

Start notepad and create a script like this:

```
@echo off
logoff /q
```save it as logoff.cmd, also saved in c:\windows

Create a shortcut to this cmd-file in the start-menu Autostart folder. Logout.
Everytime windows start up, your preferred user is logged in and automatically logged out immediately. And, as it happens, immediately when VirtualBox is started headlessly.

Now, on the linux side. Try this at a shell-prompt (after a reboot to make sure it all works after a fresh start of your linux host):

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\system32\sol.exe" 192.168.0.104:3389 -u "username" -p password
```Of course, substituting the IP-adress, username, and password for yours. In this case, solitaire should start seamlessly. And windows does not log out here, because it is explorer.exe that launches the logoff.cmd file, and explorer.exe is not your loginshell when you run stuff seamlessly like this.

All that remains to do now is to create a menu-entries in Gnome or KDE using varieties of the above commandline to launch the window apps you need.

Oh, and if you do need access to the complete desktop (for installing new software for instance) just do

```
rdesktop 192.168.0.110
```Substitute the IP for the one you gave to your tap0 interface. Now the usual windows loginscreen shows up. Type in your password and hit enter. Hold down shift while windows logs you in, and the autostart entries are bypassed.

Hope this is of some help!

Sounds great.. the VM automatically logs off, but I have an issue. When I issue the rdesktop command, windows pops up in a window (a linux controlled window) at the login screen. Even if I manually login at this point, it still wont work seamless.

For example, using:
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\system32\sol.exe" 192.168.0.17:3389 -u "Penguin" -p gsfs
Brings up a window (controlled by Linux) of my windows desktop. Period. No solitaire even opening or anything, let alone it running by itself in its own window. Im so close.. I must be missing something really simple.

---

### Post by GSF1200S on 2007-09-16
After mind numbing research, I found the problem, but I dont know how to fix it.

In the /etc/rc.local this directory is specified:

/proc/sys/net/ipv4/conf/tap0/proxy_arp'

but it doesnt exist! The directory's for lo, default, ath0 exist, but not tap0. This is why im getting a:

ERROR: No route to host  

when issuing the rdesktop command.

Kate (i use kde, not that it matters here) shows that directory in red, which im assuming shows that the directory doesnt exist. I cant create anything new, even if the file manager is run as root. Any ideas on how to fix this?

**EDIT** I did a reboot just for good measure, and I noticed something right before the display manager booted up.. 

/etc/rc.local  :13 syntax error unexpected newline (something like that.. i had to kill X to read it)

So, apparantly rc.local isnt being run because of an error, which of course causes it to exit.. I copied it exactly as listed in this howto, and changed all that was needed. I should not that Kate shows the very first line of the text added to be line 13, which is the number thats in the error. Heres my entire rc.local- anyone see any "syntax error?" (ip addresses arbitrary)

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
tunctl -t tap0 -u <poeticrpm>
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig ath0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 ath0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.0.14 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.0.13 dev tap0
 arp -Ds 192.168.0.13 ath0 pub
exit 0

---

### Post by MKdon on 2007-09-28
Hi,
Here is my rc.local and it works if you are getting the error message mentioned 

#!/bin/sh -e
# # rc.local # # This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
# # In order to enable or disable this script just change the execution # bits. 
# # By default this script does nothing. 
# For Network Bridging/TAP to enable Virtual Box 
# Set permissions of tun device
 chown root:vboxusers /dev/net/tun 

#Add a bridge, add ra0
#!/bin/sh
# set PATH for the case we are called via sudo or su root

PATH=/sbin:/usr/sbin:/bin:/usr/bin

# create a tap
sudo chmod 0666 /dev/net/tun
tunctl -t tap0 -u (user_name)
ip link set up dev tap0

# create the bridge
brctl addbr br0
brctl addif br0 tap0
Hi this is my rc.local and it works

# set the IP address and routing
ip link set up dev br0
ip addr add 10.1.1.1/24 dev br0
ip route add 10.1.1.0/24 dev br0 

#set up If ra0
ifconfig ra0 0.0.0.0 promisc 
brctl addif br0 ra0 
dhclient br0 

# Create tap0
#tunctl -t tap0 -u (user_name) 
#Be sure to change user_name to your user name 

# Enable tap0 
#brctl addif br0 tap0 
ifconfig tap0 up 

MAKE SURE YOU CHANGE user_name to your username and set rc.local to execute.

in a terminal $sudo chmod +x /etc/rc.local

Good luck

---

### Post by MKdon on 2007-09-28
Of course you have to change the i/f ra0 to your i/f name.

---

### Post by mjwood0 on 2007-10-01
This looks perfect for me as I really need Windows for work.

If I were to install XP in a virtual machine such as this, how would the XP license work?

Here's the deal --

I have an unused XP license.  I don't want to activate it until I upgrade my hardware as it's tied to the MB and that's something I want to upgrade.  So I was going to wait.  But if I can install it in a virtual machine, when I upgrade hardware, does the XP license checker send up a red flag?

I'm really not trying to get around anything here.  I just don't want to register too soon.

Thanks for any ideas!

---

### Post by mr_byte on 2007-10-02
> This looks perfect for me as I really need Windows for work.

If I were to install XP in a virtual machine such as this, how would the XP license work?

Here's the deal --

I have an unused XP license. I don't want to activate it until I upgrade my hardware as it's tied to the MB and that's something I want to upgrade. So I was going to wait. But if I can install it in a virtual machine, when I upgrade hardware, does the XP license checker send up a red flag?

I'm really not trying to get around anything here. I just don't want to register too soon.

Thanks for any ideas!


I'm not really sure how this affects your license.  Personally, even though I *HAVE* a license for XP Home and Pro, I use a cracked version.  

M$ may differ, but I just use my moral code of "if it's only running one place at a time, then I'm legal" and my VM and my "real" XP never run at the same time.

Also, if I'm following you, you're worried if an upgrade of the physical Mobo will cause the VM'd XP to sense a hardware change. My gut here says no. The "hardware" in the VM should never change, as it's still the same software running it.  It just (hopefully) runs faster on new physical hardware.

This sounds logical, but it is still a guess, YMMV.

Jeff

---

### Post by Frak on 2007-10-02
> **mr_byte said:**
> I'm not really sure how this affects your license.  Personally, even though I *HAVE* a license for XP Home and Pro, I use a cracked version.  

M$ may differ, but I just use my moral code of "if it's only running one place at a time, then I'm legal" and my VM and my "real" XP never run at the same time.

Also, if I'm following you, you're worried if an upgrade of the physical Mobo will cause the VM'd XP to sense a hardware change. My gut here says no. The "hardware" in the VM should never change, as it's still the same software running it.  It just (hopefully) runs faster on new physical hardware.

This sounds logical, but it is still a guess, YMMV.

Jeff
I'll clarify for everybody

Virtualization is running an OS on your hardware, but translating the calls into your own native OS's as that one programs. ex. Windows calls on explorer.exe to run, it shows in Ubuntu as VirtualBox.bin running an extra process. It also uses the hardware of your computer directly through no middleman.

Emulation is a completely new hardware base, such as QEMU. It also somwhat translates the OS calls into your own OS's calls. But it mostly it emulates the hardware and runs it as its own process running in its own. All the hardware calls must be translated in the processor to run on the native hardware.

---

### Post by mr_byte on 2007-10-03
Now we're more confused :-)

But it does indeed sound like an upgrade of the actual hardware in the host machine will be completely unnoticed by the virtual machine.

I'd be able to test it, except the virtual setup I had on my old laptop didn't get backed up, so I cannot just plonk in the hardfile and run it.

---

### Post by AndyCooll on 2007-10-09
> **mr_byte said:**
> Now we're more confused :-)

But it does indeed sound like an upgrade of the actual hardware in the host machine will be completely unnoticed by the virtual machine.

I'd be able to test it, except the virtual setup I had on my old laptop didn't get backed up, so I cannot just plonk in the hardfile and run it.

In effect he's saying that if you are using "virtualisation" then you are using the actual graphics card that's in your box to process graphics whereas if you are using "emulation" then the emulating software uses a fake "emulated" graphics card with code created by the emulating software. In such cases you could have the latest most powerful graphics card available in your box but the app running under the emulation software would still only see the bog standard fake emulated card.

:cool:

---

### Post by mr_byte on 2007-10-09
Well, in my case using VirtualBox, the only piece of hardware that appears to not be emulated is half of my Turion X2 CPU.  All the other hardware is either VBox <something> or some other stuff I **Know** isn't in my hardware (Intel bits on an AMD system?????)  So I guess it's emulating all the support hardware, etc, but the CPU is not emulated, hence the speed I (usually) see from VBox

On another note, I cannot seem to get seamless working again. :( using VBox 1.5 in Seamless mode is less than nice, as all the windows look like XP, not Ubuntu.

When I last had it running, I was on Kubuntu Feisty, no beryl, compiz, compiz fusion, no XGL, or anything fancy.  

And while CF looks nice, I think I'm gonna have to dump it because my should-be-flying-fast lappy is prone to functional-dysfunction ala Vista Home Ultimate (which I trashed in 5 minutes - came with this new laptop.)

However, I did have my network running fine using the VBoxManage commands.  I have (had) wireless that MUST have network manager.

But now, even after checking the registry entries for NoDesktop, logging out automagically and manually, etc. I don't get a seamless desktop.  I get a window, unless I use the built-in seamless mode in VB1.5, which has it's own problems.  This problem was also in the repo version of VBox (1.4?) which is why I put the non-repo version in.

Any ideas?

---

### Post by magiceraser06 on 2007-10-14
Hey guys. Got seamless working just fine using the option with the new virtualbox.  i don't really care about using the rdesktop. but my question is:

when seamless is enabled, howcome the windows desktop is still showed? the ubuntu desktop is only visible when a XP application or window is open? then, when I close it, you can see the shadow effects of the windows on the screen until i open an other window.

any ideas?

---

### Post by Haama on 2007-10-15
Hi!

This is really cool, I only use windows for gaming though. And this really doesn't fit my purpose..?
Are there any programs that support 3D acceleration? In windows I was able to enable 3D on vmware in a windows xp or 2003 machine by adding mks.enable3d = TRUE to the configuration file. Also, would there be a performance boost if I ran the virtual machine full-screened on one desktop (not seamless)?

---

### Post by TheOtherLinuxFreak on 2007-10-17
Will this guide work with Gutsy? When I reformat, I also want to do this.

---

### Post by ShiftyPowers on 2007-10-20
I can confirm that this works in Gutsy.  Just tried it and it works seamlessly.  Is there a way to enable 32bit color thought?

---

### Post by Zenchess on 2007-10-21
This guide is not necessary anymore, you can just install guest additions in virtual box (its a menu option),  then choose 'seamless mode'.  I've been using it and it works great.

---

### Post by Islington on 2007-10-21
Hey Guys, I followed this all the way though to step 3 were it tells you to start windows.

I keep getting this error message:

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

can someone please help me?

---

### Post by pompeyjohn on 2007-10-22
> **Zenchess said:**
> This guide is not necessary anymore, you can just install guest additions in virtual box (its a menu option),  then choose 'seamless mode'.  I've been using it and it works great.

Whoa there tonto, not so hasty.

You'll still want to do the registry hacks to hide the desktop and increase the color depth.

---

### Post by Frak on 2007-10-22
> **Islington said:**
> Hey Guys, I followed this all the way though to step 3 were it tells you to start windows.

I keep getting this error message:

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

can someone please help me?
run
```
sudo gpasswd -a **username** vboxusers
```

replace **username** with your actual username.

---

### Post by mulder_edu on 2007-10-24
I'm trying this seamless environment between Gutsy and Windows 2k Pro.  Everything seems to work to a point, but Windows 2k Pro doesn't come with Remote Desktop.  I recall there might be a way to make it work.  Any ideas?

Edit:
Ah, never mind.  Tried the Seamless mode.  That did the trick.  I'll go ahead and pull the registry hacks.  Any way to make the windows start menu show up on all of my ubuntu desktops?

Edit:
Ah, figured that out too.  Just right click on the app and have it show Always on Visible Desktop.

Anyone know how to have my Windows desktop boot automatically when I log into Ubuntu?

---

### Post by chickan on 2007-10-24
> **magiceraser06 said:**
> Hey guys. Got seamless working just fine using the option with the new virtualbox.  i don't really care about using the rdesktop. but my question is:

when seamless is enabled, howcome the windows desktop is still showed? the ubuntu desktop is only visible when a XP application or window is open? then, when I close it, you can see the shadow effects of the windows on the screen until i open an other window.

any ideas?

I had the same issue, so I tried turning off the "NoDesktop" registry change (changed it to 0), and that solved the problem, no more ghosting of windows where they look like they are still there, but aren't.  Got it working with Fiesty + Beryl + i945 drivers (acer laptop).

One issue I'm running into, when I switch to another desktop, I get nothing but the blank background until I switch back to my primary desktop.

The Windows part can't get online either, I'll have to play with that some more.

EDIT: After playing around some more, turns out turning NoDesktop off doesn't help either.  Anyone else have ideas?

---

### Post by chickan on 2007-10-24
> **mulder_edu said:**
> Anyone know how to have my Windows desktop boot automatically when I log into Ubuntu?

System - Preferences - Sessions

VBoxManage startvm WinXP

Change WinXP to the name of yours.  Small modification to what was done in the original post.

---

### Post by mysticmatrix on 2007-10-24
> **mr_byte said:**
> Well, in my case using VirtualBox, the only piece of hardware that appears to not be emulated is half of my Turion X2 CPU.  All the other hardware is either VBox <something> or some other stuff I **Know** isn't in my hardware (Intel bits on an AMD system?????)  So I guess it's emulating all the support hardware, etc, but the CPU is not emulated, hence the speed I (usually) see from VBox

Quite right. Only CPU industry(Intel/ATI) support Virtualisation, which allows virtual machines to use CPU directly. Guess GPU's might follow soon :)

---

### Post by WiseOdd on 2007-10-24
Hey guys. First of all, THANK YOU ALL for this great post. Running xp simultaneously with linx is SOO great. it has solved many problems for me :)

BUT this made me wo )nder: When running xp in virtualbox, you set it up to do so via remote connection (i havent done this yet, i kinda like the showoff in just switching between desktops :) ) Is it possible to have a complete standalone Xp install, and then use virtualbox to connect via remote desktop, and have it run like it does when using the howto in this post?

The reason for this is two things. First i wont be able to use wired connections for the install, because ill mainly be using xp at the university. Second, since I have to use the space for my virtual install, this enables me to work, but NOT game, because I am not really able to play games on the virtual box. Of course ill mainly use it for working in PS and Premiere, but gaming on it would be nice too :)

Again Thx to yo all for you contributing to this thread, being able to work in win-only progs, while enjoying Ubuntu takes away a lot of grievances!!!!
Also switching between win and ubuntu are really going to make those annoying "know it all" students at the university gawk at my sweet setup :)

Regards to all, power to the Tux!

edit: lol just thought: of course i wont be able to connect via remote connection... the xp system wont be running when booting linux... doh. But still: if theres a way to configure the virtual box to use a standalone xp install, so i dont have to have both a virtual isntall and a regular install, that would be soo sweet... any1 got any ideas?

---

### Post by Jiipbe on 2007-10-28
Hi

First of all thank you for this great post. And excuse me for being a total newbie to Ubuntu and Linux, but I'm enjoying it so far. 

I'm having a little bit of a problem though since I would like to make it work wireless. I'm now running it under Gutsy with the guest addition and using NAT. But I need to be able to print on a XP machine on my network and then the Nat configuration unfortunately comes up short. 

Any ideas on how to achieve this bridge ?

Am also having a problem of ghost windows and black background. 

Any ideas?

Thank you.

---

### Post by hondoslack on 2007-10-29
props dude, works great on my Archlinux install with a virutal XP. now if only I can figure out wtf is going on with my mouse cursor in the XP windows, I'll be set!

BTW, does everyone find that XP boots, shuts down, and runs programs WAY faster virtualized than when running off real hardware? I am astounded at my performance levels, even when I have several applications open in Vbox, and in linux. I couldn't be happier :-).

---

### Post by hondoslack on 2007-10-29
> **Jiipbe said:**
> Hi

First of all thank you for this great post. And excuse me for being a total newbie to Ubuntu and Linux, but I'm enjoying it so far. 

I'm having a little bit of a problem though since I would like to make it work wireless. I'm now running it under Gutsy with the guest addition and using NAT. But I need to be able to print on a XP machine on my network and then the Nat configuration unfortunately comes up short. 

Any ideas on how to achieve this bridge ?

Am also having a problem of ghost windows and black background. 

Any ideas?

Thank you.

Sorry dude, VirtualBox and wireless don't play nice in that regard. Try seeing if you can get it working with port forwarding. Search this thread, some dude describes how to do NAT and port forwarding. Cheers.

---

### Post by hondoslack on 2007-10-29
> **WiseOdd said:**
> edit: lol just thought: of course i wont be able to connect via remote connection... the xp system wont be running when booting linux... doh. But still: if theres a way to configure the virtual box to use a standalone xp install, so i dont have to have both a virtual isntall and a regular install, that would be soo sweet... any1 got any ideas?

You can go this route with VMWare, I don't believe its possible in VBox. I had this setup for this very reason with VMWare, but ended up ditching it, 'cause I have no time to game anymore :cry:. Do some googleing regarding VMWare and raw disks. I never found any single magic post in any forum that helped me, I had to piece together everything myself based on several posts, and some trial and error (and stupidly didn't document my success). Just a note, I never got it working on my inspiron 9400 laptop, although hypothetically it should be possible.

---

### Post by Revfisk on 2007-10-29
Hi,

I'm new to all this.

I tried downloading the Feisty version of virtual box and the installation stalled.  Now I can't get into any installation, from th 7.10 update to Synaptic Package Manager.  I'm being given an error message that says another update manager is working AND that I need to manually run    dpkg --configure -a, which is a "superuser" something or other.

Help!  I just want to like Ubuntu!  :)

---

### Post by Revfisk on 2007-10-29
OK...so now it's a new problem.  Now it's telling me that "the package virtualbox needs to be reinstalled, but I can't find the archive for it." 

That's it.  Updates etc won't work.  Help? :)

---

### Post by Scotty562 on 2007-10-29
This is great and everything, but when I use the rdesktop with explorer.exe my Ubuntu background gets removed and it is replaced with the windows background. In fact, the only ubuntu part of the desktop is my title bar across the top.  Can I make this just show the windows bar? I'm using vmware, but I don't think that matters that much.

Don't get me wrong, this seemless stuff is great. The g/f didn't even know I was running linux. I suppose that means it is indeed integrated well enough :).  Then again, as long as girls can get to their myspace they are pretty much content. Oh, and ares.

Also, it seems to dislike the avant window application with a deep passion. The windows title bar will move up and down and all kinds of other oddities. Although, without the it running my network icon still wiggles around on it's own. It's not a big deal or anything, but it is rather curious.

Anyone else experience these issues?

---

### Post by Fuzz on 2007-11-02
> **Revfisk said:**
> OK...so now it's a new problem.  Now it's telling me that "the package virtualbox needs to be reinstalled, but I can't find the archive for it." 

That's it.  Updates etc won't work.  Help? :)

Add this to /etc/apt/sources.list:
```
http://www.virtualbox.org/debian gutsy non-free
```
and then open a terminal and do this:
```
wget http://www.virtualbox.org/debian/innotek.asc
sudo apt-key add innotek.asc
sudo apt-get update
```
It should show up in the archive now.

---

### Post by Haama on 2007-11-04
[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

A nice guide on running your existing windows install with vmware.

---

### Post by ssc351 on 2007-11-05
Hi,

I've had this working great until the other day...I am not sure if I did anything or not but here is the error I am getting....I am running Gusty with an XP pro guest and Vbox 1.5.2.  I followed an early post in this thread to use port forwarding so Network Manager would still work...and like I said it was working great.  I've tried uninstalling and reinstalling Vbox but no luck...tried sending the port forwarding commands but no luck. I can get the VM started if I uncheck "cable connected" under the settings of the network=>NAT.  But I really need to use the internet on the XP guest.  Any help?


Unknown configuration in port forwarding.
VBox status code: -2805 (VERR_PDM_DRVINS_UNKNOWN_CFG_VALUES).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by starscalling on 2007-11-12
can something like this be done with qmeu?
i need good redraw rates - for video or so

---

### Post by pompeyjohn on 2007-11-13
> **starscalling said:**
> can something like this be done with qmeu?
i need good redraw rates - for video or so

*gets excited* so QEMU has a faster redraw rate? The only reason I dual boot now is because I have a flight sim (phoenix) which heavily uses directx and the .net framework. If I could get this running on ubuntu I would be skipping with joy.

somebody please tell me QEMU can do this, and that it can rock directx !

---

### Post by jonray74 on 2007-11-13
seamless feature works very well on VirtualBox, but it's not the big thing in my opinion, as for me, I prefer VMWARE because of the USB features that VMWARE offers.

VirtualBox has a bug when it comes to detecting USB devices. I tried connecting my Nokia 6300 Cell phone on VirtualBox and it was very unsuccessful quite frustrating, I also tried plugging in my Canon SD600 digital camera with TWAIN driver installed and it was unsuccessful as well. For some reason, VirtualBox hasn't completed that feature yet. 

VMWARE however was very successful in detecting all of my USB devices which is what I wanted. For me, the seamless feature is minor, cause when it comes to performance, VirtualBox still has a lot to work on compared to VMWARE. The good thing about VirtualBox though is that it's opensource unlike VMWARE.

---

### Post by Frak on 2007-11-13
> **pompeyjohn said:**
> *gets excited* so QEMU has a faster redraw rate? The only reason I dual boot now is because I have a flight sim (phoenix) which heavily uses directx and the .net framework. If I could get this running on ubuntu I would be skipping with joy.

somebody please tell me QEMU can do this, and that it can rock directx !
There is no VM for Linux available that can play graphical games. Even on Windows and OS X the quality and speed is bad.

---

### Post by Luci4 on 2007-11-14
never mind...

---

### Post by maxxum on 2007-11-15
A great howto! I've had mixed success installing XPPro. Anyways what I wanted to achieve was to run yahoo messenger and install my logitech communicate stx webcam. While yahoo messenger works, I have no idea how to make XP see my webcam, even after installing logitech drivers and software.
Is this something that cannot be done?
On a similar note, I installed Office 2007 and now want to print from MS Word. How do I go about installing a printer? 

EDIT: After some research, it seems that some version of virtualbox has options for USB settings while mine does not. So now the question is that how to upgrade my virtualbox without losing the XP installation and settings? My virtualbox version is 1.5.0 and I am using Gutsy.
EDIT2: I installed virtualbox 1.5.2 after uninstalling 1.5.0_OCE. The virtual machine is intact. However I get this USB error when it starts up:
```
Failed to access USB subsystem.
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.
```

---

### Post by lime4x4 on 2007-11-15
Have u tried this? I saved it from another post on the forum here. This is what i did to get usb working.

Basically, in the file /etc/init.d/mountdevsubfs.sh you need to edit the lines:

Code:

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

to look like this (removing four #'s):

Code:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

3. Edit the file /etc/udev/rules.d/40-permissions.rules (for this, you must have administrative privileges)

    3.1 Search for the following lines

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb_device",                    MODE="0664"

    3.2 Change them to the following

    # USB devices (usbfs replacement)
    SUBSYSTEM=="usb_device", GROUP="usbusers", MODE="0664"

4. Restart your PC

5. You should now have write access to all usb devices.

---

### Post by maxxum on 2007-11-15
I got the USB to work. It made the virtual machine a bit sluggish...but it works.

---

### Post by Amin1_0_1 on 2007-11-16
I can't find "Remote Display and Enable VRDP Server" in my settings,where is it?

---

### Post by dlogic on 2007-11-16
Hello everyone, 
I'm wanting to follow this particular how-to but I actually followed another how-to previouls y and created a host interface that I would like to remove first.

ifconfig output:
```
br0       Link encap:Ethernet  HWaddr 00:12:3F:A7:62:80  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fea7:6280/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1275506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:942653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1380436961 (1.2 GB)  TX bytes:279053127 (266.1 MB)

eth0      Link encap:Ethernet  HWaddr 00:12:3F:A7:62:80  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1275589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:942660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1398992502 (1.3 GB)  TX bytes:279053661 (266.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vbox0     Link encap:Ethernet  HWaddr 00:FF:50:BE:52:3D  
          inet6 addr: fe80::2ff:50ff:febe:523d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:2758 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

How would go about removing vbox0?  

Thank you in advance for your help.

---

### Post by viko on 2007-11-18
hi DLogic

sudo VBoxAddIF vbox0 <user> br0

---

### Post by duncanyoyo1 on 2007-11-18
For some reason after i installed VirtualBox I get a new Server version of ubuntu on my boot menu. It works it's just that it runs in restricted graphics mode ( no effects and the resolution is limited to 800x600 ) how can I get it to run normally? I cannot check the restricted drivers, It says I need to install something, But I cannot seem to be able to install it ( I even copy and paste the code into the terminal and it says package not found ) If I cannot make it run normally I would like to just remove it from my boot menu.

---

### Post by dlogic on 2007-11-18
viko:  That actually did not remove the host interface for me, it basically just created vbox0 that was already there.

---

### Post by CoronaBVW on 2007-11-20
To DELETE the interface use:

VirtualBox host networking interface creation utility, version 1.5.2
(C) 2005-2007 innotek GmbH
All rights reserved.

Usage:** VBoxDeleteIF <interface name>**
Delete the permanent interface <interface name> from the host system.

---

### Post by Lothas on 2007-11-23
Wow, I've gone through almost every step of this How To:
[http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop](http://ace2016.net/tutorials/linux/run-windows-xp-applications-seamlessly-on-your-linux-desktop)

I'm still having 2 problems:
1. I can't open the X: shared folder even though it appears under My Computer
2. I can't rdesktop to the virtual machine. I get "connection refused" when using this command:
```
rdesktop -rsound:remote -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Shell\WinShellEx\WinShellEx.exe" -c "c:\seamlessrdp" localhost:6666 -u "Username" -p -password -N
```
Or "connection time-out" when using this command:
```
rdesktop -rsound:remote -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Shell\WinShellEx\WinShellEx.exe" -c "c:\seamlessrdp" 10.0.2.15:6666 -u "Username" -p -password -N
```

I've been looking at other posts but there's too much info out there. It's overwhelming!

---

### Post by pneaveill on 2007-11-23
Am running Gutsy ubuntu on AMD k-7 machine with dual monitors and dual OS with Win2k.  What I am hoping to do and not take things off track in this thread is to run the win2k from linux kernel natively.  If moderators need to move this to its own thread, that is fine.

I loaded virtualbox and it gives this error: 
```
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

(1) I ran on google search and it brought me here.

(2) I see in the posts below that someone suggested loading Beryl might help.  Guess I don't know enough about Beryl to know if it will or not.  **[COLOR=RoyalBlue]FYI: I have xinerama driving my matrox 400/450 card. Will this conflict with Beryl?[/COLOR]**

(3) I attempted auto remove from synaptic and it crashed twice, then did apt-get remove and apt-get purge to remove it, which finally worked. Rebooted machine and reinstalled from apt-get rather than synaptic. Why won't synaptic remove this thing off the computer?

(4) same errors as previous attempts. What am I doing wrong on this thing?

Appreciate the assist for a semi-newb

---

### Post by Lothas on 2007-11-24
> **pneaveill said:**
> 
I loaded virtualbox and it gives this error: 
```
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

```


I believe I had the same problem. Make sure that your user is part of the group vboxusers (under Syestem > Administration > Users & Groups). Go to manage groups, find vboxusers, properties then make sure your user is ticked. Close everything, log off and log in again. That might solve it.

---

### Post by pneaveill on 2007-11-24
> **Lothas said:**
> I believe I had the same problem. Make sure that your user is part of the group vboxusers (under Syestem > Administration > Users & Groups). Go to manage groups, find vboxusers, properties then make sure your user is ticked. Close everything, log off and log in again. That might solve it.

I appreciate the follow through. At first, I forgot to check that my name was listed in those that have access to it. For those future readers who missed this, under system -> Administration -> Users and groups, you click on the item you need, then check who has access to it. In my particular case it listed myself and root, with neither of them checked. I checked them both and rebooted and it came up.

Thanks so far and will list the next error in another box

---

### Post by pneaveill on 2007-11-24
> **pneaveill said:**
> I appreciate the follow through. At first, I forgot to check that my name was listed in those that have access to it. For those future readers who missed this, under system -> Administration -> Users and groups, you click on the item you need, then check who has access to it. In my particular case it listed myself and root, with neither of them checked. I checked them both and rebooted and it came up.

Thanks so far and will list the next error in another box


For some reason, it seems to be looking for the floppy (despite my best efforts to have the floppy disabled). The error it gave was this:
```
 PXE-E53: no boot filename received

PXE-Mof: Exiting Pxe ROM
Fatal: could not read from boot medium!
    System halted.
```Fatal error indeed!! It locked it up tight, causing me to hit reset button after about a 10 minute wait for it to recover.  Seems like I lost use of the keyboard and mouse on that computer.

---

### Post by pneaveill on 2007-11-24
> **pneaveill said:**
> I appreciate the follow through. At first, I forgot to check that my name was listed in those that have access to it. For those future readers who missed this, under system -> Administration -> Users and groups, you click on the item you need, then check who has access to it. In my particular case it listed myself and root, with neither of them checked. I checked them both and rebooted and it came up.

Thanks so far and will list the next error in another box

Here is the next error: DHCP error and craps out while looking for floppy

---

### Post by stldirty on 2007-11-25
ok, i get all the way up to the part that says to run the command in terminal to actual run windows xp seamlessly.  right after it says i should make a launcher for the following commands.  but when i enter the info into the terminal, instead of an xp desktop popping up all i see is the terminal saying "Autoselected keyboard map en-us"  and nothing else...any ideas?

edit:  ok after a couple of minutes it says "ERROR: connect: Connection timed out"

---

### Post by Lothas on 2007-11-25
> **stldirty said:**
> "ERROR: connect: Connection timed out"

I'm having the same problem

---

### Post by MasterJS on 2007-11-25
Okay, the best way i had success was following the instructions that the last poster of page #17 wrote. It helps u use NAT and it works flawlessly.

---

### Post by Lothas on 2007-11-25
I tried following the steps from the last post on page #17 but still no luck. Now Windows is "running" but I can't see it, stop it or do anything with it. Also, when I try to rdesktop to it, I get:
ERROR: recv: Connection reset by peer

---

### Post by adrianmak on 2007-11-25
I used the NATconnection method posted in page#17 and it is working fine for me. However the task bar of xp guest show out of my screen.

As shown in below screen cap.

[IMG]http://i108.photobucket.com/albums/n16/adrianmak/Screenshot.png[/IMG]

---

### Post by stldirty on 2007-11-26
how do you get sound working?

---

### Post by adrianmak on 2007-11-26
I want to excute Internet Explorer 
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\IEXPLORE.EXE" <IP recorded from Windows>:3389 -u "<Your Windows Username>" -p <Your Windows Password>

But it just give a windows xp desktop, no IE executed and it is not seamless

---

### Post by adrianmak on 2007-11-27
I compiled rdesktop with a patch introduce by Kilou on page11, which patched rdesktop  have one more option to execute win app with an existing rdp session.

Compilation process is smooth.
But when I execute rdesktop as normally as before, it give me an error
Failed to open keymap en_us

What's the problem ??  I didn't see this error in old rdesktop binary

---

### Post by JetPack on 2007-12-02
I may be missing the point.... but VirtualBox v1.5.2 comes with a "seamless" mode. Without running the guest OS as headless and accessing through RDP. This is done by right_CTRL^L as default from the window view.

I have noticed that this does "mask" the Gnome desktop so it is not possible to manipulate icons on the gnome desktop whilst the Windows window is "expanded" (where you can see the Windows start button) but just minimise the Windows window and then the gnome desktop is fully accesible. Obviously, restore the window to get back to the Satrt Button view.

I am not a gamer but I use my laptop for business and I have found this a great solution for integrating those nasty Microsoft applications into my serene Ubuntu environment (Visio, Access, Project).

Also, I have sound, VM shares, networking, and the display all working fine in the guest OS.

There are two commands that can be used to start-up and shudown the guest OS without even needing to run the VirtualBox GUI.

To start (using the appropriate guest OS name in quotes):-
```

VBoxManage startvm "WinXP-Pro"

```

To elegantly shutdown (again, guest OS name in quotes):-
```

VBoxManage controlvm "WinXP-Pro" savestate

```

I am now trying to find out how to place the second command as part of the gnome shutdown (or restart, or logout) routine.

---

### Post by sythem on 2007-12-02
An alternative to the networking would to be use port forwarding and Nat. Disable the built in remote desktop option and then use these 3 commands with the virtual machine off.

```
VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/Protocol" TCP

VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/GuestPort" 3389

VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/HostPort" <whateverportyouwanttouse>

```

This works with Nat networking and doesn't require any other linux networking configuration. Hope it's helpful.

---

### Post by ziroks on 2007-12-22
<Ignore>

---

### Post by ashmew2 on 2007-12-28
Hi , Thanks for the Ultimate Guide.. But i have one tiny question , I added shared folders to my Windows XP  Guest Machine (I added /media itself so i could have all the drives enlisted with a single command) , So i wanted to know , how do i get read/write access on all the partitions from within the Virtual Machine (the Windows XP guest)
Thanks

---

### Post by ziroks on 2007-12-28
> **ashmew2 said:**
> Hi , Thanks for the Ultimate Guide.. But i have one tiny question , I added shared folders to my Windows XP  Guest Machine (I added /media itself so i could have all the drives enlisted with a single command) , So i wanted to know , how do i get read/write access on all the partitions from within the Virtual Machine (the Windows XP guest)
Thanks

Hi, I had the same problem (or atleast similiar). I do not remember exactly what I did, but if my memory serves me well there are only two things that must be done.

1. Very important is to have installed Guest Additions for your Windows image.
2. To know that shared folders are stored in special server. By default this is:
\\vboxsvr\<shared_folder_name>

Of course for easier access to the shared folder you can map your \\vboxsvr in your Windows image.For XP this is done from My Computer >> Tools menu >> Map network drive

You can check this also in the user manual for Virtual box, which is placed in:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
(User Manual (version 1.5.2, updated 2007-10-18) )

* * * * *

Here I have another question:  Is it possible to run games this way?

I mean i have done all the walk through and almost everything seems to work properly. However when I try to run some game (of course using Direct 3D engine) there goes "Visual C++ runtime error" or somethingl like this. This occurs only when I start the game while the Virutal machine is accessed with Remote Desktop. If I ran the virtual machine in Virtual box as a separate window all works perfectly.

Please answer when can. Hapy Holidays!

---

### Post by glennric on 2008-01-20
> **sythem said:**
> An alternative to the networking would to be use port forwarding and Nat. Disable the built in remote desktop option and then use these 3 commands with the virtual machine off.

```
VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/Protocol" TCP

VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/GuestPort" 3389

VBoxManage setextradata "NameOfTheVirtualMachine" "VBoxInternal/Devices/pcnet/0/LUN#0/Config/remotedesk/HostPort" <whateverportyouwanttouse>

```

This works with Nat networking and doesn't require any other linux networking configuration. Hope it's helpful.

You should point out that the rdesktop command to connect to the virtual machine with this setup is
```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <IP of Ubuntu>:3389 -u "<Your Windows Username>" -p <Your Windows Password>
```
It took me a while to figure this out.  The problem with this is that it is not very seamless.  The client loads fullscreen.  You can then alt-tab to linux apps and then the panel appears, but the desktop does not.  If you try to do anything with the client it takes over the fullscreen again.

---

### Post by hotroddude on 2008-01-20
wow, thats so cool. is there any place where i can find the edgy iso?

---

### Post by ashmew2 on 2008-01-22
Go look in [www.ubuntu.com](www.ubuntu.com)  for the edgy ISO.
But i was wondering why is rdesktop so very slow as compared to the Vbox running in the foreground ?
And is there any way to speed it up ?

---

### Post by bharadwaj on 2008-01-22
how much ram would i be needing for installing basic windows apps?

---

### Post by MNICY on 2008-01-24
Just did this in Gutsy.
Worked perfectly (except for a spelling mistake, but that was MY fault) ;)

---

### Post by MNICY on 2008-01-24
any way to do Window Matching with Compiz?
The "exporer.exe" shows up as "Untitled Window", but i can not get window matching to work with that title (because it is untitled?)

is there a way to force an rdesktop window to have a name or something?

---

### Post by mikeytag on 2008-01-30
For anyone reading this post, Virtualbox now has a seamless mode that you can get into by pressing the right Control key and S. This is the official way to do seamless windows now and is much much easier and is being more actively developed than this old tutorial that I wrote. I recommend anyone to install the newest version of Virtualbox and give the native seamless a shot before following this.

---

### Post by TSJason on 2008-02-07
I'm extremely happy with this post and find it very cool that virtualbox has integrated this functionality. I am now wondering if it's possible to achieve similar results when the OS's are swapped? IE, can I run some of my linux apps seemlessly from my windows desktop. At works I have to use the Windows desktop but I greatly prefer the stability and functionality of several linux apps over those in Windows. RIght now, I use an NX session in a seperate window to do this. I'd like to just use the particular apps in a seemless mode instead. I already searched google for this but the results are overwhelmingly windows in linux. Any thoughts on this are appreciated.

*Edit*

I realized a split moment after submitting this that someone may suggest cygwin, but that's not really feasible in this situation. I really would prefer connecting to the running linux apps in terminal services style from the remote machine....after all cygwin on linux is only as stable as windows itself.

---

### Post by rockerrock on 2008-02-14
I would like to point out that after following your awesome tut that this method is EXCELLENT for "clustering". After setting this all up in Vbox on my linux machine, I took the Vbox image and put it on my real world Windows XP machine and emulated it there.

What this means, VBox (Windows XP seamless virtual machine) uses a second pc for all its processing and memory while working the same if it was local.

!! Tested on 100M network, no lag vs running locally noticeable !!

Its tons faster than running local with Linux and while Linux is busy, you can work with your seamless XP environment with no slowdown, on the same screen!


Soo cool!

If you already have this set-up per tutorial, just move your Vbox hard disc image to another machine and press start. Just make sure the other pc is networked and ports unblocked as you would for any typical network.
(Windows XP: Helped me to setup a network bridge between VirtualBox Virtual Interface and my LAN adapter)

---

### Post by shmengie on 2008-02-16
> **Amin1_0_1 said:**
> I can't find "Remote Display and Enable VRDP Server" in my settings,where is it?
yeah, me too. i'm running 1.5.0 ose.

**edit**: nvm. i found the deb for 1.5.4.

**edit again**: holy macaroni! i am up and running. this is the coolest, thx!

---

### Post by lancerocke on 2008-02-16
> **woodgdo1 said:**
> Pretty cool idea. I think I will give it a shot with my vmware install to see if that works.
I cant get the internet working.
Here is my 
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
tunctl -t tap0 -u danny
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth0 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth0
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.1.102 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 192.168.1.100 dev tap0
 arp -Ds 192.168.1.100 eth0 pub
exit 0
```

---

### Post by shmengie on 2008-02-16
okay, perhaps i spoke too soon. after i had everything working, i decided to test the auto-start function to see if it would work at boot up. well, i heard the windows startup sound and "VBoxManage startvm WXP -type vrdp" is in the startup group and is running as a session, but i don't see the windows taskbar. so i reran```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.1.3:3389 -u "xxxx" -p xxxxx
```of course, i got only a windows view, so i logged out and reran the just mentioned 'rdesktop' command again. this time, i saw the windows taskbar for about half a second, then it went away. this time, 'vboxmanage...' is not in the current sessions. (btw, i just tried the 'rdesktop' command again. this time, i had the windows taskbar for about 5 seconds before it just vanished).

bottom line, it seems like it's working, but crapping out very quickly for some reason. after i had it working, i didn't make any changes other than rebooting to check the auto-start. anyone have any ideas?

thx!

---

### Post by shmengie on 2008-02-17
okay, i figgered out what's going on: if i close my terminal session, it kills the reomte session. is this expected behavior? any way to fix it? thx!

---

### Post by themonkeyspanner on 2008-02-17
I am having trouble with this VBOX setup.:confused:

Do I have to do anything with my " **/etc/network/interfaces** " file?

As I have used the scripts detailed here and set everything up but I can not see the virtual WinXP Pro machine from my Windows Vista physical machine on my network. I can not ping the VM machine at all or anything.

Am I doing something wrong?:(

---

### Post by tshearman on 2008-03-01
Oh jeez! I'm so close!

Windows is up and running, everything is cool.

```

toby@CHEMATHHome:~$ VBoxManage startvm "Windows" -type vrdp
VirtualBox Command Line Management Interface Version 1.5.6
(C) 2005-2008 innotek GmbH
All rights reserved.

Waiting for the remote session to open...
Remote session has been successfully opened.
toby@CHEMATHHome:~$ 

```

All is good...

Now I run

```

toby@CHEMATHHome:~$ rdesktop -rsound -A -s "C:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" 192.168.1.199:3389 -u xxx -p xxx

Autoselected keyboard map en-us

```

But the entire Windows Desktop pops up, not just the Taskbar...
EDIT:  It is seamless though.  It has no titlebar etc... just the whole screen as Windows Desktop (alt + grab doesnt do anything)

Thoughts anyone...  I saw someone wrote that virtualbox now has it's own seamless built in... does anyone know how to make that work?

Thanks

---

### Post by bben on 2008-03-08
> **tshearman said:**
> Thoughts anyone...  I saw someone wrote that virtualbox now has it's own seamless built in... does anyone know how to make that work?

Thanks

I had to press right-control + L to enter seamless mode
It's glitchy though, especially when you're using compiz-fusion

---

### Post by enitemaus on 2008-03-19
I've managed to do everything without any errors, it works perfectly (amazing job you've done with this howto).

As I said, everything went well except for one thing: The rdesktop seems to mess with keyboard layout stuff...  when i start the VM normaly, it works perfectly (i use PT-BR on ABNT2 Brazilian keyboard), but when i start in background and connect with rdesktop, it's all messed up.

Anyone having the same issue? Or know anything i can do to fix this?

That's the only reason i'm not using this on production environment yet. Thanks for everything else anyway!

---

### Post by sp3ctum on 2008-03-28
I'd very much like to try this, but I'm not sure what to follow. The howto reads it's for edgy, but I have gutsy. Do I need another tutorial, or am I good with the one on the first page?

---

### Post by dundel on 2008-03-29
I never got rdekstop working i'm going to try this, thanks for the tut.
I'm running a virtualized Windows XP (vbox), now for almost 7 months. It's a really nice setup to be working in.
I'm using Gutsy with 3 taps

---

### Post by sp3ctum on 2008-03-29
Is the tutorial on the first page valid, or do additional steps need to be undertaken for 7.10 ?

---

### Post by rpm161 on 2008-04-01
> **bben said:**
> I had to press right-control + L to enter seamless mode
**It's glitchy though, especially when you're using compiz-fusion**

Can you elaborate on this?  I've also experienced some "glitchyness" with seamless mode and thought that it might be due to compiz-fusion.  Glitches include: screen freezing, XP application windows not disappearing when the "X" button is clicked to close, WinXP start menu gets stuck open, black screen, etc.

Pls let me know if you've found a workaround!

---

### Post by sythem on 2008-04-17
You have to sign in twice, the 2nd time it's seamless, don't know why.

P.S. This was obviously a reply to a much earlier post.

---

### Post by Tim0miT on 2008-04-22
erm yeah, thanks


NOT, totally f**ked my XP install up, i gota go through the whole XP install now, and go through eh who activation again, which took me like 1/2 a f**king hour to sort out!!!

they gota make this seemless windows things alot more user friendly!!!

sorry im angry, lol

---

### Post by navaburo on 2008-04-30
Great HOWTO! I am happily using seamless XP/Vbox on my Fedora 9 system. Nothing had to be changed except the VBox install itself. I needed to get the generic Linux version (.run).

The above works perfectly for me, using synergy to share a mouse and keyboard between the desktop and the laptop. Synergy and VirtualBox's gui DO NOT GET ALONG. But rdesktop has much better mouse handling so synergy is no problem.

I have a minor addition: **HOWTO use NAT instead of Bridging**:

I use this setup on a laptop which is always traveling around. Some networks I use regularly are quite picky about what machines they allow on the network, and so bridging really isn't an option. Also, Jose, you may find this useful (since bridging broke your system). So I use NAT in the following way:

1. Use the default VBox networking settings (NAT).

2. Add a port forward for rdesktop (3 commands on the host system):
```

VBoxManage setextradata "LifXP" "VboxInternal/Devices/pcnet/0/LUN#0/Config/guestrdesk/Protocol" TCP

VBoxManage setextradata "LifXP" "VboxInternal/Devices/pcnet/0/LUN#0/Config/guestrdesk/GuestPort" 3389

VBoxManage setextradata "LifXP" "VboxInternal/Devices/pcnet/0/LUN#0/Config/guestrdesk/HostPort" 3389

```
3. In the rdesktop command, instead of <the windows IP you wrote down> use localhost. You actually never need to write down the windows ip ;)

4. Enjoy! :popcorn:


**EDIT**: Clarification about network/nat/seamless
The above technique does NOT make seamless work! The way I was using seamless was by pressing [HOST]+L in VirtualBox. Below I will give the various possible methods by which seamless over a network could work:

1) The rdesktop technique will work over the network, but will only be seamless if you use Bridged. No NAT. :(

2) In a NAT configuration, by using ssh R-tunneling, initiated on the guest (think Putty), you can access the VM's port 3389 instead of that of VBox, in theory allowing seamless rdesktop use. However, every time I have tried this I get a login screen (even though i am allready logged in) on the rdesktop display (no seamless), which has a password typed in and grayed out. Simultaneously the VM crashes.

3) Just use the seamless mode that is built into VirtualBox, by pressing [HOST]+L. Of course, if you want to use this over the network you will need X-forwarding. However, I have found this to be slow, glitchy (invisible windows and smearing), and unstable (causing the VM to randomly crash).


Hope some of this can be useful. I have certainly learned from over three days of playing with this and reading through this epic thread!

---

### Post by ashmew2 on 2008-06-07
For people with Hardy Heron and new version of Vbox (1.6.x) , check : 
[http://ubuntuforums.org/showthread.php?p=5134497#post5134497](http://ubuntuforums.org/showthread.php?p=5134497#post5134497)

---

### Post by mojorising on 2008-06-23
Woodgdo1, Thanks for the AD tip I was wondering why I wasn't getting the seamless windows in my rdp session going and your tip really did the trick!

Mike

---

### Post by mojorising on 2008-06-27
This works pretty well. Thanks for the great howto!

I am running into one pretty serious problem, however. 

When I run my rdesktop session, I see these messages at the command line:
```

WARNING: Failed to aquire ownership of PRIMARY clipboard
WARNING: Failed to aquire ownership of CLIPBOARD clipboard

```

While rdesktop is running and connected to my VM, I can not copy or paste at all. When I try, the application I'm trying to paste to gets "stuck" for a minute or two, preventing any input from the keyboard or mouse. 

The issue is serious because I *really* need to be able to copy and paste among Linux applications (if I can't copy/ past from Linux to Windows or in Windows at all, that's not a problem).

I searched Google for this error message and I only found one English result, which doesn't give me much to run with: [http://osdir.com/ml/network.rdesktop.user/2004-11/msg00006.html](http://osdir.com/ml/network.rdesktop.user/2004-11/msg00006.html)

Thanks a ton for any help anyone out there can provide.


Mike

---

### Post by Be_Linux on 2008-07-09
i'm useing this virsion of VirtualBox
[[IMG]http://up5.m5zn.com/photos/00087/gnicl94ijeqo_th.jpg[/IMG]](http://up5.m5zn.com/photos/00087/gnicl94ijeqo.jpg)

and i Can't find Remote Display in liste
[[IMG]http://up5.m5zn.com/photos/00087/py1gla57hens_th.jpg[/IMG]](http://up5.m5zn.com/photos/00087/py1gla57hens.jpg)

how can i install the missing one ---> [COLOR="Red"]Remote Display[/COLOR]

---

### Post by liechtir on 2008-07-11
Hi guys

The tutorial tell us to disable the network manager. My wlan card is running using the nm-applet 0.6.6 which I guess is the user itnerface for the network manager.

How can I run my card without network manager, so I can do that seamless integration of XP to gnome?

At the moment I'm using NAT in XP image, so I'm able to browse the internet from that win xp image.

Thanks,
Remo

---

### Post by mr_byte on 2008-07-11
> **liechtir said:**
> Hi guys

The tutorial tell us to disable the network manager. My wlan card is running using the nm-applet 0.6.6 which I guess is the user itnerface for the network manager.

How can I run my card without network manager, so I can do that seamless integration of XP to gnome?

At the moment I'm using NAT in XP image, so I'm able to browse the internet from that win xp image.

Thanks,
Remo

I had that problem as well.  Go to [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=2980021#post2980021[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2980021#post2980021") and read my summary.

I've added things since then, but you'll get the gist of it.  The first bit shows how to redirect a port and you won't need that tap0 stuff that messes with networkmanager. :guitar:

---

### Post by liechtir on 2008-07-12
Setting up Windows with the outlogout worked great, thanks for that!

Now I got the problem, that if I do:
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" localhost:6666 -u "user" -p password

I get:
Autoselected keyboard map en-us
ERROR: connect: Connection refused

First: I need to use Swiss German keyboard, can this be set somewhere in VBox(or is the rdesktop the one who set's it?)

How to configure the network interface in VBox? At the moment it's set to NAT. 

Thanks dude!

Remo

---

### Post by mr_byte on 2008-07-12
> **liechtir said:**
> Setting up Windows with the outlogout worked great, thanks for that!

Now I got the problem, that if I do:
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" localhost:6666 -u "user" -p password

I get:
Autoselected keyboard map en-us
ERROR: connect: Connection refused

First: I need to use Swiss German keyboard, can this be set somewhere in VBox(or is the rdesktop the one who set's it?)

How to configure the network interface in VBox? At the moment it's set to NAT. 


Thanks dude!

Remo

I always use NAT, myself, so as to not have to run a virus scanner etc. I figure that if someone can hop thru my router and the NAT to my VM, then they DESERVE to be in there ;) but there's nothing in there I'm worried about them getting into. (then again, I rarely network out of my seamless VM anyway.)

Rdesktop will be where you set the keyboard, not sure of how to do that, might be in the man page.

For the connect refused:  You are sending the user/password you setup in your VM?  Also, you need to wait a little to get the VM up and running.  If you are using the flag file setup like I described, it should go fine.

The only other thing I can think of is that the VM is not running for some reason.  Try running the VM from VBox first, before you run it headless from a command prompt.  Make sure that the name you call from the command prompt is the same you used to setup the VM (ie:Seamless, or XP, or what have you)  

Have you reset your networking to get rid of the tap0 stuff?  I don't know that it would conflict, but it could.

Jeff

---

