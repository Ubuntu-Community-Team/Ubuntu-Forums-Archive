---
title: "Firefox and Thunderbird 1.5: &quot;Check for updates&quot; not available"
date: 2006-04-15
forum: Desktop Environments
---

### Post by roncrump on 2006-04-15
Hi,

I have Firefox 1.5 and Thunderbird 1.5 installed in Breezy. Followed the instructions (I think correctly) on the wiki, and they both have been running fine for some time.

Howver, for some reason the "Check For Updates" option is not available from the Help menu (ie it is present but greyed out/inactive). I know there are updates available for the Widnows version and presume that there are for the linux one. Any suggestions as to what may be wrong.

I believe that, although the option is set in my preferences, firefox is not automatically checking for updates either.

Ron.

---

### Post by John.Michael.Kane on 2006-04-15
You will probably have to install the new version the same way you did the frist time.

---

### Post by towsonu2003 on 2006-04-15
not exactly. Check out the same wiki again (wiki.ubuntu.com/FirefoxNewVersion). It has a section about how to update. Automatic updates won't work because users don't (and shouldn't) have privileges to change applications. wiki explains it briefly.

---

### Post by 5-HT on 2006-04-15
*EDIT: towsonu2003 got to it while I was writing. Why oh why didn't I just link to the wiki? It's much better described there.
--------------------------------------

To install them, did you take the binaries from the mozilla site, put them into /opt, and make the proper symbolic links for 'firefox' and 'thunderbird'?

If you did, you need to do a 

```
gksudo firefox
gksudo thunderbird 
``` 
Or if the sym links aren't set up ```
 gksudo <path to executable> 
``` 
in order to check for and install updates.

Be careful NOT to surf around while firefox is running with root priviledges. 
Just update and close the program, then open it back up as a normal user.

Same thing goes for thunderbird. Just update and close, do not check for or read any mail while it's running under root priviledges.

Hope that helps.

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=5-HT]
```
gksudo firefox
gksudo thunderbird 
``` 
[/QUOTE]
that still is risky though. A small unknown bug in either firefox or thunderbird may trash your system (bc firefox/thunderbird is now free to do whatever it pleases with your system). 

The sudo/gksudo way also have the probablity of changing file ownerships of your profile. If you already did the sudo firefox / gksudo firefox to update it/them, see if your profile got it wrong, and fix it: 

To check if everything is okay (note that there is no use of "sudo"):
```
chown -R username:username ~/.mozilla/firefox
```
no errors means profile is good. Errors (like "no permission to blabla") mean you need to fix the profile. 

To fix the profile (note the use of "sudo" now):
```
sudo chown -R username:username ~/.mozilla/firefox
```

PS. I accidentally did the update your way as well :oops: ;) .
PSS. There are reports that gksudo firefox do not change permissions in your profile. I did my update with sudo firefox, and it changed profile permissions to root...
PSSS. If doing the wiki way of updating, do **NOT** forget to change /opt/firefox ownership to root right after the update; do not wait a second to do that.

---

### Post by 5-HT on 2006-04-15
[quote=towsonu2003]that still is risky though. A small unknown bug in either firefox or thunderbird may trash your system (bc firefox/thunderbird is now free to do whatever it pleases with your system)
...

PSSS. If doing the wiki way of updating, do **NOT** forget to change /opt/firefox ownership to root right after the update; do not wait a second to do that.[/quote] 
I stand corrected.
I'll change ownership to myself to do the updates from now on to avoid the influence of any bugs in the program having possible system-wide repercussions.

Thanks.

---

