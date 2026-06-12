---
title: "moving .evolution folder elsewhere"
date: 2011-01-18
forum: Desktop Environments
---

### Post by rafalr on 2011-01-18
The reason I need to do it is that I want to keep all my e-mails and attachments in an encrypted folder (within ~/home).

I did go through all Evolution-related posts here and did not find solution other then using ln as mentioned in some threads. I do not like this solution and would prefer to instruct Evolution directly to store its folder in an alternative location / path.

Any ideas or - better - tested solutions for that ?

Thanks,
Rafal

---

### Post by theDaveTheRave on 2011-01-18
the problem that you face is that evolution is expecting the ./evolution folder to be in this specific location, hence the need to create a link to the new location.

I don't know, but there may be a config option to point evolution to a different location, but it would probably be a system wide change. So only good if you are the only user of your terminal.

I don't know how evolution would handle an 'encrypted' folder - probably slowly. From what I understand evolution is happy to encryp incoming and outgoing mail using pgp (public /private) key pairs.

The only other solution, would be to create a /mail partition and mount it specifically to the ./evolution folder - it's a bit like doing the linking in the opposite direction.

You could then conceivable have a pen drive, and stuff it into your usb port and have it automount. Then when you log off (or walk away from your pc) you simply take your pen drive with you and all your mails, attachments etc. This has a second advantage that all your mail stuff is there when ever you need it, just have a shell script on the key to mount it to the correct location, if you are using someone elses pc.n I'll admit it isn't 'encrypted', but at least you will know exactly where it is at all times.

Don't know if that would work for you?

David

---

### Post by rafalr on 2011-01-18
Thanks, David, I did not think of this.

I am using [EncFS]("http://www.arg0.net/encfs") for encryption where you can almost freely (within your ~/home) assign the mount point.

Next weekend I will give it try on a fresh Ubuntu/Evolution installation and will let know the outcomes.

Rafal

---

### Post by theDaveTheRave on 2011-01-18
glad to be of help.

nice to know I do occasionally have a wierd but useful idea ;)

let us know how it goes (particularly the encryption thing).

David

---

### Post by theDaveTheRave on 2011-01-18
glad to be of help.

nice to know I do occasionally have a wierd but useful idea ;)

let us know how it goes (particularly the encryption thing).

David

---

### Post by rafalr on 2011-01-19
Could not wait with that and did spend some time last night on that.
Works perfectly - thanks David for that simple and elegant idea.

I moved all contents of ~/.evolution to another location, emptied ~/.evolution folder, then made a new encfs volume and made sure that the script to open it is mounting this volume/folder to ~/.evolution. Then I populated the ~/.evolution back with the data and unmounted the encfs.

After proper mounting of the encfs volume to ~/.evolution, the Evolution starts without a blink and works flawlessly. I was pretty sure it should go like that and my only worry was if fuse/encfs will be able to work on two encfs folders at the same time (the second one is for regular documents). But it can, regardless which is mounted first and everything rocks.

The only thing to remember is that the evo folder needs to be mounted first before Evolution starts. I ofcourse made an experiment to launch Evo on unmounted ~/.evolution but nothing did actually blow up - Evolution did set up some empty structure of cache and mail subfolders and pulled all fresh e-mails from the pop3 server. So the only worry in that case is that those emails are not anymore on remote server to be pulled up again after proper mounting of evo catalogue and one needs to export them and then import again after starting Evo on a properly mounted folder. Working on IMAP server will solve it alltogether and that is what I am going to do now.

Rafal

---

### Post by theDaveTheRave on 2011-01-19
you could write a little script for starting evolution, to get it to check for the presence of the folder, and kick out an error message on fail, or have it try to mount it first, wait a bit, then start evolution?

David

---

