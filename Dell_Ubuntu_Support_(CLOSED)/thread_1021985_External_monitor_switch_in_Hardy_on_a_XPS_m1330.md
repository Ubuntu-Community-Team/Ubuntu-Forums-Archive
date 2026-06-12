---
title: "External monitor switch in Hardy on a XPS m1330"
date: 2008-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by futuroimperfetto on 2008-12-26
Hi,

I've got a Dell XPS m1330 with a 8400 GS nVidia card. I bought it this summer with Gutsy on it and then upgraded to Hardy. I'm still running Ubuntu 8.04 and haven't decided to upgrade to Intrepid for various reasons.

I use my laptop a lot to go to conferences, but the one time I tried it on an external projector it failed me and I am curious if there is a fix for this.

Is there any script I can write or package I can download to re-activate the FN+F8 combination? 

More generally, if I plug in the VGA cable into my laptop and then turn it on, I still don't get anything projected outside the computer. Somehow, the computer does not detect the projector.

Any idea?

Thanks!

---

### Post by futuroimperfetto on 2009-01-07
**[SIZE="5"]Bump![/SIZE]**

---

### Post by acreech on 2009-01-08
I just figured out how to get an "Infocus" projector to work with my Intrepid system. I added the following lines to my xorg.conf file at the bottom where it says "Section Device"

> 
# Option "TwinView" "Yes"
# Option "TwinViewOrientation" "Clone"
# Option "MetaModes" "1400X1050,1680X1050,1680X1050"


On the third option, make the first set of numbers what you want you projection resloution to be. When I want to use the projector I remove the "#" from each line, save & close (both gedit and terminal), then Ctl+Alt+Backspace and then log back in.

This transfers my laptop monitor to the projector. One thing to note here is it turns your laptop monitor completely off.

I also found this website, but have not got the method that is suggested to work....

[http://www.len.ro/2007/03/external-m...aptop-nvidia-/](http://www.len.ro/2007/03/external-m...aptop-nvidia-/)

Any other suggestions on this would be great.

---

### Post by Gooler on 2009-01-08
Have you tried installing nvidia-settings?
That made it for me using a Samsung t200hd via VGA

---

### Post by acreech on 2009-01-08
> **Gooler said:**
> Have you tried installing nvidia-settings?
That made it for me using a Samsung t200hd via VGA

I do have have nvidia-settings installed. I have looked through that and am not sure how to adjust it or use it to make the external monitor or projector work. 

Can you give advice on how to use it?

Thanks

---

### Post by futuroimperfetto on 2009-01-11
Dear acreech and Gooler,

 Thank you both for your replies. I haven't had the chance to test the changes suggested by acreech, but hope to do it this week. I've got two questions, though:

To acreech, making the change you suggested transfers your video to the projector. Do you need to make this change in xorg.conf anytime you plug it to a projector or is it a one-time change?

To Gooler, I've got nVidia-settings installed on my machine too. How can I use it to make an external device work? I just noticed that in the "X Server Display Configuration --> Display" window, there is a "detect display" button. Is that the one we should try?

Cheers

---

### Post by Gooler on 2009-01-11
I did this long ago, but I don't remember doing anything special, I connected the VGA to the monitor, hitted Fn+F8 a few times, went to nvidia-settings and selected the resolution...

By the way, there is a BIOS upgrade at Dell.com, the A15 revision, and maybe that solves something:

Fixes/Enhancements
------------------
1. Enhance Fn+F8 function

---

### Post by futuroimperfetto on 2009-01-11
Dear Gooler,

 Thanks for your update. You touch a pretty sensitive issue. It appears to be a well known issue that the nVidia 8400 GS card is possibly defective and it might die at some point. Here is one of many official links regarding the issue and the extension of the warranty:

[http://en.community.dell.com/blogs/direct2dell/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx]("http://en.community.dell.com/blogs/direct2dell/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx") (extension of warranty for failure of the nVidia card)

To reduce the likelihood of having your card fried, one should have BIOS A12 or greater, which have a smarter fan control and fire up the fan whenever the heat goes up. My version came it with A12 preinstalled.

How do you update the BIOS from within Ubuntu? The file that is provided here

[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R207196&SystemID=XPS_M1330&servicetag=&os=WLH&osl=en&deviceid=14178&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=290116]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R207196&SystemID=XPS_M1330&servicetag=&os=WLH&osl=en&deviceid=14178&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=290116") (link to BIOS update A15)

is a Windows executable. I'm curious to try the BIOS change, but also a bit scared because I've been following the graphic card issue on many forums and there seems to be no general agreement on what BIOS is better or if changing the BIOS makes anything good for your laptop.

What do you recommend?

In any case, I installed nVidia-settings for the purpose of monitoring the temperature of my card and this week I'll try to plug a monitor again and see if I can make it work!

Thanks!

---

### Post by Gooler on 2009-01-12
I know this well as mine died about 4 months ago, and I upgraded to A12 as soon as it was published. I think that if your's faulty, it's going to die soon or after, no matter what. A software patch can't solve a hardware manufacturing problem.

For the BIOS upgrade, look here: 
[http://ubuntuforums.org/showpost.php?p=5270360&postcount=5](http://ubuntuforums.org/showpost.php?p=5270360&postcount=5)

---

### Post by futuroimperfetto on 2009-01-12
Dear Gooler,

**[SIZE="3"] External Output.[/SIZE]** I've finally tried nVidia-settings on a monitor and on a projector. It's easier than I thought. Just need to detect the device and tell it to go on an external device. I had some problems with the projector, but it still detected it (though it displayed only a corner of my screen). Will tinker with it later.

**[SIZE="3"]BIOS update.[/SIZE]** Before I follow your instructions, I wanted to ask you: this solutions install the latest available BIOS directly from Dell, I understand. Is it possible to switch back to a previous BIOS (or choose the one you'd like installed)?

**[SIZE="3"]nVidia 8400 GS troubles.[/SIZE]** On another note, since you mentioned troubles with the nVidia card, I'd like to ask you a bit about it.

When did you buy your XPS? What do you usually do with it?

Since I've bought it I've tried to be maniacally careful with it: I've installed nVidia-settings to monitor the temperature which I always try to keep at less than 54 degrees (It goes to 61 when I watch flash videos). I know that this might only delaying the problem.

Did you have it changed under warranty? How was your experience with Dell support?

Thanks for your help!

Cheers

---

### Post by Gooler on 2009-01-12
> **futuroimperfetto said:**
> 
**[SIZE="3"]BIOS update.[/SIZE]** Before I follow your instructions, I wanted to ask you: this solutions install the latest available BIOS directly from Dell, I understand. Is it possible to switch back to a previous BIOS (or choose the one you'd like installed)?

I really don't know, but every update is supposed to contain previous changes and work better than the previous version...

> **futuroimperfetto said:**
> **[SIZE="3"]nVidia 8400 GS troubles.[/SIZE]** On another note, since you mentioned troubles with the nVidia card, I'd like to ask you a bit about it.

When did you buy your XPS? What do you usually do with it?

I bought mine around November 07, I've used it just as you would use any other laptop, no special cares with the graphic card or the temperatures. I've played with it (bought it with Vista), I've seen HD videos, and mainly used it for programing and Internet reading.

> **futuroimperfetto said:**
> Since I've bought it I've tried to be maniacally careful with it: I've installed nVidia-settings to monitor the temperature which I always try to keep at less than 54 degrees (It goes to 61 when I watch flash videos). I know that this might only delaying the problem.

Did you have it changed under warranty? How was your experience with Dell support?

Thanks for your help!

Cheers


One day, without any previous problem, the screen started to show strange colours bars and after that I couldn't get to the OS, so I called Dell Warranty (I've got Bussines Warranty) and two days after a technician came home to replace the mainboard. 

This was actually the 2nd time that needed to call Dell Support, as first time the screen had a full row of blank pixels on top.

Back to this 2nd time, the technician didn't closed right the laptop and now it lacks one screw :(, I had to open it up and put the things in the right places in order to make it close ok again. It was in Badajoz, so if you ever need a repair, try to avoid requesting it there :D. First time the repair was in Granada and it was great.

Saludos.

---

### Post by Gooler on 2009-01-12
nm

---

### Post by futuroimperfetto on 2009-01-15
Hi Gooler,

 Sorry for the late reply. Thanks for all the info about nVidia-settings, updating the BIOS and your experience with Dell support.

I also have at-home international support (including the CompleteCare protection in case an avalanche falls on it) and am hoping it's going to be good in case of need. By the way, I didn't expect to get an answer from somebody else also living in Spain :) Now you've also given to me first-hand experience of support in my current country :D

Meanwhile, I keep my paranoia and monitor the temperature of the computer while I work!

So long and thanks for all the fish

Cheers

---

### Post by acreech on 2009-01-19
> **futuroimperfetto said:**
> Dear acreech and Gooler,

 To acreech, making the change you suggested transfers your video to the projector. Do you need to make this change in xorg.conf anytime you plug it to a projector or is it a one-time change?



Sorry for the late reply on this. You have to change it every time, or else you will not be able to see your monitor on the laptop. so prior to putting the projector away I put the "#" in front of the 3 lines that I added. save and then restart. 

This will put the display back to your laptop. This is not the most ideal setup, but it did do the trick for me. 

acreech

---

