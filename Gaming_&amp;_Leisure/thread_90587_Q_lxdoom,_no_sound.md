---
title: "Q: lxdoom, no sound"
date: 2005-11-15
forum: Gaming &amp; Leisure
---

### Post by gmc on 2005-11-15
Hi Folks,

     I was cleaning out an old box of cd's and came across my old Doom games. I managed to save the *.wad files even though the cd's are pretty scratched up.

     Anyhow, I've installed lxdoom with the lxdoom-sndserv; lxdoom runs fine, but there's no sound. Anyone have any ideas?

G.

---

### Post by kaamos on 2005-11-15
Hello!

Tried to google this once, and my conclusion was that the sdl-libraries that the legacy packages use are too old.. I suggest trying doomsday. ([http://www.doomsdayhq.com/](http://www.doomsdayhq.com/))

```
deb http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
```

Adding these to your sources.list will make life a bit easier, since you don't have to compile doomsday. :)

---

### Post by Yagisan on 2005-11-16
[QUOTE=kaamos]```
deb http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
```

Adding these to your sources.list will make life a bit easier, since you don't have to compile doomsday. :)[/QUOTE]Thanks for the plug :) A full list of packages is available here [http://eyagi.bpa.nu/~jamie/doomsday.en.html](http://eyagi.bpa.nu/~jamie/doomsday.en.html) with some screenshots.

---

### Post by NeoChaosX on 2005-11-16
Hey Yagisan, hope you don't mind me asking this here, but are you going to be uploading any new Doomsday packages soon? I'd like to see the one of high-res texture packs for jHexen be avalible (the UI pack just isn't enough! ;) )

---

### Post by Yagisan on 2005-11-16
[QUOTE=NeoChaosX]Hey Yagisan, hope you don't mind me asking this here, but are you going to be uploading any new Doomsday packages soon? I'd like to see the one of high-res texture packs for jHexen be avalible (the UI pack just isn't enough! ;) )[/QUOTE] I uploaded a few new packs recently, mainly music and some special effects for doom and heretic. I always update the website when new packs are released, but I don't update it if I just upgrade a package. Sadly there isn't a real high resolution texture pack for jHexen at the moment, (there is a pack where someone ran all the hexen textures through photoshop to resize them, but you get a much better result by setting "use smart texture filtering" in the control panel). The next pack I have for jHexen is an audio pack, and as I get time I'll post it.

---

### Post by gmc on 2005-11-16
[QUOTE=kaamos]Hello!

Tried to google this once, and my conclusion was that the sdl-libraries that the legacy packages use are too old.. I suggest trying doomsday. ([http://www.doomsdayhq.com/](http://www.doomsdayhq.com/))

```
deb http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
deb-src http://eyagi.bpa.nu/~jamie/ubuntu breezy main restricted universe multiverse
```

Adding these to your sources.list will make life a bit easier, since you don't have to compile doomsday. :)[/QUOTE]

Great! Thanks.

G.

---

### Post by mhancoc7 on 2005-11-25
Hi, I just upgraded to Breezy. I noticed that I had lost my sound with lxdoom. I fixed it by downgrading my lxdoom-sndserv to the Hoary release. I have attaced the deb. Hope this helps, Jereme

---

### Post by porschemad911 on 2006-01-11
Hey mhancoc7, you don't happen to have the Hoary version of the lxmusserv package handy as well do you? Pretty please?

---

### Post by mhancoc7 on 2006-01-11
I am sorry, but I do not. I tried to see if it was on the Hoary install disc, but I could not find it.
God Bless, Jereme

---

### Post by porschemad911 on 2006-01-12
Thanks for trying! :p

---

### Post by Bloch on 2006-02-20
Thanks mhancoc7 for that older debian package for lxdoom-sndserv.
I aptget remove lzdoom-sndserv
and installed the new one with dpkg.
Now I have sound. . . . . Are there so few people playing doom 1 on ubuntu? It took me a while to find this solution. For doom fans, install the freedoom package (in universe)  to see a new version of doom with much more interesting sound.
It seems odd that there's no fullscreen ability on lxdoom though . . .

---

### Post by mhancoc7 on 2006-02-20
No problem. It took me awhile to get it figured out as well. I am glad that you found this thread. Yeah I wish lxdoom had full screen too. For now I just use the following command which sets the window to a size that fills my screen just right. I use the turbo command to slow it down a bit.

/usr/games/lxdoom -width 1023 -height 673 -iwad /home/mhancoc7/doom/DOOM.WAD -turbo 75

God Bless, Jereme

---

### Post by Yagisan on 2006-02-21
[QUOTE=Bloch]Are there so few people playing doom 1 on ubuntu? It took me a while to find this solution.[/QUOTE] It's not that there are few people playing doom, rather it is that other ports such as prboom or deng are preferred to lxdoom.

---

### Post by Burgresso on 2006-03-14
I noticed this, hoping it would solve the problem for me too.

> Hi, I just upgraded to Breezy. I noticed that I had lost my sound with lxdoom. I fixed it by downgrading my lxdoom-sndserv to the Hoary release. I have attaced the deb. Hope this helps, Jereme
[QUOTE]Attached Files
File Type: gz 	lxdoom-sndserv_1.4.4-9ubuntu1_i386.deb.tar.gz (47.2 KB, 12 views)[/QUOTE]

But being a noob, how would I do this? Thanks in advance! :-k 
:)

---

### Post by mhancoc7 on 2006-03-14
Hi Burgresso,
No problem. 

You will need to download the file that I attached. Then extract its contents to you Home directory. You can do this by right clicking on the file and selecting extract here with it in your Home directory. Then open a Terminal window and type the following command.

sudo dpkg -i lxdoom-sndserv_1.4.4-9ubuntu1_i386.deb

That should install the old version of the lxdoom-sndserv. If it asks you if you intend to downgrade just say yes.

I hope that helps.

God Bless, Jereme

---

### Post by Burgresso on 2006-03-14
Thanks Jerome, I'll try that tonight. You rock.

UPDATE: It worked! Thanks again - the sound effects are not on!

---

### Post by wanger123 on 2006-05-13
Many thanks for the .deb Jereme!

I just pass this command for fullscreen on my widescreen laptop

$ lxdoom -width 1440 -height 900

ciao

wanger

---

### Post by fululian on 2007-10-08
> **mhancoc7 said:**
> Hi, I just upgraded to Breezy. I noticed that I had lost my sound with lxdoom. I fixed it by downgrading my lxdoom-sndserv to the Hoary release. I have attaced the deb. Hope this helps, Jereme

gee, you're one clever guy. 't will be a doom-playing night for me. thanks a lot.

---

