---
title: "How to make &quot;euro currency sign&quot;, &quot;pound sterling sign&quot; and &quot;degree sign&quot;"
date: 2006-03-09
forum: Desktop Environments
---

### Post by JimS on 2006-03-09
...

I can make these sign when in MS enviroment,
but not in Linux environment.
Is there an easy way to make them in Linux?

JimS[COLOR="Blue"]
Prostate Cancer Aware
[/COLOR]
,,,

---

### Post by Sutekh on 2006-03-09
How did you make these symbols in Windows?

In Windows I make them with the Character Map.  

In Ubuntu I make them with the Character Map.  

Its in the Applications -> Accessories menu.

---

### Post by JimS on 2006-03-09
...

In MS Windows I make the 3 symbols as follows:
Euro ==> Alt 0128
Pound ==> Alt 0163 or Alt 156
Degree ==> Alt 0176 or Alt 248
I keep a little post-it on the wall as a reminder.

Character map seems ackward,
but I probably don't know how to use it correctly.

I may just keep a little text file with these charactors
and when I need one, I can copy and paste
 €  £  ° as I have done here.
But it is not an elegant way.
Little better than my post-it way.

What I had in mind is to assign 1 or more keystrokes
for each character; i.e., alt ctrl p for pounds sterling.
Could that be done at the OS level, and if so, how?

JimS[COLOR="Blue"]
Prostate Cancer Aware[/COLOR]

,,,

---

### Post by Sutekh on 2006-03-09
Okay first go to **View** and change to **By Unicode Block** then you can see to more common latin symbols and the ones you want.
[ATTACH]6885[/ATTACH]

One way to get the character over is to double click the charater so it goes in the 'Text to Copy' Area and then select it and use the middle-mouse button to paste.  You can use the middle mouse button to paste any selected text.  But this is pretty laborious.


Another way (and much easier) I just found is to add a **Character Palette** to a panel.  Right-click an panel add choose **Add to Panel**.  The Character Palete is down in Utilites.  
[ATTACH]6888[/ATTACH]

Once its on the panel you can choose the palete set by clicking the drop down arrow.  Choose the symbol you want and middle-click your mouse to paste it in.
[ATTACH]6884[/ATTACH]


The easiest way would to setup a shortcut like you do in Windows.  I don't know how to do that yet.


**Edit:** I do now.

Ctrl + Shift plus the hexadecimal code of the symbol (from the character map)

£ - Ctrl + Shift + A + 3
° - Ctrl + Shitf + B + 0
&#8364; - Ctrl + Shift + 2 + 0 + A + C

---

### Post by JimS on 2006-03-09
...
JimS
This looks like what I'm after.
I got to go, but when I get back
I'll give it a try.

Many thanks, Danke, tusan tak, arigato, etc.

[COLOR="Red"]JimS[/COLOR] :D 

,,,

---

### Post by JimS on 2006-03-10
...

From the menu:
#1. No.  I have to agree, number one is not for me.
#3. No.  It may be like I do in MS Windows, but I use
Ctrl + Shift to toggle keyboard languages.  I tried it,
but it won't do both.
So I will use #2.  It works.  It is easy.  It does take
up an inch of panel real estate and I have only one
skinny panel and one transparent weather gDesklet.

My monitor is 20" with 'Ferrari on the beach' wallpaper.
Can't put clutter in that scene.  NO NO NO

So many thanks to Sydney's Sutekh and others for
their help.  \\:D/ 

[COLOR="Red"]JimS[/COLOR][COLOR="Blue"]
Prostate Cancer Aware[/COLOR]

,,,

---

### Post by Sutekh on 2006-03-10
[QUOTE=JimS]
#3. No.  It may be like I do in MS Windows, but I use
Ctrl + Shift to toggle keyboard languages.  I tried it,
but it won't do both.[/QUOTE]I was afraid you'd say that, it was the one tiny flaw in the method!  Unless you can change the key bind for changing keyboards .... :-k 

[QUOTE=JimS]
So I will use #2.  It works.  It is easy.  It does take
up an inch of panel real estate and I have only one
skinny panel and one transparent weather gDesklet.

My monitor is 20" with 'Ferrari on the beach' wallpaper.
Can't put clutter in that scene.  NO NO NO[/QUOTE]Yeah I can see that you are really strapped for space!!  Sorry about that! ;)  Good Luck with it!

---

### Post by Icebear on 2006-03-10
I saw in the System>preferences>Keyboard

then click layout options

A spot where it say option about Euros don't know it works but I think it would be a good idea to check it out.

---

### Post by jarno on 2006-03-10
I can get those signs by pressing following key combinations:
euro &#8364;: alt gr + e
pound £: alt gr + 3
degree °: alt gr + shift + 0

There might be some differences between keymaps, I'm using fi-latin1.

--
    /jarno

---

### Post by Sutekh on 2006-03-10
[QUOTE=jarno]I can get those signs by pressing following key combinations:
euro &#8364;: alt gr + e
pound £: alt gr + 3
degree °: alt gr + shift + 0

--
    /jarno[/QUOTE]
I've seen that notation used before, but what does the 'gr' stand for?

---

### Post by jarno on 2006-03-10
[QUOTE=Sutekh]I've seen that notation used before, but what does the 'gr' stand for?[/QUOTE]

Alt gr stands for 'alternate graphic'. It is the next key to the right from space bar, but I'm not sure if it exists in US-keyboards. I've only used these scandinavian keyboards, with swedish/finnish layouts.

[http://en.wikipedia.org/wiki/AltGr]("http://en.wikipedia.org/wiki/AltGr")

-- 
    /jarno

---

### Post by JimS on 2006-03-11
...

jarno,

I couldn't find a AltGr key.JimS
I tried the examples in wikipedia,
both with my US keyboardJimS
and with it toggled to Danish.
NO GO,
but thanks for the added info.

I'll use the panel style.  It means
taking one hand off the keyboard
and operate the mouse --
which is wasted movement IMO.

MVH,
[COLOR="Red"]JimS[/COLOR]

,,,

---

### Post by rbarryza on 2006-05-09
I often type in Afrikaans, and often need ê,ë,ö,ô,ì,í,é, etc. The way I got it to work is:
1. System->Preferences->Keyboard.  
2. Click on the Layout Options Tab.  
3. Choose a Compose Key (Under Compose Key Position).  I chose "Right Ctrl is compose"
4. Close

Now you can type special characters using the compose key as follows:
For ê : Right Ctrl+Shift+6 (ie Right Ctrl+^) e (Press Right Ctrl,Shift and 6 at the same time, release and then press e)
ë,ö : Compose+" letter
é,ó,ì : Compose+' , letter (' is on the same key as " on a standard american keyboard, so just don't use the shift key)
è,ò,ì : Compose+` letter (` is to the left of 1 on my keyboard)

Those cover everything I need in Afrikaans, but I'm sure you can figure out the rest for another language.

---

### Post by mcduck on 2006-05-09
[QUOTE=JimS]...

jarno,

I couldn't find a AltGr key.JimS
I tried the examples in wikipedia,
both with my US keyboardJimS
and with it toggled to Danish.
NO GO,
but thanks for the added info.

I'll use the panel style.  It means
taking one hand off the keyboard
and operate the mouse --
which is wasted movement IMO.

MVH,
[COLOR="Red"]JimS[/COLOR]

,,,[/QUOTE]
You can use alt+ctrl instead of alt gr, so the keys would be alt+ctrl+5 (or alt+ctrl+e) for €, alt+ctrl+3 for £..

---

### Post by Edward The Bonobo on 2006-05-09
I'm using a standard UK keyboard.  I've never even noticed AltGr before...but there it is right in front of me!

That looks useful.  Is there a keyboard map somewhere which tells me how to type à, é, è, î. ö, ä, ü, ç, ß...etc when I type in French or German?  Or are the Gnome/KDE key bindings the same as for M*******t Office? (eg alt+shift+;/: , u for ü - und so weiter)?

(I'm not on a Linux machine to test at the moment)

---

### Post by bluenova on 2006-05-09
[QUOTE=jarno]I can get those signs by pressing following key combinations:
euro &#8364;: alt gr + e
pound £: alt gr + 3
degree °: alt gr + shift + 0

There might be some differences between keymaps, I'm using fi-latin1.

--
    /jarno[/QUOTE]
Ditto, With British English as the keyboard setup.

---

### Post by bluenova on 2006-05-09
[QUOTE=Edward The Bonobo]I'm using a standard UK keyboard.  I've never even noticed AltGr before...but there it is right in front of me!

That looks useful.  Is there a keyboard map somewhere which tells me how to type à, é, è, î. ö, ä, ü, ç, ß...etc when I type in French or German?  Or are the Gnome/KDE key bindings the same as for M*******t Office? (eg alt+shift+;/: , u for ü - und so weiter)?

(I'm not on a Linux machine to test at the moment)[/QUOTE]
I use a little gnome panel app to get all those, as my girlfirend is Flemish and needs them. I have it setup as a draw so I just click the draw and it pops down, I select the caracter I need and it sticks it on the 'clipboard' (what's the clickboard called in Linux terms??) Ctrl+V and you have the letter

---

### Post by Edward The Bonobo on 2006-05-09
ASCII = Anglo-Saxon Cultural Imperialism Imposed

---

### Post by syg00 on 2006-05-11
Whoa  !!!! Somebody is a little bitter and twisted.
Glad my background is EBCDIC. Also makes me big-endian.

But maybe we'd better not go there ....:twisted:

---

### Post by mixmaster on 2006-09-16
Well, I have a UK keyboard UK set as the default layout, but I can't get a UK currency symbol (should be shift-3).  The rest of the layout is correct.

---

### Post by mitkaese on 2008-06-30
This may be obvious, but I can't seem to get the inverted exclamation and question marks used in Spanish. I've set (in Ubuntu 8.04) the AltGR to the right Alt and all accented characters work well. I just can't seem to find anything about the inverted characters.  Any help would be appreciated.

---

