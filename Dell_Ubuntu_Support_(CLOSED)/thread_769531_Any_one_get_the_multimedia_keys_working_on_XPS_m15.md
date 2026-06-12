---
title: "Any one get the multimedia keys working on XPS m1530 with hardy?"
date: 2008-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spacesearcher on 2008-04-26
I have volume up down and mute working, and the mediadirect button opens amarok but I haven't figured out how to get the play/pause, stop, fwd, back buttons working. :/ I couldn't get it working in gusty and still can't in hardy. has any one found a fix for this yet?

---

### Post by Vaun on 2008-04-27
They all work fine with Hardy.  The eject button needs a few tweaks due to the way a cd/dvd is mounted.  All others work great :)

---

### Post by crash91 on 2008-04-27
Easy, just go to System>Preferences>Keyboard shortcuts
For play/pause, click the shortcut thing and then press the play button, do this for the rest of the keys as well. This worked perfectly on my Dell Inspiron 6400.

---

### Post by spacesearcher on 2008-04-27
I tried the keyboard shortcuts and its not working for amarok it will work for rythmbox but not for amarok. I tried this [http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/) and I cant get the media keys to do any thing. When i put in <Control><Alt><Shift>f in into the run_command_1 and under key binding commands in command_1 i put amarok -f to make it play next song it works but if i type 0x99 (my next button) into the run_command_1 and leave the command in command_1 the same it doesn't work. am I putting the correct key into the run_command_1 box I don't have any of these >< just 0x99 like it said in the keyboard shortcuts menu. Or is there some other way to put it in so it recognizes that I am pushing that key? 

I also tried putting different commands in like firefox when it was set to be launched by a media key and it still didn't work but if I used one from the rest of the keyboard it did work. under the keyboard shortcuts menu I have all the keys disabled that I am using.

---

### Post by crash91 on 2008-04-29
I remember i used to use a software for this on Fedora previously, i forgot the name but im googling right now. Will edit if i find it.

EDIT: Found it! Hope this helps you! I remember that you have to set it to run each time you log in so just go to System>Preferences>Sessions and add lineak to it.
[http://lineak.sourceforge.net/](http://lineak.sourceforge.net/)

I found it on this forum:[http://www.linuxquestions.org/questions/linux-hardware-18/media-buttons-on-a-dell-inspiron-9400-566932/](http://www.linuxquestions.org/questions/linux-hardware-18/media-buttons-on-a-dell-inspiron-9400-566932/)

---

### Post by spacesearcher on 2008-04-29
it works!!! 
so this is what I did if any one else wants to know if they are having the same problem.

Went into synaptic and installed lineaked
then in terminal sudo gedit
opened lineakkb.def in /etc
scrolled down to the bottom added 

```
[DXPS]
brandname = "Laptop/notebook"
modelname = "Dell XPS and Inspiron 9100"
[KEYS]
Play = 162
Previous = 144
Next = 153
Stop = 164
[END KEYS]
[END DXPS]

```
then I saved

 I got that from [http://ubuntuforums.org/archive/index.php/t-15780.html](http://ubuntuforums.org/archive/index.php/t-15780.html)
it originally had volume controls but mine are working so I didn't want to mess with that. 

then tested it with Lineakd -l 
I found it on the list at the end of the D's so now we know its there

Now I typed: lineakd -c DXPS

I tried to install klineakconfig from synaptic but it didn't work so i did a sudo apt-get install klineakconfig

then ran it: klineakconfig

A little tux icon appeared in the upper right corner I clicked it. and a window came up where I could double click the button I wanted and put a custom command like amarok -previous

after I set this up I clicked apply and it started to work.
it wont start when you log back in. someone correct me if I am wrong but I think to get it to work all the time you have to log out then back in type  lineakd & in terminal. then you can close that window. then go into system>preferences>sessions and add the command lineakd to the startup. now when ever you login it will automatically start up. If this doesn't work disable the autostart up thing for lineakd in sessions. log out then login then run klineakconfig re-do your commands then run lineakd & in terminal then re-enable the auto startup thing.

it also reset my default media player so I had to go back into preferred applications and set it back to amarok.

---

### Post by collinsl on 2009-01-23
Sorry to revive this, but I can't get the Mute button working on my XPS M1530. All the other media buttons work and as far as I know the button is recognized in keyboard options.

Also, this is the first time I have looked into Linux properly, so full instructions please!

Thanks,
Lloyd Collins

---

### Post by Strongman332 on 2009-02-13
same problem bump

---

### Post by spacesearcher on 2009-02-14
mine worked fine out of the box did you change anything?

---

### Post by jespdj on 2009-02-15
> **crash91 said:**
> Easy, just go to System>Preferences>Keyboard shortcuts
For play/pause, click the shortcut thing and then press the play button, do this for the rest of the keys as well. This worked perfectly on my Dell Inspiron 6400.
This worked for me on the XPS M1530 - no special software necessary.

---

