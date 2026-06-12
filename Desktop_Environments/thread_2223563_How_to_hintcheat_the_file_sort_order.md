---
title: "How to hint/cheat the file sort order?"
date: 2014-05-11
forum: Desktop Environments
---

### Post by mtfr on 2014-05-11
On Windows I used to name some important folders surrounded by the "-" or "#" characters, to force the sorting to place them on top (e.g. the Rock subfolder in my Audio folder :P ). Coming to Ubuntu it seems to be doing something clever. It ignores the punctuation characters, and will casually resolve the "- rock -" folder sorting between the P and S folders.

This is too clever and I don't need this behaviour. What kind of trick do you guys use on Linux to cheat the sort order?

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-05-11
a trick would be to name something like 'a_rock' or 'a rock'. . . that might help! actually i never neither think nor used it

---

### Post by vasa1 on 2014-05-11
> **mtfr said:**
> ..
This is too clever and I don't need this behaviour. What kind of trick do you guys use on Linux to cheat the sort order?
AFAIK, there's no way other than to prefix the name with letters or numbers.
Anyway, if this is a dealbreaker, there's always Windows :)

---

### Post by steeldriver on 2014-05-11
Fundamentally, the sort order *should* be determined by your locale settings (in particular, the LC_COLLATE environment variable) - for instance in the terminal if I have a directory containing the following listing (in the default order for my locale)

```

$ ls tests
a  -a-  #a  b  -b-  #b  c  -c-  #c

```

then if I specify a C locale on the command line instead I get

```

$ LC_COLLATE=C ls tests
#a  #b  #c  -a-  -b-  -c-  a  b  c

```

You *may* be able to do the same with nautilus, either via a config setting (gconf / gsettings) or via the environment - at least that should give you some search terms to try.

---

### Post by QIII on 2014-05-11
To ensure portability, some filesystems that follow the Posix specification generally do not allow # in the filename and treat both . and - as hidden files.

I really haven't looked into it because I haven't used some characters I've been avoiding for 35 years for, well, 35 years.  Reserved "words" or characters in the shell, for instance.

There are always ways to get around things, if you don't mind creating potential problems for yourself.

There's a pretty good discussion [here]("http://www.dwheeler.com/essays/fixing-unix-linux-filenames.html").

---

### Post by vasa1 on 2014-05-11
> **QIII said:**
> ...
There are always ways to get around things, if you don't mind creating potential problems for yourself.
Very true. I'm doing my best to use letters, hyphen, underscore and numbers only. I got bitten once.
> **QIII said:**
> There's a pretty good discussion [here]("http://www.dwheeler.com/essays/fixing-unix-linux-filenames.html").Bookmarked! But I'm going to save a copy locally and format it a bit. Right now, it's a bit "wall-of-text".

---

### Post by mtfr on 2014-05-15
> **QIII said:**
> To ensure portability, some filesystems that follow the Posix specification generally do not allow # in the filename and treat both . and - as hidden files.

I really haven't looked into it because I haven't used some characters I've been avoiding for 35 years for, well, 35 years.  Reserved "words" or characters in the shell, for instance.

There are always ways to get around things, if you don't mind creating potential problems for yourself.

There's a pretty good discussion [here]("http://www.dwheeler.com/essays/fixing-unix-linux-filenames.html").

Thanks, this was an interesting read (I sifted through, didn't honestly read all :) ), too bad file systems couldn't figure a good standard after so many tens of years. But nevertheless, glad we're out of the woods after that 8.3 FAT 16. Speaking of which, it's beyond ridiculous how to this day Microsoft tries to use 8.3 file names in its products where possible.

---

### Post by mtfr on 2014-05-15
> **steeldriver said:**
> Fundamentally, the sort order *should* be determined by your locale settings (in particular, the LC_COLLATE environment variable) - for instance in the terminal if I have a directory containing the following listing (in the default order for my locale)

```

$ ls tests
a  -a-  #a  b  -b-  #b  c  -c-  #c

```

then if I specify a C locale on the command line instead I get

```

$ LC_COLLATE=C ls tests
#a  #b  #c  -a-  -b-  -c-  a  b  c

```

You *may* be able to do the same with nautilus, either via a config setting (gconf / gsettings) or via the environment - at least that should give you some search terms to try.

Thanks man. I like the case insensitivity of the non-C collation. And also, as a general principle of trying to find the most universal solution, instead of changing the locale I chose to use a zero character prefix to force the folder to be top sorted. So my "- rock -" or "# rock #" folder is now "000 rock 000" :D Also a minor throwback to the old ASCII .nfo days :D

---

### Post by oldrocker99 on 2014-05-16
I personally put wanted folers at the top by renamnig them with a leading zero.

---

