---
title: "gutsy compiz = no window borders"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by Digitallysick on 2007-09-27
I have no window borders with compiz under gutsy, i can't figure out why

---

### Post by wilberfan on 2007-09-27
> **Digitallysick said:**
> I have no window borders with compiz under gutsy, i can't figure out why

I JUST got Gutsy beta up and running, figured out why I couldn't get the nvidia driver working (yay), but I, too, have no window borders...

I checked the xorg.conf, and I DO have that "    'Option  "AddARGBVisuals"	"True" ' in there, so I'm stumped.  :confused:

[edit]  This should have probably gone in the "Gutsy" forum, sorry...   In fact there's already a thread or two there:  [http://ubuntuforums.org/showthread.php?t=556796](http://ubuntuforums.org/showthread.php?t=556796)

---

### Post by Digitallysick on 2007-09-27
Now i have a different issue, compiz loads, i get a random emerald theme, when i got emerald , i see no themes, so i added the non gpl themes from subversion, and they show up, but when i select them nothing happens, its as if emerald is just dead?

---

### Post by teruokun on 2007-09-28
You will need to restart emerald to make the chosen theme appear.  Hit alt+F2 and type

emerald --replace

and that should do it.  That's what I had to do to switch themes

---

### Post by madnux on 2007-09-29
> **teruokun said:**
> You will need to restart emerald to make the chosen theme appear.  Hit alt+F2 and type

emerald --replace

and that should do it.  That's what I had to do to switch themes

That's work!

Thanx!

:lolflag:

---

### Post by ProfKaramba on 2007-10-02
and how did you fix the window borders??

---

### Post by Rupertronco on 2007-10-02
> **ProfKaramba said:**
> and how did you fix the window borders??

> **teruokun said:**
> You will need to restart emerald to make the chosen theme appear.  Hit alt+F2 and type

emerald --replace

and that should do it.  That's what I had to do to switch themes

Read.

---

### Post by ProfKaramba on 2007-10-02
When I enable visual effects I can't run nothing... I press Alt+F2 and nothing happens :x

---

### Post by Rupertronco on 2007-10-02
All Alt + F2 does is bring up the run dialog, for some reason maybe your visual effects mapped over that key binding. 

Any command put in an Alt + F2 box can be run in a terminal, and if you wan that command to keep running, even after you've closed the terminal put an ampersand (&) behind the command.

---

### Post by ProfKaramba on 2007-10-02
I tried to put it into a terminal console and when I press enter, nothing occurs. Doesn't execute the command. Stays waiting for more parameters or something... :x

---

### Post by Digitallysick on 2007-10-02
I ended up giving up on gutsy and just going back to fawn with no compiz, it gives me alot of problems even though i have a good graphics card

---

### Post by wilberfan on 2007-10-02
Well, here's how I got my window borders back:

I did a CLEAN install of Gutsy!

Seriously, that did the trick.   I hung out in the #ubuntu+1 IRC room, and had a very patient guy try and help me with this problem.    We couldn't solve it under my UPGRADE from Feisty to Gutsy.   He thought it must have something to do with having used a script, or something?

I remembered that that's exactly how I had installed Fusion under Feisty!   There was a script called [CF_Installer-Updater_v.2.sh]("http://ubuntuforums.org/showthread.php?t=508769") that I used...

Fusion is a little harder to get configured than I might have guessed, given all the fanfare about it being 'included' in Gutsy....     Maybe it'll be easier come the final release?   It wasn't difficult--just a little more involved than I would have predicted.

Still, borders are back--and the cube is rotating!  :guitar:

---

### Post by Digitallysick on 2007-10-02
i think your right, i had used those same scripts, it must become borked from the upgrade, gutsy has compiz built in

---

### Post by peterdm on 2007-11-19
Being new to ubuntu, coming from opensuse and gentoo, I notice the same problems in every distro ;-)

In case of nvidia cards, try the following:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

This worked for me!

If you still have no window borders, make sure you have the window decorations enabled.
If you don't have the compizconfig mgr installed, do it like this:

sudo apt-get install compizconfig-settings-manager

Then open System->Preferences->Advanced Desktop Effects Settings.
Find "Window Decoration" in the "Effects" section and make sure it is checked.

If you still have no window decorations, click on the "Window Decorations" icon and in the "Command" field type:

gtk-window-decorator --replace

Note that this last command is gnome-specificand you should try it out from a command prompt first to see if it works.


Regards,

Peter

---

### Post by slash123 on 2007-12-06
I noticed this happening too often for my liking.

My workaround - created a launcher in the taskbar (which remains active)
Command: emerald --replace
Name: Redraw Borders..

Whenever the borders disappear, I jut click on this launcher (I have positioned it next to the User Switcher) and everything is back to normal.

Hope this helps :)

ML

---

### Post by nrfool on 2007-12-30
thanks peterdm. The sudo line fixed my problem!

---

### Post by nardis_Miles1 on 2008-01-02
I am running gutsy on a 32 bit box with a GeForce 6200 card. I have installed the proprietary nvidia driver. I have followed the suggestions here but I still don't get window decorations for new windows, although, when I restart firefox, I get decorations on the windows from previous sessions. compiz is running, as I get wobbly windows for those that retain their decorations.

---

### Post by nardis_Miles1 on 2008-01-02
Just to clarify, it turns out that I have a fully functional compiz in KDE, but not gnome.

---

