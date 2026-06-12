---
title: "Wget help"
date: 2008-12-05
forum: General Help
---

### Post by glotz on 2008-12-05
Hi there!

I'd like to get the ogg files from [http://www.archive.org/details/ym1999-10-21.shnf](http://www.archive.org/details/ym1999-10-21.shnf) with Wget, how would I go about that?

I tried reading the manual page and there was an example that looked quite similar, the one about gif files. However, it didn't work. I just got some folders and a robots.txt file. However, I did manage to wget the first ogg file by just pointing wget to the URL, so I think it can be made to work. They also offer a list view [http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf](http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf)

Anybody around here with some Wget-fu got a minute?

---

### Post by Ayuthia on 2008-12-05
Are you able to download the file if you do something like this:
```
wget -c http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf/ym1999-10-21d1t01.ogg
```

Is that what you are looking for?  The -c will allow the file to continue downloading where it left off if for some reason the connection disconnects.

---

### Post by glotz on 2008-12-05
Thanks for the reply. I got the one file just fine. I'd like to get them all now. Of course I could do it manually but I'm sure there's a better way for lazy people like yours truly.

---

### Post by kuhlbeans on 2008-12-05
I believe that the -r (recursive) option will get all the files in a directory.

---

### Post by Ayuthia on 2008-12-05
Without having to write a script, you could also attach multiple files on one line:
```
wget -c http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf/ym1999-10-21d1t01.ogg http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf/ym1999-10-21d1t02.ogg
```

I am not for sure how many can fit into one line though.

---

### Post by glotz on 2008-12-05
Thanks again guys. Still not exatly what I want. I don't want the mp3 files or anything else besides the oggs. And I'd like to find out how to do it the smart way. :)

---

### Post by Ayuthia on 2008-12-05
Are you able to access the site via ftp?  I am not for sure if it will ask for a username or password.  If it does not, you would be able to get the files that way.  I would try it out, but I currently don't have ftp installed (currently using gentoo).

---

### Post by glotz on 2008-12-05
Well for the heck of it I tried ftp. They don't do passive mode. Don't like it otherwise.

I'm sure there's a simple wget one liner to get this simple job done. And out there's somebody who knows it.

---

### Post by kuhlbeans on 2008-12-05
Sorry, didn't realize there were other files in the directory.  You can use the -A (or --accept) option.

wget -A ogg [http://whatever/it/is](http://whatever/it/is)

You can read more about it in the wget manual.

---

### Post by glotz on 2008-12-06
No worky. :confused:

**wget -A ogg [http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf/](http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf/)**
--10:30:51--  [http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf/](http://ia301113.us.archive.org/2/items/ym1999-10-21.shnf/)
           => `index.html'
Resolving ia301113.us.archive.org... 207.241.225.214
Connecting to ia301113.us.archive.org|207.241.225.214|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,164 (11K) [text/html]

100%[====================================>] 11,164        46.59K/s             

10:30:51 (46.47 KB/s) - `index.html' saved [11164/11164]

---

### Post by kuhlbeans on 2008-12-07
Ah yes, it's been a while.  Accept lists require a recursive search.

wget -r -l1 --no-parent -A.mp3 [http://your/site/dir/](http://your/site/dir/)

-r is recursive, -l# is the number of levels to go, no parent says ignore the parent directory.

---

### Post by glotz on 2008-12-07
Does that work for you? It sure doesn't for me. All I get is some empty folders and an index.html.

---

### Post by kuhlbeans on 2008-12-08
To be honest, I was never testing it the particular link you provided.  It *does* work on a normal server with a normal directory listing.  The problem with archive.org is that, if you had paid attention, when you click the download in your browser the link gets redirected to a different URL entirely to actually get the file.  I tried it on that URL and wget ends up downloading some folders and the robots.txt, but no other files.  I'm not sure if their server is identifying the wget request as a robot and rejecting it or if wget has some way around this, but I'm not sure what it is.

---

### Post by aktiwers on 2008-12-08
Usually this works:
```
wget -r -np -A ogg -l 2 www.url.com/folder/
```

But in this case it does not. It seams like the site has protected against robots.
I use that command often, just replace ogg with any extension and it will only grab files with that extension.

---

### Post by Sjums07 on 2009-01-05
Doesnt work :(

[http://www.musicindexof.com/2008/07/21/a-tribute-to-abba/](http://www.musicindexof.com/2008/07/21/a-tribute-to-abba/)

The site,

---

### Post by aktiwers on 2009-01-06
Yes it works great on that site!

To grab all mp3's do this:
```
 wget -r -np -A mp3 -l 2 _http://www.ventsi.com/Music/A%20Tribute%20To%20ABBA/_[]("http://www.ventsi.com/Music/")
```Notice that the url is a little different from yours. If you hold your mouse over one of the links, you will see (in the lower-left corner of firefox) that the files are located there. Or simply right-click and pick "copy link location" to find the location folder.

---

### Post by Sjums07 on 2009-01-09
lol :p ty :D my bad xD i should just watch it a little better :p

---

