---
title: "Compose key refuses to make å"
date: 2008-05-05
forum: Desktop Environments
---

### Post by FM1 on 2008-05-05
I'm using a US keyboard layout, but often need to type words in Swedish. Right Alt is set as Compose, and it Just Worked™ in Gutsy with the same hardware, but after a new install of Hardy, Compose won't give me å. I can do ä and ö, but not å; it appears to ignore Compose and gives me "oa" or nothing at all, depending whether I'm using US or US International/International with dead keys. I can paste å from the character palette, and it's right where it belongs if I switch to a Swedish layout, but I touch type, so I'd love to have good old familiar Alt+o+a as it was in Gutsy. I've tried changing which key is Compose, but no joy.

---

### Post by akudewan on 2008-05-05
Just a suggestion, since no one has replied to you yet. I've found that renaming the hidden directories seems to get rid of a number of problems that come with a distro upgrade.

In your case, maybe you can try renaming ~/.scim . You'll lose your settings though. But you can rename it back if it doesn't work..

---

### Post by FM1 on 2008-05-06
Thanks. I did a fresh install, not an upgrade, but renaming the directory didn't make any difference. Most of the characters seem to work--if you need þ, ø, ß, &#331; or almost anything else, I've got you covered--but no ring, caret or breve. Å is the only one I really use of those that don't work, so I guess I'll just have to get it from the character palette.

---

### Post by unutbu on 2008-05-06
I probably don't know enough to help you, but just in case, please post the output of

```
xprop -root | grep XKB
```

---

### Post by FM1 on 2008-05-06
I'll take anything...assistance, a push in the right direction, sympathy... :)

lisa@Geek-Girl:~$ xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc104", "us,se,us,us", ",,alt-intl,intl", "grp:alts_toggle,compose:ralt"


I switched from Generic 105 to Generic 104 because of something I read somewhere (read so much that I forget what), but it's still not working.

---

### Post by helicase on 2008-05-06
Try compose+a+a and compose+A+A for å and Å.

---

### Post by FM1 on 2008-05-06
*Yes!* Thank you so much! ååå ÅÅÅ That's even faster--great! :D

If the combination for that changed, perhaps that's where my caret and breve have gone as well; not that I use either often. Am I looking in the wrong place for a list? According to /usr/share/X11/locale/en_US.UTF-8/Compose, å is still Compose+o+a, but obviously, it's not.

---

### Post by helicase on 2008-05-06
> **FM1 said:**
> Am I looking in the wrong place for a list? 
I wouldn't know. I usually just twiddle with a few keys until I find what I want. Just try combinations that you think would make sense. For instance:
â: compose+^+a or compose+>+a
&#259;: compose+(+a

---

### Post by FM1 on 2008-05-06
I got them. Most are the same as they were before, and I found the only others I'm likely to use. Compose+(+a for &#259; and Compose+<+s/c/z/n for š/&#269;/ž/&#328;. I'm all set--thanks again! :)

---

### Post by fballem on 2008-05-18
So if I'm using the US International with dead keys, how do I get a c-cedille (looks like a c with a comma underneath). I can manage ñ, à, é, ê - which is what I need for French and Portuguese, but haven't found the magic to make a c-cedille. I am coming from a Windows world, and am used to a US International keyboard (which is close to the linux US International with dead keys).

Many thanks,

---

### Post by fballem on 2008-05-18
I asked a question on Launchpad and one of the other users was kind enough to raise it as a feature request. The information can be found here:

[https://bugs.launchpad.net/ubuntu/+bug/231785](https://bugs.launchpad.net/ubuntu/+bug/231785)

Hope this helps - and if it's important to you, please feel free to add your voice.

Thanks

---

### Post by fballem on 2008-05-19
Apparently we needed to go somewhere else, so here we are:

[https://blueprints.launchpad.net/ubuntu/+spec/us-international-keyboard-microsoft](https://blueprints.launchpad.net/ubuntu/+spec/us-international-keyboard-microsoft)

---

