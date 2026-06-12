---
title: "Ubuntu language rendering issues"
date: 2005-12-05
forum: Desktop Environments
---

### Post by iwsfutcmd on 2005-12-05
Hi all.  I'm a (relatively) new Ubuntu user (but not terribly n00by) and a very new user to these forums (possibly a little n00by).  I switched from XP about 3 months ago, and while I had a few issues in the beginning, I'm smooth sailing now.  Except for one little thing.  I work a lot in other languages and I noticed some problems with the rendering of the Arabic script on the Gnome desktop.  Namely, the letters are in the right order, and in the right direction (right to left) but are unjoined.  In fact, it even seems like some of them are from different fonts from each other.  The wierd thing is that it doesn't always do this.  Sometimes, it renders as nice, joined up Arabic text, other times, its a mess.  (by the way, I thought it was really funny how on the installer for Ubuntu, the Arabic and Hebrew was all backwards and unjoined.  Somebody might wanna see to that).  Anybody else having this problem, or found a solution, or whatever?  If any of you guys might know what's going on but doesn't speak Arabic, you can test it like this.  Rename a file as the following text:

&#1605;&#1603;&#1578;&#1576;

and if it's all one solid line (with dots and lines coming off of it) its rendered right, but if its broken into different letters, like this:

&#1605; &#1603; &#1578; &#1576;

it's screwy.
Also, in a related problem, I have some files named in Amharic (from Ethiopia) using the Ethiopic alphabet.  They are rendered fine, but the desktop always chooses my ugliest font for Ethiopic text.  If I change the font to a nice looking Ethiopic font, my Latin (English) text gets all ugly (my good-looking Ethiopic font has ugly Latin characters).  Is there any way to specify that Latin gets one font, Arabic gets another, Hebrew gets another and Ethiopic gets another?

Thanks for your help

---

### Post by sethmahoney on 2005-12-06
Are you talking about the font rendering for the filename that appears under the icons on your desktop or in nautilus?  If so, I have the same problem with Cyrillic, and I can sympathize - they look BAD!  Unfortunately, I haven't found a solution yet.

---

### Post by iwsfutcmd on 2005-12-06
Yep, that's it.  Good to know it's not just me.  But at least with the Cyrillic or the Ethiopic, it's readable, just ugly.  With the Arabic, the letters don't join up as they should and so it's basically unreadable.

---

### Post by sethmahoney on 2005-12-12
I just decided that maybe its an issue with the font I was using, and hey, I was right!  Bitstream Vera Sans renders (Cyrillic, at least) much more nicely than the default Sans.  To get it working on your system:

Go to System->Preferences->Font in the menu bar.
Change the application and desktop fonts to Bitstream Vera Sans.
Change the Window title font to Bitstream Vera Sans bold.
Hit close.

The non-Latin (disclaimer: Or, at least, Cyrillic) fonts in Nautilus should look much nicer now.

---

### Post by sethmahoney on 2005-12-12
Update: Just tested it, and it works with Arabic, too!

---

### Post by anil_robo on 2005-12-12
I wanted to type a document in openoffice.org, in Hindi (which is a complex language to type - some CTL thingie). Despite using a Hindi font, and playing around with lots of settings in OO.o, I haven't been able to get it working. In the languages tab in OO.o, Hindi is not listed at all! How do I install Hindi language for openoffice.org?

Edit: Found the method... it's [here!]("http://www.ubuntuforums.org/showthread.php?t=102778")
:D

---

### Post by sethmahoney on 2005-12-13
[QUOTE=anil_robo]I wanted to type a document in openoffice.org, in Hindi (which is a complex language to type - some CRT thingie). Despite using a Hindi font, and playing around with lots of settings in OO.o, I haven't been able to get it working. In the languages tab in OO.o, Hindi is not listed at all!

How do I install Hindi language for openoffice.org?[/QUOTE]

As far as I know, spell checking in Hindi isn't supported in openoffice (the file you would install is myspell-hi, but its not in Synaptic).  Also, for some reason there are no OpenOffice2.0 files for Hindi localization.  But!  If you want to work with OpenOffice1.0, you just open up Synaptic and download the file openoffice.orgl10n-hi (and, of course, all the OpenOffice1.0 files).  Then, open up OpenOffice and go to Tools and then Options.  Click on Language Settings, and then Language (I'm guessing on this part - I use 2.0, but the settings should be similar).  Change "Default languages for documents" to Hindi, and you should be good to go.

---

### Post by anil_robo on 2005-12-13
[quote=sethmahoney]As far as I know, spell checking in Hindi isn't supported in openoffice (the file you would install is myspell-hi, but its not in Synaptic).[/quote] Spellcheck ***does*** exist for Hindi. I didn't go through Synaptic, but Im more of a "mouse-man" :D . I found it in SYstem-->Administration-->Language selector. I haven't tried it yet though.

---

### Post by sethmahoney on 2005-12-13
[QUOTE=anil_robo]Spellcheck ***does*** exist for Hindi. I didn't go through Synaptic, but Im more of a "mouse-man" :D . I found it in SYstem-->Administration-->Language selector. I haven't tried it yet though.[/QUOTE]

Oh, good news!  I started a howto covering multi-language issues, but for some reason it hasn't shown up yet.  If it ever does, I'll add a note about that!

---

### Post by anil_robo on 2005-12-22
Here's a screenie I took today to prove that I was typing in Hindi on Dell Inspiron 6000 (which has English keyboard) by selecting Hindi keyboard layout:

[IMG]http://img358.imageshack.us/img358/7599/hindiinput9fl.png[/IMG]

---

