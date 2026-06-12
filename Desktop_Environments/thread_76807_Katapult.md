---
title: "Katapult ??"
date: 2005-10-15
forum: Desktop Environments
---

### Post by t2kburl on 2005-10-15
I think I have gotten the hang of using Adept now, so I'm looking to explore further ... What is katapult and how do you use it?

---

### Post by André on 2005-10-15
Hi Katapult is nice,

activate it by pressing "Alt + Space".

Then you enter the program names of apps in the start menus and you have nice access to it by pressing enter...

Sounds a bit wierd so just try:

1. "Alt + Space"

2. Something like "kmail"

3. enter

and see yourself.

Greetings
André

---

### Post by t2kburl on 2005-10-15
lol ... i typed in Firefox and it openned the Firefox Central page in Konqueror instead of openning the Firefox browser

---

### Post by Hobbsee on 2005-10-15
yes, it does bookmarks as well, which is good.

---

### Post by jeremy on 2005-10-16
[QUOTE=t2kburl]lol ... i typed in Firefox and it openned the Firefox Central page in Konqueror instead of openning the Firefox browser[/QUOTE]
You presumerably have Konq as your default browser for html.

---

### Post by N6546R on 2005-10-24
How do I add applications to Katapult?

Perry

---

### Post by ltmon on 2005-10-25
[QUOTE=N6546R]How do I add applications to Katapult?

Perry[/QUOTE]

I think it goes looking in the k-menu for applications.  If you add to the k-menu, then restart katapult you might have some luck.

L.

---

### Post by GoldBuggie on 2005-10-25
I also know that katapult takes the items in your homedirectory. I still wish I could find the config file for where it looks etc. Haven't found any good info about the subject.

---

### Post by pbrockway2 on 2005-10-27
Hi,

I was also wondering where Katapult goes looking for its shortcuts.
So I downloaded the source and had a look there.  As others have
mentioned it looks at the application menu and the home directory.
It doesn't seem to have its own configuration file.

However, it *does* look at mozilla (firefox etc) bookmarks which it
parses in a fairly simple minded way.  I opened up the file
~/.mozilla/firefox/uzmzormy.default/bookmarks.html
and added the following lines:

<!--
<A HREF="http://www.google.com/" x>qwerty</A>
-->

After a restart Katapult recognises "qwerty" and opens Google
in Konqueror, but Firefox ignores the added lines.  You can use 
other protocols (man:, smb: etc) to link to different resources.

I don't think this gives any real advantage over making a straightfoward
folder of bookmarks - but if you really want "Katapult specific" ones
you could try this.

Cheers,

Peter

---

### Post by GoldBuggie on 2005-10-27
If you want your bookmarks to open in firefox then goto
[CENTER]*Control Center->KDE Components->Component Chooser* 
[/CENTER]
 there you click on  [CENTER]*Web Browser*
[LEFT]and set 
[/LEFT]
 [/CENTER]
 [CENTER]*Open **http** and **https** URLs* 
[/CENTER]
 to 
[CENTER][I]in the following browser
[/I] [LEFT]Now in that field type
[CENTER]firefox
[LEFT]Congratulations! Firefox is now your default webbrowser and katapult will use it for its https links
[/LEFT]
 [/CENTER]
 [/LEFT]
 [/CENTER]

---

### Post by theToolman on 2005-10-31
Having seen the beauty of quicksilver on OSX I am excited that katapult is included.  It looks like the kubuntu team have picked up the source code as the original developer has ceased development.

My problem is that it seems to prefer folders in my home directory and bookmarks to applications on the K menu - meaning that the firefoxAlpha directory comes up instead of the real firefox, and if that isnt there it finds the mozilla firefox *bookmark* over the kmenu instance.

As its a app launcher I think that the k menu should have highest priority in the search and it doesnt seem to.  I might have to suggest this to the developers :D

Hey guys I found the new homepage: [https://developer.berlios.de/projects/kubuntupult/](https://developer.berlios.de/projects/kubuntupult/)

I'll post my ideas about the tool :D

---

### Post by tristure on 2005-10-31
Well, Alt-Space only activates the main window menu...

Yet Katapult is installed on my system. If I try to launch it from a konsole I get :


Ignored duplicate item: Konqueror
Ignored duplicate item: Konqueror
Ignored duplicate item: Konqueror
Ignored duplicate item: Gestionnaire de paquets Synaptic
Ignored duplicate item: Gestionnaire de paquets Synaptic
Ignored duplicate item: Konqueror
Ignored duplicate item: Kate
Ignored duplicate item: aKregator
Ignored duplicate item: KMail
Ignored duplicate item: amule
Ignored duplicate item: Kopete
Ignored duplicate item: Konqueror
Ignored duplicate item: KWifiManager
Ignored duplicate item: Audacity
Ignored duplicate item: gtick
Ignored duplicate item: KsCD
Ignored duplicate item: Kaffeine
Ignored duplicate item: KMix
Ignored duplicate item: KAudioCreator
Ignored duplicate item: XMMS
Ignored duplicate item: amaroK
Ignored duplicate item: KMenuEdit
Ignored duplicate item: Konqueror
Ignored duplicate item: KInfoCenter
Ignored duplicate item: k3b
Ignored duplicate item: Klipper
Ignored duplicate item: KNotes
Ignored duplicate item: Ark
Ignored duplicate item: Konsole
Ignored duplicate item: KMail
Ignored duplicate item: Outil de gestion de comptes
Ignored duplicate item: SPE (Stani's Python Editor)
Ignored duplicate item: KMines
Ignored duplicate item: KSnapShot
Ignored duplicate item: Gwenview
Ignored duplicate item: xCHM
Ignored duplicate item: digikam
Ignored duplicate item: KPDF
Ignored duplicate item: KGhostView
Ignored duplicate item: OpenOffice.org2 Math
Ignored duplicate item: Kontact
Ignored duplicate item: KPresenter
Ignored duplicate item: KChart
Ignored duplicate item: KWord
Ignored duplicate item: KOrganizer
Ignored duplicate item: OpenOffice.org2 Calc
Ignored duplicate item: OpenOffice.org2 Draw
Ignored duplicate item: OpenOffice.org2 Impress
Ignored duplicate item: OpenOffice.org2 Writer
Ignored duplicate item: Kivio
Ignored duplicate item: Kile
Ignored duplicate item: KFormula
Ignored duplicate item: KSpread
Ignored duplicate item: OpenOffice.org2 Base
Ignored duplicate item: Kugar
Ignored duplicate item: Konqueror


And that's it... So I still don't get what this program is about! :-)

---

### Post by f1dave on 2005-10-31
You don't launch it from your konsole. Take a look here, i hope i've explained it well enough:

[bah, scratch that, doesnt seem to want to work]

---

### Post by tristure on 2005-10-31
Your link doesn't work right now.
Alt-Space still gives me no result...

I changed the shortcut so as not to have the Alt-Space combination assigned to window menu, and I even reinstalled Katapult, but I still can not launch it.

It's a bit ironic that I can't even launch something which is supposed to, errr, lauch stuff...

---

### Post by Thorsten on 2005-11-02
[quote=tristure]
Alt-Space still gives me no result...

I changed the shortcut so as not to have the Alt-Space combination assigned to window menu, and I even reinstalled Katapult, but I still can not launch it.
[/quote] 
Starting katapult from the konsole works just fine for me:
```
katapult &
``` I do get the same message you posted earliert, but Alt-SPACE does bring up the katapult window.

Perhaps this didn't work for you earlier because you had the shortcut assigned to sth else.

Good luck,
Thorsten

---

