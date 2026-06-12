---
title: "Strange problem..."
date: 2008-11-30
forum: Desktop Environments
---

### Post by hatman on 2008-11-30
A really strange problem, on some applications/browsers there is text missing, for example on firefox everything is ok:-
[IMG]http://img.photobucket.com/albums/v298/thebaldingone/Screenshot-DesktopEnvironments-Page.png[/IMG]

But in opera the text is missing:-
[IMG]http://img.photobucket.com/albums/v298/thebaldingone/Screenshot-1-1.png[/IMG]

The data is also missing in ManDVD when telling the program which directory to use when saving data:-
[IMG]http://img.photobucket.com/albums/v298/thebaldingone/Screenshot-Choisissezledossierdedes.png[/IMG]

It's also the same in Openoffice and a couple of other apps, but in some it's ok...

I'm totally lost and it's beginning to drive me round the bend now, especially seeing as I have to struggle to remember which is which and what is what on the by now invisible toolbars... 

Any ideas?

Ta...

---

### Post by lian1238 on 2008-11-30
It could be white text on white background. Try going to Theme->Customize->Colors changing the colors around. From the whites to.. maybe red, to see which one it is.

To get to Theme..

[LIST]
[*]Right-click desktop, Change background, Theme
[/LIST]
or

[LIST]
[*]System->Preferences->Appearance
[/LIST]

---

### Post by Keyper7 on 2008-11-30
The screenshots with problems seem to be from programs that use Qt. It might be than some important Qt module is not installed.

Open those from the terminal and see if some error message is printed.

PS: it might take an entire day to check your reply to this, but I will

---

### Post by binbash on 2008-11-30
I guess you are using nvidia card.This is an issue with nvidia cards, try installing latest nvidia drivers (maybe beta) to fix this solution.I saw ppl got it fixed via doing this.

---

### Post by hatman on 2008-12-01
Yeah, I'm using the nVidia drivers...  I'll try the Qt thingy first before I mess with the nVidia drivers... 

cheers

---

### Post by meatball on 2008-12-09
Has anybody gotten this fixed? As I too am having this very same problem. Also using nVidia drivers...Screenshot included

---

### Post by meatball on 2008-12-09
Ok, found the solution (for me anyway). Seems it's an issue with the NV legacy drivers, particularly 96.43.09 which are included in the ibex repo's.

Gedit your /etc/X11/xorg.conf 

In the Section "Device" add line

Option "RenderAccel" "0"

Haven't been able to tell yet whether this causes a performance hit or not but it took care of the issue of this thread.

---

