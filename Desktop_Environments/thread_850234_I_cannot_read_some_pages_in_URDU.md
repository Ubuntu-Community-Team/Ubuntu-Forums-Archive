---
title: "I cannot read some pages in URDU"
date: 2008-07-05
forum: Desktop Environments
---

### Post by mirchichamu on 2008-07-05
I cannot read some pages in Urdu in Firefox although I installed the Urdu package. How can I correct that? There is urdu font download on the page but I cannot download that in UBUNTU.

---

### Post by jesuisbenjamin on 2008-08-08
The issue is font-related, what you need is:
[LIST=1]
[*]A font providing all symbols required
[*]Show Firefox what font to use.
[/LIST]

Let's start with the step 1:
[LIST]
[*]Download a nice Nastaleeq font which will provide full alphabet. Here is a nice one [http://www.crulp.org/Downloads/localization/fonts/NafeesNastaleeq/Nafees_Nastaleeq_v1.01.zip](http://www.crulp.org/Downloads/localization/fonts/NafeesNastaleeq/Nafees_Nastaleeq_v1.01.zip)
[*]Unzip the file and save the Nafees.ttf font on your desktop.
[*]Press alt-F2 and enter the following code (this will open nautilus in the right directory):

```
gksu nautilus /usr/share/fonts/truetype
```

Then create a new directory, name the directory whatever you like (choose a name that you remember if you ever need to backup your fonts personal fonts). Move the Nafees font into that directory and finally rebuild the font information files by pressing alt-F2, mark 'run in terminal' so you can see the progress and entering the following code:

```
sudo fc-cache -f -v
```
[/LIST]
*PS: for more information on how to install fonts please check: [https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d](https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d)*

Next you need to point this font to Firefox when opening an Urdu web page: 
[LIST]
[*]Open Firefox and browse to page: [http://www.bbc.co.uk/urdu/](http://www.bbc.co.uk/urdu/) (notice the missing characters which are replaced with boxes filled with digits)
[*]Then go to menu Edit and select Preferences, a box appears.
[*]Select the "content" tab and in "font and colors" click on "Advanced".
[*]Select Arabic in the drop down box "Fonts for:" and in the four boxes below chose respectively the fonts: Sans Serif, Nafees, Nafees, Nafees. 
[*]Additionally you can untick the box "Allow pages to chose their own etc." though note this may affect all pages for all languages.
[*]Click OK and watch your BBC page transform into proper Nastaleeq script!
[/LIST]

Enjoy reading!

---

### Post by jesuisbenjamin on 2008-08-09
Despite this work around, there is an issue fundamentally remaining:
The default font provided with Ubuntu for Urdu has missing characters, as the attached screenshot can show.
Urdu is the *lingua franca* of Pakistan and Northern India, the keyboard can be selected as *India>Urdu *or *Pakistan>Default*.

The questions are why are there missing character in the default font? Who is able to update the font so as to provide a care-free usage to Urdu speaking users?

Thanks

---

### Post by jesuisbenjamin on 2008-08-10
Anyone?

There seem to be a similar issue with Chinese [http://ubuntuforums.org/showthread.php?t=885681](http://ubuntuforums.org/showthread.php?t=885681)
Who is to be addressed? How can we troubleshoot? Missing letters are an important issue, even if this is an English-written forum, or isn't it?

---

### Post by mirchichamu on 2010-11-30
> **jesuisbenjamin said:**
> The issue is font-related, what you need is:
[LIST=1]
[*]A font providing all symbols required
[*]Show Firefox what font to use.
[/LIST]

Let's start with the step 1:
[LIST]
[*]Download a nice Nastaleeq font which will provide full alphabet. Here is a nice one [http://www.crulp.org/Downloads/localization/fonts/NafeesNastaleeq/Nafees_Nastaleeq_v1.01.zip](http://www.crulp.org/Downloads/localization/fonts/NafeesNastaleeq/Nafees_Nastaleeq_v1.01.zip)
[*]Unzip the file and save the Nafees.ttf font on your desktop.
[*]Press alt-F2 and enter the following code (this will open nautilus in the right directory):

```
gksu nautilus /usr/share/fonts/truetype
```

Then create a new directory, name the directory whatever you like (choose a name that you remember if you ever need to backup your fonts personal fonts). Move the Nafees font into that directory and finally rebuild the font information files by pressing alt-F2, mark 'run in terminal' so you can see the progress and entering the following code:

```
sudo fc-cache -f -v
```
[/LIST]
*PS: for more information on how to install fonts please check: [https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d](https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d)*

Next you need to point this font to Firefox when opening an Urdu web page: 
[LIST]
[*]Open Firefox and browse to page: [http://www.bbc.co.uk/urdu/](http://www.bbc.co.uk/urdu/) (notice the missing characters which are replaced with boxes filled with digits)
[*]Then go to menu Edit and select Preferences, a box appears.
[*]Select the "content" tab and in "font and colors" click on "Advanced".
[*]Select Arabic in the drop down box "Fonts for:" and in the four boxes below chose respectively the fonts: Sans Serif, Nafees, Nafees, Nafees. 
[*]Additionally you can untick the box "Allow pages to chose their own etc." though note this may affect all pages for all languages.
[*]Click OK and watch your BBC page transform into proper Nastaleeq script!
[/LIST]

Enjoy reading!

Thanks a lot. It solved my problem in firefox but chrome is still the same.

---

### Post by jesuisbenjamin on 2010-12-06
Hello,

Since then BBC adopted a new font which is working perfectly for Urdu on Firefox (better than Nafees). I am not sure it is even possible to change the font in Chrome, i couldn't find it when i tried (and i really disliked the program so i dropped it).

In any case, the font is called Urdu Nashk Asiatype. It is to be found [here]("http://www.bbc.co.uk/urdu/fontinstall/popupwin.shtml").

Good luck,
Benjamin

---

### Post by mirchichamu on 2010-12-20
> **jesuisbenjamin said:**
> Hello,

Since then BBC adopted a new font which is working perfectly for Urdu on Firefox (better than Nafees). I am not sure it is even possible to change the font in Chrome, i couldn't find it when i tried (and i really disliked the program so i dropped it).

In any case, the font is called Urdu Nashk Asiatype. It is to be found [here]("http://www.bbc.co.uk/urdu/fontinstall/popupwin.shtml").

Good luck,
Benjamin

Thanks bro although a bit late...rather a million thanks for being with me after a long time.
Actually firefox is displaying all pages correctly even BBC with a different font but readable..If you want to use the font of BBC which is asunaskh then you will have to tick that web pages to select its own font. Which will creat problem again. So I am happy with the way you suggested above.

Only chrome is a problem. The language and font selection for chrome is different from Firefox. So I didn't succeed in chrome..If you find any way for chrome then please let us know.
Again bundle of thanks.

---

### Post by hasanarbab on 2011-07-13
Assalamo Alaikum.

For people who are having problem in chrome; Click on settings icon on the left on address bar strip -> Select 'Preferences' -> in second division in opened settings page, you'll see a button 'Customize Fonts', click it -> another division will open with the title 'Fonts and Encoding'. Select 'Nafees' in first option named 'Standard Font'. Close Preferences tab.

This must solve your problem in Google Chrome....... but unfortunately, it still does not work on facebook. :confused:

---

### Post by khalidaziz on 2011-09-09
Hi,

Apologies for bringing up an old thread. Here's the issue I am facing:

While using Urdu, the letters in words connect to each other in ways different as compared to when they are used individually. For example:

[SIZE="4"]&#1605; + &#1740; + &#1606; = &#1605;&#1740;&#1606;[/SIZE]

Note that the letter [SIZE="4"]&#1722;[/SIZE] is supposed to connect in the same way as [SIZE="4"]&#1606;[/SIZE]. This means that if I were to type [SIZE="4"]&#1605; + &#1740; + &#1722;[/SIZE], I should get the same output as above, except without the dot in the last letter (the one on the far left).

However, what I get is the following: [SIZE="4"]&#1605;&#1740;&#1722;[/SIZE]. As you can see, the connection doesn't happen. This is also true for other letters. 

What is the root of the problem? I can tell it's not a browser issue, because I'm reproducing the same across different applications in Ubuntu, including gedit. HOWEVER the font is rendering fine in OpenOffice and LibreOffice.

---

### Post by jesuisbenjamin on 2011-09-12
It has to do with the font (LibreOffice automatically changes the font to one that supports Perso-Arabic scripts).

You can find many fonts here: [http://www.wazu.jp/gallery/Fonts_Urdu.html](http://www.wazu.jp/gallery/Fonts_Urdu.html)

As far a the browser go you should be bothered about reading Urdu. I recommend CNN's Urdu font for that (mentioned above in the thread). 

The font you may have to use while typing in the browser's content may depend on the content's font request. For instance, you'll be stuck with a crappy font in Facebook.

Typing in the search field etc. of the browser, should depend on your default system font.

---

### Post by khalidaziz on 2011-09-12
Hi!

Thanks for your response. :) After meddling about a bit in FireFox, I realized that if I force FireFox to use a specialized Urdu font, that works great for Urdu text, but my English text gets distorted (not significantly, but the fact that it appears differently from the rest of the system is jarring). 

Do you know how I could make FF auto-select the font based on the type of script? Would this way (if it exists) work on pages with mixed Urdu and English words, such as my post above?

Thanks once again!

---

### Post by jesuisbenjamin on 2011-09-19
Yes, go to Edit > Preferences.
In the **Font and Colors** section, click on button [Advanced ...] then specify in the drop-down list what type of script you want to specify a font for, choose Arabic (it's a universal category for Perso-Arabic script).
Choose your font, click [ OK ]and change your default font back to what you need, then [x Close] and you should have what you want.

This should work.

---

### Post by khalidaziz on 2011-09-22
Doesn't work. It's still appearing broken on my screen. I think the system is getting confused as to what font to apply.

---

### Post by jesuisbenjamin on 2011-09-26
Did you try the BBC Urdu font? It's the one that works best for me on Firefox.

---

