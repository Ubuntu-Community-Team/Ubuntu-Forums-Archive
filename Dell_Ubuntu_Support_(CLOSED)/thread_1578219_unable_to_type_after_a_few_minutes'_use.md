---
title: "unable to type after a few minutes' use"
date: 2010-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by F104G on 2010-09-20
Hello people.  I've done a search and can't find anything quite like this in here.
I have a Dell Inspiron 630M which is misbehaving.  When I turn it on, while the screen is still showing the blue Dell logo, the machine lets out a series of high-pitched beeps (sometimes one or two, sometimes twenty or more).  Ubuntu then fires up as normal.  I type in my password no probs, and everything seems OK for a minute or two.
Then the trouble starts...
There are some extra buttons on the front edge of the laptop, for play/pause, rev, ffw, mute etc.  These light-up for seemingly no reason, and then I'm unable to type or click.  Sometimes (only sometimes) I can type if I hold down the shift key.  This is pretty annoying, but it does enable me to save stuff etc.  Also, once this has happened I cannot click on stuff in the header bar unless I'm holding down shift.  Sometimes even this doesn't work, and the only way I can close the machine is to Control/Alt/Delete - strangely enough, if I do this I can then click on the "shut down" option without any problems.  Sometimes (but not always) the on/off symbol is missing from the top right of my screen, so even if I am able to click there's nothing to click.
Is this a hardware thing or a software prob?
Should I just throw the old laptop in the bin and buy a shiny new one?
Thanks in advance.

---

### Post by wilee-nilee on 2010-09-20
Have you tried plugging in a external keyboard.

---

### Post by F104G on 2010-09-20
> **wilee-nilee said:**
> Have you tried plugging in a external keyboard.

Yes I have.  It makes no difference.  I can only type using the external keyboard if I hold down the shift key.

---

### Post by ianmillington on 2010-09-20
Very strange. I have that machine with kubuntu 10.04 on it. It's certainly still good enough for me so I wouldn't think of binning it yet. 

Do you have a live cd available? If so, does everything work Okay when you run it? If it does then it may be a config issue (although frankly I doubt it).

You might also check whether the keyboard connector has come loose. It's easy to fix. Take out the battery and you will find 2 small screws that go into the case. That will enable you to remove the strip above the keyboard. Once that is off the keyboard simply lifts out and you can check the connection.

However, if you check here

[http://support.dell.com/support/edocs/systems/ins630/en/sm/keyboard.htm](http://support.dell.com/support/edocs/systems/ins630/en/sm/keyboard.htm)

It makes no reference to the screws underneath the battery so there must be 2 types. Make sure you check for the screws before you lever that panel off!

Good luck

---

### Post by F104G on 2010-09-20
> **ianmillington said:**
> 

Good luck


OK thanks.  Must admit: it *SEEMS* like a hardware thing to me but you never know.  I'll have a go with the screwdriver and see what I can find.  I don't have the machine with me at the mo' so I'll report back later.

Mind you... if it IS a problem with the keyboard would this affect the external keyboard too?  And why do those blue lights keep coming on?

---

### Post by ianmillington on 2010-09-20
I don't know really - it might be that if the keyboard isn't properly detected that it throws everything out. 

Re-reading your first post, is the multimedia buttons lighting up the pre-cursor to the failure? Could one of them be stuck? If they are coming on seemingly with a mind of their own then the basic assumption must be that there is a short somewhere. I've not got my laptop with me but wonder whether these buttons could be disabled in the bios.

---

### Post by F104G on 2010-09-20
> **ianmillington said:**
>  is the multimedia buttons lighting up the pre-cursor to the failure? 
Yes.  It's why I call them the blue lights of death.  The lights come on and everything goes t**s-up.

> **ianmillington said:**
> Could one of them be stuck? If they are coming on seemingly with a mind of their own then the basic assumption must be that there is a short somewhere. I've not got my laptop with me but wonder whether these buttons could be disabled in the bios.
Perhaps.  They don't APPEAR to be stuck, by which I mean they're all sitting proud.  I can't decide if the lights are a symptom or the cause.
Now I'm back home I have just taken off the keyboard.  Everything looked fine under there, but I removed the ribbon and re-installed it carefully (just in case).  Firing the machine back up I've still got the same problem: computer's fine for 2 or 3 minutes... and then BLEURGH!

---

### Post by ianmillington on 2010-09-20
Hmmmm. It's the couple of minutes then "bam" that I don't understand.

I'm really starting to wonder if there's something deeper going on here. However, a couple of points:

1. Have you tried with a live cd?

2. I assume you don't dual-boot but if you do what happens when you are "on the dark side"?

---

### Post by F104G on 2010-09-21
> **ianmillington said:**
> 1. Have you tried with a live cd?

No - what's a "live CD"?

> **ianmillington said:**
> 2. I assume you don't dual-boot but if you do what happens when you are "on the dark side"?

That's right: I don't dual boot.  Ubuntu is the only OS I have on the laptop.

---

### Post by lisati on 2010-09-21
A couple of thoughts here. 

I don't actually use a Dell, but have encountered beeps at power up on other machines that suggest that something has gone belly-up with the hardware. This could be anything from a loose connection or a card that simply needs reseating to something more drastic. If this is the case there's a good chance that there's some kind of pattern to the beeps that indicate what kind of problem is being detected. 

The lights: part of the Power-on self test or something else? Hmmmm.....

---

### Post by F104G on 2010-09-21
> **lisati said:**
>  something has gone belly-up with the hardware. 

That's my hunch.  Is it safe to attack the thing with a screwdriver, or am I in danger of breaking it completely?  Gotta admit: at the moment it's a fairly unusable machine anyway, so I can't make it much worse.

> **lisati said:**
>  there's a good chance that there's some kind of pattern to the beeps that indicate what kind of problem is being detected. 

I can't detect any pattern.  Sometimes it's lots of rapid-fire beeps (hard to count 'em, but somewhere in the region of 30) and other times it's a single beep.

> **lisati said:**
> The lights: part of the Power-on self test or something else? Hmmmm.....

The lights do indeed come on when the machine is fired up.  They go out again within a second or two, before the Dell logo appears.  Sometimes they don't come on again for quite some time - the other day I had about half an hour of trouble-free browsing and music playing - sometimes they come on after 15 seconds.  The result is always the same: unable to type or click.  :confused:

---

### Post by ianmillington on 2010-09-21
The live cd is the one you slap into the cd drive and boot up the machine with it in, enabling you to take ubuntu for a test run.

Must confess though I think there is something deep going on here.

---

### Post by F104G on 2010-09-21
> **ianmillington said:**
> The live cd is the one you slap into the cd drive and boot up the machine with it in, enabling you to take ubuntu for a test run.

Ah, I see.  I don't have one of those - I loaded Ubuntu from a USB stick.
Anyroadup: I took the plunge this evening and attacked the machine with a screwdriver.  After taking it apart I removed the ribbon from the back of the media button panel (just tucked it up under itself) and it seems to have stopped the dreaded blue lights.  Trouble is: my mouse pad is now not working - ha!  I took the thing apart again and noticed the ribbon had come adrift from the pad, but I can't get to where it belongs - I think the pad is glued on.  I stole a mouse from my other half's Mac and that works fine.  Perhaps I should just buy myself a mouse for the laptop.  I'll be in the sticky stuff when she finds out I've stolen her mouse...

---

### Post by ianmillington on 2010-09-21
Doesn't your USB stick do the same, i.e allow you to try before you (don't) buy?

Is the keyboard working okay now? - hope so.

If so, I agree a small mouse costing a few quid isn't too much of a price to pay

---

### Post by F104G on 2010-09-22
> **ianmillington said:**
> Doesn't your USB stick do the same, i.e allow you to try before you (don't) buy?

Yeah, I see.  Although I don't have it on my USB stick anymore 'cause it was working fine for a while after I installed.  Didn't think I'd need it again. :-\"

> **ianmillington said:**
> Is the keyboard working okay now? - hope so.

If so, I agree a small mouse costing a few quid isn't too much of a price to pay

Yes, keyboard is fine.  I might see if I can replace the mouse pad - I'm one of those strange people who actually prefer these to "proper" mice (?mouses?).  I can see where the ribbon cable has come adrift but can't get to it to re-attach.  Looks like the pressure pad is glued onto the mounting frame - not sure.  I removed every screw I could see and it still wouldn't budge.  Anyway, I've got a useable pooter again and it hasn't cost me anything so far.
Thanks for your help, sometimes just talking things through with someone helps to clarify things. :cool:

---

### Post by F104G on 2010-09-23
Well, not EVERYTHING is as it should be :)
I bought myself a cheapo mouse from Tesco last night and spent a couple of hours on the laptop with no problems.  But...

when I tried to turn off the machine the on/off symbol was missing.  Here's a piccy:

[IMG]http://i18.photobucket.com/albums/b147/HeidiLandRover/Screenshot.png[/IMG]

As you can see, in the top-right corner of my screen there's a blank space.  I can type ctr+alt+del and then click on shut down, but it's still not right.  Any ideas?

---

### Post by ianmillington on 2010-09-23
I'm a kde freak myself so I'm outside my sphere of expertise a bit here. However, I have read that if you right click on a panel applet you can delete it. Is it possible you have accidentally done that? If so, I understand you can replace them easily (again by right clicking).

I'm not sure what to make of it but is are the 2 panels at the top right of the screen overlapping a bit?

---

### Post by F104G on 2010-09-23
> **ianmillington said:**
> I'm a kde freak myself so I'm outside my sphere of expertise a bit here. However, I have read that if you right click on a panel applet you can delete it. Is it possible you have accidentally done that? If so, I understand you can replace them easily (again by right clicking).

I'm not sure what to make of it but is are the 2 panels at the top right of the screen overlapping a bit?

Hmmm
I right-clicked on the black portion (where the on/off symbol should be) and clicked delete panel.  Now the entire top panel is missing.  Can't seem to get it back either.  Tried right-clicking on the bottom panel and choosing new panel but nothing happens.

\Confused blog

---

### Post by F104G on 2010-09-23
OK, I got it back :)
pressed Alt/F2, opened terminal and then typed
[I]
gconfig --recursive-unset /apps/panel
pkill gnome-panel[/I]

The top panel is back - WITH the elusive on/off symbol
I'm learning (slowly)!

---

### Post by ianmillington on 2010-09-23
Yep, that's how we all figure these things out - trial and error! :-)

---

