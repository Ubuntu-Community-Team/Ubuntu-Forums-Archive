---
title: "Ubuntu 8.10 and 8.04 doesn't remember virtually any settings"
date: 2008-12-21
forum: General Help
---

### Post by forteller on 2008-12-21
My friend has a Toshiba U300 - 159 laptop. I upgraded it from Hardy to Intrepid for her, and at the same time set up a separate /home partition. After this something very strange happened:

Whenever she reboot the computer most of her settings was lost:

Playlists in Rythmbox, new startup programs (in preferences -> Sessions), themes, etc. All of it was lost.

The only things that I'm aware of that was not lost was the desktop background and that Compiz-Fusion was enabled.

So we figured we'd just have to downgrade to Hardy, and we where sure that would fix the problem, since she did not have this problem before upgrading. But it didn't. We kept the same /home folder, but formated /, installed 8.04, ran an upgrade, and it's still as bad as it was with 8.10. Another problem that I'm not sure if where present in 8.10 or not is that Network Manager doesn't remember wired 802.1X connections.

So, yeah. This is terribly frustrating! Any help will be appreciated!

---

### Post by albinootje on 2008-12-21
> **forteller said:**
> 
Whenever she reboot the computer most of her settings was lost:
Playlists in Rythmbox, new startup programs (in preferences -> Sessions), themes, etc. All of it was lost.
The only things that I'm aware of that was not lost was the desktop background and that Compiz-Fusion was enabled.

Any errors about permissions ?
If you created a default user name called "jessica", then you can safely do 
```

sudo chown -R jessica:jessica /home/jessica

```
And see whether that helps.

---

### Post by forteller on 2008-12-21
Thanks for a quick reply!

I got this message:

```
chown: cannot access `/home/andrea/.gvfs': Permission denied
```

---

### Post by albinootje on 2008-12-21
> **forteller said:**
> Thanks for a quick reply!

I got this message:

```
chown: cannot access `/home/andrea/.gvfs': Permission denied
```

That's normal, don't worry. Seen it many times.

Is there any improvement now after logging out and logging in again ?

---

### Post by forteller on 2008-12-21
Yes, it fixed it! :)

Thank you very much! So, do you know what happened? It must have been when "upgrading" to 8.10, which wasn't actually an upgrade, it was a cleen install. So the wrong permission stuff was there from the begining of a cleen install. Which is, of course, really, really bad. But it's obviously not happening to everyone, so I'm terribly confused about this... :|

---

### Post by albinootje on 2008-12-21
> **forteller said:**
> Yes, it fixed it! :)

Thank you very much! 

Excellent :)
> So, do you know what happened? It must have been when "upgrading" to 8.10, which wasn't actually an upgrade, it was a cleen install. So the wrong permission stuff was there from the begining of a cleen install. Which is, of course, really, really bad. But it's obviously not happening to everyone, so I'm terribly confused about this... :|

Normally a new user in Ubuntu will get uid (User ID) 1000.
If you create another new user, that user will get uid 1001.
Did you use exactly the same username ?
And you didn't create any other users ?
If you only had one user, with the same username, and you left the /home partition as it was, then this is weird.

But if you've copied /home to an external disk, and copied everything back, then that can explain the permission problems.

---

### Post by forteller on 2008-12-21
> **albinootje said:**
> Excellent :)


Normally a new user in Ubuntu will get uid (User ID) 1000.
If you create another new user, that user will get uid 1001.
Did you use exactly the same username ?
And you didn't create any other users ?
If you only had one user, with the same username, and you left the /home partition as it was, then this is weird.

But if you've copied /home to an external disk, and copied everything back, then that can explain the permission problems.

Yeah, that's what we did when we did the clean install of 8.10. So I guess it was our fault, not Ubuntu's then. Kinda.. But I do think it should be easy to upgrade by taking a backup of your /home and then copy it back afterwards without getting these kinds of problems, though. I hope that will "fixed" some time soon!

---

### Post by albinootje on 2008-12-21
> **forteller said:**
> Yeah, that's what we did when we did the clean install of 8.10. So I guess it was our fault, not Ubuntu's then. Kinda.. But I do think it should be easy to upgrade by taking a backup of your /home and then copy it back afterwards without getting these kinds of problems, though. I hope that will "fixed" some time soon!

If you think this needs to be fixed in Ubuntu, then you can add it as a suggestion at [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com)

---

