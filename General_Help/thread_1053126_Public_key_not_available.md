---
title: "Public key not available"
date: 2009-01-28
forum: General Help
---

### Post by stillious on 2009-01-28
Hi guys

I have a problem when running apt-get update, where the below error is returned:

```
Fetched 308B in 0s (1273B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C71839136CF5CE97
W: You may want to run apt-get update to correct these problems

```

Running apt-get update again does not fix the above error. At first (because of my noobness) I thought it might be a duff entry in sources.list, but this does not seem to be the case :/ Do I need to install a key, but it doesn't know where to find it?

Any help appreciated ;)

---

### Post by stillious on 2009-01-28
OK so after some Googling, I found an answer of sorts and managed to get a solution. In my case I entered the following:

```
gpg --keyserver subkeys.pgp.net --recv C71839136CF5CE97
```

Then

```
gpg --export --armor C71839136CF5CE97 | sudo apt-key add -

```
Then a good old update to finish off

```
sudo apt-get update
```

Fixed :)

---

### Post by rebegin on 2009-01-28
hey,
thanks, i was looking for exactly the same thing.

---

### Post by greyfox1 on 2009-01-29
Wow, kudos for posting this stillious!  I was getting this error and your solution worked like a charm!  In my case, I was getting the error with different keys, so I just had to plug mine into the commands and now I'm set.  I just wish the "thanks" button were working right now :D  

Cheers!

---

### Post by rebegin on 2009-01-29
hehe, that's just funny that i was looking for the "thanks" button for like 10 minutes but no luck. now i know at least that it's simply not around here nowadays :(

---

### Post by Mickser_52 on 2009-01-30
Just adding my thanks! The solution didn't work at first till I discovered I had left out the space between add and - in the last line.

sudo apt-get update worked without any error message and after all that there was no update!

Wonder why it happened in the first place?

---

### Post by hesjnet on 2009-01-30
It worked perfectly! thanks:p

---

### Post by greyfox1 on 2009-01-30
> **rebegin said:**
> hehe, that's just funny that i was looking for the "thanks" button for like 10 minutes but no luck. now i know at least that it's simply not around here nowadays :(

I think that the thanks button, along with the option to mark threads "solved" is temporarily not available for some reason.  It has happened before, although I'm not exactly sure why.  I believe both will be back at some point.

---

### Post by Zeedok on 2009-01-30
Someone has written a script which sorts this out for me.  You can find it [here]("http://ubuntuforums.org/showthread.php?t=1047743&page=5").

---

### Post by Richie_ on 2009-01-31
I get this message too, and while the solution posted seems to work I'm reluctant to try it.

The whole meaning of gpg keys is to make sure you access the server you think you use. If the key has changed the server you access could be a malicious one.

That said, call me paranoid, but I would really like to know why the key isn't known by my install before I add that key to my system!

---

### Post by mb_webguy on 2009-01-31
If you're that paranoid, maybe you shouldn't use PPAs to begin with...  ;)

But really, each PPA has a link to its key on the Launchpad page (and if you don't trust *that*, then you really *shouldn't* use PPAs).  All you have to do is click on the link, then right-click on the keyID link to save it to your computer.  Then click the Add button on the Authentication tab of Software Sources, and select the downloaded file to add the key.

The addition of keys for Launchpad PPAs is relatively new.  I imagine that future releases of Ubuntu will include some sort of one-click support for downloading and installing PPA keys.

---

### Post by Richie_ on 2009-01-31
OK, thanks for clarifying. I feel confident enough now ;)

Still don't really understand why it complains about the key all of a sudden, as I didn't change anything for at least a month.

---

### Post by jammrk on 2009-04-19
Just wanted to say thank you for the post, I had the problem myself and it worked perfectly.

---

### Post by happyenduser on 2009-04-21
[FONT=Trebuchet MS][SIZE=3][COLOR=Black]Thanks for this stillious info, 
problem is solved.

Teh google was not strong with me 
on my original searches.[/COLOR][/SIZE][/FONT]

---

### Post by sharath kumar on 2011-05-02
Your solution worked superbly thanx alot

---

