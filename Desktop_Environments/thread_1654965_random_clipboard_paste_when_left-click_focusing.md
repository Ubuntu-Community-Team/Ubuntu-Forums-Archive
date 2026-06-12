---
title: "random clipboard paste when left-click focusing"
date: 2010-12-29
forum: Desktop Environments
---

### Post by ToFue on 2010-12-29
When I'm typing in a text field of any kind, upon initially left-clicking in the field to focus, whatever was recently copied to clipboard pastes to the text field. 

This has been occurring randomly in gnome since I've installed Natty..

I can't recreate this most of the time; when it does happen, it usually happens a few times in a row then it doesn't happen for a good period.

Its more annoying, really.

I haven't come across anything that could explain it so I'm left suspecting a bug. If it is a bug, what would be useful to add in the bug report? 

Thanks in advance!

---

### Post by mcduck on 2010-12-29
Are you sure you don't accidentally middle-click? Or have both mouse buttons down at the same time (left+right works as middle click as well). Or perhaps the right mouse button is a bit stuck, resulting in left+right click?

If you have access to another mouse you could try if the same problem happens with it...

---

### Post by ToFue on 2010-12-29
Thanks for the reply, mcduck!

Sadly I have no middle button on my touchpad.  Second Click Simulation is disabled as well as Dwell Click.. during upsets I'm careful to not 'unison click' and it still happens.  I don't use mice on my laptop except for the touchpad, but haven't tried it with a mouse yet.

However, it seems to have upsets when text-editing applications like gedit and oo.org are in use.  I've rarely seen it occur with just firefox running, and it also occurs when focusing into a terminal window. Again, this is intermittent for me, ever since upgrading (clean reinstalling) to Natty.

Any more ideas are greatly appreciated!

---

### Post by phil_bell on 2011-01-15
I'm using Kubuntu 10.10 and I'm having a issue similar enough to join this thread, I think.

My left touchpad button periodically pastes random text when I click. I've noticed it in Firefox, Chromium, and OpenOffice, which leads me to believe it is a system issuse. I have only two buttons and I disabled the middle click function just in case I was accidentally hitting both buttons, but it is not the case.

Strangely, the randomly pasted text can be found in the clipboard, but I never cut or copied it there. They are things I've typed in searches and the address bar, but it seems the clipboard is copying and pasting with a mind of it's own.

A few other strange things are that occassionally a left click on my touch pad doesn't register and I have to press it again, and sometimes when I switch to a different tab on Firefox by left clicking on it, the tab will close instead. It has happened enough times that I'm sure I'm hitting the center of the tab and not the "X".

I don't know who to tell or where to post potential bugs. I'll keep tracking this issuse and let you know if I figure out anything else.

---

### Post by joe606 on 2011-01-23
I'm having the same random paste bug with my laptop touchpad (with no third mouse button)

Also i'm having problems when scrolling. if I hold down the left mouse button and move a scroll bar up and down (like when reading a long webpage) not keeping the mouse directly above the scroll bar, occasionally the mouse "drops" the scrollbar and starts highlighting what ever its over at that time - Very frustrating. its almost like the system temporarily decides the mouse button isnt still being held down, even though im sure it is!

Any help on this would be greatly appreciated!

---

### Post by phil_bell on 2011-01-24
I haven't figured out why the left mouse button randomly pastes things in the clipboard (Klipper in my case). Nor have I figured out why the clipboard stores things that I've typed, but that I have never cut or copied. I don't typically use scroll bars so I haven't noticed anything weird there.

However, since my last post I've turned on tapping on my touchpad. Since I've switched to tapping, there have been no occurences of random pasting. 

I guess I could boot into Windows and try using the left button and scroll bars for a while to rule out a mechanical issue. The next time I use Windows I'll try to remember and post the results.

---

### Post by phil_bell on 2011-01-28
I was not able to reproduce the random copying and pasting bug with the left button on my laptop running Windows XP natively. The left button works perfectly in Windows every time.

I noticed a few new bugs in Kubuntu. As joe606 noted, the left button releases randomly, even when I'm sure I'm holding it down. For me it happens with any action (scrolling, dragging a file, selecting text, etc.); although, it doesn't happen too often. To be sure, I booted back up to Windows XP and it does not happen there at all. 

The other new thing I noticed relates to the random copying and pasting bug. I discovered that if I'm holding down the left button and dragging something, when I lift my finger off of the trackpad pasting occurs 50% of the time. I doesn't happen evenly, but out of 20 tries it pasted 10 times. It's pasting the text that I selected, even though I never copied the text.

I was curious to see if the same error happen in WINE applications. So I opened Microsoft Word in WINE and only the random left button release occurred, not the random pasting. Then I noticed scroll feature flashing for a split second. Once I noticed it (it's fast), I was able to see it about 50% of the time when dragging something and lifting my finger off of the trackpad.

Just to be clear, the above issues happen only with my laptop's built in left button and trackpad regardless of whether or not the tapping feature is turned on. There are no early releasing or random pasting issues when using a USB mouse or when using the tapping feature alone for dragging operations.

**My conclusions:**
[LIST=1]
[*]The left button releasing randomly is a bug with the Synaptics Touchpad driver in Kubuntu 10.10. (No issues in 10.04)
[*]The random copying/pasting that occurs when dragging with the left button and lifting off of the touchpad is also a bug with the Synaptics Touchpad driver in Kubuntu 10.10. It seems that combination triggers a middle click&#8212;pasting in Linux and scrolling in Windows (WINE).
[/LIST]

**My workarounds:**
[LIST=1]
[*]Don't use the left button, use the tapping feature or a mouse instead.
[*]Turn off the middle click feature (if you forget not to use the left button like I do, at least it won't copy and paste things all the time).
[/LIST]

---

### Post by morriña on 2011-02-08
I have Ubuntu 10.10. The left-button of my laptop's touchpad is not only pasting random things, but also closing tabs in Firefox, when I did not left-clicked on the X at all.
phill_bell, thank you for the suggestions.

---

### Post by the-angry-scientist on 2011-02-09
:-({|=  Someone needs to fix it before I go CRAZY :mad:

When I click [Ok] or other similar buttons, I have to double click in order for it to register...it's so annoying!

---

### Post by joe606 on 2011-02-18
> **phil_bell said:**
> 

The other new thing I noticed relates to the random copying and pasting bug. I discovered that if I'm holding down the left button and dragging something, when I lift my finger off of the trackpad pasting occurs 50% of the time. I doesn't happen evenly, but out of 20 tries it pasted 10 times. It's pasting the text that I selected, even though I never copied the text.


Getting all the same problems as you are!!

Does anyone have a bit of software that will log mouse activity?? i want to log mouse events when this weird stuff happens... if focus is lost, but nothing logged, then it cant be the mouse driver. Similarly, if stuff is pasted with no mouse events, it cant be the driver... all points to problems with u10.10

---

### Post by linux_wannabe on 2011-02-25
This has been driving me insane since I installed Ubuntu 10.10!  I didn't have problems with it under 10.04 (but used it a whole lot less).  I'm doing a lot of programming for school, and I keep having random snippets pasted throughout my code... it's killing me!  It even inspired me to stop lurking on this forum and actually register!  :o)

Like the others posting about it, I've experienced the following:

-- Random pasting of things that I have or have not copied when I click the left mouse button.  It doesn't occur all the time, but often happens in spurts.  Like with phil_bell, it seems to happen most when I lift my finger off the trackpad while holding down the left mouse.  It's practically impossible to highlight a longer segment of text, because before you get to the end it stops and pastes whatever you had highlighted (you can imagine how this could be killing my coding efforts.....).
-- Closing tabs in Firefox and Chrome when I just left click on them.
-- "Dropping" the scroll bar and start highlighting text when I scroll down a page with the left mouse button down.  (The worst is when it then randomly pastes the newly-highlighted text into the middle of my code when I click back to it!)

Thinking that maybe I was running afoul of the middle-button simulation, I disabled it (and confirmed that it's not happening with Xev), but it's still happening.  I currently have mouse-pad tapping turned off, too.

Somebody please help!

---

### Post by congruent on 2011-03-19
> **phil_bell said:**
> I'm using Kubuntu 10.10 and I'm having a issue similar enough to join this thread, I think.

My left touchpad button periodically pastes random text when I click. I've noticed it in Firefox, Chromium, and OpenOffice, which leads me to believe it is a system issuse. I have only two buttons and I disabled the middle click function just in case I was accidentally hitting both buttons, but it is not the case.

Strangely, the randomly pasted text can be found in the clipboard, but I never cut or copied it there. They are things I've typed in searches and the address bar, but it seems the clipboard is copying and pasting with a mind of it's own.

A few other strange things are that occassionally a left click on my touch pad doesn't register and I have to press it again, and sometimes when I switch to a different tab on Firefox by left clicking on it, the tab will close instead. It has happened enough times that I'm sure I'm hitting the center of the tab and not the "X".

I don't know who to tell or where to post potential bugs. I'll keep tracking this issuse and let you know if I figure out anything else.

I'm having the exact same issue. I'm using Kubuntu on a flash drive...but I still expect it to work :) You're right, the strangest thing about this issue is it randomly pastes text from various text input fields that was never copied.

---

### Post by stephenhau on 2011-03-20
I'm also getting this problem in Firefox when editing in Gmail, and it's driving me nuts... I just want to get on with working, rather than hacking away at Ubuntu.

I didn't get this problem in the first few days, but have noticed it today. Here are some things I'm doing/using which may be non-standard, and possibly have some effect...

[LIST]
[*]Using [utouch]("https://launchpad.net/%7Eutouch-team/+archive/utouch") for my laptop's Synaptics TouchPad
[*]Using [fingerprint-gui]("http://www.n-view.net/Appliance/fingerprint/")
[*]Recently using hibernate/sleep rather than shutdown
[*]Added my wireless to the suspend_modules config according to [this]("http://ubuntuforums.org/showpost.php?p=6465454&postcount=6")
[/LIST]
I'll search around too and let you know if I find a solution...

---

### Post by linux_wannabe on 2011-04-04
I'm really hoping against hope that Ubuntu 11.04 will have somehow resolved this issue.  I have a TON of programming assignments I'm working on right now and this has really cost me a lot of debugging time.  I've contemplated upgrading to the Beta 1 to see if the bugs in the Beta cost me less time than this issue... has anyone tried out the 11.04 alpha or beta to see if the issue remains?

take care!

---

### Post by super ben on 2011-04-05
I'm running 10.04 and I have a similar problem. Sometimes when I'm scrolling down a page in Opera using the scroll on the side of my laptop touch pad, it will take me to a google search page. The search is always a series of words from the page I was previously on, though I never highlighted or copied it.

---

### Post by linux_wannabe on 2011-04-13
Hey all!  In an act of desperation or insanity, I tried installing the 11.04 beta 1 to see if it would resolve the random pasting issue... miraculously, it's working fine!  I'm not sure what part of the upgrade fixed it, but I've been running on 11.04 for 3-4 days and haven't had a single random mouse paste (or random browser tab closing when I click to switch to it, or any of the other extremely frustrating manifestations of this plague).  Hurray!  :P

---

### Post by uturn on 2011-04-18
This was driving me insane, but I solved it by turning off button 2 emulation and the corner button.

synclient TapButton2=0
synclient RTCornerButton=0

---

### Post by chrisking8613 on 2012-01-18
Hello everyone, I had the exact same problem and have found a significant fix : )  First, I have only encountered this problem while using Ubuntu and Kubuntu on Laptops. I believe that the random posting is caused by the touch-pad accumulating fingerprints or anything sticky (even though I see no direct connection). The way that stopped the random pastes, is by going into "touchpad settings", locating the "tapping" tab, and disable the "tapping with one finger feature". Further, using a USB mouse and keyboard should also stop the pastes because there is no interaction with the touchpad. This works fantastic for me, hope it helps someone else!

---

### Post by fhaddad78 on 2012-01-18
I can confirm that I am having this problem as well. However, I'm using a desktop computer with a Microsoft Comfort Mouse 6000 wired mouse.

The scenario...

I'll copy some port of code to the clipboard and then I will paste it somewhere else in the program, and the pasted contents will appear in multiple areas. This happens a lot, however, I can't seem to recreate the problem. The only thing I do know is that it will only occur if I have something in the clipboard.

---

### Post by fhaddad78 on 2012-01-18
After some research on this issue, I have come to realize that this is part of the functionality of the X11 system and the middle mouse button.

If you open up a text editor and open up a web browser, highlight some text on the web site, then switch back to your text editor and click your middle mouse button (or push the mouse wheel down) and you will see the text get pasted into your open document right where the blinking cursor.

The solution is to disable the middle mouse button (which you can find lots of resources on) if you don't want this sort of functionality to occur.

---

### Post by ingannilo on 2012-06-10
> **uturn said:**
> This was driving me insane, but I solved it by turning off button 2 emulation and the corner button.

synclient TapButton2=0
synclient RTCornerButton=0


Hey!  I want to thank you.  This was infuriating to me, and here you have the solution.  Is there are resource to understand other things that you can tell this touchpad to do?

---

