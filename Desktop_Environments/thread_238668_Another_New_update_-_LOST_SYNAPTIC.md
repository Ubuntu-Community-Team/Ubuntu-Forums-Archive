---
title: "Another New update - LOST SYNAPTIC"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Uncle Spellbinder on 2006-08-18
I just received and installed the newest update. Yet another Gnome Terminal, python vte and such. Terminal works fine. I now cannot launch Synaptic Package Manager. Not from the icon, not from command, not at all. Ideas??

---

### Post by 23meg on 2006-08-18
Any errors you're getting? Type ```
sudo synatpic
```at a terminal and paste the output.

---

### Post by Uncle Spellbinder on 2006-08-18
Wow. When I copy/paste *sudo synaptic*, here's what I get:

```
wombat@wombat:~$ sudo synatpic
sudo: synatpic: command not found

```

When I type *sudo synaptic*, I get:

```
wombat@wombat:~$ sudo synaptic
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

```

---

### Post by Uncle Spellbinder on 2006-08-18
Someone on the compiz forum just suggested a "hack" for the time being:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

Good idea?

---

### Post by Cable on 2006-08-18
+1 on this problem.  Just updated a few minutes ago, I get this...
```

caleb@Cable:~$ sudo synaptic
Password:
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

```

---

### Post by orbital on 2006-08-18
I'm having the same problems with Synaptic and Terminal.

---

### Post by Uncle Spellbinder on 2006-08-18
```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

This worked. Synaptic is back!  Thanks go to *DBO* on the Compiz forum.

---

### Post by orbital on 2006-08-18
It worked. Now both Synaptic and Terminal work again.

---

### Post by Cable on 2006-08-18
The posted solution worked.  Doing that isn't going to mess with anything is it??

---

### Post by Uncle Spellbinder on 2006-08-18
> **Cable said:**
> The posted solution worked.  Doing that isn't going to mess with anything is it??

Not that I can tell. I've rebooted. Used Synaptic (and Terminal) without error. All seems just fine.

---

### Post by DBO on 2006-08-18
termporarly deleted

---

### Post by DBO on 2006-08-18
temporarly deleted until I can figure out exactly which source the new libvte4 came from.  The debs and the source arent matching.

edit - oops, didnt mean to make a new post

DBO

---

### Post by corefile on 2006-08-18
cool thanks the linking it fixed it for me

---

### Post by 23meg on 2006-08-18
> **Uncle Spellbinder said:**
> Wow. When I copy/paste *sudo synaptic*, here's what I get:That was my typo, obviously; I typed *synatpic *instead of *synaptic*.

---

### Post by kno on 2006-08-18
> **corefile said:**
> cool thanks the linking it fixed it for me

+1
It would be good to do more/some test before update...

---

### Post by DBO on 2006-08-18
well whats going on here is hes giving use a new libvte that is patched for true transparency.  I am guessing he has pulled it from edgy instead of doing this manually, which would be version 0.13.5, but he source hes uploaded to the repos is 0.12.x, so something is wrong here.  The issue is that in dapper we use libvte.so.4, where as edgy uses libvte.so.9, so this needs to be changed.  He appearantly forgot to do this (which is why the symlink is needed).  Its really a simple 2 second fix, which I was in the middle of posting a walkthrough of how to do when I discovered the source doesnt match.  Still trying to figure out exactly what he did.

DBO

---

### Post by janbockaert on 2006-08-18
This is why i switched to ubuntu. In suse it would have taken days to solve this problem. In ubuntu, a couple of hours; Same problem, and same solution worked! Thanks!

---

### Post by domino on 2006-08-18
Can some post and confirm if any new updates fixes this problem? I don't want to upgrade any of the affected files at this point.

thanks

---

### Post by kno on 2006-08-18
> **domino said:**
> Can some post and confirm if any new updates fixes this problem? I don't want to upgrade any of the affected files at this point.

thanks

Sorry, but no new update at this time.

---

### Post by SonicChao on 2006-08-18
Hm...I tried it without the hack and it worked for me.

```

sonicchao@sonicchao-laptop:~$ sudo synaptic
Password:
sonicchao@sonicchao-laptop:~$

```

So I donno what the problem could be...I usually just use apt-get anyway. ;)

---

### Post by distroman on 2006-08-18
> **Uncle Spellbinder said:**
> ```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

This worked. Synaptic is back!  Thanks go to *DBO* on the Compiz forum.
Thanks, did it for me too. 

Need a Red Alert Red Alert voice going of when updates become available :p at least the last one told you it would break stuff.

---

### Post by Uncle Spellbinder on 2006-08-18
One thing is for sure. When a new update is available, I'll be checking here and/or the Compiz thread before applying it.

---

### Post by amiga_os on 2006-08-18
This fix worked for me too.

What a bizarre problem...

---

### Post by Arzzka on 2006-08-18
Edit: huh.. it works. Thank you Random Roadkill..

---

### Post by Random Roadkill on 2006-08-18
your probably pressing shift+backspace by accident...i kept doing this during typing. add ```
xmodmap /usr/share/xmodmap/xmodmap.uk 
``` to your
system -> Prefrences -> Sessions -> startup programs. it just changes the default compiz keyboard mapping.

---

### Post by amr2205 on 2006-08-18
> **Uncle Spellbinder said:**
> Someone on the compiz forum just suggested a "hack" for the time being:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

Good idea?
You're right! I was trying to install compiz and after that, Synaptic and XFCE-Terminal haven't run anymore. I guess the compiz installation changed the symlink to that library. Thanks for the tip!

---

### Post by neymac on 2006-08-18
After the last update I've lost synaptic too. To get it back I downgrade the last 5 updates.


 ```
cd /var/cache/apt/archives
 
sudo dpkg -i gnome-terminal_2.14.2-0ubuntu2_i386.deb gnome-terminal-data_2.14.2-0ubuntu2_all.deb python-vte_1%3a0.12.2-0ubuntu2_i386.deb libvte4_1%3a0.12.2-0ubuntu2_i386.deb libvte-common_1%3a0.12.2-0ubuntu2_all.deb   

``` Then I got synaptic back.

Now I just  wait until the right versions apear to update again.

---

### Post by Cable on 2006-08-18
> **Uncle Spellbinder said:**
> One thing is for sure. When a new update is available, I'll be checking here and/or the Compiz thread before applying it.
Are you speaking of a specific thread, or just the compiz forum in general?  If you're speaking of a specific thread, will you post a link to said thread?  :p

---

### Post by ykpaiha on 2006-08-18
the trick with a link works fine 
thanks

---

### Post by domino on 2006-08-18
hmm, no synaptic update that fixes this yet? It's really strange that it's taking this long to get a fix. Again, if someone comes across the update, please post a reply here so I can finally get rid of the update icon on the Panel :D.

thanks

---

### Post by Uncle Spellbinder on 2006-08-18
> **Cable said:**
> Are you speaking of a specific thread, or just the compiz forum in general?  If you're speaking of a specific thread, will you post a link to said thread?  :p


It's this thread:  [**Fonts are now complete crap :(**](http://www.compiz.net/topic-3116-fonts-are-now-complete-crap)  Nearly 13 pages long now.

The thread title aluuded to the original update which screwed up fonts. It seems to be encompassing the whole update scenario that is happining now with the  compiz repos.

---

### Post by ChadMMc on 2006-08-19
I myself had just experienced the same problem with Synaptic and the latest upgrade.

I used the instructions given earlier in this thread and it is back up and running.

THIS is why I think Ubuntu Linux is GREAT!

If this was a commercial update and it caused this problem, I would most likely either still be waiting for a fix of some tyoe or rebuilding my system  again. 

Again. The Ubuntu Linux Community is great!

:) :D

---

### Post by domino on 2006-08-19
hmm, okay. now updates are gone. I never updated the packages that pertains to this thread. I guess that's good...

---

### Post by drudrewdizzy on 2006-08-19
> **Uncle Spellbinder said:**
> Someone on the compiz forum just suggested a "hack" for the time being:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

Good idea?

This solved my issue, this happened after I was playing w/ GLX/COMPIZ etc...

thnx.

---

### Post by bluevoodoo1 on 2006-08-19
> **Uncle Spellbinder said:**
> Someone on the compiz forum just suggested a "hack" for the time being:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

Good idea?

Thanks.

---

### Post by tomplast on 2006-08-20
If this is something related to XGL then fine but if this is due to an update it's really bad for people who don't know how to solve things like this (parents anyone?).

---

### Post by mrgnash on 2006-08-21
> **tomplast said:**
> If this is something related to XGL then fine but if this is due to an update it's really bad for people who don't know how to solve things like this (parents anyone?).

It's only related to XGL/Compiz. So I think it's safe that the mum & dad novice users aren't going to encounter it :)

---

### Post by Drakonik on 2006-09-04
I created the link, but synaptic still refuses to start. I'll restart, but I don't know if that will help.

Edit: No good. Any suggestions?

---

