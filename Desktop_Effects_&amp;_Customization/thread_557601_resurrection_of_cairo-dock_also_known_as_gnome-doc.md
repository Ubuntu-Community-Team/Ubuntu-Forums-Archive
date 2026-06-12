---
title: "resurrection of cairo-dock also known as gnome-dock"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by marijus on 2007-09-22
everybody interested, please check out this site:

[http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/)

lots of improvement compared to former cairo or gnome dock!!!
regards!
marijus

---

### Post by amadeus266 on 2007-09-23
I checked it out. I really like the functionality and customizability but I need to brush up on my French skills.  Really good work.

---

### Post by marijus on 2007-09-23
you can change the language of the configurator to english... 
rightclick the dock 
go to cairo-dock -> configure -> all
than choose the cairo dock table

and at the very top you can switch languages between french and english!!!

---

### Post by Lord Illidan on 2007-09-23
> **marijus said:**
> you can change the language of the configurator to english... 
rightclick the dock 
go to cairo-dock -> configure -> all
than choose the cairo dock table

and at the very top you can switch languages between french and english!!!

Doesn't do anything for me. It looks good, but I don't understand french!

---

### Post by marijus on 2007-09-23
- choose english as language 

- press apply

- restart configurator

after the restart the language should be english...
this way it at least works for me..

---

### Post by Lord Illidan on 2007-09-23
No..it didn't work neither.
Are you using the deb version or did you install from source?

---

### Post by marijus on 2007-09-23
im using deb version 1.3.3
maybe you also have to restart the dock?

---

### Post by pieisgood4589 on 2007-09-23
hey there everyone. i'm new to ubuntu, and still can't install the dock. can anyone explain it to me?

the command prompt tells me that i need intltools but i don't know how to get it.....

---

### Post by marijus on 2007-09-23
download this two debs:

[http://prdownload.berlios.de/cairo-dock/cairo-dock_1.3.3_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock_1.3.3_i686-32bits.deb)
[http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_1.3.3_i686-32bits.deb](http://prdownload.berlios.de/cairo-dock/cairo-dock-plug-ins_1.3.3_i686-32bits.deb)

and install them with gdebi... no need for intltools than... :)

press alt-f2 and enter cairo-dock and press enter to start the dock

---

### Post by Lord Illidan on 2007-09-23
> **marijus said:**
> im using deb version 1.3.3
maybe you also have to restart the dock?

I did! Heck, I even restarted my pc! Still in french though. And yes, using your own debs. Can you give me a screenshot of what your configuration screen looks like, then?

---

### Post by marijus on 2007-09-23
there it is :)

these are not my debs... its the ones from the project page... :)

---

### Post by Lord Illidan on 2007-09-23
And here is mine...

---

### Post by walkerk on 2007-09-23
I also tried these weeks ago and i was unable to swicth it from french to english...

---

### Post by marijus on 2007-09-23
hmm... funny

try to check the config file in /home/username/.cairo-dock/current_theme/cairo-dock.conf

what does it say in about line 59

mine looks like this:

[Cairo Dock]
#s-[en;fr]    Language (for config windows) : /
language=en

---

### Post by Lord Illidan on 2007-09-23
I even removed them and re-installed the whole thing, still can't get english!
The language = en, same as yours, too.

---

### Post by marijus on 2007-09-23
than im afraid i cant help you :(

but its strange... as it works for me and i just tried switch it back and forth a couple of times and it always just did it...

---

### Post by Lord Illidan on 2007-09-23
I am going to try compiling it from source, perhaps that might help!

---

### Post by FuturePilot on 2007-09-23
Yes, I'm getting French too. I can't get it to change.

---

### Post by Lord Illidan on 2007-09-23
I gave up. No instructions are provided, and installing from cvs just gave me a load of silly errors. And, there's only 1 developer!

---

### Post by marijus on 2007-09-23
disregard this message

---

### Post by marijus on 2007-09-23
have you tried another theme maybe?

i just found out if using any of the preset themes i also cant change language to english...
if i use my own it works...

---

### Post by Lord Illidan on 2007-09-23
> **marijus said:**
> have you tried another theme maybe?

i just found out if using any of the preset themes i also cant change language to english...
if i use my own it works...
Can you send me your own theme?

---

### Post by Lord Illidan on 2007-09-23
How would I go about making a theme, anyway?

EDIT : And I've tried all of the preset themes. Any tips how to make a new theme, or else can you send me one?

---

### Post by fabounet on 2007-09-23
Hi there ! :-)
Thanks to Marijus who told me about this topic.
Did you try to switch en -> fr -> en ?

The conf files are in /usr/share/cairo-dock/data, so you can try to replace the conf file in your current theme with the default english one. Then, does it the language switch work ?
Also, is the theme selector in french too ?
Thanks for any info, I'll try to fix it for the 1.3.4 ;-)

Edit : @Lord Illidan's Avatar  	
Lord Illidan : a theme is the set of behaviour parameters, design parameters, plug-in parameter, launchers, and optionnaly icons, so in fact it's just the "~/.cairo-dock/current_theme" directory. You can save your current theme and switch from a theme to another simply with the theme selector, that allows you to save/charge all or part of a theme's set.

Edit2 : oh I forgot, do you have a "cairo_dock_replace_key_values (0)" message in the console when you change language ?

---

### Post by marijus on 2007-09-23
ok...
unpack it and put in folder: /home/username/.cairo-dock/themes

there should be two icons firefox and evolution
im curious if its gonna work...

---

### Post by Lord Illidan on 2007-09-23
Well, your theme worked, marijus! It's now in english!

>  Edit2 : oh I forgot, do you have a "cairo_dock_replace_key_values (0)" message in the console when you change language ?

Yes, I do.

I think I managed my way around it now, by copying the english conf to the theme directory.  Thanks for all the help everyone!

---

### Post by Lord Illidan on 2007-09-23
One last problem. I can't modify the clock at all, it seems. Whatever settings I change, even the name, it remains the same. I tried editing ~/.cairo-dock/current_theme/plug-ins/clock/clock.conf

but, it's useless.

---

### Post by fabounet on 2007-09-23
@ Lord Illidan : the clock is a little buggy (you have to configure it one time to make it start) I've corrected that already so it will be in the next version.
But I think you should be able to change its name or theme. Is the conf file of the clock writbable ?

---

### Post by eitan_a on 2007-10-28
Is this just an app launcher, or taskbar as well?

---

### Post by Pabx on 2007-10-28
Thank you! Ive tried it , but link its not working right now...

if someone could upload it ...

---

### Post by ebeckhusen on 2007-10-28
Yeah, I've been trying to get the debs from their site for the past 2 days, but something must be overloading their servers or something.  So, if anyone can do so, please upload them?

---

### Post by zyg0t3 on 2007-10-28
Is there an alternate site that the files are hosted at because [http://prdownload.berlios.de](http://prdownload.berlios.de) keeps timing out. And i am unable to retrieve any files.

Why not have them hosted here at the repositories?

---

### Post by zyg0t3 on 2007-10-29
Ok with a little bit of homework i've figured out how to compile the source using the helpful tutorial at [https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

basically you do this

```
cvs -z3 -d:pserver:anonymous@cvs.cairo-dock.berlios.de:/cvsroot/cairo-dock co cairo-dock
```

and this 

```
cvs -z3 -d:pserver:anonymous@cvs.cairo-dock.berlios.de:/cvsroot/cairo-dock co plug-ins
```

then 

```
sudo apt-get install build-essential libcairo2-dev libgtk2.0-dev librsvg2-dev libglitz1-dev libcairo2 librsvg2-2 libglitz1 
```

move to the newly created directory (cairo-dock first) and type :

```
autoreconf -isvf && ./configure --prefix=/usr && make 

sudo make install 
```

but you really should check out that link, it explains it in depth.

This version of cairo-dock is really nice. I prefer it over AWN or kiba-dock. Smooth and highly configurable.

Here's a shot.
[[IMG]http://img255.imageshack.us/img255/9301/screenshotde2.th.png[/IMG]](http://img255.imageshack.us/my.php?image=screenshotde2.png)

---

### Post by Hhkmac on 2007-10-31
Cheers for this, Dock works great!

I've had huge issues with Gutsy and Compiz, etc.

Been wanting a pretty dock like my dock on XP.... and now I've got one... still got a bit of tinkering to do, but cheers!!!

:guitar:

---

### Post by ubuntios on 2007-11-01
Hi guys ,

I just download the cairo-dock 1.3.8     from [http://developer.berlios.de/projects/cairo-dock/](http://developer.berlios.de/projects/cairo-dock/)
I install it and works just  fine , you can change all the settings on the dock and I'didn't have any problems what so ever . 
I think the last version is very  stable and is worth to install it !

---

### Post by zyg0t3 on 2007-11-02
Yeah, call me weird but most of the time i like to compile from src anyway. Usually it'll be the bleeding edge release that isn't packaged yet into a .deb. And maybe i like to be super-geeky. :)

---

