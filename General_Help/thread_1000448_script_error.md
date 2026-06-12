---
title: "script error?????"
date: 2008-12-02
forum: General Help
---

### Post by oilspot on 2008-12-02
I'm having to run my computer off the  live disk right now to ask for help. I've been running ubuntu for about 2 months now. Everythings updated, etc.
 All of a sudden tonight whenever I open firefox it opens, it pretty much freezes up. It gives me a message that there's an error trying to run a script. It offers the option to try to let it run, or cancel it. Neither does anything. There's no way to make the message go away, and firefox will not respond. I've tried restarting a few times and the same thing happens....
 very frusturating!!!
 what do I do?

---

### Post by oilspot on 2008-12-03
while waiting for answers I looked around... found on the firefox page that it's a firefox problem.   
 So I tried to run firefox in safemode. typed 
/path/to/firefox/firefox -safe-mode 
into the terminal. Now firefox will not open at all. (oh yeah, I'm on a winning streek!!!)


 I was hoping I could just reinstall firefox. tried in the add remove. 

is there anyway to just reinstall firefox?

---

### Post by oilspot on 2008-12-03
i was thinking "what the hell did I do that made firefox not open at all"
 It was when I had firefox opened, and then in the file tab i hit the quit button.
 Just figured I'd throw that in there before I go off to bed. Hope there will be some good answers in the morning. 
 thanks for your help!:D

---

### Post by oilspot on 2008-12-03
anyone?

---

### Post by Diabolis on 2008-12-03
Remove completely and then reinstall:
```
sudo apt-get remove --purge firefox
sudo apt-get install firefox
```

Reinstall firefox:
```
sudo apt-get install --reinstall firefox
```

If the version in the repos doesn't work for you, download it directly from firefox site.

If you had more info about what the error said or which is the script that fails, maybe we could track down the source of the problem.

---

### Post by oilspot on 2008-12-03
somehow, by flailing around I managed to get firefox working again. I uninstalled a part of firefox and reinstalled it, and now I'm not getting the script error anymore.

 Here's my problem now. when I try to open firefox via the large button, a blank terminal comes up. I'm also getting a message that says
"there was a problem creating the child process for this terminal"

 I... in my flailing around figured out that I'm able to open firefox in blank terminal window by going to help, then report a problem, that sucessfully opens firefox... go figure


 on a side note... is there anyway to change my forum status to "proof that anybody can make ubuntu work":D:D:D
 thank god for these forums!!!

---

