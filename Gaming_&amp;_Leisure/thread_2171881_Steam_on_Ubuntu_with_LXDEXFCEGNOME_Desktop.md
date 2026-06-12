---
title: "Steam on Ubuntu with LXDE/XFCE/GNOME Desktop"
date: 2013-09-02
forum: Gaming &amp; Leisure
---

### Post by michael-jstc on 2013-09-02
I'm 17, and I've just recently started dabbling in Linux, and right now I'm running off of Ubuntu 12.04 from a 32GiB Sandisk. I can boot from the thumb drive on any computer I come into contact with. Right now, I'm having a problem. I was getting annoyed with the default Unity desktop, so I installed Gnome, LXDE, and XFCE, just to try out different control methods. As of yet, I prefer the LXDE desktop, as it is best organized, but I noticed a couple of drawbacks. Primarily, when I try to start steam, it just comes up with a message that looks just like the steam update window, but instead of "Updating Steam," it used to say "Updating %appname%." and disappears almost immediately. It still disappears, but what it now says is in the screenshot. I have to be in Unity to use it, and this severely slows down the computer when I try to play a game, even one like Psychonauts. It doesn't even work in Gnome. Secondly, there's a problem with the volume control in LXDE, that is that if you ever mute it, you have to go into the administrator audio mixer settings and unmute it. From there, I can just control the volume with the shortcut buttons on my keyboard. I can mute it with the shortcut, but not unmute. Any suggestions on how to get a taskbar item for volume control, or how to get Steam to work in my other desktop themes?

Any Help Appreciated,

Michael

---

### Post by oldrocker99 on 2013-09-02
I have not encountered the Steam problem you have; I would recommend unstalling Steam and reinstalling it.

I also use LXDE, and the volume control problem you describe isn't something I have seen (yet).

---

### Post by michael-jstc on 2013-09-04
I found out that what was going on with steam was that I had incorrectly re-installed it in an attempt to solve the first part of the problem, and am currently updating it before it starts. I'm in LXDE and it's working fine, but I haven't started the client yet, so if it continues to give me problems on that part, I'll reply here again.

---

### Post by michael-jstc on 2013-09-04
Yep, it's still doing it.
Even when it finished updating, when I started the launcher, it took quite a while to "unpack the steam runtime" and when that finished, it seemed like nothing happened.
Then I clicked the desktop steam shortcut and the update window just barely blipped on for a millisecond, and i was barely able to see it.
Tried it again in ubuntu unity, and same thing.
I'm gonna try just completely scrapping and reinstalling ubuntu, as it seems to work just at first, but then stops working later.

---

### Post by KryoMouse on 2013-09-07
Before you reinstall (if you haven't already) could you try running Steam from a terminal and copy/paste the output in code tags on here? Knowing what's going on behind the scenes could help enormously.

---

### Post by junktext-0 on 2013-09-07
So, I have a similar problem that the original poster describes.  I wanted to test out LXDE to see if my Steam games would run any smoother, so I installed LXDE from the Software Center, rebooted, chose LXDE as my desktop environment prior to logging in (which loaded up just fine), and then tried to launch Steam.  For me, Steam also just had a blip of the GUI pop up stating "Verifying installation..." (this is in my ZIP file I uploaded) and then nothing else happens graphically.  I figured the problem was with LXDE, so I rebooted and went back to Unity.  Now I get the same results, with just a blip of the Steam GUI loading and nothing else.

I then concluded my Steam installation was broken, so I tried to fully reinstall Steam from scratch, but the methods I choose don't seem to be able to get me back to a usable Steam client.  I have attempted the following methods to reinstall my Steam client on Unity:


[LIST=1]
[*]Removed and reinstalled Steam using the graphical Ubuntu "Software Center". 
[*]Ran in terminal: **sudo apt-get remove steam-launcher** (and then later: **sudo apt-get install steam-launcher**) 
[*]Ran in terminal: **sudo apt-get purge steam-launcher** (and then later: **sudo apt-get install steam-launcher**) 
[*]In all of the above, I also manually deleted the following directories before reinstalling: _**~/.steam**_ and _**~/.local/share/Steam**_ 
[/LIST]

Additionally, I recorded what error messages are reported in a terminal by launching Steam via the "**steam**" command (this is also in the ZIP file I uploaded).  The first part of the output is regarding the re-building of my Steam client files (from a fresh install) and the rest of the output is what will result if I kill out the previous "**steam**" command and re-run "**steam**", resulting in a bunch of "***GLXBadDrawable***" messages from Steam.  Be aware that even though no Steam GUI loads up, the Steam process is still running in the background unless I kill it, which I have confirmed with "**top**" (even though nothing happens if I wait for 20+ minutes, and the Steam client only uses up between 1-3% of my CPU which I think is low from when it was working fine). 



* My system: I am running Ubuntu 13.04 (64-bit) with an NVIDIA driver (GeForce 310M) on a  Samsung Q430 laptop (Intel i5 CPU M450 @ 2.40GHz x 2 Cores,  4.0 GB of RAM).  Keep in mind that prior to me using LXDE, every  Steam game I had worked flawlessly for over 4 months, so I do not think it is my NVIDIA driver, as every other graphical app I use (Firefox, Konversation, Thunderbird, et cetera) still works fine in Unity.

---

### Post by junktext-0 on 2013-09-07
Quick update, but still no resolution:  So, after I performed all of the  above, I decided to check to make sure my "steam-launcher" was fully  updated as I thought that I remember when I did the "**apt-get install**"  process it had an older version from the current Ubuntu repositories vs.  Valve's Steam repositories once Steam is installed.  I was correct.   Even if you do a "**sudo apt-get update**" prior to running "**sudo apt-get  install steam-launcher**" you'll get stuck with Steam v1.0.0.35.  So,  after I fully reinstalled Steam, I did another "**sudo apt-get update**" and  then ran "**sudo apt-get -s upgrade**" (to simulate upgrading to tell me if  anything has changed).  There indeed was an update to my Steam client,  so I ran "**sudo apt-get upgrade**" (without the -s flag) and it installed  the latest Steam v1.0.0.41.

However, after all of this exciting  news, I still cannot make Steam work again.  It just reports the same  messages to my terminal that I already logged in my ZIP file.

---

### Post by oldrocker99 on 2013-09-08
Have you tried downloading the package from Steam's website? I have fixed a weirded-out Steam installation myself that way.

---

### Post by junktext-0 on 2013-09-08
oldrocker99, thanks for the suggestion, but unfortunately this didn't work either.  Although, your method of downloading the latest .deb from [www.steampowered.com](www.steampowered.com) helped to provide me with the very latest Steam client (v1.0.0.41) without me having to go through the odd double usage of an "apt-get update" as I mentioned earlier.  After installing and running, Steam went through the process of pretending it was updating the client files by downloading a 163 MB of something (like it did in my past example, which was logged to my previous terminal output).  The most obvious thing that sticks out to me is that the Steam GUI has some weird neon colors (the blue and green) rather than the black and grey colors expected by Steam.  I feel like there is some crazy X11 setting jacking up Steam, but the thing is I am surprised only Steam is having this problem.  None of my other software that uses X11 is having a problem.  So, I don't dare blame LXDE for being buggy (as Firefox ran fine in that environment, as it still does in Unity).  With this, I assume Steam is its own problem and doesn't like to play nicely when switching around with desktop environments.

---

### Post by michael-jstc on 2013-09-08
Well, it's now working for me, and I've already finished my whole game that I got, which was Psychonauts. What worked for me was to install the current 304 NVidia driver, but not the updates, just the original. Oddly enough, the 'recommended' driver provided by canonical, was a very old update, 174.

---

### Post by junktext-0 on 2013-09-08
michael-jstc, what did you do exactly in terms of getting your Steam to work again?  I did as you suggested and I reverted my NVIDIA driver back to the 304 version (the one without the 'updates' description), rebooted, fully reinstalled Steam again (removed packages and folders and did a clean install from apt-get), and I am still stuck on a broken Steam launcher.  I ask, as the last message you posted was that you were going to completely reinstall Ubuntu from scratch...  Did you do this?  If so, I assume this would fix my issue too, but I don't want to undergo the pain of that.

Thanks,

--William

---

### Post by michael-jstc on 2013-09-09
Try this,
sudo apt-get remove steam
sudo apt-get purge steam
cd ~/.local/share && rm -rf Steam
sudo apt-get update
sudo autoremove
sudo apt-get install steam

---

### Post by michael-jstc on 2013-09-09
autoremove should remove the rest of steam if there is any left
also, if you still have problems, try searching through your bin folders (/bin, /usr/bin, etc.) and delete anything related to steam, like steamlauncher
also, 
sudo apt-get install steamlauncher

should work

---

### Post by michael-jstc on 2013-09-09
and, just as an afterthought, go to your update manager and scroll down to the bottom after you install steam. There should be an update for the launcher there. If not, then it's already current.

---

### Post by junktext-0 on 2013-09-09
michael-jstc, thanks for the feedback and suggestions.  I really appreciate it.  I had my hopes up when I attempted your idea of using "**sudo apt-get autoremove**" as it removed _nvidia-common_ and a few others, so I was assuming the odd X11 glitch would be repaired...  Nope, still the same issue with a broken Steam client launcher (and the obviously odd retro green & blue colors for the fleeting moments the client is visible).

Note:  I rebooted my machine before I attempted to reinstall Steam, as I was curious if this would make a difference, but it didn't.

Second note: In case you were wondering, _nvidia-common_ was reinstalled automatically when I did "**sudo apt-get install steam-launcher**".

---

