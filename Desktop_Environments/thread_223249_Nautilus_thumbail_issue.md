---
title: "Nautilus thumbail issue"
date: 2006-07-26
forum: Desktop Environments
---

### Post by kronicd on 2006-07-26
Hello,

I recently ran an 'apt-get dist-upgrade' which seems to have caused some problems with Nautilus (2.14.1).

The issue is that thumbnails are not being generated or displayed. When I had this problem previously I removed .thumbnails from my home directory and the problem was solved. However this did not help this time.

The .thumbnails directory was recreated automatically by Nautilus, however no  thumbnails were generated.

Here is a screenshot of Nautilus and the issue.

[IMG]http://ems.kronicd.net/images/Screenshot.png[/IMG]

Any assistance/ideas would be greatly appriciated.

---

### Post by orb9220 on 2006-07-26
Have you done a reboot? I had the same problem but it went away and now works   fine.

My settings are the same as yours.

Sorry I couldn't help.

---

### Post by kronicd on 2006-07-26
> **orb9220 said:**
> Have you done a reboot? I had the same problem but it went away and now works   fine.

My settings are the same as yours.

Sorry I couldn't help.

Thanks for the suggestion, I've tried rebooting a couple of times but it hasnt helped :(

---

### Post by kronicd on 2006-07-26
I've found something quite odd...

If I swap from 'local files only' to 'always' in the preferences dialog it starts working perfectly!

So for some reason its not detecting that the local files are infact local.

I'm not sure what this means and as nobody else is reporting the same problem I don't think I should report a bug until i can isolate/repicate the issue on another machine.

Anyone got any ideas?

---

### Post by orb9220 on 2006-07-26
Well mine is local so you may want to switch it back to local and see if the thumbs stay.

Just a thought.

---

### Post by levhita on 2007-06-07
It happens exactly the same with me, I'm using ubuntu feisty all updated.

By the moment I turn it to "Always" I don't use nautilus to browse ftp sites anyway.

---

### Post by drunya on 2007-06-09
I have the same problem... Ubuntu 7.04 all upgraded and no thumbnails.. :( May be someone knows how to solve it?

---

### Post by GrouchoMarx on 2007-08-10
Try manually recreating the .thumbnail directory tree first:

.thumbnails
.thumbnails/fail
.thumbnails/fail/gnome-thumbnail-factory
.thumbnails/large
.thumbnails/normal

For some reason nautilus doesn't seem able to create the directories itself.

---

