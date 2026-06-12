---
title: "Can't login to forums"
date: 2007-08-25
forum: Forum Feedback &amp; Help
---

### Post by benbelly on 2007-08-25
I am using firefox in Feisty, and I am having a LOT of trouble logging in to the forums.  I've (obviously) managed to find a work-around, but it's unpleasant.
  My problem is that I get redirected back to the forums as a non-logged in user after typing the correct username and password.  I'm sure I type them correctly, and I get the 'Thank you for logging in benbelly' message.  But after redirection, I'm not logged in anymore.

  The workaround I have discovered is to:
- Clear cookies
- Log in
- Click the "fail to redirect" link BEFORE getting redirected.

  This allows me to be logged in for one to five page views.  Then I'm gone again.

  What the heck is going on?!

  Can anyone give me some tips?  I'm comfortable with the terminal, so feel free to suggest command line tools.

-Ben

---

### Post by angryfirelord on 2007-08-25
Clear your cookies by going to Edit-->Preferences-->Privacy-->Cookies-->Show Cookies-->Remove All Cookies. Under the Cookies option, select Accept cookies from sites and keep until they expire.

---

### Post by bapoumba on 2007-08-25
Try also to clear your cache.

---

### Post by benbelly on 2007-08-25
Thanks for the suggestions.  I tried them all, and no love.  I still can't log in.  Grrrrrr.

Links2 seems to work OK.

---

### Post by benbelly on 2007-08-25
Reinstalled firefox - that didn't help.  I'm kinda glad about that.  I'd hate to think Ubuntu was acting like Windows!

---

### Post by bapoumba on 2007-08-25
If links works, then its not something with your internet connection. Try to disable all your extensions in Firefox. Add them one by one if this works.

---

### Post by benbelly on 2007-08-25
I disabled everything (just mouse gestures, session manager, and foxy proxy).  No good.

---

### Post by angryfirelord on 2007-08-25
I'm just throwing anything out at the moment, but install epiphany-browser (in repos) and [swiftweasel](http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717) and see if either of those makes a difference.

---

### Post by bapoumba on 2007-08-26
Please disable foxyproxy and logout from your Ubuntu session. Then log back in, and try.

---

### Post by benbelly on 2007-08-26
I disabled everything, including FoxyProxy, and got the same problem.

I also fail to log in using epiphany and swiftweasel.
On a whim, I ran sudo firefox.  That didn't help either.  It did have BBC Headlines as the toolbar news RSS feed.  That made me wonder if there is something wrong with my time settings.  I went to System->Admin->Time and Date.  Everything there was correct.  Switched to NTP just to see what would happen.  That didn't make a difference.  I'm chasing rabbit trails now.  :(

---

### Post by bapoumba on 2007-08-26
What do you get with a:
```
ping ubuntuforums.org
```
(you end it with ctrl-c)

```
:~ $ ping ubuntuforums.org
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=1 ttl=52 time=54.8 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=2 ttl=52 time=56.6 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=3 ttl=52 time=54.6 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=4 ttl=52 time=57.2 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=5 ttl=52 time=53.8 ms

--- ubuntuforums.org ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4000ms
rtt min/avg/max/mdev = 53.857/55.431/57.243/1.315 ms

```

---

### Post by benbelly on 2007-08-27
Well.  This is a little embarrassing.  I've been going to
[www.ubuntu-forums.org](www.ubuntu-forums.org)

Which is the address that doesn't work w/ firefox.  When I use
ubuntuforums.org

everything works fine.  I'm not sure where I got that hyphenated address, but I'm switching to the non-hyphenated.

Thanks for all the help!!

Here's the ping output for both addresses in case you're curious about it.

ben@duel:~$ ping ubuntuforums.org
PING ubuntuforums.org (82.211.81.186) 56(84) bytes of data.
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=1 ttl=46 time=107 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=2 ttl=46 time=107 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=3 ttl=46 time=105 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=4 ttl=46 time=109 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=5 ttl=46 time=109 ms

--- ubuntuforums.org ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 105.020/107.854/109.887/1.794 ms

ben@duel:~$ ping [www.ubuntu-forums.org](www.ubuntu-forums.org)
PING [www.ubuntu-forums.org](www.ubuntu-forums.org) (82.211.81.186) 56(84) bytes of data.
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=1 ttl=46 time=109 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=2 ttl=46 time=109 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=3 ttl=46 time=108 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=4 ttl=46 time=111 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=5 ttl=46 time=112 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=6 ttl=46 time=113 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=7 ttl=46 time=105 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=8 ttl=46 time=113 ms
64 bytes from ohiggins.ubuntu.com (82.211.81.186): icmp_seq=9 ttl=46 time=107 ms

--- [www.ubuntu-forums.org](www.ubuntu-forums.org) ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8027ms
rtt min/avg/max/mdev = 105.179/109.994/113.967/2.817 ms
ben@duel:~$

---

### Post by angryfirelord on 2007-08-27
Glad to see that the problem is resolved, but it's weird that adding a hyphen would direct you to a different server or different location on the server. The IP addresses on the two are the same.

Oh well, we'll leave that for the mods to figure out. ;-)

---

### Post by bapoumba on 2007-08-27
> **angryfirelord said:**
> 
Oh well, we'll leave that for the mods to figure out. ;-)
/me passes it to the admins ;)
Glad to see you got it to work now!

---

### Post by PriceChild on 2007-08-27
Yeah that'll need to be changed to a redirect like ubuntuforums.com

---

