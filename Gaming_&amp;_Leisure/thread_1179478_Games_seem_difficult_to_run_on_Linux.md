---
title: "Games seem difficult to run on Linux?"
date: 2009-06-05
forum: Gaming &amp; Leisure
---

### Post by Anybloodyid on 2009-06-05
Hi,

I downloaded this
**[SIZE=2][supertux-0.1.3.x86.package (x86 only)]("http://download.berlios.de/supertux/supertux-0.1.3.x86.package")[/SIZE]**


Now what do I do?

Thanks

---

### Post by del_diablo on 2009-06-05
Fire up a terminal and type in this:
```
sudo apt-get install supertux
```

---

### Post by Tibuda on 2009-06-05
I think you have the Windows mindset, where to install stuff you open google, find a site, download a file and install it, right? This also works on Linux, but it is not the better way. You have a great package manager with tons of software to install with few clicks in Applications > Add/remove. Supertux is available in this package manager, and I suggest you to use it. Read more about it here: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Anybloodyid on 2009-06-05
Well that was simple enough! Thanks
I take it I do the same for all packages?
And is it best to stick to packages when looking for games/apps

---

### Post by Anybloodyid on 2009-06-05
Daniel,

Yep windoze mindset, but I am trying as I now only have linux on my machine so it's try or die!

Thanks

---

### Post by Tibuda on 2009-06-05
> **Anybloodyid said:**
> Well that was simple enough! Thanks
I take it I do the same for all packages?
And is it best to stick to packages when looking for games/apps

It is always best to first search for an application in the package manager, but not every app/game are available there.

---

### Post by Anybloodyid on 2009-06-05
Just had look through the PM and I think it will keep me going for quite a while yet!

Thanks for the help

---

### Post by simeon87 on 2009-06-05
Instead of critizing the Windows mindset, we should also be honest and say that packages in repositories aren't updated as frequently as they should and that sometimes, manually installing a package is just the better option.

---

### Post by Tibuda on 2009-06-05
> **simeon87 said:**
> Instead of critizing the Windows mindset, we should also be honest and say that packages in repositories aren't updated as frequently as they should and that sometimes, manually installing a package is just the better option.

I was not critizing him, only showing the package manager, but you are right about the updates.

---

### Post by mocoloco on 2009-06-05
Actually I'm going to go ahead and criticize the Windows way ;).  You see, if a Windows third-party app causes your system to crash, Microsoft (if you actually contact them for support, which most people don't) will just say "too bad, that's the app's fault, not ours".  And they're right.  So the end user is responsible for keeping his/her system error free.
In contrast, Canonical & the Ubuntu community are responsible for making sure a package will work with a giving release (on a reasonable array of hardware configurations at least) before it's packaged and put in to a repository.  That means the distributor, not the end user, is primarily responsible for making sure software is compatible.

Now in reality that doesn't always work out 100%, but it's of course still better to have a community working to make it work, rather than just the OS provider and the 3rd party developer. And that's why the latest and greatest versions of apps (usually) aren't put into the repositories right away, so they first can be tested and readied for support.

And I'm now realizing I am going off topic so sorry, but it's something that came to mind when seeing this thread :)

---

### Post by CharmyBee on 2009-06-05
And if you're ever executing them DOS style (terminal, cd'ing your way there, but you shouldn't have to), don't forget the ./. That threw me off too from my habits of typing 'gamegame' rather than './GameGame.so'

---

### Post by Nixie Pixel on 2009-06-06
> **CharmyBee said:**
> And if you're ever executing them DOS style (terminal, cd'ing your way there, but you shouldn't have to), don't forget the ./. That threw me off too from my habits of typing 'gamegame' rather than './GameGame.so'
Thanks, that's one of those things that Windows converts just don't realize until far into their Linux experience..

:redface:

---

### Post by LinuxFox on 2009-06-06
> **Anybloodyid said:**
> Well that was simple enough! Thanks
I take it I do the same for all packages?
And is it best to stick to packages when looking for games/appsDeb packages are easier to install, but the Repos aren't usually up to date.  Some downloads don't even use a package.  For example, Nexuiz and Open Arena, just unzip and play.

By the way, that's an autopackage.  To install it you need to right click the icon, choose Properties, choose Permissions, and check the "Allow as executing program box"  Then it should run.  More details can be found on the [Autopackage website]("http://www.autopackage.org/docs/howto-install/").

---

