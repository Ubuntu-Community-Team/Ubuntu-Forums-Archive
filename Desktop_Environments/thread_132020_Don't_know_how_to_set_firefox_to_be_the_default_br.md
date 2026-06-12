---
title: "Don't know how to set firefox to be the default browser."
date: 2006-02-17
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2006-02-17
Ok, here's my dilemma.

Every time I click a link in gaim, it opens up the site in konqueror. I'd prefer it to be in Firefox. I'd like it to open up a new tab in firefox with the site. Anyone know how to do it?

I had it working fine in Gnome, but since I've switched to KDE, I wasn't able to get it working.

---

### Post by souteneur3190 on 2006-02-17
in firefox
edit
prefrences
general
default browser

---

### Post by eqisow on 2006-02-17
Well since my system is currently fubar'd and I can't actually look at KDE atm... I'm doing this from memory. But it's something like Kontrol Panel ---> KDE components ---> Browser ---> type 'firefox' in box (no quotes). There may be another sub menu like default programs or KDE defaults or something like that that I'm forgetting... but it's somewhere in that area.

Edit: or maybe it works sout's way... never tried that.

---

### Post by YourSurrogateGod on 2006-02-17
[QUOTE=souteneur3190]in firefox
edit
prefrences
general
default browser[/QUOTE]
Tried it before, no go.

---

### Post by YourSurrogateGod on 2006-02-17
[QUOTE=eqisow]Well since my system is currently fubar'd and I can't actually look at KDE atm... I'm doing this from memory. But it's something like Kontrol Panel ---> KDE components ---> Browser ---> type 'firefox' in box (no quotes). There may be another sub menu like default programs or KDE defaults or something like that that I'm forgetting... but it's somewhere in that area.

Edit: or maybe it works sout's way... never tried that.[/QUOTE]
Stupid question, where's Kontrol Panel?

---

### Post by eqisow on 2006-02-17
Well, again, because my system is currently hosed I can't look and tell you... but I know you can open up a terminal and just type kcontrol.

---

### Post by YourSurrogateGod on 2006-02-17
[QUOTE=eqisow]Well, again, because my system is currently hosed I can't look and tell you... but I know you can open up a terminal and just type kcontrol.[/QUOTE]
Nah... I couldn't find what you meant.

The closest to what you were trying to describe was...
KControl -> KDE Components -> Component Chooser -> Web Browser
then check "Default Component" in the following browser (insert firefox.)

But that still didn't do the trick.

---

### Post by tagg3rx on 2006-02-17
Its located @

K -> Settings -> KDE Componets -> Componet Chooser
On the left choose Web Browser
Put a Dot on "in the following browser"
Browse your menu to internet and choose the firefox browser

Should do the trick
Too bad its not that easy to change the default file manager from konquer to Krusader

edit -- oh that didnt work?
intresting....

---

### Post by YourSurrogateGod on 2006-02-17
[QUOTE=tagg3rx]Its located @

K -> Settings -> KDE Componets -> Componet Chooser
On the left choose Web Browser
Put a Dot on "in the following browser"
Browse your menu to internet and choose the firefox browser

Should do the trick
Too bad its not that easy to change the default file manager from konquer to Krusader

edit -- oh that didnt work?
intresting....[/QUOTE]
The odd thing is that when I do make that change, the button at the bottom that says 'Apply' is inactive... weird... I'll try to do the same thing as root.

---

### Post by eqisow on 2006-02-17
I'm with tagg3rx... not sure why that doesn't work. GAIM and such still launch Konqueror after that?

Edit: instead of going through the menu to choose a browser, try just typing firefox manually. Shouldn't make any difference, but /shrug... I'm pretty much at a loss.

---

### Post by YourSurrogateGod on 2006-02-17
[QUOTE=eqisow]I'm with tagg3rx... not sure why that doesn't work. GAIM and such still launch Konqueror after that?[/QUOTE]
Yep...

On another note, I just tried running Kcontrol as root, but it wouldn't work. Here's what I've tried...
```
$ sudo kcontrol&
Password:
[4] 11651

[4]   Stopped                 sudo kcontrol
andrew@d146h110:~$ kcontrol&
[5] 11652
```
I get to the part where you have to insert your password, but it won't allow me for some reason... weird.

---

### Post by z-vet on 2006-02-17
Ok, i think i have a solution. First, a script:

```
#!/bin/sh

URL="$*"
#Path to Firefox executable, modify it to match your installation:
FFOX=/usr/lib/mozilla-firefox/firefox

FFOX_REMOTE="${FFOX} -a firefox -remote"

firefox_running()
{
    $FFOX_REMOTE "openurl($URL,new-tab)"
}

firefox_new()
{
    $FFOX $URL
}


if $FFOX_REMOTE "ping()" 2>&1 | grep "Error:" >/dev/null; then
    firefox_new;
else
    firefox_running;
fi
``` 
Save it in a file, name it like "start-firefox" or something and make it executable. This script allows you to open every link you click on in new tab of running Firefox. Then do "Alt+F2" and type 'kcontrol', press Enter.  Go to KDE Components > Component Chooser > Web Browser. There you have two choices, you need a second: "in the following browser". Click on radio button beside this option and enter there a full path to "start-firefox" script. Now "Apply" button will be active, press it and enjoy Firefox as your default browser. :)
Here's a screenshot of my kcontrol, hope it will help you:
[[IMG]http://img480.imageshack.us/img480/9362/kcontrol7ez.th.png[/IMG]](http://img480.imageshack.us/my.php?image=kcontrol7ez.png)
PS: you need to modify a path to Firefox binary in case you have it installed in non-default location. See a comment inside of my script.

---

### Post by YourSurrogateGod on 2006-02-17
I did the FF 1.5 install exactly as shown [here](https://wiki.ubuntu.com/FirefoxNewVersion).

I'm trying to figure out which directory I should pick.

---

### Post by YourSurrogateGod on 2006-02-17
Damn, I did what you suggested z-vet, no go :( . Still opens up in Konqueror.

Maybe if I try to go back to 1.0.7 and then try to update it with Automatix... hmm...

---

### Post by YourSurrogateGod on 2006-02-17
Ok, I reinstalled 1.5 with Automatix, still no go :( .

---

### Post by Adrian on 2006-02-17
I believe the problem is that Gaim is a Gnome application. 

[QUOTE=Asimon]GAIM has it's own setting which browser to use and doesn't follow KDE's settings. In Gaim choose in the menu "Tools", then "Browser" in the tree and set your browser there.[/QUOTE]

(from [this]("http://www.ubuntuforums.org/showpost.php?p=506987&postcount=5") post)

---

### Post by YourSurrogateGod on 2006-02-17
[QUOTE=Adrian]I believe the problem is that Gaim is a Gnome application. 



(from [this]("http://www.ubuntuforums.org/showpost.php?p=506987&postcount=5") post)[/QUOTE]
*bangs head against the wall*

Thank you Adrian. Works flawlessly now.

---

### Post by computerdave on 2006-03-01
in GAIM, Tools --> Preferences --> Browser on the left --> Under browser select Firefox, then select how you want the link to open in Firefox (I chose New Tab)

---

### Post by NeoChaosX on 2006-03-01
Gaim has it's own browser preferences seperate from KDE. You want to go to the Browser section of Gaim's preferences and change the preferred browser.

edit: outresponded by computerdave

---

### Post by Mis_Uszatek on 2006-03-01
Hello

I have different problem but with opera and Kontakt(I suspect that other applications would behave the same).
It is possible for me to choose an Opera as default browser, but then behaviour is very strange. If I click on link in Kontakt, content of the web_site.html is downloading to /var/... and webbrowser is opening file from /var. If I choose Konqueror, everything is different, content of the file is downloading, but Konqueror opens site, not the file from /var.

Any ideas?

---

### Post by YourSurrogateGod on 2006-06-22
[QUOTE=Mis_Uszatek]Hello

I have different problem but with opera and Kontakt(I suspect that other applications would behave the same).
It is possible for me to choose an Opera as default browser, but then behaviour is very strange. If I click on link in Kontakt, content of the web_site.html is downloading to /var/... and webbrowser is opening file from /var. If I choose Konqueror, everything is different, content of the file is downloading, but Konqueror opens site, not the file from /var.

Any ideas?[/QUOTE]
Yes, I'm having the same problem with opera. Now, my problem is that I don't even have a "Browser" option, weird.

---

