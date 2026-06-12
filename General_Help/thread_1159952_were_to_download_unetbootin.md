---
title: "were to download unetbootin?"
date: 2009-05-15
forum: General Help
---

### Post by Bearded-flower on 2009-05-15
yeah the title pretty much sums it up
i cant find anywhere .

---

### Post by KhurramM on 2009-05-15
U didnt try google?

U didnt try the local cops or the interpol?

Goto:

[http://packages.ubuntu.com/search?suite=all&keywords=unetbootin](http://packages.ubuntu.com/search?suite=all&keywords=unetbootin)

PS
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by gettinoriginal on 2009-05-15
Check System > Admin > Software Sources > Ubuntu Software tab and make sure that the first 4 boxes are checked, and then reload your repositories.  Once that is done, then unetbootin should be in your Synaptic Package Manager, or if you prefer terminal:
```
sudo apt-get install unetbootin
```

---

### Post by Bearded-flower on 2009-05-15
> **gettinoriginal said:**
> Check System > Admin > Software Sources > Ubuntu Software tab and make sure that the first 4 boxes are checked, and then reload your repositories.  Once that is done, then unetbootin should be in your Synaptic Package Manager, or if you prefer terminal:
```
sudo apt-get install unetbootin
```

Nope, didnt work

---

### Post by gettinoriginal on 2009-05-15
That's wierd, I found it on mine.
[ATTACH]113866[/ATTACH]

---

### Post by colau on 2009-08-31
> **Bearded-flower said:**
> Nope, didnt work
Can you post:
```

sudo cat /etc/apt/sources.list

```

---

### Post by jocko on 2009-08-31
> **colau said:**
> Can you post:
```

suo cat /etc/apt/sources.list

```
The correct command is:
```
cat /etc/apt/sources.list
```
No sudo required, a normal user does have the right to read that file. Quit telling people to use sudo when it's not necessary.

---

### Post by colau on 2009-08-31
> **jocko said:**
> The correct command is:
```
cat /etc/apt/sources.list
```
No sudo required, a normal user does have the right to read that file. Quit telling people to use sudo when it's not necessary.
Typo.
Edited.

---

### Post by jocko on 2009-08-31
> **colau said:**
> Typo.
Edited.
Not done with your editing. Remove the "sudo". Don't tell people to use sudo where it's not needed, it's almost as bad as telling them to enable the root account.

---

### Post by chriskin on 2009-08-31
> **jocko said:**
> Not done with your editing. Remove the "sudo". Don't tell people to use sudo where it's not needed, it's almost as bad as telling them to enable the root account.

using cat with sudo will not make anything bad now, will it? 
:popcorn:

---

### Post by jocko on 2009-08-31
> **chriskin said:**
> using cat with sudo will not make anything bad now, will it? 
:popcorn:
No, but the next time it may be a more harmful command that someone runs as root without knowing what they're doing...

---

### Post by chriskin on 2009-08-31
> **jocko said:**
> No, but the next time it may be a more harmful command that someone runs as root without knowing what they're doing...

can't say you are wrong at that one :)

---

