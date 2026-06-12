---
title: "Cleaning Ubuntu"
date: 2006-07-26
forum: Desktop Environments
---

### Post by music_man on 2006-07-26
Hi

Is there a disk cleanup utility for Ubuntu?

Cheers

---

### Post by Uncle Spellbinder on 2006-07-26
I seem to remember a sudo command that included "clean".  Hopefully someone will post it.

---

### Post by avtolle on 2006-07-26
Uncle Spellbinder: the command is sudo apt-get clean.

Music_Man: From your post, I assume (yes, I know how dangerous that is ;) ) you are referring to defrag. Due to the way Linux handles its file systems, defragging the drive is really not needed. There are some threads in the forum which explain this much better than I can. If I'm in error on my assumption (highly probable, I'm sure), please post again with a bit more clear description of what you are after.

---

### Post by music_man on 2006-07-26
> **avtolle said:**
> Uncle Spellbinder: the command is sudo apt-get clean.

Music_Man: From your post, I assume (yes, I know how dangerous that is ;) ) you are referring to defrag. Due to the way Linux handles its file systems, defragging the drive is really not needed. There are some threads in the forum which explain this much better than I can. If I'm in error on my assumption (highly probable, I'm sure), please post again with a bit more clear description of what you are after.

There is a Disk Cleanup utility...

---

### Post by snellgrove on 2006-07-26
I dont think he mean't a 'defrag' utility.

These don't generally exist, as the ext3 file system saves 5% of your disk space as slack, for things to expand into. Its quite good, but not perfect. and you lose 5% of your available disk space - ouch.

The best way to 'defrag' a file system on linux, is to copy the contents of the drive off, format it, and then copy things back.

as for typing in:

```
sudo apt-get clean
```

this will only remove the cached package files that apt-get downloads. (for example, if you install a program such as filelight, it will keep the .deb in a place called /var/cache/apt/archives so if you need to re-install, or if you uninstall and then later need it again..  it wont bother the Ubuntu servers (and make you wait!) by fetching it, and then installing. it'll just install from the .deb from that folder :)

You can clean this folder out by typing in, also:

```
sudo apt-get autoclean
```

I found a handy thread ages ago, about all the ways you can save disk space.. I'll try and find it :)

:edit:

yipee... found it :p 

[enjoy - click here.](http://www.ubuntuforums.org/showthread.php?t=140920&highlight=cleaning+ubuntu)

---

### Post by music_man on 2006-07-26
I did the instructions on that thread. Thanks so much!

I think I may make a launcher button so I can click it and it goes. How does logging in work with that?

---

### Post by airtonix on 2006-08-02
you use zenity....

for a start open a terminal and install leafpad (its a better text editor for doing quick stuff than leafpad).

> sudo apt-get install leadpad 

then, open up your nautilis-scripts folder by typing

> sudo nautilus ~/.gnome2/nautilus-scripts

after which you will want to star the bash script off like this 

> #!/bin/bash\

it is a header that acts like the <html>  and ?php monikeers... (loosely)..they tell the parse what kind of document language is being expected.

next you will either want to use a series of piped command or work out your logic flow for the use of stored values.

ie : this is how i update the dyndns of my webserver 
> 
#!/bin/bash
gksudo 'ddclient -verbose' | zenity --text-info --width=720 --height=430 &


imho using a series of piped commands could be better due to the lack of variables lying around waiting for you to clear them....

any thoughts peoples?

---

### Post by airtonix on 2006-08-02
you use zenity....

for a start open a terminal and install leafpad (its a better text editor for doing quick stuff than gedit)

> sudo apt-get install leafpad  
then, open up your nautilus-scripts folder by typing

> sudo nautilus ~/.gnome2/nautilus-scripts 
after which you will want to start the bash script off like this 

> #!/bin/bash

it is a header that acts like the <html>  and ?php monikeers... (loosely)..they tell the parse what kind of document language is being expected.

next you will either want to use a series of piped command or work out your logic flow for the use of stored values.

ie : this is how i update the dyndns of my webserver 
> 
#!/bin/bash
gksudo 'ddclient -verbose' | zenity --text-info --width=720 --height=430 &
 
imho using a series of piped commands could be better due to the lack of variables lying around waiting for you to clear them....

any thoughts peoples?:-k

---

### Post by cantormath on 2006-08-02
> **music_man said:**
> Hi

Is there a disk cleanup utility for Ubuntu?

Cheers

What do you want to clean up?

---

### Post by ifergus on 2008-01-29
kleansweep is a kde cleaning program install using synaptic or apt-get,
be careful with it though.

this page may help too [http://www.ubuntu-unleashed.com/2007/09/clean-up-ubuntu-junk-files.html](http://www.ubuntu-unleashed.com/2007/09/clean-up-ubuntu-junk-files.html)
:popcorn:

---

