---
title: "VMWare player vs VMWare Server"
date: 2006-07-02
forum: Desktop Environments
---

### Post by josys36 on 2006-07-02
I know that quite a few of us are using VMWare to run windows. I have a few questions for the folks out there who are doing so.

1. Have you experienced the CPU clock running slow issue? If so, what did you do to fix it if any.

2. I looked at VMWare Server, but did not like it since I could not find a way to quickly switch from the Windows guest to the Ubuntu host. Is there a way like in VMWare Player to quickly move between the Windows guest and the Ubuntu host?

3. Which did you prefer? VMWare Player or Server.

Thanks!

Jason

---

### Post by Thund3rstruck on 2006-07-02
IMO, vmware server is better by far. It's so simple to install and configure and I love that i can access network VM sessions. I have had no problems switching quickly between the guest and host. Its a little non-intuitive but if you always go to quick switch mode, you have to move the mouse to the top of the screen to see a hidden menu that allows you to minimize the guest and go back to the host

---

### Post by mdurham on 2006-07-02
I think you need to install Vmware Tools.

---

### Post by josys36 on 2006-07-03
So there is an option that allows quick switching from the guest to the host! I knew one had to be there I just did not try quick switch mode.

I will put back server and see how this works.

Jason

---

### Post by josys36 on 2006-07-03
Oh and I already have VMWare tools installed.

---

### Post by josys36 on 2006-07-05
Well I tried VMWare Server again and it did not solve my issues. I really don't like the quick switch option at all, and the clock problem is still there.

Maybe they are working on this for the next release of Player.

Jason

---

### Post by scxtt on 2006-07-05
1. what "running slow" issues are you getting?  a few Mhz off or something much worse? -- i don't touch the "CPU" for my VMs and they're always listed as the same as my actual CPU ...

2. all i do it hit "Ctrl + Alt" at the same time and shrink VMware server when i need to ... i'm having trouble coming up w/ 'quick switch' problems you could be having - what method do you use now that you don't like?

3. VMware Server, hands down -- what's the point of only running other peoples' VMs, i'd MUCH rather be able to create my own ...

---

### Post by quedigg on 2006-07-05
use Xen , here is a toturial of windows intallation fron ubuntu !
[http://www.planetjoel.com/viewarticle/568/HOWTO%3A+Windows+XP+running+under+Xen+3.0+on+Ubuntu+Dapper+Drake]("http://www.planetjoel.com/viewarticle/568/HOWTO%3A+Windows+XP+running+under+Xen+3.0+on+Ubuntu+Dapper+Drake")
[IMG]http://planetjoel.nfshost.com/images/win-desktop.thumb.png[/IMG]

---

### Post by FredB on 2006-07-06
Xen ? Wow ? ;)

I know I am a geek, but I don't want to get my brain running out of my ears using Xen ;)

-->[]

---

### Post by josys36 on 2006-07-07
The issue I have with VMWare player vs server is the method to switch from the guest to the host. What I like about player is that there is a hidden menu up at the top of the guest, which you can then use to minimise the guest and go back to the host. I tried the same functions in server, but when the guest is full screen, there is no hidden menu without doing Ctrl + Alt. I HATE having to use keyboard shortcuts! This works for some, but for me they drive me nuts.

The speed issue I am having is with the PC clock. The clock runs 50% slow. This is a known issue for VMWare and they are working on it. For example VMWare tools will auto sync your guest clock to your host clock once a minute. This allows your guest clock to stay more current. This causes problems with sound. For instance if you are playing a MIDI file it will play about 50% slower then it should. This is because MIDI players use the PC Clock for their timing.

Personally I wish Server would come the same way that workstation does. Workstation comes with both Workstation to build VMs and then Player to play those VMs. But, I really don't mind using Server to build my VMs and then installing player to play em.

---

### Post by mannheim on 2006-07-07
> **josys36 said:**
> What I like about player is that there is a hidden menu up at the top of the guest, which you can then use to minimise the guest and go back to the host.

Yes, absolutely! I own the "Workstation" version; but like you, I use the Player for actually running my VM's. This one user-interface feature is the reason.

> 
The speed issue I am having is with the PC clock. The clock runs 50% slow. This is a known issue for VMWare and they are working on it. 

I don't have that problem (I know that's no help) running Windows XP as guest and dapper as host on my Dell P4 machine.

---

### Post by FredB on 2006-07-07
So do I. No problem of slower clock. Strange anyway ;)

---

### Post by mdurham on 2006-07-07
Have you tried [http://www.easyvmx.com](http://www.easyvmx.com) for creating virtual machines?

---

### Post by josys36 on 2006-07-07
I found out about EASYVMX after I had built my windows xp virtual machine. However, the next time I need to create a new one I will check them out. 

When I first switched to Linux I was making virtual machines all the time. Mostly just to dink around an learn. Now I have my Win XP machine up and running so I don't have a need to create VMs that often.

But who knows, I might want to fool around with OS/2 again!

Jason

---

### Post by josys36 on 2006-07-13
Well VMWare Server is now out of Beta.

I am going to download the new version and see how this works.

Jason

---

### Post by cogsprocket on 2006-07-13
The point is kind of moot by now but I should make a few statements about VMWare that can help people decide which they'd prefer.

Essentially if all you want is a Windows environment on your system so you can run Windows programs from within Linux (providing this software doesn't work outside of a virtual machine on Linux) then your best bet is VMWare player with an easyVMX virtual machine build.  The reason I say this is that player provides you with a smaller footprint and cuts out a lot of the things you'll never use that are included in server.  The end result is a Windows system for all those things you just can't live without at a small cost to your overall performance.


If you want more involved development tasks or you're running a server and want to add a Windows server for some reason then VMWare server is your best bet.  The benefits of server over player are that you have a little better control over your virtual machine's settings and with server your virtual machine will continue running even if you close the program (so if you see a reduction in performance on your host machine after shutting down server you'll probably want to be sure and suspend or shutdown your VM before closing VMWare server).  VMWare server will also allow you to remotely access your VMWare environment and power up virtual machines if need be (useful if you're not allow any form of VNC or remote desktop control.

Before you attempt anything with VMware I would make sure I have a good deal of RAM as it really helps when trying to run a VM.

I kind of loosely read over this thread before posting.  If I'm repeating anybody I apologize.

---

### Post by LoKi128 on 2006-07-13
For the clock thing, check this out:

[Clock in a Linux Guest Runs More Slowly or Quickly Than Real Time]("http://www.vmware.com/support/kb/enduser/std_adp.php?p_faqid=1420")

It fixed the clock in my VM.

---

### Post by josys36 on 2006-07-14
Sure, but the post is if you are running a Linux guest. I am running a windows guest.

From what I have seen there is no perm solution for the Windows guest clock issues.

Right now this issue is just a minor annoyance since AOL radio seems to be working just fine under wine. But, it would be nice to be able to play all my audit from right inside my Windows guest. The good part is that that is my only issue. Everything else is running very well, and even sometimes better then on native Windows.

Jason

---

### Post by josys36 on 2006-08-04
I just upgraded to a T60 from my T43. The PC clock issue I was having with the T43 now seems to be gone. The T60 has a dual core CPU, and VMWare seems to love this quite a bit.

I will keep you posted as I notice other things.

Jason

---

### Post by josys36 on 2006-08-08
Well I just upgraded to a T60, and the machine is nice, but I did not know that VMWare Player does not have support for multiple CPUs. Maybe something for them to think about for the future.

Jason

---

### Post by tagra123 on 2006-09-21
> **josys36 said:**
> The issue I have with VMWare player vs server is the method to switch from the guest to the host. What I like about player is that there is a hidden menu up at the top of the guest, which you can then use to minimise the guest and go back to the host.

I'm using server because of the added options but I have to agree that the dropdown menu at the top of vmplayer is very nice and is much easier than ctrl-alt then minimizing.  I wonder if you can set up a hot-key to do that automatically.

---

### Post by josys36 on 2006-10-09
Well a new version of VMWare Player has come out and I have switched back. I liked server, but I got sick and tired of having to CTL+ALT to swich back and forth. 

So now I just use Player with single CPU support. Seems to run better then Server with a dual core CPU in Windows XP anyway.

Jason

---

### Post by austway on 2006-10-09
I just run VMWare Server in a separate workspace to my Linux applications and switch between the two as appropriate. Works great.

---

### Post by galego on 2006-10-10
> **austway said:**
> I just run VMWare Server in a separate workspace to my Linux applications and switch between the two as appropriate. Works great.

same here. after i installed VMTools i have no need to use ant key bindings to release the mouse.
(Host-Dapper 6.06; Guest-XP64/CentOS/Vista64 5600) If any one is using Beryl, unless you have an abnormaly powerful machine it would be best to log in to a regular Gnome session, you will save a ton of resources not running Beryl. and as far as fast switching, just have 4 workspaces in Gnome and switch workspaces. I love the server for one main reason ITS FREE! :shock:

---

### Post by josys36 on 2006-10-18
One thing I do love about running VMWare is that it give me a good play pen to run Edgy Eft. Since Dapper is running fine I don't really risk goofing up my main production machine. 

Jason

---

### Post by dave.dolan on 2007-08-07
well you can have your cake and eat it too... use vmware server to run your windows guest os and then rdesktop to it. That way you can push ctrl alt del, or move the mouse out as you want without any problems at all.  You could also create your vm image on vmware server, and then run vmware tools installation, then power it down and use it on a host with only the player and you'll have tools.   Two free tools, one does what you want, one doesn't so... lets just use them in the right order and then you're all ready to rock.  I personally leave my vm running as a daemon and I rarely ever use the console tool to manage it.  I don't like the vmware gui hanging around my machine, so rdesktop seems to work just fine to connect to my invisible host :) plus, whatever it's doing with the display isn't affecting my cpu load unless I'm connected to it.

What is the difference in software and memory footprint for server versus player, does anyone know? (Linux host, windows guest, for example)

---

### Post by dabl on 2007-09-02
OK, I managed to get VMWare Player v.2 installed and configured on Kubuntu Gutsy 64-bit. I have 2 different .vmx machines, that I want to install Win XP on.  But, upon opening either one, I get a "vmplayer Error while powering on: Failed to connect to peer process." message, and I cannot "grab input" with Ctrl-G, nor can I see the CD ROM drive at all.  :confused:

Has anyone beat this yet?  One of the .vmx machines worked on Ubuntu Feisty 64-bit, and the other one I just built on EasyVMX, and made sure to specify "1 CPU", so I don't think it's my 64-bit/Core 2 platform, but it may related to 32-bit libraries.

Clues?

---

### Post by dpj23 on 2007-09-02
O.K. I'm currently running VMware workstation 6 on Ubuntu 7.04 and found some of these same problems.

I would like to make these recommendations:

Your going to need VM server or Workstation to create your machines so pretty much answers that question.  Now, after building your guests you can use vmplayer to play these machines...

Time synchronization problems:  Linux host and windows guest. 
1. install vm tools and select that the quest sync's with host. ( I have found this not to hold the settings)  You try and set the windows guest to check a time server and correct this problem during your instance of running windows.


***Things to watch***

Machines created with earlier versions of Workstation, VMserver are not compatible with VMplayer 2.  So, if you haven't run into this problem yet... You will...

Machines created with workstation 6 are not platable with an earlier version of vm products... However, the reverse is...

---

### Post by dabl on 2007-09-02
Cool -- OK, thanks for the advice.

There is an older version of VMWare Player in the Gutsy repo -- I may try that first, rather than go whole hog into the workstation thing.

Appreciate the reply!

---

### Post by josh2112 on 2008-02-02
VMWare Server has gotten on my last nerve.  I am currently figuring out how to ditch it and get Player back on my machine.  Not only does it require a "license key", it refused to work at all until a couple reboots later.  My Windows XP virtual machine runs horribly slow in it... every 5 seconds or so the disk activity light will go on and the CPU activity (in the host, not the VM) will max out for a second or two.  What can it be doing?  It's not the guest doing it, that's a fresh install of Windows.  Whatever it is, it sure bogs down the rest of the computer.  Furthermore, I'm not able to change any options (even on VMs) without starting the Server as root.  That's just plain annoying.  And last but not least, no matter what combination of options I select, VMWare Server insists on doing a cold boot of the VM every time I reboot the host!  Why can't it suspend and resume the VM like VMWare player?

VMWare Server might be fine if you're in a corporate setting or running multiple VMs over a network.  But for the home user who just needs to run another OS once in a while, say for that rare Windows program, it has no advantages over Player.  It's easy enough to create virtual machines on your own:  just use QEmu to create a blank virtual IDE disk, then copy that every time you need a new virtual machine.  There are websites that will generate VMX files for you.  And you can install vmware-tools provided you're able to find the ISO online.

One thing I DO like about the Server:  Switching to the guest's native resolution on fullscreen.  Especially useful for DOS VMs and old games that must run at 640x480 or whatever ;-)

---

### Post by FrankVdb on 2008-02-03
Try VirtualBox. I like it better than the VMWare stuff. Easy GUI configuration, it just works.

Seamless integration into your Linux system. I'm running XP in a virtual machine and it only takes 7 to 8 seconds to bring it back to life from suspended mode. It's incredible.

---

### Post by noogen on 2008-02-03
> **FrankVdb said:**
> Try VirtualBox. I like it better than the VMWare stuff. Easy GUI configuration, it just works.

Seamless integration into your Linux system. I'm running XP in a virtual machine and it only takes 7 to 8 seconds to bring it back to life from suspended mode. It's incredible.

It takes me less time than that to cold boot XP in vmware server.  It could be that I am running 64 bit.

Even vmware server has problem with two processor (at least v1.0.4).  Using 1 processor will be much faster than 2 processors.  The latest vmware server (2.0) is still in beta.  VMWare player 2.0, on the other hand, is boasting to be able to do two processors (* experimental).

---

