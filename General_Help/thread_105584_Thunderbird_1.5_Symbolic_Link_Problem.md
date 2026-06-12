---
title: "Thunderbird 1.5 Symbolic Link Problem"
date: 2005-12-18
forum: General Help
---

### Post by Sebby on 2005-12-18
I installed Thunderbird 1.5 as per the Wiki guide (into /opt), but for some reason, it hasn't worked properly. I've done something to the symbolic links, and can start 1.5 by typing [FONT="Courier New"]thunderbird,[/FONT] but cannot run 1.0.7. If I click the Thunderbird icon, I get:

```
Failed to execute child process "mozilla-thunderbird" (too many levels of symbolic links)
```

Running [FONT="Courier New"]mozilla-thunderbird[/FONT] from the command line gives:

```
bash: mozilla-thunderbird: command not found
```

Can someone help me sort this out? I'm sure it's just a case of incorrect symbolic links, but I don't know how to sort them being still fairly new to Linux.

Many thanks in advance.

---

### Post by BathroomNinja on 2005-12-19
Somewhere, you have 1 or more broken sym links.  I couldn't understand from your post, but are you trying to go BACK to 1.0.7, and remove 1.5?  Or are you trying to stick with 1.5 and remove 1.0.7?  Also, can you run either version at all?

---

### Post by Sebby on 2005-12-19
Thanks for the reply.

I to keep both, as per the Wiki guide, being able to run version 1.5 (in /opt) as thunderbird and 1.0.7 as mozilla-thunderbird, but now I'd just like to get rid of 1.5 and go back to 1.0.7!

Many thanks.

---

### Post by BathroomNinja on 2005-12-19
which one of the guides did you follow?  link please

---

### Post by Sebby on 2005-12-19
[https://wiki.ubuntu.com/ThunderbirdNewVersion](https://wiki.ubuntu.com/ThunderbirdNewVersion)

When I got to do the symbolic links (can't remember if it was one or both), it gave me an error saying the file already exists. I then started to play around and have subsequently broken it!

So what I need to do is remove all links and start a fresh. Help. :p

---

### Post by BathroomNinja on 2005-12-19
I'm up really late here at work when I would normally be sleeping; so my judgment may be a bit impared.  However, after reading that very short guide, it looks like it has /opt/thunderbird/thunderbird linked to BOTH
/usr/bin/thunderbird
AND
/usr/bin/mozilla-thunderbird

and as far as my half-asleep mind is telling me; that's possibly not a good thing.

you may need to remove the later link
you would do that with:
```
sudo rm /usr/bin/mozilla-thunderbird
```

After you remove that link, try running it again and see what happens, then report back.

---

### Post by Sebby on 2005-12-19
Thanks, got 1.5 working now by removing the mozilla-thunderbird link. I thought that part of the guide was wrong...

Any idea how to make 1.0.7 work as mozilla-thunderbird?

Sorry for keeping you up. :)

---

### Post by BathroomNinja on 2005-12-19
You're not keeping me up.  I just decided to work overtime tonight.  You will have to either create a link to the old thunderbird file, or just run it directly. However, I'm not sure where it IS.  It looks like the profiles under your /home directory were renamed to .mozilla-thunderbird, but as far as I can tell, the actual binaries were over written by the new version.  Of course, I could be horribly wrong.

---

### Post by Sebby on 2005-12-19
Hmm, not sure, but unless someone knows, I'm not too bothered now 1.5 is working well. :)

---

### Post by BathroomNinja on 2005-12-19
OK.  I followed the same instructions, only I backed everything up first.  And it bonked out on me, so I edited the wiki to reflect a simple step that corrects the issue.

As to your older version of thunderbird, go to the terminal, and do the following:
```

cd /usr/bin
ls -al mozilla-thunderbird
```

if you see something like this:
```
-rwxr-xr-x  1 root root 10584 2005-10-13 11:43 mozilla-thunderbird
```
then you can still run the old version of thunderbird the way you always have.

if you see something like this:
```
lrwxrwxrwx  1 root root 28 2005-12-19 19:38 mozilla-thunderbird -> /opt/thunderbird/thunderbird
```
then I don't know where the old copy of thunderbird is, but you can run the new version using the old icons.

If you see the first one, and want to use the new version of thunderbird with the old versions icons, then do the following:
```
sudo mv thunderbird-1.5rc1.tar.gz /opt/
sudo tar xzvf /opt/thunderbird-1.5rc1.tar.gz
```

---

### Post by Sebby on 2005-12-20
Thanks for the corrections. :)

---

