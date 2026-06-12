---
title: "Ascii/nfo viewer application"
date: 2005-10-24
forum: Desktop Environments
---

### Post by graabein on 2005-10-24
I have been searching for a small app to view nfo-files. What do you guys use and is it in Synaptic?

---

### Post by Zeroedout on 2005-10-24
[quote=graabein]I have been searching for a small app to view nfo-files. What do you guys use and is it in Synaptic?[/quote]

I use gedit, just turn the text/word wrapping off

---

### Post by graabein on 2005-10-25
I have been using gedit too but I don't like it very much for ascii/art/nfo files. Maybe this thread could be moved to the community chat?

---

### Post by mykey on 2005-10-25
try leafpad - its much faster than gedit

and then - we are not in windoze here - ascii files should just be watched with apps capable of  ascii display - use a fixed width font like monospace and you can have fun with the arts

---

### Post by ow50 on 2005-10-25
Since elegant NFO file-viewing needs a different encoding and font, it's good to have a separate app for it. As I found no NFO viewer, I wrote one myself.

To try it:
1. Install packages "python" and "python-gtk2" if you don't have them already.

2. Get the Lucida Console P font
```
cd ~/.fonts
wget http://home.online.no/~aageli/luconP.ttf
```
monospace works as well, but it's not as good.

3. Download my script
[http://koti.mbnet.fi/~ots/scripts/nfoview](http://koti.mbnet.fi/~ots/scripts/nfoview)
Put it for example in ~/bin or some place that's in your PATH and give it execute permissions. Edit the settings at the start of the file if needed.

4. Use it
```
nfoview file.nfo
```

For easy use, you can add a mime-type for .nfo extension and make a desktop file for nfoview.

---

### Post by mykey on 2005-10-25
.. not bad at all OW50 not bad at all .. I like it :p

---

### Post by graabein on 2005-10-28
[QUOTE=mykey].. not bad at all OW50 not bad at all .. I like it :p[/QUOTE]

I might give this a try when I get home. Care to post a screenshot to get my hopes up? ;)

---

### Post by ow50 on 2005-10-28
[QUOTE=graabein]Care to post a screenshot to get my hopes up? ;)[/QUOTE]
No, but I'll describe it, since it's rather simple. It's a text view widget put in a window. No toolbar, no menubar, no buttons. ASCII-art looks as it should.

---

### Post by bionnaki on 2005-10-28
nice!
I do miss DamnNFO in windows...
gedit just doest cut it.

---

### Post by mangoshake on 2005-10-28
very nice! does exactly what it needs to.

Thanks ow50

---

### Post by graabein on 2005-10-28
Yes, that was what I wanted. Thanks champ, I owe you one. You should put it on a howto or a wiki for later reference, maybe with an explanation on how to make mime-types etc...

---

### Post by bionnaki on 2005-10-28
I dont have a ~/.fonts directory...where should I put the LC P font?

you should make this a how-to...
I'm sure alot of others would use it.

---

### Post by mangoshake on 2005-10-28
bionnaki,

I didn't have that directory either but I just created it and it worked (I checked in gedit and saw the font there).

Edit: I didn't have ~/bin either and again, I created it and it got added to my path.

---

### Post by ow50 on 2005-10-28
[QUOTE=bionnaki]I dont have a ~/.fonts directory...where should I put the LC P font?[/QUOTE]
Create that directory.
```
mkdir ~/.fonts
```

[QUOTE=bionnaki]you should make this a how-to...
I'm sure alot of others would use it.[/QUOTE]
I think I will. Maybe in a couple days when I have more time.

---

### Post by ow50 on 2005-10-28
I made small changes to the script and posted a [lenghty HOWTO](http://ubuntuforums.org/showthread.php?t=83499).

---

### Post by bionnaki on 2005-10-29
thanks!

---

