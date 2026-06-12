---
title: "ubuntu 9.04 freezing constantly."
date: 2009-06-04
forum: General Help
---

### Post by DAGATH on 2009-06-04
Hi folks, 

I have ubuntu 9.04  installed on my laptop. At first all was well but now it just freezes for no reason. i have done very little in with ubuntu since i first installed it. In fact i think i could say with all honesty that i have only used it maybe 20 times. its a big problem for me as i used to have ubuntu 8.04 on a previous laptop and loved it. 

I would very much appriciate any assistance you could offer. is there a repair program perhaps? what steps should i take. 

Basically the problem is that i boot it up, thats fine. i open Firefox it freezes. i open any program in fact and it just freezes. Right now im talking you you from the install disk as i cant do anything with the installed version. :( I thought it might be ram but the laptop has 2 gig ram. 

Really this kind of thing is beyond my knowledge base, im new to ubuntu and i have only touched the surface of its capabilities. 

Hope you guys can shed some light on this for me. I really dont want to be using MSxp or any other MS product for that matter. 

Kind Regards.
D.

---

### Post by epek on 2009-06-04
On what kind of machine are you working at?
If it ist a Laptop with an integrated intel graphics chip (i945), there are currently known problems with 3D-acceleration with xorg and compiz.

If that is the case, please turn off compiz (desktop effects) and you have a stable system again. Intel is working on a remake of their drivers, but it will take some time.

I had the problem on an hp nx7400 laptop especially after hibernating - the system seemed to work for some minutes and then suddenly "froze".

If that is not your specific situation, please give us more information about the machine and other hints.

regards
erich

---

### Post by DAGATH on 2009-06-04
> **epek said:**
> On what kind of machine are you working at?
If it ist a Laptop with an integrated intel graphics chip (i945), there are currently known problems with 3D-acceleration with xorg and compiz.

If that is the case, please turn off compiz (desktop effects) and you have a stable system again. Intel is working on a remake of their drivers, but it will take some time.

I had the problem on an hp nx7400 laptop especially after hibernating - the system seemed to work for some minutes and then suddenly "froze".

If that is not your specific situation, please give us more information about the machine and other hints.

regards
erich


Hi epek, 
Tnx for the reply. 

Yes indeed its a laptop and as u say integrated chip i945. its a Dell Latitude D630. 
as for "compiz" i am running the comp with no visual effects at all, but im not sure what compiz is exactly and indeed where to turn it off. Where do i do that? i tryed the ubuntu help button to get info about compiz but guess what... it will not work ouch! :(

I have gone through the recovery mode where i spent at least 2 hours hittin the "Y" key repairing stuff i have no understanding of. (but it seemed like the right thing to do)
 Since that it is working better, i have also un-installed any recent programs that i added. namely,  Chromium, An anti virus program (the name escapes me), Wine, and Galeon browser.

---

### Post by Gina on 2009-06-04
I have Jaunty on three machines at present and two of them occasionally freeze needing a cold restart.  Worst is my AMD64 desktop but my laptop does it occasionally.  I also run Jaunty on my ancient AMD K6-2 desktop running my weather site webcam continuously day and night (OK so webcam is useless in the dark but it's there at dawn when I'm asleep) and I've had no system freezes that I know of.  But this is running just a minimal install plus Ubuntu desktop and **webcam** utility.

---

### Post by leandromartinez98 on 2009-06-04
> **DAGATH said:**
> Hi epek, 
Tnx for the reply. 

Yes indeed its a laptop and as u say integrated chip i945. its a Dell Latitude D630. 
as for "compiz" i am running the comp with no visual effects at all, but im not sure what compiz is exactly and indeed where to turn it off. Where do i do that? i tryed the ubuntu help button to get info about compiz but guess what... it will not work ouch! :(

I have gone through the recovery mode where i spent at least 2 hours hittin the "Y" key repairing stuff i have no understanding of. (but it seemed like the right thing to do)
 Since that it is working better, i have also un-installed any recent programs that i added. namely,  Chromium, An anti virus program (the name escapes me), Wine, and Galeon browser.


Indeed there are problems with the Intel 9*5 drivers in 9.04. 
You want to follow the indications of this thread:

[https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/jaunty/+source/xserver-xorg-video-intel/+bug/359392)

Particulary this one, it is harmless and seems to work:

[Patch for Jaunty]
A low-risk workaround that has proven effective at eliminating freezes, or at least greatly reducing their frequency, is to increase the Virtual framebuffer size. Some users do this locally as a matter of course to gain dual-head support, so this setting has received extremely widespread testing already.

The patch for Jaunty causes the Virtual size to be set to 2048x2048 if it is not otherwise specified. Users can still override this with their own settings, larger or smaller, as desired.

---

### Post by Shunsuke_01 on 2009-06-04
> **DAGATH said:**
> as for "compiz" i am running the comp with no visual effects at all, but im not sure what compiz is exactly and indeed where to turn it off. Where do i do that?
Try typing "metacity --replace" without the quotation marks in the terminal and see what happens. It should disable compiz and stop any compiz-related errors.

---

### Post by DAGATH on 2009-06-04
Ok, i have run this "metacity --replace" and am awaiting results through just going about my normal business on the laptop. i will let you know what happens. 
Next
When i was running the recovery mode it was showing ALOT of I/O errors which i choose to fix. this has helped alot but there is still problems. for instance. i just tried to open a simple JPEG image and it failed to open reporting an input output error. this seems to be the crux of the problem with everything i am doing. 

Are the input output errors related to the integrated chip i945??? surely not... any suggestions for that? 

Also i should mention that, if i go through the recovery mode and fix issues, then start the system all is fine. however when i restart the system then it all goes belly up again, so as it stands, i have to go to recovery mode every time i start the system just so things run smoothly. im sure you can understand that this is very frustrating.

---

### Post by DAGATH on 2009-06-04
a quick update on the errors in the recovery mode.

I get loads of errors which read like this
"Buffer I/O error on device sda5 logical block" then a string of numbers, but there are two many errors and different sets of numbers to list here. 

Again the questions stands about the  integrated chip i945??? could this be the cause of the errors? 

cheers

---

### Post by Iusedtowearatie on 2009-06-04
This has been discussed at great length in this thread:
[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

Towards the end, the discussion seems to lean towards kernel upgrade to solve the problem, alt remain on 8.10.

---

### Post by leandromartinez98 on 2009-06-04
> **DAGATH said:**
> a quick update on the errors in the recovery mode.

I get loads of errors which read like this
"Buffer I/O error on device sda5 logical block" then a string of numbers, but there are two many errors and different sets of numbers to list here. 

Again the questions stands about the  integrated chip i945??? could this be the cause of the errors? 

cheers

This is a filesystem error. Your harddrive may have a problem, or there may be many corrupted files. You should use fsck to analyze to check the harddrive for errors, probably, but I'm not going to suggest exactly how because I'm not sure.

---

### Post by Iusedtowearatie on 2009-06-04
> **leandromartinez98 said:**
> This is a filesystem error. Your harddrive may have a problem, or there may be many corrupted files. You should use fsck to analyze to check the harddrive for errors, probably, but I'm not going to suggest exactly how because I'm not sure.

Agreed, I didn't read all the way down the thread, only the "freeze" part.

---

