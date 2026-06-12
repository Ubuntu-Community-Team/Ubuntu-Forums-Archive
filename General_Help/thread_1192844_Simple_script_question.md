---
title: "Simple script question"
date: 2009-06-20
forum: General Help
---

### Post by shipitkthx on 2009-06-20
I have a bunch of files that got improperly named, i know how it happened but its not worth explaining, anyhow the files are named like this:

<filename>.flac928391832dassdedh32819083
<filename>.flac3823910eaklsduja98s43hqwd

and so on and so on.

I just want to write up a quick SH script to strip off everything after the .flac

I have a couple rename scripts but bash syntax confuses the hell out of me.

---

### Post by geirha on 2009-06-20
There's a rename command ...
```
rename -n 's/\.flac.*$/.flac/' *
```

The -n makes it only print what it would've done, but not actually do it. Replace it with -v to have it actually do the renaming, if the output with -n looks right.

---

### Post by shipitkthx on 2009-06-20
```
jim@jim-desktop:~/Desktop/testfolder$ ls -w 1
test.flac328190839108231903
test.flac9831902831902udaskjdklad
test.flacasjdkljda392819312903d
jim@jim-desktop:~/Desktop/testfolder$ rename -n 's/\.flac.*S/.flac/' *
jim@jim-desktop:~/Desktop/testfolder$ rename -v 's/\.flac.*S/.flac/' *
jim@jim-desktop:~/Desktop/testfolder$ 

```

no luck :-(

---

### Post by geirha on 2009-06-20
> **shipitkthx said:**
> ```

jim@jim-desktop:~/Desktop/testfolder$ rename -n 's/\.flac.*[COLOR="Red"]S[/COLOR]/.flac/' *

```


[COLOR="Red"]$[/COLOR] (dollar sign), not [COLOR="Red"]S[/COLOR]. $ matches the end of a line.

---

### Post by shipitkthx on 2009-06-20
ooops, works now, thank you very much

---

### Post by ghostdog74 on 2009-06-21
not every distro has rename. in case its so, just normal bash/awk 
```

for file in *.flac*
do
  newfile=${file%%flac*}.flac
  mv "$file" "$newfile"
done 

```

---

