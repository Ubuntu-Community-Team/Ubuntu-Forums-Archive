---
title: "36 MKV parts - Having trouble merging them."
date: 2009-04-14
forum: General Help
---

### Post by simak on 2009-04-14
I installed MKVmerge but it gives me error when I try appending the rest of files. Firstly, it doesnt even see it as supported media, probably becasue of the fact that the files are:

*.mkv.001 ..... *.mkv.036

I tried using cat, ( yes I did paste it 36 times as my last effort ), but i got some error. Maybe I made a mistake somewhere, maybe wrong use of cat.

But a bigger question is, how to merge them when there are so many. Someone has certainly thought of some kind of string that automatically picks up *.001 *.036 for exmpl. 

I have around 6 files that are split into 36 files. And more incoming soon.
I could always boot to windows to get some idiotic program to do it, but I dont want to give in! 

There has to be a way!! :) If someone could show it to me.

( i tried searching these forums but i havent found any threads about this exact problem )

best regards,

---

### Post by mb_webguy on 2009-04-14
What exactly are these files?  They don't look like audio or video streams.

What you have looks more like some sort of archive.  What does the Type column in Nautilus say for the files?  (Alternatively, you could right-click the file, select Properties, and look at the Type line on the Basic tab.)

---

### Post by simak on 2009-04-14
They are Matroska stream (application/x-matroska). Type confirms it.

I can even play mkv.001 in the mplayer. Of course it just shows the really small part of the series.

---

### Post by mb_webguy on 2009-04-14
Hrm.  Are you using the command-line version of mkvmerge, or the GUI?

---

### Post by simak on 2009-04-14
GUI version.

It was my bad i think. The first file is only mkv type. all the other mkv.002 - mkv.036 are unknown types.

I was thinking, maybe it doesnt have to do anything with mkv. Maybe i should just use a normal merger or soemthing.
I am thinking of this because mkvmerge doesnt see *.mkv.001 as supported media file.

After first 'add' click, on mkv.001 it works. But when i try 002 it gives me the error, unknown type. Which is logical since Nautilus doesn't recognize the type either.

---

### Post by mb_webguy on 2009-04-14
Try identifying the parts using the "file" command in the terminal.  It probably won't work if Nautilus can't identify them, but it's worth a try.

And you say you've tried "cat file1 file2 file3 ..." to merge the files?

---

### Post by simak on 2009-04-14
I downloaded someething else with only 11 parts.

Cat worked now. I had to type in all this though.. :(

```
 "[HorribleSubs] Shangri-la - 01 [480p].mkv.001" "[HorribleSubs] Shangri-la - 01 [480p].mkv.002" "[HorribleSubs] Shangri-la - 01 [480p].mkv.003" "[HorribleSubs] Shangri-la - 01 [480p].mkv.004" "[HorribleSubs] Shangri-la - 01 [480p].mkv.005" "[HorribleSubs] Shangri-la - 01 [480p].mkv.006" "[HorribleSubs] Shangri-la - 01 [480p].mkv.007" "[HorribleSubs] Shangri-la - 01 [480p].mkv.008" "[HorribleSubs] Shangri-la - 01 [480p].mkv.009" "[HorribleSubs] Shangri-la - 01 [480p].mkv.010" "[HorribleSubs] Shangri-la - 01 [480p].mkv.011" > Shangri-La01.mkv
```

Though I have a question, there must be a workaround for not having to type 36 times a very long name and just add .001 .002 .003.

Long time ago I saw someone use some command after cat. something like /*. or something similar, in order to let it automatically detect 001-036.

Does this exist or am I wrong ?

---

### Post by mb_webguy on 2009-04-15
> **simak said:**
> I downloaded someething else with only 11 parts.

Cat worked now. I had to type in all this though.. :(

```
 "[HorribleSubs] Shangri-la - 01 [480p].mkv.001" "[HorribleSubs] Shangri-la - 01 [480p].mkv.002" "[HorribleSubs] Shangri-la - 01 [480p].mkv.003" "[HorribleSubs] Shangri-la - 01 [480p].mkv.004" "[HorribleSubs] Shangri-la - 01 [480p].mkv.005" "[HorribleSubs] Shangri-la - 01 [480p].mkv.006" "[HorribleSubs] Shangri-la - 01 [480p].mkv.007" "[HorribleSubs] Shangri-la - 01 [480p].mkv.008" "[HorribleSubs] Shangri-la - 01 [480p].mkv.009" "[HorribleSubs] Shangri-la - 01 [480p].mkv.010" "[HorribleSubs] Shangri-la - 01 [480p].mkv.011" > Shangri-La01.mkv
```

Though I have a question, there must be a workaround for not having to type 36 times a very long name and just add .001 .002 .003.

Long time ago I saw someone use some command after cat. something like /*. or something similar, in order to let it automatically detect 001-036.

Does this exist or am I wrong ?

You should have been able to use something like this:```
cat "[HorribleSubs] Shangri-la - 01 [480p].mkv."*
```The "*" is a wildcard, that basically stands for anything.  So "cat foo*" would concatenate all files in the current directory that begin with the letters "foo".  Filenames with spaces or other special characters must either be enclosed in quotes or else have those special characters preceeded with a backslash, since commands usually separate arguments (like filenames) by spaces.  In this case, the "*" would go after the quotes, since you aren't looking for a file that actually contains a "*".

---

### Post by simak on 2009-04-15
That works!! 

I'd like to thank you for your help and patience! 
All the best!

---

### Post by binbash on 2009-04-15
you can join them with lxsplit

---

