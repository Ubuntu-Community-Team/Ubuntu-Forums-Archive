---
title: "Do you know of script or an app to replace blanks with a &quot;-&quot; in file names"
date: 2009-06-07
forum: General Help
---

### Post by paul_anders on 2009-06-07
I have mp3 and ebooks about 21gigs in total.
Do you know of script, command or an app to replace the blanks with a "-" in file names.

for example
the song name.mp3 (changed to something like) the-song-name.mp3

thank you
PA

---

### Post by unutbu on 2009-06-07
```
rename 's/ /-/g' *
```

---

### Post by paul_anders on 2009-06-07
thanks ubuntu for a real quick reply.

where does that "s" come from ?

as im not real good with building good functions from cli 
i did look at the man pages and saw this 

rename [ -v ] [ -n ] [ -f ] perlexpr [ files ]

so im lost what is the "s" for, what do it do. ?
does it mean substitute

[http://unixhelp.ed.ac.uk/CGI/man-cgi?rename](http://unixhelp.ed.ac.uk/CGI/man-cgi?rename)
however thanks again
PA

---

### Post by SeanTater on 2009-06-07
It's a perl regular expression (I think - I'm no perl programmer)

Most probably this is the syntax:

s/WHAT_TO_REPLACE/REPLACEMENT/g

BTW: I don't know if this is the case in perl, but you can usually use anything you like instead of /, as long as you use it everywhere, like this:

s|WHAT_TO_REPLACE|REPLACEMENT|g

or this
s:WHAT_TO_REPLACE:REPLACEMENT:g

---

### Post by paul_anders on 2009-06-07
thanks Sean

i knew the bash is powerful but didnt even know that it could use perl
untill now. DAM Linux gets better and better everyday. WOW

Thanks again
PA

---

### Post by ghostdog74 on 2009-06-07
> **paul_anders said:**
> I have mp3 and ebooks about 21gigs in total.
Do you know of script, command or an app to replace the blanks with a "-" in file names.

for example
the song name.mp3 (changed to something like) the-song-name.mp3

thank you
PA


if you want, you can use my Python script (check my sig, last item called File Renamer) eg usage

```

# python filerenamper.py -p " " -e "-" -l "*.mp3"

```
You can use -d <depth> to define how many levels of subdirectories you want to rename. eg
```

# python filerenamper.py -d 3  -p " " -e "-" -l "*.mp3"

```
remove "-l" option to commit changes.

---

