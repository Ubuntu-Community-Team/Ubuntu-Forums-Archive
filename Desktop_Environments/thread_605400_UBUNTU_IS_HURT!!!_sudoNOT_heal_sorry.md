---
title: "UBUNTU IS HURT!!! sudoNOT heal sorry?"
date: 2007-11-07
forum: Desktop Environments
---

### Post by Kalibur on 2007-11-07
Here is my story about how ubuntu could not heal its self?  Such that I had to go surgical and perform multiple organ transplants to fix my ubuntu?  It all started with mythtv that ..you know what of a gorgeous application.  Something was wrong with its files and so I performed reinstallations, removed mythtv including config files - Ironically the configurations details kept coming back after each install no matter what and thats when i realized that they never really left (removed using 'sudo apt-remove mythtv*' and using synaptic for a more thorough uninstall) but the system couldn't forget the old myth stuff and I just need to start a fresh mythtv installation.  I really needed it to function and so.....

And so I become su so I can handle the biz of removing rouge elements manually (gksu nautilus)
I went here '/etc/init.d/' and deleted yes deleted mythtv-backend becoz it couldn't stick to my frontend anyway.  MUHAHAHAHA BAD su and then I tracked down all other mythtv elements and deleted them all HAHAHAHA.
Here is the logic:
If you install software files are created right?  But not with ubuntu 7.10 Gutsy Gibbon 64bit which is what am running am not sure about other ubuntus, you go try it on yours lol.  So anyway I after  nstallation was completed it said to me it could not start the mythtv-setup because of dependency  issues and I thought the whole idea of having automated install was to make sure all files required are installed. I mean it always tell me that in addition to the program i want to install ??? libraries and ???-data will also be installed.

So I got tired of being knocked about the box and decided to set myself free by thinking outside the box -  trashing the logic above, i set to invistigate the locations I had intially cleared  the myth files from and to my great surprise the files were absent.  :popcorn: yea this will keep me going a lil longer *chews on popcorn* 

So it turns out that all the time I was running installations the files where never (re)created, because all I found were empty folders.  So If install mythtv-backend successfully the files tten to the disk??? this dont make sense.  

So at the moment I have made these conclusions
1 - When you unstall somethings are not removed from my ubuntu they are just marked as absent when infact they are still there.
2 -  Unbuntu 7.10 does not create or heal itself once files are created they never leave and are assumed to exist forever and it never bothers to replace its missing components even when instructed to do so thru apt-get or synaptic (same thing i  know)

in a nutshell ubuntu is a human being without healing machinism and the only solution is to perform surgery and replace malfuctioning organs.
And thats what i did copied the files i delete earlier from another installation of gutsy and mythtv started working again properly this time so I reckon my original files got corrupt and my donated ones fixed it.

---

### Post by franket on 2007-11-07
I feel that too !! 

I think that may be we can solve a problem another way such as system restore.
I ever seen in this link

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

