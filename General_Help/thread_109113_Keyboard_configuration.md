---
title: "Keyboard configuration"
date: 2005-12-27
forum: General Help
---

### Post by ubuntuubuntu on 2005-12-27
I choosed to install Ubuntu in English, now I can't type the following, which I need (characters from Portuguese):
á,é,í,ó,ú
à
â,ê,ô
ã,õ

(I copied these characters from a website).

How do I configurate my keyboard in order to be able to use these characters?

---

### Post by anil_robo on 2005-12-27
Please see my tutorial on non-English languages [here.]("http://www.ubuntuforums.org/showthread.php?t=102778")
Just assume Portugese wherever I said Hindi. It should help you. Do let me know if it worked for you.

---

### Post by ubuntuubuntu on 2005-12-29
It didn't work. I want to type in Portuguese. I did the following, as said in your tutorial:
"4. If you want to type in Hindi characters, you have to choose keyboard layout as "India". To do that, go to System-->Preferences-->Keyboard and go to the layout tab. There, click ADD and select India from the country list. Don't expand the list - Hindi is not listed there. If you select India everything should be fine. Now make this layout default by activating the checkmark in front of its name in the layout tab. Close this screen. Try typing a text document in gedit and you'll see that now you can type in Hindi too!"

But the layout for Brazil is NOT the layout of my keyboard. My keyboard is U.S. English.

---

### Post by Icebear on 2005-12-29
I am a very Newbie and I have to be in windows for the net::( 
so this is out of my memory

But I Think you got to system, preferences, keyboard, and choose  Portuguesel then you have then you change to the keyboard layout buy hitting both "alt" keys. Or you can go  to system, preferences, keyboard and go to the next option in the top list then choose group control and then choose what keys can change the keyboards. If you want you can then go the led section in the same window and make a led light comes on when you change keyboards

---

### Post by ubuntuubuntu on 2005-12-30
[QUOTE=Icebear]I am a very Newbie and I have to be in windows for the net::( 
so this is out of my memory

But I Think you got to system, preferences, keyboard, and choose  Portuguesel then you have then you change to the keyboard layout buy hitting both "alt" keys. Or you can go  to system, preferences, keyboard and go to the next option in the top list then choose group control and then choose what keys can change the keyboards. If you want you can then go the led section in the same window and make a led light comes on when you change keyboards[/QUOTE]

I think it doesn't work. Can someone help me?

---

### Post by jonathanm on 2005-12-30
[QUOTE=ubuntuubuntu]I think it doesn't work. Can someone help me?[/QUOTE]
make sure that when you change the keyboard lang settings you also restart, i messed around, put it into japanese.  Nothing changed!  When i restarted... 

Aaaaaagh

lets change that back quick

---

### Post by truthfatal on 2005-12-30
[QUOTE=ubuntuubuntu]I think it doesn't work. Can someone help me?[/QUOTE]
Follow Icebear's directions... you should see [see my attached .png] under "layouts".

[QUOTE=ubuntuubuntu]
But the layout for Brazil is NOT the layout of my keyboard. My keyboard is U.S. English.
[/QUOTE]
I'm pretty sure there are some alt-[numpad] combinations you could use to type accented letters and special characters -- I've never tried them in GNU/Linux. or you could use the "Character Palette" panel applet. (Right click panel, select 'Add To Panel' scroll down to the Utilities section and select 'Character Palette')

---

### Post by ubuntuubuntu on 2006-01-07
I still can't solve this problem, and I know other Brazilian people with the same problem.

---

### Post by HanZo on 2006-01-27
>  messed around, put it into japanese. Nothing changed!
try this: change the layout, open a terminal and type **setxkbmap** or **sudo setxkbmap** (not shure if you need su permissions)
on my system this worked... at least on time.

and now the long story:
some things in Breezy seem to be corrupted regarding to the keyboard stuff... on my German keyboard usually I have to type the accent key and then the letter I want to have accented and this should usually result in something like è or à... but since Breezy (Hoary didn't seem to have this problem) it always looks like 'e or 'a... apparently this is a problem with the keyboard config, so I tried to change that, but, know what it just won't change the bloody keyboard layout...
after days of hacking around I noticed that executing the command "setxkbmap" would make X apply the new keymap...

---

### Post by mc_bizon on 2006-01-27
> try this: change the layout, open a terminal and type setxkbmap or sudo setxkbmap (not shure if you need su permissions)
on my system this worked... at least on time.

thank you

---

### Post by simosx on 2006-01-27
It is better to use the GNOME Keyboard configuration tool.

Have a look at
[http://planet.hellug.gr/misc/bra/](http://planet.hellug.gr/misc/bra/)  (requires :KS flash:KS )

It shows how to type with Brazilian Portuguese, can be used with any other language, in any Linux distribution that uses GNOME! \\:D/

---

### Post by Rhawi Dantas on 2006-01-28
Well, I'm Brazilian too but I use a german keyboard (Microsoft Natural Multimedia Keyboard 1.0A).

This thread was very helpful. I downloaded the packages to german language with the "Language Selector" and then added to the "Keyboard" my layout and the type of my keyboard, then, I just typed at the shell "sudo setxkbmap".

Thanks to you all...

---

### Post by thojoh on 2006-01-31
> try this: change the layout, open a terminal and type  
> sudo setxkbmap 

(sorry, I do not know how to add Quotes to my reply...)

THANKS HanZo!!!!!

This is the answer to a problem I have been battling with over the last few months (finally settling with the fact that I don't understand what's wrong). 
I changed keyboard layouts and options but nothing would give me back the keyboard use that was used to. (getting ö for example when typing " + o )

Sometimes, for some reason it worked, the next time it didn't. I gave up. But now I found this command  (sudo setxkbmap) that you suggest, and it works!!

My only question is whether there is a possibility to solve this bug more structurally. At them moment I have to open my terminal everytime on startup and type this command, which is a bit of a strain.

Any smart Ubuntu Breezy person with a good idea?

thanks again + greetings!!!
\\:D/

---

### Post by taygan on 2006-02-02
Special characters can be typed by crtl+shift+unicode  for example ctrl+shift+e7 gives you a ç.  applications>accessories>character map will tell you the codes.

enjoy!

---

### Post by zugvogel on 2006-02-05
[QUOTE=HanZo]try this: change the layout, open a terminal and type **setxkbmap** or **sudo setxkbmap** (not shure if you need su permissions)
on my system this worked... at least on time.
[/QUOTE]

Thank you so much for this. Typing "sudo setxkbmap" made it recognise the change in the keyboard layout and solved my problem.

Does anyone know whether this bug is going to be fixed in the next Ubuntu release? It seems a rather significant problem.

Incidently, I was rather impressed by the fact that Ubuntu immediately recognised my new wireless keyboard and mouse - plug and play. Even though the man in the shop told me it was only for windows and wouldn't work under Linux...

---

