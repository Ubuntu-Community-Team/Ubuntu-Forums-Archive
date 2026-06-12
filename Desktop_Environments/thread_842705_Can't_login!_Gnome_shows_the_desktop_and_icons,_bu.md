---
title: "Can't login! Gnome shows the desktop and icons, but never the panels"
date: 2008-06-27
forum: Desktop Environments
---

### Post by Digimer on 2008-06-27
I've got a fresh install on Ubuntu on my Thinkpad t40. It's a fresh install because Ubuntu had recently decided to use PIO mode for my HDD and wouldn't let me change it back. Now the drive is working fine, but after a few reboots (updating the system and restoring from backup) Gnome never fully loads!

This is very frustrating!

I've created a new user and deleted everything from my main user account but it's always the same story; I enter my name and password, I hear the login sound and my desktop background and desktop icons load but then nothing more. The panels never load. >_<

I'm supposed to leave for vacation in a couple of hours. Any quick replies would be *very* appreciated!

Digi

PS - Hint? It takes two tries at pressing <ctrl> + <alt> + <backspace> to get gdm to restart.

---

### Post by Digimer on 2008-06-27
Additional;

Gnome failsafe is no better, and I've rebooted several times since clearing stuff out.

---

### Post by mptpro on 2008-07-02
same problem here
running hardy
dell vostro 1500

---

### Post by Digimer on 2008-07-07
I never found an answer, save to reinstall. 

Bah. Makes me want to go back to Debian... old as it is.

Digi

---

### Post by HotCupOfJava on 2008-07-07
Well - this sounds dumb, but I have noticed that the "autosizing" for certain monitors doesn't always work correctly. I have had to adjust the display on my monitors berfore because the bars at the top and bottom of the desktop will be drawn off-screen. In my old comp running Xubuntu I had to change the screen resolution under the display settings to get the bottom bar to show. Don't know if this is related to your problem or not.

---

### Post by Digimer on 2008-07-08
Hiya,

  Not in this case, I am afraid. I had desktop icons near the middle, and they never appeared. Also, I couldn't right-click -> create new launcher. Thanks for the suggestion though!

  As an aside, I saw another thread complaining of the same issue and a posted commented that 'gnome-panel' had been removed and needed to be reinstalled. Not sure if this was my problem, but thought I'd mention it here in case someone has the same trouble down the road and finds this while searching.

Digi

---

### Post by kaola_linux on 2008-07-08
hey guys, I have the same Exact problem also..Try Looking at the general help part of the forums...I've posted it there...

Try this:
in your terminal type "gnome-panel"
or if it does not "sudo gnome-panel"

I've tried this 2 but it doesn't help on my sit..Can a GURU help us here...I'm about to reinstall but the risk is so bad for my part because I don't have my own internet I'm just sharing...

---

### Post by Digimer on 2008-07-08
What happens if you open another terminal (ctrl+alt+f1, enter your name and password) and then reinstall gnome-panel? Try typing:

```
sudo apt-get install gnome-panel
```

Then restart GDM with:

```
sudo /etc/init.d/gdm restart
```

Digi

---

### Post by kaola_linux on 2008-07-08
Better try this out...this error gives me a headAche!!!:mad:

---

### Post by kaola_linux on 2008-07-08
> **Digimer said:**
> What happens if you open another terminal (ctrl+alt+f1, enter your name and password) and then reinstall gnome-panel? Try typing:

```
sudo apt-get install gnome-panel
```

Then restart GDM with:

```
sudo /etc/init.d/gdm restart
```

Digi

Using ```
sudo apt-get install gnome-panel
``` didn't worked for me..it said i already have the latest version...

---

### Post by Digimer on 2008-07-08
Bah, sorry then. That was what I saw suggested in another thread.

What if you try:

```
sudo apt-get install --reinstall gnome-panel
```

Failing that, I am back to being lost.

Digi

---

### Post by phoenix_abhi on 2008-07-08
go to usr/bin search for gnome panel and double-click.It will restore the panel after a restart

---

### Post by Digimer on 2008-07-08
> **phoenix_abhi said:**
> go to usr/bin search for gnome panel and double-click.It will restore the panel after a restart

Given that the other poster is having the same problem I had, they may want to try:

```
sudo /usr/bin/gnome-panel
```

Digi

---

### Post by phoenix_abhi on 2008-07-08
Is that helped ?

---

### Post by sayakb on 2008-07-08
A simple **killall gnome-panel** at a terminal should bring up the panel. Goto System->Preferences->Sessions->Current Session to see if the **Style** of gnome-panel is set to **Restart.**

---

### Post by dayneman1 on 2008-07-08
I've been having this problem on my laptop for some time now, but the panels would eventually load after a short time.  This is a fresh install on my parents computer and every thing was going fine until this.  Now i have no access to the panels or the command terminal (its alt+F2...right?).  I'm so close to just saying #$@! it and reinstalling windows xp.

---

### Post by kaola_linux on 2008-07-09
> **Digimer said:**
> Bah, sorry then. That was what I saw suggested in another thread.

What if you try:

```
sudo apt-get install --reinstall gnome-panel
```

Failing that, I am back to being lost.

Digi

     I even tried reinstalling the desktop but it didn't worked also...I'll try this at home.

     Can someone out there know my error...My guess is that maybe my Gnome is broken because I've installed something from here: [http://www.gtk.org/](http://www.gtk.org/)

     And guys, mine is Ubuntu 8.04 AMD64 please help me...Can I just reinstall the Gnome again without altering the programs I'd installed??

    Thanks....

---

