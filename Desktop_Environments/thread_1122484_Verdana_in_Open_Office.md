---
title: "Verdana in Open Office"
date: 2009-04-11
forum: Desktop Environments
---

### Post by mucklas on 2009-04-11
Could someone please explain this to me? In Open Office, when I type "é" I instead get "È". Believing my keyboard settings might be off I used the "insert special character" function. In the chart the letter "È" appeared twice, once in it's logical place and once where you would expect the letter "é" to appear. In short: it's impossible to get "é" on the screen. This problem is limited to Verdana in Open Office only, everywhere else the font and the keyboard works as I would expect, every other font has the letter "é" in it's proper place. Help?

---

### Post by Ratscallion on 2009-04-11
Do you have Windows installed on another partition? If so, do you have the verdana font file in C:\Windows\Fonts ? (replace C with your Windows drive name) if you do, just copy it to /usr/share/fonts/thai and then in a terminal type the following to reload your font cache:
```
 sudo fc-cache -f -v 
```
Once that's done, try loading OpenOffice again, and try the é thing again in Verdana. Does the same issue happen with other fonts, if so then it's Openoffice that's your problem.

---

### Post by mucklas on 2009-04-11
I have no Windows at all. My Verdana font is here /usr/share/fonts/truetype/msttcorefonts

---

### Post by coffeecat on 2009-04-11
I can't reproduce your problem in either Jaunty Beta with OO 3.0, or in 8.04 with OO 2.4.1.

I don't know how to get accented characters with this UK keyboard, but I tried with Insert > Special Character. See my screenshot to see if I have understood you correctly, but it seems to me that [FONT=Verdana, sans-serif]È, è, É and é are all there.

One thing occurs to me. Even if you select Verdana for the whole of your document (as you can see I have), when you open the 'Special Characters' sub-window, the font drop-down selector defaults to your desktop font. I had to select Verdana here as well. Could this be the problem?[/FONT]                            [FONT=Lucida Grande]

[/FONT]

---

### Post by Ratscallion on 2009-04-11
I always use right alt or alt gr and then the letter to make é. Try that, then tell me what happens. Cheers!

---

### Post by coffeecat on 2009-04-11
> **Ratscallion said:**
> I always use right alt or alt gr and then the letter to make é

I wasn't quite sure whether you were addressing the OP or myself, so I tried it anyway, to see if that might be of some use to the OP. But just to complicate matters, I'm using an Apple keyboard with the gnome settings for Macintosh keyboard. When I typed right-Alt-e in OpenOffice, I got an ordinary e with no accent.

However, you have done me a favour. :) I accidently pressed Right-Cmd-e and got what you see in the screenshot. I can't find in Compiz settings what on earth I triggered, but it's rather nifty, don't you think? :p

Cheers!

---

### Post by mucklas on 2009-04-11
See, this is what's really strange. My special character meny doesn't look like that. Look! 
alt e or altgr e doesn't work either.

Happy something good came out of this, coffeecat! :)

---

### Post by coffeecat on 2009-04-11
Yes, very strange. If you compare my and your screenshots side-by-side it look as though only the accented [FONT=Verdana, sans-serif]É and é are affected. I don't have any further suggestions except to look on the [OpenOffice support site]("http://support.openoffice.org/index.html"). There's a couple of forums linked there. Someone must have come across this before.[/FONT]

> **mucklas said:**
> Happy something good came out of this, coffeecat! :)

Thanks! It made me jump when the screen went like that though. I thought I'd done something seriously wrong. :|

---

### Post by mucklas on 2009-04-11
I just tried something. If I open a document containing the letter é and change the font to Verdana all the é:s turn to È:s. Really depressing... :P

Searching the Open Office forum produced nothing. I'm in the process of upgrading to Intrepid, maybe I should step it up...

As always I'm profoundly grateful for the time spent by the wonderful people here just to help me. Chocolate chip cookies all around!!

---

### Post by coffeecat on 2009-04-11
Here's an idea. Goodness knows whether it will work. Have a look in your home folder. There a hidden folder called '.openoffice.org2'. I presume this keeps your personal settings. Don't delete it (just yet). Rename it (so that you can restore it if neccessary) and then reopen Open Office. Hopefully, you'll get the OO default settings again. ( :? ) You'll lose all your OO personal settings, of course, but if this is a problem in your personal settings, this might just fix it.

Actually, before you do that, create another user account. Log out and log in to the new account and open OO. Do you get the same problem? If you do, there's something screwy with OO in the system/application files. If you don't, then it's safe to assume it's something to do with your personal settings and you could try the above.

Keep us posted with developments! :p

**Edit:** and here's another idea. :wink: I wonder if this might be a corrupted Verdana font. Try and get hold of the Verdana*.ttf files from somewhere. There's eight Verdana*.ttf files on my system. Do you have a friend with Windows? If so, delete all your Verdana*.ttf files and do what Ratscallion suggested.

---

### Post by mucklas on 2009-04-11
It's fixed! I deleted all and every verdana file, had my husband (who sometimes still runs Windows) send me his verdana font, copied them into the same old folder, reloaded the cache (thanks Ratscallion) and Bingo! It works!
Corrupt files, thankyou coffeecat.

More cookies to everyone!! :D

---

### Post by Ratscallion on 2009-04-12
You're very welcome! Glad I could be of assistance!

---

