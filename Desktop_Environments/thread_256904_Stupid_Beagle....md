---
title: "Stupid Beagle..."
date: 2006-09-13
forum: Desktop Environments
---

### Post by Odinist on 2006-09-13
So I installed Beagle, didn't care for it, uninstalled it, and now the Search feature under the Places menu doesn't work, because it's trying to start Beagle.

How do I get it back to normal?

---

### Post by Odinist on 2006-09-14
::bump::

Come on, no one knows?

---

### Post by turbojugend_gr on 2006-09-14
Actually I have the same issue since 1st of June, 1 hour after the installation of Dapper Drake... You know my solution to this was very easy and better (though I never fixed that one). I use the VERY VERY VERY fast and always finding all hits "locate" app through a terminal. It is so much quicker than anything I 've seen in any OS. If you are unfamiliar with it's use, a "locate Filename_you_are_searching_for" is enough, though I suggest you try a "man locate" for a verbose explanation, it is feature-packed also, despite being stuck on the command line.

---

### Post by Odinist on 2006-09-14
Thanks for the reply!

Can locate look for things more general than specific filenames? For instance, all files of a certain type?

---

### Post by turbojugend_gr on 2006-09-14
try a "locate *.avi" for instance or a "locate *.avi *.mpeg Chicks university" and as many keywords you need! just leave a gap (space) between them oh, a better use is "locate -i ...etc" so you don't need to be case sensitive in your searches (you now case sensitive is when "Kids" is different to the PC from "kids", or "levEl" isn't level"). Be sure to read through the manual by typing "man locate", just in case you aere new to linux you may "man" almost all commands.

---

### Post by turbojugend_gr on 2006-09-14
Some helpfull syntaxis on the locate application.

>When I look for the path of a file I know it exists but can't locate it:```
locate File_name_case_sensitive
```
>When I try to find a file I can't recall it full name but I know it cointains "info" for instance:```
locate -i info|less
``` This |less is so can control the flow of the results (as the may be hundreds of them) then you quit as usual by striking Q when desired.
>When I try to index my music along with the songs paths for instance, check it out that's magical stuff: ```
locate *.mp3 *.ogg >> ~/musicindex
```
The >> signs make the output of any command to be written in the top of the file you tell it to (if you wish a replace of the files data with the new one > sign will do the job). SO in this case I have my entire music collection indexed and path-named in this file! =D> see it is far more handy than gui-stuff.

---

### Post by Odinist on 2006-09-14
Not new (been using Ubuntu since like, Dec. 04, Jan 05), but I'll definitely read the man pages for more info about it.

Thanks a million!

---

### Post by turbojugend_gr on 2006-09-14
Oh i just saw the join date... sorry for making me a fool again ;), anyhow at least I pointed out it's "hadnyness".

---

### Post by wildutah on 2006-09-17
XXX: delete

---

### Post by wildutah on 2006-09-17
XXX: Delete

---

### Post by wildutah on 2006-09-17
> **turbojugend_gr said:**
> "locate *.avi *.mpeg Chicks university"

This is what you'd like to see:

```
~> locate -i .avi .mpeg Chicks university
/home/user/Desktop/university.experiment.eggs.incubating.chicks.avi
~>
```

:-\" 

but locate performs an OR search instead of an AND search (which just means somebody in the slocate design team is clinically brain dead).

So try this instead:

```
~> locate -i chicks | egrep -i university | egrep -i "avi|wmv"
```

A locate that kept track of files as they change on the system would be a welcome improvement.

---

### Post by Odinist on 2006-09-17
> **wildutah said:**
> This is what you'd like to see:

```
~> locate -i .avi .mpeg Chicks university
/home/user/Desktop/university.experiment.eggs.incubating.chicks.avi
~>
```

:-\" 




HAHAHAHAHAHAHA!!!! =D>

---

### Post by chajuram on 2006-09-18
as far as i understand locate does not read in a file. that is the reason it is faster. i like it a lot, but for the updatedb (though I understand it can be automated).

---

