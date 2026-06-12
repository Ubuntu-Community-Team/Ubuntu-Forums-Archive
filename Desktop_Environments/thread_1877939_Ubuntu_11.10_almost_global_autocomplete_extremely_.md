---
title: "Ubuntu 11.10 almost global autocomplete extremely annoying. need to disable"
date: 2011-11-09
forum: Desktop Environments
---

### Post by krack3rz on 2011-11-09
So I has a serious problem, I cant get anything done because of it, its this damn autocomplete.

In the terminals, in the programs like jedit, gedit, etc. it always kinda looks like its inserting some word but in a very annoying and stupid way,

Looks kinda like this when you edit in text:
cp ./file.txt ./somelong_filename_|xt

whever you edit something, like adding a word, it looks like you are inserting a word and it overwrites but it doesnt, it has a "|" type of line at the right side of end of new text, and when you press [enter] it goes to next line,
when you stop typing word, aka pause, then want to type a number or something, it with be the same way and even type it where you click or press [left] or [right] keys

as far as I know I didnt enable this blasted option...

Please help me get rid of this garbage ware!!

P.S. when it autocompletes, it tries inserting dictionary words, and sometimes a stupid dialog box appears, which you can click

Specs: Ubuntu 11.10 Oneiric (latest updates, as of now), Unity, cairo-dock

Image(s):
[IMG]http://s9.postimage.org/d1rc502xr/annoying_Insert.png[/IMG]

P.S. (edit): I tried taking a screenshot of the dialog box but everytime I have it open and take a screenshot, the screenshot button on keyboard the dialog closes...

**_Following programs I found it affects:_**
[COLOR="DarkGreen"]gedit, jedit, libreoffice, chrome browser (so far only in search and this text box)[/COLOR]

---

### Post by krack3rz on 2011-11-11
Did I write this up wrong or something? Or Does no one just know?
Can someone say something? Feels like i'm being ignored...

---

### Post by typhoon_tip on 2011-11-11
Is not that, is that this problem is so weird that I think no one has a clue of what it can be due to... There is no such option in Ubuntu, it can only be concluded that is some external program causing this issue.

I think you have installed some sort of software somewhere but who knows... I think best way to deal with this problem would be to do a "sanitation" of the system, or a complete re-install from scratch without enabling external PPA or sources.

---

### Post by keithpeter on 2011-11-12
Hello krack3rz

Just tried to reproduce this on a fresh install of 11.10, just the Ubuntu defaults plus restricted extras. 

Can't see the effect, which would drive me mad definitely.

---

### Post by krack3rz on 2011-11-12
It definitely drove me nuts :)
Programming homework made me tear my hair out, writting appletviewer kept giving me "apple viewer" ](*,)

But I bring good news, after a restart the effect stopped. I have no idea how or what turned this blasted auto-dictionary-corrections but its not on now...

I checked the keyboard shortcuts, and nothing that could be it is there, and I would have remembered turning something like this on

It cant be a graphical program that did this all the ones I use all the time never yielded this before...and cant be terminal based since nothing was or is running from them, must be a service or program started that runs in the -background-

Maybe this could help someone else reading this.

---

### Post by BillyBoa on 2011-11-12
I have the same problem but with google in chrome. I write "we are..." and ends like "weather".

---

### Post by krack3rz on 2011-11-13
Does this happen to you all the time?
And does it ever go away? For me it was disabled when I restarted

Do you remember what programs you installed right before it started?

We both have the same thing so that means between us we can weed it out.

And I cant believe no one knows about this. Its global, so its gotta be a major program, one that takes your inputs and tries to suggest, in a very annoying way, what you mean to write.

Also, I dont know if you found a way to get it to stop underlining temporarily and changing stuff but ESC key helped stopping it (for every work though...sadly).

---

### Post by krack3rz on 2011-11-17
WOW!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

So I haz done it.

I solved the problem, it so simple....
Heres what you do to disable the autocomplete feature:
[CTRL] + [SPACE]

It starts it and stops it.

Its iBus, you can clearly see in the Preferences > Input Preferences that ctrl+space turns it on and off...

I hope this helps many out there :)

---

