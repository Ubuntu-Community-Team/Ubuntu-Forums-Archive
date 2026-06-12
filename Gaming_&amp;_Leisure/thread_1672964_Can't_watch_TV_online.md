---
title: "Can't watch TV online"
date: 2011-01-21
forum: Gaming &amp; Leisure
---

### Post by Gillette88 on 2011-01-21
Hi everyone! I'm very much new to all this Ubuntu stuff, and recently completely erased my Windows hard drive in favour of Ubuntu 10.10. :) It's been wonderful, but I'm having some issues. Mainly, I've been trying to watch The Big Bang Theory on the ctv.ca website and nothing comes up but a grey block where the show should play. That's really my main concern, but I've also noticed that youtube videos don't tend to play very easily either. I either have to refresh the page until the video works, or it just never works at all. I've downloaded the ubuntu-restricted-extras thing in my terminal (I think, it's hard to tell if it worked or not) but it's made no difference. Any ideas?

---

### Post by ernz on 2011-01-21
Hi Gillette88. In Ubuntu the Adobe flash plugin is called a "restricted extra". It's obtainable but you need to agree to licensing restrictions to install it via the software manager. It's not a big deal and it's easy to resolve. 

Go to the Application menu in the top left and hit "Ubuntu Software Center". Type in your admin password and do a search for "restricted". One of the options will be "Ubuntu restricted extras". This will install support for MP3 playback, support for certain video formats and, most importantly, flash media!

Hit install, do a reboot and open Firefox again. The gray box should now be replaced with the proper content.

---

### Post by Gillette88 on 2011-01-21
Hi ernz, I've just checked and I do have the Ubuntu Restricted Extras installed. I'm not sure if I did that before, I installed a lot when I installed Ubuntu on Sunday, but either way it's there and there's still nothing coming up other than the grey screen. Should I uninstall it, reinstall and then reboot?

---

### Post by codymyth on 2011-01-21
i would suggest going to the package manger and searching for adobe flash, i believe the file you want is adobe-flashplugin

---

### Post by ernz on 2011-01-21
Hrm. That should really work. Another way to do this is to install the official package from Adobe. [Here's the link to the 32-bit .DEB installer file.]("http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_10.1_for_Linux_(.deb)")

It might install some other rubbish like Adobe Air (whatever that is?!) and some installer somewhere. I've used this method on another machine and it worked without any undesirable effect. Give it a shot! Go-go gadget guinnea pig! (I know you're new, please report back if it works so others can see if it worked ;)  )

EDIT: If that doesn't work, codymyth's method might. I think the package he/she's referring to is flashplugin-installer. There's a quick way of installing individual packages in ubuntu. Go to Applications > Accessories > Terminal and type in:
```
sudo apt-get install flashplugin-installer
```

My understanding of this package is that it will prompt you to install flash from Firefox. I could be wrong? May be best to check out the official package first at the link above.

---

### Post by codymyth on 2011-01-21
Hello ernz, I just opened synaptic package manager and did a quick search for adobe flash player and at the top of the list the  first thing listed was adobe-flashplugin and my computer showed it was isntalled. The one you mentioned was listed there also but not installed on my computer, but I think the first method of getting it from the website will work.

On the AdobeAir thing, I think it is a player for video games. I know if you want to play an internet football game called Quickhit you have to install adobeair (or atleast you used to).

---

### Post by Gillette88 on 2011-01-21
Thanks for the advice, but it's still not working yet :( I tried going to the website and installing flash, but all it said in the software centre was that I have the latest version already. The I tried installing it through the terminal like ernz suggested, restarted and still nothing. Any other ideas?

**Edit** I was, however, able to watch the big bang theory on icefilms.info, using megavideo. So somehow it's maybe just the ctv website? I'd use another channel but the American ones don't work in Canada because I'm not in America here :P

**Edit 2** Just found out I also can't play the games on Shockwave.com, but I do have the shockwave plugin. Thoughts??

---

### Post by ubudog on 2011-01-21
Welcome!

Open a terminal, type the following command:

```
sudo apt-get install ubuntu-restricted-extras
```

And all all your problems will be solved!  (hopefully)  :p

---

### Post by ernz on 2011-01-21
Gillette88, That's interesting. You can test your flash installation at the adobe site [here]("http://www.adobe.com/software/flash/about/")

I actually tried loading a video at ctv.ca and it said they were experiencing issues at the moment and to try again later. It just stuck a blank flash box up where the video should have been. Perhaps it is an issue specifically with CTV.

---

### Post by ubudog on 2011-01-21
> **ernz said:**
> Gillette88, That's interesting. You can test your flash installation at the adobe site [here]("http://www.adobe.com/software/flash/about/")

I actually tried loading a video at ctv.ca and it said they were experiencing issues at the moment and to try again later. It just stuck a blank flash box up where the video should have been. Perhaps it is an issue specifically with CTV.

Perhaps.  Thanks for the test link.

---

### Post by Gillette88 on 2011-01-21
Ubudog, I did try that and everything is installed on that end.

ernz, the site said everything was running fine. Le sigh... this can be very frustrating! But I'm sure I'll figure it out eventually. It might just be the site, but now that the shockwave website isn't working either I'm suspecting it's my computer. when I was running the trial Ubuntu off my Windows everything still worked, but I had people install random things. I should've paid attention back then :)

---

### Post by ernz on 2011-01-21
> **Gillette88 said:**
> Ubudog, I did try that and everything is installed on that end.

ernz, the site said everything was running fine. Le sigh... this can be very frustrating! But I'm sure I'll figure it out eventually. It might just be the site, but now that the shockwave website isn't working either I'm suspecting it's my computer. when I was running the trial Ubuntu off my Windows everything still worked, but I had people install random things. I should've paid attention back then :)

Do not fear my Reddit brother! We shall fix this yet! Here's a couple of things you could try instead.

Firstly, [try installing Chrome]("http://www.google.com/chrome/intl/en-GB/landing_tv.html"). It's a sweet browser and apparently has it's own native flash plugin which would negate all of the firefox plugin issues.

Secondly, if you have ATI graphics, try running:
```
export XLIB_SKIP_ARGB_VISUALS=1 && firefox
```
as per [this thread on another forum]("http://askubuntu.com/questions/11465/firefox-youtube-flash-player-shows-as-grey-box")

EDIT: If you are ATI and go that route, remember to restart the PC after doing that command. No telling what kind of graphical wizardry is running in the background when rendering flash via a Firefox plugin!

---

### Post by Gillette88 on 2011-01-21
Just tried to install Chrome and this is what came up:

An unhandlable error occured
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

Also, I'm not sure what ATI graphics are. I'm a supernoob. Also also, I don't know what Reddit is. Thirdly also, I'm not a brother. (which might explain the lack of understanding when it comes to all things tekkie. Bring on the sammich jokes)

---

### Post by ernz on 2011-01-21
OK my...Ubuntu sister? I've read that this is because update manager or package manager is running. Try closing everything and running it again or restarting the PC and just going straight to that Chrome link without doing anything else.

---

### Post by ernz on 2011-01-21
You could also do a search for "Chromium" in the software centre. That is pretty much the same thing as Chrome. Give that a shot.

---

### Post by ubudog on 2011-01-21
> **ernz said:**
> You could also do a search for "Chromium" in the software centre. That is pretty much the same thing as Chrome. Give that a shot.

You may have to add the ppa for that, pretty straightforward though.  Also, Chromium is more open than Chrome.

---

### Post by William AGuyton on 2011-01-22
Thanks for this information, This is the most inportand things for everyone

---

### Post by ubudog on 2011-01-22
@Gillete - Any improvements?

---

### Post by Gillette88 on 2011-01-22
Nope, no improvements. I asked my techie friend when he got home from work and he couldn't figure it out (this guy writes his own code, so he knows his stuff). He said just to leave it and hopefully with updates things should work. I tried to download Chrome AND Chromium and neither were able to even install. An error message popped up saying it wasn't happening. So I've decided to leave it for now, still frustrating sometimes but hey, life's full of frustrations. Gotta pick your battles :) Thanks for all the help though! I'll post again if I figure out a solution.

---

### Post by ubudog on 2011-01-22
And just to make sure, you are in Canada, right?

There are restrictions for watching online tv like that outside the US and Canada.

---

### Post by ernz on 2011-01-23
> **Gillette88 said:**
> Nope, no improvements. I asked my techie friend when he got home from work and he couldn't figure it out (this guy writes his own code, so he knows his stuff). He said just to leave it and hopefully with updates things should work. I tried to download Chrome AND Chromium and neither were able to even install. An error message popped up saying it wasn't happening. So I've decided to leave it for now, still frustrating sometimes but hey, life's full of frustrations. Gotta pick your battles :) Thanks for all the help though! I'll post again if I figure out a solution.

You know who else was a quitter? Hitler.

---

### Post by Gillette88 on 2011-01-23
@ubudog: yeah, I'm in Canada but I'm trying to get at ctv.ca, which is a Canadian broadcaster. I've watch it on Windows and on the trial version of Ubuntu, so I don't know why it's not working. My boyfriend has convinced me to try things again, so I'm back on the hunt to find a solution! I'm thinking if I can figure out how to get shockwave games to work it'll hopefully fix the tv show problem.

@ernz: LOL :D

---

### Post by ubudog on 2011-01-23
This is what the wiki has to say about Shockwave.  It may help you.

[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

---

### Post by ernz on 2011-01-24
I am not in Canada so every time I try these video's it just shows a black area where the video should be. Ubudog will be able to test this better.

---

### Post by ubudog on 2011-01-24
> **ernz said:**
> I am not in Canada so every time I try these video's it just shows a black area where the video should be. Ubudog will be able to test this better.

Alas, I am not in Canada either.

---

### Post by beew on 2011-05-23
It works perfectly for me. Try install flash with the firefox flash-aid addon, it is the easiest way and it optimizes flash for Ubuntu, forget about installing from the repository (which is old) or the adobe site.
[URL="https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"]
https://addons.mozilla.org/en-US/firefox/addon/flash-aid/[/URL]

Edited: it works for 10.10, 11.04 Nvidia, ATI and Intel graphic cards, just tested them all. Looks like a horrible show, btw. :)

---

