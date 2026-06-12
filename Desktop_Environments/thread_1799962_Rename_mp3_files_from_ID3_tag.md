---
title: "Rename mp3 files from ID3 tag"
date: 2011-07-08
forum: Desktop Environments
---

### Post by mister_p_1998 on 2011-07-08
Hi All, Im trying to auto rename badly named mp3's using info from the id3 tag. I got a nice little program called id3ren, it works fine apart from it doesn't add the track number. Cant figure how to enable this function. The track numbers are in the ID3, but it just renames to Artist/Trackname. Any other users on here?

---

### Post by adit on 2011-07-08
Run id3ren with -template argument.  The following code will rename the file with [Artist Name]-[Song Name]-[Track Number].mp3
```
id3ren -template='[%a]-[%s]-[%n].mp3'

```
You can modify the above template with the any character you want.
For example the template (%a)_(%s)_(%n).mp3 will rename the file as
(Artist Name)_(Song Name)_(Track Number).mp3
Don't modify the characters % and ' in the template.
What does %a %s %n mean? From the id3ren man page:
> %a  - Artist name
%c  - Comment
%s  - Song name
%t  - Album title
%n  - Track Number
%y  - Year
%g  - Genre
If you don't give any template arguments id3ren will use '[%a]-[%s].mp3' as a default template


Edit:
Don't use above code. It has errors.  See post#8 for correct code.

---

### Post by coffeecat on 2011-07-08
For a GUI app, try EasyTAG. It's in the repository. Use Scanner (menu) -> Fill Tags. %n is the track number as in the previous post and the other usable legends are listed in the Tag and File Name scan window.

The good thing about EasyTAG is that it changes illegal (illegal in Windows/Windows shares that is) characters to those allowed in filenames. I'm for ever getting hold of albums with ":" or "?" in the title field and EasyTAG deals with that. I've even had illegal characters in the filenames in albums I've purchased from the Ubuntu One store. That really confused my NAS with a Windows share. Confused me too until I worked out what was going on! :rolleyes:

---

### Post by mister_p_1998 on 2011-07-09
OK tried this at home on my 8.04 Hardy install and Im getting the error 'no id3 tag in file XX'
when I run the file through easytag, all the id3 stuff IS there. I was using it before at work on my Lucid install and that read the id3 tags ok. Hmm wierd, its not a major problem because I use it mainly at work on my Vortexbox jukebox.

Steve

---

### Post by coffeecat on 2011-07-09
8.04 Hardy support ended in April (for the desktop version) so you might want to consider upgrading/reinstalling your home system. The version of Easytag in Hardy is a slightly earlier version than that in Lucid/Maverick/Natty.

---

### Post by koleoptero on 2011-07-09
I use mostly ex falso for the job of editing tags and renaming the files based on tags. I find it much easier and straightforward than easytag.

---

### Post by mister_p_1998 on 2011-07-11
> **coffeecat said:**
> 8.04 Hardy support ended in April (for the desktop version) so you might want to consider upgrading/reinstalling your home system. The version of Easytag in Hardy is a slightly earlier version than that in Lucid/Maverick/Natty.

Got the same error on Lucid, pasted your command into the terminal and got the error:
id3ren -template='[%a]-[%s]-[%n].mp3'
id3ren: Not enough arguments specified


Steve

---

### Post by mcduck on 2011-07-11
> **mister_p_1998 said:**
> Got the same error on Lucid, pasted your command into the terminal and got the error:
id3ren -template='[%a]-[%s]-[%n].mp3'
id3ren: Not enough arguments specified


Steve

You'll also have to tell it what file(s) you wish to rename. ;)

id3ren -template='[%a]-[%s]-[%n].mp3' /path/to/some.mp3
id3ren -template='[%a]-[%s]-[%n].mp3' *.mp3

---

### Post by coffeecat on 2011-07-11
> **mister_p_1998 said:**
> Got the same error on Lucid, pasted your command into the terminal and got the error:
id3ren -template='[%a]-[%s]-[%n].mp3'
id3ren: Not enough arguments specified


Steve

That was actually adit's command, but it seems to be missing the current filename(s) of the file(s) you are working on. I've not used id3ren, but looking at the man pages, I guess it would be:

```
id2ren -template=[TEMPLATE] FILE1 FILE2 FILE3....
```

or

```
id2ren -template=[TEMPLATE] WILDCARDS
```

But why not use EasyTAG -it will work in Lucid - or exfalso as koleoptero suggested?

**EDIT**: beaten to it by mcduck! :)

---

### Post by mister_p_1998 on 2011-07-11
Yeah, I usually use easytag, but Im testing id3ren on Lucid so I can run the commandline version on my Vortexbox jukebox which runs on Fedora, complicated eh? Apparently Easytag cant access Samba shares or I would use it like a shot!

---

### Post by mister_p_1998 on 2011-07-11
> **mcduck said:**
> You'll also have to tell it what file(s) you wish to rename. ;)

id3ren -template='[%a]-[%s]-[%n].mp3' /path/to/some.mp3
id3ren -template='[%a]-[%s]-[%n].mp3' *.mp3

Ah! of course! I was thinking the .mp3 was the wildcard but its part of the filename variable, Duh! yea all works ok now other than hitting accents in French tracks.

---

### Post by mister_p_1998 on 2011-07-13
Still not working in Hardy though...

---

### Post by adit on 2011-07-13
Actually your mp3 files contain id3v2 tags.  The program id3ren works well with id3v1 only.  Already a bug report has been filed.
_[https://bugs.launchpad.net/ubuntu/+source/id3ren/+bug/314949](https://bugs.launchpad.net/ubuntu/+source/id3ren/+bug/314949)_

---

### Post by kentfx on 2012-02-12
> **coffeecat said:**
> For a GUI app, try EasyTAG. It's in the repository. Use Scanner (menu) -> Fill Tags. %n is the track number as in the previous post and the other usable legends are listed in the Tag and File Name scan window...

There's no help file and the tagging system is not designed for the faint-of-heart (if you're not a programmer you can get into serious trouble).  Too bad; looks like fun for techies.

---

