---
title: "Language support (en_NZ + de_CH + pt_PT)"
date: 2004-12-15
forum: Desktop Environments
---

### Post by swerner on 2004-12-15
I have Ubuntu (Warty) installed and running just fine for myself. However, I want to give Ubuntu to someone else (a total newbie to computers) who's native tongue is Portuguse, but lives in Switzerland. He has Mandrake set up and running, but I prefer to give support for Ubuntu, since I have it on my desktop. So I want him to be able to switch between three languages: English (for installation, en_NZ), German (de_CH) and Portuguse (pt_PT).
So I'm testing the configuration on my computer. I installed Ubuntu for my native tongue "en_NZ" and I have changed the locale to "de_CH" using
```
sudo dpkg-reconfigure locales
```
But this does not seem to change the language settings, everything is still in English. I tried a log-out, and a reboot, but still everything is in English.
Am I missing some langauge packages?

Thanks for your support.

---

### Post by jobezone on 2004-12-15
I've installed ubuntu in portuguese, pt_PT, and about 95% of gnome and applications are translated. In the install process I chose portuguese as my language(or as my region/country? I can't remember), and it was automatic from then on.

---

### Post by swerner on 2004-12-15
Are you able to switch between langauges, such as english and portuguse? If you can, how do you?

---

### Post by burlap on 2004-12-15
I've had some problems with this myself (pl_PL + en_US + es_ES) and I've posted on the forum, but there was no answer...

However, I have this more less working. Logging out did not help for me either, so I posted on the forum and swithed off my computer. When I switched it back on and logged in with Spanish (default is Polish) - there was Spanish. Ergo: you have to reboot! (Although it seems strange, but there was no other solution for me). 

Why more less? Some apps remain in the previous language when I log in with a new language (mostly panel applets but you can see them all the time and this is really annoying to have date in a different language...). 

Also - exporting LANG directly in the terminal does not work (I have posted this problem, no answer either).

---

### Post by mrosenlof on 2004-12-15
I took the standard install, added Japanese locales and rebooted.  After logging in, most of the desktop applications now had user interfaces in Japanese.  Shell utilities like 'top' 'ls' 'df' and so on are still in English.

To change the language of the desktop applications, the process that starts them up has to have ITS environment set for the language. 

I also have a shell script for when I'm in Japanese and want to run a particular application in English.  I had to change more than the LANG and environment variable for it to work correctly.  I'll try to remember to post it when I get home.  That may give some more clues about the correct environment setup.

---

### Post by mrosenlof on 2004-12-15
my 'do this command in English' script is a single line text file in my PATH that has the following line

LC_ALL=en_US LANGUAGE=en_US GDM_LANG=en_US XMODIFIERS= LANG=en_US $*

The file is called 'en' so I enter a command like

   en xcdroast

and it runs xcdroast and I get English menus.

if you're in a terminal window you can look for these parameters set by a command like

echo $LC_ALL

or

echo $LANG

when you choose a new language at the gdm screen, these environment variables should change.

But like I said in my last post, shell commands, like 'ls' or 'top' will still be in English.  But you should find applications like 'gedit' or 'xmms' come up in your chosen language.

This is all assuming the chosen language is supported!  I've only looked at English and Japanese.  Haven't tried German, Portugese or Kiwi.

hope this helps!

---

### Post by mrosenlof on 2004-12-15
take a look at the man pages for locale.gen and locale-gen

they might help too.

good luck.

---

### Post by burlap on 2004-12-16
> my 'do this command in English' script is a single line text file in my PATH that has the following line

LC_ALL=en_US LANGUAGE=en_US GDM_LANG=en_US XMODIFIERS= LANG=en_US $*

Thank you for this nice script - I wouldn't gess you have to set so many variables... (instead of simply "LANG=" as it worked for me in Aurox (redhat/fedora)). With bash completion it works really great!

---

### Post by jobezone on 2004-12-16
[QUOTE=swerner]Are you able to switch between langauges, such as english and portuguse? If you can, how do you?[/QUOTE]

I don't need this feature, so I've never tried it(and am not in ubuntu right now to do it). I do notice that in GDM there is an option to start gnome in portuguese or in english, but I didn't try it. Maybe the other replies helped you.

---

### Post by josel on 2004-12-18
I solved this problem for me by running
```
sudo dpkg-reconfigure locales
```
and selecting the locales i wanted - in my case danish and portuguese and can now run apps in the  languages of my desire - well actually only gtk apps.
For all gtk/gnome apps just select the language in the language menu in GDM and you're done.
If you use KDE, you can use kontrolcenter to control the language. 

Single GTK/Gnome apps kan be run in the desired language like this
```

jose@pollux:~ $ LANGUAGE=da_DK oowriter
jose@pollux:~ $ LANGUAGE=pt_PT oowriter

```
The above is done when running gnome in english language and getting oowriter in danish  or portuguese.
So making a little script you could easily choose the language of your desire with a single click.

I'm so far not able to use the same trick with KDE apps but i havent tryed very hard since i normally use KDE

---

