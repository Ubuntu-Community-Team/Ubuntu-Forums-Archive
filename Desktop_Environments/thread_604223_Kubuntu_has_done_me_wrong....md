---
title: "Kubuntu has done me wrong..."
date: 2007-11-05
forum: Desktop Environments
---

### Post by linuxmann on 2007-11-05
This is coming from my own opinion of KDE and my experence with it...

Well, thats it... No more Kubuntu for me at all. Too many problems too many times. It is strange that i have had problems with linux at all. Ive switched back and forth with ubuntu and Kubuntu alot to see what works best. Gnome does. here's what i have experenced with KDE...

1. What ever package is broken or is corrupted, it screws up the ablity to actually change and manage packages. Unless you restart the computer into recovery mode, start aptitude and remove the package from there for Adept to work again.

2. Interface glitches make the windows and desktop look bad. Looks like a messed up version of an nes game.

3. Constant hacking. Yes i do get hacked when i run linux, but it is mostly when i ran kubuntu. All of these X windows popup on my toolbar and crash my computer. I have had my firestarter acting up on me.

Has anyone experenced these problems and then some? I am not trying to bash linux and KDE. I also want to know why these things happen.

---

### Post by Kingsley on 2007-11-05
I have no clue what's going on with your computer. My best 6 months on Linux were with Kubuntu. The only reason I switched to plain Ubuntu is because Gnome is funner to customize.

P.S. You're not the youngest Kubuntu user. My chemistry advisor's son is 10 and he uses Kubuntu.

---

### Post by jabeez on 2007-11-05
well as far as broken packages, not sure what you're doing to cause this but both versions use apt, just different frontends. I personally use kubuntu but install synaptic as well, I like adept for some things and synaptic for others. anywho, as for the other things, not a clue what you're talking about as Kubuntu works really well for me and since switching to Kubuntu at the Breezy release, have never seen any signs of being "hacked"..............diff'rent strokes tho, use what works...........

---

### Post by Rhubarb on 2007-11-05
If you're getting hacked, then I'd seriously consider:
. Make sure there's no SSH ports open available from the outside internet.
. Don't use a simple password, and certainly make sure your login is not the same as your password.
. Keep up to date with all the latest security updates.
. Are you sure you're really being hacked?  Maybe your Kubuntu ISO was burned to the blank CD-ROM too fast - try burning it at a slower speed to prevent a corrupted burn.

---

### Post by igknighted on 2007-11-05
Adept does suck.  Install Synaptic if your prefer, or use the apt-get and aptitude commands on the cli... its faster and easier.

---

### Post by Incense on 2007-11-06
Kubuntu is bad, but not that bad. Never had any of the problems you're talking about. I have never had a problem with adept . Searching feels a bit faster in adept then it does in synaptic on my machine. Anyway, maybe you should look into a clean install and see if that helps.

---

### Post by igknighted on 2007-11-06
> **Incense said:**
> Kubuntu is bad, but not that bad. Never had any of the problems you're talking about. I have never had a problem with adept . Searching feels a bit faster in adept then it does in synaptic on my machine. Anyway, maybe you should look into a clean install and see if that helps.

Searching is faster, but adept has some rather major bugs.  For one, if an install needs you to ok something, be it the license for Sun's java, or some question about setup, etc. then Adept does not properly handle this, and usually fails the install.  You then need to use an apt-get -f install to finish it off vie the CLI before it will work again.

The search is nice.  It does it on the fly as you type, so the results are pretty much instantaneous.  Much nicer than having to click "search" in synaptic.  However, in synaptic you can just start typing to filter the results too, so its not that much of an advantage.

---

### Post by Incense on 2007-11-06
> **igknighted said:**
> Searching is faster, but adept has some rather major bugs.  For one, if an install needs you to ok something, be it the license for Sun's java, or some question about setup, etc. then Adept does not properly handle this, and usually fails the install.  You then need to use an apt-get -f install to finish it off vie the CLI before it will work again.

The search is nice.  It does it on the fly as you type, so the results are pretty much instantaneous.  Much nicer than having to click "search" in synaptic.  However, in synaptic you can just start typing to filter the results too, so its not that much of an advantage.

I think they finally fixed this in Gutsy. I recall the java window coming up when I installed the kubuntu-restricted-extras package. The new gdebi-kde installer does have a way to go. Always hangs on my system. While I do like searching in Adept more, that's really all. Synaptic is much nicer. I hate clicking on a package in adept and seeing the description appear inline.

---

### Post by K.Mandla on 2007-11-06
Moved to Desktop Environments.

---

### Post by hangfire on 2007-11-17
> **linuxmann said:**
> 
1. What ever package is broken or is corrupted, it screws up the ablity to actually change and manage packages. Unless you restart the computer into recovery mode, start aptitude and remove the package from there for Adept to work again.


I have this problem too. I just switched to synaptic, which I do anyway after all installs.

The following command-line commands might help you:

[B]sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a[/B]

> **linuxmann said:**
> 
2. Interface glitches make the windows and desktop look bad. Looks like a messed up version of an nes game.


You have display driver problems. xorg is trying to use more display memory than you have, your card was detected wrong, you have a bad card, something is wrong with your *xorg.conf* setup.

> **linuxmann said:**
> 
3. Constant hacking. Yes i do get hacked when i run linux, but it is mostly when i ran kubuntu. All of these X windows popup on my toolbar and crash my computer. I have had my firestarter acting up on me.


Usually unwanted windows come from unwanted input, such as an oversensitive touchpad, bad mouse driver, etc launching things that you didn't think you asked for (but did). Again, the primary culprit is usually a bad *xorg.conf*.

> **linuxmann said:**
> 
Has anyone experenced these problems and then some? I am not trying to bash linux and KDE. I also want to know why these things happen.

I've done what I can. Hope the next go-round is better for you. I'm having a few teething pains too, but nothing I haven't been able to work-around yet.

-HF

---

