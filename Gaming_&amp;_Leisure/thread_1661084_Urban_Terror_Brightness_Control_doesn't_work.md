---
title: "Urban Terror Brightness Control doesn't work"
date: 2011-01-06
forum: Gaming &amp; Leisure
---

### Post by SVEN1 on 2011-01-06
Installed Ubuntu 10.04. When starting up Urban Terror, it's too dark. Any maps are like playing at dusk. The Brightness slider control does not work.
I am running a ATI Radeon xt1900xtx video card. Had no problems in earlier versions of Ubuntu with brightness.

Any ideas on how to fix, short of getting a new video card?

---

### Post by Jim_in_Omaha on 2011-01-08
Mine works in full screen mode only and when I task switch to desktop it's gamma is turned up also until I exit the game.

In windowed mode it does nothing.

---

### Post by SVEN1 on 2011-01-10
> **Jim_in_Omaha said:**
> Mine works in full screen mode only and when I task switch to desktop it's gamma is turned up also until I exit the game.

In windowed mode it does nothing.

Doesn't matter if I am in full screen or windowed mode. still dark. I even tried re-installing it several times. I can play the brighter maps if I am on the blue team, the red team is easier to spot.

Would like to get this resolved.

CrossBones UT ID

---

### Post by _outlawed_ on 2011-01-10
Same issues here on 10.10. Tried some of the work arounds on the UrT forums, but none worked for me (compiz/metacity, manually settings r_gamma higher, etc).

So far I've been getting by by manually adjusting my monitors brightness via it's button controls, but that is a hassle having to do that everytime. :(

EDIT; Forgot to mention specs. Ubuntu 10.10 64bit with ATI Radeon HD 4200. Yes I know ATI sucks, but I can play UrT at ~95FPS easy on max settings.

---

### Post by space_cadet on 2011-01-11
> Same issues here on 10.10. Tried some of the work arounds on the UrT forums, but none worked for me (compiz/metacity, manually settings r_gamma higher, etc).

Strange that I should stumble across the very same issue one day later, but I too have tried all of the above (compiz vs. metacity, r_ignorehwgamma, r_gamma, r_intensity, disable gnome desktop effects) before I came here - to no effect. 

Help?

Edit: Intel GMA X4500HD, Ubuntu 10.04

---

### Post by SVEN1 on 2011-01-16
Semi solved the brightness problem. Ran the Windows version in the latest version 1.3 Wine. 
Still have one issue to resolve now.
I have a slow internet conection 3mbs and frame rates are down to from 85 (when I had a faster connection) down to 35-59-80 with lag. Makes it tuff to play. Hopefully will upgrade once again to the faster internet that we once had 10mbs.

---

### Post by Jim_in_Omaha on 2011-01-16
> **SVEN1 said:**
> Semi solved the brightness problem. Ran the Windows version in the latest version 1.3 Wine. 
Still have one issue to resolve now.
I have a slow internet conection 3mbs and frame rates are down to from 85 (when I had a faster connection) down to 35-59-80 with lag. Makes it tuff to play. Hopefully will upgrade once again to the faster internet that we once had 10mbs.

Well I know this much from my experience:

Your internet speed is not the issue. I have a 1.5mb DSL and I wish I had 3mb service. I ran into major lagging problems with wireless connection to the router. 

If you direct connect to the modem does it work better?

What I did to fix my wireless is I put in a new DLink wireless 'N' card with the Atheros AR922X chipset (lspci info) and using a 'N' Netgear router hooked to the DSL modem/router. It works almost as good as direct CAT5 cable.

As far as the FPS goes, I have a Q9450 cpu with a NVidia 9800GT and it will maintain close to 125fps on a Asus 26" monitor at 1920X1200 res with everything set high. The only time it start to drop down is with lots of smoke going on. It may get to 85fps.

I also am using the new optimized 64bit ioq-urt native version of Urban Terror that can be downloaded here:

[http://www.www0.org/w/Optimized_executable;_builds_of_ioq3_engine_for_urt]("http://www.www0.org/w/Optimized_executable;_builds_of_ioq3_engine_for_urt")

---

### Post by sudo_0 on 2011-01-16
[]("http://www.www0.org/w/Optimized_executable;_builds_of_ioq3_engine_for_urt")same issue with the screen brightness...

anyone else also get Nternet spiking really hard??? ping all over the place... like 80-300-65-250-125-40... tried resetting router... restarting computer.. i'm the onlyone on my network... strange

thanks in advance to whoever miracles this one. :)


__________________________
Macbuntu [Macbook 5.1] Linux only
Ubuntu 10.10 Maverick Desktop 
Intel Core 2 Duo (2.4Ghz x2)
2GB ddr3
kernel 2.6.35-24 gen.

---

### Post by Jim_in_Omaha on 2011-01-16
> **sudo_0 said:**
> []("http://www.www0.org/w/Optimized_executable;_builds_of_ioq3_engine_for_urt")same issue with the screen brightness...

anyone else also get Nternet spiking really hard??? ping all over the place... like 80-300-65-250-125-40... tried resetting router... restarting computer.. i'm the onlyone on my network... strange

thanks in advance to whoever miracles this one. :)



Have you tried direct connection with ethernet cable to the router?

---

### Post by SVEN1 on 2011-01-17
I have a direct connection thru Cogecos router same lag and low fps.
Doesn't matter if I use the direct connection or thru direct connection from the wireless router. I don't use wireless on my desktop.
Thought about switching video cards

---

### Post by SVEN1 on 2011-02-09
So thought I could solve my brightness problem with a diff video card, found a nice used XFX 9600GT. Removed the ATI x1900xtx popped in the XFX.
Got the computer up and running with the new card. 

By the way added a Coolermaster PCU cooler which solved my lag problem and FPS problem.Playing UT drove my CPU up to 97C, using this cooler drops it down to 30C. I'm right up at 95fps again.

As for the brightness problem the 9600 did not solve it. Even tried downloaded and reinstalling UT several times. Still no change.

Well will just have to resort to playing UT in Virtual Box Windows.

Did decide to try a couple different shooting games. Game Cube and Sauerbraten in Ubuntu 10.04 They work just fine.

---

### Post by liamuk on 2011-02-09
for the brightness problem, i use a bash script in the urt directory to start urt:

#!/bin/bash
xgamma -gamma 1.2
./ioUrbanTerror.i386
xgamma -gamma 1

---

### Post by SVEN1 on 2011-02-11
> **liamuk said:**
> for the brightness problem, i use a bash script in the urt directory to start urt:

#!/bin/bash
xgamma -gamma 1.2
./ioUrbanTerror.i386
xgamma -gamma 1

can you explain exactly how to do that? Thanks

---

### Post by liamuk on 2011-02-11
Basically you just create a new bash script with what I posted. Open up mousepad, paste what I posted, 

> **liamuk said:**
> 
#!/bin/bash
xgamma -gamma 1.2
./ioUrbanTerror.i386
xgamma -gamma 1

and save it in the directory the ioUrbanTerror executable is. Instead of starting UrT by running the executable, just run the script. It will change the brightness from 1 to 1.2, and then change it back to 1 when UrbanTerror closes. If you want to make it even brighter, just change 1.2 to a higher value.

---

### Post by sgtslwilson on 2012-02-16
Having the same problem in Natty. The solution worked somewhat....but is still unacceptable for serious play. I don't think this is an Ubuntu Issue but probably a UrT issue.

Still has not been solved.

---

### Post by SVEN1 on 2012-03-01
I just run UT in Wine have no problem adjusting brightness there.
I don't play much any more as I find no one else does and most of the servers are arun with bots. Not interested in playing against bots.

Bought an Xbox and play there now (not UT).

---

### Post by synaptix on 2012-03-04
This has been an issue in UrT for Linux for the longest time now. I just usually increase my monitors brightness manually to ~50%-65% depending on the map. It's quick easy solution (muscle memory).

I'm hoping FrozenSand fixes this issue in the next version of UrT.

---

