---
title: "Adding Debian Repositories !!"
date: 2006-02-06
forum: Desktop Environments
---

### Post by Seinfeld on 2006-02-06
Hi

Is it OK to add Debian official reposotries (e.g. debian testing) to the ubuntu sources.list ?

I have been using Debian (Mepis being a DCC) for some time and now have switched to Ubuntu and very happy with it. However, there are some packages there that are available right away (e.g. Azureus and some more). Is it OK just to add the Debian repository. ??

To be honest, when I tried that; my available packages (on synaptic) greatly expanded by about 2000 more. I am not sure if what I have done is OK or might have caused any conflict or deletion on some packages... Did it ?? What exactly happens for similar packages in this case??  

Also, did I loose any Ubuntu packages, being replaced by a new package from Debian as result, in other words did I do something that's not recommended ?

I also noticed that the "update Manager" does not show automatic upgrades automatically, was that relevant ??:confused: 
 
Your detailed explanation is highly appreciated.. :) 

Thanks a million

---

### Post by RAOF on 2006-02-06
Adding Debian repositories is a recipe for unpleasantness.  You will almost certainly break your Ubuntu at some point - a critical library will be overwritten by a Debian one with a higher version number, and the Debian packages aren't guaranteed to be binary compatible.

Unless you installed some software after you added the Debian repository, nothing will have been done to your system.  Just remove the repo from your sources.list.

If you want cutting-edge stuff, might I suggest dist-upgrading to Dapper?  It's been pretty stable for me.  Your milage may vary ;)

---

### Post by newuser111 on 2006-02-07
bad idea, i am using only ubuntu official and 3rd party repos and have 17950 packages available in synaptic

i can post my sources.list if you like

use debian if you want debian repos, a lot of things compiled for debian wont even install on ubuntu unless you start changing a lot of dependencies

---

### Post by Seinfeld on 2006-02-07
Very generous replies.. I see.. that is why when I tried to install "mplayer" for example while having Debian testing repos active (uncommented), I got a library dependency problem. I commented out the debian repos, I did apt-get update to retrieve the original Ubuntu sources.list status, tried again and BINGO, installed quite smoothly without any problem.. 

You are right guys..;) 
Cheers
Thanks a lot. \\:D/

---

### Post by Seinfeld on 2006-02-08
When you remove any repository from synaptic by going Synaptic->Settings-> Reposotories and remove a custom or a Ubuntu one. It COMPLETELY erases it from sources.list and not just comments it out "#". So I have to back up sources.list everytime I add/remove a repository and  have to google to find it back..:mad: 
Well, I have been using Mepis/Debian, the case is not like that there, it just comments the removed repository line by #ing it. I see this more logical .. 
What do you think or recommend??

Help ???

Thanks a lot

---

### Post by nix4me on 2006-02-08
The checkbox next to the repository should allow that line to be #.

nix4me

---

### Post by BlackJack on 2006-02-08
[QUOTE=newuser111]bad idea, i am using only ubuntu official and 3rd party repos and have 17950 packages available in synaptic

i can post my sources.list if you like

use debian if you want debian repos, a lot of things compiled for debian wont even install on ubuntu unless you start changing a lot of dependencies[/QUOTE]

Having a list of available repositories would be a blessing. I, for one, would greatly apreciate your list. Is there anyplace on-line that lists all the available repositories out there?

Thanks..........

---

### Post by Seinfeld on 2006-02-08
nix4me

I am sorry I did not get it.. For example, I added the other day the skype repos. when I removed it from synaptic settings window, it completely erased the sources.list line for skype.. That is what I mean, is there a way just to comment it other than going into the file and commenting it?? I am not that lazy ;)  but the Synaptic window shows all of the repos in detail also it is safer to add/remove by just clicking a button 
 
Can you please walk me through this, I do not figure out which checkbox  you mean in case of removal..

BlackJack.. Thank you.. I am asking the very same questiony ou posed, especially that I cannot retrieve all of them again as result of removing them the way I did above :rolleyes: 

Thanks

---

### Post by nix4me on 2006-02-08
I thought by un-clicking the checkbox next to the entry in the list would comment it out and not delete it?

I have not tried this so I am asking.

I use the command line to edit sources.

nix4me

---

### Post by Ramses de Norre on 2006-02-09
```
sudo gedit /etc/apt/sources.list
``` and comment them out manually.
Think that's the easiest way;)

---

### Post by Seinfeld on 2006-02-09
nix4me

Thanks for the email

The checkbox just gives you the option of ONLY adding repos from multiverse, universe, etc... (if this is the checkbox that u mean, I do not fiind any other one). Somtimes, not necessarily we are adding Ubuntu reops. You may add some other custom ones like Skype for example as I mentioned. In this case, you will not have the choice if you want to remove it or any other one temporarily in case of any dependency or broken packages problem. 
We have to back up a snapshot of the WHOLE file, otherwise we won't be able to retrieve it. :cry:

Yes Ramses de Norre, The only way, is to # it manually, always backup and do not use the Synaptic->Settings-> Repository option when removing any.  :cry:  

 I think we should report that Don't we ??

---

### Post by Seinfeld on 2006-02-09
nix4me

Thanks for the email

The checkbox just gives you the option of ONLY adding repos from multiverse, universe, etc... (if this is the checkbox that u mean, I do not fiind any other one). Somtimes, not necessarily we are adding Ubuntu reops. You may add some other custom ones like Skype for example as I mentioned. In this case, you will not have the choice if you want to remove it or any other one temporarily in case of any dependency or broken packages problem. 
We have to back up a snapshot of the WHOLE file, otherwise we won't be able to retrieve it. :cry:

Yes Ramses de Norre, The only way, is to # it manually, always backup and do not use the Synaptic->Settings-> Repository option when removing any.  :cry:  

Thanks

---

