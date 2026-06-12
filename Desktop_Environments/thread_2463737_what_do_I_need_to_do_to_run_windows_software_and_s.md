---
title: "what do I need to do to run windows software and steam/EA games on ubuntu desktop"
date: 2021-06-17
forum: Desktop Environments
---

### Post by tross9 on 2021-06-17
I'm looking at switching from windows 10 to ubuntu on my desktop.

i mainly use my desktop for
  gaming ( window or doxbox)
  video and picture editing
  web scraping and loading to stock info to database for analysis.
  game developing

I use the following and would like to know what I need to do to run them on ubuntu.
   I think that some will have a Ubuntu version that I'll need to install.
     but i see posting about emulators but not sure which one is best or if they are really needed.
     
several Steam game (DCS, Xcom, etc...)
several EA games ( Battlefield,...)
several windows ( non steam of non EA controlled )  
DosBOX
WOrld of Tanks
Battle Net games
   
CHCTmgr -- a CH-Products controller software for joysticks and other controller
  
-- other software: short list --
vb script
unity
epson scanner software
powerbuilder (Sybase)  
blender
handbrake
obs studio
visual studio
mySql
Powershell

i can probable figure out which software has a ubuntu version but i really need to know what i need to run the above software.

Thanks Tim.

---

### Post by TheFu on 2021-06-17
Linux is not Windows.  Expecting to keep working the same way you did on Windows will just lead to frustration.  With Unix-like system, you'll want to start thinking a different way and some hardware might not work at all.

WINE is how most people run Windows software on x64 Intel CPUs under Linux. Many programs work fine, a few are good to excellent. But IME, about 80% don't work at all.  I spent months trying to get Quicken working about 10 yrs ago.  Never got everything working in it - the tax planning parts never worked under WINE.  Then a new Ubuntu release came out and broke WINE. I spent a week trying to get it working and failed.  Decided that having a Windows VM for the 5 things that were easier under Windows was just smarter. It wasn't worth my time to fight software to get it working.

I had an Epson page scanner. It never worked under Linux. NEVER.  Forget about most hardware connected software from working. You'll need to use Linux tools going forward.

I wouldn't expect vb-script to ever work under Linux.  There is good news.  Ruby, Python, Perl, bash are all extremely capable scripting languages and work crazy-great.  The bad news - none of those are vb-script.  
blender, handbrake, obs, mariaDB (nobody uses mysql anymore) are all available on Linux.  You'll probably want to research blender and obs addons to ensure some you might depend on exist for Linux.  For example the green-screen addons for OBS are non-trivial to get working and require deeper understanding of Linux and kernel modules than most normal people can handle.

Powershell - on Linux?  Some things are just, just, just, WRONG!  ;)

There are many things called "unity" on Linux. You'll need to be more specific. If it is the Unity DE from Ubuntu 12.04 - 16.04, then know that project is not official anymore and only maintained by volunteers. That means people will get bored and leave every year, especially as other DEs meet their needs better.

When you say video editing, that can mean 1000 different things.  I edit videos almost daily, but have never used blender. Different sorts of editing uses different tools.  I mostly use mplayer as my editor these days with EDL file creation --> script --> resulting, edited, video, but sometime drop back to an MS-Windows program when finer editing is needed. The Windows program cannot handle all the different video file encodings I use. It is much too picky.

Nobody here can answer all the questions, since nobody here uses their computer(s) exactly the same way you do.  I don't game on Linux at all.  I do stock market stuff, but that's all using scripts I've written over decades and a webapp that dynamically creates stock views for my research.  
I'd say you have a 50/50 chance of getting most of those items working under Linux. The learning curve will be steep.  There's no chance everything will work, so you'll have to decide if enough does to switch or not.

---

### Post by scorp123 on 2021-06-17
> **tross9 said:**
>  several Steam game (DCS, Xcom, etc...)


There's a Linux version of "Steam" and in its latest releases it offers the possibility to play Windows games too. But it needs to be enabled.
[https://itsfoss.com/steam-play/]("https://itsfoss.com/steam-play/")

Also: This does NOT work for every game.


> **tross9 said:**
>  several EA games ( Battlefield,...)


EA's "Origin" is a mixed bag as far as Linux goes. Even if you get it working, chances are the next "Origin" update will break it again. I personally found it extremely annoying to get it working under Linux. Your mileage will definitely vary.
[https://www.addictivetips.com/ubuntu-linux-tips/how-to-use-ea-origin-on-linux/]("https://www.addictivetips.com/ubuntu-linux-tips/how-to-use-ea-origin-on-linux/")

Me personally I found it all so annoying ... setting the PC to dual-boot was easier and less problematic. So I boot into Linux if I need to do serious work ... and I still have a Windows 10 partition I can boot into if I want to play games. And all the games just work out of the box and don't require any manual fiddling.


> **tross9 said:**
> vb script
visual studio
Powershell


Those are programming languages and development environments native to Windows. They serve no purpose under Linux in my opinion. If you insist on using those you'd be better off using a VM or dual-boot.

[LIST]
[*]VB Script => you should learn Python instead, or any other language that's popular on Linux.
[*]Visual Studio => If you want to program in Java on Linux then use "Eclipse", "IntelliJ" .. and there are many more alternatives.
[*]PowerShell => Linux has its own shells and scripting languages, e.g. "Bash", "Zsh", and several others. No need for PowerShell here.
[/LIST]

---

### Post by oldfred on 2021-06-17
Good advice above.
Dual boot or use virtual install.
Expect steep learning curve, but worth it if willing to try.

My story.
I used Windows XP at work & home before retiring, years ago. 
At work used MS Access and VBA a lot to automate tasks & use data in a small division, originally mostly stand alone. Corporate hated me as I had created a  lot of essential apps for multiple departments and they did not want users using MS Access once they took over our computer systems. Converted most to use SQL-server so server backups backed up data better. And downloaded other data from Corporate servers.

But then at home used XP with Firefox, Thunderbird, OpenOffice and Quicken. I intentionlly installed the first 3 apps as I knew there were Linux versions. I dual booted for probably 5 years just for Quicken. But found updating Windows took most of Saturday AM just for Quicken updates. Found Linux app, not nearly as good, but ok. And then like theFu created my own programs using python & sqlite. Not as easy or integrated as Access, but more powerful.

I have one Windows 10 system just for TV. I hate tying to find how to make a minor fix or change. On line many examples but all screen based and it seems my version, does not match whatever version the example is. And clicking thru all the gui screens to get to setting, it seems the last screen is still the same as my old XP. But with Linux, settings are command line based since many gui. And terminal commands are a lot easier to use. I still do not remember many, but keep a zim file set with my own reference info.

---

### Post by ActionParsnip on 2021-06-17
[https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](https://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)
You can use this to check WINE compatibility. As stated earlier some applications don't work, some won't even install and some may even perform better than under Windows. Its a real mixed bag

---

### Post by tross9 on 2021-06-17
Thank you all for your replies,

   It appears that I'm stuck with windows on my desktop.  but if I want to see for myself what will or wont run , I at least have suggestions and an old laptop to play with.
    (well , at least my servers are running ubuntu.)

Again thanks for you replies/ suggestions

---

### Post by scorp123 on 2021-06-17
> **tross9 said:**
>  It appears that I'm stuck with windows on my desktop.  

You can still experiment with Linux e.g. by installing Ubuntu into WSL. If your Windows version allows it, that is. That way you'd be able to keep Windows 10 as a desktop but a functional Linux environment that's running at near-native speeds would only be one mouse-click away.

---

### Post by TheFu on 2021-06-17
I'm a strong believer in using virtual machines.  There is very little risk to the other OSes, unlike dual booting.  The storage is all "virtual" for any guest machines, so a 40G single file on Windows running a virtual Ubuntu brings very little risk to Windows, but almost all the power needed to try out Linux stuff ... except video editing and high-end games.  

Most people start with virtualbox on a Windows host, create a Linux VM and learn for 6-12 months that way.  You can try out video editing and try out most games and they will work, but the virtualGPU (VMs don't have direct access to hardware) just isn't the same performance level as even a $100 GPU would provide. Still, you'll know if something works or not. Information is power.

Eventually, some people fall in love with the normal power that Unix-like systems provide and will want the security, speed, and flexibility offered.  Then you'll probably want to swap your hostOS around.  Linux as the Host, still running virtualbox, but Windows as a guest VM.  By this point, you'll know which programs work well under Linux and will probably have different priorities than high-end gaming. If not, more powerful hypervisors (VM hosting software) and some specific hardware can allow hardware passthru to a guest VM.  A number of Linux users run a Windows VM and pass their better GPU into the Windows VM for native performance.  This is non-trivial and requires specific CPUs and GPUs and motherboards with kernel options setup a specific way.  It used to be extremely difficult, but today it is only non-trivial.  The required hardware isn't too exotic - just a motherboard that supports VT-x and IOMMU, and 2 GPUs - one for the hostOS and the other for exclusive use of 1 guest VM, usually Windows.  BTW, the software to make all this possible is 100% F/LOSS. No charge. Open Source.  People doing this (which I've never bothered), run the best games, at high frame rates, inside a virtual machine.

I ran Win7 Media center inside a virtual machine for a long time.  When Microsoft stopped providing free schedule data, I move over to some custom scripts to handle TV recording. I've been using Linux-based streaming boxes for a long time.  Have 2 r-pis now, running a specialized version of Kodi (the fork of XBMC).  

My Linux-fu is fairly good. Each week, I pull TV schedule data down (screen scraping automated; takes about 10 min), convert that data into a text DB, then run a filter to get the programs the house members would like to record, and schedule those recordings to happen over the next 6 days. Everything but scraping the schedule data takes less than 1 second.  Until Monday, there are 12 TV shows to be recorded.  Recording them doesn't mean someone will watch.  For the screen scraping to work, a little manual setup is needed which takes about 20 seconds inside a browser, manually.  Initially, I tried to automate everything, but it was too hard. Screen scraping requires clickable buttons to be in specific places. I got it down to 1 button needing to be in a specific location and wrote a tiny setup macro to show where the button needed to be located. Just resize and scroll the browser to make that happen, then it is golden for scraping 7 days of data.  Turns out, the macro just does 1 day of data, 7 times.  At some point, I might want 10 or 14 days of data.  BTW, Wayland breaks this workflow. It will only work with X11.  Wayland breaks a number of my workflows which became 2nd nature for me in the early 1990s.

I've tried to help people with their WSL setups and always found it frustrating. Things were just off, wrong, and the locations of files and shell commands didn't work correctly.  At the time, there wasn't any Linux GUI possible, so all the select/paste workflows didn't work either.  More frustration for me and the other person, because tab-completion didn't work right either.  Tip:  Windows has always supported using a / instead of a \ for directory separation. Always.  If you use WSL or powershell or cmd.exe, try using the / instead and you'll see that it works ... everywhere ... even when Windows is fighting against it.

---

### Post by ActionParsnip on 2021-06-18
Could install Ubuntu to USB (not just transfer the ISO and use persistence. A real install) then boot that when you want to use Ubuntu. For your needs it sounds like Windows is the better solution.

---

### Post by scorp123 on 2021-06-18
> **TheFu said:**
>  I've tried to help people with their WSL setups and always found it frustrating. 

It got a lot better. I now prefer WSL over CygWin or a Linux VM (e.g. VirtualBox, VMware, Hyper-V ...) if I have to work with Windows (e.g. company setting + mandated by employer). So if I can't get a pure Linux OS on my metal for whatever reasons ... then WSL it is.

> **TheFu said:**
>  Things were just off, wrong, and the locations of files and shell commands didn't work correctly.

Can't reproduce that. The Ubuntu 20.04 inside my WSL behaves exactly like I'd expect an Ubuntu 20.04 installation to behave, for the most part. The only thing missing here is access to ACPI tables and hardware sensors that I noticed so far. E.g. I have bits inside my ~/.bashrc that would read the system's current load, temperature, battery status etc. and print that out to me when I login. The temperature  and battery status parts don't work on WSL but that's about it as far as I can tell.

> **TheFu said:**
>  At the time, there wasn't any Linux GUI possible

The latest release will soon offer this possibility. For whatever good (or evil) that will do.

> **TheFu said:**
>  so all the select/paste workflows didn't work either. 

You can enable "Shift+Ctrl+C" and "Shift+Ctrl+V" and copy & paste stuff (e.g. whatever text you marked using your mouse...) that way.

[IMG]https://i2.paste.pics/5872bb2b37ec0754a26b903d5facf083.png[/IMG]
 
> **TheFu said:**
>  If you use WSL or powershell or cmd.exe, try using the / instead and you'll see that it works ... 

WSL does not support "\" for directory separation. Or maybe I should say "not anymore". You try that now and you get an error thrown at you, as I'd expect from a Linux system.

[IMG]https://i2.paste.pics/214aa951153563a0793f773ff8a3f7b6.png[/IMG]

---

### Post by tross9 on 2021-06-18
the main reason for this post was this,   
   ( the short answer -- i would prefer not to have to use new Windows 10 at all, because of the apps MS is requiring us to use. (edge, etc..) 

-- the long answer --
i'm running windows 10 build 18363 ( i did not want to upgrade to windows 10 at all because of the complaints i heard but i had too)
  when i first install windows 10 , i used the windows debloater PowerShell script (found it on the web) to dejunk windows ( remove/disable Cortana, Edge, cloud , and the rest of the trash Microsoft adds.)
    i upgraded to the latest build and found that Microsoft made it harder to remove their trash apps. ( the Debloater script updated for the new build , does not remove or disable all that it did the first time , looks like MS is forcing those apps)

i reverted back to 18363, i don't like were windows is going and prefer to control what my pc loads and does. ( Microsoft is getting into Big data and their apps need to capture what you do, in order to support their Big data project).
  and all those apps adds over head to the PC. ( not to mention the Big Brother aspect )

i'll look at WSL , and  maybe creating a Linux os with a virtual windows system could work. 

again thanks.

---

### Post by TheFu on 2021-06-18
WSL lacks all sorts of capabilities that a VM provides.  Any Core2 Duo or faster CPU with 6+ GB of RAM can easily run Linux inside a full VM.
Setup your network firewall to block most MS stuff and only allow access to the virtual machine running Linux to online resources.

Most of us here have ended up with a hybrid solution. My firewall is busy blocking most of what MSFT's OS wants to send. Linux is my daily use solution.

---

### Post by scorp123 on 2021-06-18
> **TheFu said:**
>  Linux is my daily use solution.

Same here. Especially at home. But at work? I sometimes don't have this choice and have to use the OS that an employer mandates. And in such a setting WSL has proven very useful for me.

---

### Post by scorp123 on 2021-06-18
> **tross9 said:**
>  i would prefer not to have to use new Windows 10 at all, because of the apps MS is requiring us to use. (edge, etc..) 

So... why not dual-boot then? Do your serious work (e.g. banking, writing mails, surfing the web, etc.) on Linux so Microsoft won't track you. But keep a Windows 10 partition for gaming, and just for gaming and nothing more.

This would be kind of "best of both worlds". Windows 10 would only get booted up for the occasional gaming session and rarely for much else. Not much to track there if you keep it that way.

---

### Post by CatKiller on 2021-06-18
Steam is easy: it's native. There are thousands of Linux games on Steam.

Windows games on Steam are easy: the Linux Steam client has a fork of Wine, called Proton, built in. You can see how well particular Windows games work in Proton at [ProtonDB](https://www.protondb.com/). Some are going to work better than others, obviously.

DOSBox is easy: it's native. 

Unity, Blender, Handbrake, OBS, MySQL are all native. Powershell is native, but you might come to prefer the standard shells which Powershell is trying to emulate. There are plenty of video editors, image editors, scripting utilities and IDEs. You'll still be able to do the same tasks, even if you're using different tools than the ones you've used before.

Non-Steam Windows games are easiest handled by Lutris. It sets up containers so that each game can have its own version of Wine, and can automatically apply tweaks that people have found necessary for particular games. 

I don't have any EA games, but my understanding is that the games themselves work pretty readily, but EA keep breaking their mandatory launcher. I only tried one Blizzard game, but that worked without any problems in Lutris.

---

### Post by tross9 on 2021-06-18
these are all good suggestions, i'll give them a try.

 I do have a laptop that is a core 2 duo, that i can use as a test site, so that if i mess up i won't lose anything.

 thanks again.

---

### Post by oldfred on 2021-06-18
If using an older system, a lightweight flavor is probably better. 
Ubuntu using gnome3 expects newer systems with more RAM & better video cards/chips.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

My old Core2 Duo laptop from 2006 has only 1.5GB of RAM. 
I used to install Ubuntu, then converted to using "fallback" gui which was lighter weight when Ubuntu converted to Ubiquity from old gnome2. Typically slow with Ubuntu even then. And limited on how many apps I could load at once.
With 20.04, it would not install Ubuntu. Ended up installing server & then adding fallback.

But then converted desktop to Kubuntu and tried that on laptop. Bit surprised as Kubuntu not a lightweight flavor but it works reasonable well. Desktops now have SSD, so old laptop is slow in comparison, but functional.

---

