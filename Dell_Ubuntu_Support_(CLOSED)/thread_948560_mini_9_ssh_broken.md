---
title: "mini 9 ssh broken"
date: 2008-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by abakus on 2008-10-15
hello, I just got my inspiron mini 9 with ubuntu on it. SSH always hang up right after I entered my password. It doesn't matter if I use x window or not. 

I found a post describing the same problem and pointing out a possible fix, but it doesnt work for me:[http://ubuntuforums.org/showthread.php?t=917187&highlight=ssh&page=7](http://ubuntuforums.org/showthread.php?t=917187&highlight=ssh&page=7)

Any idea? Thanks!

---

### Post by mssever on 2008-10-16
> **abakus said:**
> hello, I just got my inspiron mini 9 with ubuntu on it. SSH always hang up right after I entered my password. It doesn't matter if I use x window or not. 

I found a post describing the same problem and pointing out a possible fix, but it doesnt work for me:[http://ubuntuforums.org/showthread.php?t=917187&highlight=ssh&page=7](http://ubuntuforums.org/showthread.php?t=917187&highlight=ssh&page=7)

Any idea? Thanks!
Please describe your problem more clearly. Are you trying to SSH into your machine or from your machine? What does X have to do with it? Also, please provide a link to the post you referred to. Linking to the page of the thread doesn't work well since different people view different numbers of posts per page. That means that when I clicked the link, it didn't show me the post you referred to. You can find the specific link to post by clicking the post number.

---

### Post by ChuckFrain on 2008-10-18
I bumped into this problem on my Mini as well. If you take a look at launchpad bug #259816 this pretty much describes the problem. 

If you follow the post of [Pete Graner]("https://bugs.launchpad.net/dell/+bug/259816/comments/3") as listed the problem is resolved on a perlogin basis. I don't know how to make the solution persistant. I create a shell script to run it in my ~/bin directory. All it contains is the line 'sudo iwpriv eth1 set_vlanmode 0' sans quotes.

---

### Post by jr06compmaster on 2008-10-19
Any advice on how to make this run at startup?  I made a script but I can't seem to get it to automatically run.  Hard to believe dell shipped these with ssh broken like this...

---

### Post by mssever on 2008-10-19
> **jr06compmaster said:**
> Any advice on how to make this run at startup?  I made a script but I can't seem to get it to automatically run.  Hard to believe dell shipped these with ssh broken like this...
Run your script from /etc/rc.local

---

### Post by jr06compmaster on 2008-10-19
So...just paste the line from the above poster that works when you execute it, into that file before it exits?

---

### Post by mssever on 2008-10-19
> **jr06compmaster said:**
> So...just paste the line from the above poster that works when you execute it, into that file before it exits?
Yes, but you don't need the sudo since rc.local runs as root already.

---

### Post by jr06compmaster on 2008-10-19
So I put that in the file but it's still not working.  If I execute the line:  

sudo iwpriv eth1 set_vlanmode 0

in the terminal ssh works.  So I added "iwpriv eth1 set_vlanmode 0" into the rc.local file after resetting it's permissions and it still doesn't work.  Am I doing something wrong?

---

### Post by mssever on 2008-10-19
Oh, my bad. I forgot that, since you're presumably using NetworkManager, rc.local runs too early, since NM doesn't initialize wireless until after login. So you have to run it at startup (System > Preferences > Sessions). That means you'll need to put gksudo in front to the command, instead of sudo. However, it's possible that even that might run too early. In that case, your best bet is to create a custom launcher on your panel and manually run it when appropriate. According to the linked bug, this problem has been fixed, so you shouldn't need the workaround anymore once the update gets to you.

---

### Post by jr06compmaster on 2008-10-19
Thanks!  It worked after I changed it from sudo to gksudo :)

---

### Post by jr06compmaster on 2008-10-21
> **jr06compmaster said:**
> Thanks!  It worked after I changed it from sudo to gksudo :)

Just kidding...it was working, now it isnt lol.  What were you saying about "once the update gets to you"?  Is there something out to fix it already?

---

### Post by mssever on 2008-10-21
> **jr06compmaster said:**
> Just kidding...it was working, now it isnt lol.  What were you saying about "once the update gets to you"?  Is there something out to fix it already?
The linked bug has been fixed. So if your problem is indeed the same, then when you upgrade to version 2.6.24.14-21.51 of linux-restricted-modules-2.6.24, you'll get the fix. It's in intrepid and hardy-updates.

Otherwise, please give more information about what isn't working.

---

### Post by ajbaerg on 2008-11-03
I managed to fix this permanently by adding the following line to the end of /etc/network/if-pre-up.d/wireless-tools

/sbin/iwpriv eth1 set_vlanmode 0

---

### Post by ajbaerg on 2008-11-03
I managed to fix this permanently by adding the following line to the end of /etc/network/if-pre-up.d/wireless-tools

```
/sbin/iwpriv eth1 set_vlanmode 0
```

---

### Post by abakus on 2008-11-04
> **ajbaerg said:**
> I managed to fix this permanently by adding the following line to the end of /etc/network/if-pre-up.d/wireless-tools

```
/sbin/iwpriv eth1 set_vlanmode 0
```

ajbaerg, your method works perfectly for me! thank you so much you saved my mini's life.

---

