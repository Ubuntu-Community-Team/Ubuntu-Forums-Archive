---
title: "Maple Story"
date: 2005-12-18
forum: Gaming &amp; Leisure
---

### Post by Niz972 on 2005-12-18
Howdy, well im trying to install a game called maple story.. everything works fine until i get to the install shield wizard.. and the maple story image pops up. 

> err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000001-0000-0000-c000-000000000046}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040155err:ole:CoMarshalInterface Failed to marshal the interface {00000001-0000-0000-c000-000000000046}, 80040155
fixme:ole:CoRegisterClassObject CoMarshalInterface failed, 80040155!
fixme:ole:CoCreateInstance no classfactory created for CLSID {91814ec0-b5f0-11d2-80b9-00104b1f6cea}, hres is 0x80004002


and i get an error popup that says > The installshield Engine (iKernel.exe) could not be launched. (0x80004002).

Any help..? :(

---

### Post by hampus on 2005-12-18
Try step 5 in this article:
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=2](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=2)

---

### Post by Niz972 on 2005-12-18
alright, well i downloaded the DCOM98.EXE but wheneveri enter the command > WINEDLLOVERRIDES="ole32=n" wine dcom98.exe and choose to install, it comes up with an error  of > DCOM98 can only be installed on windows 98, for windows nt please install latest service packs

---

### Post by hampus on 2005-12-18
Maybe you have to set wine to act as windows 98. I looked in the config files that existed in ~/.wine but I couldn't find anything. But maybe anyone else here has a solution?

---

### Post by Niz972 on 2005-12-18
ok, i found a way to make it install to 98, but whenever i type the > WINEDLLOVERRIDES="ole32=n" wine dcom98.exe

it shows this in the term.

> err:setupapi:SetupDefaultQueueCallbackA copy error 5 "Z:\\home\\jesse\\Desktop\\IXP000.TMP\\install.exe" -> "c:\\windows\\system32\\dcom98\\oldole\\uninstall.exe"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "Z:\\home\\jesse\\Desktop\\IXP000.TMP\\dcom98.inf" -> "c:\\windows\\system32\\dcom98\\oldole\\dcom98.inf"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "Z:\\home\\jesse\\Desktop\\IXP000.TMP\\eula98.txt" -> "c:\\windows\\system32\\dcom98\\license.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "Z:\\home\\jesse\\Desktop\\IXP000.TMP\\relnt98.txt" -> "c:\\windows\\system32\\dcom98\\relnotes.txt"
err:setupapi:SetupDefaultQueueCallbackA copy error 5 "Z:\\home\\jesse\\Desktop\\IXP000.TMP\\dcom98.inf" -> "c:\\windows\\inf\\dcom98.inf"

and when i put the next steps 
> WINEDLLOVERRIDES="ole32,oleaut32,rpcrt4=n" wine setup.exe
in.. it gives me 
> wine: cannot find 'setup.exe'

---

### Post by hampus on 2005-12-18
Are you sure you're in the same folder as your program when you run the command?

---

### Post by Niz972 on 2005-12-18
im sure

---

### Post by hampus on 2005-12-18
and the setup program you try to run is called setup.exe?

---

### Post by Niz972 on 2005-12-18
no, its MSSetup.exe
but when i type that out, it runs the program, and gives me the errors ive been trying to fix

---

### Post by Zeroedout on 2005-12-18
Try using the latest version of WINE from [www.winehq.com](www.winehq.com) . Try and install it, if it dosn't work, then try winecfg and switch it to win98, then install DCOM

---

### Post by mztriz on 2005-12-19
I followed all of the instructions on that website and got 
Game Gard initiazation error. Try rebooting and executing the game or close the program considered to cause the collision

---

### Post by mztriz on 2005-12-19
it does this ```
mztriz@ubuntu2:~$ wine /home/mztriz/Maple-Story/MapleStory.exe
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
fixme:wininet:INET_QueryOptionHelper Stub! 75
fixme:wininet:INET_QueryOptionHelper Stub! 40
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ntice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"siwvidstart.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:advapi:SetServiceObjectSecurity 0x7fe12240 4 0x7fb1f9c0
fixme:ntdll:NtCreateSymbolicLinkObject (0x7fb1fa9c,0x000f0001,0x7fb1fab0, 0x7befec68) stub
fixme:advapi:GetFileSecurityW (L"Z:\\home\\mztriz\\Maple-Story\\GameGuard\\npggNT.des") : returns fake SECURITY_DESCRIPTOR
fixme:advapi:SetEntriesInAclA 1 0x7fb1ef94 (nil) 0x7fb1ef70
fixme:advapi:SetFileSecurityW (L"Z:\\home\\mztriz\\Maple-Story\\GameGuard\\npggNT.des") : stub
fixme:vxd:VXD_Open Unknown/unsupported VxD L"procguard.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"mcnahook.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"vsdatant.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"jamilah.vxd". Try setting Windows version to 'nt40' or 'win31'.
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtQueryVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process

```

---

### Post by mztriz on 2005-12-20
[QUOTE=mztriz]it does this ```
mztriz@ubuntu2:~$ wine /home/mztriz/Maple-Story/MapleStory.exe
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"smartvsd.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
fixme:wininet:INET_QueryOptionHelper Stub! 75
fixme:wininet:INET_QueryOptionHelper Stub! 40
fixme:powermgnt:GetSystemPowerStatus (): stub, harmless.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ntice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"siwvidstart.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:advapi:SetServiceObjectSecurity 0x7fe12240 4 0x7fb1f9c0
fixme:ntdll:NtCreateSymbolicLinkObject (0x7fb1fa9c,0x000f0001,0x7fb1fab0, 0x7befec68) stub
fixme:advapi:GetFileSecurityW (L"Z:\\home\\mztriz\\Maple-Story\\GameGuard\\npggNT.des") : returns fake SECURITY_DESCRIPTOR
fixme:advapi:SetEntriesInAclA 1 0x7fb1ef94 (nil) 0x7fb1ef70
fixme:advapi:SetFileSecurityW (L"Z:\\home\\mztriz\\Maple-Story\\GameGuard\\npggNT.des") : stub
fixme:vxd:VXD_Open Unknown/unsupported VxD L"procguard.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"mcnahook.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"vsdatant.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"jamilah.vxd". Try setting Windows version to 'nt40' or 'win31'.
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtQueryVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtProtectVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process
err:virtual:NtAllocateVirtualMemory Unsupported on other process

```[/QUOTE]
:confused:

---

### Post by Mr_J_ on 2005-12-23
Why don't you try setting the windows version to nt40 or win311?
It says so right there...

It's most likely a bug in the game!
Try to set wine to windows XP. This would ne Windows NT 5.1 or something.

Also looks like there is a problem in the allocation of virtuall memory.

By the way! How did you even download the thing?
I try to open the site and it tells me to use Internet Explorer.
WTF is up with that?

---

### Post by starscalling on 2005-12-24
you know you can set your browser to emulate ie to web

---

### Post by mwaddoups on 2006-01-13
bump.

Has anyone actually got Maple Story working in Ubuntu, or any kind of linux?

---

### Post by akurashy on 2006-01-13
MapleStory won't run because GameGuard is NOT supported yet, so it just going to be a pain trying to run it. though i don't know if there is a way to skip it . I tried running it and well I reported it to winehq.com to see what was wrong and they said gameguard is not supported.

---

### Post by Kuronori on 2007-02-09
I can tell you why you can't run MapleStory on Linux. 

in the last post it says "gameguard isn't supported yet" and I doubt it ever will be because of the simple fact that game guard is, simply put, a rootkit.

It's designed to detect hacking attempts but exploiting the windows kernel and monitoring other threads, and when it finds these hacking attempts it will reboot your winblowz box or give you everyones favorite, a BSOD

if you have a winblowz dual boot or virtual machine give it a try n run a rootkit scanner like IceSword n look at your kernel modules. You'll see a big fat npkcusb.sys and npkcrypt.sys but thats just the stuff they use to scan your winblowz box's running processes then encrypt the log file n send it to the people at nProtect.

The real sneaky stuff happens when you run MS and it creates GameMon.des secretly then in your your winblowz System Service Descriptor Table it sinks in it's nasty little rootkit fangs n jacks a few kernel services which include NtWriteVirtualMemory, NtReadVirtualMemory, NtProtectVirtualMemory, NtOpenProcess, and NtDeviceIoControlFile but are not limited to these.

[COLOR="Black"][FONT="Arial Black"][SIZE="4"]Long story short, you need GameGuard to run or MS won't, GameGuard is a windows rootkit trying to hack an emulated windows os on a linux box, GameGaurd can't so it won't run, so no MS
[/SIZE][/FONT][/COLOR]

So, the question is, do you want to be rootkit-ed today? If so, switch back to winblowz. It sucks but yeah.

---

### Post by oo-boon-too on 2007-02-11
I have been against the game guard programs from the day i found out what they did. My question is: How are they considered legal?

---

### Post by Praill on 2007-02-28
Yes, as the above poster described, maple story will not run in wine since gameguard somehow actually modifies the windows kernel :S

However I have had some very minor success with Maple Story, in that I've gotten past the Game Guard (dont get your hopes up its not working yet).

You can run an windows emulation with a, now open source, project called VirtualBox. It creates a virtual drive on your linux partition and will install any os you like onto the virtual drive. Everything seems fine except, for some strange reason, the **2D** game Maple Story insists on using **3D** rendering and VirtualBox video drivers dont yet support 3D acceleration.
To me, this is just another tick on the list as to why Maple Story is the most horribly supported, narrow scoped mmo available.

However, keep your eyes open for a new version of VirtualBox's guest addition drivers that will support 3D acceleration.

For a guide to install VirtualBox yourself if you want to try it (it wont work) you can go here:
[http://flyff.gpotato.com/phpbb/viewtopic.php?p=2696013](http://flyff.gpotato.com/phpbb/viewtopic.php?p=2696013)

---

### Post by Praill on 2007-02-28
I finally figured it out, and have it running in Edgy.
I wrote up a little how-to since one doesnt exist on these forums.
You can find it here:
[http://www.ubuntuforums.org/showthread.php?t=372928]("http://www.ubuntuforums.org/showthread.php?t=372928")

---

### Post by Hansuonu on 2007-03-28
hi i have prob..... HOW U GET TO DL MAPLE STORY ???? it need IE but IE is only for Windows  and we are talking in Ubuntu forums and i more question ubuntu can open a .exe files...??

---

### Post by el mariachi on 2007-03-28
use [IES4LINUX]("http://www.tatanka.com.br/ies4linux/page/Main_Page")
then istall IE6 and download MS. from then on use the HOW-TO

---

### Post by Hansuonu on 2007-03-28
ok TY for Linux IE

---

