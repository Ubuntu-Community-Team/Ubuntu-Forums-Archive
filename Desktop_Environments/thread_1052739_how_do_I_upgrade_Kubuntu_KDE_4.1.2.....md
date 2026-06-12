---
title: "how do I upgrade Kubuntu KDE 4.1.2...."
date: 2009-01-28
forum: Desktop Environments
---

### Post by bagwanram on 2009-01-28
Hello,

This is my first post, and i must say thanks for how helpful these forums have been in getting UbuntuStudio running on my computers! 

I have been sucessful in getting Kubuntu-kde4-desktop installed on a Dell Inspiron 1721. I am running Hardy 8.04.

Can I update KDE 4.1.2 to the new 4.2 yet?

May I please get the process to do so?

If it is not availabe for hardy yet, how can I upgrade to 4.1.4?

Thanks!

---

### Post by Wintervenom on 2009-01-28
Check the Kubuntu homepage, and your question shall be answered. ;)

---

### Post by bagwanram on 2009-01-28
Ok I found howto get 4.1.4 Iam getting it now... I'll restart and see...


Thanks for the quick reply!

---

### Post by bagwanram on 2009-01-28
Ok after reboot I still have KDE 4.1.2

I opened Adept, then enabled pre-release software, clicked full upgrade.
20 updates were installed, after restart I still have 4.1.2.

hmmmm

Is there a repository i must add to get 4.1.4?

the instructions on the web site were quite easy....

(from the website)

[I]KDE 4.1.4
Submitted on Tue, 2009-01-13  
The latest KDE 4 update 4.1.4 is compiling now in the proposed updates section of Kubuntu 8.10.
To install it enable Pre-released Updates in Adept, then under Changes click on Upgrade and Apply[/I]

Hmmm am I missing something else?

---

### Post by Wintervenom on 2009-01-28
[http://www.kubuntu.org/news/kde-4.2]("http://www.kubuntu.org/news/kde-4.2")

---

### Post by bagwanram on 2009-01-28
Thanks! I am tring it now...

---

### Post by bagwanram on 2009-01-28
Ahh...

I now see... The KDE page says nothing about 4.1.4 and Ubuntu Hardy 8.04.

Ok fine then, does 8.10 Intrepid Ibex support dual-core Procs w/ rt-kernel yet?

It is the only reason i am running 8.04

---

### Post by mac71 on 2009-01-28
Hi,
Here's what I did:

Open Adept and click on sources. Then click on edit software sources.
Now click on the third party software tab and then click on add at the bottom.
Paste this line into the box:
[HTML]deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main[/HTML]

Also paste this into konsole to add the package signing key:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```

Update and restart.

Hope that gets you sorted.

---

### Post by bagwanram on 2009-01-28
So this will work on 8.04? I thot I tried that earlier(I have been majorly geeking out on two computers each with multiple boot options) and after restart it would only boot to Gnome....hmmmm

---

### Post by fung on 2009-01-28
> **mac71 said:**
> Hi,
Here's what I did:

Open Adept and click on sources. Then click on edit software sources.
Now click on the third party software tab and then click on add at the bottom.
Paste this line into the box:
[HTML]deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main[/HTML]

Also paste this into konsole to add the package signing key:
```
gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -
```

Update and restart.

Hope that gets you sorted.

I believe this upgrades you to KDE 4.2...

---

### Post by bagwanram on 2009-01-28
Kde 4.2 would be nice. If this method works for 8.04 i'll try it...
Is it advisable to wait till it is officially supported for 8.04?

---

### Post by fung on 2009-01-29
I literally updated to 4.2 about 20 minutes ago on my laptop. I can't say I've tried out all the features yet but it seems fine just like before.

---

### Post by jacksaff on 2009-01-29
I'm not sure kde4.2 will get official support for 8.04. Wasn't 8.04 a kde3 based release?
It will probably be backported, but it won't be in main.

---

### Post by bagwanram on 2009-02-04
Thanks All, if there are any updates to KDE 4.2 on Hardy I would like to know.

Peace
Jazz

---

