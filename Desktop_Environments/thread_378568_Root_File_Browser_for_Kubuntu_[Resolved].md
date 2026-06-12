---
title: "Root File Browser for Kubuntu [Resolved]"
date: 2007-03-07
forum: Desktop Environments
---

### Post by RAdams on 2007-03-07
I've been messing with Kubuntu lately, and have come across a strange problem. In Ubuntu, "gksu nautilus" would give me a root file browsing window without any problems. However, "kdesu konqueror" gives me the following error message when I try to edit text files (such as my xorg.conf): "KDEInit could not launch 'Kate'." Anyone have any insight as to why this might be? Thanks.

---

### Post by milton1 on 2007-03-07
kde is a bit funny about what should work with kdesu and what does work with kdesu. try launching it with sudo. I know it should be wrong, but sometimes it works.

---

### Post by true_friend on 2007-03-08
Go to that folder by normal konqueror permission right click on file to be editied choose from actions Edit As Root
ender password and edit the file. by the way i never experienced any problem like this.

---

### Post by RAdams on 2007-03-08
> **true_friend said:**
> Go to that folder by normal konqueror permission right click on file to be editied choose from actions Edit As Root
ender password and edit the file. by the way i never experienced any problem like this.

I'm aware of that method, but it's not what I want. I want a root file browser. I'll try the sudo suggestion.

---

### Post by RAdams on 2007-03-09
When I use sudo, it simply never launches. The Konq task shows up in the taskbar, but the program never opens, asks for a password, anything. When I sudo konqueror in the terminal, I get:
```

X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

and the same error happens: when I attempt to open a text document, I get the above mentioned error message. Actually, I get it twice for some reason.

When I kdesu konqueror in a terminal, it never opens, or asks for a password, just returns the error mentioned above. :( 

Any insights?

---

### Post by aysiu on 2007-03-09
Read this:
[Preventing the error message "KDEInit could not launch kdesu"](http://www.kde-forum.org/archive/14916/thread.html)

Also, please **never** use *sudo* with a graphical application like Kate or Konqueror. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by RAdams on 2007-03-09
Thanks for the informational link about sudo and graphical programs. I had thought that was true, and that explanation makes perfect sense.

Alas, the first link, while the solution seems like it should work, gives me the exact same error... :(

For the record, using the Right-Click --> Edit as Root option works fine for me, and I haven't changed anything with KDEInit, Kate, or Konqueror that could bring this about.

UPDATE: Restarted after tinkering around with some completely unrelated stuff. It works now. I couldn't tell you why a restart fixed it. It appears it did, though... :\

---

### Post by RAdams on 2007-03-12
IMPORTANT: Given that this is the #1 result in google for "root file browser kubuntu" I thought I would come back and say I'm getting that error again... :(

I really don't understand why it works like a charm some times and not others... any insights? I can post any debugging info you want to see.

---

### Post by bigfatgeek on 2007-03-13
Try this... do an alt+F2 to bring up the "Run Command" dialogue box and insert the following command...

kdesu kfmclient openProfile filemanagement

You could also make a desktop or toolbar item/icon. 

Of course it's relatively unsafe, and you should do your file management deeds and close it. I wouldn't peruse any Internet URL's in that mode either. 

Hope that works for you.

---

### Post by RAdams on 2007-03-13
> **bigfatgeek said:**
> Try this... do an alt+F2 to bring up the "Run Command" dialogue box and insert the following command...

kdesu kfmclient openProfile filemanagement

You could also make a desktop or toolbar item/icon. 

Of course it's relatively unsafe, and you should do your file management deeds and close it. I wouldn't peruse any Internet URL's in that mode either. 

Hope that works for you.

I've tried that. I get the same results as "kdesu konqueror".

---

### Post by MamiyaOtaru on 2007-03-19
Try running kdeinit as root first.  

I *think* your problem sounds like something I used to run into that was solved by running kdeinit first.

---

### Post by mocha on 2007-05-07
This is a problem for me as well.  Ever since I upgraded my Kubuntu Edgy I am having problems opening Konqueror as root.  I tried restarting kdeinit and then it works, but after that nothing else works and I get "launcher could not talk to dcop" (or something like that) as well as some other weird errors when trying to run applications.

I think the upgrade screwed this system.  I'm really trying hard not to reinstall, as I've usually been able to recover in the past, but I think this time it's a gonner.  If I reinstall this time I'm doing straight Ubuntu and adding KDE base.  I only went with Kubuntu for KDE anyway.

---

### Post by bailout on 2007-05-08
> **RAdams said:**
> I've been messing with Kubuntu lately, and have come across a strange problem. In Ubuntu, "gksu nautilus" would give me a root file browsing window without any problems. However, "kdesu konqueror" gives me the following error message when I try to edit text files (such as my xorg.conf): "KDEInit could not launch 'Kate'." Anyone have any insight as to why this might be? Thanks.

I have never tried running konq as root but I have noticed that the 'edit as root' menu opens the file in kwrite instead of kate. I don't know why but I assume there must be some reason why the devs included 2 editors and use kwrite for root when kate is the main txt app otherwise. 

I usually install kedit as it is faster and I don't need all the added features of kate. I think kedit with tabs would be ideal as the default and leave kate as an optional install for those who use an editor for programming etc and need the features.

---

### Post by mocha on 2007-05-08
I finally figured out what was wrong.  I needed to copy "konq-kubuntu.rc" to /root/share/apps/konqueror".  Now I can open Konqueror in root mode and have it look like it used to.

---

### Post by icindr13 on 2008-05-16
With your help, and some logic here is what made it work 4 me...

1. Open a terminal in Root mode(Start>Aplications>system>Terminal)
    from the "Sessions" dropdown menu select new root shell...
2. Type apt-get install konqueror(and/or dolphin)
3. After install exit root terminal and type kdesudo konqueror
4. It all works... You are browsing your computer in root mode!!!
   Have Fun With Kubuntu!!!

I run on Kubuntu 8.04 KDE4 remix and this little issue gave me a 3h torrment..
What i would not do 4 gaming on Kubuntu... :D

---

