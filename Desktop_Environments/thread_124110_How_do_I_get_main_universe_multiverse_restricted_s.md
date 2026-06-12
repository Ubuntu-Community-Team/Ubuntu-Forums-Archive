---
title: "How do I get main universe multiverse restricted software?"
date: 2006-01-31
forum: Desktop Environments
---

### Post by buster on 2006-01-31
I did a search and noticed from some threads that the Synaptic error for 'backports' can be corrected by eliminating the source. If I do that, how do I get the software usually stored in 'main universe multiverse restricted'? (I am at present trying to solve my Ubuntu's inability to play Quicktime movie trailers.)

---

### Post by Adrian on 2006-01-31
[QUOTE=buster]I did a search and noticed from some threads that the Synaptic error for 'backports' can be corrected by eliminating the source. If I do that, how do I get the software usually stored in 'main universe multiverse restricted'? (I am at present trying to solve my Ubuntu's inability to play Quicktime movie trailers.)[/QUOTE]

You need the repositories listed in this document:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

There you'll also find an up-to-date backports repository.

---

### Post by buster on 2006-01-31
Thanks Adrian, I'm updating my Synaptic as I write. I made the appropriate change. (I must say I feel I may have communicated with you in a different distro forum in the past.)

Again thanks for the quick and clear response.

Buster

---

### Post by buster on 2006-02-01
Hi Adrian,

I only substitiuted in this particular server:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

And now I can't get logged into a gui. I'm assuming in retrospect I should have pasted in the whole list rather than just replace the one server?  I've created some kind of conflict mess?

---

### Post by Adrian on 2006-02-01
Hi, again.

[QUOTE=buster]I only substitiuted in this particular server:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse[/QUOTE]

That should be enough, really. 
Feel free to post your /etc/apt/sources.list if you want us to take a look at it.

> And now I can't get logged into a gui.
Which GUI? Synaptic?
What error messages do you get?

---

### Post by buster on 2006-02-01
Which GUI? Synaptic?
What error messages do you get?"

I get to the loggin page, put in my user password, and it keeps going back to the loggin page - no message. When I do an alt ctrl F2 and log in and try startx I get server errors. I'm in another distro at the moment.

---

### Post by Adrian on 2006-02-01
[QUOTE=buster]Which GUI? Synaptic?
What error messages do you get?"

I get to the loggin page, put in my user password, and it keeps going back to the loggin page - no message. When I do an alt ctrl F2 and log in and try startx I get server errors. I'm in another distro at the moment.[/QUOTE]

This sounds very strange. Things like that are not supposed to happen no matter what you do to your sources.list (provided that you didn't install anything afterwards). Did you install anything after altering sources.list?

---

### Post by buster on 2006-02-01
"This sounds very strange. Things like that are not supposed to happen no matter what you do to your sources.list (provided that you didn't install anything afterwards). Did you install anything after altering sources.list?"

Yes. In a way. I did an update, and then an upgrade - I believe I selected Smart Upgrade. Saw Amorak coming in but I don't recall anything to do with XOrg or anything. Maybe about ten things. Looked like a typical procedure to bring the software uptodate. (But obviously it wasn't.) I had done the kernel upgrade previous to this, but had rebooted with no problem. Then changed the source - did the update/upgrade.

Tried booting with the old kernel too and it made no difference.

---

### Post by Lord Illidan on 2006-02-01
Can you use failsafe mode?
When you log in, type startx.

or ```
sudo /etc/init.d/gdm start
```

---

### Post by buster on 2006-02-01
"Can you use failsafe mode?
When you log in, type startx."

booted recovery mode
took me to root@ubuntu
startx took me into root's home with a gui desktop
one error - "failed to initialize HAL'

But I am in. Should note that when I updated to Breezyquite awhile ago I ended up with a Kubuntu KDE login site rather than the gdm.

Any suggestions while I'm here Adrian or Lord?

---

### Post by buster on 2006-02-01
Kind of humourus that so many have complained they can't get into a root desktop, and it's the only place I can get!

---

### Post by buster on 2006-02-01
SOLVED SOLVED SOLVED!!!!!!
  
Thanks for your help everyone. This particular thread got me into a root desktop, and a clue on another thread about problems after trying to install Firefox 1.5 lead to a solution. 

What I ended up doing was going through recovery mode and doing a startx. Then through root's home got to my user home and deleted the .ICEauthority file. Rebooted and it worked.

Thanks to Lord Illidan. Adrian, and ipp3l1.

---

### Post by Adrian on 2006-02-01
[QUOTE=buster]SOLVED SOLVED SOLVED!!!!!![/QUOTE]

Congratulations :)
I'm glad you solved it at last. Seemed to be a tricky problem.

---

