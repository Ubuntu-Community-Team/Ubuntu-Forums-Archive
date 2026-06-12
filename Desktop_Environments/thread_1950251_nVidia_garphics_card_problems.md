---
title: "nVidia garphics card problems"
date: 2012-03-31
forum: Desktop Environments
---

### Post by rpaster1 on 2012-03-31
A little background first. I have been using Ubuntu for several years, as a dual boot with Windows XP. Windows is my primary OS, with Ubuntu for fun. I am currently on Ubuntu 11.10. I am not an expert in Ubuntu, but am somewhat experienced, mostly using the GUI. In previous upgrades from 10.10 to 11.04, and from 11.04 to 11.10 I have experienced problems with the nVidia graphics card usually being the culprit, but was always able to find someone in this forum to help me get the GUI to run, with the extra nVidia drivers. I could never get 3D Unity to run, but 2D worked fine, as well as classic Gnome.

I just replaced my old nVidia graphics card (Geforce FX5300) with a new nVidia graphics card(Geforce GX8400GS), when the old card died. Now I can't get Ubuntu to run in graphics mode. If I select Ubuntu on the grub menu, the Ubuntu splash screen comes up, with the little dots below Ubuntu, then it shows various start up information followed by "[OK]" until it gets to "checking battery"  then stops. If I reboot and select "recovery mode" I can get to Ubuntu in text mode fine, but I can't start the GUI.

In looking earlier at this forum I followed several suggestions doing the following:

sudo apt-get install nvidia-current
sudo nvidia-xconfig 

tried to reboot, no luck still the same message

anyway so i reinstalled it

sudo apt-get install --reinstall nvidia-173

Still no luck. How can I check to see which nvidia driver I need for my new card?

How do I get the correct nVidia driver activated to allow the GUI to run at start up?

Any help would be greatly appreciated!!!

Bob

---

### Post by 23dornot23d on 2012-03-31
Have a look in  

**cd /etc/X11/**

See if there is a xorg.conf file there .....

if so 

**mv xorg.conf xorg1.conf**

and reboot ..... it should go into a 2d gui mode ...... then from there - we can try to
purge all the old Nvidia Drivers and load up a new one .....
from what you have already said there may be more than one driver in there now.

Best I can think of at the moment ..... once you have a gui its is easier to copy and 
paste things to here so that we can see what is happening ......

---

### Post by Bobhuber on 2012-03-31
> **rpaster1 said:**
> A little background first. I have been using Ubuntu for several years, as a dual boot with Windows XP. Windows is my primary OS, with Ubuntu for fun. I am currently on Ubuntu 11.10. I am not an expert in Ubuntu, but am somewhat experienced, mostly using the GUI. In previous upgrades from 10.10 to 11.04, and from 11.04 to 11.10 I have experienced problems with the nVidia graphics card usually being the culprit, but was always able to find someone in this forum to help me get the GUI to run, with the extra nVidia drivers. I could never get 3D Unity to run, but 2D worked fine, as well as classic Gnome.

I just replaced my old nVidia graphics card (Geforce FX5300) with a new nVidia graphics card(Geforce GX8400GS), when the old card died. Now I can't get Ubuntu to run in graphics mode. If I select Ubuntu on the grub menu, the Ubuntu splash screen comes up, with the little dots below Ubuntu, then it shows various start up information followed by "[OK]" until it gets to "checking battery"  then stops. If I reboot and select "recovery mode" I can get to Ubuntu in text mode fine, but I can't start the GUI.

In looking earlier at this forum I followed several suggestions doing the following:

sudo apt-get install nvidia-current
sudo nvidia-xconfig 

tried to reboot, no luck still the same message

anyway so i reinstalled it

sudo apt-get install --reinstall nvidia-173

Still no luck. How can I check to see which nvidia driver I need for my new card?

How do I get the correct nVidia driver activated to allow the GUI to run at start up?

Any help would be greatly appreciated!!!

Bob
295.33 is the most recent driver for your card. This can be found at Nvidia's site but you will have to manually install it should you decide to use there drivers. Many posts on how to do this and actually very easy once you get the hang of it. Assuming you have a 64/bit system the following link will help.
[http://www.nvidia.com/object/linux-display-amd64-295.33-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.33-driver.html)

---

### Post by rpaster1 on 2012-04-01
> **23dornot23d said:**
> Have a look in  

**cd /etc/X11/**

See if there is a xorg.conf file there .....

if so 

**mv xorg.conf xorg1.conf**

and reboot ..... it should go into a 2d gui mode ...... then from there - we can try to
purge all the old Nvidia Drivers and load up a new one .....
from what you have already said there may be more than one driver in there now.

Best I can think of at the moment ..... once you have a gui its is easier to copy and 
paste things to here so that we can see what is happening ......


Followed your directions and still no gui at start up. There are several other files (like xorg.conf.upgrade-201110xxxxxx< with the xxxxxx being a month, date and some other numbers) in that directory. Do I need to mv them also???

Thanks,

Bob

---

### Post by gordintoronto on 2012-04-01
You went from an eight-year-old card to a five-year-old card?

Can you run from a LiveCD?

---

### Post by rpaster1 on 2012-04-02
> **gordintoronto said:**
> You went from an eight-year-old card to a five-year-old card?

Can you run from a LiveCD?

Yes. If I boot into the live CD I get Unity Gui. I'm actually using it right now!!!. Seems to work fine.

Thanks, but now what?

Bob

---

### Post by gordintoronto on 2012-04-02
Sorry, my only suggestion is to try what Bobhuber suggested.

I have an Nvidia 9400GT, and it "just works," using the Nvidia-current driver.

---

### Post by wildmanne39 on 2012-04-02
Hi, I suspect you still have the old driver from the old card installed if you remove it and make sure your new driver is installed it should work.

Have you installed the new driver yet?
Thanks

---

### Post by 23dornot23d on 2012-04-03
> 
Followed your directions and still no gui at start up. There are several  other files (like xorg.conf.upgrade-201110xxxxxx< with the xxxxxx  being a month, date and some other numbers) in that directory. Do I need  to mv them also???

Thanks,

Bob
The others do not matter they are all backups ...... all I did was to move the xorg.conf out of the way ..... to see if the Nouveau driver was running ....

I think you need to remove all your Nvidia drivers and then re install nvidia-current

do 

**[COLOR=Blue]uname -a[/COLOR]**

( this will show which kernel you are running -  you could check to make sure that the headers are installed for it by searching for the returned kernel from the command above - look in synaptic package manager and using the numbers given in the kernel
make sure that the headers exist with the same numbers in the title ...... )

Then do the following ...... if you are unsure of anything post back the information
you get and someone will help you get through all of this .....

____________________ Just removing drivers to get to a clean start
[COLOR=Blue][B]
sudo apt-get remove nvidia-settings

 sudo apt-get remove nvidia-current[/B]  [/COLOR]

( if you loaded a lot of other Nvidia things in - then remove them too - often
its as easy to run synaptic package manager - search on nvidia - remove all
the nvidia things you see ...... then continue as below as the following commands
will put everything in that you need )
 
________________ Just updating the repository lists for apt-get and aptitude

[COLOR=Blue]**sudo apt-get update**[/COLOR]

[COLOR=Blue]**sudo apt-get install aptitude**   [B]
    
 sudo aptitude update

[/B][COLOR=Black]________________ Now installing the latest nvidia settings and drivers[/COLOR][/COLOR]

[COLOR=Blue][B]sudo aptitude install nvidia-settings

sudo aptitude install nvidia-current[/B] [/COLOR]
( or at this point you could install the Nvidia Site ..... Driver .....  the instructions are on their site I believe
if not post back and someone will help you install it this way - but first try the current one as above in blue 
[http://www.nvidia.com/Download/indexsg.aspx?lang=en-us](http://www.nvidia.com/Download/indexsg.aspx?lang=en-us) )

Also as it installs watch and make sure it installs correctly with no [COLOR=Red]**FAIL **[/COLOR]markers anywhere ....

you can then re-create a new xorg.conf after doing this by doing ..... 

________________ Now creating a new xorg,conf 

[sudo **nvidia-xconfig**]("http://linux.die.net/man/1/nvidia-xconfig")

reboot ....

Hope this sorts it out for you ....

---

### Post by rpaster1 on 2012-04-03
> **23dornot23d said:**
> The others do not matter they are all backups ...... all I did was to move the xorg.conf out of the way ..... to see if the Nouveau driver was running ....

I think you need to remove all your Nvidia drivers and then re install nvidia-current

do 

**[COLOR=Blue]uname -a[/COLOR]**

( this will show which kernel you are running -  you could check to make sure that the headers are installed for it by searching for the returned kernel from the command above - look in synaptic package manager and using the numbers given in the kernel
make sure that the headers exist with the same numbers in the title ...... )

Then do the following ...... if you are unsure of anything post back the information
you get and someone will help you get through all of this .....

____________________ Just removing drivers to get to a clean start
[COLOR=Blue][B]
sudo apt-get remove nvidia-settings

 sudo apt-get remove nvidia-current[/B]  [/COLOR]

( if you loaded a lot of other Nvidia things in - then remove them too - often
its as easy to run synaptic package manager - search on nvidia - remove all
the nvidia things you see ...... then continue as below as the following commands
will put everything in that you need )
 
________________ Just updating the repository lists for apt-get and aptitude

[COLOR=Blue]**sudo apt-get update**[/COLOR]

[COLOR=Blue]**sudo apt-get install aptitude**   [B]
    
 sudo aptitude update

[/B][COLOR=Black]________________ Now installing the latest nvidia settings and drivers[/COLOR][/COLOR]

[COLOR=Blue][B]sudo aptitude install nvidia-settings

sudo aptitude install nvidia-current[/B] [/COLOR]
( or at this point you could install the Nvidia Site ..... Driver .....  the instructions are on their site I believe
if not post back and someone will help you install it this way - but first try the current one as above in blue 
[http://www.nvidia.com/Download/indexsg.aspx?lang=en-us](http://www.nvidia.com/Download/indexsg.aspx?lang=en-us) )

Also as it installs watch and make sure it installs correctly with no [COLOR=Red]**FAIL **[/COLOR]markers anywhere ....

you can then re-create a new xorg.conf after doing this by doing ..... 

________________ Now creating a new xorg,conf 

[sudo **nvidia-xconfig**]("http://linux.die.net/man/1/nvidia-xconfig")

reboot ....

Hope this sorts it out for you ....


Thanks for the specific instructions.  I ran uname -a and I'm running 3.0.0-16-generic. I couldn't run synaptic package manager  to check headers, because I have no graphics capability, but ubuntu was running fine before installing the new graphics card. So I think that the headers are okay???

I then did each of the steps you suggested, but still could not boot into ubuntu in the gui. I didn't see any "failed" steps in any of the commands you suggested. I can still go into "recovery mode", then exit and log in as myself, but still no GUI.

Do I need to re-install ubuntu from the live-cd to get the GUI to work (maybe wait until new version (12.04 comes out)???

Again, thanks for the help!!!

Bob

---

### Post by rpaster1 on 2012-04-03
> **Bobhuber said:**
> 295.33 is the most recent driver for your card. This can be found at Nvidia's site but you will have to manually install it should you decide to use there drivers. Many posts on how to do this and actually very easy once you get the hang of it. Assuming you have a 64/bit system the following link will help.
[http://www.nvidia.com/object/linux-display-amd64-295.33-driver.html](http://www.nvidia.com/object/linux-display-amd64-295.33-driver.html)

I'm using a 32 bit system (Windows XP dual boot), but since I can't boot in ubuntu gui, I can't run Firefox to get the download from nvidia's web site. Is there a way from the ubuntu command line to get the latest driver? I have used the apt-get command as 23dornot23d suggested, but still not working.

Thanks for you help, hopefully someone can help me figure this out.

---

### Post by wildmanne39 on 2012-04-03
Hi, boot into recovery mode with networking and run:
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
make sure have have an internet connection.
Thanks

---

### Post by rpaster1 on 2012-04-04
I tried the steps that 23dornot23d suggested and it didn't work. Then I tried what wildmanne39 suggested and I still can't boot into "normal" ubuntu gui. I then did one (23dornot23d) after the other (wildmanne39) and it still didn't work.

Not sure what else I can try, so at this point I'm thinking that I should wait until the new version of ubuntu (12.04) becomes available and delete the 11.10 version and then install 12.04.

Any other ideas could be tried out, but I seem to have graphics card driver problems every time I upgrade ubuntu. Should I sow this thread as "solved" or leave it open?

Thanks for all the help!!!

Bob

---

### Post by 23dornot23d on 2012-04-04
Leave the thread open ..... as when users search for solved - they need a answer that
works ..... and upto now we have not got one ,,,,

Not sure why ..... and you did try the one from the Nvidia website ......

I did notice when I searched though that your model of graphics card was not listed
on the driver ...... it just used the lates driver ....

may be best searching on your card[[COLOR=Blue]_** 8400GS and solved**_[/COLOR]]("http://www.google.fr/search?q=linux+Geforce+8400GS+solved&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

_____________________________________________

This one is for mint but advice is given to use [[COLOR=Blue]**Xswat PPa**[/COLOR]]("http://www.google.fr/search?q=Xswat+PPa&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")
[http://forums.linuxmint.com/viewtopic.php?f=109&t=70052](http://forums.linuxmint.com/viewtopic.php?f=109&t=70052)

[https://www.google.fr/search?q=Xswat+PPa&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=fr&client=firefox-a&rls=org.mozilla:en-US%3Aofficial&biw=1016&bih=499&sclient=psy-ab&q=Xswat+PPa+8400&oq=Xswat+PPa+8400&aq=f&aqi=&aql=&gs_l=serp.3...9936l19486l0l19768l23l12l11l0l0l0l187l1562l0j12l34l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=d9ffb195ccc1a251](https://www.google.fr/search?q=Xswat+PPa&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=fr&client=firefox-a&rls=org.mozilla:en-US%3Aofficial&biw=1016&bih=499&sclient=psy-ab&q=Xswat+PPa+8400&oq=Xswat+PPa+8400&aq=f&aqi=&aql=&gs_l=serp.3...9936l19486l0l19768l23l12l11l0l0l0l187l1562l0j12l34l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=d9ffb195ccc1a251)
______________________________________________

Another option is here ...... was searching for this before .... purging all the Nvidia 

[http://ubuntuforums.org/showpost.php?p=11320706&postcount=10](http://ubuntuforums.org/showpost.php?p=11320706&postcount=10)

Best I can do for now ....

---

### Post by rpaster1 on 2012-04-05
> **23dornot23d said:**
> Leave the thread open ..... as when users search for solved - they need a answer that
works ..... and upto now we have not got one ,,,,

Not sure why ..... and you did try the one from the Nvidia website ......

I did notice when I searched though that your model of graphics card was not listed
on the driver ...... it just used the lates driver ....

may be best searching on your card[[COLOR=Blue]_** 8400GS and solved**_[/COLOR]]("http://www.google.fr/search?q=linux+Geforce+8400GS+solved&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")

_____________________________________________

This one is for mint but advice is given to use [[COLOR=Blue]**Xswat PPa**[/COLOR]]("http://www.google.fr/search?q=Xswat+PPa&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a")
[http://forums.linuxmint.com/viewtopic.php?f=109&t=70052](http://forums.linuxmint.com/viewtopic.php?f=109&t=70052)

[https://www.google.fr/search?q=Xswat+PPa&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=fr&client=firefox-a&rls=org.mozilla:en-US%3Aofficial&biw=1016&bih=499&sclient=psy-ab&q=Xswat+PPa+8400&oq=Xswat+PPa+8400&aq=f&aqi=&aql=&gs_l=serp.3...9936l19486l0l19768l23l12l11l0l0l0l187l1562l0j12l34l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=d9ffb195ccc1a251](https://www.google.fr/search?q=Xswat+PPa&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a#hl=fr&client=firefox-a&rls=org.mozilla:en-US%3Aofficial&biw=1016&bih=499&sclient=psy-ab&q=Xswat+PPa+8400&oq=Xswat+PPa+8400&aq=f&aqi=&aql=&gs_l=serp.3...9936l19486l0l19768l23l12l11l0l0l0l187l1562l0j12l34l0.frgbld.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=d9ffb195ccc1a251)
______________________________________________

Another option is here ...... was searching for this before .... purging all the Nvidia 

[http://ubuntuforums.org/showpost.php?p=11320706&postcount=10](http://ubuntuforums.org/showpost.php?p=11320706&postcount=10)

Best I can do for now ....

Well, 23dornot23d, you saved the best for last. I used the last option [(http://ubuntuforums.org/showpost.php?p=11320706&postcount=10]("http://ubuntuforums.org/showpost.php?p=11320706&postcount=10")) and I now can get to ubuntu  in graphics mode, both classic Gnome & Unity 2d. Not sure about Unity option, but not really too concerned about that.

Thank you so much!!!. I am showing this thread "solved"!!!

Bob

---

