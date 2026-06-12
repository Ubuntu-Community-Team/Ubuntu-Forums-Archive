---
title: "Openoffic 2.0 frustration"
date: 2006-01-03
forum: General Help
---

### Post by sunny_nwho on 2006-01-03
I recently installed OOo2.0 to my experience it is a worts thing to install.....I agree it has good features but I cannot edit any word documents that has graphics....the graphics sometimes have no colors and frquently crashes whihc i load documents with pictures.....i dont know why this is happening....i am the only one in my faculty using linux or ubuntu and i alone use openoffice....but i cannot edit my friens files....even though i give them in the doc format from OOo2 it does not open properly in Word....it is very frustrating....I will be very grateful if anyone can give me a solution

---

### Post by Aphorism on 2006-01-03
What architecture are you running?

What version of Ubuntu are you running?

Specifically, with examples, what happens?

Your question is too wrought with panic to really lend any help to.  There are hundreds of people who can help you immediately on this forum, but you need to try to be as specific as possible.

The problem really lies that your 'friends' are using closed source applications to develop their documents.  Try using OpenOffice and saving in a native format.  You will find that it works quite effeciently.

---

### Post by DarkW0lf on 2006-01-03
Yes it may be related to the linux distro, as the windows version works quite well and easily ports with Ms office.

Try updating the packages if you can. Ubuntu 5.10 ships with 2.0 RC2 and the most recent version is 2.0.1 (as in final). They may have fixed whatever your issue is.

Also make sure in your options that you set it to open and save MS documents.
The windows installer will ask you if you want to open and save those documents, I don't know how ubuntu sets it.

Tools | Options | Load/Save

There are four options for MathType, WinWord, Excel and PowerPoint.
Winword is the doc format your are talking about.
Altough I think Winword goes back to the 3.1 days of windows.
Nope it's called that in both version (?why, nevermind don't answer).

I'd check your settings then update if that doesn't work.

---

### Post by sunny_nwho on 2006-01-04
thank u for the replies....the problem i face is specifically with word files...but when i save and use odt for my personal use i can get them working without a hitch.....

---

### Post by DarkW0lf on 2006-01-11
If you still have a need to work with MS formats I would check your settings you shouldn't have any problems.

Good that you can create documents now.
OpenOffice is compatible with alot of formats, the only one I know of that has problems is MS Works Database. I once tried converting it and had no end of problems, otherwise it can work with a lot.

---

### Post by dcstar on 2006-01-12
[QUOTE=DarkW0lf]Yes it may be related to the linux distro, as the windows version works quite well and easily ports with Ms office.

Try updating the packages if you can. Ubuntu 5.10 ships with 2.0 RC2 and the most recent version is 2.0.1 (as in final). They may have fixed whatever your issue is.
.......[/QUOTE]
OO 2.0.1 for Breezy is available at this repository:

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

Add the line to the end of your /etc/apt/sources.list file, and use Synaptic to upgrade.

---

### Post by sunny_nwho on 2006-01-14
this is great repo dcstar it updates OOO to 2.0.1 gr8 man thank u

---

