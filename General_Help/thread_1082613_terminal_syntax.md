---
title: "terminal syntax"
date: 2009-02-28
forum: General Help
---

### Post by pmooney78 on 2009-02-28
I have experience using command-line processing under Windows but am having a hard time making the transition to the Linux bash terminal. Nothing seems to work the way I expect it to.

For instance, I'm trying to transcode aac files in an .m4a wrapper to mp3 by using a command like this:

```

for i in $(ls $m4a); do faad -o - | lame --replaygain-accurate -h -v 2 --ta Anathallo --tl "Floating World" --pad-id3v2 --id3v2-only -${i%m4a}.mp3; done

```

All I get is a bunch of output errors saying that various files can't be found. As far as I can tell, the problem is that the filenames contain spaces. But renaming all of the files one at a time to remove spaces is too much trouble. Quoting the variable containing filename on the command line doesn't seem to help.

Any suggestions?

---

### Post by andrew.46 on 2009-02-28
Hi pmooney,

> **pmooney78 said:**
> [...] I'm trying to transcode aac files in an .m4a wrapper to mp3 [...] Any suggestions?

You are making life a little hard for yourself :-). Best way might be to use a program like FFmpeg particularly if you are interested in a commandline method. Try [HOWTO: Install and use the latest FFmpeg and x264]("http://ubuntuforums.org/showthread.php?t=786095"). 

Andrew

---

### Post by lloyd_b on 2009-02-28
> **pmooney78 said:**
> I have experience using command-line processing under Windows but am having a hard time making the transition to the Linux bash terminal. Nothing seems to work the way I expect it to.

For instance, I'm trying to transcode aac files in an .m4a wrapper to mp3 by using a command like this:

```

for i in $(ls $m4a); do faad -o - | lame --replaygain-accurate -h -v 2 --ta Anathallo --tl "Floating World" --pad-id3v2 --id3v2-only -${i%m4a}.mp3; done

```

All I get is a bunch of output errors saying that various files can't be found. As far as I can tell, the problem is that the filenames contain spaces. But renaming all of the files one at a time to remove spaces is too much trouble. Quoting the variable containing filename on the command line doesn't seem to help.

Any suggestions?

Try this:
```
IFS=$'\n';for i in $(ls $m4a); do faad -o - | lame --replaygain-accurate -h -v 2 --ta Anathallo --tl "Floating World" --pad-id3v2 --id3v2-only -"${i%m4a}.mp3"; done
```
What's happening is that the default "field separator" used by the "for ..." construct considers spaces, tabs, and newlines to mark the end of an item.  The "IFS=..." added to the beginning of the command tells it to *only* consider the newline as a valid field separator.

Note: The quotation marks around any place you use the "i" variable is still required - almost all command line programs see a space as a parameter separator, unless enclosed in quotation marks.

Lloyd B.

---

### Post by heindsight on 2009-02-28
> **lloyd_b said:**
> Try this:
```
IFS=$'\n';for i in $(ls $m4a); do faad -o - | lame --replaygain-accurate -h -v 2 --ta Anathallo --tl "Floating World" --pad-id3v2 --id3v2-only -"${i%m4a}.mp3"; done
```
What's happening is that the default "field separator" used by the "for ..." construct considers spaces, tabs, and newlines to mark the end of an item.  The "IFS=..." added to the beginning of the command tells it to *only* consider the newline as a valid field separator.

Note: The quotation marks around any place you use the "i" variable is still required - almost all command line programs see a space as a parameter separator, unless enclosed in quotation marks.

Lloyd B.

You can also do:
```
ls *.m4a | while read i; do
  faad -o - "$i" | lame --replaygain-accurate -h -v 2 --ta Anathallo --tl "Floating World" --pad-id3v2 --id3v2-only - "${i%m4a}mp3"
done

```
Note I made a few changes, like ls *.m4a rather than ls $m4a, also you need to actually supply faad with the file name to convert. Finally the substitution you were using to transform the .m4a filename to a .mp3 name would have resulted in an extra . you were stripping off m4a and adding .mp3

---

