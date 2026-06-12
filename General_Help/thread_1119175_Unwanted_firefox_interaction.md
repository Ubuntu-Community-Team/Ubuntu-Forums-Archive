---
title: "Unwanted firefox interaction"
date: 2009-04-07
forum: General Help
---

### Post by hangfire on 2009-04-07
OK, here is the scenario. I'm working from a 8.04 KDE desktop, logged into via SSH to two Linux servers, A and B.

I start a firefox Server A, OK. It is on my desktop.

I start another firefox on the Server B, to view local HTML files on the filesystem of Server B. Instead, up pops another instance of firefox from Server A. I cannot view the local files of Server B. Booo.

Yes, I share the same home dir on Servers A and B.

I read the docs, I try firefox -no-remote. I get an error from B, "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."

My workflow requires I have both windows up at once. This is a MAJOR FAIL of my otherwise happy X Server usage of Ubuntu 8.04/KDE. I'm not sure who to blame, firefox, Gnome, X, Kubuntu, the other servers, or what.

Does anyone have a workaround, or is firefox hopelessly broken on NFS shared home dirs?

-HF

---

### Post by sdennie on 2009-04-07
You could probably solve this problem by using multiple firefox profiles.  In fact, I think that's the only way you will solve it if you have the same home directory on each server.  Try starting firefox with -ProfileManager and setup multiple profiles.  If you call them like, "Server_A" and "Server_B" you should then be able to start firefox with "-P Server_?".  Not sure if -no-remote is needed in that case.

---

### Post by maheshasolkar on 2009-04-07
Are you using same profile to launch Firefox on the two servers (with shared home directories)? If so, I would suggest using two different profiles.

Use the following to create profiles:

```
  firefox --profilemanager &
```

Create two separate profiles for server A and server B (with names ServerA and ServerB, for instance). Then launch firefox from the two servers with -no-remote. From server A:

```
  firefox -no-remote -P ServerA &
```

And from server B:

```
  firefox -no-remote -P ServerB &
```

---

### Post by hangfire on 2009-04-08
Thank you, sdennie & maheshasolkar. Your suggestions work great! As it turns out, *-no-remote* is needed.

**Solution**

First I used **firefox --profilemanager** & to create the 20 or so profiles I need. I named each with the short hostname. I also created one named *defaultprofile*, just in case.

Then I put the following in my .bash_profile:

```
export SHORTNAME=$(/bin/hostname -s)
```

And this alias in my .bashrc:

```
alias ff="firefox -P ${SHORTNAME:-defaultprofile} -no-remote"
```

Now, I can just launch with ff& and I get a correctly localized firefox.

---

### Post by sdennie on 2009-04-08
Sounds like a perfect solution.  Glad I could help point you in the right direction.

---

