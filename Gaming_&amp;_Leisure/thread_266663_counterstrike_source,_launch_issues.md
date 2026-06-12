---
title: "counterstrike source, launch issues"
date: 2006-09-27
forum: Gaming &amp; Leisure
---

### Post by jeffrock on 2006-09-27
Hi all. I have had ubuntu for about 2 days, after xp x64's trial ran out,  so bear with me please :-D
I successfully installed wine thanks to kilz, and his awesome howto. Took a little tinkering but finally got it. Installed steam, and downloaded css with no issues. However when i try to launch css off of the steam window, it comes up, and just as fast as it comes up, crashses. I have read that thsi could be a sound issue. I have enabled the OSS sound thingie, like i have read in previous posts, however it did not correct the issue. 

winecfg opens correctley, however when i click the audio tab i get the following output in term.

ox:~$ winecfg
err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

what do I have to do next? should this even effect source? 
Let me know what to do next. Thanks

**edit, found this post [http://ubuntuforums.org/showthread.php?t=196217](http://ubuntuforums.org/showthread.php?t=196217) should help with lib issues. will let yall know if css worked!**


UPDATE! even after following the steps listed above in the link to the other post, it produces the same error message.

---

### Post by CAUSTICROUTER on 2006-09-27
What version of wine are you using?

---

### Post by smartalecks on 2006-09-27
Open Synaptic, then search for and install these libraries. They will be named differently in Synaptic, which is why we are searching for those keywords :). 

libasound
libartsc
libesd
libjack

See if that helps.

---

### Post by jeffrock on 2006-09-28
i am using wine 0.9.21, i tried installing those packages, but under synaptic, when i searched for them, i had them already installed, so i reinstalled, still same problem. do i need ot donwload the dev's too?

---

### Post by CAUSTICROUTER on 2006-09-28
I had the same problem, it's because of a bug in the new(0.9.21) wine. Just downgrade to 0.9.20. and it should work.

---

### Post by delta99 on 2006-09-28
> **CAUSTICROUTER said:**
> I had the same problem, it's because of a bug in the new(0.9.21) wine. Just downgrade to 0.9.20. and it should work.

Not for me it didn't. I tried 0.9.20 + 0.9.19 but still cannot launch css.

I just been fiddling with cedega, steam once again absolutly no problems, but when you go to launch counter-strike source... I get a black screen flashes and then complete freeze. (cannot do anything but to restart using CTRL+ALT+BACKSPACE).

wish someone knew why, I have spent almost 2 weeks trying to play css on ubuntu, but I have failed.

still i keep trying, ubuntu itself is damn good os. :rolleyes:

---

### Post by echo $USER on 2006-09-28
> **delta99 said:**
> Not for me it didn't. I tried 0.9.20 + 0.9.19 but still cannot launch css.

I just been fiddling with cedega, steam once again absolutly no problems, but when you go to launch counter-strike source... I get a black screen flashes and then complete freeze. (cannot do anything but to restart using CTRL+ALT+BACKSPACE).

wish someone knew why, I have spent almost 2 weeks trying to play css on ubuntu, but I have failed.

still i keep trying, ubuntu itself is damn good os. :rolleyes:

Wine is very finicky.  The best version of wine to run steam and source games is 9.12.  No problems whatsoever.

---

### Post by byoon on 2006-09-28
> **delta99 said:**
> Not for me it didn't. I tried 0.9.20 + 0.9.19 but still cannot launch css.

I just been fiddling with cedega, steam once again absolutly no problems, but when you go to launch counter-strike source... I get a black screen flashes and then complete freeze. (cannot do anything but to restart using CTRL+ALT+BACKSPACE).

wish someone knew why, I have spent almost 2 weeks trying to play css on ubuntu, but I have failed.

still i keep trying, ubuntu itself is damn good os. :rolleyes:

Wine 0.9.20 & 0.9.21 don't work for me with CSS and HL2.

Wine 0.9.19 works great with CSS and HL2, except no task tray icon.

---

### Post by CAUSTICROUTER on 2006-09-28
Yeah, I am using wine 0.9.20 and CSS works great.  It didn't work with 0.9.21. But any type of downgrade should work.

---

