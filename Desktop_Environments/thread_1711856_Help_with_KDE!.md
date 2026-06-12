---
title: "Help with KDE!"
date: 2011-03-21
forum: Desktop Environments
---

### Post by superstarks on 2011-03-21
So I decided to  give Kubuntu a try and since I did I had some problems with my sound  card (nothing major, but I want to go back to the pure Gnome Ubuntu). I  tried the command located at this link [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome) but ended up getting up an error in my terminal that read:

Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
E: Broken packages


This isn't the end of the world if I can't understand the KDE and go  back to pure Gnome.. but if anyone has any suggestions it would be  greatly appreciated.

I'm running Ubuntu 10.10 and I tried the KDE uninstall from Gnome desktop.

Thanks!
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]    		 		 		 		 		
[URL="http://ubuntuforums.org/newreply.php?do=newreply&p=10584202"]
[/URL]

---

### Post by ankspo71 on 2011-03-22
Hi,
Try using the following commands to refresh your repositories and  fix any dependency problems that may be on your system:
```
sudo apt-get update
sudo apt-get install -f
```
Now try using using the "pure gnome" command again. 

If that doesn't help...
Are any of those java related packages that you listed installed on your system? If they are and you don't need them it might help to remove them, then try the "pure gnome" command again. 

I can't imagine why removing Kubuntu and reinstalling Ubuntu would want to install Java though. 

Hope this helps.

---

### Post by ankspo71 on 2011-03-22
Hi again,
I was reading another thread about something similar and it seems a certain package called 'libgif4' was causing the errors. The workaround is to not uninstall that package while removing Kubuntu.

See this forum thread (post #15) for more details:
[http://ubuntuforums.org/showthread.php?t=1579169&page=2](http://ubuntuforums.org/showthread.php?t=1579169&page=2)

---

### Post by Alejandro Nova on 2011-03-25
Try to use Aptitude instead of apt-get. It's better at not leaving messes like those.

---

