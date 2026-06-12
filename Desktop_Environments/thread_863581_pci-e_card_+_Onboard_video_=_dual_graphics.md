---
title: "pci-e card + Onboard video = dual graphics?"
date: 2008-07-18
forum: Desktop Environments
---

### Post by jeremygjohn on 2008-07-18
Is it possible to run Ubuntu 8.04 on a second monitor when it is in Virtualbox. I know virtual machines can be on a second monitor but can my host Windows Vista Ultimate run off my 8600GT and my virtual guest run on the second monitor from onboard graphics?

---

### Post by jeremygjohn on 2008-07-18
bump

---

### Post by overdrank on 2008-07-18
Hi and you may wait a little longer before bumping. I am sure it can be done but configuring your xorg will take some time. I had tried it once but gave up as I did not have the patient. You may search the forums and find some old threads and this one may help
[http://ubuntuforums.org/showthread.php?t=854719&highlight=multiple+graphics+cards](http://ubuntuforums.org/showthread.php?t=854719&highlight=multiple+graphics+cards)

---

### Post by jeremygjohn on 2008-07-18
ok nvm i edited this post did not see you reply

---

### Post by overdrank on 2008-07-18
> **jeremygjohn said:**
> *sigh* does no body know?? seems like i have to triple post EVERYTIME I WANT HELP BEFORE SOMEONE DOES... I guess my questions are too complicated..:(:lolflag:

Well that is to close to bump as you can see I did reply. :)
Why do you say that that you have to triple post? You are a new member and you have only three post?:confused:

---

### Post by jeremygjohn on 2008-07-18
sorry i saw your post late i changed my post. And i have had earlier accounts here thats why. But i think that link to the thread you gave me doesnt really help much. I know it is impossible to run onboard and video card at same time but could it be tricked if i ran host on video card and guest virtual machine on onboard graphics? i think it wont work most likely but i hope it will.

---

### Post by overdrank on 2008-07-18
> **jeremygjohn said:**
> sorry i saw your post late i changed my post. And i have had earlier accounts here thats why. But i think that link to the thread you gave me doesnt really help much. I know it is impossible to run onboard and video card at same time but could it be tricked if i ran host on video card and guest virtual machine on onboard graphics? i think it wont work most likely but i hope it will.

Hi and it can work with the onboard graphics and another graphics card as I have seen threads in the past. As I stated earlier I have tried with nvidia and intel onboard but did not have the patients on Hardy 8.04. 
I do hope you know it is against forum rules to have multiple accounts :(

---

### Post by jeremygjohn on 2008-07-18
ok im glad to hear it is possible lol. But i keep trying to install ubuntu in virtual box but i always get host low memory error and i am not running anything else..
if i cant get it to work in a week or so it wont matter because i have a VGA to DVI-I converter being shipped so they would both go into the card then which would be much easier but i still want to try to get this too work because im bored.

---

### Post by bapoumba on 2008-07-18
> **jeremygjohn said:**
> sorry i saw your post late i changed my post. And i have had earlier accounts here thats why.
I could find 3, would you like to have them merged into this one ? Please send me a list by PM, and we can have it taken care of.

---

### Post by jeremygjohn on 2008-07-18
i dont remember the user names.

---

### Post by bapoumba on 2008-07-18
> **jeremygjohn said:**
> i dont remember the user names.

Please check your PM box, thanks :)

---

### Post by jeremygjohn on 2008-07-18
Does any body know how to run onboard graphics with my NVIDIA 8600GT video card and would i have to use virtual box to use the secound one?

---

### Post by jeremygjohn on 2008-07-18
guess ill give up since seems like im not only one with no idea on how to do this...

---

### Post by jeremygjohn on 2008-07-18
Is there anyway to use both of these at same time to use 2 monitors i cannot find a way but people say it is possible on some sites..

---

### Post by jeremygjohn on 2008-07-18
should i ask this somewhere else lol?

---

### Post by jeremygjohn on 2008-07-18
Help

---

### Post by Shazaam on 2008-07-18
Unless you can finagle your pc's bios to run both at the same time I think you will be out of luck.

---

### Post by jeremygjohn on 2008-07-19
..ok people say to look at those dual head guides but i dont think those will help me with my problem i want to use oboard graphics and my 8600GT at same time some people said it was possible to dual screen this way but i cant find out how.

---

### Post by jeremygjohn on 2008-07-19
bump

---

### Post by overdrank on 2008-07-19
> **jeremygjohn said:**
> ..ok people say to look at those dual head guides but i dont think those will help me with my problem i want to use oboard graphics and my 8600GT at same time some people said it was possible to dual screen this way but i cant find out how.

Hi and this is the third thread you have started on the same issue. Not to mention the annoying bumping of the thread sometimes on the hour.
[http://ubuntuforums.org/showthread.php?t=863581](http://ubuntuforums.org/showthread.php?t=863581)
[http://ubuntuforums.org/showthread.php?t=863220](http://ubuntuforums.org/showthread.php?t=863220)
As I stated in your other thread it is not impossible but it requires some work and patients that you are not showing. Hardy's xorg has changed compared to the previous versions and it will take some tweaking and trying different methods to see what works and what does not. The biggest hurdle as I see is if your motherboard will cooperate with the two graphics cards. As some will deactivate the onboard graphics if a another graphics card is installed.

---

### Post by PmDematagoda on 2008-07-19
jeremygjohn, you maybe new to the forum but please try and understand that creating duplicate threads(triplicate in your case) is not allowed since it just makes a mess of everything. Also please understand that you are only allowed one bump within 24 hours.

bapoumba:- I merged the three threads together:).

---

### Post by jeremygjohn on 2008-07-19
Would adding the onboard video device into xorg and making a monitor section using that device enable my secound monitor with onboard and my other monitor on 8600GT?

---

### Post by jeremygjohn on 2008-07-20
do i only get responses when i bump it? lol i give up on you guys i get in trouble f or bumping but then no body will help me unless i do.

---

### Post by overdrank on 2008-07-20
> **jeremygjohn said:**
> Would adding the onboard video device into xorg and making a monitor section using that device enable my secound monitor with onboard and my other monitor on 8600GT?

Hi and you may try and use this command ```
gksu displayconfig-gtk
``` then use this to change and detect your graphics. It will make adjustments to your xorg so it will make it easier.


> **jeremygjohn said:**
> do i only get responses when i bump it? lol i give up on you guys i get in trouble f or bumping but then no body will help me unless i do.
I have a spare system that I was trying to configure the two graphics on and I will attempt again but I do work nights and have other things to do. The bumping is ok just do it once a day as this subforum does not move as fast as say Beginners.
Edit typo on the command

---

### Post by jeremygjohn on 2008-07-20
ok thank you for trying to help if i cant get this to work in like a week ill be able to connect both to video card because my converter will arrive but i still want to try this until then.

gksu displaycofig-gtk does nothing?

---

### Post by overdrank on 2008-07-20
> **jeremygjohn said:**
> ok thank you for trying to help if i cant get this to work in like a week ill be able to connect both to video card because my converter will arrive but i still want to try this until then.

gksu displaycofig-gtk does nothing?

I do apologize as a typo in place
```
gksu displayconfig-gtk
```

---

### Post by jeremygjohn on 2008-07-21
ok my converter came today so i have 2 screens on vista business now but like when i run a game my 2nd smaller screen is 1024x768 goes black how came i make it stay in desktop? My main is bigger 1440x900.

---

### Post by overdrank on 2008-07-21
> **jeremygjohn said:**
> ok my converter came today so i have 2 screens on vista business now but like when i run a game my 2nd smaller screen is 1024x768 goes black how came i make it stay in desktop? My main is bigger 1440x900.

Hi and are you asking "how to" in windows?

---

### Post by jeremygjohn on 2008-07-21
nvm what i want to find out is is it possible to get a desktop background to fill both screens but i mean is does not repeat it continues onto the secound one? would it have to be a huge resolution? i have a 2560x1200 and it stops have way on my smaller screen?

---

### Post by jeremygjohn on 2008-07-22
is it too soon to bump?

---

### Post by overdrank on 2008-07-22
> **jeremygjohn said:**
> nvm what i want to find out is is it possible to get a desktop background to fill both screens but i mean is does not repeat it continues onto the secound one? would it have to be a huge resolution? i have a 2560x1200 and it stops have way on my smaller screen?

Are we talking Ubuntu? :) Are you using the nvidia settings to adjust you dual monitors?  If you have not install the setting as of yet you can do so by using synaptic manager and then use the command ```
gksu nvidia-settings
```

---

### Post by jeremygjohn on 2008-07-22
Yes talking about ubuntu now

---

