---
title: "Ubuntu thinks audio file to be ASF video"
date: 2006-01-08
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-01-08
I got several .wma files on my machine. Sound files. The machine thinks they are .asf video files, but plays them fine anyway.

BUT: I can't burn them to a audio CD, nor convet them. Using the audio-convert script, it'll convert the first second - and that's it.

How can I work around that, or solve the problem?

G

---

### Post by mcduck on 2006-01-09
Have you tried renaming them to .asf, as that is what they really are anyway.. ;)

---

### Post by GabrielWolff on 2006-01-09
[QUOTE=mcduck]Have you tried renaming them to .asf, as that is what they really are anyway.. ;)[/QUOTE]

Did that. Did no good.

The file is still labeled under ASF (naturally), but when named .asf, xmms won't play it anymore. MPlayer plays it fine, but it did so before anyway.

Converting still doesn't work. Is there a script for converting .asf files? But I would need a plugin that would enable me to burn them anyway, wouldn't I? Isn't there an .asf plugin for k3b or GnomeBaker?

Is .asf a coded .wma file?

G

---

### Post by stalefries on 2006-01-09
As far as I know, this was a problem with Nautilus reading the mime types for the file, and getting confused. This has been fixed, and I think it should be in Gnome 2.14, which will come with the new Dapper Drake 6.04 when it comes out in April.

---

### Post by hanzj on 2006-03-10
My workaround is vsound.
```
vsound mplayer foo.wma
```

---

### Post by hanzj on 2006-03-10
Well, I tried vsound mplayer foo.wma on one of my files, which, just like yours, is "ASF File format." It didn't work, too.

---

