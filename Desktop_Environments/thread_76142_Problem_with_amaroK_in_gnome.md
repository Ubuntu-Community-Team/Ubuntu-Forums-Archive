---
title: "Problem with amaroK in gnome"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Dr. Nick on 2005-10-14
Mods if you feel this is beter off in the KDE section could you please move it, I went ahead and put it here since I use gnome and dont have KDE installed, just the necessary libs.

Ok now to my problem. I am using amarok in ubuntu breezy and it works sorta, When I resisze and of the windows inside the interface almost everything locks up, the mouse will still move the music plays on, but I cant click anywhere in amarok or the rest of gnome so I have to press reset on my case as neither ctrl+alt+delete or ctrl+alt+backspace do anything, no virtual terminals on ctrl+alt+f* work either.

I know this is hard to solve but was curious if anyone had a solution or was able to recreate it

EDIT
I am not in love with amarok :) I just like some of its features such as lyrics,wikipedia links to artist, and album art. So if anyone knows of a alternative gnome/gtk2 based program that will accomplish some or all of these I am open to trying new things, I know their is always rhythmbox to fall back on if I have too just would like something with a few more featues.

---

### Post by deeek on 2005-10-14
I had a similary problem, and I didn't get a working amaroK until I installed a fresh copy of Kubuntu.  :-/   I tried many things like installing KDE for ubuntu, but I had no luck.  I never found out what the problem was.  

As far as alternative music players for GNOME, I don't think there are any which can match the capabilities that amarok has.  You could always try banshee, quod libet, zinf or just rhythmbox in the short term.

Good luck!

---

### Post by Dr. Nick on 2005-10-14
[QUOTE=deeek]
As far as alternative music players for GNOME, I don't think there are any which can match the capabilities that amarok has.  You could always try banshee, quod libet, zinf or just rhythmbox in the short term.

Good luck![/QUOTE]

Thank you very much!!!
I discovered "quod libet" looks very promising and has plugins that seem to accomplish all I like in amaroK, and is native gtk so i dont have to load the kde libraries into memory, amaroK seems to hesitate a bit while skipping tracks in gnome for some reason, no big deal really just a tad annoying. 

The others looked good aswell and I may try them one day but out of the list quod libet looked the best, Rhythmbox seems to have slowed down development currently but I think it'll pick back up again as they were in Google Summer of Code, atlesat I hope so.

Thanks again its installing now

---

### Post by SilverTab on 2005-10-14
Yup...former Amarok user here(in hoary), now using Quod Libet! :)

---

### Post by Dr. Nick on 2005-10-14
EDIT I am figuring it out, only 3 or so of my albums got cover art , amarok got all of them so I have to figure out how to fix this in QL
*******************************
since your using it aswell did you ever tinker with the plugins? And how successfull were you :) I havent had alot of luck, they show up in the plugin list but cant see the output or a way to configure them

---

### Post by SilverTab on 2005-10-14
[QUOTE=Dr. Nick]EDIT I am figuring it out, only 3 or so of my albums got cover art , amarok got all of them so I have to figure out how to fix this in QL
*******************************
since your using it aswell did you ever tinker with the plugins? And how successfull were you :) I havent had alot of luck, they show up in the plugin list but cant see the output or a way to configure them[/QUOTE]


the plugins are in ~.quodlibet/plugins

(the directory isnt there by default...so you have to create it to put plugins in it)

I already wrote my own plugin (you can easily write them in python)...mine search on Torrentspy for the selected artist ;)

if you have a basic python knowledge, plugins are really easy to figure out...BUT, the album cover arts is a program feature, not a plugin...but again, if you have a good knowledge of python, check out the source, you can probably fix that :)

---

### Post by Dr. Nick on 2005-10-14
[QUOTE=SilverTab]the plugins are in ~.quodlibet/plugins

(the directory isnt there by default...so you have to create it to put plugins in it)

I already wrote my own plugin (you can easily write them in python)...mine search on Torrentspy for the selected artist ;)

if you have a basic python knowledge, plugins are really easy to figure out...BUT, the album cover arts is a program feature, not a plugin...but again, if you have a good knowledge of python, check out the source, you can probably fix that :)[/QUOTE]

Yeah I figured out the plugin directory. Trying to get the album art for the 10 or so albums it didnt get for me. Also have you used the lyrics plugin, I installed it and activated itbut dont see any options for it

---

### Post by SilverTab on 2005-10-14
[QUOTE=Dr. Nick]Yeah I figured out the plugin directory. Trying to get the album art for the 10 or so albums it didnt get for me. Also have you used the lyrics plugin, I installed it and activated itbut dont see any options for it[/QUOTE]


yup its working, make sure it is checked in the plugin options (in quod libet)

then just right-click on a song and go to Plugins>Show Lyrics

it uses the same library as amarok

---

### Post by Dr. Nick on 2005-10-14
:rolleyes: hmm guess I should just go to bed now, How I missed that I dont know lol, Thanks worked like a charm :)

---

### Post by SilverTab on 2005-10-14
[QUOTE=Dr. Nick]:rolleyes: hmm guess I should just go to bed now, How I missed that I dont know lol, Thanks worked like a charm :)[/QUOTE]


yup! very neat player! I love it so far!

I would add my torrent pluggins to their website, but I doubt they will accept it hehe

If you have any idea/suggestions for plugins let me know, I might be able to write it! ;)

---

### Post by seethru on 2005-10-14
is there any ipod support for quod libet?

---

### Post by Dr. Nick on 2005-10-14
Yeah, like what I see for the most part just trying to get all the album art in a efficient manner. Ill let you know if I think of anything, dont know much python but know some c++ and coding in general so I can edit some of them to my needs.

If anyone is reading this and has rhythmbox and is "afraid" of changing don't worry, the interface can easily be made to be very similar but better :) I especially like how the albums can be displayed on the side

---

### Post by SilverTab on 2005-10-14
[QUOTE=Dr. Nick]Yeah, like what I see for the most part just trying to get all the album art in a efficient manner. Ill let you know if I think of anything, dont know much python but know some c++ and coding in general so I can edit some of them to my needs.

If anyone is reading this and has rhythmbox and is "afraid" of changing don't worry, the interface can easily be made to be very similar but better :) I especially like how the albums can be displayed on the side[/QUOTE]


Nice, give it a try then! Took me like 10 minutes to write my plugin, its really easy, and if you have an error in your code, the plugin just dont show up in the list! :)

also, for the view, I really like Views >> Panned Browser 
Give it a try if you havent and like the itunes look! :)


seethru: No ipod support as far as I can tell! :(
which is the only complain I have about this program..

---

### Post by Dr. Nick on 2005-10-14
[QUOTE=seethru]is there any ipod support for quod libet?[/QUOTE]

None that I see but I dont have an IPod, I scanned through their site and saw nothing about ipod, just the iriver player.

The aforementioned Banshee looks good for iPod though
[http://banshee-project.org](http://banshee-project.org)

> With Banshee you can easily import, manage, and play selections from your music collection. Banshee allows you to import CDs, sync your music collection to an iPod, play music directly from an iPod, create playlists with songs from your library, and create audio and MP3 CDs from subsets of your library.

---

### Post by Dr. Nick on 2005-10-14
[QUOTE=SilverTab]
also, for the view, I really like Views >> Panned Browser 
Give it a try if you havent and like the itunes look! :)
[/QUOTE]

Yeah thats a good one aswell, Reminds me of iTunes and looks almost identical to Rhythmbox so if anyone wanted to switch they would have very little adjustment

---

### Post by bk452 on 2005-10-24
> I already wrote my own plugin 

I give up.  How do you install the plugins?

---

### Post by Dr. Nick on 2005-10-24
[QUOTE=bk452]I give up.  How do you install the plugins?[/QUOTE]

make a plugins direotry under your .quodlibet folder in your home folder, its not their by default and needs to be made, you will need to go to view, show hidden files in nautilus to see the directory.

Open the plugins folder and right click - hit new document, open it and paste all the contents of the plugin file from the website into the document save as "anyname.py"

Then open quodlibet and go to file-plugins and activate it.

---

### Post by bk452 on 2005-10-25
> Then open quodlibet and go to file-plugins and activate it.


I can't believe I did it.  It was so easy!  Thank you so much!!!

---

### Post by Dr. Nick on 2005-10-25
[QUOTE=bk452]I can't believe I did it.  It was so easy!  Thank you so much!!![/QUOTE]

No Problem , find any good ones :) 
All i have is the lyrics one

---

### Post by bk452 on 2005-10-25
> No Problem , find any good ones

Yes.  4 of them.  The timer, looking up the tag info in a database online, the one that uploads to an iRiver and of course, the lyrics one.

---

