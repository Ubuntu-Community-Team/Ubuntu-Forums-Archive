---
title: "Gaim IM windows issue"
date: 2005-11-21
forum: Desktop Environments
---

### Post by prizrak on 2005-11-21
I have searched high and low on this forum and have found no solution :) The problem is that my Gaim IM windows don't remember their settings, by settings I mean the height and width of the window as well as the size of the part where you type your message. It's not a very serious problem but definetly an annoying one. I was just wondering if there is a way to fix it or if it's just a Gaim/GTK issue. In case it can't be fixed can someone advise an IM program that can handle AIM/ICQ protocol (aside from the official client) (Not Kopete:) ).

---

### Post by manicka on 2005-11-21
I don't think there is a work around for that problem. I find it worth putting up with though. 
Gaim is da bomb :)

---

### Post by jrib on 2005-11-21
Mine do.  If I open an IM windows resize it, close it and then open a new one it will be the resized size.  If I close GAIM and start it again they will remain the resized size.  I don't know if this is lost after a reboot.

If yours don't it is probably because I have installed devilspie.  Devilspie let's you create config files that control the size/location (and other attributes) of windows you open.  I was currently only using it to have xchat and aim to be set to "always on the visible desktop" as soon as I opened them but since your windows are not remembering sizes and mine are, it may also be providing that functionality for me (even though I haven't created config files for aim window sizes; it just remembers the previous ones).  

So I'd suggest you give devilspie a try and see if it works for you.  There is a version available in the universe repo.  I am using a more recent version that I compiled however and the program has been completely rewritten after the version in the repos was released.  If you don't feel comfortable compiling devilspie then you should try the repo one first and if it doesn't work for you, I can step you through compiling the more recent one.

To run the program you just type "devilspie" in a terminal.  You should add it to your startup (system > preferences > sessions > startup).

Hope it works out!

---

### Post by prizrak on 2005-11-21
[QUOTE=_jason]Mine do.  If I open an IM windows resize it, close it and then open a new one it will be the resized size.  If I close GAIM and start it again they will remain the resized size.  I don't know if this is lost after a reboot.

If yours don't it is probably because I have installed devilspie.  Devilspie let's you create config files that control the size/location (and other attributes) of windows you open.  I was currently only using it to have xchat and aim to be set to "always on the visible desktop" as soon as I opened them but since your windows are not remembering sizes and mine are, it may also be providing that functionality for me (even though I haven't created config files for aim window sizes; it just remembers the previous ones).  

So I'd suggest you give devilspie a try and see if it works for you.  There is a version available in the universe repo.  I am using a more recent version that I compiled however and the program has been completely rewritten after the version in the repos was released.  If you don't feel comfortable compiling devilspie then you should try the repo one first and if it doesn't work for you, I can step you through compiling the more recent one.

To run the program you just type "devilspie" in a terminal.  You should add it to your startup (system > preferences > sessions > startup).

Hope it works out![/QUOTE]

Thanks for the idea the devilspie from the repo doesn't want to start it can't load the theme, says the file devilspie.xml doesn't exist. I'll try compiling it if you point me in the direction of the site that has it :)

---

### Post by jrib on 2005-11-21
[QUOTE=prizrak]Thanks for the idea the devilspie from the repo doesn't want to start it can't load the theme, says the file devilspie.xml doesn't exist. I'll try compiling it if you point me in the direction of the site that has it :)[/QUOTE]

[http://www.burtonini.com/blog/computers/devilspie](http://www.burtonini.com/blog/computers/devilspie)

---

### Post by linkunderscore on 2005-11-21
What window manager/ DE are you using?

---

### Post by prizrak on 2005-11-21
D'oh! I use Gnome on Ubuntu Breezy.
I'm having issue with the compiling. 
This is the error I get 
checking for WNCK... configure: error: Package requirements (glib-2.0 >= 2.6
        gdk-2.0
        libwnck-1.0 >= 0.17) were not met.
Couldn't find the glib package in the repos and also not sure what packages it wants exactly

---

### Post by jrib on 2005-11-21
[QUOTE=prizrak]D'oh! I use Gnome on Ubuntu Breezy.
I'm having issue with the compiling. 
This is the error I get 
checking for WNCK... configure: error: Package requirements (glib-2.0 >= 2.6
        gdk-2.0
        libwnck-1.0 >= 0.17) were not met.
Couldn't find the glib package in the repos and also not sure what packages it wants exactly[/QUOTE]

try libwnck-dev
I also have libglib2.0-dev installed

---

### Post by prizrak on 2005-11-21
well it quit at compile time because it couldn't open some file that was ironically enough supposed to be one of the ones that were included. Oh well I guess I'll just wait for the newer version to come out since devilspie doesn't like me :)

---

### Post by jrib on 2005-11-22
[QUOTE=prizrak]well it quit at compile time because it couldn't open some file that was ironically enough supposed to be one of the ones that were included. Oh well I guess I'll just wait for the newer version to come out since devilspie doesn't like me :)[/QUOTE]

I can give you my .deb if you'd like to try it

---

### Post by prizrak on 2005-11-22
[QUOTE=_jason]I can give you my .deb if you'd like to try it[/QUOTE]
If there is an easy and painless enough way to get it (for both of us) then sure. Although I do have doubts whether it would work, but heck worth the try :)

---

### Post by Wolki on 2005-11-22
[QUOTE=prizrak]Thanks for the idea the devilspie from the repo doesn't want to start it can't load the theme, says the file devilspie.xml doesn't exist. I'll try compiling it if you point me in the direction of the site that has it :)[/QUOTE]

You have to create a .devilspie.xml file; it contains the configuration Devil's Pie will use. I've written a (sub-optimal, but long) guide here: [http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

Gaim seems to remeber size automatically here, but not position. It shouldn't be too hard to do that with devilspie, though.

[edit] a bit unclear here... it shouldn't be too hard to have it use a certain position, remembering isn't that easy.

---

### Post by jrib on 2005-11-22
[QUOTE=prizrak]If there is an easy and painless enough way to get it (for both of us) then sure. Although I do have doubts whether it would work, but heck worth the try :)[/QUOTE]

[http://www.sas.upenn.edu/~ribeiro/ubuntu/devilspie-0.14_0.14-1_i386.deb](http://www.sas.upenn.edu/~ribeiro/ubuntu/devilspie-0.14_0.14-1_i386.deb)

let me know if it works

---

### Post by prizrak on 2005-11-22
Thanks Wolki and Jason. 
Jason, I didn't need your .deb Wolki's How-to worked quite well with the older version found in the repositories.
Wolki, your HOW-TO is actually very good, it might be a bit confusing to the GUI people but not very hard to follow :)

I only have one further question, how do I get all the properties of the window? I can get it to be the width and height that I want it to be but the middle bar (one that separates part where you type messages and where you receive them) still sits wherever it wants to.

---

### Post by Wolki on 2005-11-22
[QUOTE=prizrak]Wolki, your HOW-TO is actually very good, it might be a bit confusing to the GUI people but not very hard to follow :)[/quote]

Thanks. And I'm already working on that problem ... :)

> I only have one further question, how do I get all the properties of the window? I can get it to be the width and height that I want it to be but the middle bar (one that separates part where you type messages and where you receive them) still sits wherever it wants to.

Hm... Basically, you can't set that with Devil's Pie, because that is an issue of the application and not the window manager. The interesting thing is that gaim seems to perfectly remember the location of the middle bar here, on my (pretty standard) Breezy install. :-/ Not sure why it doesn't on yours... could be a gaim settings issue, or maybe a plugin? I installed some of the additional gaim packages, it could have to do with that...

---

### Post by jrib on 2005-11-22
[QUOTE=prizrak]Thanks Wolki and Jason. 
Jason, I didn't need your .deb Wolki's How-to worked quite well with the older version found in the repositories.[/QUOTE]

cool, glad it worked out for you.  Like Wolki said above, my gaim seems to remember the middle bar setting as well.  Not sure what it could be.

---

### Post by prizrak on 2005-11-22
Yeah it's weird, I got a fairly standard Breezy myself, weird thing is that when my other machine had XP on it I had the same exact problem GTK doesn't like me :). Thanks for your help guys :)

---

