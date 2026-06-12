---
title: "Compiz restore"
date: 2011-03-20
forum: Desktop Environments
---

### Post by 1chess2u Christian on 2011-03-20
My compiz has been acting up lately since I updated my Ubuntu about two weeks ago. In fact, it is not working at all. All the open window applications do not have a close bar, and I cannot drag them, so in order to close the application, I have to right click on that application's icon on the panel, which is very frustrating. I know that I still have it on my computer, I just don't know why it won't work. :confused:

---

### Post by WlaadDyaab on 2011-03-20
> **1chess2u Christian said:**
> My compiz has been acting up lately since I updated my Ubuntu about two weeks ago. In fact, it is not working at all. All the open window applications do not have a close bar, and I cannot drag them, so in order to close the application, I have to right click on that application's icon on the panel, which is very frustrating. I know that I still have it on my computer, I just don't know why it won't work. :confused:

I don't know about the Compiz or Ubuntu restoration, but once, I had something similar to your problem; not finding buttons to close or minimising or restoring windows...etc

I think the solution for me was:

- System > Preferences > Appearance > Appearance Preferences (windows) (or right-click on Desktop > Change Desktop Background > )Appearance Preferences (windows))

Note: make sure you remember what you have at the moment i.e. Is it "None", or "Normal", or "Extra", or "Custom". So make sure you remember what you have ticked/chosen at the moment

- In "Preferences Appearance" windows - "Visual Effects" tab - Tick "None"

- Then again go back to "Preferences Appearance" windows - "Visual Effects" tab - Tick whatever you had before you chose "None"

Then open up anything to see if the "Close"/"Minimise"/"Restore" are back

Hopefully that will sort out the problem :)

---

### Post by 1chess2u Christian on 2011-03-20
What if it is already at None?

---

### Post by 1chess2u Christian on 2011-03-20
Never mind. I think that I fixed it. I have the close bar back on top of the windows!:D
Thank you!!

---

### Post by 1chess2u Christian on 2011-03-20
sorry for posting so many times, but do you have any idea how to restore compiz at all? even an apt-get would be okay

---

### Post by WlaadDyaab on 2011-03-20
> **1chess2u Christian said:**
> What if it is already at None?

Then just try and change around Lol

I learnt that if you take a strait path with computers you'll get really frustrated, but if you play around and crash this and mess that up...then trying to put it back together with yourself you'll probably learn more than than just taking strait instructions

Obviously I have a cheap PC for that Lol. I use my Laptop for the important stuff where I can't mess around with

---

### Post by WlaadDyaab on 2011-03-20
> **1chess2u Christian said:**
> sorry for posting so many times, but do you have any idea how to restore compiz at all? even an apt-get would be okay

Do you mean that you unistalled Compiz and can't get it back?

---

### Post by realzippy on 2011-03-20
```
sudo apt-get purge compiz*
```
uninstalls compiz

```
cd $HOME && rm -rf .compiz/ .config/compiz/
```
deletes compiz config files

---

### Post by 1chess2u Christian on 2011-03-20
> **WlaadDyaab said:**
> Then just try and change around Lol

I learnt that if you take a strait path with computers you'll get really frustrated, but if you play around and crash this and mess that up...then trying to put it back together with yourself you'll probably learn more than than just taking strait instructions

Obviously I have a cheap PC for that Lol. I use my Laptop for the important stuff where I can't mess around with

Thanks for the advice, but I have neither the know-how nor the resources to mess around with stuff, and tampering with things that I don't know about usually makes me more frustrated than if I just got a strait path to the goal.

---

### Post by 1chess2u Christian on 2011-03-20
> **WlaadDyaab said:**
> Do you mean that you unistalled Compiz and can't get it back?

No. I just apologized for not making one reply instead of three. I definitely have Compiz on my computer, but it just won't work.

---

### Post by 1chess2u Christian on 2011-03-20
> **realzippy said:**
> ```
sudo apt-get purge compiz*
```
uninstalls compiz

```
cd $HOME && rm -rf .compiz/ .config/compiz/
```
deletes compiz config files

How do I get it back? I still want Compiz. I have gotten quite used to it (will this delete all of my settings for compiz?

---

