---
title: "testing 11.04 :-(("
date: 2011-04-24
forum: Desktop Environments
---

### Post by ottosykora on 2011-04-24
So have just started  to look at the new 11.04 which will come in few days out.

But this is kind of big problem, as it comes with this new gui which is anything but self explanatory.
No menus, main menu can be configured but it does not exist later, just some hudge icons on the left side.
Where are the menus hiding? How to configure panel so menuas are there again?

So far it seems the only way to find an app is to search in this terrible black screen with hundreds of apps.

Can I switch to some 'normal' view ?

---

### Post by andymorton on 2011-04-24
> **ottosykora said:**
> So have just started  to look at the new 11.04 which will come in few days out.

But this is kind of big problem, as it comes with this new gui which is anything but self explanatory.
No menus, main menu can be configured but it does not exist later, just some hudge icons on the left side.
Where are the menus hiding? How to configure panel so menuas are there again?

So far it seems the only way to find an app is to search in this terrible black screen with hundreds of apps.

Can I switch to some 'normal' view ?


'Classic' Gnome is available via the login screen. 

andy

---

### Post by ottosykora on 2011-04-24
hmm, how to do it? can not find anything like that.

or is it not avaiable from CD?

---

### Post by Vaphell on 2011-04-24
at login screen, when you click your handsome face, at the bottom bar you have few comboboxes. One of them is responsible for Desktop Environment.

also you may start getting used to such interfaces, gnome devs abandon clasic gnome2 too and work on gnome3/gnome shell

---

### Post by ottosykora on 2011-04-24
so am I right this will be av for me only when I install the 11.04?

Normal desktop is not av from CD?

Can the place where I have to search for apps be somehow set up so that I can see the apps in a column and not over whole screen? 
Can I somehow change the switching all to th eblack screen so it remains more bright?

The problem is, that when I click on that app icon, the screen goes black and there are lot of icons on that black screen. This is very difficult read for me, if this apps screen would be white or somehow configurable I would be able better to read it, as this black is rather difficult.

---

### Post by ottosykora on 2011-04-24
also there is something strange with the firefox.

sometimes when I switch it on, I have no choice to have menu bar, bbut then the menus do appear on the top panel.

sometimes I start FF and the menu bar is where I expect it.

Is there some setting to make it somehow consistent?

---

### Post by Vaphell on 2011-04-24
oh, you were testing livecd, missed that part. If so then yes, you can't really change the user interface of live session. Classic gnome is available in fullblown installation at login screen.

firefox issue: remember that 11.04 is in beta so buggy behavior is to be somewhat expected and some bugs can exist even in the official release. Unity tries to do what OSX does with menus but not everything is polished yet.
Also not much can be said about customization of unity at this time, though it looks quite locked down. It's new and people didn't poke it around yet.

---

### Post by KegHead on 2011-04-24
Hi!

Goto classic:

system...admin..login..

you can choose your flavor.

KegHeg

---

### Post by KegHead on 2011-04-24
Hi!

you'll need to restart to tale effect.

KegHead

---

### Post by ottosykora on 2011-04-24
I was running it from CD, so it seems there is no choice there, since no login screen...

---

### Post by ottosykora on 2011-04-24
thannks vaphell

the gui is probably the mainstream hype of today, this darkening of the screen is on windows too, but there I manged to switch it off somehow.
Will wait some time until I will update, the firefox crashes here too often and complains about this and that too.

---

### Post by Vaphell on 2011-04-24
there are tons of updates daily, that's how betas roll :)

about the apps
when you have one opened you can pin it to the panel (rightclick to get the option) just like in win7 so it is there permanently, 1 click away.
also there is a panel item responsible for programs in general, with icon of + inside magnifying glass (at least on my installed 11.04). When you rightclick it you get a list of main categories. Granted it will lead you to the black window full of icons, but they will be narrowed down to the category you want and frequently used ones should be listed at the top.

edit: also i noticed that when you hold WIN_KEY, numbers/letters show up on the icons which allows you to run panel items with key combos

---

### Post by coffeecat on 2011-04-24
> **ottosykora said:**
> I was running it from CD, so it seems there is no choice there, since no login screen...

Yes, there is. With the live CD it will automatically start the Unity desktop if your hardware supports it. But you can then logout and at the login screen choose "ubuntu" as user, then "Ubuntu Classic" from the choice at the bottom of the screen, and for a password simply press the enter key.

> **ottosykora said:**
> also there is something strange with the firefox.

sometimes when I switch it on, I have no choice to have menu bar, bbut then the menus do appear on the top panel.

sometimes I start FF and the menu bar is where I expect it.

Is there some setting to make it somehow consistent?

I think you are talking about the global menu, where application menus appear in the top panel. Global menu is simply a panel applet in Classic gnome. If you don't want it, simply right-click on it and choose "remove from panel".

---

### Post by ottosykora on 2011-04-24
OK, tried to log out, entered ubuntu as user and selected classic, but it had no effect at all, it came back simply with the same unity screen.

I have tried also other as classic no effects etc, but it all has no function at all.

The menu at the top must be something in the unity function. The panel on the top can not be clicked on or modified , it is just static there and if I open Firefox, its menus sometimes appear in the panel, sometimes in the firefox itself, no control over it.

Firefox seems to be operating in fullscreen mode only, selecting the reduced mode it simply crashes on any webpage.

I downloaded the 11.04 today, so if this is going to be the final in few days, well, then better will wait few months.

---

### Post by ottosykora on 2011-04-24
Now I also tired to select the ubuntu classic under systemsettings, login screen, I have set it there to ubuntu classic, then logged off, tried to log in again, but nothing it comes back with the unity again.

Is there some way to make this big icon panel somehow smaller? It takes some 10 percent of my screen.



Is there some way to set some preferences for the uni desktop, to change sizes of icons, colors of something etc? 
I manged to change theme , but that is about all. Particularly all those black screens need some change. Are there any themes for that?

---

### Post by coffeecat on 2011-04-24
> **ottosykora said:**
> OK, tried to log out, entered ubuntu as user and selected classic, but it had no effect at all, it came back simply with the same unity screen.

Try this: kill xserver with alt-PrintScreen-K. At the login screen click on "Other". Type "ubuntu" in Username field and click on "Login". Select "Ubuntu Classic" at bottom of screen, leave password field blank, and click on "Login" again. Voila - Classic Ubuntu.

> **ottosykora said:**
> The menu at the top must be something in the unity function.

The method for disabling global menu that I posted earlier is for classic gnome panel only. In Unity, if you want to disable the global menu you have to uninstall the package indicator-appmenu. This is feasible only with a permanent installation; I doubt you'd be able to do this in the live session.

---

### Post by ottosykora on 2011-04-25
ok, this did work, thought this is kind of complex on my notebook which has no more print scr button...
But I got finally the classic at least

so far ok, also here the FF crashes when operated in the full screen mode, and got just message the nautilus crashed as well.

---

