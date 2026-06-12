---
title: "Firefox slow as hell"
date: 2007-11-19
forum: Desktop Environments
---

### Post by erikf154 on 2007-11-19
I've always used firefox. However, since yesterday it's been retardedly SLOW. It takes 30 seconds to load a page. I have a 2Mb internet line, and never had any issues with speed. 

I use Kubuntu Gutsy, so I fired up Konquerer, and guess what, works like a charm, no delays. Something's going on with my firefox. I clear the cache, history and all that, but still sucks. I also downloaded the 2.0.0.9, but the problem still persist.

Any ideas?

---

### Post by quanumphaze on 2007-11-21
I have the exact problem. :(
 It seems to take 20 seconds to **decide** to begin loading. It just sits there, not using any network like it's waiting for something to connect.
If I open up say 3 tabs, each at 3 second intervals, they all begin to load at the same time.

Disabling IPv6 doesn't work, Fasterfox addon doesn't fix it.

There are other threads out there and few ever have conclusions. Firefox worked fine in Windows, what is wrong here?

*Offtopic-ish* And how do you install Firefox 2.0.0.9? Repos haven't updated yet and in the 'source' tarball there isn't a configure script so no ./configure, make, make install.

---

### Post by erikf154 on 2007-11-21
I fixed it. I created a new profile.

Just go to ~/.mozilla/firefox. There's a folder the called something like xxxxxx.default, change the name to xxxxxx.default.backup. Start firefox again, and it should be way faster.

Mine is incredibly snappy now.

There's a file in the profile folder called bookmarks.html, you might want to copy that over to the new profile to preserve your bookmarks.

---

### Post by justinclark on 2007-11-21
Hey I think Im missing something.  Do I type ~/.mozilla/firefox in the address bar?  If so,I tried and nothing came up.

---

### Post by beow on 2007-11-21
You have to use a shell. Open a Terminal from the Applications/Accessories menu.
Then write 

cd ~/.mozilla/firefox

at the prompt. change the profile name with this command

mv xxxx.default xxxx.default.backup

and restart Firefox. You can also use 

man cd

or

man mv

to learn about the commands

---

### Post by Linteg on 2007-11-21
~/ is your home folder (a kind of shortcut), try going to ~/.mozilla/firefox with nautilus (or konqueror/terminal/whatever), if you choose "show hidden files" you can click your way there if you prefer.

---

### Post by justinclark on 2007-11-21
Ah...duh.  Ok thanks I will give it a try.

---

### Post by newkirk on 2007-11-21
Wiping out the default folder (from firefox's perspective at least - it can't see it once you rename with '.backup')  also removes user-installed extensions and themes, cookies, caches, password storage, etc.  For many that is undesirable.  With just a little work it should be possible to find out much more precisely where the problem is coming from, and then it should be much less catastrophic to resolve and more likely that any bug allowing/causing it can be fixed.

It should be useful if someone experiencing this were to try the following:

1:  Leave everything set up as it 'was' so the problem exhibits.  Then go to 'Preferences' in Firefox, select the 'Security' tab, and try disabling "Tell me if the site I'm visiting is a suspected forgery", then restart firefox and test.  If the problem went away then post that information here, along with whether it was set to "Check using a downloaded list of suspected sites" or "Check by asking..." (Google is only one available by default - if something else is here then make a note of it)

2:  If above wasn't the cause then restore your original setting, then go to 'Tools->Add-ons' in Firefox and change to a different theme, close firefox, try again.  If the problem goes away then it's something funky with the previous theme.  (seems unlikely to me though)

3:  If that made no difference then go to 'Tools->Add-ons' in Firefox and restore your chosen theme, then disable all extensions, close and restart firefox and test.  If the problem goes away then one of the extensions is involved in causing it - in this case, re-enable half the extensions and restart firefox - if it's back then one of the re-enabled extensions is the cause, so disable half of THOSE and try again, otherwise re-disable that half and start working in the other half, and keep narrowing down to find WHICH extension is the cause.

4:  If disabling all extensions made no difference then re-enable them, THEN COPY the xxxxx.default folder to xxxxx.default.backup, instead of just moving it - this way you have a copy of everything that was there, and we can then do the following:

Remove one file or folder from within that directory, and start up firefox.  Test.  Same?  Then close firefox and remove one more and start up firefox.  Rinse and repeat until 'suddenly' firefox starts behaving as expected again.  At this point whatever file/folder you last removed is likely the culprit.  Posting the name of the file/folder and some idea of it's characteristics (size, content sumary, etc) could lead to a fix.  (A 'binary search' as with extensions above is faster but more awkward when dealing with a few dozen config files, subfolders, etc)

Finally, you can restore your 'backup' of the default folder and simply remove the offending file, which should retain most/all of your working environment while still fixing the delay.


personally, my money is on a misbehaving extension...

j

---

### Post by quanumphaze on 2007-11-21
I tried your suggestions newkirk but in the end I had to make a new profile. Disabling the extensions had no improvements and I stuffed up the random deletion of files (Firefox didn't like it).

So +1 for killing the profile, works for me.

Hopefully someone else can find the exact file(s) causing the problem.

---

### Post by justinclark on 2007-11-21
Thanks this ^ post was very helpful,  I will try those first.  My problem does not seem to happen at first so maybe its not a firefox/swiftweasel issue at all.  I have noticed when my laptop is on for a while it starts to slow down.  It didnt do this with xp, only ubuntu 7.10.  I have been researching what it might be.  I have a few things to try.  Any additional tips would be much appreciated.  Thanks in advance.
-Justin

---

