---
title: "dell d630 gutsy nvidia docking/undockng"
date: 2008-01-22
forum: Dell  Ubuntu Support
---

### Post by ccrupper on 2008-01-22
I have a brand new Dell D630 and thanks to the forums, I've been able to get most everything up and working.

I was able to install the restricted nvidia driver and everything was working well when I was using the laptop's lcd screen.

However, when I came to work and docked my laptop, I got the default ubuntu splash screen and then my screen went blank before displaying the login window.

No matter what I try, the only driver that I can get to display at anything beyond 800x600 resolution with my monitor/docking station configuration is the "nv" driver, which is really choppy when I move windows around the screen.  Also, I don't get any of the fun compiz goodness with that driver.

Any help that anyone can offer to my external display working with the proprietary nvidia driver would be greatly appreciated.

Thanks in advance!

Relevant specs:
Machine:  Dell Latitude D630, Intel Core 2 Duo 2.60GHz
Video Card:  128MB NVIDIA Quadro NVS 135M
External Display:  Dell 2007 WFPb

---

### Post by irish8890 on 2008-01-22
Install the drivers from nVidia's web-site.  You have to shutdown the graphics server & get into terminal mode to run the installer.

John

---

### Post by ccrupper on 2008-01-22
Thanks for the quick reply John.

I've already tried what you suggested.  After installing the driver and restarting ubuntu, it goes through the splash screen and then starts up in low graphics mode and says that it can't properly detect the video card.

Again, thanks for your help.  Any other ideas?

---

### Post by flippbonq on 2008-01-30
have you tried this to remove the old nvidia driver : 
```
sudo apt-get remove --purge nvidia-glx
```more info about removing/upgrading the nvidia module @ compiz,org. [[here]("http://compiz.org/NVidia")]

also which docking station are you using? i had to use nvidia-settings to get my d620/dock/external monitor to play nice. also check out this [thread]("http://www.dellcommunity.com/supportforums/board/message?board.id=insp_video&thread.id=157770&view=by_date_ascending&page=1") for more about d620 + docking. (sorry it's not d630 specific)

---

