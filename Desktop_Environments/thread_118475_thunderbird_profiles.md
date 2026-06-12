---
title: "thunderbird profiles"
date: 2006-01-17
forum: Desktop Environments
---

### Post by avantgardaclue on 2006-01-17
I am new to ubuntu and have swapped from the rather clunky evolution email to thunderbird email. Most queer, no problems at all in setting it up and using thunderbird as a stand alone application. HOWEVER when i hit an email hyperlink on a web page up pops the thunderbird profile screen asking me to choose my profile, i do, click on ’start thunderbird’ (it’s already open) and it says can’t use this profile because it’s already in use, please choose another profile or create a new one. Very very annoying…. your assistance with regard to this would be most gratefully accepted.

---

### Post by ajgreeny on 2006-01-17
Youn prpbably need to edit the profiles.ini file in your .mozilla-thunderbird folder in your home folder to point to the profile number you want to use.  Open it in gedit or kate or whatever you use and change the default profile number.

---

### Post by avantgardaclue on 2006-01-17
[QUOTE=ajgreeny]Youn prpbably need to edit the profiles.ini file in your .mozilla-thunderbird folder in your home folder to point to the profile number you want to use.  Open it in gedit or kate or whatever you use and change the default profile number.[/QUOTE]

Thanks for the advice, however i don't appear to have a mozilla-thunderbird folder in my home folder!

Is there a search function in file browser to help me find said file? Not that i can see anyway!!

Simon

---

### Post by GeneralZod on 2006-01-17
The file is actually called ".mozilla-thunderbird" and, since it's preceded by a ".", is "hidden".  If you enable "Show hidden files" in your file manager (don't know how to do this in Nautilus; sorry!), you should be able to see it.

Anyway, close down all instances of thunderbird; you can see if any are running by running

```

ps -A | grep -i thunderbird

```

Then, look around in your ~/.mozilla-thunderbird directory and subdirectories for a file called "lock".  If you find it, delete it.  You should be set after this! :)

---

### Post by avantgardaclue on 2006-01-17
[QUOTE=GeneralZod]The file is actually called ".mozilla-thunderbird" and, since it's preceded by a ".", is "hidden".  If you enable "Show hidden files" in your file manager (don't know how to do this in Nautilus; sorry!), you should be able to see it.

Anyway, close down all instances of thunderbird; you can see if any are running by running

```

ps -A | grep -i thunderbird

```

Then, look around in your ~/.mozilla-thunderbird directory and subdirectories for a file called "lock".  If you find it, delete it.  You should be set after this! :)[/QUOTE]

Thankyou General! Nautilus shows hidden files by going to view -> show hidden files, BTW! Anyhow... found the .mozilla-thunderbird directory... definetely no file called lock. 

Ran ps -A | grep -i thunderbird in terminal with tbird shut and nothing reported, ran it again with tbird open and still nothing shown

Dunno if the profile ini file is ok....

[General]
StartWithLastProfile=1

[Profile0]
Name=simon
IsRelative=1
Path=l71zv13g.default
Default=1

Cheeers.... Simon also in Hants UK

---

### Post by GeneralZod on 2006-01-17
[QUOTE=avantgardaclue]Thankyou General! Nautilus shows hidden files by going to view -> show hidden files, BTW! Anyhow... found the .mozilla-thunderbird directory... definetely no file called lock. [/QUOTE]

Did you check the subdirectories, especially l71zv13g.default?

Try

```

cd ~/.mozilla-thunderbird
find . -name "*lock*"

```


> 
Cheeers.... Simon also in Hants UK

Hehe - you won't believe this, but my name is Simon, too :p

---

### Post by avantgardaclue on 2006-01-17
Well, hey ho, no go with thunderbird then, back to Vvolution, which on reflection is now not so clunky!! Did download and install sylpheed email, which went like the clappers but didn't appear to support html composing.

Never mind, thanks everyone for your help.

Simon
Hampshire UK

---

