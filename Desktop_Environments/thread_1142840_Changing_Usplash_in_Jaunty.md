---
title: "Changing Usplash in Jaunty"
date: 2009-04-29
forum: Desktop Environments
---

### Post by Sub101 on 2009-04-29
Hi, I would like to know if anyone has been able to change the Usplash in Jaunty?

When I attempt to change it the pc boots in verbose mode. If any one has any ideas on how to fix this I would appreciate it. 

Thanks for your time.

---

### Post by celticbhoy on 2009-04-29
What method are you using to change it?

I have changed mine with startup manager without probs.

---

### Post by Sub101 on 2009-04-29
Ive tried using startup manager and by directly updating usplash. Neither seem to work though. 

Do you have a vga setting in Grub?

Its annoying as it has always worked before.

---

### Post by zasq on 2009-05-05
Hi!
I tried to change it too (with startup manager). Only the default ubuntu theme works. Have you guys found a solution?
Thanks!

---

### Post by manpoole on 2009-05-05
same here changed the usplash theme using startup manager and it shows no splash at all.

---

### Post by drs305 on 2009-05-05
I recently tried to help a user change a splash screen that replaced his log-off screen but not his boot screen. I initially recommended StartUp-Manager to him but it didn't work. I found I had the same difficulties as the OP.

I then played around with the usplash screens myself and found a combination of commands that worked for me (but not for him). Here is the thread. Post #7 is what worked for me:
[http://ubuntuforums.org/showthread.php?t=1131763]("http://ubuntuforums.org/showthread.php?t=1131763")

---

### Post by manpoole on 2009-05-06
I have tried several Usplash themes and none seem to work in Jaunty when using Startup Manager

---

### Post by Don1500 on 2009-05-06
I can not get the default Upspalsh to work right
the logo and progress bar are off set down an dto the right about 1/3 of the screen. If I try to load a different splash it goes to a blank screen (Out of Range)
My VGA is set to VGA=791 in grub

I have a ATI 9600 adaptor and I know it is not supported, that's why I'm not too upset, yet. I'll be getting a new adaptor soon and I'll get upset then.

---

### Post by drs305 on 2009-05-06
> **Don1500 said:**
> I can not get the default Upspalsh to work right
the logo and progress bar are off set down an dto the right about 1/3 of the screen. If I try to load a different splash it goes to a blank screen (Out of Range)
My VGA is set to VGA=791 in grub

I have a ATI 9600 adaptor and I know it is not supported, that's why I'm not too upset, yet. I'll be getting a new adaptor soon and I'll get upset then.

Have you tried other vga settings? Here is a site that lists various configurations: [http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers")

If you don't know how to enter a new vga setting at boot to temporarily check out a new one, here is a page I just updated this week:  [_BootOptions_]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Sub101 on 2009-05-06
Im still having the issue and have tried numerous other VGA options. If anyone has any ideas id appreciate it.

---

### Post by aniruddha on 2009-05-09
Hey, compiling themes from their source code (if available) seems to work. For e.g. when you are browsing gnome-look download the source code (it should be marked with a link). Go to the directory where you have extracted it. then run:

sudo make
sudo make install. 

That got these themes working for me:

[http://gnome-look.org/content/show.php/Crunchy+Branch-Usplash+Jaunty+%26+Intrepid?content=102489](http://gnome-look.org/content/show.php/Crunchy+Branch-Usplash+Jaunty+%26+Intrepid?content=102489)

[http://gnome-look.org/content/show.php/Heliocentric+-+Usplash?content=103632](http://gnome-look.org/content/show.php/Heliocentric+-+Usplash?content=103632)

see if they (or anything else works). 

no worries

---

### Post by cojeda on 2009-07-30
I have not had trouble changing usplash often startupmanager in jaunty.  

 Eg:  
 Choose a usplash on this site download it to Images folder.
Launch startupmanager 
Select tab Aspect and go to Admin Themes Usplash button.
Next, click Add button, and select the images directory from the downloaded file. 
 Click on listbox "usplash theme" and select name of downloaded file
Click  close button.
 
Pre-check from the terminal as follows:  

 cristian$ sudo usplash-r downloaded file appears correctly.
ALT-F7 to exit

---

### Post by linux000019 on 2009-08-26
this thread maybe has been started again elsewhere, i found this first though so here goes.

First attempt: didn't even try usplash, downloaded splashy and gsplashy. failing after a good 8 hours of attempting to change, i shutoff computer.


2nd attempt(day 2): i removed splashy, couldnt figure out how to remove gsplashy so its somewhere haunting my system. 
reinstalled usplash, found many tutorials; looking good and bright so far. after 3 hours or so i reboot and find that NOTHING is working. plus now i have an annoying beep when i restart; i fixed the beep with a blacklist i picked up off another google search.
so now no splash on bootup, lots of text. better than the completely blank screen i got after trying splashy though. also, the shutting down screen gave me a shot, it started working again; for 1 shutdown. 


day 3: here i am, on the ubuntu forums after 3 hours of configure and such. i actually finaly made the customized splash screen i want to use when i get this working instead of the preconfigured splash screens i tried with splashy and usplash. this is MISLEADING, what i mean is nothing works, only now i've got the background picture ready to use when something is WORKING.


alright so if ur gonna ask heres the info: laptaop 1080x768, followed the OFFICIAL ubuntu change usplash page. yes i got tons of dependancies, and Start up Manager.
as of now, 3 days ago the default ubuntu splashes worked. now all i get is text.

What do i do?

---

### Post by marifzein on 2009-08-26
Just trying to help ...

If u have any trouble to customize usplash , try replace it with splashy ...
[http://www.makeuseof.com/tag/how-to-easily-change-your-usplash-screen-in-ubuntu/](http://www.makeuseof.com/tag/how-to-easily-change-your-usplash-screen-in-ubuntu/)


if u get error when installing splashy try this 
[http://ubuntuforums.org/showthread.php?t=1243129](http://ubuntuforums.org/showthread.php?t=1243129) 

I've been frustating to customize my boot splash screen for long time :(, and now I'm satisfied after change to splashy.:popcorn:
Sorry 4 my bad english.....

---

### Post by linux000019 on 2009-08-27
> **linux000019 said:**
> this thread maybe has been started again elsewhere, i found this first though so here goes.

First attempt: didn't even try usplash, downloaded splashy and gsplashy. failing after a good 8 hours of attempting to change, i shutoff computer.


2nd attempt(day 2): i removed splashy, couldnt figure out how to remove gsplashy so its somewhere haunting my system. 
reinstalled usplash, found many tutorials; looking good and bright so far. after 3 hours or so i reboot and find that NOTHING is working. plus now i have an annoying beep when i restart; i fixed the beep with a blacklist i picked up off another google search.
so now no splash on bootup, lots of text. better than the completely blank screen i got after trying splashy though. also, the shutting down screen gave me a shot, it started working again; for 1 shutdown. 


day 3: here i am, on the ubuntu forums after 3 hours of configure and such. i actually finaly made the customized splash screen i want to use when i get this working instead of the preconfigured splash screens i tried with splashy and usplash. this is MISLEADING, what i mean is nothing works, only now i've got the background picture ready to use when something is WORKING.


alright so if ur gonna ask heres the info: laptaop 1080x768, followed the OFFICIAL ubuntu change usplash page. yes i got tons of dependancies, and Start up Manager.
as of now, 3 days ago the default ubuntu splashes worked. now all i get is text.

What do i do?


Day 4: YAY i followed a JAUNTY guide from here >> [http://www.flyninja.net/?p=884](http://www.flyninja.net/?p=884)
now i am seeing my image on boot. now to change the size and get rid of the black rectangle on bottom of image are my next steps..... any suggestions?

---

### Post by armageddon08 on 2009-08-27
I changed mine through startupmanager without any problems. But then again I used Usplashes specifically having jaunty versions.

---

### Post by linux000019 on 2009-08-27
update : usplash failed; i failed; when changing the size of image to 1028x768.
against instincts, i reinstalled splashy. this program is completely incompatable with jaunty. anyone saying different hasn't tried it. the reports of failures are innumerable. im now back at square 1 with a black screen i got from splashy.

---

### Post by marifzein on 2009-08-28
1. i have same problem with usplash to change the size and get rid of the black rectangle on bottom of image(i'm getting frustated) ...and after changing to splashy there is no problem anymore.

2. have you add 
splash vga=791
at the kernel line  in /boot/grub/menu.lst

3. you should enable 'Use Splashy from initramfs' in Startup-Manager , Advanced tab

4. First, try to test with default splash image from splashy. Test it via preview theme button in Startup Manager, you will see the preview of splash theme, if you dont see anything..well thats another problem .

 

hope this help...

---

### Post by linux000019 on 2009-08-28
> **marifzein said:**
> 

4. First, try to test with default splash image from splashy. Test it via preview theme button in Startup Manager, you will see the preview of splash theme, if you dont see anything..well thats another problem .

 

hope this help...

and still no solution

stuck with default ubuntu usplash theme for now

---

### Post by linux000019 on 2009-08-28
first of all, if you read recent news in splashyville, the developers are crowded on the bug site over a install error/compatibility error.

as recently as 6-26 they are looking for testers to help get the kinks out.

i can't install the newest version im on a single processor. the old version installs after doing a force overwrite. 3.10 i think. 

gsplashy is recommended on the backend tutorials, i think its really easier to use the splashy_config.

still, there weren't any themes i could get to work when i used splashy. plus gsplashy popped up with file's missing errors for me, on the bug tracking site only 2 other people reported the same error and they didnt get any help so i suppose i out with Splashy.

---

