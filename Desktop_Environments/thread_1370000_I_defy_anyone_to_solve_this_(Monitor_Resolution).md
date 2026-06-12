---
title: "I defy anyone to solve this? (Monitor Resolution)"
date: 2010-01-01
forum: Desktop Environments
---

### Post by owenisred on 2010-01-01
Please please please someone help me. I have been working on this for 8ish hours. I have seen virtually the same problem unanswered on so many pages. If anyone can help it would be much appreciated.

I have recently downloaded ubuntu 9.10. It is dual ran with xp.
The monitor res is set to 800 x 600 although when I'm on xp it can go FAR higher. 
I go system > preferences > display and my monitor is not recognized. Furthermore the two resolutions I am offered are 800 x 600 and 640 x 480.

xorg.conf apparently does NOT exist.

Should I REALLY have to make my own? It seems not worth the hassle. Otherwise ubuntu is great but I am so fed up with this I may simply go back to xp. If anyone could help it would be fantastic. 

Thank you,
Owen.

---

### Post by Repentinus on 2010-01-01
If you are able and willing to use Nvidia drivers (proprietary) then System -> Administration -> Hardware Drivers should let you install them and after installing them you should have Nvidia X Server Settings under Administration menu which lets you adjust your monitor resolution nicely.

It worked for me, I hope that you have Nvidia GPU and these work for you too. If not, they can wait anybody else with same problem and Nvidia GPU.

If you are using another graphics card, post it here, and I will try to find the solution. I know for sure that neither Debian's or Ubuntu's System -> Preferences -> Display application works with my laptop and card (Nvidia GeForce 9650M GT), so...

---

### Post by vandorjw on 2010-01-01
What video Card do you have in your machine?

I didn't see you say anything about nvidia, ati or intel?

---

### Post by owenisred on 2010-01-02
Nothing is in my Hardware drivers.

My video card is Inter(r) something i think...?
How do i find video card?

---

### Post by vandorjw on 2010-01-02
open up the terminal and type:

> 
lspci | grep -i vga


lspci is a command that will list your hardware. Grep simply then selects only those that mention vga in this case. the -i is there to ignore upper or lower case. Hope this helps.

Since you mentioned you have intel it should return something saying intel.
Also since you have windows XP you can also boot into that, right click the desktop, click settings, and then...go to the very last tab, where you control the resolution, it should tell you the name of your video card there also.

Once I know the video card, I can tell you the driver you need, and how to install it.

Hope this helps,

Cheers cc7gir
----------------------------------------------------------------------
EDIT
I am not sure, but this might also help you.

> 
sudo apt-get install xserver-xorg-video-intel


It been a while since i used ubuntu, so I am not 100% certain i have the name correct.
if that doesn't give you the capability increase your resolution I have something else you can try also.

---

### Post by Bartender on 2010-01-02
owen has an Intel 845 chipset.  He already ran lspci in the [other thread]("http://ubuntuforums.org/showthread.php?t=1369680&page=2").

[http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/](http://www.workswithu.com/2009/05/06/the-ubuntu-904-intel-graphics-fiasco/)

This is a real embarrassment.  If you can't get a picture up on the screen, that's pretty much a deal-breaker for most users.

owen, if you have a few bucks laying around and a PCI-x slot, you may want to drop in a basic graphics card like the ASUS EN8400GS.  That's what I'm using to drive two fairly large monitors.  Cheap, functional, works fine once you download the nVidia hardware drivers and configure it.

---

### Post by owenisred on 2010-01-02
cc7gir plugged that into terminal - said it was already the newest version...?

Thank you Bartender! - I am having difficulty doing the fix tho. It says

> Add the following lines to your /etc/apt/sources.list: I entered /etc/apt/sources into terminal, with 

> Add the following lines to your /etc/apt/sources.list: As the result...? please advise.

Edit: oops forgot .list part :s still doesn't work tho - permission denied?

Discovered this
> 
[http://www.ubuntugeek.com/new-intel-graphics-drivers-for-ubuntu-9-04-jaunty.html](http://www.ubuntugeek.com/new-intel-graphics-drivers-for-ubuntu-9-04-jaunty.html)Possible? downloaded it from here 

> [http://lists.freedesktop.org/archives/xorg/2009-April/045043.html](http://lists.freedesktop.org/archives/xorg/2009-April/045043.html)No idea how to install it tho - extracted it to my home folder... Dont know what to do from there - there is an install-sh file but I can't get it working properly

Edit: really tired of this lol would it be possible/advisable to get ubuntu 9.04?

---

### Post by owenisred on 2010-01-02
SOLVED IT!

After trying so many different ways to overcome the resolution problem myself - I got it working a different way: Ill stick it in here to help anyone who is having trouble with sharap's fix

1. open terminal (Applications > Accessories)
2. Type  	
 	 	 		 			 				 gksudo gedit /etc/apt/sources.list 			 		 	 	 
 hit enter and type your password (if you are prompted) and enter again.
3. Scroll to the bottom of the text that appears and paste
 	
 	 	 		 			 				deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main 			 		 	 	 
5. open a new terminal
6. type 
 	
 	 	 		 			 				sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xce90d8983e731f79 			 		 	 	 
7. Wait fr the thing to download
8. New terminal type

 	
 	 	 		 			 				sudo apt-get update 			 		 	 	 
9. Again add password if necessary
10 type 
 	
 	 	 		 			 				sudo apt-get install xserver-xorg-video-intel-2.4 			 		 	 	 
thatl be you

type  	
 	 	 		 			 				sudo /etc/init.d/gdm restart 			 		 	 	 
 to reset ubuntu.

When i did it my monitor went crazy and I had to switch off at plug, but then on opening ubuntu again resolution was fine :smile:

PHEW!

Thanks for all the help guys REALLY appreciated!

---

### Post by Bartender on 2010-01-03
Hey, owen, good job -

Those directions did get a little geeky.  Glad to see you persevered, and shared your version of what worked.  That's the spirit!  Lend a hand to the next guy with the same problem.

---

