---
title: "firefox always loads arizona.edu? at startup, or new window."
date: 2006-07-12
forum: Desktop Environments
---

### Post by nismoskys on 2006-07-12
hey.. havent posted here in a while.. hows everyone? lol
well im having a problem
everytime i open ff, the first page it automatically loads in [www.arizona.edu](www.arizona.edu). no, it's not my home page. if i click the "home" button on the toolbar, i get gracefully transferred to google.com(my actual set homepage)

i dont know how this could've happened.. i dont even know anyone who goes to the university of arizona. regardless, i really dont care, i just want to fix it, if anyone can help me.

my only thought is that it might have something to do with my tabmixplus firefox extension, which can restore the last browser page at startup, but it normally restores only whatever i saved at close, but then it also adds that arizona page for some unknown reason.

well i tried uninstalling tabmixplus but i've still got the same problem.

thanks alot.

---

### Post by metalheart on 2006-07-12
If you run firefox from the command line, does it have the same behaviour?

```
firefox
```

---

### Post by nismoskys on 2006-07-12
no, no it doesnt. it goes straight to my homepage.

to start firefox, i use the code 
firefox %u
(i start it from the starter bar of gdesklets)

running firefox %u from the terminal, i get that same arizona page, but im fine without %u.

---

### Post by bulldog on 2006-07-12
I had something similar,and I got it by using the gdeskletbar.
Removed de gdeskletbar and it was gone.
Later I downloaded an image for the top-bar and another startpage came up.
Maybe did you installed something?
Don't ask how it works,cause I don't know,but not using those items did the tric for me.

---

### Post by T700 on 2006-07-12
Very strange.  I've seen the same problem on a Windows forum.  No solution was ever found, other than uninstall and reinstall of Firefox.

Paul

---

### Post by nismoskys on 2006-07-12
its weird though why does just "%u" take me to arizona.edu . what exactly is %u for? used to work fine before with %u at the end.

---

### Post by nismoskys on 2006-07-12
so what do you guys think i should do? just use ff without the %u?

---

### Post by Irony on 2006-07-12
This perhaps obvious but have you gone to *Edit > Preferences > Privacy* and cleared out everything?

---

### Post by jordilin on 2006-07-12
Delete your firefox profile which I suppose is the default by going to your home and do rm -rf ~/.mozilla/firefox/xxxx.default and create another profile by executing $ firefox -ProfileManager & and create another one. I recommend doing a backup of the .mozilla/firefox folder ($ tar -czvf firefoxbackup.tgz .mozilla/firefox) to go backwards if things don't go well. I think that deleting your profile and creating a new one should work around your problem.

---

### Post by metalheart on 2006-07-12
I guess this command string passes on search string to the default search engine (Google in my case) wich takes you to the first matching website. You could try all the letters from a to z :) How to change this? Dont know.

---

### Post by PapaWiskas on 2006-07-12
Just delete the %u portion and you will be fine.  This is a known glitch/bug/annoyance.

---

### Post by nismoskys on 2006-07-12
cool, thanks.

---

### Post by nismoskys on 2006-07-12
wow thats crazy metalheart lol.. nice observation. yeh i guess ill just stick without the %u

---

### Post by matthew on 2006-07-12
Sorry I didn't notice your thread earlier...this has been a firefox problem for some time, not just with ubuntu.

[http://www.ubuntuforums.org/showthread.php?t=94869](http://www.ubuntuforums.org/showthread.php?t=94869)
[http://www.ubuntuforums.org/showthread.php?t=96414](http://www.ubuntuforums.org/showthread.php?t=96414)
[http://www.ubuntuforums.org/showthread.php?t=104529](http://www.ubuntuforums.org/showthread.php?t=104529)
[http://www.ubuntuforums.org/showthread.php?t=111964](http://www.ubuntuforums.org/showthread.php?t=111964)
[http://www.ubuntuforums.org/showthread.php?t=188399](http://www.ubuntuforums.org/showthread.php?t=188399)

Let me again note, while this is frustrating until you get it solved, I still think it cool that it goes to the website of my Alma Mater... :)

---

