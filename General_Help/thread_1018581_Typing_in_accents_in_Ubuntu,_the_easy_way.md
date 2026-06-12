---
title: "Typing in accents in Ubuntu, the easy way?"
date: 2008-12-22
forum: General Help
---

### Post by Lupusceleri on 2008-12-22
Hey there,

I find myself using accents quite often. With accents, I mean things like é è ç ä ë ï û and so on. In Windows, I used to just press the corresponding accent and then the letter I wanted it above. So to type what I just did up there, I'd actually hit these keys: 'e `e 'c "a "e "i ^u and so on.

For some reason, Ubuntu doesn't do this, or at least not by default. I know for sure that Xubuntu DOES have this functionality, since I use that on my laptop and it works there without having to put in additional settings.

Is there any way I can enable this function, as I really miss it?

Thank you very much,

Lupus.

---

### Post by ajcham on 2008-12-22
You can set up a Compose Key in System » Preferences » Keyboard » Layouts » Other Options…

---

### Post by Lupusceleri on 2008-12-22
> **ajcham said:**
> You can set up a Compose Key in System » Preferences » Keyboard » Layouts » Other Options&#8230;

Thanks for the answer, but that's not (exactly) what I mean... What you describe there is requiring you to hit one extra button each time you want an accent. While of course much easier than going to the special characters menu every time you need an accented character, it's still not ideal. :)

What I'm looking for is that it doesn't at once put down the accent when I hit the button, but that it waits to see if I am going to hit another character (like the e) whereafter it gives the corresponding character with the right accent above the e.

Anyway, if xfce can do it, surely gnome can too?

---

### Post by engine on 2008-12-22
Most apps seem to recognise the, erm, "shortcut" Ctrl+Shift+U for unicode selection: hold down control and shift, press u, type in the four-digit Unicode number and release control and shift.
OpenOffice doesn't, but offers its own Insert special character (or is it Insert symbol? don't have it installed on this machine)
And there were some other replies to my posting in [June 2008]("http://ubuntuforums.org/showthread.php?t=841108")

hth

---

### Post by Spacize on 2008-12-22
I think it's to do with the keyboard layout you choose

---

### Post by Lupusceleri on 2008-12-22
> **Spacize said:**
> I think it's to do with the keyboard layout you choose

Right, I'm from Holland and I use a Logitech G11 with, afaik, the USA International setting.

---

### Post by Icebear on 2008-12-22
I think what you are wanting is what called a dead key.

On the holland layout I think it is on the "[" key for (on my keyboard the key to the right of the P)

I gave a quick test and seem to be the only extra bits you can get is ä the two dots. Maybe if you get add a spanish layout you could get the extra acents

---

### Post by Icebear on 2008-12-26
also found this sight from a latter forum


[http://www.debianadmin.com/special-characters-made-easier-in-ubuntu.html](http://www.debianadmin.com/special-characters-made-easier-in-ubuntu.html)

---

### Post by Lupusceleri on 2009-01-22
After reinstalling again (I had messed up stuff) with Kubuntu instead of Ubuntu this time, I found out the fix.

Instead of USA International, I had to use USA Alternative International (Old International) as keyboard.

It boggles the mind why they´d remove that functionality in the first place, but oh well.

---

### Post by ajcham on 2009-01-22
> **Lupusceleri said:**
> It boggles the mind why they´d remove that functionality in the first place, but oh well.

Not really - what do you do when you actually want to use quotes, apostrophes etc.?  How does the system know not to turn it into an accented letter?

EDIT: I've just realised that the apostrophe in your post ("they´d") is in fact an acute accent, so does that mean you've lost the actual apostrophe character completely?

---

### Post by Lupusceleri on 2009-01-22
> **ajcham said:**
> Not really - what do you do when you actually want to use quotes, apostrophes etc.?  How does the system know not to turn it into an accented letter?

EDIT: I've just realised that the apostrophe in your post ("they´d") is in fact an acute accent, so does that mean you've lost the actual apostrophe character completely?

Heh, probably. I thought it was just a glitch.

So on to the next problem. At least I can type accents-on-letters properly again.

---

### Post by Lupusceleri on 2009-01-23
Fix for the apostrophe ' and quotes " is just hitting the spacebar after pressing the accent button, rather than pressing the accent button twice to get the accent.

---

### Post by ajcham on 2009-01-23
> **Lupusceleri said:**
> Fix for the apostrophe ' and quotes " is just hitting the spacebar after pressing the accent button, rather than pressing the accent button twice to get the accent.

In that case it makes sense that they would change the functionality - I think the average English-speaker would use apostrophes and quotes far more often than they use accents and diacritics, so it's quite reasonable to make them the more convenient to type.

---

### Post by mssever on 2009-01-23
The layout I use is "USA International (AltGr dead keys)". The advantage of this particular layout is that it works just like the standard US layout (so quotes work properly), but if you use AltGr (right Alt), you get full access to accented characters.

This is in Gnome. I presume that the same layout is available for all desktops, but I can't guarantee it.

---

### Post by HyperHacker on 2009-01-23
I have a similar issue with Xfce. It's got Right Alt set as the "compose" key or whatever it is, that if I hold it and type e, I get é, etc. It's useful, but I'd rather have that useless "menu" key do that, and the Alt key be an actual Alt key. How do I do that?

---

### Post by mssever on 2009-01-23
> **HyperHacker said:**
> I have a similar issue with Xfce. It's got Right Alt set as the "compose" key or whatever it is, that if I hold it and type e, I get é, etc. It's useful, but I'd rather have that useless "menu" key do that, and the Alt key be an actual Alt key. How do I do that?
Look in Keyboard Preferences > Layouts > Other options > Third level choosers. But I don't think that the menu key is one of the available choices. Rather lame, if you ask me. It should be possible to specify any arbitrary key.

EDIT: Oops, didn't see that you're running Xfce. My comments apply to Gnome.

---

