---
title: "Ubuntu logs me out when I do too much"
date: 2009-03-17
forum: General Help
---

### Post by Hank_61 on 2009-03-17
I looked around to see if anyone else had the same problem and couldn't find anything.

About a week or so ago I finally upgraded to Intrepid and I've been having a weird problem. As soon as I start to do several things at once the screen goes black for a second and then sends me back to the log in screen. This happens if I have more than, say, ten tabs open in Firefox (sometimes more or less...depends on how heavy the tabs are). It also will happen if I use just one tab in Firefox while music plays and I run gimp and open office (and any other programs) at the same time.

I think it's strange that the whole computer doesn't just crash. Instead it sends to the log out screen. What's up with that? I have a gig of ram so I didn't think it's related to that.

This isn't hugest problem to work around since it's not the end of the world if I have to limit myself to 8 tabs at a time. But still, it bothers me because it never used to happen before (on Hardy I'd had 20+ tabs open while watching a dvd and running all sort so ther apps, and it was always fine). On the occasion that I happen to forget to keep my CPU usage low and it does log me out, I end up losing all unsaved information, which is very frustrating.

Any ideas?

Thanks,

-Hank

---

### Post by Peasantoid on 2009-03-17
Are you accidentally hitting Ctrl-Alt-Delete or some variant thereof?

(Yeah yeah, I know it's a stupid question, but it's good to be sure.)

---

### Post by Hank_61 on 2009-03-17
No, nothing like that. It's like it gets overloaded when I do too many things. The screen goes black for a split second and then I'm right back at the login screen.

---

### Post by Vaphell on 2009-03-17
looks like X is crashing and restarting itself, but i don't know how to find out why

---

### Post by tgalati4 on 2009-03-18
Check /var/log for errors.

Check your home directory (ls -la) for xsession errors.

Update:  20 May 09

Hello Hank,

I was replying with a nokia n800, a mobile device, so I didn't have a Linux machine to give you the specific files.

In a terminal:

>ls -la

That will give you a list of files in your home directory. If you are not in your home directory, then:

>cd

That will change directory to your home directory.

The files you want to look at:

>cat .xsession-errors

In /var/log:

>cd /var/log

>cat Xorg.0.log

This all may sound complicated, but the X server has been around since 1980, so it has a lot of history. The X Windows system was one step away from the "W" windows system which became microsoft windows.

There are lots of things that can crash the X server, now called xorg server after the X Organization that maintains it.

Update your thread with entries from those files and you will get more helpful answers.

Using the terminal is like lifting the hood of a car. If you can fix a car then you can fix anything in Linux. All you need is a little patience and some knowhow. The forums can provide 99% of those answers.

Hope that's helpful.

Regards,

Terry,

West Hills, California

---

### Post by plucky on 2009-03-18
Is your swap partition working?

From a terminal ```
free -m
```

---

### Post by Hank_61 on 2009-03-18
> **tgalati4 said:**
> Check /var/log for errors.

Check your home directory (ls -la) for xsession errors.

Sorry, I'm a little confused by what you mean. Exactly which file do I have to open in /var/log/ to check for errors? I saw a lot and couldn't figure out which one I'm looking for.

And what does "ls -la" mean?

Sorry, I'm kind of a noob.


> **plucky said:**
> Is your swap partition working?

From a terminal ```
free -m
```

Okay, here's what it said:

```
             total       used       free     shared    buffers     cached
Mem:          1011        916         94          0        133        519
-/+ buffers/cache:        263        747
Swap:         1314         10       1303
```

I'm not really sure what means. How does it look?

Thanks a lot,

-Hank

---

### Post by plucky on 2009-03-19
> Swap:         1314         10       1303

Your swap partition is working,so it is not that.

Good Luck

---

### Post by Hank_61 on 2009-03-20
So does anyone have any other advice they can offer? It seems like it's slowly getting worse and it's really frustrating. 

I am pretty sure that it is, as a previous poster suggested, an issue of X crashing and rebooting, because it's the exact same thing that happens when you press ctrl+alt+backspace. It seems to be caused by doing too much stuff at once, which never used to happen before I upgraded.

Any reason why this would all of a sudden start happening when I upgraded to Intrepid Ibex? Any advice on how I might fix this?

Thanks a lot,

-Hank

---

