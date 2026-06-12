---
title: "Where is the desktop cube gears?"
date: 2009-03-31
forum: Desktop Environments
---

### Post by Ecstatic23 on 2009-03-31
Hears a screenshot of my compiz window:
[IMG]http://img24.imageshack.us/img24/9452/screenshot1par.png[/IMG]

I can't seem to find cube gears..

---

### Post by James_Lochhead on 2009-03-31
It should be under effects. It is for me at least.

---

### Post by zjagannatha on 2009-03-31
Are you sure you're running the latest version of Compiz?

---

### Post by Godly on 2009-03-31
> **Ecstatic23 said:**
> Hears a screenshot of my compiz window:
[IMG]http://img24.imageshack.us/img24/9452/screenshot1par.png[/IMG]

I can't seem to find cube gears..
What is under Preferences? Click on that and let it load. There should be a check box on the left for "extra" or somehting of that nature. Make sure that is checked, and you should see cube gears next to cube. Please let me know, I'll check into it for you.

---

### Post by Ecstatic23 on 2009-04-01
It isn't under effects, they're's nothing really worth mentioning in preferences, I think I have the newest version, I've only had compiz for just over a month.

---

### Post by 3rdalbum on 2009-04-01
Install the "compiz-fusion-plugins-extra" package from Synaptic and you should have the Cube Gears plugin.

---

### Post by Ecstatic23 on 2009-04-01
> **3rdalbum said:**
> Install the "compiz-fusion-plugins-extra" package from Synaptic and you should have the Cube Gears plugin.

I just installed that, I check the cube gears box, then two seconds later it un checks itself???

---

### Post by steeleyuk on 2009-04-01
Usually they uncheck because its an older version that doesn't work with the current one. Either that or there's a fault somewhere.

---

### Post by Giblet5 on 2009-04-01
> **steeleyuk said:**
> Usually they uncheck because its an older version that doesn't work with the current one. Either that or there's a fault somewhere.

That.

If you installed compiz via svn/git/tarball, then... Good luck. Those methods are not for people who need to ask what's wrong, they're for people who can figure it out from the code.

If you have installed Compiz from Synaptic, then what release of Ubuntu are you on?

You're missing a lot of stuff...

[IMG]http://img5.imageshack.us/img5/5569/32504834.jpg[/IMG]

---

### Post by Ecstatic23 on 2009-04-01
> **Giblet5 said:**
> That.

If you installed compiz via svn/git/tarball, then... Good luck. Those methods are not for people who need to ask what's wrong, they're for people who can figure it out from the code.

If you have installed Compiz from Synaptic, then what release of Ubuntu are you on?

You're missing a lot of stuff...


I'm using Hardy. I did install from Synpatic, which I can't get to work because it keeps asking me to reload it, but anyway,

I have the extra package, all my options are there, it just won't let me enable them.

---

### Post by Giblet5 on 2009-04-01
> **Ecstatic23 said:**
> I'm using Hardy. I did install from Synpatic, which I can't get to work because it keeps asking me to reload it, but anyway,

I have the extra package, all my options are there, it just won't let me enable them.


It could be a permissions or ownership problem.

It's wise to start with:
chown -R $LOGNAME:$LOGNAME $HOME

If you upgraded to Hardy, try creating a dummy account, log out, log in as the new dummy user, set up compiz the way you want it, then compare the common files under both user's home directories.

---

