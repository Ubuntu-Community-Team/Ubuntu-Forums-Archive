---
title: "Easy graphics install"
date: 2009-05-31
forum: General Help
---

### Post by dougalkerr on 2009-05-31
I had this posted elsewhere but, thought I should share it generally as there are probably and hopefully a lot of newbees out there that, like me, need all the help they can get. So here is my last post which covers an easy way to install drivers for ATI cards (and NVidia) and the other topic is a short discussion about my efforts to get over the delay problem apparent in Jaunty and Compiz window resizing.

Window resize from minimize delay: I have set my Visual Effects to 'None' so that I do not have the resize delay. It was getting too annoying.
I also reinstalled Ubuntu and played around with installing/reinstalling the graphics card driver - didn't make the slightest bit of difference to the resize effect delay. I tried to follow all suggestions that I could find but, they were either too complex to follow for a mere mortal like me that is used to installing operating systems and fault finding applications (mostly in Windows, unfortunately) or the suggestions did not work...

On the plus side - I used to use Envyng to install the ATI driver for my machine but, when Jaunty came out there was not an install available from the Envy website - now there is.
Alberto Milone has made Envyng available for Ubuntu 8.04 onward and it works just fine. No more faffing about trying to follow install instructions from ATI or the Ubuntu help page (sorry guys, you do an excellent job otherwise). It was actually available in Synaptic - wow!!
Once Envy is installed you have to click on the application in the newly created 'System Tools' sub-menu to the 'Applications' menu to activate the driver then reboot. All is well.
I usually check the graphics using the Sky Rocket screensaver. I test the Appearances 'Visual Effects' setting of 'None', 'Normal' and 'Extra' and then open the screensaver settings applet to select Sky Rocket and right-away I found that I only had two choices, None or Extra. Normal would upset the Window Manager controls and even disable or freeze things forcing a reboot. On extra I had the resize delay from minimized windows but, on None I have no problems. My screensaver runs well and no other visual problems at all. In fact the system runs fast with None selected. I do not need the Extra effects even if they do look pretty. I would keep them if the delay bug was not present as I like being able to swap desktops using the cube but, the delay is just too damn annoying as I said.
Phew!! well hope someone enjoys reading this. If anyone knows of an alternative to Compiz it might prove interesting...
Cheers for now.

---

### Post by Arup on 2009-05-31
Envy was very good and it still remains an easy way for novices to install drivers, however Jockey which is default in Ubuntu since Hardy makes it easier as well, all you do is click on hardware drviers applet in system>admin, select the driver, let it install and reboot. The advantage of envy previously was that it would download latest driver from nvidia or ati, also download build essential and other requirements and compile and install the drivers. Now it just pulls the drivers from the Ubuntu repo.

The alternate to compiz is gnome's own metacity manager but then its basic stuff and you dont get the whiz bang of compiz. If you install latest driver from manufacturer, the performance is usually better than the one included in the repos due to it being the latest.

---

### Post by dougalkerr on 2009-06-06
Thanks for the info Arup. This is the first time I have seen graphics card install explained so easily.
I will be doing some further investigating this weekend as I have installed Ubuntu 9.04 on my Dell at work but, there seems to be a problem getting the Envyng to work properly. I have followed Alberto's guide to the letter and in Terminal everything is installing but, when I look for Envyng in the System Tools sub-menu, Envyng nor the sub-menu exist. It did the very first time. Now whenever I install Envyng and test the graphics the PC is either blank when running 'Sky Rocket' screensaver on Visual Effects set to 'None' or if set to 'Extra' then I get a few seconds of good rendering then the PC screen goes blank and I can't input anything by keyboard nor mouse and have to reboot to Recovery Mode to fix the graphics which looses the driver again.
When I check in Hardware Drivers there is not one there. I am using a Radeon X600 with 128Mb memory. Any ideas...
Cheers and thanks for your input.

---

