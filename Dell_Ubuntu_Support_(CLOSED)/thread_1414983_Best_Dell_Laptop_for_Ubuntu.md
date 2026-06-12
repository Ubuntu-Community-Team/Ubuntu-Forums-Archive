---
title: "Best Dell Laptop for Ubuntu"
date: 2010-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ubtsay on 2010-02-24
I am a newbie to this forum. please suggest me a good Dell laptop for Ubuntu. As per Dell's website they have only one model (mini 10v) that is supported ubuntu pre-installed. A week ago i saw inspiron 15n listed but that is not seen anymore on their website
 
[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&l=en&cs=19](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&l=en&cs=19)
 
Thanks

---

### Post by wojox on 2010-02-24
I've got a Dell Studio 64-bit 2Gb of ram. It came with Vista preinstalled and I wiped it out and put Karmic on it. Runs like a champ.

---

### Post by stillnotcool on 2010-02-24
> **ubtsay said:**
> I am a newbie to this forum. please suggest me a good Dell laptop for Ubuntu. As per Dell's website they have only one model (mini 10v) that is supported ubuntu pre-installed. A week ago i saw inspiron 15n listed but that is not seen anymore on their website.

Dell models disappear/reappear from the Ubuntu product page on an unfortunately frequent and erratic basis.  I'd check back soon to see if Dell is offering new systems with Ubuntu.  Only a few weeks ago (maybe 2, or 3?) Dell was offering four systems with Ubuntu preinstalled.

---

### Post by gradinaruvasile on 2010-02-24
Dells are usually compatible with Linux/Ubuntu/Debian. At work i have a Dell Optiplex 755 desktop and Dell D630 laptop, my wife has a Dell C640 laptop, all work perfectly with Linux (Ubunutu 8.04-9.10, Debian Squeeze) they even have dedicated programs made by Dell (i updated the D630 laptop's BIOS, for instance, from Ubuntu). Also, i installed Ubuntu on Inspiron 530 desktop and worked well too.

My advice is to go to them with a live CD/USB stick (the latter is better because its way faster) and boot from it the models you like and check if everything works well (wireless, bluetooth, video, audio) etc. As a rule of thumb i would suggest nvidia graphics, but in the laptop world that can be a bit expensive - i would rate ati next and the worst is the intel onboard - for example the 4500 version (that is ubiquituous in newer laptops) has very crappy drivers (in Ubuntu 9.10), not even flash plays well on it.

---

### Post by bhallett71 on 2010-02-24
I just purchased a refurbished D620 from the Dell Financial Services website ([http://www.dfsdirectsales.com/](http://www.dfsdirectsales.com/)).  I found one that did not have an OS loaded, and got a really good deal.  Dual Core, 2GB RAM, 120GB drive, WiFi for under $350.  When it arrived (3 days w/ standard shipping)  I used a 9.10 live CD to give it a run and everything seemed to work fine.  I then loaded MS XP and had a bunch of problems that were not evident when I booted from the 9.10 live CD, most notably the WiFi and Ethernet ports were not being detected.  
 
I then remembered why I hate MS. ](*,) 
 
The solution was to partition the hard drive, install 9.10, and set-up the dual boot.  The GRUB boot loader is real nice.  No problems with Ubuntu.  30min total for the Ubuntu install.  I am still trying to get the XP issues resolved... going on 6hrs.
 
Hope that helps.

---

### Post by Alex Deez on 2010-02-24
Hey all I'm just posting here so I can find this topic again when it has more posts.  Good info so far though.

---

### Post by KegHead on 2010-02-24
Hi!

I have a Dell mini 9 /9.10, 16 gb ssd, 2gb ram w/no problems.

Also a Dell B130 free from my sister. Came w/xp. 512 ram, 60 gb hd.
Loaded 9.10 w/no problems.

Dell seems to be Ubuntu friendly.

KegHead

---

### Post by leg on 2010-02-24
I have the Inspiron 17 which came with Windows 7 pre installed. I installed Ubuntu beside it and it works just fine.

---

### Post by ubtsay on 2010-02-25
I've placed an order for Studio 15 [FONT=Arial]i7-720QM today. Many thanks for the suggestions.[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]Thanks again[/FONT]

---

### Post by jms-ubuntu-en on 2010-02-27
I have had good experience with a Precision M4300 / Ubuntu combination as a everyday utensil for about 2 years now. I Recommend :D

Question: 
Any experienses with Precision M6500 with Ubuntu so far? 
I noticed that there is an option to have it with RedHat EL 5.3 preinstalled, but I have to follow our company policy and so it will be delivered with Windows7 preinstalled. I'm going to install Ubuntu to it if there are not any bigger troubles noticed (and if the livecd test is a 'pass').

---

### Post by IVirOrfeo on 2010-03-15
Hi, I had the same question, first of all, thank you everyone for the information on this page! I appreciate it. I am considering the inspiron 15, I worry about the driver issues, because it is not the one they had on the ubuntu page, (that one is out of stock the serviceman said in chat) I worry because of course, there are levels of compatibility, I would assume that not all inspiron 15's are the same model number, I would prefer to buy it with ubuntu pre-installed for that very reason. the tip about trying out a live cd on a demo floor was brilliant and would benefit me greatly if I was able to do so, however I am not, and they have a great deal on this inspiron, and it is limited, should I move on it, or wait for an ubuntu pre-installed Inspiron to come on dell's website?
Thanks in advance/

---

### Post by waynefoutz on 2010-03-16
I's my experience that most products from Dell will run Ubuntu fine out of the box, you might have to do a little bit of work getting the wi-fi up and running on some laptops, but that rarely consists of nothing more than plugging the laptop into the router with a wired connection long enough so it can download the restricted drivers. It almost always does this on it's own. Another problem are laptops, and desktops, with older ATI graphics in them. ATI's Linux support is abysmal, and the open source drivers aren't quite up to snuff, although they are getting better. If you are buying a Dell and want to get a good Ubuntu experience, make sure it has either Intel or Nvidia graphics.

---

### Post by Kixtosh on 2010-03-17
> **IVirOrfeo said:**
> ... should I move on it, or wait for an ubuntu pre-installed Inspiron to come on dell's website? ...You might be waiting a long time ... I'm not sure that this should be a concern, really, since even those machines sold by Dell with Ubuntu installed currently have to upgrade to a newer release version that is independent of Dell altogether at some point.
 
The issues arise, from what I can determine, when they make some sort of proprietary driver "fix" to integrate some piece of hardware that was not really compatable with Linux initially (so why did they include it in the unit?!). A good example might be the Dell Inspiron Mini 12, which did exist at one point with Ubuntu, but when purchased with Windows instead, there were all sorts of headaches with the video driver that don't really have any 100% satisfactory solution and Dell seems to have no intention of helping out.
 
What I would do is just try to determine what hardware is most likely to work out of the box, such as Nvidia for video, rather than ATI, for example. It would be great if we could compile a Dell specific list of hardware that is known to work, and a Dell specific list that is known to be problematic. Then again, perhaps Lenovo is the better choice for aspiring Ubuntu users (and they do have great deals too, from time to time) but Dell and Lenovo are usually considered the most Linux friendly from everything I've been reading here on the forum.

---

### Post by rpared01 on 2010-03-17
i was using ubuntu 9.10 on my inspiron 13, but the only thing that didnt work out of the box for was the wireless. If you look for a laptop preloaded with ubuntu, i would recommend the "Dell Vostro v13". i just got mines yesterday and it came with dell verions of ubuntu 9.04

---

### Post by brianfactors on 2010-03-18
I can't remember any major hardware problems with my Inspiron 1545 and Ubuntu 9.10.

My laptop: (well, almost) [http://www.dell.com/us/en/home/notebooks/laptop-inspiron-1545/pd.aspx?refid=laptop-inspiron-1545](http://www.dell.com/us/en/home/notebooks/laptop-inspiron-1545/pd.aspx?refid=laptop-inspiron-1545)

---

### Post by Knowle on 2010-03-18
I got a Inspiron 1545n, pre-loaded with Ubuntu when Dell use to offer it. It's the same as the Inspiron 1545 pre-loaded with Windows. I've had zero issues with it through 3 upgrades(8.10 -> 9.04 -> 9.10). I plan on throwing the 10.04 Beta 1 on there later today when it's officially released. Re-installs have worked perfect as well with no issues.

---

### Post by tephelan on 2010-03-18
> **waynefoutz said:**
> I's my experience that most products from Dell will run Ubuntu fine out of the box, you might have to do a little bit of work getting the wi-fi up and running on some laptops, but that rarely consists of nothing more than plugging the laptop into the router with a wired connection long enough so it can download the restricted drivers. It almost always does this on it's own. Another problem are laptops, and desktops, with older ATI graphics in them. ATI's Linux support is abysmal, and the open source drivers aren't quite up to snuff, although they are getting better. If you are buying a Dell and want to get a good Ubuntu experience, make sure it has either Intel or Nvidia graphics.
Same here. I have a Vostro that I ordered with the Nvida card and it works fine except for the WiFi.

---

### Post by yomuffin11 on 2010-03-18
Hello!  I have a Dell 1555 Studio with Ubuntu 9.04 and works very, very well! Waaaayy better than Microsoft Windows any day! I may wipe out my Windows just to show how much I love Linux! It is great!

---

### Post by Tikkyca on 2010-03-18
Almost any model can run great with ubuntu.

---

### Post by emptythevoid on 2010-03-18
> **jms-ubuntu-en said:**
> I have had good experience with a Precision M4300 / Ubuntu combination as a everyday utensil for about 2 years now. I Recommend :D

Question: 
Any experienses with Precision M6500 with Ubuntu so far? 
I noticed that there is an option to have it with RedHat EL 5.3 preinstalled, but I have to follow our company policy and so it will be delivered with Windows7 preinstalled. I'm going to install Ubuntu to it if there are not any bigger troubles noticed (and if the livecd test is a 'pass').

I got an M6500 through work just a few days ago, so I set it to dual boot with Win7 and Ubuntu 9.10.  Here are things that have happened on mine, but your mileage may vary.

The wireless needed proprietary broadcom STA drivers, and I installed the proprietary nvidia drivers for 3D effects as well.

For some reason, after running updates after the clean install, startup would fail on kernel 2.6.31-20-generic.  If I booted into 2.6.31-14-generic, it was fine.  It seemed to halt when you see the Ubuntu logo in the center of the screen before it takes you to the login screen, so I did this:

sudo gedit /etc/default/grub

	change the line
		GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
	to 
		GRUB_CMDLINE_LINUX_DEFAULT="quiet"

save, close, reboot

So that switches the boot to text only mode, which for some bizarre reason, seems to fix the problem.  Maybe it's something to do with the video mode, but as it works for now, I'll just wait for a newer kernel to make its way out and try again.

I'm having some issues burning DVDs with the HL-DT-ST DVD+/- GS20N slim slot loading drive that's in here, but I think it's just picky about what discs go in it, because it had problems in Win7 as well (with latest firmware).  Not sure what to make of that, and I'm still testing it.  I had similar problems with another HL-DT-ST drive in a Dell Inspiron 6000 where it just refused to burn on certain recordable DVDs.

Other than those (and aside from the DVD issue, I think those are minor worries), it seems pretty solid.  System Monitor reports 8 CPU threads on the Corei7. :D

---

### Post by jms-ubuntu-en on 2010-03-19
I have got a m6500 as well through work with Windows 7 preinstalled. Big disappointment at first was that it was equipped with ATI's graphics (Firepro M7740). 
I installed Lucid right away and after that I installed Windows 7 as virtual machine using virtualbox. 
ATI was not a big issue after all, and actually all hardware seems to work like a charm.

---

### Post by pizza-is-good on 2010-03-19
My Latitude E6400 runs karmic nicely. Very good hardware compatibility (Hail the Linux kernel!!!).
Web-cam, wireless, integrated mic, screen intensity control, keyboard back-light, speakers. All run good.

---

### Post by dirtrider1 on 2011-05-23
I currently have a few years old HP Pavilion dv6700 with AMD Turion X2 cpu and Nvidia graphics and it run's perfectly well. But beware of some of the newer HP laptops they may not work with any Linux Distro at all. There was an issue with the BIOS on one of the new HP laptop's I worked on, I can't remember exactly what it was but it was not compatible with anything but the Windows OS that came preinstalled, and good luck getting any support from HP whatsoever. Needless to say my next laptop will not be an HP as I run Ubuntu only on my laptop.

---

