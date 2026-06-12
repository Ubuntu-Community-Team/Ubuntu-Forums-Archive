---
title: "Getting Rid of Yahoo"
date: 2009-04-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dave30c on 2009-04-20
My Dell Mini came with Yahoo's browser installed, and I want to get rid of ALL Vestiges of Yahoo.  How do I accomplish that?

Then, I want to download Firefox.  I presume that is done the same way as on a Mac or via Windoze.  

Thanks for the help.

Dave

---

### Post by ddrichardson on 2009-04-20
Not familiar with Dell's install but use synaptic package manager to search for Yahoo then remove. Firefox can be installed the same way.

---

### Post by Cowchip7 on 2009-04-20
That's what I did. Just remove the Yahoo toolbar extension using the synaptic package manager. ;)

---

### Post by dave30c on 2009-04-20
OK, thanks for the quick reply, but I'm brand new to Ubuntu & Linux.  What you just said is meaningless.  Maybe it can be translated into Mac-ese?

---

### Post by ddrichardson on 2009-04-20
> **dave30c said:**
> OK, thanks for the quick reply, but I'm brand new to Ubuntu & Linux.  What you just said is meaningless.  Maybe it can be translated into Mac-ese?
I don't know what that mac-ese is.

Click System->Administration->Synaptic Package Manager. Enter your password, use the search facility to find "yahoo" and untick any applications that are returned, if they say Yahoo. Click Apply.

---

### Post by Cowchip7 on 2009-04-20
> **dave30c said:**
> OK, thanks for the quick reply, but I'm brand new to Ubuntu & Linux.  What you just said is meaningless.  Maybe it can be translated into Mac-ese?

You'll get the hang of it in no time!

I got rid of Dell's deskbar launcher and use the classic desktop mode. You should try the same. :)

---

### Post by dave30c on 2009-04-20
Well, I found that Synaptic thingy and also the Yahoo extension, then deleted.  It didn't work.  Yahoo's browser is still there.

---

### Post by dave30c on 2009-04-20
Oh, am in Classic mode now. 

Lots to learn.

Even got one of my  own photos onto the desktop.  Wish I could figure out how to do that on my MacBookPro!!!

Dave

---

### Post by wsonar on 2009-04-20
Damn yahoo trying to stick there **** in ubuntu pre install's

that's the last thing we need

and enless onslaughter on usless toolbars

---

### Post by Cowchip7 on 2009-04-20
> **dave30c said:**
> Well, I found that Synaptic thingy and also the Yahoo extension, then deleted.  It didn't work.  Yahoo's browser is still there.

What "Yahoo browser" are you talking about? If it is the search bar immediately to the right of the url bar, then you just have to click on the little black triangle next to the Y! and change it to Google... or whatever else you want.

---

### Post by anjilslaire on 2009-04-20
No, The Dellbuntu brands Firefox as "Internet Browser, and doesn't actually say "Firefox", IIRC. It's branded as Yahoo in some way, but it *is* firefox.

---

### Post by jaqrah on 2009-04-20
>  wsonar  	
Re: Getting Rid of Yahoo
Damn yahoo trying to stick there **** in ubuntu pre install's

that's the last thing we need

and enless onslaughter on usless toolbars    


I think you mean Damn Dell trying to stick Yahoo's @#$! in Ubuntu.  Thats Dellbuntu for you!  ;)

---

### Post by ugm6hr on 2009-04-21
> **dave30c said:**
> Well, I found that Synaptic thingy and also the Yahoo extension, then deleted.  It didn't work.  Yahoo's browser is still there.

It is easier to ensure the result by using Terminal (Applications -> Accessories -> Terminal)

Close Web Browser

Then, in Terminal, type:

```
sudo apt-get remove yahoo-toolbar-extension
```

It will ask for your password - type it in (case sensitive) and press Enter (you won't see any flashing cursor to confirm).

Then restart Web Browser.

---

### Post by dave30c on 2009-04-21
> **Cowchip7 said:**
> You'll get the hang of it in no time!

I got rid of Dell's deskbar launcher and use the classic desktop mode. You should try the same. :)


Finally found preferences, under Edit on the menu bar.  On a Mac's Firefox, it's under "Firefox."  So, all I did was change home page to the correct news site, and problem solved.  Also changed the search tool to Google, and that problem is solved.  

Terminal command said the Yahoo extension was already removed, so must have dinged Yahoo's extension via that Synaptic thingy.  

Now to figure out how to change the Web browser from a plain square to Firefox's icon.  But that's for another day.

Thanks for all the help and tips.  You guys are Great!!

Dave

---

### Post by Cowchip7 on 2009-04-21
A plain square? The Firefox icon should be a blue globe! :P

If I am not mistaken, even if you were to install the vanilla version of Ubuntu, you would still have the generic blue globe icon for Firefox. There should be posts in this forum to change it- but I don't bother.

---

### Post by dave30c on 2009-04-21
> **Cowchip7 said:**
> A plain square? The Firefox icon should be a blue globe! :P

If I am not mistaken, even if you were to install the vanilla version of Ubuntu, you would still have the generic blue globe icon for Firefox. There should be posts in this forum to change it- but I don't bother.

I know.  That's what I have on my Mac.  On the Dell it's just a plain square.

---

### Post by Cowchip7 on 2009-04-21
Firefox isn't a square on my dell mini! :lolflag:

That would make me want to change it too!

---

### Post by Arndtwe on 2009-04-21
Well it certainly should not be a square. Just FYI, it is the realFF icon in vanilla install... Even UNR. There are tons of different icon themes out there, and good tutorials as well. it is a fairly simple process to undergo in order to change your theme. Best of luck!

---

### Post by Cowchip7 on 2009-04-21
> **Arndtwe said:**
> Well it certainly should not be a square. Just FYI, it is the realFF icon in vanilla install... Even UNR. There are tons of different icon themes out there, and good tutorials as well. it is a fairly simple process to undergo in order to change your theme. Best of luck!

You get the real firefox icon in the vanialla install now?! My last ubuntu install was Dapper. I think I had the blue globe then! :D

---

### Post by duckfeet on 2009-04-22
Just go into synaptic and click to remove entirely any yahoo junk you see installed there--it's good to get used to synaptic anyway, especially if you don't want to deal w/command line yet....the browser *is* firefox, just a lean model, which is good...and I'd switch out of the Dell Desktop, and then you'll never see Yahoo again...if yahoo had spent half the time designing a good search engine, as they did trying to install themselves everywhere, yahoo would still be a player, instead of the semi-malware they've become....

What an embarassing company that must be to work for, when it always has to sneak in uninvited, and is the *first* thing everybody wants to remove...what a joke...

---

