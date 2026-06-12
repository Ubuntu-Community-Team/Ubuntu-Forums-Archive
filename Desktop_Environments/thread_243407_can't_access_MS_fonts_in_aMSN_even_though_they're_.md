---
title: "can't access MS fonts in aMSN even though they're system wide everywhere else"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Loungefly on 2006-08-25
Hey all,

I just installed amsn from synaptic and I'm stumped on how to select MS fonts. They aren't showing up in the font selector.

I copied my windows fonts from my windows partition over to Ubuntu and they  are system-wide everywhere else (even in OpenOffice), yet I can't access them from within aMSN.

Any help would be greatly appreciated :)

---

### Post by Demio on 2006-09-07
I'm having the same problem. Can someone help us?

---

### Post by raul_ on 2006-10-10
Ok let's have a recall:

> Quote:
If aMSN won't see your TrueType? fonts, try running:

Code:

cd /path/to/your/TTF/fonts mkfontdir -o fonts.dir mkfontscale -o fonts.scale fc-cache -fv xset +fp /path/to/your/TTF/fonts xset fp rehash

and adding the last 2 lines to your .xinitrc

-------------------------------

i get this error
Code:

raul@raul:/usr/share/fonts/truetype$ sudo xset +fp /usr/share/fonts/truetype/ xset: bad font path element (#76), possible causes are: Directory does not exist or has wrong permissions Directory missing fonts.dir Incorrect font server address or syntax

and plus, i can't find .xinitrc with "locate" =\

-------------------------------------------

Now, i checked, and i DO have a fonts.dir file. As for the .xinitrc just type "locate xinitrc" copy that file to your home dir and rename it to .xinitrc and do what u please with it. and i couldn't solve the problem =P maybe it'll work with someone else

---

### Post by dagnabit dang doohickey on 2006-10-10
Just for clarification, I'm assuming you also have a fonts.scale file as well. If so, something goofy about xset seems to be the current focus of this issue.

---

### Post by raul_ on 2006-10-10
ur assumption is right

---

### Post by dagnabit dang doohickey on 2006-10-10
Another way to write

xset +fp /usr/share/fonts/truetype

is

xset fp+ /usr/share/fonts/truetype

I don't know if that'll make any difference, though.

---

### Post by dagnabit dang doohickey on 2006-10-10
Also, since those xset commands should be added to .xinitrc, you can try doing that, but since just running the command is causing an error, I don't have high hopes.

---

### Post by raul_ on 2006-10-10
Like u said it's just another way to write, so it produces the same error =P i found this article in portuguese, i'll translate it:

    * Crie o diretório /home/usuario/.fonts, e coloque suas fonts neste diretório.
    (Create a directory /home/youruser/.fonts and put your fonts in it)

fc-cache /home/youruser/.fonts

----------------------------------

i'm kinda reluctant, because there are 130 mb of fonts, and i don't want to have 130mb of something that i already have in another folder, not to mention i think it's a stupid ideia. aMsn must get the fonts from some file or folder, it's a just a matter of knowing which (maybe)

---

### Post by dagnabit dang doohickey on 2006-10-10
I agree with your last post. I think throwing fonts into .fonts is a way for users without admin rights to handle fonts.

I'm curious; can you post the contents of fonts.dir and fonts.scale?

---

### Post by raul_ on 2006-10-10
lol...i thinks something's not right =\ 
```

raul@raul:/usr/share/fonts/truetype$ cat fonts.dir
0
raul@raul:/usr/share/fonts/truetype$ cat fonts.scale
11
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-ascii-0
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso10646-1
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-15
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-1
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-2
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-3
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-4
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-9
StayPuft.ttf -misc-staypuft-medium-r-normal--0-0-0-0-p-0-ascii-0
StayPuft.ttf -misc-staypuft-medium-r-normal--0-0-0-0-p-0-iso10646-1
StayPuft.ttf -misc-staypuft-medium-r-normal--0-0-0-0-p-0-iso8859-1

```

---

### Post by dagnabit dang doohickey on 2006-10-10
I just noticed that the OP created this thread is in the "Desktop Environments" category. Rats! To bad he didn't create it "General Help". Does anybody even come to this part of town? :p

---

### Post by raul_ on 2006-10-10
LOL! good point. I don't know how people browse the forums. Honestly i didn't know this section existed =\

---

### Post by dagnabit dang doohickey on 2006-10-10
> **raul_ said:**
> lol...i thinks something's not right =\ 
```

raul@raul:/usr/share/fonts/truetype$ cat fonts.dir
0
raul@raul:/usr/share/fonts/truetype$ cat fonts.scale
11
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-ascii-0
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso10646-1
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-15
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-1
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-2
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-3
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-4
Isabella.ttf -misc-isabella-medium-r-normal--0-0-0-0-p-0-iso8859-9
StayPuft.ttf -misc-staypuft-medium-r-normal--0-0-0-0-p-0-ascii-0
StayPuft.ttf -misc-staypuft-medium-r-normal--0-0-0-0-p-0-iso10646-1
StayPuft.ttf -misc-staypuft-medium-r-normal--0-0-0-0-p-0-iso8859-1

```

Hmm...It seems that mkfontdir doesn't automatically search subdirectories. Since I have nothing but directories in my fonts/truetype dir, I would imagine I'd get a 0 in fonts.dir just like you did.

---

### Post by raul_ on 2006-10-10
newsflash!
```

fc-cache: "/usr/share/X11/fonts/Type1": caching, 44 fonts, 0 dirs
fc-cache: "/usr/local/share/fonts": caching, 0 fonts, 0 dirs
fc-cache: "/home/raul/.fonts": skipping, no such directory
fc-cache: succeeded
raul@raul:/usr/share/fonts/truetype$ xset +fp /usr/share/fonts/truetype/mstt/
xset:  bad font path element (#76), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
raul@raul:/usr/share/fonts/truetype$ xset +fp /usr/share/fonts/truetype/
raul@raul:/usr/share/fonts/truetype$ xset fp rehash
raul@raul:/usr/share/fonts/truetype$ xset +fp /usr/share/fonts/truetype/
raul@raul:/usr/share/fonts/truetype$

```

i think u can tell i typed the command twice because i didn't believe it the first time. i restarted amsn but no good. i'll try logging in and out ("a la windows") and see what happens

PS: that /mstt/ dir was just an experiment to see what happened

EDIT: ok nothing happened. i don't know why i use amsn if i can only use bad fonts and can't send files (only to linux users YEAHH!! linux rules )

---

### Post by dagnabit dang doohickey on 2006-10-10
Something else:

Running mkfontscale before mkfontdir might be helpful.

> 
Installing scalable fonts is very similar to installing bitmap fonts: you create a directory with the font files, and run `mkfontdir' to create an index file called `fonts.dir'.

There is, however, a big difference: `mkfontdir' cannot automatically recognise scalable font files. For that reason, you must first index all the font files in a file called `fonts.scale'. While this can be done by hand, it is best done by using the `mkfontscale' utility.

    $ mkfontscale /usr/local/share/fonts/Type1/
    $ mkfontdir /usr/local/share/fonts/Type1/

Under some circumstances, it may be necessary to modify the `fonts.scale' file generated by mkfontscale; for more information, please see the mkfontdir(1) and mkfontscale(1) manual pages and Core fonts and internationalisation later in this document.

[link]("http://ftp.x.org/pub/X11R7.0/doc/html/fonts2.html")

---

### Post by raul_ on 2006-10-10
Same thing. now i can go through the instructions but amsn still doesn't show my fonts. i can't seem to find anything about this on google =|

---

### Post by dagnabit dang doohickey on 2006-10-10
I'm getting the feeling we've been taking the long (possibly old and dusty) road to nowhere.

[aMSN: fonts look ugly!]("http://ubuntuforums.org/showthread.php?t=3571") [ubuntuforums.org]

---

### Post by raul_ on 2006-10-10
lol. but if it doesn't support truetype fonts, how come it's in the FAQ ? this is linux, it has a solution for everything =p

---

### Post by dagnabit dang doohickey on 2006-10-10
Reading this [thread]("http://amsn.sourceforge.net/forums/viewtopic.php?t=1561"), it seems that all the info in the [aMSN wiki link]("http://amsn.sourceforge.net/wiki/tiki-index.php?page=Installation+Instructions#tcl/tk") I previously posted is all important, including the part about updating tcl/tk and recompiling aMSN.

---

### Post by dagnabit dang doohickey on 2006-10-10
Also, I'm guessing that if you decide to go the update/recompile route, all this stuff:

> cd /path/to/your/TTF/fonts
mkfontdir -o fonts.dir
mkfontscale -o fonts.scale
fc-cache -fv
xset +fp /path/to/your/TTF/fonts
xset fp rehash

probably won't even be necessary.

---

### Post by raul_ on 2006-10-10
well i tried, but now i have another problem..when i run ./configure on amsn it will only recognise tk8.4 and tcl8.4 and if i try to remove them with synptic i have to uninstall python and etc etc.. i think the compiler is just stupid =P

---

### Post by dagnabit dang doohickey on 2006-10-10
Maybe [this]("http://ubuntuforums.org/showthread.php?t=84765") will be helpful.

---

### Post by raul_ on 2006-10-10
lol thanks but a little late :) i already compiled everything, but now i get a "segmentation fault" when i start amsn and i'm stuck with that, that's why i didn't post nothing

i got round the segmentation fault problem, amsn runs with tcl and tk 8.5 and guess what???????? NO MS FONTS! that's hilarious (or not) i'll try to run those commands u posted first

EDIT: nop nothing...no arial, no comic sans, no nothing :(

---

### Post by dagnabit dang doohickey on 2006-10-10
What previously sounded so silly to both of us a little while ago, sounds downright genius to me now: copying a couple of the fonts you want(maybe alias' to them?) into your .fonts dir and giving those commands another spin.

---

### Post by raul_ on 2006-10-10
SOLVEDDDD!!! lol u're my hero, i would never try that, it only shows how much consideration i have for u :P anywayz, i copied the windows fonts to the new directory ~/.fonts/  ran the instructions with the new path, and voila, ARIAL on aMsn :) man, this isn't that big but for the time i spent with it, it reallyyyyy feels good :) that's what i like in linux, the satisfaction u get when u make something work.
Thank u dagnabit dang doohickey for ur support :) [[]]

---

### Post by dagnabit dang doohickey on 2006-10-10
Fantastic!
Thanks for the thanks raul_, but you did all the drivin', I just read the map every now and then. ;) 

> that's what i like in linux, the satisfaction u get when u make something work.

Ditto

Cheers, raul_


[I]Note to any future travelers who happen upon this thread:
It appears mkfontdir and mkfontscale are limited to only reading fonts in a single directory and cannot traverse subdirectories. If any light can be shed on this, please do so.[/I]

---

