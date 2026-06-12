---
title: "Glest 2.0.0-1 installed..now what?"
date: 2007-11-22
forum: Gaming &amp; Leisure
---

### Post by Lor Boo on 2007-11-22
I just installed Glest 2.0.0-1 for some fun via this page:
[http://linuxgames07.blogspot.com/200...nux-games.html](http://linuxgames07.blogspot.com/200...nux-games.html)

And now that it's installed... 
```

drinky@drinkyvador:~$ cd Desktop
drinky@drinkyvador:~/Desktop$ sudo dpkg -i glest-data_2.0.0-1~getdeb1_all.deb
[sudo] password for drinky:
Selecting previously deselected package glest-data.
(Reading database ... 106134 files and directories currently installed.)
Unpacking glest-data (from glest-data_2.0.0-1~getdeb1_all.deb) ...
Setting up glest-data (2.0.0-1~getdeb1) ...

drinky@drinkyvador:~/Desktop$ killall gnome-panel
drinky@drinkyvador:~/Desktop$ glest
bash: glest: command not found
drinky@drinkyvador:~$ Glest
bash: Glest: command not found

```


I don't know how to run it. I mean. Honestly, what do I do?

There is no icon in the GUI.
I ran killall gnome-panels. I tried Glest in terminal. I searched for it using - Places - Search for Files. And here - It finds the downloaded files on the desktop... but if I tell it to search the 'FileSystem' It finds NOTHING. That includes the files on the desktop which I found earlier when I searched my home folder. So what the hell is the 'Search FileSystem' Searching? Root folder only?


So here I am in the forums to find the missing page of the howto.
I understand RTFM. I've got a few certs. I've done a few years of tech support. I know pibcac (problem exists between computer and chair).... but yet... when that last mile is missing....
Man does it make me feel like I'm stupid.

---

### Post by Lor Boo on 2007-11-22
Might have figured it out:
I checked the pages again and seen a second file there not mentioned
in the walkthrough.

Downloaded him and ran it to this new error:
```

drinky@drinkyvador:~/Desktop$ sudo dpkg -i glest_2.0.0-1~getdeb1_i386.deb 
[sudo] password for drinky:
Selecting previously deselected package glest.
(Reading database ... 107803 files and directories currently installed.)
Unpacking glest (from glest_2.0.0-1~getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of glest:
 glest depends on libxerces27; however:
  Package libxerces27 is not installed.
dpkg: error processing glest (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 glest
drinky@drinkyvador:~/Desktop$ 


```

but I think I saw posting or two about this so I may be able to resolve this this afternoon after I do some off computer running around.

Thanks.
Lor Boo

---

### Post by Lor Boo on 2007-11-22
So this evening an update tells me there's a problem and to run:

sudo apt-get install -f

Which I do... 
and presto.. 
now I have Glest Icon in the Games folder.
And it works.  :guitar:

---

### Post by pokkets on 2008-03-04
I had some trouble with a few games downloading from repoubuntu source, but Thee Mahn from Ubuntu ultimate said that he was uploading 8 GB which might take some time,and to expect some 404 file not found for a while. and the files that were missing were the data files. There's the header, less than a megabyte sometimes, and data files which can be big. glest is about 65mb. I was told to do an apt-get -f install same think I thing, and it goes to the repository to get the missing dependencies. There are still file not found, so I found this site which has all sorts of debian packages. I'm going to fix my broken packages there
[http://www.getdeb.net/browse.php](http://www.getdeb.net/browse.php)

---

