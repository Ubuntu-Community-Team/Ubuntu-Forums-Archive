---
title: "Todays update wants to remove mobloquer"
date: 2009-03-23
forum: General Help
---

### Post by raffytaffy on 2009-03-23
I saw an update this morning for these packages : moblock, moblock-control. It also wants to install a new package called blockcontrol. But the problem I am seeing is that mobloquer is marked for removal. Any idea what can be done? I am including a screenshot of what the updater wants to do. I am using Hardy.

[[IMG]http://img201.imageshack.us/img201/3310/snapshot46.th.png[/IMG]](http://img201.imageshack.us/my.php?image=snapshot46.png)

---

### Post by jre on 2009-03-23
Which distribution are you on?

There are currently no mobloquer packages for gutsy and hardy. So if you are on this dist I recommend to update to intrepid. If you don't want to do that, stay with your current packages for the time being. Maybe I can readd them.

---

### Post by raffytaffy on 2009-03-23
> **jre said:**
> Which distribution are you on?

There are currently no mobloquer packages for gutsy and hardy. So if you are on this dist I recommend to update to intrepid. If you don't want to do that, stay with your current packages for the time being. Maybe I can readd them.
I am using Hardy right not. I would much rather stay on hardy since its LTS. Thank you very much for responding to my post.

---

### Post by jre on 2009-03-23
I'll try to find a solution.

Until then I've setup a static repository with the old packages. You can use it in case you accidentaly update to the new packages and break your apt db. But as I said, it's static, so it will not get further updates.

You can get it with this line in /etc/apt/sources.list:
```
deb http://moblock-deb.sourceforge.net/20090109 hardy main
```

---

### Post by raffytaffy on 2009-03-23
> **jre said:**
> I'll try to find a solution.

Until then I've setup a static repository with the old packages. You can use it in case you accidentaly update to the new packages and break your apt db. But as I said, it's static, so it will not get further updates.

You can get it with this line in /etc/apt/sources.list:
```
deb http://moblock-deb.sourceforge.net/20090109 hardy main
```

I have these repos : 
```

deb http://moblock-deb.sourceforge.net/debian/ hardy main 
deb-src http://moblock-deb.sourceforge.net/debian/ hardy main 
deb http://moblock-deb.sourceforge.net/20090109 hardy main

```
Whenever I attempt to upgrade moblock and install blockcontrol, it asks to remove mobloquer. I will hold off on the update for now.

---

### Post by Z-T on 2009-03-24
[http://forums.phoenixlabs.org/showpost.php?p=123649&postcount=9](http://forums.phoenixlabs.org/showpost.php?p=123649&postcount=9)

if you still want to use mobloquer you'll have to stick to the old moblock repositories :

since the repositories have changed, deactivate the them :

deb [http://moblock-deb.sourceforge.net/debian/](http://moblock-deb.sourceforge.net/debian/) hardy main 
deb-src [http://moblock-deb.sourceforge.net/debian/](http://moblock-deb.sourceforge.net/debian/) hardy main 

but keep this one :
deb [http://moblock-deb.sourceforge.net/20090109](http://moblock-deb.sourceforge.net/20090109) hardy main

then if you have already installed the newest versions, completely remove all moblock related packages, reload (update your sources list), and reinstall the old packages.

many thanks to jre, he kept a lot of bogon ips away from my machine, during the past year. a very fine stable ipblocker this is !
big hug,
greets Z-T

---

### Post by dj_flx on 2009-03-27
Arg. Yes, a pain since I have to stay in Hardy or lose my legacy nvidia drivers.

---

### Post by jre on 2009-03-27
Well, sorry, but then you have to stay with the static repository for now. After all this just means, that you get no updates.
If this repository goes away, this means that I found a solution to compile the actual mobloquer version under hardy again.

---

### Post by jre on 2009-03-28
I have just uploaded a patched version for mobloquer hardy to the normal repository. Please try again with the sources.list entry
```
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main
``` and give me feedback if everything works.

---

### Post by raffytaffy on 2009-03-30
> **jre said:**
> I have just uploaded a patched version for mobloquer hardy to the normal repository. Please try again with the sources.list entry
```
deb [http://moblock-deb.sourceforge.net/debian](http://moblock-deb.sourceforge.net/debian) hardy main
``` and give me feedback if everything works.

Tried to update, but got errors.
```
E: blockcontrol: subprocess post-installation script returned error exit status 1
E: mobloquer: dependency problems - leaving unconfigured
E: moblock-control: dependency problems - leaving unconfigure
```

Goin back to static repo.

---

### Post by jre on 2009-03-31
Hmm, I'd need more of that logfile to see what went wrong. There *might* be something in /var/log/blockcontrol.log. But I guess I have to check the postinst once again...

---

### Post by jre on 2009-04-02
I just checked raffytaffy's blockcontrol.log (received privately). Everything seems to be ok there.

I've just uploaded a new version (1.3-6), which adds some more verbosity to the postinst. So the output during package installation might be more helpful.

If you try again, please post the complete output that you get during the updating phase.

---

### Post by raffytaffy on 2009-04-03
Well, I updated today and it seems to be a success. Here are the exact steps I took in case anyone wants to know. I edited the apt-get source list adding the moblock repo and the src repo. ```
deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main

``` I then opened synaptic package manager and set mobloquer to be updated, it asked to also update moblock and block-control. The update was a success. :) I wanted to thank JRE for all his time he spent helping me out. It really means a lot to me as I have become a big fan of moblock and its gui mobloquer. The transition to blockcontrol was smooth and the conf had no issues.

---

### Post by jre on 2009-04-04
> **raffytaffy said:**
> Well, I updated today and it seems to be a success. 
[...]
The transition to blockcontrol was smooth and the conf had no issues.
Finally, I'm really glad to hear this. I really hope that I now have fixed all matters in the postinst. After all I wanted to smooth the update there - and not cause problems. I think for most people it worked perfectly with the first release, but for a minority obviously not :-/
So I will remove the static repository soon.

Enjoy!
jre

---

