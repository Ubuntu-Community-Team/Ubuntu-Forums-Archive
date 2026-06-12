---
title: "Installation Password"
date: 2009-04-09
forum: General Help
---

### Post by Chargr on 2009-04-09
Hello, I recently downloaded the latest Ubuntu, and I wanted to try it out  before installing, but I'm getting an image which says I need a User/password access. I don't know where this information is at. 

Thank you.

---

### Post by oldos2er on 2009-04-09
Did you run 'Check CD for defects', or md5sum? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Chargr on 2009-04-10
Any reason why It would ask me to log in when I want to try it out for the first time?

---

### Post by CatKiller on 2009-04-10
> **Chargr said:**
> Any reason why It would ask me to log in when I want to try it out for the first time?

Because it's broken. Test your image and the cd you burned, following oldos2er's advice.

You won't normally be asked for a username/password for the live cd session.

---

### Post by Therion on 2009-04-10
Where did you download your install file from?  

I ask because some distros do require you to enter a default username & password ever for a Live session (seems silly to me but I've run into this very situation more than once); a plain-vanilla Ubuntu LiveCD will not.  If you're using something like Super Ubuntu though, the username and password are... Unsurprisingly, **ubuntu**.

---

### Post by N_Nick on 2009-04-10
Ubuntu does sometimes ask for a user and password when for example you kill X (Ctrl + Alt + Del).  It automatically logs in "ubuntu" user after 10 seconds though.

---

### Post by Chargr on 2009-04-10
I downloaded it from this site:

Here's the link

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download).

I used IMGburn to burn the ISO. I guess I'll just burn the iso again.

Thanks for your support.

---

### Post by CatKiller on 2009-04-10
There is a utility on the first menu of the cd that will check for errors by checking the MD5 hashes of all the files. Doesn't take that long. It's worth doing.

Burning at a slower speed often helps to prevent burning errors.

Ubuntu comes with a utility to check the hash of a downloaded file, which you can check against the expected hash [here]("https://help.ubuntu.com/community/UbuntuHashes"). There's probably a similar kind of utility available for Windows, if that's what you're using to download the file. This will check that your download was OK.

---

### Post by coffeecat on 2009-04-10
> **Therion said:**
> some distros do require you to enter a default username & password ever for a Live session (seems silly to me but I've run into this very situation more than once)

Even sillier is the login screen for one distro's live CD (either Mepis or PCLinuxOS iirc) which tells you the username and password above where it's asking you to enter the username and password. :-k 'demo' and 'demo', I think. :-|

---

