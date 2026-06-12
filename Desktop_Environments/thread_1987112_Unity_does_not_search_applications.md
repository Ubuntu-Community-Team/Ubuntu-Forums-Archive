---
title: "Unity does not search applications"
date: 2012-05-25
forum: Desktop Environments
---

### Post by IAmTheAnswer on 2012-05-25
For reasons unknown to me, I cannot search for applications with the dash.  It looks like this:

[IMG]http://i.imgur.com/fLydq.jpg[/IMG]

So I searched and found [this]("http://askubuntu.com/questions/65727/unity-not-searching-applications/69498#69498") answer.  So, after trying that, I restarted and got this error:

[IMG]http://i.imgur.com/FjQ9P.png[/IMG]
(Note: I may have seen this message before.)

The problem remains unsolved.  How can I fix this?



Side question: How can I search for programs with the terminal?  I am rather new to Ubuntu, so I don't really know.

---

### Post by zombifier25 on 2012-05-26
Someone needs to file a bug report. Most of the times the Dash will show installed apps, but sometimes it doesn't. Try logging out and logging back in to see if the problem is fixed.

---

### Post by IAmTheAnswer on 2012-05-26
> **zombifier25 said:**
> Someone needs to file a bug report. Most of the times the Dash will show installed apps, but sometimes it doesn't. Try logging out and logging back in to see if the problem is fixed.

I have.  I've also restarted the computer a few times.

Somewhere, I found a way to reset Unity with the terminal, which seemed a possible solution.  After doing so, everything I did appeared in the terminal.  When I searched for an application, it said I didn't have the application lens.  I can go where it says it doesn't exist and find it.

Fun fact: The guest account will search for applications.

---

### Post by Frogs Hair on 2012-05-26
This happened when installing 12.04 on a friends computer yesterday and following command solved the problem.
```
Unity --reset
```

---

### Post by IAmTheAnswer on 2012-05-26
> **Frogs Hair said:**
> This happened when installing 12.04 on a friends computer yesterday and following command solved the problem.
```
Unity --reset
```

That is the reset command that I used.  It was also unsuccessful.

---

### Post by Frogs Hair on 2012-05-26
Since it is a Nautilus error you could try restarting with the following and pay attention to any errors if they appear. ```
nautilus -q
```

---

### Post by IAmTheAnswer on 2012-05-26
It didn't appear to do anything.

---

### Post by zombifier25 on 2012-05-27
> **IAmTheAnswer said:**
> That is the reset command that I used.  It was also unsuccessful.

It's "unity" not "Unity". If you know this already, then ignore this post.

---

### Post by n411303 on 2012-07-19
No applications were showing via Dash in Precise Pangolin 12.04.  Search did not work.  Software-Centre would not load just got a grey crash.  But Guest account was showing applications and searching.  Tried loads of things posted from various forums including deleting lots of hidden files and folders from the home folder, tried resetting unity, reinstalled software centre.  Nothing worked.  

But got solution as follows.  

* Logout
* Log back in with Ubuntu 2d
* Launch software centre and this time it did load 
* Close software centre
* Logout (note it took a long time to logout seemed to be saving lots of settings)
* Log back in with normal Ubuntu
* Everything back to normal.  

No idea why !!!

---

