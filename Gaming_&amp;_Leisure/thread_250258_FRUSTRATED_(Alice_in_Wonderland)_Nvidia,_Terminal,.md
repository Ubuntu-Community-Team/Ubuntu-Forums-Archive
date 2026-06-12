---
title: "FRUSTRATED (Alice in Wonderland) Nvidia, Terminal, and other adventures..."
date: 2006-09-03
forum: Gaming &amp; Leisure
---

### Post by roboghast on 2006-09-03
ok, I'm not a noob to gaming. I am old, 45 but I like to game. I played Asheron's Call from beta, Daoc, AC, Ultima online, WOW and Shadowbane I like wolfenstein and America's army.

I have a alienware dual core 3 mghz 1 gig mem with nvidia 6800 yada yada...

Well I am really frustrated. I have completely given up on Windows and have come to Ubuntu. I'm a noob to Linux, sure. But finding information to tweek the system for games is really tiresome. You search the "community" and the help doesn't fit your system, like I did a nvidia search but all I found was about a "legacy" thing or the XGL thing. OR the thread is 180 posts long the majority saying 

"Try this"

"I Did - it don't work"

Then sudo this Hoodoo

"nah that just maed the screen go blank.."

Etc. 

Don't get me wrong I'm not flaming just venting my frustration about getting some concrete, consise, step by step information. 

Hmm looked at Wine - found out how to install it - got it off a repository I think - but I couldnt find it in the menu - gave up on that after reading the posts - sounds too much for me now..

Gaming Attempt 1 - Planeshift - hmm it looked cool "let's try to install that!" Downloaded it -  took me a day to figure out how to install it. Searching the forums never gives you the exact information you need. The searches always give you ambiguous information not specific to your problem. Either its incomplete, or they are talking about Warty or sumthin else. 

after a few days - and many attempts -- Got Planeshift installed - but all the files were locked! heh, how can I install something then not be able play it? (you know,  I don't) - ok let's uninstall and start over - hmm they are locked can't uninstall it. well.. look for an hour or two to find out how to get permission. oh I found it - but there are 4 files that will not delete - hmm ok I put them in trash can, they are still there to this day...(or they were there until I messed up my desktop GUI trying to get the games running with commands I cut and paste from the forums.then had to do a clean install, which deleteed all the firefox bookmarks I had from the forums ugh) 

after searching the forums to try to figure out how to do the run file thing I got it installed!!- cool my first game!! - installer is running!! -- Icons on my desktop!!! click on Icon -- nothing happens.... no flicker, no nuthin. hmmm... search forums... nuthing about *"Planeshift - I got the icons up, the game is installed but it won't start"* topic -- ok I give up on that one...


[COLOR="Red"]OK lets forget about planeshift - lets try something more popular...[/COLOR]

**Attempt 2** - America's Army - ok - cool they have a linux download! this should be easy! (muhahaha) download the file try to run it - hmm open in the terminal - it doesn't work. read forums. It doesn't want to install. Its a run file. I tried a day to get it to work - eventually gave up. 

**Attempt 3 **- Wolfenstein ET, my latest attempt! ok tried to install it - nothing happens. Read forums. currently I forgot which sudo and nano and other things it took to get it installed but it installed! Thats one thing about those terminal commands, I can't remember what I did or what forum post I got it from...after I did it

ICON IN MENU WOOT!! 

Click menu Icon -- SCREEN FLICKS - nothing happens...a sad feeling comes over me... (kinda like my old 1962 ford pickup I had) try again - Screen Flicks nothing happens -- OK read more forums - read read -- oh maybe its my Nvidia drivers! after all I had to update drivers all the time on Windoze!! ok cool found a post entitled "XGL Install and General Tips For Gnome and Nvidia" COOL general tips! thats what I need for my Nvidia -- went through it - crashed my desktop GUI - it was actually the instructions for the XGL - did it twice first time it farted my GUI funky terminal character popped at bootup told me I configured everything bad or sumthin. SO I HAD TO reinstall everything - cause I didn't know how to undo it. 

Tried this a second time a few days later - same thing happened this time I sorta understood the nano gedit on the things file. so I erased the one file that changes things (the configuration file I think) and it restored my system to the desktop when I booted up - well at least I didnt have to reinstall 

read more forums tried some tweeks here and there and W00T!! Wolfenstein starts BUT...BUT....BUT... its running so slow it the introduction movie is like a slide show. The sound and graphics move every 3 seconds!  weeee!!! fun fun the mouse too! Got.. too....move....real....slow...too...get....to...the....exit....button...

exit game.

hmmm ok must be sumthin with my drivers... so I check out the driver file thing. xorg.conf (xorg X Window System server configuration file) - yea I learned about this the past few days...to me its mumbo jumbo - it looks ok I guess. hard to tell since I can't find any information about what its supposed to be set at... 

ok maybe lets try Nvidia webstie!!!! yea thats it - lets go to the newest driver things...go to website -- coool! they have linux driver in a file -  [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

and which one? there are four hmm I am not solaris I think... Im not BSD (even though that sounds dirty) hmm Im not a 32 bit - must be that Linux IA64 file -- hmm whats the IA mean? open it!! -- woot! I push download - firefox opens it like a web page and I get what looks like script!! LOL no file is downloading -- hmm am I supposed to cut and paste this?? the thing is like 20 pages long! LOL

this is it:
! /bin/sh
skip=642
CRCsum=3232997086
MD5=1cb347a27c40e73f2d12b16bdf961a1e
label="NVIDIA Accelerated Graphics Driver for Linux-ia64 1.0-5336"
major_version=1
minor_version=0
patch_version=5336
pkg_version=1
script=./nvidia-installer
targetdir=NVIDIA-Linux-ia64-1.0-5336-pkg1
scriptargs=""
keep=n
add_this_kernel=
TMPROOT=${TMPDIR:=/tmp}
TARGET_OS="Linux"
TARGET_ARCH="ia64"

#
# NVIDIA Accelerated Graphics Driver for Linux-ia64 1.0-5336
# Generated by Makeself 1.6.0-nv
# Do not edit by hand.

yada yada 

now where to put this? who knows. 

OK thats me so far - I have come to a conclusion: 

**LINUX IS A GAME!!!** Best one I have tried so far!! It's puzzling! Strategic! I can role play a frustrated hacker! Its educational!! It is keeping me captivated, each problem is a quest!!! And when things work!! excellent gratification!! Its kept me occupied now for a week and I haven't given up! Don't plan to. And you don't give up either. Maybe there will be some sticky threads on how to install these games but for now - I'll just have to keep at it. 

SO you don't need to reply - really,  I probably won't be able to find this post again or forget about it since I will be occupied trying to figure out why my uber gaming computer won't dance. 

Yours 

roboghast
(Mossy in WOW, Lannick and Moosh in Shadowbane, Thorvard and ogus in others)

---

### Post by em3raldxiii on 2006-12-25
I am thinking #ubuntu and #ubuntu-offtopic would be your friend.

Let's pretend you have no idea what that is.  It is an IRC (Internet Relay Chat) channel specifically taylored to helping folks like you *IN REAL TIME*.

So, we'll see if we can find a simple "how-to" to get you using the channel, and then I think you will be one extremely happy camper.

In the meantime (until I or someone else can come up with a super slim and easy way of connecting to the IRC channel), do a few searches about it and see if you can figure it out.  The only reason I am telling you that, in light of your recent adventures, is that it is the fastest way to learn how to get the most out of your Ubuntu.  Until the developers make stuff a little more point-and-click. :D

---

