---
title: "Google Earth issues"
date: 2009-06-15
forum: General Help
---

### Post by blur xc on 2009-06-15
Google Earth is one of my favorite apps- I mountian bike (used to a lot more than I do now, but I'm trying to get back into a steady habit agian), with gps, and love exploring new trails and putting my tracks into google earth.
 
So, I've got a couple of problems.  First- I must have installed it wrong or something.  I downloaded the .bin file from their website, rather than using the sudo apt-get install googleearth command.  When I run google earth it throws 3 or so error messages at me, saying it can't create folders in the /home/root (I think) directory.  
 
So, once I figured out how to get all that going, I ran that command, thinking it might fix my install, and it didn't.  It installed another google earth on my computer, and it gives the same error messages on startup.  So, I had two.  Removign ti via synaptic didn't help either.  I removed the one, but the other is still there, and isn't showing anywhere in synaptic.
 
So, how do I removed an app that doesn't show up on synaptic, and then, install google earth w/o messing anything else up, and getting rid of those error messages?
 
Thanks,
BM

---

### Post by Soul-Sing on 2009-06-15
Take a look in your /opt folder. Maybe there are traces of the program.
And ./googleearth in your home is already removed?
maybe also in usr/share/googleearth

---

### Post by Soul-Sing on 2009-06-15
> When I run google earth it throws 3 or so error messages at me, saying it can't create folders in the /home/[COLOR="Red"]root[/COLOR] (I think) directory.

What is the exact error message? Maybe there are messed up permissions....

---

### Post by blur xc on 2009-06-15
> **leoquant said:**
> What is the exact error message? Maybe there are messed up permissions....

Here is the original thread with my first go-a-round. [http://ubuntuforums.org/showthread.php?t=1183338](http://ubuntuforums.org/showthread.php?t=1183338)

How come I have a functioning Google Earth installed that doesn't show itself anywhere in synaptic?

BM

---

### Post by Soul-Sing on 2009-06-15
> sudo googleearth -style GTK+ %f
this isn't ok. It should start up without using sudo. .debs are found in synpatic packagemanager, not .bin installs. Normally they show up in /opt.

---

### Post by Soul-Sing on 2009-06-15
```
When I run google earth it throws 3 or so error messages at me, saying it can't create folders in the [COLOR="Red"]/home/root[/COLOR] (I think) directory. 
```

> [COLOR="Red"]sudo[/COLOR] googleearth -style GTK+ %f 

Indicates problems, this has te be done imo:

```
sudo chown -R <user_name>:<user_name> ~/.googleearth
```

---

### Post by blur xc on 2009-06-16
> **leoquant said:**
> ```
When I run google earth it throws 3 or so error messages at me, saying it can't create folders in the [COLOR=Red]/home/root[/COLOR] (I think) directory. 
```

Indicates problems, this has te be done imo:

```
sudo chown -R <user_name>:<user_name> ~/.googleearth
```

did that- didn't work.  So, how can I remove the app installed from a binary file, so I can reinstall from apt?

I changed to "/opt/google-earth" and did a ls -lha, and all the files in that directory are owned by root.  I don't know if that's normal or not.  This is the command initiated by the panel launcher- "/opt/google-earth//googleearth %f"

thanks,
BM

---

