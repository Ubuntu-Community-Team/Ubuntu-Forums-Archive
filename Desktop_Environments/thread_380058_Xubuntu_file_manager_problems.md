---
title: "Xubuntu file manager problems"
date: 2007-03-09
forum: Desktop Environments
---

### Post by Ethelbert2 on 2007-03-09
[FONT="Georgia"][COLOR="DarkGreen"][SIZE="3"]I have Xubuntu 6.10. If I plug in a usb flash memory it appears on my desktop.
 
I can open it and [FONT="Fixedsys"]file manager[/FONT] appears showing every thing nicely inside it. I can navigate around inside [FONT="Fixedsys"]file manager[/FONT].

Now, I have an [FONT="Fixedsys"]OpenOffice[/FONT] file there, in the Flash Memory. Double clicking on it causes [FONT="Fixedsys"]Abiword[/FONT] to open, instead of [FONT="Fixedsys"]OpenOffice[/FONT]. But it does not open the .odt file - it just sits there as [FONT="Fixedsys"]Abiword[/FONT]. 

If I open [FONT="Fixedsys"]OpenOffice Writer[/FONT] and then click on the "open file" button inside I cannot find the file. It lists my home file but does not show the Flash Memory either directly or under "Desktop". It may as well not be there. 

So I cannot open this odt file that way.

Right clicking on the odt file in the flash mem when displayed in [FONT="Fixedsys"]file manager[/FONT] does help, under "open with" I choose [FONT="Fixedsys"]OpenOffice Writer[/FONT] and it brings up the file correctly in [FONT="Fixedsys"]Open Office[/FONT].

But I would like to just be able to double click on the file and have its native programme open it, or find it **withhin **an application, or see if [FONT="Fixedsys"]Abiword[/FONT] will do stuff with it.

Also, under the [FONT="Fixedsys"]kfce[/FONT] desktop, I cannot find [FONT="Fixedsys"]File Manager[/FONT] anyway, to open it directly. It will open if a flash mem icon is displayed and I click on it but otherwise - where is it?

Have I failed to configure something - or are there tricks to this?

Many thanks[/SIZE][/COLOR][/FONT]

---

### Post by jem7v on 2007-03-09
1. I believe that in Ubuntu Edgy the file manager is under Applications -> System -> Thunar File Manager, which is approximately the most obscure place they could put it.  In 6.06 and in 7.04 I think that File Manager is the 3rd or 4th item in the Applications menu, but when I used Xubuntu 6.10 the menu was... sorta weird.

2. Right-click on the file and choose Properties. There should be a drop-down box labeled Open With... That's where you can change what program is used to open that file type.  It'll apply to all the other other files of the same format too.  (You can do that for any type of file.)

---

### Post by Ethelbert2 on 2007-03-09
[COLOR="DarkGreen"][SIZE="3"][FONT="Georgia"]Many thanks for your answer - found Thunar - as you say not the most intuitive place to look. That's useful.

I can open a file with the context menu and choose the application.  But I am not sure how to set my preferred application **always** to open it. 

And  --- how do I find the usb and its list of  from **inside** OOo Writer - it simply does not show up - nor in Abiword. [/FONT][/SIZE][/COLOR]

---

### Post by jem7v on 2007-03-09
"I can open a file with the context menu and choose the application. But I am not sure how to set my preferred application always to open it. "

No, what I mean is:
1. Right-click to get the context menu.
2. Choose Properties.
3. There is a drop-down list in the Properties dialogue that lets you select your preferred application. That's what you need to use.


As for finding the USB drive from inside the programs? I'm not quite sure about that one, as I don't have a thumbdrive and haven't therefore tried to do that!

---

### Post by zubrug on 2007-03-09
You may have to copy the file to your home folder and then right click and select properties, check to see what the permissions are set at. good luck

---

