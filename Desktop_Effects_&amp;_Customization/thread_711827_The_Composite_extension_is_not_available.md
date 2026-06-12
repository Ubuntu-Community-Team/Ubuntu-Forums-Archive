---
title: "The Composite extension is not available"
date: 2008-03-01
forum: Desktop Effects &amp; Customization
---

### Post by rahmanhm on 2008-03-01
Dear Folks,
I am a total beginner and I have just installed Ubuntu 7.10! I updated the respository lists After the instalation I got the restricted driver message!
-  I searched trough the forum and could enable that I am using a Radeon X4100 ATI graphic card with a T60 IBM ThinkPad. 
- going to terminal and typing fglrxinfo i get the following message that shows no problems with the graphic card installtion

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

- Then i tried to enable the compiz. I went to the Appearence and clicking the Extra radio button I got the following message. 
              The Composite extension is not available. 

I tried installing some of the missing packages like the compiz-setting-manager but nothing changed and I still have the same message and can't have the desktop effects activated. 
Can some one tell me how to over come this problem.
Regards
Hamid

---

### Post by _Phineas_ on 2008-03-01
The same deal with my card but I received no help or replys for it.

---

### Post by rahmanhm on 2008-03-01
Phenees, 
Lets bee hopeful, we will get the reply soon. Don't worry! Some is there who would help us for sure.

---

### Post by JBAlaska on 2008-03-01
Your driver looks correct, Just install the xgl server;

```
sudo apt-get install xserver-xgl
```

Then the compiz settings  manager;
```
sudo apt-get install compizconfig-settings-manager
```

Now restart x and you should have your effects.

(It's been awhile since I had a ati card, so I'm kinda going from foggy memory but this should work for you).

---

### Post by rahmanhm on 2008-03-02
Thanks alot for the hint. Actually it worked well The Message is not displayed anymore. But I still can't have everything working. 

In the Visual Effects now I have an extra option called "Custom" and next to it is a "Preferences" butthon, but It doesn't work if I click it. 

I ca'nt have more than two desktops and eventhough I can't go to the second desktop, notthing happens, the shortcut keys are disabled, the moust scroll which ususally shoudl swtich between the two desktops, doesn't do anythign, what is wrong? I can't figure it out.

---

### Post by rahmanhm on 2008-03-07
Dear Folks, 
Finally I could solve my problem taking the following steps, I don't know if they make sense or not but now my Compiz is working and I have all those dashing animations active.

- I totally deleted all partitions on my hard disk,
- Installed Ubuntu 7.10 once again. 
- I clicked System>>Administration>>Software Sources and then ticked all the check boxes in Ubuntu Softwares, Third-Party Software, Updates and Statistics Tabs. 
- Then upon closing the tabs, I clicked the reload button and I had my Respository List updated.

-Next step I went to System>>Administration>>Update Manager and Installed all the available updates except for the four updates that belonged to Compiz. I unchecked them before. 

- Then I installed my xgl driver the xserverXgl package and its related dependencies using the System>>Administration>>Synapticmanager ofcourse. 

- Next step I went to System>>Administration>>Restricted Drivers Manager and clicked my AtI Driver check box and then clicked the enable button on the appreaing dialouge box. It was enabled and I had to restart my PC. 

- The last step I opened a Terminal and typed the following as was advised to me an in earlier post
>  ```
sudo apt-get install compizconfig-settings-manager
```

My compiz works perfectly now and I have everything working quite well. and the last but not the least step that I took is to post this to the forum now. 
cheers!!

---

