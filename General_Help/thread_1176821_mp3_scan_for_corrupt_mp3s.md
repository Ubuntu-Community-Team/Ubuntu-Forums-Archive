---
title: "mp3 scan for corrupt mp3s"
date: 2009-06-02
forum: General Help
---

### Post by PGScooter on 2009-06-02
Does anyone use a tool to check the integrity of mp3 files?

I found two tools: mp3check and mp3val, but neither seems to be popular or talked about (a search on ubuntuforums yielded no results).

I tried mp3val since it seems to be the most recently updated and it found a lot of errors and was even able to fix them. After listening to 3 of the files that were fixed, I only noticed 1 that fixed something from what I could tell (before, there was a lot glitch sort of noise).

Are music players so advanced now that they can get by most errors? Am I missing a good tool that people use?

Thanks!

---

### Post by PGScooter on 2009-06-02
please note that I cross-posted on the multimedia subforum (I forgot about it before!):
[http://ubuntuforums.org/showthread.php?t=1176923](http://ubuntuforums.org/showthread.php?t=1176923)

---

### Post by MyR on 2009-06-02
I suspect almost no one has use for such a tool, which is unfortunate for you.  I bet you would have a better shot in the multimedia production subforum.

peace

---

### Post by swimfish on 2010-12-05
I would like to know how to remove bad mp3s as well.  i used some sort of mp3 processor with a GUI and it ran two different profiles on my mp3's.  I have one Music folder and anything that reasonably is worth keeping, I would like to keep.  if it has two many errors, then i need it gone. after using the two profiles using "mp3 diags" from ubuntu repo i am now fixing headers and tags on all my files in my Music folder, but now i am ready to purge anything that shouldn't qualify as a mp3.  

thanks

---

### Post by kartabosh on 2010-12-05
> **PGScooter said:**
> Does anyone use a tool to check the integrity of mp3 files?

I found two tools: mp3check and mp3val, but neither seems to be popular or talked about (a search on ubuntuforums yielded no results).

I tried mp3val since it seems to be the most recently updated and it found a lot of errors and was even able to fix them. After listening to 3 of the files that were fixed, I only noticed 1 that fixed something from what I could tell (before, there was a lot glitch sort of noise).

Are music players so advanced now that they can get by most errors? Am I missing a good tool that people use?

Thanks!

mp3diags is great for detecting corrupt mp3s not so great at fixing them (if you're a noob that is)

---

### Post by swimfish on 2010-12-05
any tips on fixing them and deleting all mp3s that are beyond repair ?  maybe a simple bash script ?

---

### Post by kartabosh on 2010-12-05
> **swimfish said:**
> any tips on fixing them and deleting all mp3s that are beyond repair ?  maybe a simple bash script ?

not one, i scanned my mp3 collection once, and repaired a few quite nicely so i decided to let it have its way with all of them and it screwed up big time
most of the problematic ones were the ones with multiple streams and mp3diags says that a mp3 should have exactly one so it decides to delete the other ones ruinig the whole mp3, i know they shouldn't have more than one stream but i'd rather have a working mp3 with multiple mp3 streams than a broken one with a ok file structure :)
it does however fix the VBR headers which confuse mp3 players (you know, like when you have a mp3 thats 4 minutes long and the player says its 3 hours long)

---

### Post by swimfish on 2010-12-05
i clearly have damaged mp3s and was wondering how i could find them all and delete them.  multiple streams ok.  mp3 diag was something i used before using a command line utility to attempt fixing them.

---

### Post by kartabosh on 2010-12-05
i'm not sure you can do anything about it, because technically they're flawless (at least mine)

---

### Post by swimfish on 2010-12-05
some of my mp3s have been shortened as a part of the repair process.  those i would like deleted as well.

---

### Post by kartabosh on 2010-12-05
well, as far as i know the modifications aren't logged anywhere so i don't think anyone could tell which ones were modified (maybe if you check the modification date on them you could, but that's not a reliable method)
if you find anything let me know :)

---

### Post by Boondoklife on 2010-12-05
Hey hows is? I don't know of a way to detect broken mp3s via bash, but you could try using a command line app called mp3gain.

If you run the app against your mp3s it will tell you if it can not  process a file it will throw an error "Can't find any valid MP3 frames  in file"

with this in mind we could try this.
```
find . -type f -name "*.mp3" | xargs mp3gain 2>&1 | grep  "Can't find any valid MP3 frames in file" > /tmp/mp3.log
```

this would ran from the dir that has mp3s. note it will run recursive so  if you have all your mp3s in folders, run it in the parent folder to  scan them all.

---

### Post by swimfish on 2010-12-05
that script wouldn't execute properly from my parents Music folder.  mp3gain is installed.  a blank mp3.log file is created.  

were anyone to fix it, could the log be used to remove each defective mp3 one by one without prompting ?

thanks

---

### Post by swimfish on 2010-12-05
i found a package in the repo called mp3val and it has a -p pipe input setting though i dont't know how to pipe directory contents into mp3val so it can attempt to fix them all.  i believe i picked up that it was the best mp3 fixer / validator but piping output to it, i've no idea, for a file list.

---

### Post by Boondoklife on 2010-12-05
Try taking off the last bit and seeing if you get any output

```

find . -type f -name "*.mp3" | xargs mp3gain 2>&1 | grep  "Can't find any valid MP3 frames in file"

```This should spit the output to your commandline. If you still do not see anything then try

```

find . -type f -name "*.mp3" | xargs mp3gain 2>&1

```This will spit ALL output, this will show valid mp3s and invalid

On a side note, make sure of the case in your files, mp3 is different from MP3 and Mp3 and mP3. You can change it in the code if you need to.

If you find your files have different formats for the extention then try this:
```

find . -type f -iregex '.+\.mp3' | xargs mp3gain 2>&1 | grep  "Can't find any valid MP3 frames in file" > /tmp/mp3.log

```

---

### Post by swimfish on 2010-12-07
for some reason when i ran the find command from within my ~/Music directory mp3gain never even started to look for files to validate.

within ~/Music 

find -type f -name '*.mp3' | mp3val -f -nb -p > log.txt

and 

grep '^ERROR:' log.txt | awk -F '"' '{ print $2 }' | xargs -0 -i rm '{}'

both those commands and mp3val would validate and remove bad mp3s.  some slipped through the cracks, and are still too far gone.

in your second find command xargs is wanting a -0 switch but it cannot be applied.

---

### Post by Boondoklife on 2010-12-08
That is odd as the commands work just fine on my side, and I don't have anything saying it needs the -0 option?

Though if you were going to use the -0 option, you should append -print0 to your find command to ensure it is outputting in a format xargs can take.

---

### Post by swimfish on 2010-12-08
this is what i get:

find . -type f -name "*.mp3" | xargs -0 -print0 mp3gain 2>&1
xargs: argument line too long

---

### Post by Boondoklife on 2010-12-08
This is the proper syntax
```

find . -type f -iregex '.+\.mp3' -print0 | xargs -0 mp3gain 2>&1 | grep  "Can't find any valid MP3 frames in file" > /tmp/mp3.log

```If your files have spaces in the name, then that would explain the problems; The print0 and 0 flags will fix it though. You can use your mp3val app in place of mp3gain if it does what you are looking for.

---

### Post by swimfish on 2011-02-18
i've tried all of these from my parents ~/Music folder

bobcat@oceana:~/Music$ find . -type f -iregex '.+\.mp3' | xargs mp3gain 2>&1 | grep  "Can't find any valid MP3 frames in file" > mp3.log
bobcat@oceana:~/Music$ cat mp3.log
bobcat@oceana:~/Music$ find . -type f -name "*.mp3" | xargs mp3gain 2>&1 | grep  "Can't find any valid MP3 frames in file" > allbad.log
bobcat@oceana:~/Music$ cat allbad.log
bobcat@oceana:~/Music$ sudo find . -type f -name "*.mp3" | xargs mp3gain 2>&1 | grep  "Can't find any valid MP3 frames in file" > /tmp/mp3.log

it does not search for a single thing.  

i would also like the log dumped to user mp3 dir as mp3del.log 

i have this script

[http://pastebin.com/YsZDwEjT](http://pastebin.com/YsZDwEjT)

and this script to remove mp3info detected bad files

[http://pastebin.com/KLpC6AeV](http://pastebin.com/KLpC6AeV)

and that does work.  

i would like to do one run through inside my ~/Music and have it go in and out every folder checking for good or bad mp3 using mp3gain and then log to parent directory mp3bad.log or some such.  then i'd like a script that will nuke every no valid frame mp3 file that is containted within the log.  

one last think i hope to accomplish is to do another -Rf ~/Music search (you catch my drift) and delete all mp3s that are 25 seconds or shorter.  perhaps mp3gain will get those before i do that run as well.

thank you all for your time, you too Boondock

---

### Post by swimfish on 2011-02-18
my bad -- this right here *IS* creating a mp3.log file for me 

find . -type f -iregex '.+\.mp3' -print0 | xargs -0 mp3gain 2>&1 | grep  "Can't find any valid MP3 frames in file" > /tmp/mp3.log
anyone know an easy way to delete those files in the log ?

thank you

still need to know how to delete 25 second or shorter mp3 songs for the utlimate clean up.

---

### Post by swimfish on 2011-02-18
actually  -- that log file ended up having 0 bytes.  not sure what to think of that.  if it had no matches, then cool.  i don't know how i'd get cut off mp3's and have it still pass that bash parameter so if anyone can write a one liner or a script to nuke -Rf inside of ~/Music all files that are 25 seconds or less.

thanks guys and gals !

---

### Post by Boondoklife on 2011-02-18
Can you put an a few example bad mp3's up somewhere so I can download and play with them. I have a little time at the moment and will try to help ya out.

---

### Post by williamts99 on 2011-02-18
One tool that I have used in the past is Musicbrainz Picard.  It's great for tagging, but it also will do an 'audio fingerprint' of the file and see if it matches their database.  If it doesn't match, then you will know that it is corrupt.
[http://musicbrainz.org/doc/MusicBrainz_Picard](http://musicbrainz.org/doc/MusicBrainz_Picard)

---

