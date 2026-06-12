---
title: "Internet Explorer Via Wine"
date: 2005-12-13
forum: General Help
---

### Post by JoshHendo on 2005-12-13
I am trying to install internet explorer via wine (only so that some other programs that I use will work, as they require IE). Every time I try to install it I get the following error:
[img]http://www.freephotopost.com/uploads/27fcf3316d.png[/img]
Is there anyway to get this to work? Thanks :)

---

### Post by newuser111 on 2005-12-13
get this program it installs internet explorer for you in wine

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

### Post by aysiu on 2005-12-13
You can also try IEs4Linux. It's self-installing and needs only *wine* and *cabextract* installed beforehand--both are in the repositories.

If you have no idea what I'm talking about, you need to read the links in my sig.

---

### Post by beameup on 2005-12-13
Ouch. I thought this was some kind of joke. :confused: 

What about using Opera and making it "Identify as IE"? Would that work?

If you really need IE, then it's probably best you dual boot with whatever flavor of windows you own. Just my opinion.

---

### Post by aysiu on 2005-12-13
[QUOTE=JoshHendo]I am trying to install internet explorer via wine (only so that some other programs that I use will work, as they require IE).[/QUOTE] Most IE "requirements" can be worked around using the Firefox extension [User Agent Switcher.](https://addons.mozilla.org/extensions/moreinfo.php?id=59)

[quote=beameup]If you really need IE, then it's probably best you dual boot with whatever flavor of windows you own. Just my opinion.[/quote] That would entail rebooting every time you needed to access a website that needed IE. Running IE using Wine or using Firefox's User Agent Switcher is a much quicker solution.

I haven't found Opera's "Identify as MSIE 6.0" to really work on most IE-only sites. Just my personal experience.

---

### Post by beameup on 2005-12-13
Yea, I understand the rebooting thing. I do it for MS Money all the time. Moneydance is close, I could probably get by with it, but it's not free. (Personally, I don't mind paying a "few dollars" for something like that.)

I come from the "side" that doesn't want or need any MS software running in my 'nix. I have seen a few polls in the last few weeks that show 60 to 70% of linux users need Wine, win4lin, or crossover to run MS software and I'm baffled.  But hey, you do what you have to do right?

---

### Post by JoshHendo on 2005-12-17
[QUOTE=newuser111]get this program it installs internet explorer for you in wine

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)[/QUOTE]
Tried that, and now....... >.<, when ever I open a program in wine none of the text is shown. Is there a way to reverse this? (I tried completly uninstalling wine and installing it again, didn't help :()

---

### Post by dk_pa on 2005-12-17
If you have a copy of Windows around I would run VMWare Player.  There is a how to on the forums here that is nicely done and Windows actually runs very fast under.  I would say the biggest done side to this is needing much more space (I would say 4G minimal for OS installation and a little room to grow) but you are then running a full Windows environment.

I have been using Photoshop CS and some Burning Applications under the VMWare Player with a Windows 2000 installation on an Athlon XP 2500 512 Megs of ram and it's almost full speed.  I would imagine once I get my 2GB of memory it would be just like Windows.

---

### Post by soulestream on 2005-12-17
I tried IEs4Linux that aysiu posted. Works well. It crashes a little, but hey so does firefox. ;) 


I had to do a "full" install (all 3 versions) for some reason to get it to work. 

Good recommendation though.


soule

---

### Post by shakin on 2005-12-17
If you install Wine from Wine's repositories (so you get 0.9.3) you can just run MS' IE installer and it will work. winetools (same repository) will also do it as well as install other dependencies.

The reason IE is needed in Wine is because other Windows programs require it, such as Office 2000. Cedega gets around this by substituting the Mozilla control for the IE control when it's requested, but Wine doesn't do this.

---

### Post by Dimitriid on 2007-09-09
I tried using the installer and IE just displays a blank page every time. Seems like it broke after 9.3 or something. I need IE to run wine programs that specifically need IE to be able to render things, but the program has the same behavior in wine: Opens up but shows only a blank screen. I have agent switched on my Ubuntu install of Firefox but I don't know how to tell wine to use it, will I need to install the windows Firefox Version under wine and THEN install the agent switcher?

---

