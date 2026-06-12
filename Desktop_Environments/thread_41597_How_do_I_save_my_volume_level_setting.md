---
title: "How do I save my volume level setting?"
date: 2005-06-14
forum: Desktop Environments
---

### Post by twoseids on 2005-06-14
Every time I log into Ubuntu, my master volume bar is at around 50% or less.  I crank it, and check "Save Current Setup" when logging out, but when I come back in, it's back down to 50% again.

How can I set it so that my master volume will always be at 100%?

---

### Post by Xian on 2005-06-14
Other applications can sometimes effect what the master volume level gets set at, including many audio packages like XMMS, Realplayer, and so forth. However, if these are not the cause then you should be able to preserve your sound levels with this command:

```
$ sudo alsactl store
```

---

### Post by twoseids on 2005-06-14
[QUOTE=Xian]Other applications can sometimes effect what the master volume level gets set at, including many audio packages like XMMS, Realplayer, and so forth. However, if these are not the cause then you should be able to preserve your sound levels with this command:

```
$ sudo alsactl store
```[/QUOTE]
 Worked great!  Thanks a lot.

---

### Post by clawfrank on 2005-08-19
[QUOTE=twoseids]Worked great!  Thanks a lot.[/QUOTE]
 I have this problem too, but it always starts up at 100%, and if I try that command I get the following output:

```
alsactl: save_state:1194: No soundcards found...
```

I'm using an a7n8x deluxe with onboard soundstorm audio, so of course there is no soundcard found.  Is there a similar command I could use?

---

### Post by Ceebo on 2005-08-31
i have the same problem too. In Xmms, everytime i boot xmms volume reset to 100% 
help me !

---

### Post by schdefan on 2005-08-31
you should check if your alsa packages are broken. Try to reinstall them.
Did you get the same message when you open alsamixer?
You should see your soundcard when you run
```
lspci  | grep sound
```

Find out the module name of your soundcard (a7n8x)!
schdefan

---

