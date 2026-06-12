---
title: "mplayer will not install"
date: 2006-06-06
forum: Desktop Environments
---

### Post by luvdemheels on 2006-06-06
it says the following:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libjack0.80.0-0 (>= 0.99.0) but it is not going to be installed


PLEASE HELP. ](*,) 

this is a fresh install of 6.06 after trying easy ubuntu

---

### Post by Jason_25 on 2006-06-06
Can you post the full terminal ouput when do you 
```

sudo apt-get install mplayer

```
?

---

### Post by buildid on 2006-06-06
i ve got the same problem , i removed the lib, but nothing works , so i look into the usr/lib directory found a newer version , and i give this command , dont know if it is right but mplayer is working again :

cd usr
cd lib

i guess i did this as root dont know anymore 
ln -s libjack-0.100.0.so.0.0.23 libjack-0.80.0.so.0

to tell you the truth i did try apt-get install and uninstall mplayer no errors at al , compile an svn version but that does not work either .
so i remember this command from edonkey.com forum for installing eDonkey , so ill give it a try and for me it is working.

but i have absolutly no idear what i have done , i was just trying ...

---

### Post by luvdemheels on 2006-06-06
The output is in my original message but here it is again:

"Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
mplayer-386: Depends: libjack0.80.0-0 (>= 0.99.0) but it is not going to be installed"

I wonder if it has something to do with my repositories, they all say breezy and nothing about Dapper or 6.06.

---

### Post by mrtrick on 2006-06-06
What repos do you have enabled?

---

### Post by luvdemheels on 2006-06-06
Good question, I tried to use easy ubuntu thinking I would take the easy way out to get all my multimedia going and now I have this and still cannot play avi files.

Everything normal seems enable but it all says breezy and there is also some plf repositories enabled. I wish I could see someone's repositories that are working correctly with the new Dapper.

---

