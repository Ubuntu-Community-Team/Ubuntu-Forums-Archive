---
title: "User settings not sticking"
date: 2009-05-24
forum: General Help
---

### Post by kennedyjch on 2009-05-24
I've now had two ubuntu machines which exhibit signs of malware attacks:
- .gconf changes to evolution, keyboard and network setup
- firefox lost bookmarks; attempt to examine addons crashes firefox

Has anyone else had similar problems? How to protect against? How to recover .gconf?

Thank you in advance.

---

### Post by colau on 2009-05-24
How could you detect the malware attacks?

---

### Post by aysiu on 2009-05-24
It actually sounds more like you somehow changed ownership of those directories to root (probably by using *sudo* with graphical applications instead of using *gksudo*).

Close all your applications. Then type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username:username* /home/*username*
``` where *username* is your actual username.

---

### Post by kennedyjch on 2009-05-24
Thanks for the tip on premissions - however that has not fixed the problem that my evolution always launches the wizard despite there being messages, etc. I presume that the e-mail configuration got trashed. I do not know which file it is (I suppose something in the .gconf structure). Any clues?

---

### Post by aysiu on 2009-05-24
Well, it could be a bug in Evolution.

I would try either /home/*username*/.evolution or somewhere in /home/*username*/.gconf

---

### Post by kennedyjch on 2009-05-25
ALso noticed that the "locations" settings (date, time, etc.) have been lost - I had at least 3-4 different locations specified - now they are all gone. 

What could have done this?

---

### Post by bapoumba on 2009-05-25
Moved to Security.

---

### Post by aysiu on 2009-05-25
> **bapoumba said:**
> Moved to Security.
Really? I'm not convinced this is a security breach at all. It seems to be either some kind of accidental user error, a software bug, or a combination of the two.

---

### Post by Wiebelhaus on 2009-05-25
Run [Bit Defender]("http://www.bitdefender.com/PRODUCT-80-en--BitDefender-Antivirus-Scanner-for-Unices.html") It's free and the best malware protection , period.

But I agree with aysiu on this matter , I don't think the machine has been compromised but it's better to be safe than sorry.

---

### Post by HermanAB on 2009-05-25
Hmm, well, I would not classify Evolution as malware, but it is rather buggy and I won't use it.  Try Thunderbird instead - it is very stable.

---

### Post by bodhi.zazen on 2009-05-26
> **aysiu said:**
> Really? I'm not convinced this is a security breach at all. It seems to be either some kind of accidental user error, a software bug, or a combination of the two.

+1

It is sad that viruses and what not are so prevalent in some OS that every time there is a problem one assumes it is a virus.

This is simply not the case in Linux and there is not much here to suggest we know what the cause of the problem is , so best not to jump to conclusions.

---

### Post by aysiu on 2009-05-26
I've retitled the thread and moved it to General Help.

---

### Post by bapoumba on 2009-05-26
> **aysiu said:**
> Really? I'm not convinced this is a security breach at all. It seems to be either some kind of accidental user error, a software bug, or a combination of the two.
Sorry :)
Thanks for moving it back.

---

### Post by aysiu on 2009-05-26
> **bapoumba said:**
> Sorry :)
Thanks for moving it back.
No worries. I can understand why you might have moved it.

---

### Post by kennedyjch on 2009-05-30
Thanks all for the replies. I too do not want to be "alarmist" but this all started when I visited a page in FireFox. FF indicated that the site was "dangerous" and I ceased going further.

However, just at that time, my FF bookmarks disappeared. I was able to get them back deactivating "Ubuntu Firefox modifications 0.7".

At the same time, I noticed that my evolution account information disappeared - again, the inbox and other folders appeared to be there and filled with data. Just no account information thereby evolution started the wizard.

Next, I found that some desktop settings (screen saver, locations on the date-time drop-down" too have been lost. I restored them, but they periodically disappear when I logout and re-login.

I've checked ownership of /home/<myusername> files and their descendents.... No problem.

So, I'm still looking for solutions and a reason for the erratic behaviour I'm experiencing. I had used a stable Ubuntu system pretty much since 7.04 and now I concerned that I committed some terrible "user error" or that there is something funny going on with my 9.04 installation.

Any additional suggestions would be appreciated. I'm considering that, lack of anything else, reinstalling 9.04. But I do not want to do that until I've used up other options as I've configured DansGuardian and other services that would be a hassle to reconfigure...

Thank you in advance.

---

