---
title: "AmaroK can't play files"
date: 2006-06-02
forum: Desktop Environments
---

### Post by cypresstwist on 2006-06-02
I did an upgrade to Dapper final from the Dapper testing I installed some weeks ago. Now amaroK can't play any files. I can't even select xine-engine (which btw IS installed):

[i]sudo apt-get install libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree... Done
libxine-extracodecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/i]

[img]http://img236.imageshack.us/img236/4977/screenshoterroramarok0rs.png[/img]

I don't know what to do. XMMS plays them fine. :(

---

### Post by Rackerz on 2006-06-02
Remove amarok and get 1.4. Check the amarok page on kde.org.

---

### Post by cypresstwist on 2006-06-02
[QUOTE=Rackerz]Remove amarok and get 1.4. Check the amarok page on kde.org.[/QUOTE]

I'm using AmaroK 1.4a. Forgot to mention :)

---

### Post by Rackerz on 2006-06-02
Have you tried re-installing the xine engine?

---

### Post by cypresstwist on 2006-06-02
[QUOTE=Rackerz]Have you tried re-installing the xine engine?[/QUOTE]

Yes. No change. I even tried installing amarok-engines, but other engines don't show up in the list...

---

### Post by Ramses de Norre on 2006-06-02
Is everything set up correct in the engine section of the amarok configure section? Do you have set the right output plugin etc?

---

### Post by tribut on 2006-06-02
[QUOTE=Ramses de Norre]Is everything set up correct in the engine section of the amarok configure section? Do you have set the right output plugin etc?[/QUOTE]

I've got the same problem and so those people: [http://www.ubuntuforums.org/showthread.php?t=26308](http://www.ubuntuforums.org/showthread.php?t=26308)
It seems as if xine does not provide an arts output plugin on dapper (at least it does not show up in the list if I do a "killall artsd && amarok" and then select xine as engine...

---

### Post by cypresstwist on 2006-06-02
[QUOTE=Ramses de Norre]Is everything set up correct in the engine section of the amarok configure section? Do you have set the right output plugin etc?[/QUOTE]

This worked:

rm ~/.kde/share/config/amarokrc

I lost all amarok settings but hey, xine engine working again :D
Thanks for the help! :KS

---

### Post by tribut on 2006-06-02
[QUOTE=cypresstwist]This worked:
rm ~/.kde/share/config/amarokrc[/QUOTE]

Unfortunately, it did not work for me. Also, I get the same error trying to start kaffeine with xine-engine (Loading of player part 'KaffeinePart' failed. / All Audio Drivers failed to initialize!). So I don't think this can be resolved by simply deleting amarok config-files...

:-?

---

