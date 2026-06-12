---
title: "Menu Bar"
date: 2012-05-09
forum: Desktop Environments
---

### Post by ramakanta on 2012-05-09
yesterday i have install ubuntu 12.04. previous was 10.04. but in 12.04 there is no menu bar displayed  for open various program . is there any setting to display menu bar ?? please help me.
thank you.
:confused:

---

### Post by ubuntu27 on 2012-05-10
Ubuntu 12.04 uses Gnome3 + [Unity Shell]("http://unity.ubuntu.com/about/"). It doesn't have the "place" (forgot the name) where [ONLY] current running user application are.

The Unity Launcher which is located to the left of the screen is where your opened applications and windows are displayed. It also serves as a Launcher in which you can "pin" or "lock" an Launcher Icon.

Alternatively, you can install Gnome-Fallback that will allow you to use a desktop environment that is similar to Gnome 2 that you are used to.

[GNOME Classic in Ubuntu 12.04: It’s Like Nothing Ever Changed]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed/")

---

### Post by zombifier25 on 2012-05-10
If you are looking for application menu (like File, Edit, ...) it's located at the very top panel of the screen.

I'm posting this because OP didn't clarify on what type of menu he is looking for.

---

### Post by ubuntu27 on 2012-05-10
Oh, right! The original poster might have been talking about the Global Menu.

@ramakanta: Here are some guides that could help you out explore or familiarize yourself with Ubuntu 12.04:
[URL="http://spreadubuntu.org/en/material/brochure/1204-poster"]
Ubuntu 12.04 Poster[/URL] (Mini guide). Download the PDF ;-)
[URL="http://ubuntuguide.org/wiki/Ubuntu_Precise"]
Ubuntu Guide[/URL]

Also:
> **josephmills said:**
> open Ubuntu Software Center and enter [I]ubuntu book 
[/I]


Give the new Desktop Environment (Gnome 3 + Unity Shell) a chance.
If you think that it is not for you, then try:

[How to return to classic Gnome in Ubuntu]("http://www.psychocats.net/ubuntu/classicgnome")

---

### Post by ramakanta on 2012-05-15
My means in screen-shot..
 that given here.

---

### Post by ckop64 on 2012-05-15
> **ramakanta said:**
> My means in screen-shot..
 that given here.

The menu bar can be displayed by hovering your mouse over the top panel. Alternatively, you can use the HUD, which is basically a wrapper around the menu system. That can be displayed by pressing Alt on your keyboard. There you can search the menu entries. Activation of an entry is done by pressing Enter (or Return) or by clicking on the respective entry.

EDIT
Forgot to mention, that the HUD activation key (Alt) can be rebound in the CCSM. In case you want that install "CompizConfig Settings Manager" from the software centre, or "ccsm" if you prefer the command-line approach.

---

### Post by zombifier25 on 2012-05-15
> **ramakanta said:**
> My means in screen-shot..
 that given here.

Unity doesn't have that kind of menu anymore. Simply click the first button of the left panel and search for whatever apps you want to launch there.

---

### Post by TREESofRIGHTEOUSNESS on 2012-05-15
> **ramakanta said:**
> My means in screen-shot..
 that given here.
check out this one
[https://launchpad.net/cardapio](https://launchpad.net/cardapio)

the code to install it is
```
sudo add-apt-repository ppa:cardapio-team/cardapio-ppa && sudo apt-get update

```
```
sudo apt-get install cardapio
```

It is a menu and it is different but it should help until you figure out the dash

---

### Post by ramakanta on 2012-05-15
then where to find *[COLOR=green]Place[/COLOR]* and *[COLOR=green]System[/COLOR] *tab. please help me .
thank you.

---

### Post by ckop64 on 2012-05-17
> **ramakanta said:**
> then where to find *[COLOR=green]Place[/COLOR]* and *[COLOR=green]System[/COLOR] *tab. please help me .
thank you.

They are gone. Places is the third "lens" in the Unity dash (See screenshot). System settings can be found either in the launcher, or (if you have removed it) can be found using the search bar in the dash, or under the session management indicator (top right corner).

---

### Post by TREESofRIGHTEOUSNESS on 2012-05-17
actually I think you really want to
```

sudo apt-get install gnome-session-fallback

```Logout and choose the "Gnome  Classic" session
You'll see 
'Applications' and 'Places'
'System' is gone and contained in 'Applications'
to move stuff around and change the panel is WAY different.
Alt plus right click (or Super + Alt + Right click if you are using Compiz)

---

### Post by diesch on 2012-05-17
If you just want a simple menu have a look at [ClassicMenu Indicator](http://www.florian-diesch.de/software/classicmenu-indicator/)

---

### Post by j8a on 2012-05-18
I installed Ubuntu 12.04 and the global menu bar does not appear. 
I run the following and restart 
sudo apt-get remove appmenu-gtk appmenu-gtk3 appmenu-qt 
Then 
sudo apt-get install appmenu-gtk appmenu-gtk3 appmenu-qt
Restart again but nothing happend

---

