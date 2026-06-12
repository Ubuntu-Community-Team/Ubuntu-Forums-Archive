---
title: "Control-Backspace to delete part of address in FF?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by HBK on 2006-07-25
Hi everyone,
Having tried all three ubuntus so far, I decided to have a serious go at it again and try to replace XP entirely.
While using Firefox I noticed a small yet (for me) quite annoying difference to the Windows version. Think of a longer path in your address bar, consisting of several parts separated by slashes (e.g. [http://www.ubuntuforums.org](http://www.ubuntuforums.org)**/**usercp.php). If you go to the end of the address in windows and do a ctrl-backspace, only the part after the slash is deleted (usercp.php), whilst in ubuntu the whole address bar is cleared.
I hope that was somehow comprehensible :rolleyes::-D... I'd rather have it the windows way, can be extremely handy when browsing Wikipedia for example  ;). And well, as we're using Linux, I'm pretty sure there must be some way of changing this behaviour, isn't there? Forum search didn't give me anything useful, maybe you can help me :)?

Thanks in advance,
HBK

---

### Post by moore.bryan on 2006-07-25
probably not an ubuntu issue... my guess is it lies in firefox.  use the
```
about:config
```
in the url bar to find how it handles urls.

on a side note, you may want to look into swiftfox ([www.getswiftfox.com)](www.getswiftfox.com)), an optimized firefox build for linux; it's amazingly faster.  ;-)

---

### Post by HBK on 2006-07-27
Hm, thx for your answer, I had already tried about:config, didn't really find an option to change it. Does anyone have an idea how it is called?

Cheers,
HBK

---

### Post by moore.bryan on 2006-07-27
i looked around some more and don't think it's a ff issue, but a linux one.  some mozdev posts talk about the same issue, but only arising on linux.  have you tried any of the keybinding extensions (like keyconfig) or emacs?

---

### Post by Missyme on 2007-03-11
I had this same problem and I found the solution here: 
[http://www.ubuntuforums.org/showthread.php?t=314579&highlight=ctrl-backspace+firefox](http://www.ubuntuforums.org/showthread.php?t=314579&highlight=ctrl-backspace+firefox)

in about:config change   "layout.word_select.stop_at_punctuation"    from false to true.

That fixed everything and I am happy again :)

---

