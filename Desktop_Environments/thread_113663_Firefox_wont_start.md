---
title: "Firefox wont start"
date: 2006-01-06
forum: Desktop Environments
---

### Post by dannyngweekiat_85 on 2006-01-06
I try to start firefox to get online and it just close.
I try to run it from terminal and it show this

```

/opt/firefox/run-mozilla.sh: line 131: 26871 Segmentation fault      "$prog" ${1+"$@"}

```

Anyone here know how to fix this problem?

---

### Post by apparition on 2006-01-06
I *think* the permissions of your executable may be incorrect.  Here is why I think that:

Check out line 131 of your run-mozilla.sh file.  I used ViM, so...

```
sudo vim /opt/firefox/run-mozilla.sh
:131  // while in ViM this takes you to line 131

```

Line 131 (and a bit onwards) in /opt/firefox/run-mozilla.sh is:

```
moz_run_program()
{
   prog=$MOZ_PROGRAM
   ##
   ## make sure the program is executable
   ##
   if [ ! -x "$prog" ]
   then
      moz_bail "Cannot execute $prog."
   fi
```

The comment suggests the program is not executable.  So now this will depend on where you installed firefox to.

For me:

```
ls -l /usr/lib/mozilla-firefox/firefox
```

returned:

```
-rwxr-xr-x  1 root root 11170 2005-10-10 11:31 /usr/lib/mozilla-firefox/firefox
```

If your firefox executable doesn't have those permissions, then you can set it with:

```
sudo chmod 755 /usr/lib/mozilla-firefox/firefox
```

---

### Post by dannyngweekiat_85 on 2006-01-07
i did 

```

ls -l /usr/lib/mozilla-firefox/firefox

```

and saw this
```

-rwxr-xr-x  1 root root 11170 2005-10-10 23:31 [COLOR="Lime"]/usr/lib/mozilla-firefox/firefox
[/COLOR]

```

so wat does that mean?.. got permission or not?... well after doing chmod its the same color.. if it had permission should it be blue? and still i cant execute firefox

---

### Post by dcstar on 2006-01-07
[QUOTE=dannyngweekiat_85]i did 

```

ls -l /usr/lib/mozilla-firefox/firefox

```

and saw this
```

-rwxr-xr-x  1 root root 11170 2005-10-10 23:31 [COLOR="Lime"]/usr/lib/mozilla-firefox/firefox
[/COLOR]

```

so wat does that mean?.. got permission or not?... well after doing chmod its the same color.. if it had permission should it be blue? and still i cant execute firefox[/QUOTE]
Those permissions are ok, Firefox is run by typing "firefox", have you done this?

---

### Post by Paulus on 2006-01-07
hey you'll be suprised to know i literally had just the same problem, had u just installed a new theme?  If so do the following:

browse to ~/.mozilla/firefox  and enter the directory of your profile

open a file called prefs.js

goto line wher it says : "general.skins.selectedSkin"  and change the value next to it to "default", save and start firefox.   

this'd work if u had the same problem I did, with one of the "most popular" themes on the firefox website, namely **[[B]Saarang 2006.**]("https://addons.mozilla.org/themes/moreinfo.php?id=1671&application=firefox")[/B]

---

### Post by dannyngweekiat_85 on 2006-01-07
> **Paulus]hey you'll be suprised to know i literally had just the same problem, had u just installed a new theme?  If so do the following:

browse to ~/.mozilla/firefox  and enter the directory of your profile

open a file called prefs.js

goto line wher it says : "general.skins.selectedSkin"  and change the value next to it to "default", save and start firefox.   

this'd work if u had the same problem I did, with one of the "most popular" themes on the firefox website, namely **[[B]Saarang 2006.**]("https://addons.mozilla.org/themes/moreinfo.php?id=1671&application=firefox")[/B][/QUOTE]

Well i open that file and its a empty file. Maybe because i din install the theme  said:**
> 
Those permissions are ok, Firefox is run by typing "firefox", have you done this?


Well i did that by typing firefox in terminal. But the problem is stil there. :confused: quite new to linux system...haha... just change to it for 3 weeks+
:) now using galeon browser... but like firefox better..

---

### Post by art on 2006-01-07
What is the output of 

ls -ltr ~/.mozilla/firefox/pluginreg.dat 

For me once it happened that this file got wrong permissions and firefox wouldn't start.

---

### Post by dannyngweekiat_85 on 2006-01-07
[QUOTE=art]What is the output of 

ls -ltr ~/.mozilla/firefox/pluginreg.dat 

For me once it happened that this file got wrong permissions and firefox wouldn't start.[/QUOTE]

Well look at the file... it is in ~/.mozilla/ for me. No permission is set for the file so i set it..  but then still have the same error when trying to run mozilla ... wierd....??:confused: before this i have been running it smoothly. The error just happen recently and i have no idea wat may have gone wrong... :confused:

---

### Post by art on 2006-01-08
The one in .mozilla is for the older version of firefox (1.07 which ships with ubuntu), and epiphany. You have Firefox 1.5 installed. There should be a folder called .mozilla/firefox and you have to have a file pluginreg.dat in there too. Do you have it? Also try running epiphany. Does it run?

---

### Post by dannyngweekiat_85 on 2006-01-08
well did not find the file in the folder. I updated to 1.5 using automatix.  well.... no epiphany in my pc ... will try to install it now and c how is it.

---

### Post by art on 2006-01-08
also try running 

sudo firefox

I now don't remember how exactly i fixed the problem... But I remember the cause of the trouble:)

---

### Post by dannyngweekiat_85 on 2006-01-08
haha...
i try sudo ... and su also...
but still the same errot come out...wierd.... will try to find ther source of problem...

edited:
Epiphany browser can be succesfully run!... just install it...

---

### Post by art on 2006-01-08
after running as sudo do you see that file in /mozilla/firefox?
If yes change permissions and owner to match you...

---

### Post by dannyngweekiat_85 on 2006-01-08
[QUOTE=art]after running as sudo do you see that file in /mozilla/firefox?
If yes change permissions and owner to match you...[/QUOTE]

just check in sudo nautilus... still cant find teh file in mozilla/firefox...
all the pluginreg is int he .mozilla folder... even the one in root.

---

### Post by art on 2006-01-08
OK, I just removed my pluginreg.dat file in .mozilla/firefox. Then run 

sudo firefox 
 
from terminal. Go to Edit->preferences->Downloads and hit View and Edit actions. The file gets regenerated, for me at least. Tell me how it goes...

---

### Post by dannyngweekiat_85 on 2006-01-08
```

rahxephon@ubuntu:~$ cd .mozilla
rahxephon@ubuntu:~/.mozilla$ dir
firefox
rahxephon@ubuntu:~/.mozilla$ cd firefox
rahxephon@ubuntu:~/.mozilla/firefox$ dir
mcnewfjy.default  profiles.ini
rahxephon@ubuntu:~/.mozilla/firefox$ cd mcnewfjy.default
rahxephon@ubuntu:~/.mozilla/firefox/mcnewfjy.default$ dir
bookmarks.html  compatibility.ini  extensions      mimeTypes.rdf  search.rdf
chrome          compreg.dat        localstore.rdf  prefs.js       xpti.dat
rahxephon@ubuntu:~/.mozilla/firefox/mcnewfjy.default$ sudo firefox
/opt/firefox/run-mozilla.sh: line 131:  4989 Segmentation fault      "$prog" ${1+"$@"}

```

Well deleted the file... this are the file in my .mozilla directory..
Still met with the problem... is reverting back to the original mozilla can be a solution?..

---

### Post by art on 2006-01-08
Yeah, run mozilla-firefox from terminal (FF 1.07), see what that does... If it recreates the file you must be able to run 1.5 too

---

### Post by dannyngweekiat_85 on 2006-01-08
```
rahxephon@ubuntu:~/perl$ sudo mozilla-firefox
Password:

run-mozilla.sh: Cannot execute /opt/firefox/mozilla-firefox-bin.

rahxephon@ubuntu:~/perl$ mozilla-firefox

run-mozilla.sh: Cannot execute /opt/firefox/mozilla-firefox-bin.


```

did this... how to run back the older verseion..?... where can i find it?.... is it the  way i type above?.. bu then this came up :confused:

---

### Post by art on 2006-01-08
I don't know how exactly automatix works, haven't used it... Anyway, try 

/usr/bin/mozilla-firefox

this should run the old one... Also you don't need to run this one with sudo, though it should have worked. Also you can check in synaptics if the package firefox is installed. I don't know if automatix removes the older firefox... If it's not there 

sudo apt-get install firefox

should install the original version which ships with ubuntu. Please post back.

---

### Post by dannyngweekiat_85 on 2006-01-09
Well i just remove off the firefox 1.5 off my pc... and found out that automatix did not remove the 1.07 off. Well after that i try to install the 1.5 again but the same problem arise. So now i revert back to 1.07 and it works fine.... so i think will stick with this 1 until dapper release :( Well better than having to use other browser... like firefix more...:)

---

