---
title: "Keyboard (Language) Indicator"
date: 2007-08-05
forum: Desktop Environments
---

### Post by Ingla on 2007-08-05
Hello.

I'm an Ubuntu user (Feisty and Dapper), who briefly experimented with Xubuntu.

Although setting up a working keyboard changer on Xubuntu was a bit of a challenge, I did like the look of it. It was possible to display country flag icons instead of text to indicate the language keyboard in use. 

Does anyone know whether it's possible (and, if so, how) to accomplish that with Gnome?

Thanks.

---

### Post by joe.turion64x2 on 2007-08-05
It is quite possible. I do it all the time with my lappy.

Just right click in the panel to which you want to add the "Keyboard indicator", select "Add to panel" and within it there is the Keyboard indicator. Once launched it will display both the flag & layout name. Right click it and you will be able to get into its configuration (if you already set that in XFCE then doing it in GNOME should be straight forward).

Joe.

---

### Post by Ingla on 2007-08-06
Thanks for the reply.

I have always had the keyboard indicator on the panel. But that's where I lose you. It only shows text. 

Right clicked and looked around in Keyboard Preferences, but there's nothing there about flag icons, as far as I can see.

Can you clarify/elaborate where you see these options?

Thanks.

---

### Post by joe.turion64x2 on 2007-08-06
> **Ingla said:**
> Thanks for the reply.

I have always had the keyboard indicator on the panel. But that's where I lose you. It only shows text. 

Right clicked and looked around in Keyboard Preferences, but there's nothing there about flag icons, as far as I can see.

Can you clarify/elaborate where you see these options?

Thanks.
Upps, I think I made a mistake with that. I have just remembered that it is KDE who actually provides that option (flags).

It is possible however that some nice Gnome theme does that trick for you, or perhaps a Widget. I am not sure.

Joe.

---

### Post by Ingla on 2007-08-06
I think I may have found a way to do this, but Feisty doesn't have any flag icons. Do you have any on your system you might be able to share?

---

### Post by joe.turion64x2 on 2007-08-06
> **Ingla said:**
> I think I may have found a way to do this, but Feisty doesn't have any flag icons. Do you have any on your system you might be able to share?
I am afraid not. If you installed KDE too you might have some.

Joe.

---

### Post by Ingla on 2007-08-08
**PROBLEM SOLVED.** I have the Feisty Gnome keyboard indicator using flags. Just in case anyone else is interested, this is how it's done:

I found out about this (mostly) on a Russian language Ubuntu site at:
[http://www.nabble.com/%D0%A4%D0%BB%D0%B0%D0%B6%D0%BA%D0%B8-%D1%81%D1%82%D1%80%D0%B0%D0%BD-%D0%B2-%D0%BF%D0%B5%D1%80%D0%B5%D0%BA%D0%BB%D1%8E%D1%87%D0%B0%D1%82%D0%B5%D0%BB%D0%B5-%D1%80%D0%B0%D1%81%D0%BA%D0%BB%D0%B0%D0%B4%D0%BE%D0%BA-GNOME.-t3639724.html](http://www.nabble.com/%D0%A4%D0%BB%D0%B0%D0%B6%D0%BA%D0%B8-%D1%81%D1%82%D1%80%D0%B0%D0%BD-%D0%B2-%D0%BF%D0%B5%D1%80%D0%B5%D0%BA%D0%BB%D1%8E%D1%87%D0%B0%D1%82%D0%B5%D0%BB%D0%B5-%D1%80%D0%B0%D1%81%D0%BA%D0%BB%D0%B0%D0%B4%D0%BE%D0%BA-GNOME.-t3639724.html).

1**. If you haven't got a language indicator**, right click on a panel and select "Add to Panel", find "Keyboard Indicator" near the bottom of the pop up dialogue, highlight it and click "Add", then "Close".

2. When the indicator appears on the panel, right click it and choose "Keyboard Preferences". Select the "Layouts" tab and use the "Add" button to **choose your languages** (Gnome only allows four). Put a check by the languages you want as default. Close the dialogue. You should have a language indicator showing some not terribly esthetic text. Click on it to change languages.

3. **Now, you need flag images**. The above mentioned site links to two images, one for the US flag and one for the Russian. These are at: 

[http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1226](http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1226) - us.png
[http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1227](http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1227) - ru.png 

I don't need Russian, but since these folks had done the work, I downloaded the images to find out the proper sizes. The images are (width) 64 x (height) 43 pixels.

If you can't find suitable flags, going to Wikipedia and searching for a country name will bring you to a page which includes the country's flag. It can be downloaded by right-click>Save image as... I didn't take these myself, but someone told me he got some there. A brief look at their site didn't seem to reveal any legal problem downloading - especially since it's only for your own desktop. It's even OK for your web site (with acknowledgment of the source [see their page for details]).

These are much larger images than you need, so right click the image and select "Open with > the Gimp". When the image opens in the Gimp, right click it and select "Image>Scale Image". In the dialogue box, change the width to 64. The height should take care of itself and come out around 42-47 (as mentioned, theirs are 64x43). Hit the "Scale" button and close. 

Then, in the File menu, choose "Save as..." and, leaving the .png format, name the image according to the standard two letter country code, e.g., us.png, es.png, fr.png etc. (Use the country names as found in the keyboard indicator as in #2 above ... the system recognizes languages by those country names. So, for Spanish, you must use "es.png", not "Spanish.png" or "mx.png", etc... country names - not language names: "us", not "en" [you could use a Mexican flag as long as the image were named "es.png"]). Close the Gimp.

4. **Place your flag images in /usr/share/pixmaps or ~/.icons/flags **(I only tried the first). If cut and paste won't work because of permission issues, move them with the command line (example: sudo mv -i Desktop/cn.png /usr/share/pixmaps/cn.png).

5.** Go to Applications>System Tools>Configuration Editor**. It seems to ship with Feisty but was not visible in my menu. If that's the case with you, try System>Preferences>Main Menu to open the Menu Editor. Find Applications>System Tools and see if it's there just waiting for you to put a check mark by it (and do that). Then you should see it in the Applications menu. You can also open it from a terminal by typing " gconf-editor" (no quotes). As a last resort, you can install it from Synaptic or apt-get (gconf-editor, gconf2-common, and gconf2).

6.** After you have the Configuration Editor open,** go to Desktop>Gnome>Peripherals>Keyboard>Indicator and check the box on the right side that says showFlags. Close the editor and you should have flags instead of text in your keyboard indicator. (The Russian page cited above gives different instructions, but they seem to be for another keyboard indicator applet).

When I first did this, the flags appeared quite small. After a reboot, they came back in a better size (maybe refreshing the panel would have done that).

Also, at one point, my keyboards wouldn't switch. A reboot might have fixed that, but I was in the middle of a download, so I removed the indicator from the panel (AFTER removing all languages but one!). I then added the indicator back to the panel and put back the languages and it's been fine).

Hope this is of help to someone.

---

### Post by joe.turion64x2 on 2007-08-08
> **Ingla said:**
> **PROBLEM SOLVED.** I have the Feisty Gnome keyboard indicator using flags. Just in case anyone else is interested, this is how it's done:

I found out about this (mostly) on a Russian language Ubuntu site at:
[http://www.nabble.com/%D0%A4%D0%BB%D0%B0%D0%B6%D0%BA%D0%B8-%D1%81%D1%82%D1%80%D0%B0%D0%BD-%D0%B2-%D0%BF%D0%B5%D1%80%D0%B5%D0%BA%D0%BB%D1%8E%D1%87%D0%B0%D1%82%D0%B5%D0%BB%D0%B5-%D1%80%D0%B0%D1%81%D0%BA%D0%BB%D0%B0%D0%B4%D0%BE%D0%BA-GNOME.-t3639724.html](http://www.nabble.com/%D0%A4%D0%BB%D0%B0%D0%B6%D0%BA%D0%B8-%D1%81%D1%82%D1%80%D0%B0%D0%BD-%D0%B2-%D0%BF%D0%B5%D1%80%D0%B5%D0%BA%D0%BB%D1%8E%D1%87%D0%B0%D1%82%D0%B5%D0%BB%D0%B5-%D1%80%D0%B0%D1%81%D0%BA%D0%BB%D0%B0%D0%B4%D0%BE%D0%BA-GNOME.-t3639724.html).

1**. If you haven't got a language indicator**, right click on a panel and select "Add to Panel", find "Keyboard Indicator" near the bottom of the pop up dialogue, highlight it and click "Add", then "Close".

2. When the indicator appears on the panel, right click it and choose "Keyboard Preferences". Select the "Layouts" tab and use the "Add" button to **choose your languages** (Gnome only allows four). Put a check by the languages you want as default. Close the dialogue. You should have a language indicator showing some not terribly esthetic text. Click on it to change languages.

3. **Now, you need flag images**. The above mentioned site links to two images, one for the US flag and one for the Russian. These are at: 

[http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1226](http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1226) - us.png
[http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1227](http://forum.ubuntu.ru/index.php?action=dlattach;topic=6303.0;attach=1227) - ru.png 

I don't need Russian, but since these folks had done the work, I downloaded the images to find out the proper sizes. The images are (width) 64 x (height) 43 pixels.

If you can't find suitable flags, going to Wikipedia and searching for a country name will bring you to a page which includes the country's flag. It can be downloaded by right-click>Save image as... I didn't take these myself, but someone told me he got some there. A brief look at their site didn't seem to reveal any legal problem downloading - especially since it's only for your own desktop. It's even OK for your web site (with acknowledgment of the source [see their page for details]).

These are much larger images than you need, so right click the image and select "Open with > the Gimp". When the image opens in the Gimp, right click it and select "Image>Scale Image". In the dialogue box, change the width to 64. The height should take care of itself and come out around 42-47 (as mentioned, theirs are 64x43). Hit the "Scale" button and close. 

Then, in the File menu, choose "Save as..." and, leaving the .png format, name the image according to the standard two letter country code, e.g., us.png, es.png, fr.png etc. (Use the country names as found in the keyboard indicator as in #2 above ... the system recognizes languages by those country names. So, for Spanish, you must use "es.png", not "Spanish.png" or "mx.png", etc... country names - not language names: "us", not "en" [you could use a Mexican flag as long as the image were named "es.png"]). Close the Gimp.

4. **Place your flag images in /usr/share/pixmaps or ~/.icons/flags **(I only tried the first). If cut and paste won't work because of permission issues, move them with the command line (example: sudo mv -i Desktop/cn.png /usr/share/pixmaps/cn.png).

5.** Go to Applications>System Tools>Configuration Editor**. It seems to ship with Feisty but was not visible in my menu. If that's the case with you, try System>Preferences>Main Menu to open the Menu Editor. Find Applications>System Tools and see if it's there just waiting for you to put a check mark by it (and do that). Then you should see it in the Applications menu. You can also open it from a terminal by typing " gconf-editor" (no quotes). As a last resort, you can install it from Synaptic or apt-get (gconf-editor, gconf2-common, and gconf2).

6.** After you have the Configuration Editor open,** go to Desktop>Gnome>Peripherals>Keyboard>Indicator and check the box on the right side that says showFlags. Close the editor and you should have flags instead of text in your keyboard indicator. (The Russian page cited above gives different instructions, but they seem to be for another keyboard indicator applet).

When I first did this, the flags appeared quite small. After a reboot, they came back in a better size (maybe refreshing the panel would have done that).

Also, at one point, my keyboards wouldn't switch. A reboot might have fixed that, but I was in the middle of a download, so I removed the indicator from the panel (AFTER removing all languages but one!). I then added the indicator back to the panel and put back the languages and it's been fine).

Hope this is of help to someone.
Excellent, thanks for the hint.

Joe.

---

### Post by nanogeek on 2007-08-23
Great Post.
This is the sort of step by step guide that helps us green beans.
One problem though.
I got down to step 6 and where it says:
Desktop>Gnome>Peripherals>Keyboard>Indicator
There is no "Indicator" under Keyboard.
I am running Edgy.
Should I be looking elsewhere?

---

### Post by Ingla on 2007-08-23
Hi.

As mentioned, I wrote this for Feisty. I don't have Edgy running anywhere, so I can't check.

The Russian site used a different path in the Configuration Editor: 

 Apps->gswitchit->Applet->showFlags .

I don't seem to be running gswitchit (as far as I can see from Synaptic ... it isn't even listed). Maybe you have it. 

Other than that I don't know. I never really used Edgy. 

Maybe if you make a post some Edgy user could provide information on its keyboard applet. 

Good luck.

---

### Post by nanogeek on 2007-08-24
Thank you.
The alternate Configuration Editor selection did the trick!

---

### Post by noamr on 2007-08-26
> **Ingla said:**
> 
3. **Now, you need flag images**.

It's great, thanks a lot!

You actually don't need all this GIMP stuff. You can just download the SVG file from wikipedia and put it in /usr/share/pixmaps/flags/XX.svg

Have a good day,
Noam

---

### Post by Wolki on 2007-08-26
There was a flag pack for the keyboard indicator some time ago, but I can't seem to find it anymore :-/

If you're wondering why this is so difficult, there are political reasons. One of the developers gives a few explanatory links here: [http://community.livejournal.com/xkbconfig/982.html](http://community.livejournal.com/xkbconfig/982.html)

---

