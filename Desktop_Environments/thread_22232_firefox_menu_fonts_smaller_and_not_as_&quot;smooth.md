---
title: "firefox menu fonts smaller and not as &quot;smooth&quot; as usual"
date: 2005-03-26
forum: Desktop Environments
---

### Post by greatshape on 2005-03-26
I 've just installed kubuntu on my laptop.
Everything works great, but the menu fonts in firefox don't look the same as wih Ubuntu or my other box running Suse 9.2. The are smaller and not as smooth as normal. I have the same in openoffice.
As far as i remember i had this once before about 1 year ago when i installed firefox without XFT+GTK support. After installing the version with GTK+XFT the problem was solved then.   
Any idea's?
tnx
Steve

---

### Post by wbeck85 on 2005-03-26
[QUOTE=greatshape]I 've just installed kubuntu on my laptop.
Everything works great, but the menu fonts in firefox don't look the same as wih Ubuntu or my other box running Suse 9.2. The are smaller and not as smooth as normal. I have the same in openoffice.
As far as i remember i had this once before about 1 year ago when i installed firefox without XFT+GTK support. After installing the version with GTK+XFT the problem was solved then.   
Any idea's?
tnx
Steve[/QUOTE]
 I FIGURED IT OUT!!!

This has been bothering me too since I installed Kubuntu several weeks ago. THis afternoon, I finally found a package that solves this problem.
The problem is that Firefox is using GTK to render, or whatever. I know very little about this. But I do know that Gnome uses GTK and KDE uses QT for the most part. Please, someone correct me if I am wrong.
So, KDE is not rendering the GTK fonts correctly in Firefox ro any other gnome based app. the solution?

$ sudo apt-get install gtk2-engines-gtk-qt
(or install via synaptic/kynaptic/kpackage)

Once it is installed, go to settings:/LookNFeel/ in Konqueror. Click on the new icon that is there. It is the gnome footprint and says "GTK Styles and Fonts." Under GTK Styles, select "Use another style" and select "Qt."  Under "GTK Fonts" Select "Use another font" and change it to whatever you want. I suppse you could leave the two choices at "Use my KDE..." but for some reason, that did not work for me.
Anyway, open up Firefox/thunderbird/synapitc/gaim and marvel at the beauty!

---

### Post by greatshape on 2005-03-26
[QUOTE=wbeck85]I FIGURED IT OUT!!!

$ sudo apt-get install gtk2-engines-gtk-qt
(or install via synaptic/kynaptic/kpackage)

Once it is installed, go to settings:/LookNFeel/ in Konqueror. Click on the new icon that is there. It is the gnome footprint and says "GTK Styles and Fonts." Under GTK Styles, select "Use another style" and select "Qt."  Under "GTK Fonts" Select "Use another font" and change it to whatever you want. I suppse you could leave the two choices at "Use my KDE..." but for some reason, that did not work for me.
Anyway, open up Firefox/thunderbird/synapitc/gaim and marvel at the beauty![/QUOTE]

Perfect job man!!!!
Works like a charm!! Tnx!!

Regards, steve.

---

### Post by ensenadaubuntulover on 2005-05-21
[QUOTE=wbeck85]I FIGURED IT OUT!!!

This has been bothering me too since I installed Kubuntu several weeks ago. THis afternoon, I finally found a package that solves this problem.
The problem is that Firefox is using GTK to render, or whatever. I know very little about this. But I do know that Gnome uses GTK and KDE uses QT for the most part. Please, someone correct me if I am wrong.
So, KDE is not rendering the GTK fonts correctly in Firefox ro any other gnome based app. the solution?

$ sudo apt-get install gtk2-engines-gtk-qt
(or install via synaptic/kynaptic/kpackage)

Once it is installed, go to settings:/LookNFeel/ in Konqueror. Click on the new icon that is there. It is the gnome footprint and says "GTK Styles and Fonts." Under GTK Styles, select "Use another style" and select "Qt."  Under "GTK Fonts" Select "Use another font" and change it to whatever you want. I suppse you could leave the two choices at "Use my KDE..." but for some reason, that did not work for me.
Anyway, open up Firefox/thunderbird/synapitc/gaim and marvel at the beauty![/QUOTE]



EXCELLENT!!! many many thanks my eyes feel better now!!!

---

### Post by ceti on 2005-05-22
Where's this LooknFeel thing?
Can't find it.
Thanx.

---

### Post by greatshape on 2005-05-22
[QUOTE=ceti]Where's this LooknFeel thing?
Can't find it.
Thanx.[/QUOTE]

In the address field from Konqueror, type  " settings:/LookNFeel/ "   
(without the " " of course!)  :) 
Regards, Steve

---

### Post by ceti on 2005-05-22
[QUOTE=greatshape]In the address field from Konqueror, type  " settings:/LookNFeel/ "   
(without the " " of course!)  :) 
Regards, Steve[/QUOTE]


Ok, I'll try it.
Thanx.

---

### Post by angrykeyboarder on 2005-05-22
[QUOTE=wbeck85]I FIGURED IT OUT!!!

This has been bothering me too since I installed Kubuntu several weeks ago. THis afternoon, I finally found a package that solves this problem.
The problem is that Firefox is using GTK to render, or whatever. I know very little about this. But I do know that Gnome uses GTK and KDE uses QT for the most part. Please, someone correct me if I am wrong.
So, KDE is not rendering the GTK fonts correctly in Firefox ro any other gnome based app. the solution?

$ sudo apt-get install gtk2-engines-gtk-qt
(or install via synaptic/kynaptic/kpackage)

Once it is installed, go to settings:/LookNFeel/ in Konqueror. Click on the new icon that is there. It is the gnome footprint and says "GTK Styles and Fonts." Under GTK Styles, select "Use another style" and select "Qt." Under "GTK Fonts" Select "Use another font" and change it to whatever you want. I suppse you could leave the two choices at "Use my KDE..." but for some reason, that did not work for me.
Anyway, open up Firefox/thunderbird/synapitc/gaim and marvel at the beauty![/QUOTE]

Beauty indeed! With those packages installed Firefox often looks better in KDE than it does in GNOME.  Go figure....

---

### Post by ensenadaubuntulover on 2005-05-23
[QUOTE=angrykeyboarder]Beauty indeed! With those packages installed Firefox often looks better in KDE than it does in GNOME.  Go figure....[/QUOTE]

I did it in my laptop and worked beautifully now I want to repeat the action in my desktop and no can do  , what went wrong?
got lost somewhwre (no new icon found)

---

### Post by ensenadaubuntulover on 2005-05-23
found it (have to turn off the machine  ;-)  firdt (duh) and now it worked beautifully

---

### Post by dilmah on 2005-07-23
If you really want to make your Firefox look and behave more like KDE as well (including reversing the buttons on dialogs so that they're not "backwards") have a look at this theme for Firefox:

[http://www.polinux.upv.es/mozilla/plastikfox/releases/crystalsvg/plastikfox-crystalsvg/install.html](http://www.polinux.upv.es/mozilla/plastikfox/releases/crystalsvg/plastikfox-crystalsvg/install.html)

If you previously had the cutemenus extension installed, ensure you disable or uninstall it as this replaces it.
Unfortunately it doesn't replace the open/save dialogs. Can't have everything I guess.. :)

Regards,
A recently converted kUbuntu fan

---

### Post by dinges on 2005-07-24
Thanks, wbeck85. This one has been bugging me for days. Dou you know what stylesheet Human used under gnome? Then the sites would display a lot better I think.

---

### Post by muzzie on 2005-09-04
I'm having this problem with FF too, but I can't seem to be able to locate the "gtk2-engines-gtk-qt" package.  Checked apt-get.org also, and no luck there.  
Maybe I'm just stupid? :P

---

### Post by muzzie on 2005-09-04
Nevermind, I got it.  Just had to allow the "universe" repository in my apt sources.list .
The fix worked wonderfully! Thanks, wbeck.

---

### Post by Thulemanden on 2005-09-13
Good work. The instruction was very useful. :-P

---

### Post by hil on 2005-11-16
I followed the instructions to change the "GTK style and fonts" in konqueoro with "settings:/LookNFeel/" but the "GTK style and fonts" window did not show up. I had to go to kcontrol first and use the search with keyword "gtk" to locate "GTK style and fonts". In my "GTK style and fonts" window=>use another style, I have "Raleigh" instead of "QT" in "GTK style" section. I chose that. I clicked on "user another font" in "GTK Fonts" section to select the Chinese font I want. It worked very well. I can start Firefox or Gaim with better fonts. Thanks you all.

---

### Post by ozorba on 2005-11-17
[QUOTE=wbeck85]I FIGURED IT OUT!!!

This has been bothering me too since I installed Kubuntu several weeks ago. THis afternoon, I finally found a package that solves this problem.
The problem is that Firefox is using GTK to render, or whatever. I know very little about this. But I do know that Gnome uses GTK and KDE uses QT for the most part. Please, someone correct me if I am wrong.
So, KDE is not rendering the GTK fonts correctly in Firefox ro any other gnome based app. the solution?

$ sudo apt-get install gtk2-engines-gtk-qt
(or install via synaptic/kynaptic/kpackage)

Once it is installed, go to settings:/LookNFeel/ in Konqueror. Click on the new icon that is there. It is the gnome footprint and says "GTK Styles and Fonts." Under GTK Styles, select "Use another style" and select "Qt."  Under "GTK Fonts" Select "Use another font" and change it to whatever you want. I suppse you could leave the two choices at "Use my KDE..." but for some reason, that did not work for me.
Anyway, open up Firefox/thunderbird/synapitc/gaim and marvel at the beauty![/QUOTE]

After you select "Qt" Theme, your GNOME settings get messed up. However, if you select "Human" you do not see this problem with GNOME. 

Watch out!

---

### Post by bennettg on 2006-01-08
cool

---

### Post by mayo on 2006-01-09
Just upgraded to Firefox 1.5 and this fix is not working anymore :|

---

### Post by bennettg on 2006-01-16
it doesnt work for me in ff 1.5 either.  can someone help????

---

### Post by greatshape on 2006-01-30
[QUOTE=bennettg]it doesnt work for me in ff 1.5 either.  can someone help????[/QUOTE]

Yes i can :-)

1.Install these packages:
```

gtk2-engines-clearlooks - Clearlooks GTK+ 2.x engine and theme
gtk-clearlooks-gperfection2-theme - gtk theme for the clearlooks engine
kde-style-klearlook - The Klearlook widget style for KDE

```

2.Go to system settings, appearance, gtk styles and fonts.
3.Mark "use another style" and choose "clearlooks-gperfection2"
4.Hit apply

You're done!!! Restart firefox and marvell at the beauty again ;-)

Regards,
Steve

---

### Post by nimonika on 2006-02-09
Hi,

I tried your suggestion with 5.10, however in my case, the GTK icon hangs up indefinitely and does not work even on rebooting the machine. What could be wrong?

Thanks
[QUOTE=wbeck85]I FIGURED IT OUT!!!

This has been bothering me too since I installed Kubuntu several weeks ago. THis afternoon, I finally found a package that solves this problem.
The problem is that Firefox is using GTK to render, or whatever. I know very little about this. But I do know that Gnome uses GTK and KDE uses QT for the most part. Please, someone correct me if I am wrong.
So, KDE is not rendering the GTK fonts correctly in Firefox ro any other gnome based app. the solution?

$ sudo apt-get install gtk2-engines-gtk-qt
(or install via synaptic/kynaptic/kpackage)

Once it is installed, go to settings:/LookNFeel/ in Konqueror. Click on the new icon that is there. It is the gnome footprint and says "GTK Styles and Fonts." Under GTK Styles, select "Use another style" and select "Qt."  Under "GTK Fonts" Select "Use another font" and change it to whatever you want. I suppse you could leave the two choices at "Use my KDE..." but for some reason, that did not work for me.
Anyway, open up Firefox/thunderbird/synapitc/gaim and marvel at the beauty![/QUOTE]

---

### Post by pcalvert on 2006-06-23
Here's a simple, alternative approach:

1. Make sure that you are connected to the Internet.

2.  Open Konsole or your favorite terminal program if it's not already open.

3. Type this at the command prompt:

sudo aptitude install msttcorefonts

(*or*  sudo apt-get install msttcorefonts)

4.  Press the ENTER key.

This will download and install some Microsoft TrueType fonts.

Note:  You may have to close Firefox and then re-open it in order to see a difference.  I noticed a difference as soon as I opened a new window.
:)

Phil

---

