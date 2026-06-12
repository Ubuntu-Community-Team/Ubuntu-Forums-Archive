---
title: "Wierd! Thunderbird lost all my mail settings?"
date: 2005-12-30
forum: Desktop Environments
---

### Post by NobleSavage on 2005-12-30
Ok, I fire up Thunderbird to check my mail this AM and it presents me with the Add New Account Wizard!!!  Huh? I cancel out of this and then go to Edit > Account Settings and there are no accounts listed.  What hapend to my mail?  :confused:

---

### Post by kperkins on 2005-12-30
Is your .mozilla-thunderbird folder still in your home folder?
Did you upgrade, or anything?

---

### Post by NobleSavage on 2005-12-30
[QUOTE=kperkins]Is your .mozilla-thunderbird folder still in your home folder?[/quote]

Yes

> 
Did you upgrade, or anything? Ocassioanaly, my laptop will overheat and just shut down.  That may have happend last night - I'm not sure. It happens quite often (POS Alienware).

Other than that, I didn't do anything.  Any idea what could have happend? Should I check my log files, if so which ones?  

Thanks.

---

### Post by art on 2005-12-30
The same thing happened to me recently, when I tried the integrated "Check for upgrade" in Thunderbird 1.5. So if you have the 1.5 RC1,2 then if you followed instructions on wiki must have .thunderbird and .mozilla-thunderbird in your home directory. Remove .thunderbird with

cd ~/.thunderbird
rm -rf *
cd ~
rmdir .thunderbird

cp -r .mozilla-thunderbird .thunderbird

That did the trick for me. 
HTH

---

### Post by NobleSavage on 2005-12-30
[QUOTE=art]The same thing happened to me recently, when I tried the integrated "Check for upgrade" in Thunderbird 1.5. So if you have the 1.5 RC1,2 then if you followed instructions on wiki must have .thunderbird and .mozilla-thunderbird in your home directory. Remove .thunderbird with

cd ~/.thunderbird
rm -rf *
cd ~
rmdir .thunderbird

cp -r .mozilla-thunderbird .thunderbird

That did the trick for me. 
HTH[/QUOTE]

I've got Thunderbird 1.0.7

and I don't have a .thunderbird directory. :???:

---

### Post by art on 2005-12-30
What's in your .mozilla-thunderbird? Do a 

ls -a ~/.mozilla-thunderbird 

please post results...

---

### Post by NobleSavage on 2005-12-30
[QUOTE=art]What's in your .mozilla-thunderbird? Do a 

ls -a ~/.mozilla-thunderbird 

please post results...[/QUOTE]


6gf70q7s.default  appreg  profiles.ini

---

### Post by art on 2005-12-30
Also 

more profiles.ini

It should look like 

more profiles.ini
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=bgbcwzcp.default
Default=1

---

### Post by NobleSavage on 2005-12-30
more profiles.ini gives me this:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=6gf70q7s.default
Default=1

---

### Post by art on 2005-12-30
This all looks fine man, when you launch Thunderbird from Applications->Internet->Thunderbird Profile Manager, what happens?

---

### Post by NobleSavage on 2005-12-30
[QUOTE=art]This all looks fine man, when you launch Thunderbird from Applications->Internet->Thunderbird Profile Manager, what happens?[/QUOTE]

Same thing, it launches the Set up New Account wizzard. This is wired.

---

### Post by art on 2005-12-30
Well, it comes to the point that I am confused. When you launch it from command-line, you run mozilla-thunderbird right? Then on thing to check 

more /usr/bin/mozilla-thunderbird


and see if you have this line

  MOZ_USER_DIR=".mozilla-thunderbird"
 
Also what is in your .mozilla-thunderbird/6gf70q7s.default directory?

---

### Post by NobleSavage on 2005-12-30
[QUOTE=art]Well, it comes to the point that I am confused. When you launch it from command-line, you run mozilla-thunderbird right?[/quote]
Yes

> 
more /usr/bin/mozilla-thunderbird


and see if you have this line

  MOZ_USER_DIR=".mozilla-thunderbird"

Yep, it's there.
 > 
Also what is in your .mozilla-thunderbird/6gf70q7s.default directory?


abook.mab          components.ini  key3.db         prefs.js   XUL.mfasl
cert8.db           compreg.dat     localstore.rdf  secmod.db
chrome             defaults.ini    mailViews.dat   US
compatibility.ini  extensions      mimeTypes.rdf   xpti.dat


I hope my mail isn't lost for good, I had some important stuff in there. :(

---

### Post by art on 2005-12-31
It seems to be pretty bad, in my understanding, all Mail folders gone... Was it a POP account or IMAP? What's in prefs.js, do you see any information on your accounts? You aren't logged in as a different user accidentaly, are you? Other than that I really don't know, maybe you can also look for the profile directory moved somewhere, like do a search as 

 locate *default | grep thunderbird

Although I doubt it... Maybe someone more knowledgable has better I ideas?

---

### Post by NobleSavage on 2005-12-31
> **art]Was it a POP account or IMAP? [/quote]

It was a POP account that I run from my web server. 

>  What's in prefs.js, do you see any information on your accounts?  this is what is in prefs.js: user_pref("extensions.disabledObsolete", true) said:**
> 
You aren't logged in as a different user accidentaly, are you? 

No, I only have one account on this computer.

> 
Other than that I really don't know 

Well, thanks for trying to help!

---

### Post by art on 2005-12-31
It's really impossibe for a whole directroy just to dissappear (by itself)... Maybe someone else has access to your computer, and accidentally removed/renamed the profile directory? I don't know... Maybe it's worth doing a 

ls -a ~/ 

and see what you have there...

---

### Post by NobleSavage on 2005-12-31
[QUOTE=art]It's really impossibe for a whole directroy just to dissappear (by itself)... Maybe someone else has access to your computer, and accidentally removed/renamed the profile directory? I don't know... Maybe it's worth doing a 

ls -a ~/ 

and see what you have there...[/QUOTE]

What is the name of the profile directory? What kind of files am I looking for?  I never examined Thunderbird before.  The only one who could have accessed my computer is my pet Cat... She does like to walk around and over the keyboard often.

---

### Post by art on 2005-12-31
So, in the Thunderburd that comes with Ubuntu installation it's .mozilla-thunderbird, on the Thunderird 1.5 it's .thunderbird. Then in this directory you have 3 things

appreg  [COLOR="RoyalBlue"]**bgbcwzcp.default**[/COLOR]  profiles.ini

the **[COLOR="RoyalBlue"]bgbcwzcp[/COLOR]** is a random name for profile directory, in which all your settings and mails are stored. This is a list of my profile directory

30892379.s         downloads.rdf          key3.db          secmod.db
abook.mab          [COLOR="RoyalBlue"]**extensions**[/COLOR]               localstore.rdf  [COLOR="RoyalBlue"]**US**[/COLOR]
cert8.db               extensions.cache   [COLOR="RoyalBlue"]**Mail**[/COLOR]                 virtualFolders.dat
[COLOR="RoyalBlue"]**chrome**[/COLOR]                extensions.ini          mailViews.dat  xpti.dat
compatibility.ini   extensions.rdf          mimeTypes.rdf   XUL.mfasl
components.ini    history.mab             [COLOR="RoyalBlue"]**News**[/COLOR]
compreg.dat        [COLOR="RoyalBlue"]**ImapMail**[/COLOR]                  panacea.dat
defaults.ini            install.log                 prefs.js

As you see I have ImapMail folder, Mail folder, the 30892379.s has the passwords... I don't have a POP account, so I dont know, probably there will also be a PopMail folder...

---

### Post by kperkins on 2005-12-31
You should have a Mail directory in you default profile folder.  It seems that you don't.  Have you checked your trash to see if it got deleted by mistake?
You may be missing some other stuff too, from the looks of it.
If the Mail folder got deleted, and isn't in the trash, then I think you've lost it for good.

---

### Post by skunkjoe on 2007-08-19
Hi!

I had a similar problem. after doing a "sudo mozilla-thunderbird"(update) all my mail-accounts disappear....
this solution worked for me: delete the .mozilla folder that has been created in the /root directory...
(also check the size of the mail folder...if its larger than a few MBytes your mails should be still in there)

-skunkjoe

---

### Post by evolving_monkey on 2007-08-29
Something similar happened to me after the last Thunderbird update. My email is downloaded to a storage drive so I luckily still have that. Since that update, however, it keeps telling me the passwords for my email accounts are wrong or that the server is not responding. I reenter the correct passwords and I simply get the same error messages.

I also have Thunderbird on a windows box that pulls down the same email accounts and it has no problem. The XP box is running Thunderbird 2.0. 

It might just be coincidence with the update but I've been using it for months without a problem. Now after the update the problem shows up.

EDIT: forgot to mention that the password problem seem to be the only problem. All of my other settings seem to be fine. Also it only seems to happen when I am trying to send mail. Receiving seems to be working fine.

---

### Post by ahbart on 2008-06-11
I just had the same problem with thunderbird 2.0.0.14. Just for the record, I found the solution over here:
[http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared](http://kb.mozillazine.org/Recovering_a_profile_that_suddenly_disappeared)
It has something to do with the prefs.js file after a system crash or something like that. (Back it up)
Bart

---

