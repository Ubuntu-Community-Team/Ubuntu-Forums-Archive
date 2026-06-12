---
title: "Restrictive File Attachments"
date: 2007-01-21
forum: Forum Feedback &amp; Help
---

### Post by jpeddicord on 2007-01-21
I was going to upload an image today in .xcf format, only to be stopped by the file attachment filter. Is it possible we can get some more open-sourcey formats in there? Here is my list of suggested file extensions to add to the current ones:
[LIST]
[*].tar (Like .tar.gz, but uncompressed and "completes" the archive extension list)
[*].xcf (GIMP)
[*].odt, .odp, .ods, .odg (OpenOffice.org)
[*].sh, .py (Sometimes it is better to attach a scripts than embed them)
[/LIST]

I would really like to see the GIMP and OpenOffice.org formats the most, if nothing else.

Jacob

---

### Post by matthew on 2007-01-22
> **jacobmp92 said:**
> I was going to upload an image today in .xcf format, only to be stopped by the file attachment filter. Is it possible we can get some more open-sourcey formats in there? Here is my list of suggested file extensions to add to the current ones:[LIST]
[*].tar (Like .tar.gz, but uncompressed and "completes" the archive extension list)
[*].xcf (GIMP)
[*].odt, .odp, .ods, .odg (OpenOffice.org)
[*].sh, .py (Sometimes it is better to attach a scripts than embed them)[/LIST]I would really like to see the GIMP and OpenOffice.org formats the most, if nothing else.

JacobI've added them all using limits similar to filetypes of the same sort (i.e. filesize limit for odt is the same as doc already was and so on).

---

### Post by jpeddicord on 2007-01-22
Awesome! Thanks a ton Matthew!

:guitar:

---

### Post by unutbu on 2008-10-16
Would the staff please consider removing file attachment restrictions that are based on extension? 

The following files currently cause problems:
/etc/X11/xorg.conf, 
/etc/apt/sources.list, 
/boot/grub/menu.lst, 
/etc/fstab

If we ask a new ubuntu user to attach one of these files, we also have to tell them how to alter the filename so the file can be attached. Then if we alter the file and post it for the user to download,
we must also give instructions on altering the name a second time so it can be placed in the right location. 

Thank you for considering this issue. And, while I have your attention:

Many thanks to the staff for your tireless efforts; you are making ubuntuforums a wonderful resource and a great place to hang out. I very much appreciate it. Hats off to all of you!

---

### Post by Elfy on 2008-10-17
I always ask people to cat the file in a terminal and post the output. I've never edited and posted a 'fixed' file either that I remember, I expect the op to do the real work after I've helped :)

I assume that even if errors are made the fixing of the whole adds to the learning experience.

---

### Post by hyper_ch on 2008-10-17
downloading config files et al. is a pain ;) they could [noparse]```

```[/noparse] them.... basic rule: "Help others to help you!" or put differently "don't make others require to do more work because you're lazy"

---

### Post by Elfy on 2008-10-17
> **hyper_ch said:**
> downloading config files et al. is a pain ;) they could [noparse]```

```[/noparse] them.... basic rule: "Help others to help you!" or put differently "don't make others require to do more work because you're lazy"

I hope I've misconstrued what you're saying here and are not saying that I'm lazy because I expect people to help themselves.

---

### Post by hyper_ch on 2008-10-17
no no, I agree with your forestpixie :)

---

### Post by Elfy on 2008-10-17
Glad I misconstrued you then :lol:

---

### Post by unutbu on 2008-10-17
Let's put aside the question of whether posting a complete menu.lst is too much help. There is still a road-block making life more difficult for a newbie to post his config files (be it .bashrc, fstab, menu.lst..)

Like forestpixie, I have mostly tried to use 'cat' and code tags instead of attachments. However, sometimes asking people to edit files can also be a source of problems. See for example:
[http://ubuntuforums.org/showthread.php?t=943390&highlight=ruby](http://ubuntuforums.org/showthread.php?t=943390&highlight=ruby)

The problem was solved in post #3, but the guy's editor was bungling the solution. The problem was not resolved until post #8 with an attachment and code to keep the editor out of the mix.

Btw, it is yet another example of posters (okay, me :)) having to circumvent the file attachment restriction.

---

### Post by cyberdork33 on 2008-10-17
> **hyper_ch said:**
> downloading config files et al. is a pain ;) they could [noparse]```

```[/noparse] them.... basic rule: "Help others to help you!" or put differently "don't make others require to do more work because you're lazy"
If posting a full, large config file (like an old xorg.conf) I'd rather have the attachment. It is a pain to scroll though 3 or 4 files in code tags.

---

### Post by imana86 on 2008-10-18
You have an outstanding good and well structured site. I enjoyed browsing through it.  ------ Tony ([Retro Jordans](http://www.2345kicks.com)).

---

### Post by drubin on 2008-10-20
I do not like the idea of having to download .sh users have the tendancy to give them  chmod 777 ./runstuff.sh  && ./runstuff.sh and away for away we are running  the remove command.

If they are posted as text every one passing by can at least have a look with out having to download. I just feel more comfortable knowing that the executable files are publicly being viewed all the time.

---

