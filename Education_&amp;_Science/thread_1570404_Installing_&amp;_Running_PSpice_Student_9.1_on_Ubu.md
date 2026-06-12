---
title: "Installing &amp; Running PSpice Student 9.1 on Ubuntu Lucid"
date: 2010-09-08
forum: Education &amp; Science
---

### Post by sdaau on 2010-09-08
Hi all, 

While there are a lot of threads that deal with installing this old software under Wine, I had quite a bit of troubles before success. So here are the steps that worked for me (Ubuntu 10.04 lucid, and wine-1.2 from [ubuntu-wine PPA]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")): 
```

# uninstall and clean up wine completely:

sudo apt-get remove --purge wine winetricks    # not enough, needs also:
sudo apt-get remove --purge wine1.2            
sudo apt-get autoremove --purge             # for wine1.2-gecko etc
ls -d /home/administrator/.wine*  # shows: .wine/ .winetrickscache/
rm -rf ~/.wine*

# install wine 
sudo apt-get install wine # installs winetricks, wine1.2-gecko

# run wineconfig, and set win 98 mode
winecfg 

# run winetricks and install dependencies
# note: mfc42=vcrun6
winetricks corefonts dcom98 mfc42


# run wineconfig again, and under 
# 'Libraries', set rpcrt4 to "built-in" - NOT 'native';
# else installer will crash @ 'Call from 0x7b836852 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting'
winecfg 

# now run the Pspice installer
# install Pspice in a dir without spaces; 
# for example /home/user/Orcad_Demo
# that will be Z:\\home\\user\\Orcad_Demo for wine
cd ps9_1/
wine Setup.exe

# Install should be done now, 
# programs may start, but without simulation

# check whether dll's have been registered in wine registry:
grep 'ipspice' ~/.wine/*.reg
grep 'sim' ~/.wine/*.reg
grep 'pspi' ~/.wine/*.reg

# check if PSPICEEV.INI is installed
$ ls ~/.wine/drive_c/windows/

# run wineconfig YET again, and under 
# 'Libraries', set ole32, oleaut32, rpcrt4 to "built-in" - NOT 'native';
winecfg 

# check if by any chance multiple copies of SIMSRVR.EXE have been started;
# if so kill them
ps axf | grep -i 'sim'
sudo killall SIMSRVR.EXE

```After this, you shold be able to at least start pspicead.exe and run a simulation, and "PSpice Design Manager" should work too. 

The nastiest bit was the fact that one must set rpcrt4 to "built-in" to have the installer run; this quote was relevant: 

[WineHQ Forums View topic - RPCRT4.dll and NTDLL.dll]("http://forum.winehq.org/viewtopic.php?p=34993&sid=2abf24f78d60ed9dc012a209445d3463"):
> **"http://forum.winehq.org/viewtopic.php?p=34993&sid=2abf24f78d60ed9dc012a209445d3463"]
Jcrash wrote:
wine: Call from 0x7b843942 to unimplemented function rpcrt4.dll.NdrClientInitializeNew, aborting

This means you can't use native rpcrt4.dll from dcom98. WINE NEEDS THINGS THAT DIDN'T EXIST IN WIN98.

Jcrash wrote:    
So I enabled ntdll tracing and see the following files not found, gonna try to track these down -    

All of those are normal.

Jcrash wrote:    
so after copying over the rpcrt4.dll from me windows xp partition along with the files above i get this crash any ideas?    

It won't work in most cases. IT RELIES ON LOTS OF UNDOCUMENTED INTERNAL FUNCTIONALITY WINE DOESN'T NEED / IMPLEMENT.

In simple words - if it something related to OLE and dcom98 didn't help - it won't work unless Wine's OLE is fixed.
[/quote]

I'm not sure if setting those libraries to "built-in" after install helps, but that's how I have it right now. Basically, I ran once after install, and sim failed (*when simulating, got "pspicead.exe cannot be started" - and when running it manually, got "Failed to connect to the PSPice Simulation Server"*) said:**
> 
[*] [Run PSPICE in Wine - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=550991") (mentions 'regsvr32 *.dll')
[*] [Issues with OrCAD 16.2 demo version - Cadence Community]("http://www.cadence.com/Community/forums/p/13142/21800.aspx#21800") (post @ Sun, Oct 11 2009 8:59 PM - I think this syntax may be better than calling 'regsvr32' directly)
[/LIST]


Well, hope this helps someone, 

Cheers!

EDIT: Note that even with this, there will still be a problem placing parts in OrCAD Capture (PSpice Schematic should be fine), described in [WineHQ Bugzilla &#8211; Bug 3023 &#8211; Orcad - "Place Part" never tries to put down a part]("http://bugs.winehq.org/show_bug.cgi?id=3023"):
[quote="http://ubuntuforums.org/showpost.php?p=3957310&postcount=6"]
There is a temporary solution to the "Placing Parts" problem. Hopefully it will be included with wine updates in the near future.

Here is a link to the bug:

[http://bugs.winehq.org/show_bug.cgi?id=3023](http://bugs.winehq.org/show_bug.cgi?id=3023)

Unfortunately it requires recompiling wine. I will see what I can do about creating a modified deb package.

.. however, if you have an existing Capture project, you can copy any parts that exist there and paste into a new project without problem.

---

### Post by GridLynx on 2011-04-26
Excelent Post ! I was about to post something related to not findign an equivalent to Microsim/Orcad but i am so going to try this now...

My main problem was trying to make a new directory to store my project in ( it wouldn't allow it) and of course, problems with osciloscope simulator.

At any rate, great contribution!

---

