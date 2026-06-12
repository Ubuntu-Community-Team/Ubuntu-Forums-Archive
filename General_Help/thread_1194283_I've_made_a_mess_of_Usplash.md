---
title: "I've made a mess of Usplash"
date: 2009-06-22
forum: General Help
---

### Post by c1rcu1t on 2009-06-22
To All:

I need assistance with getting Usplash themes to work. I have tried around 15 different themes downloaded from multiple sites, and only got 2 to work for me. The 2 themes I actually got to work booted into a different resolution than what my usplash.conf file was set to, and they had a black box around them. The others I tried to install, defaulted to text format when booting. I have followed all instructions carefully but can't seem to get any of them working. I found a website that gave what I thought promising instructions, and I read up to the point where it gave me this code but I don't understand it:

```
sudo dpkg-reconfigure linux-image-`uname -r`
```

When I run this command I get the result linux-image not installed. I figured that this might be referring to which image I was using, but I didn't want to alter the code with my inexperienced guesses. Please if anyone can help out I would greatly appreciate it.

---

### Post by clonne4crw on 2009-09-28
I think it's safer to use StartUp Manager than to mess around with stuff that tends to break if not handled carefully. It's got a nice interface, and usually works pretty well 

```

# sudo apt-get install startupmanager

```

then run it with 
```

# startupmanager

```

---

