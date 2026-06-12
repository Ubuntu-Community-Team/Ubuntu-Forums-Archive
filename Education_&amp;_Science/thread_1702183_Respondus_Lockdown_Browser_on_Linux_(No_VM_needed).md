---
title: "Respondus Lockdown Browser on Linux (No VM needed)"
date: 2011-03-07
forum: Education &amp; Science
---

### Post by torrentfreak on 2011-03-07
_**Lockdown on Linux**_
It really is possible, and _without a virtual machine!_

This program is challenging to say the least, as it can detect if it's  being run in a virtual machine. Therefore, a way around the  compatibility problem had to be found without utilizing a virtual  environment.
Here's the guide I found to get it running on WINE and remember to follow it **closely**! It worked for me, running Ubuntu 10.10, and a friend running another distribution. 

[http://themadhacker.net/lockdown](http://themadhacker.net/lockdown)

I didn't have to dual-boot or install a virtual machine; all i needed was to do some tweaking and investigating of my school's ID number and *voila!* it worked. I can now take my online quizzes from my computer, running linux (and nothing else!), and not have to suffer the Lockdown's *side effects* like disabling open windows and the like. Good luck and I hope this helps!!

---

### Post by psytrox on 2011-06-08
That source is not available.  Any mirrors, or a list of steps out there? Thanks.

---

### Post by kd7skx on 2011-06-10
Any one else have the instructions on hand, the link above is broken.  Thanks

---

### Post by imnichol on 2011-10-08
Yeah I'm kind of curious about this, since I was under the assumption that respondus used code natively compiled for Windows/OSX.

---

### Post by ClientAlive on 2011-11-13
This is a really big deal. Lock down browser not being available for Linux puts people in a very difficult (and I think, unfair) position. I really, really, really - hope some solution is made available for this. The experience has been absolutely excruciating!
------------------------

Edit:

> **imnichol said:**
> Yeah I'm kind of curious about this, since I was under the assumption that respondus used code natively compiled for Windows/OSX.

Wine (what the original poster mentioned) is software that allows one to run Windows programs on Linux, but it isn't perfect with every single Windows program. Lock Down browser is one of them. When I tried to run it under Wine it did not work. A more experienced person may be able to make the tweaks necessary to get it to work in Wine; but as for myself, I would need to be guided.

And yes, the link in the original post is not good.

---

### Post by boblizar on 2012-02-03
this post is a MESS please test building wine up and leaving elements of this post out and report back to further refine what is going on.  im 100% positive that this is over kill and im installing things that i do not need.(ESPECIALLY in the wine tricks department)  (though it is setup and APPEARS working with all this excessive garbage installed.  some of the install dialogs are fixed, and some of the install dialogs are still blank... so just be aware of this) (ppa:ubuntu-wine/ppa to get new wine to try to resolve moar errors regarding old winsock support and excessive winsock errors this PPA comes with winetricks to make your life easier)

ala googles page cache feature....

```
Lockdown Browser on LINUX!
posted by themadhacker on Mon, 12/26/2011 - 10:53
Image: 
Body: 

Lockdown Browser has given many Linux users trouble, given Respondus' false claims about LDB not being able to be run in any environment but Windows.

 

Folder - Site.png

STEP 1: Get WINE  2.3 [or latest version] and install. 

STEP 2: Find your school's LDB code. The code can be found at the download page that your school directs you to; the url will also contain your school's ID in the format "http://www.respondus.com/lockdown/informationb.pl?ID=451214388" where ID=451214388 is the information you need.

STEP 3: Download and unpack in an archive manager.

Inside of the archive (LockDownSFX.exe) there are two folders, the "id.txt" file you need will be in a folder like "/tmp/z451214388_26122011-121119-71/". 

STEP 4: Edit the line that is "<451214388>" for this example, keeping your school's code in between the brackets

STEP 5: Install and Run via WINE set to "WINDOWS 7" settings.
```

i have installed wine tricks to install DLL's recommended on wines page to run this.  to do wine tricks....

ala wine hq's instructions to install
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)
then when you run winetricks your going to want to select the default prefix, hit ok...

then install a windows dll hit ok...

then scroll down to mfc42.dll and install (and first try for me this was really choppy no text shown.  im going to try mfc40.dll and actually reboot this time.)

im inserting the link to windows latest java as per this posts date...  i might have to wine tricks flash up on there too....  [http://javadl.sun.com/webapps/download/AutoDL?BundleId=58124](http://javadl.sun.com/webapps/download/AutoDL?BundleId=58124)  my schools having black board problems so it might work with out this, and this is freaking wine out anyways.  it will not install and im not going to get all persistent about it just yet.

im going to wine the windows version of java and see if it resolves errors later on in this post.

then download the stupid lockdown browser from your schools directions / link because your lock down browsers link code will be different.

and as before its missing some fonts so i can only read like 1/4th the install dialog, but can guess my way to installed.  im getting tons of errors
```

fixme:advapi:GetCurrentHwProfileA (0x33fbc8) semi-stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x12bb00, filter=0xe6e9d4,flags=0x00000001) returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79e5dc,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x128328,(nil)): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x79e970): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x79e9a8): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79e5dc,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x128328,(nil)): stub
fixme:service:EnumServicesStatusW 0x1285f0 type=30 state=3 (nil) 0 0x79e7d0 0x79e7d8 0x79e7cc
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79e5dc,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x128328,(nil)): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x79e694 0x79e68c
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:ole:CoCreateInstance no instance created for interface {ea1afb91-9e28-4b86-90e9-9e9f8a5eefaf} of class {56fdf344-fd6d-11d0-958a-006097c9a090}, hres is 0x80004002
fixme:shell:IShellLinkW_fnGetPath (0x152d60): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkW_fnGetPath (0x152d60): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkW_fnGetPath (0x10e6c50): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkW_fnGetPath (0x10e6c50): WIN32_FIND_DATA is not yet filled.

```

so it looks like i gotta install some things to wine yet.  probably wininet in wine tricks (since this is a browser after all)

i installed fontfix && corefonts && liberation && uff && unifont, now my font problems are half way resolved and i can read the install dialogs.

some of the official microsoft fonts stall for my wine tricks....  i simply take the link from the output, and download the file via browser / firefox / seamonkey / opera...  then locate the file to the folder that wine tricks wants to wget the file to...  example

download this
[ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT40TSE/hotfixes-postSP3/Euro-fix/eurofixi.exe](ftp://ftp.microsoft.com/bussys/winnt/winnt-public/fixes/usa/NT40TSE/hotfixes-postSP3/Euro-fix/eurofixi.exe)

then sudo mv $HOME/Downloads/eurofixi.exe $HOME/.cache/winetricks/lucida

then re wintricks the lucida font....

back to the subject at hand, respondus does not like windows xp mode.  im going to have to dig out where to set it to windows 7 mode...

&& located

/usr/bin/winecfg

bottom of the dialog that pops up is windows 7 mode

in shell execute

wine $HOME/.wine/drive_c/Program Files/Respondus\ LockDown\ Browser/LockDown.exe

it will load the browser, but wont load my schools web stuff, probably because of requiring flash/java to access blackboard. or my school maintaining blackboard right now....

---

### Post by ClientAlive on 2012-02-04
Hope I'm not off base here, not sure if it's of any help but sun java can be installed directly onto Linux.

[http://ubuntuforums.org/showthread.php?t=1876671](http://ubuntuforums.org/showthread.php?t=1876671)

skip post 5

---

### Post by boblizar on 2012-02-05
you need a windows version of java for wine to access....  regardless this program loads, but does not load content....

---

### Post by fourdigit on 2012-09-14
I don't think this should be marked as SOLVED, because the above instructions don't let me use Lockdown browser.

---

### Post by sammyjk on 2012-09-23
I installed Respondus through WINE in 12.04, then changed the settings to Windows 7, and fallowed only part of the tutorial above (error message sidetracked me), tried opening it again, just for who-whos and ha-has and it opened no problem. I can still see the unity dock though, and the browser is of course full screen, can still switch between workspaces and even browse the web. Not sure if the winetricks did anything or if just changing the settings did the trick, but it's working and I'm not complaining.:popcorn:

---

### Post by wrkrbee1650 on 2013-05-11
I have installed Wine, and set it to run as Windows 7.  When I run the setup.exe from /home/username/respondus/ldb-setup/ location,
the error I get is:

"Institution ID has not been set correctly for this install.  Please see readme.txt for the necessary customization step"

I obtained the school ID as instructed.  I also noted that upon download the first 9 characters are also the same numbers.

Perhaps what I screwed up was:

Inside of the archive (LockDownSFX.exe) there are two folders, the "id.txt" file you need will be in a folder like "/tmp/z451214388_26122011-121119-71/".   STEP 4: Edit the line that is "<451214388>" for this example, keeping your school's code in between the brackets

Because when I found id.txt it already had the ID in the file in "<>", so I didn't know what to edit or the purpose of editing.  

So far I have been unable to find my issue anywhere.

UPDATE: 

Not sure what I did differently, but now I was able to get the LockDownSFX.exe to run (instead of setup.exe) but....when I try to run

wine LockDown.exe, I get the error:

wine:  cannot find L"C:\\windows\\system32\\LockDown.exe"

Perhaps I can fix this by copying it to the hidden drive?

---

### Post by jwfox on 2013-06-05
> **sammyjk said:**
> I installed Respondus through WINE in 12.04, then changed the settings to Windows 7, and fallowed only part of the tutorial above (error message sidetracked me), tried opening it again, just for who-whos and ha-has and it opened no problem. I can still see the unity dock though, and the browser is of course full screen, can still switch between workspaces and even browse the web. Not sure if the winetricks did anything or if just changing the settings did the trick, but it's working and I'm not complaining.

I've got the program running, and appeared to be working OK, but it ignores clicks on a lot of the school's website. Don't know if that's normal behavior for respondus or not. But the quiz list is trapped in a small space with scrollbars that won't resize and I can only view one line at a time. Also, clicking on "Start Quiz" does nothing as far as I can tell.

Hmmmph. Will probably just have to borrow my wife's notebook to do the quizzes.

---

### Post by jwfox on 2013-07-01
OK, now it looks to be working almost perfectly.

One minor glitch: tab key doesn't work to jump from username field to password field, and I have to actually use the mouse to click in the password box. I presume the tab key probably won't work elsewhere in the browser either, but it's not something I'd really ever use while taking quizzes or exams. Other than that, everything appears to be working flawlessly. It did require the use of a windows box to get it set up, though. Or more accurately, a virtualbox running Win7. Whatever.

What I did:

Installed through PlayOnLinux. Set to run as Win7 (oddly, when set to run as XP it complains about compatibility mode not being allowed). Program runs at this point, but not well enough to be usable.

In the Win7 VM, installed Sandboxie. Downloaded the copy of Respondus from the link on my school's website (already has the ID and automatically loads the schools page). Installed Respondus under Sandboxie. Export all files, and copy them into the Repondus folder in the PlayOnLinux drive.

Won't run in the VM, but works under Wine. Go figure.

---

### Post by 666threesixes666 on 2014-07-01
im glad you guys got lock down browser working, i also seen the blank content of my schools systems.  unfortunately my grades were bad enough to be financially ostracised from ferris state university.  i had written all of that up for circuits.  im pretty sure i lost boblizar from the password leaking thing.  i moved over to gentoo then ultimately funtoo, and learned how to edit wiki so i could tutorial in a more proper setting.  i promise to return to document installing gentoo and funtoo from ubuntu's excellent live media.

      -three sixes

---

