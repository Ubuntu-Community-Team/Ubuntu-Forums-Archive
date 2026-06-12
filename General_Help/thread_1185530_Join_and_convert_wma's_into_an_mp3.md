---
title: "Join and convert wma's into an mp3?"
date: 2009-06-12
forum: General Help
---

### Post by mag1 on 2009-06-12
Hi  i would like to join a bunch of wma's and convert to mp3 or convert them to a lossless format and join them then convert to mp3, whatever is best or easiest, preferably using an app, thanks.

---

### Post by LowSky on 2009-06-12
audacity should be able to handle this, its in the repos

sudo apt-get install audacity

---

### Post by mag1 on 2009-06-12
Thanks, it says it recognises the file type but was unable to import it and needs to know where ffmpeg libraries are, i think i may have installed them at some point but don't know where they are?

Edit: no its ok audacity found them automatically after i went to import/export preferences, nice.

---

### Post by colau on 2009-06-12
> **mag1 said:**
> Thanks, it says it recognises the file type but was unable to import it and needs to know where ffmpeg libraries are, i think i may have installed them at some point but don't know where they are?

Edit: no its ok audacity found them automatically after i went to import/export preferences, nice.
```

which ffmpeg

```

---

### Post by mag1 on 2009-06-12
Hmm this looks pretty manual, is there a way to append the wma on one track instead of copy pasting?, otherwise i could use a different program, i got lots of small sound clips that need joining, there must be a more automated ways of doing this?

---

### Post by mag1 on 2009-06-12
Anyone?

---

### Post by Soul-Sing on 2009-06-12
I think converting wma to mp3 gives/results in an enorm quality loss though...
You have to got your multimedia codecs allright,lame, w32,etc.
And maybe soundkonverter can do the job.

---

### Post by Chronon on 2009-06-12
Another possibility is Foobar2k (via WINE).  I'm not certain it will do what you want but I know it can join other file types and has good support for tagging and ReplayGain for WMA.

I agree that you don't want to transcode from lossy to lossy if you can possibly avoid it.

---

### Post by andrew.46 on 2009-06-13
Hi mag1,

> **mag1 said:**
> Hi  i would like to join a bunch of wma's and convert to mp3 or convert them to a lossless format and join them then convert to mp3, whatever is best or easiest, preferably using an app, thanks.

The simplest way I could see to do this would be to use Transcode, utilising its MPlayer import module, and then export as mp3. SoX does an excellent job joining mp3s and this would be the final step.

That is how I would do it myself, unfortunately I am not aware of a single application that could do all of this, does Transcode join files? Mind you a well written script utilising the above would be an excellent idea.

Andrew

---

### Post by 3rdalbum on 2009-06-13
Maybe this is a long shot, but it might be possible to simply "cat" some audio files together.

```
cat file1.wma file2.wma > endfile.wma
```

Hopefully, your audio transcoding software will ignore the headers of the individual files.

---

