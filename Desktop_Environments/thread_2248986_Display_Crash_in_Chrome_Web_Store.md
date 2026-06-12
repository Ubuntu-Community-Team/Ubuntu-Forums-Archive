---
title: "Display Crash in Chrome Web Store"
date: 2014-10-18
forum: Desktop Environments
---

### Post by ahmed19 on 2014-10-18
Ladies and gentlemen, I have a strange problem.

I'm trying to figure out what exactly is special about certain sites that causes my display to totally turn off. On these sites:
[https://chrome.google.com/webstore/](https://chrome.google.com/webstore/)
(it happened on a few others but I can't remember at the moment)

The page loads and it just totally freezes for 5 seconds and then display turns off. The processor is still active so it is not a total computer crash and I have to hard reset it to restart.

It doesn't happen on:
[https://drive.google.com](https://drive.google.com)
[https://play.google.com](https://play.google.com)
[https://gmail.com](https://gmail.com)

it doesn't seem to happen on Firefox for some reason (the same site).
I think it might be because of the HTML5 differences.
Here's my firefox results:
html5te.st/2a5aeb233bf2e066
Chrome results:
html5te.st/a0cf55233bf2c83e
It could be due to "speech synthesis" or "interactive elements" both of which are disabled in firefox.

This happens whether single monitor or dual-monitor.
I've tried disabling accelerated overflow scroll and override software rendering list. Doesn't make a difference.

I'm running the latest Ubuntu (14.04) as of now, I am fully updated and am using a Toshiba Satellite A205 and everything else seems to be working fine.

Any suggestions or help would be appreciated. Thanks :)

---

### Post by anagrammar on 2014-10-18
Same here. Problem also occurs with Linux Mint. In my case I think it's due to a less than powerful computer  (a pretty old dual core with wimpy integrated graphics), but Windows and older versions of Linux had no problems, so this should be considered an annoying bug. I ran into the same problem on the Chrome download page as well, and ended up having to install it via the terminal. There is a less than optimal workaround to at least allow you to install extensions. In Chrome go to: settings/advanced settings and disable "use hardware acceleration" and restart your browser. Leaving it disabled negatively impacts some video playback, so I'd advise turning it back on once you're done with the Web Store.

---

### Post by rudolph-chr on 2014-12-01
Same Problem here for me on google webstore with chromium browser. Current Kubuntu 14.04 LTS and like for anagrammar a pretty old laptop. Only minutes before I installed Pipelight instead of HAL for my wife watching local shows with DRM systems. Do you guys have also Pipelight on your machines, maybe this is the root cause?
Until today no other sides produced this failure. Hope it is the only one.

---

### Post by BBQdave on 2014-12-01
I'm running Ubuntu Unity 14.04 with Google Chrome on a Lenovo Thinkpad T400 (Intel® Core™2 Duo processor & 2GB of RAM) no problems. I do not have Pipelight installed. I have my music library uploaded to Google Play - use this for streaming music. Use Chrome browser for everything else, work & play.

The only extra (ugly) package I have installed on Ubuntu is gstreamer mp3. Allows me to play purchased music from Google Play, that I have downloaded to my Ubuntu system.

YouTube functions normally, but I do not watch much videos - so not a huge experience with watching web videos.

Basically, for my entertainment needs - default install of Ubuntu Unity with Google Chrome & gstreamer (ugly) mp3 added.

---

### Post by dvfreelancer on 2014-12-07
I'm running into the same problem as you guys. Everything is going along fine, suddenly Chrome locks up for a few seconds and my screen goes black. I have not found a keystroke combination to either logout or otherwise shut down without holding the power button down. 

It was getting so bad I had to switch to firefox. I'm running 14.04 on a Lenovo T61 ThinkPad. I don't like Firefox as well because Ctrl+Shift+V doesn't paste plain text it opens a page object menu.

---

### Post by stichoza on 2015-02-02
I have the same problem on Lenovo T61 Thinkpad. But in both Chrome and Firefox. I couldn't go to Chrome Download page too. When I close the laptop (suspend) and re-open (wakeup) the display is on and the wallpaper is displayed. But there is no dashboard, top bar and window title bars.

Any updates? It's the weirdest problem I have ever seen in Ubuntu.

---

### Post by stichoza on 2015-02-02
Update: I have installed [Intel Graphics Installer]("https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7") as mentioned in [this post]("http://www.omgubuntu.co.uk/2014/08/intel-graphics-installer-linux-updated-1-0-6"). Now the black screen is gone, but Unity still crashes when I go to Chrome Web Store.

Update v2: I changed the desktop manager form **lightdm** to **gdm** and Unity to Gnome Classic but still the same problem.

---

### Post by stichoza on 2015-02-03
Hey guys! Good news! It seems I **solved** this problem. I have disabled WebGL and GPU Things in **[FONT=courier new]chrome://flags[/FONT]** page, but it didn't help. The fix is simple: Go to chrome settings, go to Advanced and untick "Use hardware acceleration when possible". Everything works now.

---

