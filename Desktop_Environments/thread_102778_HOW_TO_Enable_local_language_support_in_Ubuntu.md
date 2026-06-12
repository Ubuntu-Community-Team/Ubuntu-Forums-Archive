---
title: "HOW TO: Enable local language support in Ubuntu"
date: 2005-12-12
forum: Desktop Environments
---

### Post by anil_robo on 2005-12-12
Hi all! I was aware that many people want Ubuntu in their own native language. Fortunately, Ubuntu was designed to be available in all the popular languages, so that even non-english speakers can use computers with ease. Many people were busy translating Ubuntu in their native languages, and that the translation system is online at launchpad.net.

I thought of seeing Ubuntu in my native language, Hindi, and was able to do that in about 6 minutes. Here's the shot:

[IMG]http://img221.imageshack.us/img221/2069/hindi0xu.jpg[/IMG]

** If you want to use Ubuntu in your native language other than English (default), follow these directions:**

1. First, we'll install the language pack from official repository. 
    System--> Administration--> Language selector.
    It may ask you to install other languages, click "remind me again" at this time.

2. Now you shall see all the supported languages listed. There should be two check marks against most of them. The first one enables Ubuntu system and program menus in your native language ("tranlsations"). The second menu enables a dictionary in your native language - useful when you're typing in openoffice.org etc. using your native language. I recommend you check both of these checkmarks. This should install the language from the official repositories.

3. Now that the languages are installed, you should select your native language as "default language" from the same "language selector" (System--> Administration--> Language selector)

4. Click Apply, and close the window.

5. Go to System--> Preferences--> Fonts. Make sure you have the following font combination:
Application font: Bitstream vera sans Roman
Desktop font: Bitstream vera sans Roman
Window title font: Bitstream vera sans Bold

5. Logout

6. You'll come to the login (GDM) screen again. Here, enter the options and choose the language as "Hindi". Enter username and password, and you'll be taken to Ubuntu desktop.

7. Done! You should see almost everything in your native language.

If there are some apps/menus not in your native language, or the translation is not correct, you can always contribute to translation. Most programs allow you to contribute to translation officially : right click, and select "translate this application" if available!

All set and done! Enjoy the attachment to your roots! :)

** Notes:**

1. If you make a new untitled file at your desktop, it's name would be in your native language. And it'll remain exactlly the same even if you change the system language later! Each file has its own language tags, it appears.

2. Hindi (and possibly other CTL languages like Thai) may have problems with display - I had to increase font size to 16 to see clean readable text.

3. The language development in Ubuntu needs assistance. Please contribute to translation if you can spare the time.

4. If you want to type in Hindi characters, you have to choose keyboard layout as "India". To do that, go to System-->Preferences-->Keyboard and go to the layout tab. There, click ADD and select India from the country list. Don't expand the list - Hindi is not listed there. If you select India everything should be fine. Now make this layout default by activating the checkmark in front of its name in the layout tab. Close this screen. Try typing a text document in gedit and you'll see that now you can type in Hindi too!

5. In order to quickly switch between different keyboard laybouts, you can make a button in the panel. To do this, right click in panel --> Add to panel--> Keyboard Indicator. Double click on "keyboard indicator" icon to add it to panel. Whenever you want to change the keyboard layout, click it in the panel and it will change automatically!

---

### Post by anil_robo on 2005-12-22
Edited the how-to to add the following:
1. Language selection at login
2. How to type in Hindi

Let me know how many people tried this how-to and got it working. I'd really appreciate it! :)

---

### Post by anil_robo on 2005-12-22
Here's a screenie as a proof of being able to type in openoffice.org in Hindi:


[IMG]http://img358.imageshack.us/img358/7599/hindiinput9fl.png[/IMG]

---

### Post by chintan_agarwal on 2006-01-24
I tried to type in Hindi using Lohit Hindi Font in Open Office 2 but am not able to. The text still comes in English. Could you kindly guide me.
Thanks.

---

### Post by taygan on 2006-02-02
Special characters can be typed by crtl+shift+unicode  for example ctrl+shift+e7 gives you a ç.  applications>accessories>character map will tell you the codes.

enjoy!

---

### Post by ganatronic on 2006-02-03
I'm trying to learn the Esperanto, and I thought it would be fun to have my ubuntu translated into it.

I'm following your instructions so that this login will default to Esperanto, but I'm having an issue. After I check off and install Esperanto in the Language Selector, I'm not given the option to pick it as the default language. I double-checked Synaptics, and the packages are installed, and I've logged in and out, but still, my only options for the default language are English and English variants.

Any idea why Esperanto isn't showing up in the language selector?

---

### Post by chintan_agarwal on 2006-02-07
Thanks for the help. I solved my problem by clicknig the two alt buttons simultaneously to change  to the hindi keyboard. However, the problem is  that I am not too sure about what key generates what character. Anywhere I can find this out?

---

### Post by chintan_agarwal on 2006-02-10
I would also like to know how to install a TTF font for hindi that I had. In Windows we did it using control panel->fonts->install fonts. Any such facility in Linux?

---

### Post by rajneesh on 2006-02-10
i am new to linux and ubuntu
i added indian (gurmukhi) keyboard layout. but how can switch between different layouts while writing. it was very easy in windows. i am having hard time just to find this out. there seems to be no icon for switching between layouts. any help?

---

### Post by anil_robo on 2006-02-27
[quote=chintan_agarwal]I tried to type in Hindi using Lohit Hindi Font in Open Office 2 but am not able to. The text still comes in English. Could you kindly guide me.
Thanks.[/quote]

You need to choose Hindi language settings rather than just select a Hindi font. Do that from System--> Administration--> Languages as I have posted above. Then you shall be able to type in Hindi. Also the filenames will be created in Hindi - and they won't change even if you later change to English, or even move your file to a different Ubuntu computer! :)

---

### Post by chintan_agarwal on 2006-02-28
I do not have the following option System--->Administration--->Languages. Is there any other way to access the option?
Thanks.

[QUOTE=anil_robo]You need to choose Hindi language settings rather than just select a Hindi font. Do that from System--> Administration--> Languages as I have posted above. Then you shall be able to type in Hindi. Also the filenames will be created in Hindi - and they won't change even if you later change to English, or even move your file to a different Ubuntu computer! :)[/QUOTE]

---

### Post by chintan_agarwal on 2006-02-28
[QUOTE=rajneesh]i am new to linux and ubuntu
i added indian (gurmukhi) keyboard layout. but how can switch between different layouts while writing. it was very easy in windows. i am having hard time just to find this out. there seems to be no icon for switching between layouts. any help?[/QUOTE]
System-->Preferences-->Keyboard-->Layout Options-->Group Shift/Lock Behavior
Here there will be an option that is checked. This is the combination of keys that'll enable you to shift between layout. Hope this helps.

---

### Post by anil_robo on 2006-02-28
[quote=chintan_agarwal]I would also like to know how to install a TTF font for hindi that I had. In Windows we did it using control panel->fonts->install fonts. Any such facility in Linux?[/quote]

Put any .ttf font into /usr/share/fonts/truetype and they'll show up everywhere.

To do this, open a terminal and type this:
```
gksudo nautilus
```
it'll ask your password. Give password and hit OK.

Now you should be able to open the file browser in ROOT MODE. **Be careful.** Now you can copy and paste your font file to /usr/share/fonts/truetype.

By putting the font in this directory, all the users on the computer can use that font. You can download a sample font from [www.webdunia.com](www.webdunia.com) for testing purposes.

Do let me know if it helps.

---

### Post by anil_robo on 2006-03-02
[quote=chintan_agarwal]I do not have the following option System--->Administration--->Languages. Is there any other way to access the option?
Thanks.[/quote]

You may have uninstalled the language-selector package. Install it by:
```
sudo apt-get install language-selector
```

Then access this by System --> Administration --> Language Selector

[IMG]http://img317.imageshack.us/img317/1428/languageselector1wk.gif[/IMG]

Anil

---

### Post by chintan_agarwal on 2006-03-12
[QUOTE=anil_robo]You may have uninstalled the language-selector package. Install it by:
```
sudo apt-get install language-selector
```

Then access this by System --> Administration --> Language Selector

[IMG]http://img317.imageshack.us/img317/1428/languageselector1wk.gif[/IMG]

Anil[/QUOTE]

I tried :
sudo apt-get install language-selector

I don't understand why I get this. I tried to search the forum but there was no help available for this

E: Couldn't find package language-selector

I am positive that I did not uninstall any such facility and moreover, it is not available on Synaptic. Any suggestions? Probably, I should post this problem on some thread of the forum.
Thanks for your help.

---

### Post by chintan_agarwal on 2006-03-12
[QUOTE=anil_robo]Put any .ttf font into /usr/share/fonts/truetype and they'll show up everywhere.

To do this, open a terminal and type this:
```
gksudo nautilus
```
it'll ask your password. Give password and hit OK.

Now you should be able to open the file browser in ROOT MODE. **Be careful.** Now you can copy and paste your font file to /usr/share/fonts/truetype.

By putting the font in this directory, all the users on the computer can use that font. You can download a sample font from [www.webdunia.com](www.webdunia.com) for testing purposes.

Do let me know if it helps.[/QUOTE]


This worked perfectly. In fact I was able to type in Hindi even without changing any other setting. Is there any font(TTF) available which emulates typing as per the sound i.e. assigning key a for "akshar a of varnmala"? It would be wonderful.
Thanks

---

### Post by anil_robo on 2006-03-13
[quote=chintan_agarwal]This worked perfectly. In fact I was able to type in Hindi even without changing any other setting. Is there any font(TTF) available which emulates typing as per the sound i.e. assigning key a for "akshar a of varnmala"? It would be wonderful.
Thanks[/quote]

There is a phonetic keyboard layout extension for Firefox. You can download it from here:
[https://addons.mozilla.org/extensions/moreinfo.php?id=1575&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=1575&application=firefox)
(If the link is  dead, search for INDIC in firefox extensions page)

It enables you to type in any Indic language in Firefox phonetically. This is one of  the best tools I have found for Indic phonetic typing in Linux.

Regarding other applications (e.g. openoffice), I don't know if a phonetic typing is possible. I'll do some research on this in the coming few days and  let you know.

**Note: **I could not get this tool to type in Hindi in Ubuntu forums, but it works well for other websites. This has something to do with the javascript implemented to control font flow at Ubuntu forums.

---

### Post by anil_robo on 2006-03-13
&#2354;&#2375;&#2325;&#2367;&#2344; &#2313;&#2348;&#2370;&#2306;&#2335;&#2370; &#2360;&#2367;&#2360;&#2381;&#2335;&#2350; &#2325;&#2368;-&#2348;&#2379;&#2352;&#2381;&#2337; &#2360;&#2375; &#2361;&#2367;&#2306;&#2342;&#2368; &#2335;&#2366;&#2311;&#2346;&#2367;&#2306;&#2327; &#2310;&#2360;&#2366;&#2344;&#2368; &#2360;&#2375; &#2361;&#2379; &#2360;&#2325;&#2340;&#2368; &#2361;&#2376;.

---

### Post by anil_robo on 2006-03-13
[quote=chintan_agarwal]I tried :
sudo apt-get install language-selector

I don't understand why I get this. I tried to search the forum but there was no help available for this

E: Couldn't find package language-selector

I am positive that I did not uninstall any such facility and moreover, it is not available on Synaptic. Any suggestions? Probably, I should post this problem on some thread of the forum.
Thanks for your help.[/quote]

Or maybe the name  of the package was gnome-language-selector ?

---

### Post by chintan_agarwal on 2006-03-13
Yes, in the other threads, the name is suggested to be gnome-language-selector. However, even this does not exist in Synaptic and I'm getting the same error on the console.
Thanks.

---

### Post by anil_robo on 2006-03-14
Chintan, I wonder why can't you see the language selector in your System--> Administration menu. There are a few possibilities:
1. It may be there, but hidden. Use smeg (in breezy) or alacarte (in dapper) menu editor to see if it's there but disabled. If so, enable it.
2. You may have broken this package. Try this from terminal:
```
sudo apt-get install language-selector
``` 3. Check your repositories (use directions from here:[http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php"))
4. If you happen to have an Ubuntu Live CD, I strongly recommend you boot from it, and see if the language selector is there in the live cd.

Here is a screenshot from my synaptic in Dapper:

[IMG]http://img51.imageshack.us/img51/65/languageselector8eg.gif[/IMG]

Please post the results here, and let's see what can we do.

&#2309;&#2344;&#2367;&#2354;

---

### Post by chintan_agarwal on 2006-03-15
sudo apt-get install language-selector
gives the following error:
E: Couldn't find package language-selector

Also if I booted from the live CD, there was no Language Selector option there. Even in Synaptic, it did not exist.

I'll try the other two options and post the effect.

Besides, I think that it would be appropriate to discuss this issue in the following thread.
[http://www.ubuntuforums.org/showthread.php?t=94131&highlight=language-selector](http://www.ubuntuforums.org/showthread.php?t=94131&highlight=language-selector)

Till then, of course I am learning my way to type in hindi(It's difficult as the key-letter relation has to be relearned). And there do exist fonts which map words phonetically to the keys(Bolnagri being one, [http://indlinux.org/wiki/index.php/BolNagri)](http://indlinux.org/wiki/index.php/BolNagri)). But I am not sure if documents typed in these fonts would be viewable on systems without these fonts installed.
Anyway, thanks for the trouble. It's wonderful learning experience.

&#2367;&#2330;&#2306;&#2340;&#2344;

SysConfig:Ubuntu 5.04, Dell inspiron1100.

---

### Post by midra on 2006-04-23
Hi there,

I just got my Ubuntu system running yesterday. Now, I find this being the biggest problem, I read & write 3 different languages, and often chat with people that use all these 3 different languages at the same time. I need to go and switch a language when moving from different chat screen to another. In Windows I was able to do that in a fly, but how to do that in Ubuntu? 
](*,) 

I get the impression this thread that you need to relogin every time you want to change language, surely it cannot be so?

I touch type fast so I cannot just re-learn this because of the keyboard/locale/language settings are off, that would totally mess my touch typing.

---

### Post by chintan_agarwal on 2006-04-23
System-->Preferences-->Keyboard-->Layout Options-->Group Shift/Lock Behavior
Here there will be an option that is checked. This is the combination of keys that'll enable you to shift between layout. So to shift between languages, you would just have to press this combination of keys. Hope that answers your question

---

### Post by anil_robo on 2006-04-24
[quote=midra]Hi there,

I just got my Ubuntu system running yesterday. Now, I find this being the biggest problem, I read & write 3 different languages, and often chat with people that use all these 3 different languages at the same time. I need to go and switch a language when moving from different chat screen to another. In Windows I was able to do that in a fly, but how to do that in Ubuntu? 
](*,) 

I get the impression this thread that you need to relogin every time you want to change language, surely it cannot be so?

I touch type fast so I cannot just re-learn this because of the keyboard/locale/language settings are off, that would totally mess my touch typing.[/quote]

Right click on an empty area of the panel. Choose "add to panel".
Double click on "keyboard indicator"
You will see the keyboard indicator now sitting in the panel.
You can change the language you're using by clicking on this. Interestingly, it doesn't tell which language are you using, but changes the keyboard layout according to the country.
You can cycle between keyboard layouts only for the languages that you have installed in your system.

For example, I frequently switch between English (USA) and Hindi (India) using this little utility - single click does the job!!! :)

---

### Post by bluenova on 2006-05-04
Hi there,

Does any one if I can install a language offline? I have a computer that is not on the internet or a network, so cd-rom and floppy only, which I need to install the full Dutch language onto. The default language on the ubuntu disk is incomplete and it asks to connect to the internet to complete it.:(

---

### Post by anil_robo on 2006-05-04
[quote=bluenova]Hi there,

Does any one if I can install a language offline? I have a computer that is not on the internet or a network, so cd-rom and floppy only, which I need to install the full Dutch language onto. The default language on the ubuntu disk is incomplete and it asks to connect to the internet to complete it.:([/quote]

You can open synaptic and search for the word "dutch" and then right click the found packages, and see their properties. It'll tell you which files you need. Then you can download those files from official repos, and transfer them to the other computer via CD or USB.

The dutch language pack should be a single file, but even if you find many, just download all of them and fit them in a CD. One of them has got to work! I'm saying this because not only for GNOME, but you'll also need the language pack for openoffice.org (which comes in a package different from GNOME language pack) I think.

Anil

---

### Post by bluenova on 2006-05-05
Thanks Anil,

I'll give it a go tonight.

---

### Post by Arjunanda on 2006-09-10
I have set up my system nicely and I can produce devavagari for most part without difficulty. However, when I try to produce certain conjuncts in OpenOffice, I am facing a problem. For instance in "rbhava" when typing the last glyph "va", it breaks the previous "rbha" and prints on top of it.

For instance:
Sarve&#7779;&#257;&#7745; &#346;&#257;ntir Bhavatu 
&#2360;&#2352;&#2381;&#2357;&#2375;&#2359;&#2366;&#2306; &#2360;&#2381;&#2357;&#2360;&#2381;&#2340;&#2367; &#2349;&#2357;&#2340;&#2369; &#2404; &#2360;&#2352;&#2381;&#2357;&#2375;&#2359;&#2366;&#2306; &#2358;&#2366;&#2344;&#2381;&#2340;&#2367;&#2352;&#2381;&#2349;&#2357;&#2340;&#2369; &#2404;
appears correctly in my browser and in gedit, but the glyph gets broken in OpenOffice. Do you have any idea how to solve this?

---

### Post by Arjunanda on 2006-09-10
I have set up my system nicely and I can produce devavagari for most part without difficulty. However, when I try to produce certain conjuncts in OpenOffice, I am facing a problem. For instance in "rbhava" when typing the last glyph "va", it breaks the previous "rbha" and prints on top of it.

For instance:
Sarve&#7779;&#257;&#7745; &#346;&#257;ntirbhavatu 
&#2360;&#2352;&#2381;&#2357;&#2375;&#2359;&#2366;&#2306; &#2360;&#2381;&#2357;&#2360;&#2381;&#2340;&#2367; &#2349;&#2357;&#2340;&#2369; &#2404; &#2360;&#2352;&#2381;&#2357;&#2375;&#2359;&#2366;&#2306; &#2358;&#2366;&#2344;&#2381;&#2340;&#2367;&#2352;&#2381;&#2349;&#2357;&#2340;&#2369; &#2404;
appears correctly in my browser and in gedit, but the glyph gets broken in OpenOffice. Do you have any idea how to solve this?

---

### Post by Arjunanda on 2006-09-10
When you have the keyboard indicator displayed in the panel, just right-click it to get the keyboard layout viewed, so you can locate the keys.

---

