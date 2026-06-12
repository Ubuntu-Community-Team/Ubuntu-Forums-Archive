---
title: "Shell script will not run"
date: 2009-06-05
forum: General Help
---

### Post by Rayn on 2009-06-05
Ok so basically I need to get 4500 lines of texts into 4500 different files throughout my directory structure

I used EXCEL to generate a series of commands

pasting them into putty works, but after about 30, the terminal freezes and nothing happens

so I put them in a script.

why can't I get this to work?


echo2.pl:
```

echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"1\"/>" > "/var/lib/mythtv/videos/Videos/TV/Rome/rome.201.hdtv.xvid.notv.nfo"
echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"2\"/>" > "/var/lib/mythtv/videos/Videos/TV/Rome/rome.202.hdtv-lol.nfo"
echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"3\"/>" > "/var/lib/mythtv/videos/Videos/TV/Rome/rome.203.hdtv-lol.nfo"
echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"4\"/>" > "/var/lib/mythtv/videos/Videos/TV/Rome/rome.204.hdtv-lol.nfo"
```

result:
```

root@myth:/var/lib/mythtv/videos/Videos# sh echo2.pl
: Directory nonexistentate /var/lib/mythtv/videos/Videos/TV/Rome/rome.201.hdtv.xvid.notv.nfo
: Directory nonexistentate /var/lib/mythtv/videos/Videos/TV/Rome/rome.202.hdtv-lol.nfo
: Directory nonexistentate /var/lib/mythtv/videos/Videos/TV/Rome/rome.203.hdtv-lol.nfo

```

quotes removed completely:
```
echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"1\"/>" > /var/lib/mythtv/videos/Videos/TV/Rome/rome.201.hdtv.xvid.notv.nfo
echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"2\"/>" > /var/lib/mythtv/videos/Videos/TV/Rome/rome.202.hdtv-lol.nfo
echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"3\"/>" > /var/lib/mythtv/videos/Videos/TV/Rome/rome.203.hdtv-lol.nfo
echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"4\"/>" > /var/lib/mythtv/videos/Videos/TV/Rome/rome.204.hdtv-lol.nfo
```
result:
```
root@myth:/var/lib/mythtv/videos/Videos# sh echo2.pl
: Directory nonexistentate /var/lib/mythtv/videos/Videos/TV/Rome/rome.201.hdtv.xvid.notv.nfo
: Directory nonexistentate /var/lib/mythtv/videos/Videos/TV/Rome/rome.202.hdtv-lol.nfo
: Directory nonexistentate /var/lib/mythtv/videos/Videos/TV/Rome/rome.203.hdtv-lol.nfo

```

directory exists...
> root@myth:/var/lib/mythtv/videos/Videos# cd TV
root@myth:/var/lib/mythtv/videos/Videos/TV# cd Rome
root@myth:/var/lib/mythtv/videos/Videos/TV/Rome# 

what am I missed here?
running any of these commands on the terminal alone works just fine, but I can't put in 4500 of them 1 at a time.

---

### Post by benj1 on 2009-06-05
try prefixing 'sudo' to the commands

---

### Post by Rayn on 2009-06-05
SOLVED:

run dos2linux on scripts you made in a windows environment :P

---

### Post by Boondoklife on 2009-06-05
I know this is a little late but why not just do somethng like this:
```
#!/bin/bash

SEASON=2
for i in `seq 1 10`;
do
    EPISODE=$((($SEASON*100)+$i))
    echo "<thetvdb seriesid=\"73508\" season=\"2\" episode=\"$i\"/>" > blah/blah.$EPISODE.hdtv-lol.nfo
done

```You would have to do some substituting for names or you could just mod the script to pass it on the command line. OR you could even have it generate it based on the already existing names of files.

---

### Post by KyleBrandt on 2009-06-05
> **Rayn said:**
> SOLVED:

run dos2linux on scripts you made in a windows environment :P

You can also:
```
cat oldfile | tr -d '\r' > newfile
```

---

### Post by Rayn on 2009-06-05
Will that eliminate the need to use dos2linux?  It'd be easier for the user I am working on this for.

---

### Post by KyleBrandt on 2009-06-05
> **Rayn said:**
> Will that eliminate the need to use dos2linux?  It'd be easier for the user I am working on this for.

Well this deletes the carriage returns, I don't think dos2linux does anything more than that, but could be wrong...

---

