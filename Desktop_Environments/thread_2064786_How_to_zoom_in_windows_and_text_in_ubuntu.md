---
title: "How to zoom in windows and text in ubuntu?"
date: 2012-09-30
forum: Desktop Environments
---

### Post by fafu on 2012-09-30
How to zoom in the windows and texts in ubuntu 12.04 ?
I have screen resolution  of1920X1080 , so all the windows and texts are very small.
In windows 7 you can zoom in Appearance tab of Control Panel to 125%, 150% etc..
Can someone please help me with this..

---

### Post by pompel9 on 2012-09-30
Open the system settings, in the bottom there is something called universal access (I think, my system language is not English). In there you can find things like text size (but not zoom).

---

### Post by fafu on 2012-09-30
> **pompel9 said:**
> Open the system settings, in the bottom there is something called universal access (I think, my system language is not English). In there you can find things like text size (but not zoom).


thanks...but even if you zoom in text in universal access...the text size of other programs doesn't increase...

---

### Post by grahammechanical on 2012-09-30
It all depends on the application that you are using. I am using at this moment the Chromium web browser. If I go to the View menu I see an option to Zoom In and an option to Zoom out.

If I load Libreoffice its View menu gives me an option to Zoom and from there I get a dialog where I can set the % of Zoom.

And then there is Firefox. It also has a Zoom option under its View menu.

Regards.

P.S. It is a mistake to expect any Linux distribution to copy the functions and features of other operating systems. Apple and Microsoft are likely to take legal action against organisations copying their copyrighted designs. But Linux has progressed beyond copying the looks or functions of other operating systems. Linux distributions like Ubuntu are now treading their own path.

---

### Post by NikTh on 2012-09-30
Hi , 
do you want bigger text ? Font ? 

Install gnome-tweak-tool and change the fonts from there. 

From terminal 

```
sudo apt-get install gnome-tweak-tool
``` 

Then search for "advanced settings" , select "fonts" and change them all to what you prefer.

---

### Post by fafu on 2012-09-30
> **NikTh said:**
> Hi , 
do you want bigger text ? Font ? 

Install gnome-tweak-tool and change the fonts from there. 

From terminal 

```
sudo apt-get install gnome-tweak-tool
``` 

Then search for "advanced settings" , select "fonts" and change them all to what you prefer.
But even the action buttons are small...is there any way to increase their size other than changing resolution...

---

### Post by NikTh on 2012-09-30
> **fafu said:**
> But even the action buttons are small...is there any way to increase their size other than changing resolution...


Yes , for Action buttons (if you mean window buttons) , you have right. 

Maybe if you change theme ? 

You can change themes with this same tool you installed. 

Download themes from here : [http://gnome-look.org/](http://gnome-look.org/)

Wait if someone has a better idea. 

Thanks

---

### Post by JKyleOKC on 2012-09-30
Somewhere in your settings dialogs you should find one for "dpi" which is "dots per inch." It usually defaults to a value of 96. If you increase it, the entire screen will be zoomed without changing the resolution. I'm currently running this machine with the value set to 103, to give me just a little bit of zooming which is easier on my aging eyes.

Here's how it works: your screen resolution is a fixed number of pixels. If you increase the DPI setting, each character will use a larger number of them to display and will thus appear larger.

In WinXP, where I first learned the trick, the system uses 96 as the default value but you can select "large type" in the screen property settings and it changes to 125. I suspect that all of the "zoom" settings in our applications make temporary changes in the DPI value that remain only when in that application -- but setting it in the system dialogs makes it apply almost everywhere.

It won't change the zoom for every increase. In my case, it stayed the same at 97, 98, and 99, then zoomed a bit at 100 and again at 103...

---

### Post by fafu on 2012-09-30
> **JKyleOKC said:**
> Somewhere in your settings dialogs you should find one for "dpi" which is "dots per inch." It usually defaults to a value of 96. If you increase it, the entire screen will be zoomed without changing the resolution. I'm currently running this machine with the value set to 103, to give me just a little bit of zooming which is easier on my aging eyes.

Here's how it works: your screen resolution is a fixed number of pixels. If you increase the DPI setting, each character will use a larger number of them to display and will thus appear larger.

In WinXP, where I first learned the trick, the system uses 96 as the default value but you can select "large type" in the screen property settings and it changes to 125. I suspect that all of the "zoom" settings in our applications make temporary changes in the DPI value that remain only when in that application -- but setting it in the system dialogs makes it apply almost everywhere.

It won't change the zoom for every increase. In my case, it stayed the same at 97, 98, and 99, then zoomed a bit at 100 and again at 103...


where can i change dpi ???
Could you please tell me, because i couldn't find it...

---

### Post by JKyleOKC on 2012-09-30
I found it in Settings Manager -> appearance -> fonts, but I'm using the Xubuntu variant of the system and its configuration tools are a bit different from those in the mainline Ubuntu version. Look through your system settings dialogs, concentrating on the "fonts" dialogs. You might also search the forums here for 'DPI" and see if there are other posts about it...

EDIT: I did the search and found lots of information, plus lots of threads where "dpi" was only an incidental part of a message. Some of it may help you, though. Much will depend on what kind of session you are using: Unity, Gnome Classic, KDE, or something else...

---

### Post by fafu on 2012-10-02
> **JKyleOKC said:**
> I found it in Settings Manager -> appearance -> fonts, but I'm using the Xubuntu variant of the system and its configuration tools are a bit different from those in the mainline Ubuntu version. Look through your system settings dialogs, concentrating on the "fonts" dialogs. You might also search the forums here for 'DPI" and see if there are other posts about it...

EDIT: I did the search and found lots of information, plus lots of threads where "dpi" was only an incidental part of a message. Some of it may help you, though. Much will depend on what kind of session you are using: Unity, Gnome Classic, KDE, or something else...

Thanks mate....but hard luck...there seems to be no way to change the DPI of everything in ubuntu...only thing you change is font size...

---

