---
title: "I removed mime.cache and could not log on anymore"
date: 2015-09-18
forum: Desktop Environments
---

### Post by robert48 on 2015-09-18
Hello

ClamAV found a PUA called mime.cache. I elected to remove it. Wrong move because I could no longer log on to my account. System runs ok under Guest account.

How do I get back in to my account?

---

### Post by sotiris2 on 2015-09-18
I find it weird that removing it causes you to be unable to login. Its not a threat, it's actually a file that helps the operating system distinguish filetypes (linux doesn't do that by extension if you noticed) and from what I understand it contains 'samples' from different filetypes which probably makes AV go nervous (probably thinks that its an executable virus hidden in another filetype?)

Try and see if you can login via terminal. Press Ctrl+Alt+F1 to get to a fullscreen terminal. You can get back to the graphical interface  and your guest account via Ctrl+Alt+F7. In the console you will also have to provide your username. It's one word and no capitals so if you think its Robert Williams its probably robert . After you login type in the following to recreate the file you deleted ```
sudo update-mime-database /usr/share/mime
```It will ask for your password again.

Then switch back to graphics (remember Alt+Shift+F7) and logout of guest and try logging normally. If it doesn't work it probably is not the problem preventing you from logging in but something else you/ClamAv did. Post back.

---

### Post by yetimon_64 on 2015-09-18
Some advice at [http://www.clamav.net/doc/misc-faq.html](http://www.clamav.net/doc/misc-faq.html) regarding turning on the PUA (possibly unwanted application) checks.
> At this point we **DO NOT recommend using it** in production environments,  because the detection **may be too agressive and lead to false positives**.  In one of the next releases we will provide additional features for  fine-tuning allowing better adjustments to different setups. **NOTE: A  detection as PUA does NOT tell if a application is good or bad.** All it  says is, that a file MAYBE unwanted or MAYBE could compromise your  system security and it MAYBE a good idea to check it twice. I have put the bolded text in above for emphasis only.

mime.cache is a normal system file, as sotiris2 notes "it's actually a file that helps the operating system distinguish filetypes". Something you definitely should not delete/remove. I'd try fixing the mime database as sotiris2 suggests and see if any change happens with logging in.

Just to note, I don't use clamav but have on many occasions on this forum read of clamav and what turns out as false positives.
This includes at least 1 thread where clamav found its own files it installed and declared them as a virus :lol:

---

### Post by v3.xx on 2015-09-18
Just to confirm

I removed mime.cache and successfully rebooted and used the above command to restore mime.cache.

No harm done.

---

### Post by robert48 on 2015-09-19
Hole in one!

Thank you very much for the assistance and I will now switch off the PUA check in ClamAV.

sotiris2 fix worked a treat. namely:-

Logged on using Guest account
used ctrl+alt+F1 to get to console
logged on in console to the account that I couldn't access
ran the command- ```
sudo update-mime-database /usr/share/mime
```
entered name and password again
when back to cursor ran the command-  ```
exit
```
used ctrl+alt+F7 to get back to GUI
restarted
logged in to previously inaccessible account
all is well!

Very many thanks again.

---

