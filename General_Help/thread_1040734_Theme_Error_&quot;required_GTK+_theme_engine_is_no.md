---
title: "Theme Error: &quot;required GTK+ theme engine is not installed&quot;"
date: 2009-01-15
forum: General Help
---

### Post by jhonnyboy on 2009-01-15
Hey guys I just downloaded Elegant Brit from Gnome-Look and i am getting this error:

"The theme will not look as intended because the required GTK+ theme engine is not installed"

The Theme doesn't show under themes all i can do is customized themes already there. I am guessing the theme doesn't show because of the error. 

I'm fairly new to Ubuntu so i would appreciate any help. Thank you everyone :)

---

### Post by jhonnyboy on 2009-01-16
I would appreciate any and all the help i can get guys. Please...

---

### Post by High_Speed on 2009-01-16
> **jhonnyboy said:**
> Hey guys I just downloaded Elegant Brit from Gnome-Look and i am getting this error:

"The theme will not look as intended because the required GTK+ theme engine is not installed"

The Theme doesn't show under themes all i can do is customized themes already there. I am guessing the theme doesn't show because of the error. 

I'm fairly new to Ubuntu so i would appreciate any help. Thank you everyone :)

I have the same problem.  Only mine says "the theme will not look as intended because the required GTK+ theme engine AURORA is not install."   I've tried installing Aurora a half-dozen times both manually and through the synaptic manager, and it still gives me that error.  I don't know what else to do either.  :(

---

### Post by ellalan on 2009-01-16
> **High_Speed said:**
> I have the same problem.  Only mine says "the theme will not look as intended because the required GTK+ theme engine AURORA is not install."   I've tried installing Aurora a half-dozen times both manually and through the synaptic manager, and it still gives me that error.  I don't know what else to do either.  :(

You can install Aurora engine from this link
[http://www.myscienceisbetter.info/2008/03/how-to-install-aurora-gtk-engine-14-ubuntu-hardy.html](http://www.myscienceisbetter.info/2008/03/how-to-install-aurora-gtk-engine-14-ubuntu-hardy.html)

---

### Post by BigCityCat on 2009-01-16
I will tell you that when it gives you this message you are in the appearance manager, and you are using a theme from a different theme manager. It's ok it is supposed to be in the appearance manager. It's just that the appearance manager can not tell if you have the theme manager for that theme installed. So it is basically saying. "If you don't have the theme manager for this theme that you have selected you are not getting the full benefits of this theme". like I said it is supposed to be in appearance manager, that is part of the process but you have to have the other theme manager installed to get all the aspects of the theme, If you don't have GTK then go install it. It won't change that message because the appearance manager can't tell if you have it installed or not. So it gives you the message either way. 

There is another thread about half the page down on this forum about his already. Not sure why you started a new thread without checking first. Here is the link if you need it.

[http://ubuntuforums.org/showthread.php?t=1039779](http://ubuntuforums.org/showthread.php?t=1039779)

---

### Post by High_Speed on 2009-01-17
> **BigCityCat said:**
> I will tell you that when it gives you this message you are in the appearance manager, and you are using a theme from a different theme manager. It's ok it is supposed to be in the appearance manager. It's just that the appearance manager can not tell if you have the theme manager for that theme installed. So it is basically saying. "If you don't have the theme manager for this theme that you have selected you are not getting the full benefits of this theme". like I said it is supposed to be in appearance manager, that is part of the process but you have to have the other theme manager installed to get all the aspects of the theme, If you don't have GTK then go install it. It won't change that message because the appearance manager can't tell if you have it installed or not. So it gives you the message either way. 

There is another thread about half the page down on this forum about his already. Not sure why you started a new thread without checking first. Here is the link if you need it.

[http://ubuntuforums.org/showthread.php?t=1039779](http://ubuntuforums.org/showthread.php?t=1039779)

Thanks for the help.  But how do we actually install the full Theme Manager?  I don't see System --> Preferences --> Themes 

How do I get that?

---

### Post by BigCityCat on 2009-01-17
synaptic package manager and search and install.

---

### Post by jhonnyboy on 2009-01-17
what do we search for? I already have GTK+ installed...

---

### Post by jhonnyboy on 2009-01-17
i searched for gtk2 engines and tons of them came out. I already have the basic one's installed like gtk2-engines, but there are a lot of others that i dont such as gtk2-engines-sapwood, gtk2-engines-xfce and etc...I don't know which one to pick and the error didn't specify which one to pick :(

---

### Post by jhonnyboy on 2009-01-17
ok so this link helped me out a lot. For anyone trying to get this to work...
[http://art.ubuntuforums.org/showthread.php?t=1035018](http://art.ubuntuforums.org/showthread.php?t=1035018)

That solved the error msg. 

I have a quick question though. Why can't i see my theme under appreance>themes. I can only see it when i click on a theme that i already have and i try to customize that theme. Did i not install it correctly?

To install all i did was extract the files and install them by clicking on the install button under themes. Thanks guys!

---

### Post by BigCityCat on 2009-01-17
you need gtk+2.0 theme changer. Search for it in add remove - all available apps. Install it and look in your system tools. After that follow the explanation in the other link I provided in this thread.

---

### Post by BigCityCat on 2009-01-17
> **jhonnyboy said:**
> ok so this link helped me out a lot. For anyone trying to get this to work...
[http://art.ubuntuforums.org/showthread.php?t=1035018](http://art.ubuntuforums.org/showthread.php?t=1035018)

That solved the error msg. 

I have a quick question though. Why can't i see my theme under appreance>themes. I can only see it when i click on a theme that i already have and i try to customize that theme. Did i not install it correctly?

To install all i did was extract the files and install them by clicking on the install button under themes. Thanks guys!

read the other link I provided in this thread and you will figure it out.

---

### Post by jhonnyboy on 2009-01-17
> **BigCityCat said:**
> you need gtk+2.0 theme changer. Search for it in add remove - all available apps. Install it and look in your system tools. After that follow the explanation in the other link I provided in this thread.

I did a search for the "gtk+2.0 theme changer" under add/remove and i don't see it there. I tried looking under Synpateic Package Manager but couldn't find it there either. Any suggestions?

---

### Post by jhonnyboy on 2009-01-17
ok nevermind the above post. I was able to download and install the GTK 2.0 Theme changer. Now I am getting the error "This theme will not look as intended because the required GTK+ theme 'Elegant Brit' is not installed." but i just installed it lol I clicked on install and clicked on Elegant Brit.

---

### Post by BigCityCat on 2009-01-17
It's just that appearance manager doesn't know if you installed it or not so just ignore it. you first must select the theme in gtk. its in your system tools. you work with both gtk theme manager and your appearance manager.

try and do all of this

Let me give you some real help with themes from a guy that knew very little not too long ago and I will tell you. You can't get help like this very often.

Yes, go into add remove or synaptic and search for gtk 2 theme changer. Once installed go to this website

[http://www.gnome-look.org/index.php?...78x179&page=16](http://www.gnome-look.org/index.php?...78x179&page=16)

It's the best one. On the left side of the screen you will see gtk 2 themes. Do highest rated. Find the ones you like. Download the packages to your desktop. Once your done downloading goto desktop and Right click on packages and do extract here. Hit your start menu and open appearance settings. Drag and drop the files you extracted on your desktop into the appearance manager. Sometimes the files have multiple themes and you have to open them and then drag and drop, and sometimes some themes just will not work, but most will. Slickness is a real good one. After you have draged and dropped. Hit start and go to system tools and select gtk manager. Select the theme you want to use and you will see all your controls and panel change. Then go back to appearance and hit customize. Scroll around and find the borders and controls that match the theme you selected in gtk.

Drag and drop for icons as well.

If you have compiz installed you need the compiz icon. If you don't have it, go into synaptic and search for fusion icon. Install it. After it is installed hit start, go to system tools and select the compiz icon. It should appear on your panel somewhere. Right click on it. go to select window decorator. Select gtk. Then right click on it again select window manager. Select compiz. Select it again. Go to the top and select settings manager. This is how you set up the cube.

This website is the best for describing how to set up the cube. [http://forlong.blogage.de/entries/20...-Compiz-Fusion](http://forlong.blogage.de/entries/20...-Compiz-Fusion)

Good luck. Once you get it you will love it.

---

### Post by BigCityCat on 2009-01-17
Let us know when you get it. and post a screenshot when you get it. we don't work for free lol.

---

### Post by jhonnyboy on 2009-01-18
hey guys. I was cracking up when i saw that "we don't work for free" :)

Ok...unfortunately I am posting the wrong screen shot lol

I am still getting the error after following all those steps. I have posted a screenshot so you may see how my desktop is looking. Don't give up on my please :( 

Thanks again everyone!

[IMG]http://www.freeimagehosting.net/uploads/332d25ae57.png[/IMG]

---

### Post by BigCityCat on 2009-01-18
Like I said ignore that error message.

3 questions.

Do you have emerald installed?

Is GTK 2.0 theme changer installed? Look in system tools to see if it's there.

Have you extracted the elegant brit file, and if so, have you draged and dropped it into your appearance manager?

If you have. Look at that screenshot and you see the customize button. Click on that and scroll to find elegant brit borders and controls and set those. You need to do that in GTK as well. I don't like that elegant brit at all, lol. Sorry it's just me.

---

### Post by BigCityCat on 2009-01-18
Here try this one.

[http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210](http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210)

Oh yeh, right click on your panel and select properties. Check to see that use system theme is marked.

---

### Post by jhonnyboy on 2009-01-19
1. Ya i have emerald installed. 
2. The GTK theme changer is installed. 
3. I could customize things with the elegant brit and etc...but how come i can't see it as a "theme" like i can see the rest. In other words when i right click my desktop>apperance>themes "Elegant Brit" is not under there and i can only see it if i click customize. I'm so lost, it seems i'm never going to get this to work lol
I'm going to be so happy when i learn how to do this. :)

---

### Post by BigCityCat on 2009-01-19
I think all you have to do is open gtk theme changer. scroll to elegant brit, apply it, close gtk, and open appearnce manager, select any theme really and customize it by selecting elegant brit contols and borders. Make sure you open compiz icon and select gtk as your theme manaGER.

---

