---
title: "opera browser wand problems"
date: 2008-12-11
forum: General Help
---

### Post by workshop1702 on 2008-12-11
hi my opera browser has another problem when i go to ebay and try to sign in using the wand i have this problem. i have two ebay accounts and there are two wand sign ins for the two accounts . when i click on the relavant one i want to sign into the wand seems to freeze i just get a box with nothing in it and the browser freezes. i have to force quite to get out of it , when i then reestart opera a window opens warning me there is another opera lock file active , presumably this should not be active.any help would be great. Thanks Andrew

---

### Post by .nedberg on 2008-12-12
Try to go to Tools->Preferences -> Wand->Passwords and find your eBay password and delete them.

If you can't start opera then:
```

ps axw | grep opera

```
it will show something like:
```
 3052 pts/2    R+     0:00 grep opera
**30771** ?        Sl     2:40 /usr/lib/opera/9.62/opera -style qtcurve
30809 ?        SN     0:07 /usr/lib/opera/9.62/operapluginwrapper 105 108 /usr/lib/flashplugin-nonfree/libflashplayer.so
30810 ?        S      0:00 /usr/lib/opera/9.62/operaplugincleaner 30771

```
Note the number I **highlighted**, then do
```

kill -9 **30771**

```
but replace the number. Wait and see if operapluginwrapper and operaplugincleaner is stopped (could take up to a minute).

Try to start Opera now.

---

### Post by workshop1702 on 2008-12-16
this is what i get when i try your commands 

 6756 pts/0    R+     0:00 grep opera
andrew@tatung-tablet:~$ 

what should i do please

---

### Post by workshop1702 on 2008-12-16
hi again this problem seems to be worse than i first thought , when the wand fails to work correctly the processor goes to 100% and wont come down , the only way is to do a restart , its a real pain anyone know how i can fix this please.

---

### Post by workshop1702 on 2008-12-16
hi again this problem seems to be worse than i first thought , when the wand fails to work correctly the processor goes to 100% and wont come down , the only way is to do a restart , its a real pain anyone know how i can fix this please.

---

### Post by workshop1702 on 2008-12-16
more info on this problem it seems to be the opera plugginwrapper that is using about 75-80% of the cpu resorcess if i shut this down the cpu drops to normal usage levals , if i then use the browser again it soon has the 100% processor problem again . realy need to sort this problem out anyone any ideas how i can fix it please .

---

### Post by .nedberg on 2008-12-17
I have also seen operapluginwrapper go up to 100% CPU usage when Opera has crashed. Kill it with kill -9.

Did you remove both your eBay passwords from Opera? There might be something wrong with your wand file.

Also try to run opera with
```

opera -personaldir ~/operatest

```
Now log into eBay and save your passwords. Close Opera and run that command again and see if it works. The command starts Opera with an alternative settings folder (~/operatest). If it works now, then there is something wrong with your ~/.opera folder.

---

### Post by workshop1702 on 2008-12-18
thanks for the suggestion i have removed all the ebay sign i info from wand then reentered them , also upgraded to opera 9.63 and then shut down opera and run it from the command you suggested , i had to reenter the ebay paswords again , it still has the problem i can sign into one ebay account ok and then when i sign out and then try to use the wand to resign into the other account the cpu usage goes to 100% and i have to do a restart to get out of it , just shutting down opera doesnt stop the 100% cpu usage. any more ideas would be good , its so frustrating as i can no longer use my faviorite browser.

---

### Post by Arup on 2008-12-18
Can you tell me if you are using Flash and how it was installed? Also in your case, it looks like you need to do a apt-get --purge remove opera to remove all previous config files and install it again. I have very minimal CPU usage with my Opera 9.63 and am using latest x64 Flash 10 as well which Opera accesses via /usr/lib/mozilla/plugin.

---

### Post by .nedberg on 2008-12-19
There is no need to --purge opera, running it with -personaldir makes new versions of every configfile.

I would say this is a bug in Opera and that you should report it!

---

### Post by workshop1702 on 2008-12-21
the opera PLUG IN WRAPER IS STILL USING 74% OR MORE OF CPU TOTAL CPU IS AROUND 96% TO 100% THE SIGN IN PROVBLEM USING THE WAND SEEMS TO BE ONLY WITH EBAY SIGN INS ,THE CPU USAGE IS FAR TO HIGH WHEN JUST USING THE  OPERABROWSER , SOME PROBLEMS WITH FLASH NOT WORKING AS IT SHOULD ALSO, WORKS FINE WITH FIREFOX BUT NOT OPERA , IS THE REMOVAL AND RE INSTALL OF OPERA WORTH A TRY, IF SO HOW DO I BACK UP ALL MY SETTINGS AND BOOKMARKS , IS REINSTALLING MY PREFERRANCES LIGHTLY TO BRING THE PROBLEM TO A NEW INSTALLED OPERA .JUST HAVE A FEELING THAT THE FLASH PLAYER HAS SOMETHING TO DO WITH ALL THESE PROBLEMS . ANYONE ANY MORE SUGGESTIONS ON HOW TO SORT THIS PLEASE.

---

### Post by Skripka on 2008-12-21
> **workshop1702 said:**
> the opera PLUG IN WRAPER IS STILL USING 74% OR MORE OF CPU TOTAL CPU IS AROUND 96% TO 100% THE SIGN IN PROVBLEM USING THE WAND SEEMS TO BE ONLY WITH EBAY SIGN INS ,THE CPU USAGE IS FAR TO HIGH WHEN JUST USING THE  OPERABROWSER , SOME PROBLEMS WITH FLASH NOT WORKING AS IT SHOULD ALSO, WORKS FINE WITH FIREFOX BUT NOT OPERA , IS THE REMOVAL AND RE INSTALL OF OPERA WORTH A TRY, IF SO HOW DO I BACK UP ALL MY SETTINGS AND BOOKMARKS , IS REINSTALLING MY PREFERRANCES LIGHTLY TO BRING THE PROBLEM TO A NEW INSTALLED OPERA .JUST HAVE A FEELING THAT THE FLASH PLAYER HAS SOMETHING TO DO WITH ALL THESE PROBLEMS . ANYONE ANY MORE SUGGESTIONS ON HOW TO SORT THIS PLEASE.

There's no need to scream (caps for a whole paragraph), it hurts the eyes-and only hurts you.

All one's personal settings are stored in a (hidden) folder in your home directory called ".opera", renaming it slightly to "Opera" (without the period at the start) will have the same effect from the browsers perspective-in forcing the browser to create a blank profile.

---

### Post by .nedberg on 2008-12-22
This is indeed a flash/opera problem. Flash on linux does not play well with Opera. From what I have heard this is getting better with Opera 10 and flash 10, but I have not tested it.

About the eBay problem, did you report a bug to Opera?

---

