---
title: "minecraft causes logout - intel hd graphics"
date: 2012-07-02
forum: Gaming &amp; Leisure
---

### Post by z3nhakr on 2012-07-02
ubuntu logs out right after the mojang splash is displayed. it was working fine on my radeon card so it's definitely cause by the card. any ideas?

---

### Post by anewguy on 2012-07-02
You may want to click on the big ubuntu forums on the upper left of the page, then select the gaming and leisure forum and search there.  If nothing is found, you may want to ask a moderator to move your post there.

---

### Post by z3nhakr on 2012-07-02
> **anewguy said:**
> You may want to click on the big ubuntu forums on the upper left of the page, then select the gaming and leisure forum and search there.  If nothing is found, you may want to ask a moderator to move your post there.

the problem does not concern the game, it concerns java 3d and the intel hd graphics.

---

### Post by anewguy on 2012-07-04
Do you get this anywhere else, or just in Minecraft???

If you get it other places, state what they are. 

If not, Minecraft is a game, check the gaming forum.  It can't hurt, can it?  Someone else may have had the same problem and already has a solution.

And people wonder why I quit.

---

### Post by z3nhakr on 2012-07-09
haha ok thx. i'll try that ;)

---

### Post by anewguy on 2012-07-10
Here's an example of what happens when a question about minecraft and java gets moved to leisure and gaming, and the thread is solved:

[http://ubuntuforums.org/showthread.php?t=2017716]("http://ubuntuforums.org/showthread.php?t=2017716")

---

### Post by Elfy on 2012-07-10
*Thread moved to **Gaming & Leisure**.*

---

### Post by z3nhakr on 2012-07-15
this has NOTHING to do with GAMING...how would a game cause a logout????? it's blatantly obvious that it IS a problem with the compatibility between my graphics card and the java openGL libraries....

---

### Post by Elfy on 2012-07-15
If that's the case then you need to think about thread titles and the information you put in them.

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by rizal23 on 2012-07-16
> **anewguy said:**
> You may want to click on the big ubuntu forums on the upper left of the page, then select the gaming and leisure forum and search there.  If nothing is found, you may want to ask a moderator to move your post there.

the  problem is not related to or concerning java 3d games and hd intel  graphics if you want to play the game it also depends on its vga ram  used on computer systems.

---

### Post by regor210 on 2012-07-17
It sounds like you had an ATI card in your Desktop PC and had to pull it. And now your falling back on the Intel integrated graphics adapter on your mother board? 

1st. Check your BIOS and make sure you have as much shared ram as you can allocated to your Intel graphics adapter, 16 meg's at least, more is better.

2nd. If Minecraft still will not work lets look at your 3D drivers. 

Open a terminal, press ctrl+alt+t all at the same time.  Then cut and paste the following commands into the terminal window one line at a time minus the $.

$ sudo apt-get update 
$ sudo apt-get upgrade 
$ sudo apt-get install mesa-utils

#video card and driver information 
$ lspci -vmk | grep -A 8 -B 2 VGA && lspci | grep VGA

# OpenGL rendering test. This may cause a log out. 
$ glxinfo | grep -w 'direct\|OpenGL'

Post what you if there is anything to post.

---

### Post by z3nhakr on 2012-07-18
> **Elfy said:**
> If that's the case then you need to think about thread titles and the information you put in them.

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

minecraft was an example. what other 3D standalone java games do you know of that use opengl? i could try them and see if i get the same problem.

---

### Post by z3nhakr on 2012-07-18
> **regor210 said:**
> It sounds like you had an ATI card in your Desktop PC and had to pull it. And now your falling back on the Intel integrated graphics adapter on your mother board? 

1st. Check your BIOS and make sure you have as much shared ram as you can allocated to your Intel graphics adapter, 16 meg's at least, more is better.

2nd. If Minecraft still will not work lets look at your 3D drivers. 

Open a terminal, press ctrl+alt+t all at the same time.  Then cut and paste the following commands into the terminal window one line at a time minus the $.

$ sudo apt-get update 
$ sudo apt-get upgrade 
$ sudo apt-get install mesa-utils

#video card and driver information 
$ lspci -vmk | grep -A 8 -B 2 VGA && lspci | grep VGA

# OpenGL rendering test. This may cause a log out. 
$ glxinfo | grep -w 'direct\|OpenGL'

Post what you if there is anything to post.

it's a laptop with switchable cards. but basically thats right. my ati card gets an extreeeeeemly low fps so i switched it.
i also made a thread for the ati card [here]("http://ubuntuforums.org/showthread.php?t=2014715")

because it's a laptop i cant modify the shared ram :(
but ive got 8gb and it shows as 7.7 so i assume .3 is allocated to the intel card?

---

### Post by regor210 on 2012-07-18
It looks like you have an ATI dual-GPU ati/intel hybrid video adapter.

I'm guessing you switched your ATI side of your GPU off using your BIOS?

And now your trying to use your Intel graphics adapter hoping that Ubuntu would reconfigure it's self to the now new  Intel graphics adapter. If you used the ATI property drivers Ubuntu may not be able to fully reconfigure it's self to Intel graphics adapter with out  purging the ATI property drivers or fglrx. This has been a problem lately as I've been told the Official Documentation  Community Help Wiki is out of date and not working with Ubuntu 12.04. But its worth a try, that is if you installed the ATI property drivers in the first place.

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx)

If this is no help you could try reinstalling Ubuntu with the ATI side of your GPU off.

The other side of the coin would be to get your much better for gaming ATI drivers working.

This has been a big problem for some of are Ubuntu brethren. The picture for me is a bit unclear. It seems ATI stopped supporting some of its older hardware in its GNU\Linux drivers. So the ATI driver installs but has no 3d rendering.   
 
As you have  &#8220;Intel® GMA HD 3000 graphics or AMD RadeonTM HD6470M 1GB
graphics&#8221; If it were me I would be inclined to try this
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
but again you would still have to reinstall Ubuntu.

Also, I was told the  ATI Radeon open-source driver works but again you would still have to  purge the ATI property drivers or reinstall Ubuntu.

[https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver](https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver)



Other places to look at
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx)

---

### Post by anewguy on 2012-07-18
Again - the OP put minecraft in the title and said what was happening in the initial post.  But it doesn't matter to me - they can find help from someone else.

---

### Post by anewguy on 2012-07-19
> **rizal23 said:**
> the  problem is not related to or concerning java 3d games and hd intel  graphics if you want to play the game it also depends on its vga ram  used on computer systems.

Please - we were basing our replies off the title of the thread and the 1st post.  You can leave out the attacks and just help.  Attacks will just get you banned.

Attitude is THE most important thing in these forums.  Yours and the OPs.  And z3nhakr, it's an EXTREMELY good idea not to contradict or reply like a child to someone who is on the forum staff.

---

### Post by z3nhakr on 2012-07-19
> **regor210 said:**
> It looks like you have an ATI dual-GPU ati/intel hybrid video adapter.

I'm guessing you switched your ATI side of your GPU off using your BIOS?

And now your trying to use your Intel graphics adapter hoping that Ubuntu would reconfigure it's self to the now new  Intel graphics adapter. If you used the ATI property drivers Ubuntu may not be able to fully reconfigure it's self to Intel graphics adapter with out  purging the ATI property drivers or fglrx. This has been a problem lately as I've been told the Official Documentation  Community Help Wiki is out of date and not working with Ubuntu 12.04. But its worth a try, that is if you installed the ATI property drivers in the first place.

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx)

If this is no help you could try reinstalling Ubuntu with the ATI side of your GPU off.

The other side of the coin would be to get your much better for gaming ATI drivers working.

This has been a big problem for some of are Ubuntu brethren. The picture for me is a bit unclear. It seems ATI stopped supporting some of its older hardware in its GNU\Linux drivers. So the ATI driver installs but has no 3d rendering.   
 
As you have  “Intel® GMA HD 3000 graphics or AMD RadeonTM HD6470M 1GB
graphics” If it were me I would be inclined to try this
[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
but again you would still have to reinstall Ubuntu.

Also, I was told the  ATI Radeon open-source driver works but again you would still have to  purge the ATI property drivers or reinstall Ubuntu.

[https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver](https://help.ubuntu.com/community/RadeonDriver#Removing_the_proprietary_fglrx_driver)



Other places to look at
[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)

[https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx)


i switched using amd catalyst control center. i think the drivers are bundled together because the intel card showed up as unknown in system_setting>details until i install the fglrx driver. it probably doesnt matter but they seem to be bundled together in windows too.

---

### Post by z3nhakr on 2012-07-19
> **anewguy said:**
> Attitude is THE most important thing in these forums.  Yours and the OPs.  And z3nhakr, it's an EXTREMELY good idea not to contradict or reply like a child to someone who is on the forum staff.

hey bro, chill. the vga ram, although it's not the problem, was an extremely valid possibility and im glad it was suggested. there's a difference between debating and attacks and debating is how you solve the tricky stuff like this. ;)

> **anewguy said:**
> Please - we were basing our replies off the  title of the thread and the 1st post.  You can leave out the attacks and  just help.  Attacks will just get you banned.
it's a good idea to read the rest of the thread and see what changes and progress have been made. ;)

---

### Post by ELD on 2012-07-20
> **z3nhakr said:**
> i switched using amd catalyst control center. i think the drivers are bundled together because the intel card showed up as unknown in system_setting>details until i install the fglrx driver. it probably doesnt matter but they seem to be bundled together in windows too.

Just FYI on my laptop my Intel HD4000 shows up as unknown anyway think they usually do? But it works fine as Ubuntu comes with graphics for intel chips as standard.

---

### Post by z3nhakr on 2012-07-20
mine showed up as unknown after i installed and all the desktop graphics worked fine but when i opened a game it would say it requires accelerated drivers. apparently the default ones aren't although they sure better

---

