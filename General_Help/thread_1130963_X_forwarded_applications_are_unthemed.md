---
title: "X forwarded applications are unthemed"
date: 2009-04-20
forum: General Help
---

### Post by Kareeser on 2009-04-20
Hello everybody,

I have a custom theme installed on both computer A and computer B. Their respective root accounts are also themed (through [symlinks from their user accounts](http://tombuntu.com/index.php/2007/09/18/theme-applications-running-as-root-in-ubuntu/))

Computer A executes this script:
```
ssh -X computerB
rhythmbox &
```

However, when Rhythmbox comes up on Computer A, it is unthemed. 

I'm thinking that it may be because the installed theme on Computer B doesn't exist on Computer A, but short of installing that theme on Computer A, is there anything I can do so that X forwarded applications use the theme of the connecting computer?

Thanks!

---

### Post by aeiah on 2009-04-20
i suggest just isntalling both themes on both computers. 

your post is a bit misleading because i initially thought when you said "I have a custom theme installed on both computer A and computer B" you meant the same theme, but "I'm thinking that it may be because the installed theme on Computer B doesn't exist on Computer A" contradicts this.

---

### Post by aeiah on 2009-04-20
you could also try this i suppose:

[http://urukrama.wordpress.com/2008/07/13/setting-a-custom-gtk-theme-for-specific-applications/](http://urukrama.wordpress.com/2008/07/13/setting-a-custom-gtk-theme-for-specific-applications/)


i remote in to exaile from my netbook from time to time but i havent messed around with it enough to know what works and what doesnt. right now im like you, i have an unthemed music player

---

### Post by Kareeser on 2009-04-20
Thanks for the tip, aeiah, but that didn't seem to solve the problem. I still have an unthemed app, even with the same theme on both computers. (WRT your first post :))

It definitely has something to do with the presence of custom themes, since if I change Computer A's theme to Human, the x forwarded application works perfectly. Hrm.

What makes the default theme different? Is it the fact that it's pre-installed and has symlinks *somewhere*?

---

### Post by unutbu on 2009-04-20
I don't know if this will help or not, but...

Perhaps while logged directly into Computer B run:
```

env | sort > ~/env-local.out
```

Then ssh to Computer B and run
```

env | sort > ~/env-ssh.out
```

Then compare env-local.out to env-ssh.out. Perhaps there is an environment variable that needs to be set.

---

### Post by aeiah on 2009-04-20
> **Kareeser said:**
> Thanks for the tip, aeiah, but that didn't seem to solve the problem. I still have an unthemed app, even with the same theme on both computers. (WRT your first post :))

It definitely has something to do with the presence of custom themes, since if I change Computer A's theme to Human, the x forwarded application works perfectly. Hrm.

What makes the default theme different? Is it the fact that it's pre-installed and has symlinks *somewhere*?

perhaps, yea... custom themes tend to get installed to ~/.Themes, however i think ones that exist as standard are in /usr/local/ or something? im not sure where exactly but they arent in ~/.Themes

---

### Post by Kareeser on 2009-04-20
/usr/share/themes... after much digging.

If I install the themes into /usr/share/themes then the X forwarded application is themed, so that seems to be fine.

Except the theme Shiki-Noble. For some reason, it won't theme the forwarded application. The rest of the themes included in that pack (Shiki-colors) works fine.

Odd. Must be because it's the newest one...

---

### Post by aeiah on 2009-04-20
it might require some weird-*** rendering engine that the others dont, or simply a rendering engine that isnt available on the other machine. does shiki-noble work if you set it as your theme on both machines? (just to test if its a rendering engine problem).

at least we know where themes have to be for x forwarded applications now, even if there does seem to be a little glitch

---

### Post by Kareeser on 2009-04-20
Mm... apparently, I didn't have Shiki-Noble installed on Computer B. I don't see why the theme needs to be on BOTH computers, but that's the way it is...!

---

