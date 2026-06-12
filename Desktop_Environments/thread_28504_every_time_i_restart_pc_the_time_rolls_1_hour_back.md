---
title: "every time i restart pc the time rolls 1 hour back !?"
date: 2005-04-20
forum: Desktop Environments
---

### Post by lorap on 2005-04-20
it's a very strange behavior.
does anybody know the solution for this sad problem?
reading the faq i've paied attention there are some bugs with the clock servises,but hope there would be solutions soon.
thanks.
pavel

---

### Post by sijp on 2005-04-20
Hey pavel,

I had to do this as well, this is because we changed to summer clock in israel, so ubuntu did not know it. Changing the clock manually is not the right way though.

There is a script in whatsup.org.il that fixes it  (worked well for me), you can see it here:
[http://www.whatsup.org.il/forum/22044](http://www.whatsup.org.il/forum/22044)

there is an error on the third line though, 
```
cd /usr/src/share/zoneinfo/datefiles/asia 
```
should be;
```
cd /usr/src/share/zoneinfo/datfiles/asia 
```

(should be datfiles, not dat**_e_**files)

the strange thing is that my debian box knew it.

for the non-hebrew speakers, what the script does is update the timezone with the zic file from the hebrew University, which is where the "official" configuration is.

---

### Post by lorap on 2005-04-20
thank you very much friend!
toda!
i'm gonna fix it by your instructions.
pavel

---

### Post by lorap on 2005-04-20
it did help!
thank you very much friend!
pavel

---

### Post by void_false on 2005-04-20
Toda ahi!  :wink: 
Do we change time only in Israel?

---

### Post by sijp on 2005-04-20
[QUOTE=void_false]Toda ahi!  :wink: 
Do we change time only in Israel?[/QUOTE]
 well, I am not sure... I guess not, however I know for sure Israel is the only one that did so on that specific date this year. It depends on the government, just political stuff, which unfortunatlly I do not understand.

---

