---
title: "Help! update not working!"
date: 2009-06-16
forum: General Help
---

### Post by phr33k-dc on 2009-06-16
added some software sources to software.list but obviously key is hidden so want to delete it but dont know which one it is. 
any help would would be great.
p.s i have ubuntu tweak if it helps

---

### Post by drs305 on 2009-06-16
Add the key with this command. Replace the X's with the code you are getting:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com XXXXXXXXXXXX

```
Example: 
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 60D11217247D1CFF

---

### Post by phr33k-dc on 2009-06-16
thaks a million man that did it.
do you know of any websites or repositries that would be cool to add?

---

### Post by drs305 on 2009-06-16
> **phr33k-dc said:**
> thaks a million man that did it.
do you know of any websites or repositries that would be cool to add?

You seem to have already found the launchpad repositories ;-) 

Another popular and trustworthy site (with keys) is Medibuntu, which has multimedia packages and other popular apps (googleearth, realplayer, acroread, etc). Here is a link for adding the repositories and keys:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
Run the command in the "Any Ubuntu Release and keyring:" section.


Be careful about adding 3rd party apps and repositories. The above-mentioned ones are pretty well-established, but any third-party repository may contain packages not fully tested with ubuntu and could break things. Not to mention the possibility of containing packages *designed* to break things. That doesn't happen much (if at all) in linux yet, but realize that anyone can put up a repository with anything they want inside it.

---

### Post by phr33k-dc on 2009-06-16
What do you mean by launchpad? i have the medibuntu by the way and ye it could be dodgy for someone

---

### Post by drs305 on 2009-06-16
> **phr33k-dc said:**
> What do you mean by launchpad? 

That was the repository in the original post requesting the key: [http://ppa.launchpad.net](http://ppa.launchpad.net)

---

