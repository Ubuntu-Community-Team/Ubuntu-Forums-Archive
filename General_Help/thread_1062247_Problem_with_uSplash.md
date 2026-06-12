---
title: "Problem with uSplash"
date: 2009-02-06
forum: General Help
---

### Post by Sashin on 2009-02-06
Recently I've installed a uSplash theme from gnome-look called ubuntu smooth.

[http://gnome-look.org/content/show.php?content=93386](http://gnome-look.org/content/show.php?content=93386)

However after installing the .deb file I've lost my boot loader altogether (I see text).

Is it possible to get it back, preferably with the newly installed theme?

---

### Post by Tim Sharitt on 2009-02-07
When you say you have lost your boot loader, what do you mean? Do you get the grub screen and can't boot Ubuntu (which could make some since since usplash is what you modified) or can you not boot into grub at all?

---

### Post by Sashin on 2009-02-07
Sorry, I meant splash screen not bootloader.

I see text instead of a graphical one.

---

### Post by travmon69 on 2009-02-07
> **Sashin said:**
> Recently I've installed a uSplash theme from gnome-look called ubuntu smooth.

[http://gnome-look.org/content/show.php?content=93386](http://gnome-look.org/content/show.php?content=93386)

However after installing the .deb file I've lost my boot loader altogether (I see text).

Is it possible to get it back, preferably with the newly installed theme?

do you have startup manager installed?

---

### Post by johnjohn2 on 2009-02-07
> **travmon69 said:**
> do you have startup manager installed?

Sounds to me like it does not like you resolution 

try this

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Section 6 is of interest  

Regards John

---

### Post by Sashin on 2009-02-07
I do have start up manager installed.

---

### Post by travmon69 on 2009-02-07
> **Sashin said:**
> I do have start up manager installed.

you should be able to use it to go back to the original. I can't seem to get different usplash screens to work proper neither. :-k

---

### Post by Sashin on 2009-02-07
Okay I've gone back to the original which is alright. A smoother version would have been good though.

---

### Post by travmon69 on 2009-02-07
> **Sashin said:**
> Okay I've gone back to the original which is alright. A smoother version would have been good though.

 yep, i hear that. i guess the original is better than black with white text.  do you have orange text under the ubuntu progress bar? i think it's done with ubuntu tweak.

---

### Post by Sashin on 2009-02-07
No I don't.

---

### Post by travmon69 on 2009-02-07
> **johnjohn2 said:**
> Sounds to me like it does not like you resolution 

try this

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Section 6 is of interest  

Regards John

i was looking at this an made some changes but it said no splash image found

---

### Post by travmon69 on 2009-02-07
> **Sashin said:**
> No I don't.

the show text option is in startupmanager.   i still cant get it to show new usplash tried the chrome ones.

---

### Post by johnjohn2 on 2009-02-07
> **travmon69 said:**
> i was looking at this an made some changes but it said no splash image found

did you download the deb or did you install from a repository?


what is your screen res and graphics card?

---

### Post by travmon69 on 2009-02-07
> **johnjohn2 said:**
> did you download the deb or did you install from a repository?


what is your screen res and graphics card?

i got theme from here [http://www.gnome-look.org]("http://www.gnome-look.org")  i searched for usplash. Then selected the tab  highest rated. I extracted the downloaded file. the file that startupmanager wants is the usplashwhatever.so file. I think.   
  to install it i went to my home folder, went to view tab checked show hidden files. found the  .themes folder then dragged the usplashwhatever.so inside the .themes folder. went to startupmanager and added it through manage usplash.   i also follwed the post above to edit the folder it says and and grub. then i updated grub like it says. still never worked. says no usplash found?
   
screen res i choose is 1024x768  card is ati radeon 9250  128mb

---

