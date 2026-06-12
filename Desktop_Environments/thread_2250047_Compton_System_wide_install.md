---
title: "Compton System wide install?"
date: 2014-10-26
forum: Desktop Environments
---

### Post by Ubu1son on 2014-10-26
My PC has an old nvidia gt240 card. I want to change the compositor to compton as mentioned on these forums. [http://ubuntuforums.org/showthread.p...5#post12644745]("http://ubuntuforums.org/showthread.php?t=2144468&p=12644745#post12644745")

It says to add PPA's, but I read another place that's its in software  center. Can I just install from SC, and will it update normally, or must  I add the PPA's?

Next it says:
 	 		 			 			 				you will want to create your compton config file. Save the file as "~/.compton.conf". 			 		


 	
 
Is this added in the home folder, so /home/a1/.compton.conf?   If  so, will these settings only work per logged in user, or for any user  that logs in?

There is an example conf settings in the thread to use, but it was  posted on late 2013. There is another more newer conf settings posted by  user emblem parade [http://ubuntuforums.org/showthread.p...0#post13123340]("http://ubuntuforums.org/showthread.php?t=2244519&p=13123340#post13123340")

Should I use it instead?

I must then Add the command to the auto start-up  	

 	```
**compton -b**

```

but again, I find a different post to use
 

 
```
 	 	Add:

Name: "Compton"

Description: "Compositor"

Command: "/usr/bin/compton -b" 

```
Do they both achieve the same thing?



Can this be installed system wide instead of per user?



Lastly, many threads say it stops screen tearing,  I only noticed major tearing or flashing while watching flash in Firefox.  
Installing nvidia driver fixes it.  Can compton remove tearing from flash with the opensource driver, or it only works with nvidia?


thanks.

using xubuntu 14.04lts

---

