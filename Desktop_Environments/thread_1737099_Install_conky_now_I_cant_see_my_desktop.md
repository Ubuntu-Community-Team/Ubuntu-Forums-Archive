---
title: "Install conky now I cant see my desktop"
date: 2011-04-23
forum: Desktop Environments
---

### Post by wildmanne39 on 2011-04-23
Hi, can anyone help me please, I installed conky and now i can not see my desktop. I can not even open a terminal window everything opens underneath conky and i can not open start up applications to uncheck it so it will not start the next time. I can not drop to shell and remove the file because I have some issue with display setting that will not let me see my log in screen if I log out the only thing i can do is boot in and then log on as guest but i can not fix my problem because i am not root,it will not let a guest use sudo. I have a ubuntu book that is about 2 years old and it tells me to boot a live cd but it hangs and doesnt boot all the way. If I hit ctrl and alt f2 it gives me a screen but when i type sudo telinit 1 it hangs again and never gives me a text mode menu like the book says it will. Please any ideas? I just reinstalled 2 days ago and got my system back to the way I want it this afternoon minus getting conky to work. If you have any ideas please give exact instructions, because I am still new at this. Thanks to everyone in advance, I really appreciate any help I can get.

---

### Post by Joe of loath on 2011-04-23
Log in as guest, run su (username), then you will be able to use sudo.

---

### Post by wildmanne39 on 2011-04-23
Hi, thank you for your reply, I tried what you said several times but it says Operation not permitted. I am using 11.04 do you think the command has changed or is it a bug in 11.04? Please let me know what you find out or what you think. Thanks again.

---

### Post by Joe of loath on 2011-04-23
Hmm, maybe guest doesn't allow su, then.

Log in as yourself and press ctrl-alt-f1, then log in and delete your .conkyrc file.

---

### Post by wildmanne39 on 2011-04-23
I tried several times but still does not work because there is a problem with the way ubuntu is reading my display settings all i get is a blank screen when I hit ctrl alt f1 thru f6. Thank you, any more suggestions is greatly appreciated, I know I could just reinstall but that really is not the way to fix a problem, if I can keep from it. Thanks again.

---

### Post by Joe of loath on 2011-04-23
You might as well just boot into the recovery mode, and choose the option to drop to a root prompt. That way you can delete the .conkyrc file without having to bother with going through X.

---

### Post by wildmanne39 on 2011-04-23
Hi, thank you for all your help. I actually had already done that and it did not work, but after I slept on it I remember that I also changed the file that conky gives as an example and once I had set it up to start at boot after I deleted the ./conkyrc file it defaulted to there example file so I deleted it and fixed the problem, do you think having 2 config files for conky is what broke it in the first place? Thanks again I really appreciate your help.

---

### Post by Copper Bezel on 2011-04-23
Conky shouldn't have been in front of your other windows, so that seems separate from the configuration issue. Having two files wouldn't matter, because Conky can only run with one of them (or both separately); it's no different from loading any other two files on your computer with the same application. I also think it'd be an odd coincidence that the changes you made to the sample .conkyrc actually caused the problem, as you'd really have to be *trying* to get that effect. I'd purge ("completely remove") Conky and reinstall before trying it again (and obviously, remove it from your startup applications.)

Incidentally, Conky does interact weirdly with Compiz at startup, so you'd need to add a delay to the command in startup applications, like 

```
sleep 30; conky
```

and that, if anything, is the one configuration choice that could have come close to causing your problem (but the effect isn't ordinarily the one you describe, nor remotely so troublesome.)

---

### Post by wildmanne39 on 2011-04-23
Hi,thank you for your help, I am installing ubuntu in virtualbox right know so I can get conky all figured out with out doing any major damage. I didnt think that it was because of the two really files for sure because I recently set gentoo up and found with it you could have more then one config file for the same program but I just was not sure ubuntu worked the same way. Thank you very much and I will keep trying.

---

