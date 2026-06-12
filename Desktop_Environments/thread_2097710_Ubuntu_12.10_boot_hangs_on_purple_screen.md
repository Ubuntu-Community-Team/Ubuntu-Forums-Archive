---
title: "Ubuntu 12.10 boot hangs on purple screen"
date: 2012-12-24
forum: Desktop Environments
---

### Post by brickmasterj on 2012-12-24
I've got a problem with my Ubuntu 12.10 installation.
A few weeks ago I've installed Ubuntu 12.10 on my machine (dual booted with Win7), and everything worked perfectly fine.
Now, I'm kinda a lazy person, so I never install updates. But the update notification was irritating me, so I was like 'screw it, install 200+ updates'. So I did.
But when I rebooted, it showed Grub fine, then it got to the purple screen, but then... Nothing happens. It just keeps showing a purple screen, forever...
Now, I've already tried the 'boot-repair' tool via the Live CD (USB in my case), didn't work.
I think (but I may be wrong) that it is something GPU related. So a lil' extra info: GPU is *AMD Radeon HD6570*, with *AMD Catalyst 12.11 x64 Beta* drivers. Ubuntu installation is 64-bit.
I appreciate the help :-) Don't wanna use Windows too often ;-)

---

### Post by grahammechanical on 2012-12-25
There are a couple of things that you could try.

1) At the Grub menu select Recovery mode and then select Resume. See if that gets you to a desktop.

2) At the Grub menu press E. That will put Grub into Edit mode and you can edit the boot options for Ubuntu. Find the line that says 'quiet splash' and put in front of those words nomodeset. Press F10 to boot. That should load Ubuntu with trying to set a video mode.

3) you can edit out the 'quiet splash' options and then press F10 to boot. Now when Ubuntu stops loading you may see an error message giving information as to why it has stopped. That information may give a clue as to what is wrong.

You may need to re-activate the video driver.

Regards.

---

### Post by brickmasterj on 2012-12-26
> **grahammechanical said:**
> There are a couple of things that you could try.

1) At the Grub menu select Recovery mode and then select Resume. See if that gets you to a desktop.

2) At the Grub menu press E. That will put Grub into Edit mode and you can edit the boot options for Ubuntu. Find the line that says 'quiet splash' and put in front of those words nomodeset. Press F10 to boot. That should load Ubuntu with trying to set a video mode.

3) you can edit out the 'quiet splash' options and then press F10 to boot. Now when Ubuntu stops loading you may see an error message giving information as to why it has stopped. That information may give a clue as to what is wrong.

You may need to re-activate the video driver.

Regards.

Ok, now I've tried the first option already, but forgot to mention it. What happens, is when I select 'Resume' it gives a warning about graphics drivers, and then drops to console. There I can login etc., but after around 2 min the console vanishes and a (GUI) popup shows up saying that Ubuntu will run in 'Low Graphics mode'. For some reason my mouse is not detected there so I can only press 'Enter' to 'OK', and then I get a popup asking what I want to do, but it doesn't react either keyboard or mouse input, so I'd have to restart my pc.

Now, I'll try the the second and third action ASAP. Thanks anyway.

---

### Post by sifterr on 2012-12-28
Hi Brickmasterj,

I have a Toshiba Satelite and experience  problems when installing  Ubuntu 12.10 on it. This included the monitor never turning on  when  resuming suspend, suspend resuming immediately for no reason,  and  frequently only a  purple blank screen when rebooting.
I read many posts on the issue and found one simple solution which fixed all the above problems.

 Eduard's Post here [http://askubuntu.com/questions/12009...-purple-screen]("http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen")    pointed out that amd video cards cause many of these problems.  Anyway's the solution was to install the AMD package from the Ubuntu  repository.

Then do the following commands once you're dropped to the root shell:
  sudo apt-get update 
sudo apt-get upgrade 
   sudo apt-get install fglrx     
sudo aticonfig --initial
sudo reboot 

Hope this fixes your problem.

sifterr
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12426855") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12426855")

---

### Post by brickmasterj on 2012-12-29
> **sifterr said:**
> Hi Brickmasterj,

I have a Toshiba Satelite and experience  problems when installing  Ubuntu 12.10 on it. This included the monitor never turning on  when  resuming suspend, suspend resuming immediately for no reason,  and  frequently only a  purple blank screen when rebooting.
I read many posts on the issue and found one simple solution which fixed all the above problems.

 Eduard's Post here [http://askubuntu.com/questions/12009...-purple-screen]("http://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen")    pointed out that amd video cards cause many of these problems.  Anyway's the solution was to install the AMD package from the Ubuntu  repository.

Then do the following commands once you're dropped to the root shell:
  sudo apt-get update 
sudo apt-get upgrade 
   sudo apt-get install fglrx     
sudo aticonfig --initial
sudo reboot 

Hope this fixes your problem.

sifterr
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12426855") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12426855")
Ok thanks, but what I did was just 'amdconfig --initial -f' and that fixed the problem, sort of. After doing that there was no way to get OpenGL working (even reinstalling drivers), so at the end I decided to just reinstall my system...

But thanks for the help anyways!

---

### Post by albanee on 2013-03-30
hi im having gthe same problem, im using ubuntu 12.10 64 bit with dual operating system (windows 8 and windows xp). I dont have the grub menu, windows 8 gives an option to choose either windows 8 or other versions. 
The screen freezes on the purple/ dark pink screen before i could put my login. 
Can someone please tll me the solution?
Im relatively new your help is much appreciated.

---

