---
title: "Copy a filename into a simple text file"
date: 2008-12-30
forum: General Help
---

### Post by perrti-y02 on 2008-12-30
Hello,
I am looking for a bash command that allows me to take a filename (/data/Music/Artist/Album/Song.mp3) and put it into a file to make a playlist (/data/playlists/Albumname.m3u)

Is there a command that does this?

I am not looking for a program that will create playlists for me. I am doing it mostly for fun.

---

### Post by Slim Odds on 2008-12-30
> **perrti-y02 said:**
> Hello,
I am looking for a bash command that allows me to take a filename (/data/Music/Artist/Album/Song.mp3) and put it into a file to make a playlist (/data/playlists/Albumname.m3u)

Is there a command that does this?

I am not looking for a program that will create playlists for me. I am doing it mostly for fun.

```
ls -1 /data/Music/Artist/Album/Song.mp3 > filename
```

Check out the Advanced Bash Scripting Guide ([http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/))

---

### Post by perrti-y02 on 2008-12-30
Thanks for the quick reply
[COLOR="Red"]
tim@shuttle:/$ ls -l /data/Music/"Bryan Adams"/Reckless/* > /data/playlists/correct/Reckless.m3u[/COLOR]

was the command that I used and the output in the file was as follows

[COLOR="Red"]-rwxr-xr-x 1 tim tim 4914944 2008-12-01 20:59 /data/Music/Bryan Adams/Reckless/Aint Gonna Cry.ogg.mp3
-rwxr-xr-x 1 tim tim 4871302 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Heaven.ogg.mp3
-rwxr-xr-x 1 tim tim 3897728 2008-12-01 20:59 /data/Music/Bryan Adams/Reckless/Its Only Love.ogg.mp3
-rwxr-xr-x 1 tim tim 3113685 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Kids Wanna Rock.ogg.mp3
-rwxr-xr-x 1 tim tim 4770402 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Long Gone.ogg.mp3
-rwxr-xr-x 1 tim tim 5473599 2008-12-01 21:01 /data/Music/Bryan Adams/Reckless/One Night Love Affair.ogg.mp3
-rwxr-xr-x 1 tim tim 4666630 2008-12-01 20:59 /data/Music/Bryan Adams/Reckless/Run To You.ogg.mp3
-rwxr-xr-x 1 tim tim 3871806 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Shes Only Happy When Shes Dancin.ogg.mp3
-rwxr-xr-x 1 tim tim 5665354 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Somebody.ogg.mp3
-rwxr-xr-x 1 tim tim 4324877 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Summer Of 69.ogg.mp3[/COLOR]

Is there a way of getting rid of all the information in front of it?

---

### Post by perrti-y02 on 2008-12-30
Thanks for the quick reply
[COLOR="Red"]
tim@shuttle:/$ ls -l /data/Music/"Bryan Adams"/Reckless/* > /data/playlists/correct/Reckless.m3u[/COLOR]

was the command that I used and the output in the file was as follows

[COLOR="Red"]-rwxr-xr-x 1 tim tim 4914944 2008-12-01 20:59 /data/Music/Bryan Adams/Reckless/Aint Gonna Cry.ogg.mp3
-rwxr-xr-x 1 tim tim 4871302 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Heaven.ogg.mp3
-rwxr-xr-x 1 tim tim 3897728 2008-12-01 20:59 /data/Music/Bryan Adams/Reckless/Its Only Love.ogg.mp3
-rwxr-xr-x 1 tim tim 3113685 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Kids Wanna Rock.ogg.mp3
-rwxr-xr-x 1 tim tim 4770402 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Long Gone.ogg.mp3
-rwxr-xr-x 1 tim tim 5473599 2008-12-01 21:01 /data/Music/Bryan Adams/Reckless/One Night Love Affair.ogg.mp3
-rwxr-xr-x 1 tim tim 4666630 2008-12-01 20:59 /data/Music/Bryan Adams/Reckless/Run To You.ogg.mp3
-rwxr-xr-x 1 tim tim 3871806 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Shes Only Happy When Shes Dancin.ogg.mp3
-rwxr-xr-x 1 tim tim 5665354 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Somebody.ogg.mp3
-rwxr-xr-x 1 tim tim 4324877 2008-12-01 21:00 /data/Music/Bryan Adams/Reckless/Summer Of 69.ogg.mp3[/COLOR]

Is there a way of getting rid of all the information in front of it?

---

### Post by perrti-y02 on 2008-12-30
I have removed the -l and it did what I wanted it to. What does this -l actually do then?

---

### Post by Dr Small on 2008-12-30
> **perrti-y02 said:**
> I have removed the -l and it did what I wanted it to. What does this -l actually do then?
Please see the man page for ls.
The -l option shows the long format.

---

### Post by perrti-y02 on 2008-12-30
I have so far assembled my little script as follows:

#!/bin/bash
#make playlist

elsewhere="basename `pwd`"
here="pwd"
there="/data/playlists/correct/"$elsewhere".m3u"

touch $there
ls $here > $there

This, when run from the directory that I want to make my playlist from, gives the error of

/home/tim/bin/playlist: line 8: $there: ambiguous redirect

Why is this ambiguous?

Isn't there only one possible location for line 8?

I am confused

---

### Post by Slim Odds on 2008-12-30
> **perrti-y02 said:**
> I have so far assembled my little script as follows:

#!/bin/bash
#make playlist

elsewhere="basename `pwd`"
here="pwd"
there="/data/playlists/correct/"$elsewhere".m3u"

touch $there
ls $here > $there

This, when run from the directory that I want to make my playlist from, gives the error of

/home/tim/bin/playlist: line 8: $there: ambiguous redirect

Why is this ambiguous?

Isn't there only one possible location for line 8?

I am confused

you probably wanted:```
HERE=`pwd`
```

also, in my previous example is was a -1 not -l that I showed

---

### Post by Iandefor on 2008-12-30
> **perrti-y02 said:**
> I have so far assembled my little script as follows:

#!/bin/bash
#make playlist

elsewhere="basename `pwd`"
here="pwd"
there="/data/playlists/correct/"$elsewhere".m3u"

touch $there
ls $here > $there

This, when run from the directory that I want to make my playlist from, gives the error of

/home/tim/bin/playlist: line 8: $there: ambiguous redirect

Why is this ambiguous?

Isn't there only one possible location for line 8?

I am confusedThe problem is how you defined $elsewhere. It looks like you wanted to set it to the output of the command "basename`pwd`" Double-quotes are not appropriate in this case- you want to use backticks. Double-quotes cause bash to treat it as a literal string. 

What I would do instead of using the pwd command is to use the PWD environment variable. Hence,

elsewhere=`basename $PWD`

EDIT: Also, don't bother with the $here variable because we have $PWD for that.

---

### Post by perrti-y02 on 2008-12-31
I have changed some of the things suggested and the script now works for any album with a name 1 word long. If i try to do it for an album more than 1 word long it gets confused. e.g.

The script is now as follows

[COLOR="Red"]#!/bin/bash
#make playlist

elsewhere='basename $PWD'
here="$PWD/*"
there="/data/playlists/correct/$elsewhere.m3u"

touch "$there"
sudo ls -1f "$here" > "$there"[/COLOR]

If I do the following

[COLOR="Red"]tim@shuttle:/data/Music/Muse/Origin Of Symmetry$ playlist[/COLOR]

then this happens
[COLOR="Red"]
ls: cannot access /data/Music/Muse/Origin Of Symmetry/*: No such file or directory
[/COLOR]
If i try to get the "" around Origin Of Symmetry it doesn't change it at all, but is that even the problem I am hitting?

---

### Post by perrti-y02 on 2008-12-31
The script now doesn't actually work at all.

Don't know why but the one posted above gives this error for one word

[COLOR="Red"]tim@shuttle:/data/Music/The Beatles/Love$ playlist
ls: cannot access /data/Music/The Beatles/Love/*: No such file or directory[/COLOR]

---

### Post by perrti-y02 on 2008-12-31
I think the * is being seen as an asterix as opposed to and then whatever else you see.

Is this even true and is there a way to correct it?

---

### Post by perrti-y02 on 2008-12-31
It is a wildcard issue but I don't know how to solve it.

The "" make it just a star, `` tries to execute the mp3 files as a command and '' tries to access the file called $PWD/*

---

### Post by Iandefor on 2009-01-01
Try losing the quotes around $here on that last line, double-quoting causes bash to treat an asterisk as an asterisk and not a wildcard and you don't need them to use a variable. Also, the -f switch on ls I think is unnecessary unless you want to pull hidden files and . and .. into your playlist...

EDIT: thinking about this more...

You don't need the asterisk at all. In fact, the whole rigmarole with $here is pointless. Just ls -1 > $there because the default behavior of ls is to list the contents of the present working directory. $here is duplicating the functionality of $PWD which is itself unnecessary in this case.

Also, is there a reason ls needs sudo? The only thing I can think would be for the redirect but I don't recall that ever working. The way I recall it is that bash would run the sudo foo command then redirect the output to a file as a normal user. Unless you really need sudo to get ls to work I suggest you pipe ls as a normal user to the tee command, and if you need elevated permissions to run tee as sudo. Actually, a better solution would be to fix the permissions on your file so you don't _need_ sudo permissions to write to it at all. If you can create it you shouldn't need to change anything.

---

