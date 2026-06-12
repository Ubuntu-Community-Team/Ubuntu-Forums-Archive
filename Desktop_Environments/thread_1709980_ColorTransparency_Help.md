---
title: "Color/Transparency Help"
date: 2011-03-19
forum: Desktop Environments
---

### Post by ChameleonQS on 2011-03-19
I like the compositor options I get from Xubuntu rather Ubuntu because I havent really found a way to make the inactive windows transparent in Ubuntu. But I also like the transparency options I get for the panels on Ubuntu. I can make the panel transparent but keep the icons and text and Im pretty sure launchers not. Is there a way I can edit the panels in such a way in Xubuntu or vise versa for Ubuntu with the compositor options on Xubuntu?

First Screenshot is Ubuntu 
Second Screen shot is Xubuntu

I want the red transparent panel from Ubuntu on Xubuntu or the compositing style from Xubuntu to Ubuntu.

Would be awesome if someone could help me.

-Thanks

---

### Post by Dutch70 on 2011-03-19
Just curious, how do you do it in Xubuntu? 

I thought for sure Compiz would do it in Ubuntu, but can't seem to find the plug-in.

---

### Post by mcduck on 2011-03-19
The "Trailfocus"-plugin for Compiz is what you are looking for.

If it's not installed by default, get the "compiz-fusion-plugins-extra" -package.

(Actually "Opacify"-plugin might work as well if you just want active windows as opaque and inactive ones as transparent.)

---

### Post by ChameleonQS on 2011-03-20
> **Dutch70 said:**
> Just curious, how do you do it in Xubuntu? 

I thought for sure Compiz would do it in Ubuntu, but can't seem to find the plug-in.

Do what? If you mean the transparency of inactive windows then its on the compositor tab at the Window Manager Tweaks.

> **mcduck said:**
> The "Trailfocus"-plugin for Compiz is what you are looking for.

If it's not installed by default, get the "compiz-fusion-plugins-extra" -package.

(Actually "Opacify"-plugin might work as well if you just want active windows as opaque and inactive ones as transparent.)

I will try this, but do I use this for the panel on Xubuntu or to make the inactive windows tansparent on Ubuntu?

---

### Post by Dutch70 on 2011-03-20
Pretty sure he's talking about making the inactive windows transparent on Ubuntu.

Edit: Yes, he is. It's the opacity level of unfocused windows.
Within the Trailfocus plug-in.

---

### Post by Krytarik on 2011-03-20
The "Opacify" plugin doesn't work like you want it, if I understood you right.

But it may be possible to achieve that with the "Trailfocus" plugin, if it is possible to set its options accordingly.

Unfortunately X/Compiz don't provide a window state like "active" and "inactive", I extensively searched for it yesterday, although it is obviously well aware of the actual state, but it doesn't tell us, really annoying. Otherwise we could simply put the rules of the "Opacity..." plugin accordingly.

---

### Post by Dutch70 on 2011-03-20
> **Krytarik said:**
> The "Opacify" plugin doesn't work like you want it, if I understood you right.

But it may be possible to achieve that with the "Trailfocus" plugin, if it is possible to set its options accordingly.

Unfortunately X/Compiz don't provide a window state like "active" and "inactive", I extensively searched for it yesterday, although it is obviously well aware of the actual state, but it doesn't tell us, really annoying. Otherwise we could simply put the rules of the "Opacity..." plugin accordingly.

It's not the Opacify plug-in.

 It's the "opacity setting", within the trailfocus plug-in. You can see it in the pic I put in the previous post. 
The 2nd pic shows that it does what I believe the OP is looking for.

 You may also want to go to the "behavior" tab and set the "window to start fading" option from 2 to 1.

---

### Post by Krytarik on 2011-03-20
> **Dutch70 said:**
> It's not the Opacity plug-in.

Like I said, right, because you can't specify a rule for it.

---

### Post by ChameleonQS on 2011-03-21
> **mcduck said:**
> The "Trailfocus"-plugin for Compiz is what you are looking for.

(Actually "Opacify"-plugin might work as well if you just want active windows as opaque and inactive ones as transparent.)

That is exactly what i want but Opacify only works through focus on where the mouse is. I just want all windows other than the one im on (active) to be transparent to some degree. Opacify doesnt really do this, only when im looking around and when the focus from the mouse is on other windows do the other windows opacify. I want the windows to be transparent at all times unless it is active and tranparent to a degree if they are not.

Trailfocus was close but it didnt quite do it. Either that or I didnt quite get the hang of it yet. It keeps 2 windows opaque and the rest transparent. I only want the current active window to be opaque and not transparent.

Thanks mcduck for the reply and for helping me, everyone else included too. =)

These are the options I get from the compositor on the Xfce manager [http://images.maketecheasier.com/2010/11/xfce4-compositor.png]("http://images.maketecheasier.com/2010/11/xfce4-compositor.png")

---

### Post by Dutch70 on 2011-03-21
> **ChameleonQS said:**
> 

Trailfocus was close but it didnt quite do it. Either that or I didnt quite get the hang of it yet. **It keeps 2 windows opaque and the rest transparent. I only want the current active window to be opaque and not transparent.**


As I said in my previous post...
> You may also want to go to the "behaviour" tab and set the "window to start fading" option from 2 to 1.


You can see the exact setting in the pic.

---

### Post by ChameleonQS on 2011-03-21
> **Dutch70 said:**
>  You may also want to go to the "behavior" tab and set the "window to start fading" option from 2 to 1.

Im not sure why but it keeps one extra window opaque. Am I doing anything wrong with settings?

Edit:Also I set different settings from high, medium, and low but the actual opacity didnt really change.
I think somethings wrong

---

### Post by mcduck on 2011-03-21
> **ChameleonQS said:**
> Im not sure why but it keeps one extra window opaque. Am I doing anything wrong with settings?

Set the "number of windows to track" smaller. The second window *is* transparent, but only very slightly. Exactly 1/150 of the transparency value you have configured...

Trailfocus makes increases the transparency depending on the order in which the windows have been active. So current window is opaques, previous one is a bit transparent, the one before that is bit more transparent again and so on. The "Number of Windows to track" sets how long the trail is, and therefore also how much the transparency increases per each step.

You have set the windows to track to 150, that means that the 150th window would get the transparency you have set. If you ever happen to have that many windows open. :D

So, if you want the current window to be opaque and all the others to have exactly the transparency value you set, you'd need to set the windows to track to "1".

Setting it to "2" would make current window opaque, one before that half the transparency you configure, and all others exactly the transparency you have set. Setting of "3" would make first window opaque, second 1/3 of the set transparency, third window 2/3 of the transparency and rest full transparency. And so on...

---

### Post by ChameleonQS on 2011-03-21
> **mcduck said:**
> Set the "widnows to track" smaller. The second window *is* transparent, but only very slightly. Exactly 1/150 of the transparency value you have configured...

Trailfocus makes increases the transparency depending on the order in which the windows have been active. So current window is opaques, previous one is a bit transparent, the one before that is bit more transparent again and so on.

You have set the windows to track to 150, that means that the 150th window would get the transparency you have set. If you ever happen to have that many windows open. :D

So, if you want the current window to be opaque and all the others to have exactly the transparency value you set, you'd need to set the windows to track to "2".

Still no luck I set it to two and one but didnt get it to work.

---

### Post by Dutch70 on 2011-03-21
Well, I'm not sure about that Chameleon. I had to change my background so you could tell, but as you can see in mine. It seems to be working great. 
 The only difference in my settings seems to be where you have the opacity level at 31, I have mine at 1 & where you have 150, I kept the default 5 since I'm not exactly sure how that will affect the windows anyway. Until I know for sure, I thought I'd keep the default.

---

### Post by Dutch70 on 2011-03-21
Double post :(

---

### Post by Dutch70 on 2011-03-21
After takinga 2nd look at yours, it looks like all of them are transparent except for 2. That setting may not have taken effect yet. I think you're on the right track though.

Actually, the 2nd window that is opaque, may be because it has other windows behind it. Not quite sure about that. You may have to lower that setting from 31 to 1, to get better transparency through 2 windows.

---

### Post by ChameleonQS on 2011-03-21
> **Dutch70 said:**
> Well, I'm not sure about that Chameleon. I had to change my background so you could tell, but as you can see in mine. It seems to be working great. 
 The only difference in my settings seems to be where you have the opacity level at 31, I have mine at 1 & where you have 150, I kept the default 5 since I'm not exactly sure how that will affect the windows anyway. Until I know for sure, I thought I'd keep the default.

I've also tried it at 1. =( 
Have you tried opening more windows and clicking/cycling through them? Because at first all of my inactive windows are transparent until i start to cycle through them, then theres that one extra opaque window.

> **Dutch70 said:**
> After takinga 2nd look at yours, it looks like all of them are transparent except for 2. That setting may not have taken effect yet. I think you're on the right track though.

Actually, the 2nd window that is opaque, may be because it has other windows behind it. Not quite sure about that. You may have to lower that setting from 31 to 1.

Before I apply the new settings I restore defaults then I apply the new ones. I even enable/disable them.

---

### Post by mcduck on 2011-03-21
> **ChameleonQS said:**
> Still no luck I set it to two and one but didnt get it to work.

Try setting the transparency higher and you'll see the effect better. If it doesn't work you probably have some other active Compiz plugin that also changes the transparency of windows.

I made two screenshots, one with trail length of 1, and the other with 5. I have set opacity to 25 and saturation to 10.

edit: you might also want to test with as simple background image as possible, it's pretty hard to say for sure if its working or not with your current background. To me it seems like it *is* working, fading starts immediately after the current window, and has two steps just like there should be with your current settings.

---

### Post by Dutch70 on 2011-03-21
> **ChameleonQS said:**
> I've also tried it at 1. =( 
Have you tried opening more windows and clicking/cycling through them? Because at first all of my inactive windows are transparent until i start to cycle through them, then theres that one extra opaque window.


Yes, it seems that the order that the windows are in, or which one was focused on last, affects the transparency level. 

 mcduck, how do you set the "transparency higher" or did you mean the opacity lower?

---

### Post by mcduck on 2011-03-21
> **ChameleonQS said:**
> I've also tried it at 1. =( 
Have you tried opening more windows and clicking/cycling through them? Because at first all of my inactive windows are transparent until i start to cycle through them, then theres that one extra opaque window.



Before I apply the new settings I restore defaults then I apply the new ones. I even enable/disable them.

Sorry, it seems you haven't noticed I edited my post with the instructions immediately after posting it (I had to actually open my laptop and enable the plugin to check the settings instead of just typing them out of my memory. Always a good idea with GUI applications :P).

If you want the current window opaque, and all the others at the set transparency, the trail length must be set to "1".

If you set it to "2", the current window will be opaque, one before that will be half the set transparency, and all others have the set transparency.

---

### Post by ChameleonQS on 2011-03-21
aaa> **mcduck said:**
> Try setting the transparency higher and you'll see the effect better. If it doesn't work you probably have some other active Compiz plugin that also changes the transparency of windows.

I made two screenshots, one with trail length of 1, and the other with 5. I have set opacity to 25 and saturation to 10.

edit: you might also want to test with as simple background image as possible, it's pretty hard to say for sure if its working or not with your current background. To me it seems like it *is* working, fading starts immediately after the current window, and has two steps just like there should be with your current settings.

I set opacity to 1. Well here are my settings for trailfocus.
I also disabled any other compiz app that has anything to do with opacity/transparency.

Also I think if you cycle through the windows after you set the settings on trailfocus youll get the same effects Im getting.

---

### Post by mcduck on 2011-03-21
> **Dutch70 said:**
> Yes, it seems that the order that the windows are in, or which one was focused on last, affects the transparency level. 

 mcduck, how do you set the "transparency higher" or did you mean the opacity lower?
high transparency is the same as low opacity. :D

---

### Post by mcduck on 2011-03-21
> **ChameleonQS said:**
> aaa

I set opacity to 1. Well here are my settings for trailfocus.
I also disabled any other compiz app that has anything to do with opacity/transparency.

Also I think if you cycle through the windows after you set the settings on trailfocus youll get the same effects Im getting.

If I cycle through my windows, I get exactly the effect you can see in my screenshots. :D

---

### Post by ChameleonQS on 2011-03-21
I even tried to set the values of the Window to start fading to 0 through the gconf-editor that didnt work either since 1 leaves me with 2 opaque windows.

---

### Post by mcduck on 2011-03-21
I can't say anything about 2 opaque windows or not, as on your screenshot the windows are stacked on top of each other, and white window on top of a white window would still be pretty much white regardless of transparency.

But anyway there's definitely something else wrong on your setup, as opacity of "1" should make the windows pretty much invisible. If you are absolutely sure no other plugin is affecting the window opacities, try restarting Compiz. Your setttings crearly aren't working, no matter the trail legth, you shouldn't even be able to see that many windows with the opacity settings you have. :D

---

### Post by ChameleonQS on 2011-03-21
> **mcduck said:**
> I can't say anything about 2 opaque windows or not, as on your screenshot the windows are stacked on top of each other, and white window on top of a white window would still be pretty much white regardless of transparency.

But anyway there's definitely something else wrong on your setup, as opacity of "1" should make the windows pretty much invisible. If you are absolutely sure no other plugin is affecting the window opacities, try restarting Compiz. Your setttings crearly aren't working, no matter the trail legth, you shouldn't even be able to see that many windows with the opacity settings you have. :D

Thanks alot! that worked. I cant believe I hadnt restarted compiz.
Thanks alot mcduck! It works great now, cant express my gratitude lol. 

Thanks to everyone else too!
[SOLVED]

---

### Post by Dutch70 on 2011-03-21
Great! Glad you got it working like you want. No use wasting these pics I just took though. :D

The brightness level makes a huge diff in the level of transparency too. Compare the pics & the setting.

---

### Post by ChameleonQS on 2011-03-21
> **Dutch70 said:**
> Great! Glad you got it working like you want. No use wasting these pics I just took though. :D

The brightness level makes a huge diff in the level of transparency too. Compare the pics & the setting.

Yup =D, im already playing around with the other settings.

---

