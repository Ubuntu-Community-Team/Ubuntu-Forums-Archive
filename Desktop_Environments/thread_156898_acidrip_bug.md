---
title: "acidrip bug"
date: 2006-04-08
forum: Desktop Environments
---

### Post by rcmn on 2006-04-08
If you have an issue with acidrip when u try to encode with xvid.If it say "Mencoder interrupted by user".Then look in "queue" TAB u will see a line like this:
> mencoder dvd://13 -dvd-device /dev/dvd  -alang English   -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts :bitrate=1004 -vf pp=de,crop=0:0:0:0,scale=480:-2    -o "/my/path/movie.avi"


you will have to run it from a term and change this option from > -xvidencopts :bitrate=1004 to > -xvidencopts bitrate=1004

---

### Post by veratyr on 2006-04-12
Thanks for the workaround. Any idea if it will get fixed soon?

---

### Post by rcmn on 2006-04-12
hard to say it might be a question for the maintainer Christian Marillat.Then again maybe it's already fixed.And it has not been packaged in ubuntu.To find out [http://untrepid.com/acidrip/](http://untrepid.com/acidrip/).

---

### Post by TomG on 2006-06-11
Yep thx a lot for this !

---

### Post by wvelez on 2006-06-12
Hi guys,

Go there:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1468944&group_id=63864&atid=505437](http://sourceforge.net/tracker/index.php?func=detail&aid=1468944&group_id=63864&atid=505437)

There´s a workaround at the bottom of the page.

Best regards,
-will

---

### Post by TomG on 2006-06-12
[I]"Workaround": Under Video - Options enter
"min_iquant=1:min_pquant=1" or any other xvid encode option.[/I]
Thanks. Seems good ! Will try ASAP :)

---

### Post by DirtDart on 2006-07-01
Thanks to both rcmn and TomG for the info...was beating my head against the wall trying to figure this one out.

---

### Post by TomG on 2006-07-02
If it allows to work, curiously neither the progress bar nor the figures (rates...) work during the encoding :confused: 
I can only see that it works by checking the output file size growing... I dont know if it is linked. Strange anyway.

---

### Post by tsumi on 2006-07-06
totally worked for me. i aso had to do a

```
sudo killall esd
```

thanks! these forums rule.

EDIT: i do not get status bars either.

---

### Post by !nkubus on 2006-07-10
Awesome I was wondering why it did that

---

### Post by hotani on 2006-07-16
Wow - this was really hard to find! I've been looking for a solution to this problem all afternoon. Finally put in "acidrip bitrate bug" and this thread popped up.

Thanks for the workarounds - hopefully it will be fixed soon.

---

