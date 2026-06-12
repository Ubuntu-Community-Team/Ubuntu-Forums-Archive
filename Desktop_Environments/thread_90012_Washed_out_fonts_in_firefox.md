---
title: "Washed out fonts in firefox"
date: 2005-11-14
forum: Desktop Environments
---

### Post by Darrin on 2005-11-14
I noticed some of the text displayed in firefox seems a little washed out. For instance parts of the letter "k" and "r". Almost as though part of the letter is faded away. Im not sure where to go to mess with this. I see the fonts in firefox general preferences, but Im not sure what to change and what not to touch.

---

### Post by aysiu on 2005-11-14
Can you post a small screenshot of what this looks like?

---

### Post by Darrin on 2005-11-14
I attached a sample screen shot showing a couple letters.

---

### Post by aysiu on 2005-11-14
I'm not trying to be obtuse here... I honestly don't see what's wrong with the fonts.

---

### Post by Efwis on 2005-11-14
that is based on three things.[list]
[*]Screen Resolution
[*]font 
[*]graphic exceleration (ie 3d enabled or not, graphics card used)[/list]

unfortunately I'm stuck with a 800x600 screen res currently, my good monitor fried itself after 9 years of use. so i get the same issue. I changed the default font and it pretty much solved my problem.

---

### Post by varunus on 2005-11-14
I think the "washed out" you're referring to is the font antialiasing.  Try messing with the settings; go to System-Preferences-Font and try setting your font rendering to monochrome.  Does this make it look better?  Also, you could try using the Microsoft fonts if you don't like the linux ones (install the msttcorefonts package from synaptic, its in universe), or opening up the advanced section and tinkering with antialiasing a bit more.

---

### Post by Darrin on 2005-11-14
Thanks Ill play around with it a bit and see what I can do. Is it just me? Maybe thats how it should look :confused: Am I being too picky here?

---

### Post by olzak on 2005-11-15
I have this  washed out font effect after installing msttscore fonts. Especially with k and r font as Darren write. After removing msttcore fonts there is no problem with these fonts.

---

### Post by Darrin on 2005-11-15
[QUOTE=olzak]I have this  washed out font effect after installing msttscore fonts. Especially with k and r font as Darren write. After removing msttcore fonts there is no problem with these fonts.[/QUOTE]

Thats when I noticed also. After installing the msttscore fonts. I think Ill remove them. I installed them using automatix. Im assuming I can uninstall them in synaptic. Is this correct? Im at work right now so Im not able to check.

---

### Post by olzak on 2005-11-15
[QUOTE=Darrin]Thats when I noticed also. After installing the msttscore fonts. I think Ill remove them. I installed them using automatix. Im assuming I can uninstall them in synaptic. Is this correct? Im at work right now so Im not able to check.[/QUOTE]

I'm not familiar with Automatix, but I think You can use Synaptic uninstall ms fonts.
When I install debian packages (.deb file) with command
sudo dpkg -i package_file.deb
I can always remove them also using Synaptic.

Or You can uninstall msttcorefonts using command:
sudo dpkg -r msttcorefonts

---

### Post by Darrin on 2005-11-15
[QUOTE=olzak]I'm not familiar with Automatix, but I think You can use Synaptic uninstall ms fonts.
When I install debian packages (.deb file) with command
sudo dpkg -i package_file.deb
I can always remove them also using Synaptic.

Or You can uninstall msttcorefonts using command:
sudo dpkg -r msttcorefonts[/QUOTE]
 Thanks. Ill try that out when I get home.

---

### Post by Darrin on 2005-11-15
Yes, msttscore fonts is removable in Synaptic. Once I removed them the fonts look much better. :)

---

### Post by olzak on 2005-11-16
I found interesting thread about this 'k/x/r effect' of msttcorefonts on Firefox: [http://www.ubuntuforums.org/showthread.php?t=79793&highlight=msttcorefonts](http://www.ubuntuforums.org/showthread.php?t=79793&highlight=msttcorefonts)

I think I'll try these advices next.

---

### Post by linbetwin on 2005-11-16
[quote=Efwis]that is based on three things.[LIST]
[*]Screen Resolution
[*]font
[*]graphic exceleration (ie 3d enabled or not, graphics card used)[/LIST]
unfortunately I'm stuck with a 800x600 screen res currently, my good monitor fried itself after 9 years of use. so i get the same issue. I changed the default font and it pretty much solved my problem.[/quote]

How do I find out whether I have 3D acceleration enabled or not?

---

### Post by Darrin on 2005-11-16
[QUOTE=olzak]I found interesting thread about this 'k/x/r effect' of msttcorefonts on Firefox: [http://www.ubuntuforums.org/showthread.php?t=79793&highlight=msttcorefonts](http://www.ubuntuforums.org/showthread.php?t=79793&highlight=msttcorefonts)

I think I'll try these advices next.[/QUOTE]
That was a great link. Thanks

---

### Post by olzak on 2005-11-16
[QUOTE=linbetwin]How do I find out whether I have 3D acceleration enabled or not?[/QUOTE]

Open Gnome Terminal (or Konsole if using Kubuntu) and type: 'glxinfo | grep direct'
If You see 'direct rendering: Yes' , You have 3D acceleration.

---

### Post by calande on 2006-06-11
[QUOTE=Darrin]I attached a sample screen shot showing a couple letters.[/QUOTE]

I have the same problem. My fonts look like this screenshot in Firefox :-(

---

