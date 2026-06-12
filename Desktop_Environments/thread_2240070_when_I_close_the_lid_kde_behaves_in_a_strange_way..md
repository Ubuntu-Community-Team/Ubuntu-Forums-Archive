---
title: "when I close the lid kde behaves in a strange way.."
date: 2014-08-17
forum: Desktop Environments
---

### Post by ollylove on 2014-08-17
hello everybody!!..
I'm using kubuntu 14.04 on my new MSI laptop.. but I have a problem:
every time I close the lid, after five minutes or more my desktop behaves in a weird way.. sometimes my widgets change position, sometimes some applications start, some windows re-size, or kde changes workspace..
but nothing serious, till the last two times I closed the lid for about 15 minutes -- my computer turned off!!.. I have the power button on the kde-panel, it's like the mouse moves by its own over the icon and clicks it.. but I got no mouse!!..
anyway here is a screenshot of my desktop, if it's useful:

[https://drive.google.com/file/d/0B3yxZDKAwTB6Y1JZQlNfckxoLUE/edit?usp=sharing](https://drive.google.com/file/d/0B3yxZDKAwTB6Y1JZQlNfckxoLUE/edit?usp=sharing)

can anyone understand what's the problem with my laptop??.. it seems possessed!!.. ò.ò
thank you very much!!..

---

### Post by bra|10n on 2014-08-19
Hi ollylove,

By default KDE is set to restore your previous session which _might_ explain this behaviour.
Look at systemsettings -> startup & shutdown -> session management -> and use  "empty session".

---

### Post by buzzingrobot on 2014-08-19
Are you certain the laptop is suspending when you close the lid? 

On the other hand, if it is not suspending when the lid is closed, heat will not dissipate correctly, the machine will eventually overheat, and that may trigger a shutdown.

It's also possible, I suppose, for something physical to be interfering.  E.g., a loose keycap that's in contect with the screen when the lid is closed.

---

### Post by ollylove on 2014-08-19
> **bra|10n said:**
> Hi ollylove,

By default KDE is set to restore your previous session which _might_ explain this behaviour.
Look at systemsettings -> startup & shutdown -> session management -> and use  "empty session".

I already set up my configurations at the beginning (empty session) and this doesn't seem to be the problem.. nor the power settings are the problem, since I set "no action" when the lid is closed..

> [COLOR=#000000]Are you certain the laptop is suspending when you close the lid? [/COLOR]

[COLOR=#000000]On the other hand, if it is not suspending when the lid is closed, heat will not dissipate correctly, the machine will eventually overheat, and that may trigger a shutdown.[/COLOR]

[COLOR=#000000]It's also possible, I suppose, for something physical to be interfering. E.g., a loose keycap that's in contect with the screen when the lid is closed.[/COLOR]

ahm, sorry, I'm not very expert about hardware, but I'm sure the laptop was turned off, not suspending..

but it already happened once before: I closed the lid and after some minutes I re-opened it and the power options window was appearing.. you know, if you don't choose a shutdown/suspend/restart option in 60 seconds the system will shut down, automatically.. I was lucky that time, I arrived soon and had time to close the window.. but those last two times I came late and it shut down..

sorry, I'm not sure I explained me clearly, I don't know how to explain it.. :-?

---

### Post by buzzingrobot on 2014-08-19
If it isn't suspending, or anything else, due to opting for 'No Action', then that leaves open the possibilibity of a heat buildup when the lid is closed, which triggers a shutdown.

I've seen the power option window appear on resume from suspend, as well as the "This system is about to suspend" message that appears a minute or so before a system times out to suspend.

The business of shutting down after 15 minutes may or may not be related to the window movement you noticed. Do you see windows actually move, or are they just in a different place?

---

### Post by ollylove on 2014-08-19
> **buzzingrobot said:**
> The business of shutting down after 15 minutes may or may not be related to the window movement you noticed. Do you see windows actually move, or are they just in a different place?

you mean after I reopened the lid??.. no, nothing moves while I open the lid or immediately after, I only find the widgets in a different place on the desktop or a current window resized from the full-width..
but I managed to stop my widgets moving by setting "lock objects" on the desktop.. they don't move anymore, now just the power window pops up..
but if I leave my laptop with open lid - for some minutes, for one hour, for the whole day - nothing happens..

maybe a screenshot could help.. do you want me to try and take a screenshot before and after I close the lid, in order to see what changes and how??.. hopping it doesn't shut down again!!..

---

### Post by buzzingrobot on 2014-08-20
The typical default mode in laptops is to suspend when the lid is closed. If you've disabled that by opting for "No Action", then keeping the lid closed while the machine continues to operate normally will reduce heat dissipation. Many systems will shutdown if the hardware temperatures exceed a certain threshold. Since you say your system shuts down 15 minutes after closing the lid, perhaps overheating is occuring.

---

### Post by ollylove on 2014-08-20
yes, it could be for little old laptops.. but my own one is two months old, is very large (17.3"), with two cooler fans and I don't think this is the point.. it never shut down before, since there were my widgets and my possessed system preferred them to move, instead of shutting down.. but now that's the only thing it does..
anyway, I said 15 minutes, but it could be 10 or even 5.. probably if I remove the power icon from the panel my system won't shut down anymore.. but I think it keeps on resizing the windows or open some applications from the icons on the panel..
let's see what happens if I remove the power icon..

---

### Post by ollylove on 2014-08-20
ok, I'm and idiot, I forgot to remove the icon.. but I took a screenshot before and after closing the lid.. here is before:

[https://drive.google.com/file/d/0B3yxZDKAwTB6Mi1fRVhxS2tUTzQ/edit?usp=sharing](https://drive.google.com/file/d/0B3yxZDKAwTB6Mi1fRVhxS2tUTzQ/edit?usp=sharing)

and here's after:

[https://drive.google.com/file/d/0B3yxZDKAwTB6VnBCa28waGZNemc/edit?usp=sharing](https://drive.google.com/file/d/0B3yxZDKAwTB6VnBCa28waGZNemc/edit?usp=sharing)

you see??.. the ubuntuforums tab was closed and your message was searched with google.. and the calendar appears, like when you click on the digital clock..

---

### Post by bra|10n on 2014-08-21
[IMG]http://i.imgur.com/LfPOriw.png[/IMG]

What exactly does this mean in plain english?

---

### Post by ollylove on 2014-08-21
well, that's not easy, nor in italian for me too..
but I think it means: when this option is selected, the system should always suspend when the lid is closed (if set this way), even if there is open an application which could prevent the system from suspend.. an app such as transmission, I suppose..

---

### Post by bra|10n on 2014-08-21
Or possibly the exact opposite... :)
My point is have you tried with the option both checked and unchecked?

---

### Post by ollylove on 2014-08-21
already tried!!.. nothing changes..
I've been using kubuntu on my old laptop for a year, with the same settings, same widgets, same icons and same applications.. and I never had this problem before..
at this point I think the problem is hardware.. probably the lid gets in conflict with the touchpad (since I have no mouse) and after some minutes the thouchpad gets crazy.. what do you think, could it be??..
I'm thinking of installing a windows partition and see if it happens there too.. in this case the problem is really hardware and there's nothing you could do..

---

### Post by buzzingrobot on 2014-08-21
> **bra|10n said:**
> [IMG]http://i.imgur.com/LfPOriw.png[/IMG]

What exactly does this mean in plain english?

If "Lock Screen" is checked, the user's password is required to access the normal display when the machine wakes from suspend.  I.e., if it is suspended, the user will be prompted for a password when it wakes up, aka "resumes".

The second option means pretty much what it says:  A running process won't stop suspension from taking place when you close the lid. 

Since "No Action" seems to have been selected in this instance, though, I'm not sure any of this applies here.

---

### Post by buzzingrobot on 2014-08-21
> **ollylove said:**
> 
at this point I think the problem is hardware.. probably the lid gets in conflict with the touchpad (since I have no mouse) and after some minutes the thouchpad gets crazy..


I mentioned that earlier. Typically, there's hardly any space between the screen and the keyboard/touchpad when the lid is down.  So, yes, it's possible something is making physical contact. Since you aren't suspending, I guess it's even possible that the heat buildup produces a little screen warp, for example, and the screen comes in contact with a key or the touchpad.

---

### Post by ollylove on 2014-08-21
mm.. and what if I disable the touchpad before closing the lid??..
is there something I can do, btw??..

---

### Post by buzzingrobot on 2014-08-21
You may be able to disable the touchpad in settings.  I've disabled mine in the BIOS, but that's not a useful solution for you because you want to use the touchpad.

Have you tried setting it to suspend on lid close, and checking if anything moved when it resumes?  I.e. everything is off while suspended, so that should not happen.

---

### Post by ollylove on 2014-08-21
> **buzzingrobot said:**
> You may be able to disable the touchpad in settings.  I've disabled mine in the BIOS, but that's not a useful solution for you because you want to use the touchpad.

Have you tried setting it to suspend on lid close, and checking if anything moved when it resumes?  I.e. everything is off while suspended, so that should not happen.

I've not tried yet.. but maybe I found a solution: first I plugged in a mouse.. then in settings, mouse and touchpad, tick "disable touchpad when mouse is plugged in".. again I tried to close the lid for 
20 minutes and.. nothing happened!!.. \\:D/

---

