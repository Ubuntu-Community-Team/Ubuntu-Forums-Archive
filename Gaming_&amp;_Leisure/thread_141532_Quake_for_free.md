---
title: "Quake for free?"
date: 2006-03-08
forum: Gaming &amp; Leisure
---

### Post by ubuntukid on 2006-03-08
I noticed when watching the go open videos that Quake is open source. I downloaded and installed the quake 2 and quake 2-data thing from the synaptic package manager but I noticed that I need data files from a purchased copy of the original.

Are there any free data files out there that you can recommend (legal ones of course) like mods and so on. Can you also explain how to install them.

---

### Post by polpak on 2006-03-08
[QUOTE=ubuntukid]I noticed when watching the go open videos that Quake is open source. I downloaded and installed the quake 2 and quake 2-data thing from the synaptic package manager but I noticed that I need data files from a purchased copy of the original.

Are there any free data files out there that you can recommend (legal ones of course) like mods and so on. Can you also explain how to install them.[/QUOTE]

If you don't have quake 2 you can download the nessicary data files from the shareware demo.

I think just doing a 

sudo dpkg-reconfigure quake2-data 

should give you the option.

---

### Post by den benne on 2006-03-09
indeed this works and lets you play the quake2 demo

but is there more free content?

---

### Post by ubuntukid on 2006-03-09
Your best bet is to buy a copy of Quake 2 from ebay or something. I can`t find them in stores. I`m borrowing a copy from my friend though. I had my own copy but lost it years ago so I expect it`s legal for me to take the data files from my friend. I do have a mission pack cd in my draw though and I was wondering how I install this.

Also I have a copy of Quake 1 installed on my windows laptop. Is there a similar program out there for playing Quake 1?

And lastly has Quake 3 been made open-source?

Also why won`t they release the data files for the game when they no longer sell it anyway?

---

### Post by deathbyswiftwind on 2006-03-09
here is a guide to quake 3 source and how to install it
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)

---

### Post by leech on 2006-03-09
[QUOTE=ubuntukid]Your best bet is to buy a copy of Quake 2 from ebay or something. I can`t find them in stores. I`m borrowing a copy from my friend though. I had my own copy but lost it years ago so I expect it`s legal for me to take the data files from my friend. I do have a mission pack cd in my draw though and I was wondering how I install this.

Also I have a copy of Quake 1 installed on my windows laptop. Is there a similar program out there for playing Quake 1?

And lastly has Quake 3 been made open-source?

Also why won`t they release the data files for the game when they no longer sell it anyway?[/QUOTE]

I'll take a shot at answering this.  

Think about it this way.  You have a popular engine.  The game is out for a while, and sales start to diminish.  You release the source code, but not the data files.  People then start downloading the source, then porting and cleaning it up.  Adding new features to it, like dynamic lighting, stencil buffer shadows etc, then there is new found interest in your old game and what do you know, even more people than had bought it 'back in the day' want to buy it.  Or even people who used to have the game and loved it buy new copies 'cause their originals are broken/scratched/lost.

Suddenly you have instant new revenue, and yet you didn't even have to do any work.

The quake series is a great example of this, because there are several projects out there for improving the engines.  

Leech

---

### Post by ubuntukid on 2006-03-09
Yes I do see your point here but there`s one catch. I can`t find Quake 2 or it`s mission packs in any store and I can`t find Quake 1 with mission packs either. I`m one of those who would really like to buy them and I would if I could. Why don`t they release a combo box containing Quake 1 + mission packs. Quake 2 + mission packs and Quake 3 with expansion all in one DVD set? I understand that they would sell Quake 4 seperate because that would bring more income. I saw a pack once containing 1, 2 and 3 and I should have bought it, I really should, but it didn`t have any of the mission packs in it. Man I should have bought it. I was young and dumb in those days. It would have cost me only $20.

---

### Post by charlieg on 2006-03-09
Try Amazon or ID's online store:
[http://www.idsoftware.com/store/index.php?view=quake](http://www.idsoftware.com/store/index.php?view=quake)

---

### Post by charlieg on 2006-03-09
Or OpenQuartz (free Quake content, although not as good as the original IMHO)...
[http://openquartz.sourceforge.net/](http://openquartz.sourceforge.net/)

---

### Post by ubuntukid on 2006-03-10
Could someone tell me how to install the mission pack?

---

### Post by charlieg on 2006-03-10
I'm sure you can [find out](http://www.google.co.uk/search?q=quake+mission+pack+linux+howto) if you look hard enough.

---

### Post by ubuntukid on 2006-03-11
Thanks. I`m a class 1 idiot for not finding it myself.

The command for running the Quake 2 mission pack is quite long and difficoult to remember. Is there a unix command which lets me create a permanent alias command or something like that? I want to be able to type quake2-mp2 and it launches mission pack 2 and I don`t have to type the real command which is just to long to remember.

---

### Post by WildTangent on 2006-03-12
[QUOTE=ubuntukid]Thanks. I`m a class 1 idiot for not finding it myself.

The command for running the Quake 2 mission pack is quite long and difficoult to remember. Is there a unix command which lets me create a permanent alias command or something like that? I want to be able to type quake2-mp2 and it launches mission pack 2 and I don`t have to type the real command which is just to long to remember.[/QUOTE]
What is the full command?

-Wild

---

### Post by AndyAWS on 2006-03-12
I've only managed to get the mission packs half working...and only by using the loki quake2 installer. You just need to copy the *.pak files from the addon CD to a folder named either xatrix (MP1) or rogue (MP2) under the /usr/local/games/quake2/ folder.

The BIG problem is that you need 'gamei386.so' files for each mission pack before they will work properly, and I can't find those anywhere, except in an RPM for quake2-3.20 and those cause SDL parachute errors, I believe because they ar compiled for the wrong libraries.

Does anyone have [COLOR="Red"]gamei386.so[/COLOR] files for the addons that work?

---

### Post by charlieg on 2006-03-12
When you have your command working, do this:
```
# echo "quake command" > quake-mp2
# chmod +x quake-mp2
```
Where you put the full command in quotes.
*(i.e. instead of "quake command" put "quake --run-mission-pack --or-whatever-it-is")*

Now this should run it:
```
# ./quake-mp2
```

---

### Post by WildTangent on 2006-03-12
[QUOTE=charlieg]When you have your command working, do this:
```
# echo "quake command" > quake-mp2
# chmod +x quake-mp2
```
Where you put the full command in quotes.
*(i.e. instead of "quake command" put "quake --run-mission-pack --or-whatever-it-is")*

Now this should run it:
```
# ./quake-mp2
```[/QUOTE]
Or you could copy quake-mp2 to /usr/bin and it'll work like this:
```
justin@chimera:~$ quake-mp2
```

-Wild

---

### Post by AndyAWS on 2006-03-12
So are you actually able to run the mission packs?

They load ok for me but none of the new enemies or weapons show up, and if I run from CLI I can see that the 'gekks' fail to spawn in the first mission for The Reckoning (xatrix).

Did you build the game.so files from source? I've tried but I still get the SDL error, because I believe that IDs source code does not support SDL.

Any info would be helpful.

---

