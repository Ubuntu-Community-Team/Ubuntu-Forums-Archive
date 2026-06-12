---
title: "How do you enable the windows destroy effect in Compiz?"
date: 2010-10-30
forum: Desktop Environments
---

### Post by geek2330 on 2010-10-30
I saw a video on youtube, there was an effect that when he closed any program or window it shows like multiple small boxes breaking down in pieces, very cool.

I looked in the CompizConfig Settings Manager but don't see that option when closing programs/screens.

---

### Post by GreatKeyHunter on 2010-10-30
Thats simple, first just in case make sure u have compiz extras.  you can get them by typing in the terminal sudo apt-get install compiz-fusion-plugins-extra.  
Now go to system > preference > appearance.   Click on visual effects tab, then click custom.  Click on the tab labeled animations, then check enable animations and enable extra animations.  Then choose the effect you want from the list provided.  
You can also use compiz to further customize the behavior of the effects

---

### Post by hiakaash on 2010-10-31
I've followed your steps but in ubuntu 10 there is no Custom tab under Visual Effects tab... any other ideas???

---

### Post by GreatKeyHunter on 2010-10-31
> **hiakaash said:**
> I've followed your steps but in ubuntu 10 there is no Custom tab under Visual Effects tab... any other ideas???

The only thing i can think off, is make sure have checked the features that you want in compiz enabled.  see to it that extra effects under visual effects tabs is also checked, and below that you should see a custom tab.

---

### Post by geek2330 on 2010-10-31
keyhunter, I don't have a custom radio button either under Visual Effects, just None/Normal/Extra. What specific feature will enable this from within Compiz?
In Compiz i don't see anything about "extra" animations.
Can you share a screen from your Compiz pointing to the setting you're making reference to please.

Thanks

---

### Post by georgemc on 2010-10-31
This thread got me playing with compiz :)
 

 I am using 10.04.1LTS with a Nvidia GTS250 and the latest hardware driver.
 

 My “Appearance preferences”  panel does not have the “Custom” radio button, however, I found in “synaptic”  the package “compizconfig-settings-manager”.
 

 Open “synaptic” and search for “compiz”, in the list you should be able to find “compizconfig-settings-manager”; mark it for installation and it should also mark the package “python-compizconfig”.
 

 After installation look for the menu item “System->Preferences->Compizconfig settings manager” and run it.
 

 I found a lot of really neat visual effects there.
 

 Hope this helps and have fun.
 

 George

---

### Post by geek2330 on 2010-10-31
george, but do you now have that "Custom" radio buttin under Visual Effects tab in Apperances ?

I have had System->Preferences->Compizconfig settings manager installed, is just that "custom" radio button must be enabled somehow by Compiz....

---

### Post by GreatKeyHunter on 2010-10-31
[FONT=monospace]Alright, at first when i got ubuntu out of the box, there was no option for Custom right below extra effects under the visual effects tab.  What i did was that i checked the extra effects and then went on to install compiz.  This is the order of steps that i follow. 
Open the terminal by going applications > accessories > terminal
then type the following:
sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-extra

After that, i open ccsm which you can open by either typing in the terminal ccsm or hold alt +f2 and type ccsm.
under ccsm this is what i have enabled/checked

left sidebar general tab:
commands + gnome compatability

left sidebar effects tab: 
make sure u check 3d windows, animations, animations add-on, cube reflection and deformation, wobbly windows. (animations and animations add ons is a must for the exploding windows effect)

left sidebar the preferences: in the profile & backend i have my profile as default, and backend under GConf Configuration Backend and i have checked enable integration into the desktop environment.

After all that, go back to preference > appearance > visual effects tab, and it should give u an option for custom.

If that doesn't not work let me know.  But it should.  Im running Ubuntu 10.10 with an Nvidia 9800GT graphics card.  Thats how i have always gotten compiz to work for me. Hope this guide helps you out.
[/FONT][FONT=monospace]   [/FONT]

---

### Post by geek2330 on 2010-10-31
I still don't get that "Custom" radio button under appearance, could it be b/c i had Compiz installed first or out of order? Or the video card?

I will try this on an older PC at work tomorrow and follow the steps.

---

### Post by geek2330 on 2010-10-31
i just tried again and when i go back to Appearance Visual Effects tab neither of the radio buttons is selected, if i select "Extra" then go back to Compiz i then lost the settings i did under Effects.

If i go back and enable those settings in Compiz then go back to Appearance no radio button is selected and no "Custom" option either.

Hmmmmm.....

..

---

### Post by GreatKeyHunter on 2010-10-31
Thats strange, i doubt thats the case, by any chance do u have the compiz fusion icon?  If not just down load it from the ubuntu resource center.  What kind of graphics card do u have? 

edit: can you at least do some of the window tricks like ring switcher? so that at least i know that compiz is working.

---

### Post by stinkeye on 2010-11-01
Don't worry about the custom button.
That just appears when you have changed some of the settings in ccsm.
Install fusion-icon
```
sudo apt-get install fusion-icon
```

Add fusion-icon to startup applications with this in the command box...
```
fusion-icon -n
```

logout and in.
Right click on fusion-icon in your notification area and select compiz as your window manager.

> **geek2330 said:**
> I saw a video on youtube, there was an effect that when he closed any program or window it shows like multiple small boxes breaking down in pieces, very cool.

I looked in the CompizConfig Settings Manager but don't see that option when closing programs/screens.


If you have compiz-fusion-plugins-extra installed
you should have an **Animation Add-ons** plugin.Enable it.
You should then have an explode effect in the **Animations** plugin.

---

### Post by geek2330 on 2010-11-01
ok, thanks. Trying this on another pc at work and can see the explode effects and the others, and they are enabled, however i don't get to see the effects except for the window wobbling when you grab the top portion of a screen and move it with the mouse.

If i close or minimize something i don't see the fire or explode effects, maybe i'm missing something very simple.....!!

---

### Post by geek2330 on 2010-11-01
i think i got it this time........

---

### Post by geek2330 on 2010-11-01
Thanks stinkeye, that helped a lot...

---

